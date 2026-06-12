---
title: "Home network - computer names &amp; addresses"
date: 2009-07-03
forum: New to Ubuntu
---

### Post by memilanuk on 2009-07-03
Ah... this is going to be a bit awkward - bear with me please ;)

What I have - fiber internet to a Linksys router/WAP/firewall, an eBox 'server' hooked up to one of the ports on the router (internal use only for the moment), and the rest of the house on wifi - from my iPod Touch to the HP All-in-One printer/scanner/copier, including the desktop PC and three laptops (two MacBooks and one PC laptop).  The wifi is secured using WPA2, and each machine has its own firewall as well as the one on the router/WAP.

In the past I've ran various forms of DHCP: either using the built in DHCP server in the Linksys box, which works - but doesn't allow fixed addresses, or more recently using the eBox server and fixed addresses so that the address to my printer stays the same regardless even through the odd power outage, etc. which it didn't always with plain dynamic DHCP.  The printer client software on the Mac was usually intelligent enough to 'find' it again on its own, but the PC printer client software was not - and I'd have to first realize that there *was* a problem, and then go find out what the new address was, change it in the printer driver, reboot, etc.  PITA, even for a small home network.

Even so... I'm still 'stuck' referring to machines on the network by their IP address.  There may not be a lot of them, but it still is kind of awkward.  I'm not sure I need a full DNS server for such a small network - or do I - to be able to tell my web browser on the desktop to go look at the web page I created on the small server running Apache, or to ssh into a particular machine from one of the Macbooks.  As a somewhat separate issue... I want to start using the server for a centralized SMB file server and do my back-ups from there.  I think I can get a single share set up and have everybody access it okay - but getting things sorted so that each user has their own directory and can store files in their own directory - preferably not visible, or at least not accessible, to others.  Do I need to set up a primary domain controller or LDAP server as well, or can that be handled in a simpler fashion?

Sorry for the long-winded post - I've been away from Linux for a while (years), and whilst I recognize a lot of the terms (Bind, PDC, SMB, NFS, NTP, etc.) the gory details seem to have slipped my mind ;)

Any advice or suggestions would be welcome.  I've been reading through the LTS Server guide, as well as looking at the documentation over on samba.org... but I'm just at the tip of the iceberg at this point.  Lots of documentation, but knowing what I need (or don't need) looks to be half the battle.

Thanks,

Monte

---

### Post by Boondoklife on 2009-07-03
Ok this is going to be the simplest fix, Check to see if your linksys router can take the dd-wrt firmware and if not get one.

This will let you do what you want using dnsmasq. There is even a tutorial on how to set it up on their site.

---

### Post by memilanuk on 2009-07-03
Wow!  That does look like it'd add some much needed functionality to my WRT54G box... and it looks like it's compatible.  I'll definitely have to look into that some more.  

Still kinda stumbling about in the dark about names vs. ip addresses for local machines... it looks like DNSmasq (which DD-WRT provides along with static DHCP) would do the trick?  Then I just have to get all the various services I want straightened out - starting with Samba (got the link in your sig-line, thanks!).

Thanks,

Monte

---

### Post by Boondoklife on 2009-07-03
Hey no worries, we all bumble around untill we find a good doc on how to do something. That firmware is what I run and it works great. The dnsmasq keeps the names that you assign the adapters (Static IP), and then anytime you refer to one of the names it resolves it.

---

### Post by memilanuk on 2009-07-03
I hate to say it... from looking at the DD-WRT wiki on DNSmasq & DHCP (static and otherwise)... it sounds so dang simple - using DNSmasq as both DNS forwarder for external requests, and as the DHCP server, and to 'serve up' local network names/ips... kind of one of those things I have to wonder a) why don't the OEM vendor interfaces for these routers do this and b) seems something that the 'canned' home server packages like eBox would want to be all over!

Well, time for more reading.  I'll see how it goes and then be back for more ;)

Thanks,

Monte

---

### Post by CatKiller on 2009-07-03
> **memilanuk said:**
> I'm still 'stuck' referring to machines on the network by their IP address.

If the machines have got static IP addresses (or are generally assigned the same addresses) you could always add an alias for each machine in your /etc/hosts file. It's just a list of IP addresses and the corresponding hostname. Then you can refer to each machine by hostname instead. I'd imagine there's an equivalent file for your non-Linux machines.

---

### Post by swerdna on 2009-07-04
When you finish with the router and get round to Samba, this would be worth a read:
[Samba LAN Primer for Ubuntu: HowTo Set up an Ubuntu-Windows Home & Office LAN/Network]("http://ubuntu.swerdna.org/ubulanprimer.html")

