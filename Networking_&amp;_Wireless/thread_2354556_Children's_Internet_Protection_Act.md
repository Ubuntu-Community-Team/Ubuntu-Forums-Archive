---
title: "Children's Internet Protection Act"
date: 2017-03-03
forum: Networking &amp; Wireless
---

### Post by cmcanulty on 2017-03-03
Our library has decided to accept e-rate federal funds to set up fiber optic service and so we have to comply with the Children's Internet Protection Act and filter adult images only, not any text. I can see how to install opendns to set up family shield. What I don't see is how to make the filtering  apply to images only, not text. Also according to the law the filtering has to be able to easily be turned off if an adult requests that. Can someone tell me how to be able to do that? I would prefer that the admin password would be required to turn it on and off, but I want it to apply to the limited user as the public users have no admin rights. I am running Xubuntu 16.04 64bit. Thank you very much.

---

### Post by TheFu on 2017-03-04
I don't know the answer. Sorry.  Do have a few thoughts, however.

How do other libraries do this?

I can't imaging that DNS is sufficient to filter just images. I fear you'll have to censor text with that as well. In fact, text will be easier to censor using tools like Dan's Guardian [http://dansguardian.org/](http://dansguardian.org/) based on content keyword lists. BTW, I used to work with a group of librarians and understand how much censoring is against the core values for most librarians. For more reasons against this censorship requirement: [https://www.aclu.org/other/fact-sheet-childrens-internet-protection-act](https://www.aclu.org/other/fact-sheet-childrens-internet-protection-act)

But we both live in a world were being practical is necessary.  

To disable the DNS filtering, just change the DNS provider to a different one, perhaps google's DNS?  You can run a tool to see which DNS provider is the fastest, just be aware to pick a reputable provider, since pretty much all internet security completely depends on truthful DNS. The wrong DNS provider can make spoofing HTTPS possible.

How to change the DNS provider completely depends on how the networking was setup.  With DHCP, it is harder (IMHO). With static IPs, it is just swapping a file in /etc/resolvconf/resolv.conf.d/ and restarting the resolvconf service. This can be modified remotely, so when the request happened, you wouldn't need to physically visit the PC.

Besides Dan's Guardian, Smoothwall could be worth checking into.

---

### Post by cmcanulty on 2017-03-04
Yes thanks, I was aware of the constitutional issues. Both I and the librarians are totally opposed to the filtering but our board has decided to go through with the federal e-rate program and so we are required to filter obscene images only. I am also setting it up so all our in-house computers are only wired (which is inconvenient to say the least). But then I can just enable wifi on one computer to make it fit the turn off filter requirement if requested by an adult. So I will filter the wired only and leave wireless unfiltered so other people  can use wireless on their own machines freely. What I am looking at now is how to un-enable the wireless so it holds at reboot but is easily enabled to be used if requested by an adult. So far all the ways I try to un-enable wireless don't persist at reboot. The wireless un-enabling needs to be easily enabled and unenabled by any librarian, some of whom aren't techy. Any ideas? Also for the opendns do we need to have 2 static ips coming into the router or modem? I don't understand that part as networking is my weakness but I am the volunteer tech manager so need help. Thanks again.

---

### Post by TheFu on 2017-03-04
Wifi vs wired is an interesting way to accomplish this.  I would always use wired myself, having deployed wifi to over 1,200 locations.

You'll need a better understanding of networking to make this work.  Do not have 2 IPs from the same machine on the same subnet unless you are nearly an expert.  To learn more about this, Security Now, a podcast, did about 5 episodes on "How the Internet Works" which might be helpful.  It is good knowledge to have for any adult doing any computer stuff, IMHO.  [http://grc.com/sn](http://grc.com/sn)   start with episode 25.

I would make a script on the machines that can be swapped and have those scripts only available from specific accounts.  Then back on the controlling machine, I'd have ssh keys setup to allow the other librarians to run a local script that connected to the remote machine and enabled or disabled censoring.   Something like "enable_filtering  machine1" would be the command.  The hostname, network-name and label on the top of the machine should all match.  I'd probably setup cron to enable filtering overnight too - would be bad if someone forgot to turn it off, right?   Plus, I suspect most adults wouldn't notice the difference most of the time.

