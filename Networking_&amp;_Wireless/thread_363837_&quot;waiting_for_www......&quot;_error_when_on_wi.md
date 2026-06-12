---
title: "&quot;waiting for www......&quot; error when on wireless at home"
date: 2007-02-17
forum: Networking &amp; Wireless
---

### Post by keith11 on 2007-02-17
Hi everyone, I am using firefox 2, mozilla, opera and ie6 on ubuntu edgy. I have absolutely no problems when I am on wireless at my university. But when I am at my home, I have all kinds of troubles. I am connecting to a wireless connection provided by my landlord and it has wep 64 bit encryption. The problem I am facing occurs half of the time, not always. Whenever I try to open a webpage in either of the four browsers I mentioned, I get stuck at "waiting for www...." and the page just doesn't load. 

The interesting thing about this is that when I ping a website from the console I get really good rates like 40-50 ms. I am writing this post from windows and I have the same ping rates even in windows so as far as the pinging goes, it works fine but there is some problem actually connecting to the internet in linux. It's not only my browsers which can't download a page and I know this because when I try to update the repositories, it gets stuck and shows download rate as unknown. 

I have read posts on this forum and even tried adding opendns servers to my resolv.conf but there always gets created a new file named resolv.conf~ with only my default dns servers which replaces the edited resolv.conf when I reboot. I am not sure if adding opendns dns servers works for me because whenever I have the opendns servers on top of my default servers in resolv.conf the pings go into the range of 1000-2000 ms. And if I have the opendns servers in my resolv.conf on top of my default dns servers, the wireless won't even connect from being disconnected.

Even with my default dns servers in the resolv.conf, I keep getting the internet problems I mentioned. Unfortunately, this doesn't always occur, meaning I sometimes get good speeds and I do ACTUALLY connect. This makes it more complex as I don't know  why it connects sometimes and not on other times. I have been trying to connect in Ubuntu for almost 3 hours now and when I just couldn't, I had to resort to windows (it should always be the other way around :), but anyways) and the wireless is working fine in windows. I would greatly appreciate if someone can figure out what the problem is and walk me through a solution as I am a newbie. Thank you.

Keith.

---

### Post by keith11 on 2007-02-19
Does this seem to be an issue with my resolv.conf? I am drawing this conclusion because after I have suspended my laptop by closing the lid, and then opened the lid back on, I find it impossible to connect again. At this point, I have checked my resolv.conf and the nameservers there are the same, but I am still not able to connect and if I connect then I am not able to download pages. The pings are good but I get stuck at "waiting for..." when downloading a webpage. Even when I come home from the university I find trouble connecting to my home wireless which has a 64 bit WEP encryption. I used the wireless radar applet to connect to wireless connections but whenever I am in the middle of the problem I described above, I am not able to connect to the wireless at home. I noticed one other thing that whenever I disconnect myself from my home wireless through the wireless radar applet, I can't connect back to the same wireless even though there is no problem with the wireless using the wireless radar applet. I am very confused and equally annoyed. I face absolutely no problem in the university though. I will appreciate any help regarding this. Thanks.

---

### Post by JackAcid on 2007-02-22
Not sure if this will help, but...
I am running Ubuntu 6.06LTS on a Sony Viao laptop. Wireless seems to work without a hitch everywhere except home. I did a lot of digging and finally realized that my actiontec dsl modem (and wireless router) would make itself (192.168.0.1) the first entry in the DNS table whenever I connected and I would have trouble connecting to **_some_** sites, like gmail or just google in general, and others would be no problem.
My first attempt to "fix" it was to simply remove that entry, but after some time period I would see the entry show up again and some sites would not be accessable.

I finally dug out my netgear router and put that between the modem and my network. Since I now use the Netgear router wireless and not the modem wireless, I have not had that problem.

Like I said, I'm not sure if this will help, but that is how I got around a similar problem.

have a better day!

Jack

---

### Post by Pedal_Pusher on 2007-02-23
I'm a newbie too so not sure if this will help either but ....

I had a similar problem with firefox working occasionally but using a wired connection (thread  #367562 ).

I found a note from ubunutgoz in thread #367498 :-

Try disabling ipv6

a - in FIREFOX browser type about:config
b - in the Filter bar (just below address bar) type ipv6
c - in the next window down (preferences), you'll see a single line network.disable.Ipv6
, double click until it is bold and the value is true

Firefox now works OK for me.  I suspect that it is a problem with my router (D-Link DSL-504T) which is a discontinued model.  Could yours / your landlord's be a problem ?

---

### Post by keith11 on 2007-02-23
JackAcid and Pedal_Pusher:

Thanks to both of you for your suggestions and sharing your solutions with me.:) Unfortunately, I have already implemented the solutions you suggested Pedal_Pusher and I am still having problems so it was not IPv6. I have disabled IPv6 in Firefox as well as globally. JackAcid, your solution may have worked for you, but as I mentioned I don't have access to the router as it is provided by my landlord. I have a suggestion for you though in case you want to try it out. You said your resolv.conf file was replacing the DNS server name entries. In case you want to keep the DNS entries same in your resolv.conf file, you can follow what 454redhawk suggested to me in one of my threads ([http://ubuntuforums.org/showthread.php?t=359503)](http://ubuntuforums.org/showthread.php?t=359503)), which was to lock the resolv.conf file. In order to be able to connect at home as well as other places I am using the DNS server names from opendns.org. Hope you will find this useful.

---

### Post by keith11 on 2007-02-25
Here I am again, facing the problem described in this thread. For a few days it was all working fine and pages were downloading fast and all, but suddenly, today, I am back to square one. I really don't know why I am not able to download pages when it shows I am connected. I have also observed the wireless-radar applet doesn't connect me back on if I disconnect through it once and then try to connect again. I can connect only if I restart the system, not even with restarting networking through "sudo /etc/init.d/networking restart". This is getting extremely annoying and windows-like behavior, because I don't know why this is happening. The pages just get stuck at "waiting for..." in Firefox as well as Mozilla. The pings in windows are in the range 80-100 while they are in the range 200-500 in ubuntu and this is happening just today. I haven't touched anything related to networking. I have just opened a port of Azureus yesterday. Sometimes, it just becomes so hard to work smoothly without any problems in ubuntu and the worst part is not being able to understand why it happened and how to fix it. If anyone can help me find out why I am facing this problem again and again, I will be truly thankful. 

Keith.

---

### Post by sixsmith on 2008-06-30
> **Pedal_Pusher said:**
> Try disabling ipv6

a - in FIREFOX browser type about:config
b - in the Filter bar (just below address bar) type ipv6
c - in the next window down (preferences), you'll see a single line network.disable.Ipv6
, double click until it is bold and the value is true


Pow! Works like a charm! Thanks!

---