---

### Post by MrWES on 2009-07-04
> **memilanuk said:**
> Wow!  That does look like it'd add some much needed functionality to my WRT54G box... and it looks like it's compatible.  I'll definitely have to look into that some more.  

Still kinda stumbling about in the dark about names vs. ip addresses for local machines... it looks like DNSmasq (which DD-WRT provides along with static DHCP) would do the trick?  Then I just have to get all the various services I want straightened out - starting with Samba (got the link in your sig-line, thanks!).

Thanks,

Monte

Not to confuse things, but the tomato firmware should also work on that router. I run it on my linksys router.

[http://www.polarcloud.com/tomato]("http://www.polarcloud.com/tomato")

Bill

---

### Post by memilanuk on 2009-07-04
Well... nuts.

Before when I said it looked like my WRT54G was compatible... I was looking at the firmware edition (v.1.0.1.nn).  Digging through the dd-wrt wiki some more, found where *specifically* to look for the version numbers - found mine is ***ver. 6***, s/n ***CDFD***1F*nnn*...  Great, I thought.  Even newer.  Not so great as it turns out...

> 
Linksys WRT54G Neutered Models

Version 5.0 Serial number begins with: CDFB
Version 5.1 Serial number begins with: CDFC
Version **6.0** Serial number begins wtih: **CDFD**


> 
On the neutered models listed above, Linksys reduced the flash memory and the RAM compared to previous versions of these models, thus the term "neutered"

> Having said that, if you have one of these neutered models, you'd still be much better off selling it and getting something else that is a supported device. The forum is filled with questions on these neutered models. Lots of bricks. 

> BrainSlayer himself does not encourage using one of these routers. With the limited available memory, it really doesn't pay for the developers to put alot of time into making firmware for these models. As BrainSlayer wrote in a forum post, "most problems on v5 routers are caused by out of memory situations which can result in a freezed router". This applies to all neutered routers. 

> DD-WRT Micro is the only version that works on these neutered machines. 
(the tomato thingy linked to above only covers v1-4).

Nuts.  I seem to have a knack for buying 'cripples'... found out my brand new HP Pavillion 64-bit machine with 8gb RAM, 640gb hd, etc. etc. etc. is 'crippled' in that it doesn't have hardware virtualization enabled so I can't run 64bit guest OSs inside VirtualBox, and now this.  :icon_frown:

I may try sticking the DD-WRT micro version in there... or it may just wait until August when I'm back from my summer trip.  10 days left before we leave for England, and won't be back stateside until the end of the first week of August.  I might take a look and see if the local stores have something in stock like a WRT54GL, but I'm not going to order something in between now and then.  Actually, I think I'll leave this one alone and just 'donate' it to one of the kids - daughter is getting ready to head off to college this fall, and could probably use a router/WAP for her apartment... ;)

---

### Post by Boondoklife on 2009-07-04
Does micro not have dsnmasq? I run mini use to free up the space.

---

### Post by memilanuk on 2009-07-04
It looks like it does... but silly, paranoid me... I think I'd prefer to get a less ham-strung version up and running first, on a newer router, and then go back and upgrade the ver. 6 model to DD-WRT micro afterwards - that way if it gets turned into a 'brick' (which it sounds like those models are prone to) I still have an Internet connection ;)

---

### Post by ayenack on 2009-07-04
For SAMBA take a look at this.

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by cariboo on 2009-07-04
You can set static ip addresses with the Linksys router, I have a wrt54GS, which the third party apps wont work on. What I have done is set the dhcp range from 192.168.1.100 to 192.168.1.115, and then set my static ip addresses from 192.168.1.200 to 192.168.1.250.

Only two of the computers on my network run Windows XP and they can find the server by name with no problems the other 6 computers on the network needed to have the ip addresses and names added to the /etc/hosts file. This is what my /etc/hosts file looks like.

```
cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	alexis-karmic
192.168.1.250	willy
192.168.1.200	horsefly
192.168.1.201   smc_ap
192.168.1.1	router
192.168.1.210	quesnel
192.168.1.230	likely
192.168.1.215   chilanko
```

Willy is the server, it runs samba and lamp. There is only one computer on the network that needs to be backed up, and I use grsync to to that.

---

### Post by Boondoklife on 2009-07-04
This is true I would have a back up just incase, but you could do the skidish way. Buy a router locally dont open it. If the flash goes haywire then open it. If it works then take it back.

