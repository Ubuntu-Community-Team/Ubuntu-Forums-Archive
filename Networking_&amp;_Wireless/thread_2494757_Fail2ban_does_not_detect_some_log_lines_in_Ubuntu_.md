---
title: "Fail2ban does not detect some log lines in Ubuntu 22"
date: 2024-01-25
forum: Networking &amp; Wireless
---

### Post by pmgs on 2024-01-25
Hello All,

I noticed on an Ubuntu 22 server fail2ban does not detect (and so does not ban) all IPs it should.

For instance it does not detect this line 
[I]
     Jan 24 17:30:16 vps7 sshd[121778]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=103.101.160.198[/I]
  
But detects this one

     *Jan 24 05:55:35 vps7 sshd[41654]: error: PAM: Authentication failure for root from 219.233.13.170*
  
Can this be caused by a wrong config in my server?

Thanks for your advises.

---

### Post by TheFu on 2024-01-25
fail2ban uses regex to decide what it should ban.  Does your fail2ban have a regex that matches the failure you claim it is missing?

On stock Ubuntu, remote root attempts won't get anywhere - as the root account doesn't allow local or remote logins.

If you are using keys or ssh-certs only, never passwords, why does this matter?  Forcing keys/certs to be used is 2 lines in the sshd_config file.

I have to ask why you aren't blocking 99% of the internet from ssh already. Would anyone ever be trying to ssh into your system from either China or Vietnam?  If not, just block all IPs from those countries to ssh.  It isn't hard.  You can use tcp_wrappers to create a whitelist or use geoblocking at the firewall.  Of course, just moving the public ssh service off the default port 22/tcp to some random high port, will reduce the attempts 99%.

If you want more hoops, you can setup port-knocking as a requirement to open ssh for a few minutes. This way, ssh would be disabled, until you knock with a known packet on some other port first.  Then open it just long enough for the ssh connection to be setup, the new connections over it would be closed.