If you don't use DHCP for the library machines, then which DNS is used can easily be handled locally by an admin.  No need to enable/disable interfaces or change any other settings.  Just setup 2 working resolvconf setup and swap the file (filtering or open) in and restart the resolvconf service.  The script would be 

```
#!/bin/bash

if [ "$1" = "on" ] ; then
   cp /etc/resolvconf/resolv.conf.d/filtered-settings /etc/resolvconf/resolv.conf.d/base
   service resolvconf restart
   echo "Filtering enabled."
else
   cp /etc/resolvconf/resolv.conf.d/open-settings /etc/resolvconf/resolv.conf.d/base
   service resolvconf restart
   echo "No filtering"
fi
```

Using sudo and remote logins only for specific users, it would be easy to make two icons on the desktops for each authorized librarian to enable/disable the filtering.  Simplistic sudoers Guide: [https://ubuntuforums.org/showthread.php?t=1132821](https://ubuntuforums.org/showthread.php?t=1132821)

---

### Post by cmcanulty on 2017-03-04
I just have one static ip for the library router and then local internal static ips for each computer. I do remote access by opening certain router ports for rdp (not the standard port numbers, I know enough to not do that). What I don't understand is the opendns family shield. I have read the page below, but does changing the dns settings  interfere with the static router ip or the static local computer addresses?

[https://support.opendns.com/hc/en-us/articles/228007087-Ubuntu](https://support.opendns.com/hc/en-us/articles/228007087-Ubuntu)

---

### Post by TheFu on 2017-03-04
Dude.  Don't use rdp or vnc to remote anywhere without a full VPN.  Please don't get hacked.  Running on a non-standard port doesn't hide anything.

Use ssh.  ssh, sftp, scp are highly secure AND more convenient.

There are hundreds of ssh how-tos. Find one. Get comfortable.  ssh is one of those few things that is both more convenient AND more secure. This will be a way of life if you ever hope to have secure connections on Unix systems.

If you don't understand DNS, then you'll never actually secure/filter these systems. DNS filtering is pretty easy to get around.

---

### Post by SeijiSensei on 2017-03-04
On the images-only question, I presume a large portion of these will be blocked by domain name if you use something like DansGuardian.  If there is a Squid proxy somewhere in your setup then you could write [access control lists ("acl's")]("http://wiki.squid-cache.org/SquidFaq/SquidAcl#Access_Lists")'s that would apply filtering only to media URLs and not to textual ones.
```

acl media rep_mime_type -i /etc/squid/media_mime_types.conf
acl baddomains dst_domain /etc/squid/bad_domains.conf
http_reply_access deny media baddomains

```
This blocks access to mime types in media_mime_types.conf from domains in the bad_domains.conf file.  Maybe there is an appropriate domains files in Dansguardian.  I've not looked at that software in any detail.  The current set of mime types are in /etc/mime.types; use this posting as a guide: [http://www.linuxquestions.org/questions/linux-software-2/squid-rep_mime_type-or-req_mime_type-807710/](http://www.linuxquestions.org/questions/linux-software-2/squid-rep_mime_type-or-req_mime_type-807710/)

I'd also use Squid to enable access to the "adult" machine, which I'd also wire to the network.  All the workstations should have static addresses.  Suppose the adult machine is 192.168.1.10.  Then you can have Squid rules like these:
```

acl permitted_user src 192.168.1.10
acl my_network 192.168.1.0/24

http_access allow permitted_user 

[rules for everyone else]

http_access allow my_network
http_access deny all

```

[Using Squid with HTTPS connections is tricky]("http://wiki.squid-cache.org/ConfigExamples/Intercept/SslBumpExplicit").

Will people on these machines be able to use other IP services (which?) or just browse the web?

---

### Post by TheFu on 2017-03-04
Please clarify that machines can be assigned static IPs AND that a few will need to be both filtered and non-filtered, as the current demand requires.

---

### Post by cmcanulty on 2017-03-04
Thanks everyone. We only have to have one machine available unfiltered. That is why I thought it would  be better to do it by machine rather that at the router. All the computers have an internal static ip. The router has an external wan static ip.Supposedly anyone can browse anywhere they want that isn't filtered. The filtering is supposed to be obscene images only.The issue I foresee in filtering by domain names is the fluidity of the web. It seems like it would be a constant game of changing targets. The opendns family shield seems like a valid thing to try but it is quite vague on what actually gets filtered. How much will subjecting all web addresses to a filter slow down browsing? And will they just get a page not found notice? Sorry if I offended anyone by not replying immediately. I do this as a volunteer and can't spend full time on it. The commercial filtering solutions seem quite expensive but maybe are more accurate. Thank you

---

### Post by TheFu on 2017-03-04
Just some thoughts ... 

I don't believe any filtering of just adult images is possible. Cannot think of any viable method to accomplish that on any platform without being a liar. I can think of methods that might mostly work, but it will still be domain-level filters of images regardless.  There are always ways through hacked web sites.  There are probably over a million hacked wordpress sites out there today with images that the owner doesn't know, for example. My spam email gets hit with "look at my new photos" messages a few times a week. Those photos almost always go to some wordpress site run by an organization who doesn't know how to secure their web server. As long as their main webpage is working, they don't know they are also spamming and hosting dangerous exploits, images and phishing pages.  

DNS like the family filter from opendns just blocks the entire domain. A DNS lookup to playboy.com would simply return "not found", so anything referencing that domain - using the name - wouldn't work. No text would be seen either, using the DNS method.  If someone knew the IP, they could still get there and view the content without some other filtering involved.

Browsing would probably be faster. Blocking tracking and ad servers makes browsing safer AND faster. All their content doesn't get downloaded.

Squid could provide content-based **text** filtering, but hmans are gooood at mispelng words, but still undrstndng the meeng.

I doubt any commercial filtering is actually "better." Just because they have marketing departments, doesn't mean they actually do what they claim. That could just be my bias against mass-market software. Odd since I made a living as a software developer for about a decade, but only did commercial software for about half that time.  

There are many, many, many block lists available for the interent.  I'm using some from the [pi-hole project]("https://pi-hole.net/"), which is designed to stop nasty sites (bad guys) and advertising and tracking servers.  Currently there are ... 
```
$ wc -l /etc/hosts
131533 /etc/hosts
```
different addresses being blocked. Yes, that is 131,000 web addresses. I am not blocking any strictly adult sites. However, since many "bad sites" use adult content to trick people into visiting, there is probably some overlap in my blocking.

Effectively, the open DNS family-blocking service simply doesn't return an answer when asked for a porn-site.  That can be accomplished by multiple other methods - one is using another machine to run something like pi-whole or perhaps doing what this article suggests: [https://lifehacker.com/5817447/how-to-block-unwanted-ads-in-all-applications-and-speed-up-web-browsing-with-the-hosts-file](https://lifehacker.com/5817447/how-to-block-unwanted-ads-in-all-applications-and-speed-up-web-browsing-with-the-hosts-file)


The internet is not just "the web." There are thousands of different protocols which can each be used. A few are listed in /etc/services, but this is NOT required.  Even as a guest, people can install a program into their HOME or /tmp/ and run it from there to use any of those other protocols.  This is why larger companies don't allow desktops to have direct access to the internet and only allow their proxy server to route traffic externally. All desktops are prohibited from getting to the internet by limiting DNS and through routing. They force all external desktop access through a proxy server. Only the proxy server can lookup internet DNS information, not the desktops.

---

### Post by SeijiSensei on 2017-03-05
> **cmcanulty said:**
> How much will subjecting all web addresses to a filter slow down browsing?
We maintain a Squid proxy at one of my clients' organizations that sits between about two hundred desktop users and the internet.  Even running SquidClamAV, which tests every downloaded object to see if it contains malware, you would observe no visible performance hit while browsing from a workstation.  This is a pretty hefty box (dual Xeons), but it's also scanning all incoming mail for spam and viruses as well, and still keeps up with web requests.

If all you end up doing is blocking sites via DNS, you won't see any performance hits either.

---