---

### Post by memilanuk on 2009-07-06
cariboo,

Is there any equivalent of the /etc/hosts file for Windows Vista i.e. how would I get it to do simple name-to-ip address lookup for machines on the local network like on a Linux box?  I haven't gone poking in my Macbook lately; I presume being a *BSD derivative MacOSX must have something like /etc/hosts in it somewhere?  Not sure I want to go munging that file on the wife's Macbook, though (belongs to the school district).  Ultimately it sounds like setting up dnsmasq via dd-wrt is going to be the better long-term solution, but since we're on the topic... ;)

Thanks,

Monte

---

### Post by memilanuk on 2009-07-06
<sigh>

Should have looked first...

(Windows Vista)

C:\Windows\System32\drivers\etc\hosts

(Mac OS X)

/private/etc/hosts

---

### Post by Boondoklife on 2009-07-06
Just remember to update those files if the ips or names change

---

### Post by memilanuk on 2009-07-06
Hmm...

Got the firmware upgraded to dd-wrt v.24sp1 micro generic... still sorting things out.  Seems to be a little bit of conflict between udhcpd and dnsmasq or the tutorials are a little off?  Lots of issues in their forum on DNSmasq issues - slow as a dhcp server, slow dns lookups, etc. etc.  Had to turn *off* DNSmasq as dhcp server on the setup page because machines didn't seem to be getting dhcp leases correctly.  *Now* it appears that udhcpd is 'seeing' the static dhcp reservations and honoring them, but without DNSmasq running as the dhcp server, I don't think its making its way into the hosts file.

Since all I could fit into the WRT54Gv6 was the 'micro' version of dd-wrt, I have no ssh - only telnet <gag>.  Tomorrow I'll have to login and see if I can view the config files and see whats going on.

---

### Post by Boondoklife on 2009-07-06
I would not recommend using the shell to get things done on it as it is very finicky. I personaly did not have any issues with slow dhcp or anything. Can you post up what you are changing on the pages and maybe I can help.

---

### Post by memilanuk on 2009-07-06
I wasn't planning so much on editing files from the shell on the router (unless I really absolutely have to) as much as just doing a 'less /etc/hosts' to see what was getting put in there.

At any rate, further investigation seems to indicate that [v.24 sp1 has some serious issues]("http://www.dd-wrt.com/phpBB2/viewtopic.php?t=52043") despite being the one you would logically pick for a WRT-54G v5 or v6 router on their download pages - and surprise, surprise, a lot of the issues are relate to DHCP, etc.

Looks like I need to upgrade to a newer build - at least I won't have to do it via tftp (not that that part was too tough) but can just do the next firmware upgrade from the web gui.

---

### Post by memilanuk on 2009-07-08
Hmmmm...  making progress, but not quite there.

Got the router firmware upgraded first to dd-wrt v24 sp1 micro generic, which turned out to be somewhat of a mistake - apparently v24 sp1 had a lot of bugs with regards to dhcp/dnsmasq.  So, I downloaded build 12307 - not the absolute most recent, thats at something like 12424 and counting - but its the latest recommended version for people not wanting to live on the edge or who don't use/need wireless N support.

So far using DNSmasq for the DHCP server with static IPs had been a miserable failure.  DHCP leases do not get renewed, and I have to manually configure the ip address of a network interface to get back into the web gui and fix things.  On the first 'Setup' tab, if I uncheck use 'Use DNSMasq for DHCP' which also unchecks 'DHCP-Authoritative':

[IMG]http://i12.photobucket.com/albums/a210/milanuk/computer_stuff/dd-wrt_dhcp-config-1.jpg[/IMG]

Here is what the corresponding part of the 'Services' tab looks like:

[IMG]http://i12.photobucket.com/albums/a210/milanuk/computer_stuff/dd-wrt_dhcp-config-2.jpg[/IMG]

I've seen different directions about what I am or am not supposed to enter for options in the DHCPd box, or the DNSMasq text box, and which program (udhcpd or dnsmasq) honors what.  Any insight or wisdom here would be much appreciated.

Finally, here is what the 'Wireless' portion of the 'Status' tab looks like.  It shows that I currently have three active machines on the network, my desktop, the wife's teaching laptop and the HP Photosmart network printer. It also shows the static dhcp leases (expires = never) set up for the other machines on the network (192.168.1.5x) and the dynamic address (192.168.1.100) for the Macbook.