[https://www.tecmint.com/port-knocking-to-secure-ssh/](https://www.tecmint.com/port-knocking-to-secure-ssh/)

---

### Post by pmgs on 2024-01-25
Thank for your reply.

*Does your fail2ban have a regex that matches the failure you claim it is missing?*

Probably not 

I tested the log lines with  fail2ban-regex and the first line is not detected.

It's the standard fail2ban , I did not change regex filters and assume I don't have to touch standard filters.

I totally agree with your other comments but they do not answer to the question, I'm used to use fail2ban for a long time and it's the first time I see such thing, ... that's strange and not the "standard" of fail2ban if I'm right.

PS : I don't want to ban all China or Vietnam, just "unfriendly" IPs, it's the use case of fail2ban.

---

### Post by TheFu on 2024-01-25
If the provided regex don't do what you need, you can change them or add others.  Fail2ban has the ability to support custom filters. It is documented, probably on your system already: /usr/share/doc/fail2ban/   Check out the FILTERS.gz for a step-by-step howto.

Part of my job as an admin is to prevent temptation from people who have zero reason to access our systems. Preventing problems before they can happen is most of my job.

---

### Post by pmgs on 2024-01-26
[I]you can change them or add others

[/I]
I known this, but I used fail2ban out of the box for years and it's not a recommended way to change filters for standard usage. If nobody gives me an other answer I'll report this 'filter bug' on github and swich me server to debian 12.

---

### Post by TheFu on 2024-01-26
I didn't see anything offensive here or there.   Things change, sometimes at different times.  Looks like ssh log output changed and fail2ban of that same time period didn't.  That can happen.  If it is a critical need, Debian 12 is a year newer and perhaps the fail2ban rules from it were updated?  I have a Deb12 system here somewhere.  Maybe taking the regest for ssh from that version and adding it to custom fail2ban rules for Ubuntu 22.04 will work?   IDK.  Seems like less work that swapping an OS, though if you run both already, it wouldn't be a huge change and should take less than 30 minutes to swap the OS.  OTOH, replacing the regex rules is a 3 minute effort, right?

However, I don't claim to be any expert at anything. I've just be around a long time and have lots of wide experience, not in everything but in many things related to running servers.

If what I suggest as a fix doesn't work, that's fine.  You can't please everyone all the time.  It isn't like I'm being paid.

---

### Post by foxsquirrel on 2024-01-28
Not sure why you are even using fail2ban, it is a train wreck waiting to happen, just wait until you are permanently locked out of your machine for one. All the bad actors are using VPN so selectively blocking by IP is useless.

---

### Post by TheFu on 2024-01-28
> **foxsquirrel said:**
> Not sure why you are even using fail2ban, it is a train wreck waiting to happen, just wait until you are permanently locked out of your machine for one. All the bad actors are using VPN so selectively blocking by IP is useless.

Before blocking most of China, saw thousands of ssh attempts from Chinese Universities daily clogging up the logs. They were never going to get in (we don't allow passwords over the internet), but it was annoying.  A few other countries had similar pests.

---

### Post by foxsquirrel on 2024-01-28
> **TheFu said:**
> Before blocking most of China, saw thousands of ssh attempts from Chinese Universities daily clogging up the logs. They were never going to get in (we don't allow passwords over the internet), but it was annoying.  A few other countries had similar pests.

How do you know that was not your neighbor next door over messing with you?????

You should have gave them a little bit of a challenge and then let them in too wade around in a honey pot. Now, it gets really good.

---

### Post by TheFu on 2024-01-28
> **foxsquirrel said:**
> How do you know that was not your neighbor next door over messing with you?????
Nobody hacks a Chinese university address space, except Chinese or perhaps NKs then launches attacks.  They would have been coming from MSFT corp IPs instead.  
I've seen that as well, BTW.  Started blocking all MSFT corp IPs over a decade ago.

> **foxsquirrel said:**
> 
You should have gave them a little bit of a challenge and then let them in too wade around in a honey pot. Now, it gets really good.

Blocking is 10 seconds of effort for a /8 subnet.  Anything more is beyond what I want to waste time over.

It isn't just ssh. Attacks from the same subnets come for email and websites too.  Just easier to block all ports from those IPs for the kiddies.

---

### Post by foxsquirrel on 2024-01-28
> **TheFu said:**
> Nobody hacks a Chinese university address space, except Chinese or perhaps NKs then launches attacks.  They would have been coming from MSFT corp IPs instead.  
I've seen that as well, BTW.  Started blocking all MSFT corp IPs over a decade ago.



Blocking is 10 seconds of effort for a /8 subnet.  Anything more is beyond what I want to waste time over.

It isn't just ssh. Attacks from the same subnets come for email and websites too.  Just easier to block all ports from those IPs for the kiddies.

We don't care who is trying to breach us, what touches the internet is of little or no value. The internal network at work is air-gapped, our clients will use alternate methods to get the files to us, none of it touches the internet. That network runs like a swiss watch, this is not a joke. In the last ten years or more the ONLY issue we have had are the boxes having hardware failure. All I did was swap out HDD's into a working machine and back up. I don't have to touch that network, even the windows machines run flawlessly.

The stuff the does touch the internet has dedicated "spy" machines just for PCAP per each workstation.

[B]What EVERYONE is overlooking is the clear fact their SMART PHONE is the #1 threat in the world.
[/B]
Hospitals are hanging their own fiber networks between local satellite facilities because it is a lost cause trying to stop the BS that is going on. They have deep enough pockets to do that, most other companies don't have the money.

---

### Post by TheFu on 2024-01-29
Maybe I've been lucky, but everywhere I've worked the last 30 yrs makes hospital IT look poor.  When it came to network security, they would spend whatever was required for appropriate design, hardware, software, and maintenance.

No place I worked allowed wifi connections to the network, unless a full VPN was used with 2FA. Even then, the network segments those machines connected into were firewalled off for just their specific needs, not into the general network used by administrative desktops and certainly not into the secured network or any management networks used by admins.

I've also worked with air-gapped networks.  Any breach would have to be physical and involve at least 3 people.  Part of my job was introducing new software and data files into the air-gapped network.  I'd copy the stuff I wanted/needed inside the network off tape to a specific machine on a less secure network. Fill out the paperwork, call a number so the next team could scan it, copy it for archival reasons and copy it to a specific workstation in a more secure area of the building.  BTW, the entire 6 story building was surrounded by a Faraday cage - no RF worked to get in or out.  Anyway, I'd log into the next machine and move the files off it onto the LAN where my servers were located.  If I timed it right, this could all be accomplished in about 12 hrs, but 24-48 hrs was the stated time period.  No MSFT was allowed on the air-gapped network.  Only Unix and IBM mainframes where. No Linux.  There was a bunch of custom code for the environment. Only specific, commercial, C/C++ compilers were allowed to be used.

No place I've worked until around 2012 allowed BYOD.  Any equipment was provided and managed by the company and given appropriate access based on requirements into different areas of the network.  All desktops that connected to the internet use the company proxy server.  There was no way for desktops to reach the internet without using the proxy server.  Desktops only had enough DNS to lookup internal IPs, not external and there was no route from any desktop to the internet.  Further, all work desktops had a company TLS cert used to MITM all HTTPS traffic that did make it through the proxies onto the internet.  The company was very clear. Everything you do on our network is subject to review.  The company had over 50K physical UNIX servers and about 20K physical MSFT servers - I'm not counting desktops/laptops for employees.

This specific company had a number of bluecoat devices at all key traffic points. The people who recognize that name, know what it means.  Hospitals don't have the money for that. Heck, most companies don't have the money for that.  But the largest 50 companies do and companies who are required to be secure due to their industry do. They don't have any choice.

Anyway, the people in these forums all come from wide ranging backgrounds. 

I think IoT devices are a larger threat than smart phones/tablets, but those devices are also enough of a threat that I don't have any cellular data/voice service myself.  My "smart phone" can only use SIP to make/receive calls.  But my tablet can use exactly the same method, so the phone isn't really as flexible as any 8in tablet for my needs, unless I'm not taking any bag with me and only have pockets.  Of course, people say I'm odd because I won't do what everyone else does and convince myself it is fine.

---

### Post by foxsquirrel on 2024-01-29
> I think IoT devices are a larger threat than smart phones/tablets, 

Those are too, but not as bad as the phone, those IoT devices can be used to attack infrastructure and spy on every one. The phone will give out your EXACT location. Pretty sure you have heard of pegasus, they just had the misfortune of being caught, it would very safe to say others have not been caught.

---

### Post by TheFu on 2024-01-29
> **foxsquirrel said:**
> Those are too, but not as bad as the phone, those IoT devices can be used to attack infrastructure and spy on every one. The phone will give out your EXACT location. Pretty sure you have heard of pegasus, they just had the misfortune of being caught, it would very safe to say others have not been caught.

So, if you have a cell phone, at least in my country, they are all required by law to be able to provide GPS coordinates if you dial emergency services.  Additionally, with or without any cell voice or data plan, they all must be able to connect to E911 services.  Dialing 911 here does all sorts of things on devices.  Additionally, cell towers absolutely must be able to tell where you are to provide service, clean hand-off from tower to tower during the call, etc.  

The largest 2 service providers here have never deleted call logs, well, at least since the 1970s, so any call made from basically any cell phone will have 2 records - the caller and the callee. This is not by law, but law enforcement loves to buy these records.  When cell phones became popular in the late 1990s, they added approximate location data to their records.  POTS phone service always had service location information, which isn't always an address.

Anyway, Google and Apple don't have access to those things - in theory.  It is the cell providers who have it.  In many countries the cell provider is run by the govt, so that means those govts don't need to ask for data, they already have it.

So, my not having any cell provider just vastly reduces the number of entities with access to my location. In general, it also means that a search warrant signed by a judge is required to gain location data.

You can probably guess how I might know these things.

IoT is much scarier to me.  Since my neighbors all have camera pointing at my house with data sent to servers outside the US.  Streaming devices (TVs, sticks, players) are all sending data about what we watch, listen to and view to a number of 3rd parties.  Block those 3rd parties and the streaming stick/players stop working. I was surprised to see that Roku is selling this data to Google and Facebook.  It is one thing to agree to be a Nielson family [https://www.vulture.com/2015/12/nielsen-family-what-its-like.html](https://www.vulture.com/2015/12/nielsen-family-what-its-like.html) . That's a company that used to be the only real way that advertisers could guess how many people watched a specific TV show.  It was limited to TV.  These days, Nielson wants access to your viewing on any devices and all your internet data.  CATV companies got into the same market with their cable boxes.  All those "upgrades" where 50% for better pictures and better sound - the other 50% was to track your watching.  Now, people buy IoT TVs that listen to what we play in the room and figure out any media we watch using fingerprinting tech. This data is all sent by  the "smart TV" addon maker - roku, google, apply, Amazon if they are connected to the internet.  Basically, these people will earn over $50+/yr by reporting on what they see and near in our homes.  For low-end TVs, that means in 3 yrs, they've paid for the hardware, if they charged us $0.

I have a cheap Chinese IoT wifi camera, but it is in the attic, which greatly reduces the useful information it can provide. Mostly because my wifi network is outside my real network where 3 of my public IPs are, but not the gateway IP.

While I'm pretty privacy-conscious in my daily life, much more than most people and I don't think my govt should be violating laws against unreasonable search and seizure without probable-cause and a signed court order, I'm not THAT concerned about govts from friendly nations having that data.  They haven't abused it that I can tell.  Yes, it is wrong for them to have it.  I'd like for all captured data to be deleted and only allow the govt access for data in a specific location, time, with probable-cause and a signed court order.  That goes for gathering of any data in public by the govt.  The govt shouldn't have this data, because they will and have abused it.  Doesn't matter how well-meaning they are or the claims about terrorist acts they claim to have thwarted. 330M people shouldn't give up their privacy to protect 5 or 500 or 5000 others.
> Those who would give up essential Liberty, to purchase a little temporary Safety, deserve neither Liberty nor Safety.
- Franklin
Of course, I've taken that quote out of context.  He was actually talking about taxes being levied to support a war.  Franklin wanted the taxes passed. Anyway, I like it better for my purpose.  Don't give up freedoms, like the right to privacy, for any level of security that violates that right.  I much prefer the German version of privacy over that in my country.  There are probably better solutions that better weigh privacy with the need for public knowledge.  Secrecy without a clear time limitation is a bad thing.  If I get to help re-write the Constitution of my country (doubtful), I'd put in stronger privacy protections for non-public people as a default.

Anyway, we are far off topic and the last few posts really belong in "Chat", not the "networking" subforum.

---

