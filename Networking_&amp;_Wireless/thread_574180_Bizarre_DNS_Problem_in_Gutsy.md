---
title: "Bizarre DNS Problem in Gutsy"
date: 2007-10-12
forum: Networking &amp; Wireless
---

### Post by alex77 on 2007-10-12
Hiya,

Ok, weird one this. Whenever i do sudo apt-get or try and use the package mangagers, gutsy cannot resolve the IP addresses , and so everything fails. I can connect to the internet fine through firefox.

Also, if i visit one of the urls in firefox that apt-get tried to use, and then try again everything works. I guess gutsy caches resolved urls, and then this is used first before trying to resolve an address.

anyhoo, this is a pretty rubbish workaround, so if anybody knows what i can do to fix this then please help me!

(I have disabled IPV6...)

Thanks

---

### Post by alex77 on 2007-10-16
shameless bump...

---

### Post by reticentae on 2007-10-20
yeah, came across the same problem on gutsy, I think it has something to do with an issue I noticed debian had with resolving dns'es when connected to a router (I'm connected via an adsl router), you need to add the dns of your isp to resolv.conf for that one so you might try that and see if it solves the problem. I was going to until I saw your post about getting the browser to resolve it first, and I'm kinda lazy...

---

### Post by alex77 on 2007-10-22
yeah, that sounds like my set up. I am using an adsl router. Will try editing resolv.conf later tonight

---

### Post by alex77 on 2007-10-22
ok, resolv.conf now has my nameservers in it, but still no joy.

---

### Post by Haudegen on 2007-10-22
Hi all

Ok, I'm quiet new to Ubuntu and kind of guessing about this. I had also problems with my router and the DNS settings, which has always been set to my routers IP.
I found this thread: [http://ubuntuforums.org/showthread.php?t=243239](http://ubuntuforums.org/showthread.php?t=243239)
(and similar stuff elsewhere ...)

So try this:
Edit /etc/dhcp3/dhclient.conf
Add this line at the end of the file:

prepend domain-name-servers xxx.xxx.xxx.xxx, xxx.xxx.xxx.xxx;

replace the xxx with your DNS's IP addresses. I have two of them.
After rebooting, this IP's are added to resolv.conf on reboot, and everything works fine.

---

### Post by telemetry on 2007-10-24
This is driving me nuts too - I have also appended resolv.conf and Edit /etc/dhcp3/dhclient.conf with my DNS numbers but it doesn't seem to work.  Even if I do change the DNS successfully it's all lost on reboot despite editing as super user.  It's driving me up the wall.

I'm hoping someone can help.
robert.

---

### Post by alex77 on 2007-10-24
Ok, my dns settings are not lost at reboot, they just seem to be getting ignored by everything but firefox.

---

### Post by telemetry on 2007-10-24
I've just reinstalled gutsy - doing some experiments.  The network manager isn't very configurable.

---

### Post by telemetry on 2007-10-25
I've discovered that the problem often lies with IPV6 protocol and have discovered a solution for those who are having DNS problems or can't get google or the repostitories to contact the network.

It's real simple: open terminal and make yourself root user -        

1. IPv6 is supported by default in Ubuntu and can sometimes cause problems
2. To disable it, open a Terminal (Applications > Accessories > Terminal) and type the command: gksudo gedit /etc/modprobe.d/aliases
3. Find the line alias net-pf-10 ipv6 and change it to read alias net-pf-10 off

then save the new configuration and reboot and you should be ok.  I found this solution after much searching at Tom Raftery's social media website.

hope this helps
robert.

---

### Post by paulstaf on 2007-10-25
I did the IPV6 thing, and that fixed a lot, but I still have one weird thing going on:

Whenever I ping a host by IP, it responds quickly over and over with the ping statistics...
BUT, if I ping the same host by DNS name, it sits there for 5 seconds then spits out one line of ping statistics, 5 more seconds go by then the next line of stats, etc...

It is like it is having to re-lookup the name/ip every time it does a ping....like it isn't caching the name.....this is very annoying...

BTW, this is at work, no odd home router DNS setups here...

I converted to Linux/Ubuntu about a year ago, and this is the first time I have ever had to post before....I like Gutsy, I am wondering how these basic DNS problems and IPV6 problems got out of the lab and into the mainstream....everyone seems to be having the same issues seems they would have been caught earlier...

Thanks,
Paul

---

### Post by travtek on 2007-10-30
Thanks telemetry, for the solution to this problem.  I have been fighting this issue since Feisty came out and your solution has resolved it for me.

---