[IMG]http://i12.photobucket.com/albums/a210/milanuk/computer_stuff/dd-wrt_dhcp-config-3.jpg[/IMG]

So at this point... it appears that I have dynamic DHCP working, static DHCP reservations working, it's handing out the proper settings for the gateway and DNS as evidenced by this snippet from the network connection properties from my desktop (running Vista):

[IMG]http://i12.photobucket.com/albums/a210/milanuk/computer_stuff/dd-wrt_dhcp-config-4.jpg[/IMG]

One of the things I found was on the original Setup tab, if you put 192.168.1.1 in the fields for 'Local DNS', it ends up pointing to itself twice - once there, and once when you enable 'Local DNS' under the DNSMasq options on the 'Services' tab.  So 0.0.0.0 appears to be the right way to go here:

[IMG]http://i12.photobucket.com/albums/a210/milanuk/computer_stuff/dd-wrt_dhcp-config-5.jpg[/IMG]

What I *don't* seem to have working is name lookup for local machines.  When I open up a console window from the desktop (running Vista) and type 'ping photosmart', I got a nice series of returns.  When I type 'ping macbook', I get 'Ping request could not find host macbook.  Please check the name and try again.  When I type 'ping macbook**_._**', I get a normal ping return.  If I go to the Macbook, open the Network Utility and ping 'photosmart', I get 'ping: cannot resolve photosmart: Unknown host'.  Change to 'photosmart_**.**_' and everything works fine.  As an added bonus, I can't ping the desktop (HP-PC) from the Macbook - if I try it without the '.' at the end, I get the unknown host error.   if I do append the '.', ping sends but does not receive any packets (i.e. 100% packet loss).  Maybe a problem w/ the Windows firewall some how?  A quick look didn't show anything glaringly obvious for allowing ping response...

As far as names on the web browser... if it has a web page (like the HP Photosmart printer does), entering 'photosmart.' as the URL takes me to it - but 'photosmart' returns a search from the Internet via the OpenDNS servers with possible results.

So... whats the deal with this '.' and why does it seem to be needed everywhere except when pinging the printer from the Windows PC?

How would I go about implementing a local network name like '.local' (i.e. photosmart.local'?  Is there any benefit to it?

TIA,

Monte

---

### Post by Boondoklife on 2009-07-08
Yea I dont bother with sp24 as 23 works fine for me.
Im gonna tell you what to have selected on each page that you have shown I will refer to them in the order you posted them.

In image 1 you need to check all three of the bottom boxes and you need to move the opendns servers down to dns2 and 3 and put in the routers internal ip as dns1.

On page 2 you need to set the lan domain to local if you do not have a domain you are going to use.
In the additional DNSMasq Options field put the following:```
local=/local/
expand-hosts
dhcp-option=6,192.168.1.1,208.67.222.222,208.67.220.220
```
Remeber if you use a domain name then replace the right hand local with the domain and make sure if you change the ip of the router to update it too.

---

### Post by memilanuk on 2009-07-08
Ah... this is where I think something major must have changed between v23 and v24.  The various howtos on the wiki about setting up dnsmasq hint at it, specifically:

> As of v24, DNSMasq respects the settings of the DHCP server on the "Setup" page and static leases set on the "Services" page 

They do recommend setting the check boxes and options pretty much as you suggested - but as I indicated before, it doesn't appear to work quite right with current releases.  At any rate, I went ahead and changed the settings as you mentioned, mainly to illustrate what happens:

[IMG]http://i12.photobucket.com/albums/a210/milanuk/computer_stuff/dd-wrt_dhcp-config-6.jpg[/IMG]

I'm guessing the odds are pretty good that when one of the clients goes to re-up their dhcp lease, they won't get one and I'll be back in there manually configuring the network connection to get back to the web gui and *un* checking those boxes on the Setup tab.

Followup... sure enough, it failed just as before.  When I opened up the Macbook and it resumed from sleep and went to renew its dhcp lease, it was unable to get anything, and assumed a default address.  I waited long enough for the desktop PC to do the same, and it did as well.

I put the checkboxes back to the way I had them (and my dhcp clients are happy again), pending any further discoveries.  I want to investigate the dnsmasq settings, at least the 'local' and 'expand-hosts' part, some more.  As an aside, putting the router ip first in the listing of DNS servers also results in it getting fed to the clients twice i.e. '192.168.1.1, 192.168.1.1,...'.  I think just checking 'Use DNSMasq for DNS' and then 'Local DNS' under the DNSMasq options is sufficient, from what I can tell.

Thanks,

Monte

---

