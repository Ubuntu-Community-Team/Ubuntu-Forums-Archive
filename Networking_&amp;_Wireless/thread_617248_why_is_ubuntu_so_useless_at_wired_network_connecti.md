---
title: "why is ubuntu so useless at wired network connections on my server?"
date: 2007-11-19
forum: Networking &amp; Wireless
---

### Post by madjack on 2007-11-19
I'm trying to run a server, but keep on losing my wired internet connection, wireless works fine though. How can something as important as this slip throught the net? Vista beats ubuntu hand's down in network connectivity.

---

### Post by aa.ivanov on 2007-11-19
Sysadm standard  answer #5: It all works fine at my side.

Hint: Linux log files are a lot more useful than the missunderstanding windows calls logs.

---

### Post by farruinn on 2007-11-19
Did it work fine before you configured your server stuff? Since you didn't provide much information it gives the impression you're more interested in complaining than troubleshooting...

---

### Post by Rev60073 on 2007-11-19
I'm the exact opposite. My wired connection works fine (DHCP via a router, and cablemodem). But when I tried the live CD with my laptop, it was a nightmare.

I had a better experience with Fedora werewolf for wireless.

---

### Post by RudolfMDLT on 2007-11-19
Dear friend, if you have emotional troubles there is the backyard or community cafe or the local shrink, if you want help with your networking issues, please post some info and some one might help.

Best of luck,

Rudolf

---

### Post by RudolfMDLT on 2007-11-19
> **Rev60073 said:**
> I'm the exact opposite. My wired connection works fine (DHCP via a router, and cablemodem). But when I tried the live CD with my laptop, it was a nightmare.

I had a better experience with Fedora werewolf for wireless.

Would you like help in fixing your connection? I can't guarantee that I can help but I'm sure that someone might be able to help?

---

### Post by ukripper on 2007-11-19
> **madjack said:**
> I'm trying to run a server, but keep on losing my wired internet connection, wireless works fine though. How can something as important as this slip throught the net? Vista beats ubuntu hand's down in network connectivity.

Did you check your server logs? Piece of advise -  running server on wireless is unsecure

---

### Post by Seisen on 2007-11-19
What kind of network card do you have some are not supported very well?

---

### Post by sgtbug on 2007-11-19
u cannot just make a general statement like that, just because it is not working for you.. it works well for most people..

rather than asking us why it is useless, u can be a little positive in ur approach and request people to help, which they will with pleasure..

---

### Post by aysiu on 2007-11-19
> **coolaks said:**
> u cannot just make a general statement like that, just because it is not working for you.. it works well for most people.. I've retitled the thread to more accurately reflect what's going on.

In fact, from what I've seen on these forums over the years *and* from my personal experience, I'd say wired network connections are pretty reliable for most Ubuntu users--if anything's flaky, it's wireless.

---

### Post by rustybronco on 2007-11-19
Flame bait? / troll?
[http://ubuntuforums.org/showthread.php?t=607209](http://ubuntuforums.org/showthread.php?t=607209)
[http://ubuntuforums.org/showpost.php?p=3733855&postcount=6](http://ubuntuforums.org/showpost.php?p=3733855&postcount=6)
[http://ubuntuforums.org/showpost.php?p=3733964&postcount=4](http://ubuntuforums.org/showpost.php?p=3733964&postcount=4)
[http://ubuntuforums.org/showthread.php?t=610647](http://ubuntuforums.org/showthread.php?t=610647)
[http://ubuntuforums.org/showthread.php?t=617248](http://ubuntuforums.org/showthread.php?t=617248)

---

### Post by madjack on 2007-11-19
> **coolaks said:**
> u cannot just make a general statement like that, just because it is not working for you.. it works well for most people..

rather than asking us why it is useless, u can be a little positive in ur approach and request people to help, which they will with pleasure..

why, can't I make a general statement - ubuntu seems to have a fundamental problem with it' wired connection - it's not just me, there's lot's of people who are losing their wired connection. Just because it's working for most people, doesn't mean that there isn't a problem.

---

### Post by madjack on 2007-11-19
> **RudolfMDLT said:**
> Dear friend, if you have emotional troubles there is the backyard or community cafe or the local shrink, if you want help with your networking issues, please post some info and some one might help.

Best of luck,

Rudolf

what info do you want?

---

### Post by madjack on 2007-11-19
> **Seisen said:**
> What kind of network card do you have some are not supported very well?

I don't know the exact card, but it's an intel card, in a new thinkpad. The funny thing is that it works fine and then loses the connection after some time - I then have to restart the machine, and it starts working again.

---

### Post by pjkoczan on 2007-11-19
> **madjack said:**
> I don't know the exact card, but it's an intel card, in a new thinkpad. The funny thing is that it works fine and then loses the connection after some time - I then have to restart the machine, and it starts working again.

Open a terminal (go to [http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal) in case you have trouble with that), and paste the output of the command 'cat /etc/modprobe.conf' (minus the quotes).

Specifically, paste the line that contains eth0, it should be something like:
```
alias eth0 X
```

The X will tell you what driver/chipset the ethernet interface is using (e100, e1000, sysconnect, etc), which will give you the ability to search for issues relating to that driver or have one of us suggest a fix.

Offhand, there are only a few things that I can think of besides driver/OS issues that may be giving you problems.
- Contention between wired/wireless (though I doubt it, I've had wireless and wired working simultaneously with no problems).
- Something bad in the way of your computer and the internet. Bad cable, bad router, ISP being flaky, etc.

Hope this helps.

P.S. If you've ever had to guide a new user through navigating the Windows control panel, or do a fresh Windows that doesn't include any network drivers (and by default it doesn't), then you'll know exactly how "intuitive" it is.

---

### Post by dhtseany on 2007-11-19
Gee, call me crazy but that seems a little more along the lines of a DHCP problem with your router. Before crying and complaining that it's automatically Ubuntu's problem take a look at your hardware. I'm running an Intel NIC in my laptop and I have absolutely no problems with it. 

Just my thoughts,

Sean

---

### Post by sgtbug on 2007-11-20
on my machine i am using my onboard nvidia lan.. flawless..!! the problem is my netgear wireless usb device.. it is not working properly..

mostly people do not get problems with the wired.. it is the wireless that is the problem..

some people did get wired problems in my part of the world too but it could all be fixed.. the problem was with their adsl router.

---

### Post by Udibuntu on 2007-11-20
Yup, sounds like DHCP issue.

I had the same problem on a Thinkpad.

Change to static IP with the right numbers punched in and it would probably work just fine.

Udi

P.S - lose the attitude madjack; nobody here called you a yokel 'cause you can't tell what hardware is in your server, right?

---

### Post by ukripper on 2007-11-20
Can you post output of the following?
```
sudo ifconfig
```

Last time i helped someone regarding this problem it was wierd ip address showing up in ifconfig due to DHCP not assigning ip properly!

check this post [http://ubuntuforums.org/showthread.php?t=614606](http://ubuntuforums.org/showthread.php?t=614606)

---

### Post by madjack on 2007-11-20
> **dhtseany said:**
> Gee, call me crazy but that seems a little more along the lines of a DHCP problem with your router. Before crying and complaining that it's automatically Ubuntu's problem take a look at your hardware. I'm running an Intel NIC in my laptop and I have absolutely no problems with it. 

Just my thoughts,

Sean


well, you're crazy. I'm not using dhcp, I've assigned a static ip address. Also, the reason I don't think it's the router is that the problem is resolved by restarting my pc, but not resolved by restarting my router.

---

### Post by dhtseany on 2007-11-20
> **madjack said:**
> well, you're crazy. I'm not using dhcp, I've assigned a static ip address. Also, the reason I don't think it's the router is that the problem is resolved by restarting my pc, but not resolved by restarting my router.

Then maybe specifying that would help.

But you know what? Now that I know you're using a static IP **I know exactly what's wrong**. However, since you're being a dick get support from someone else. I'm not here to help elitist jerks like yourself.

Sean

---

### Post by ukripper on 2007-11-20
> **rustybronco said:**
> Flame bait? / troll?
[http://ubuntuforums.org/showthread.php?t=607209](http://ubuntuforums.org/showthread.php?t=607209)
[http://ubuntuforums.org/showpost.php?p=3733855&postcount=6](http://ubuntuforums.org/showpost.php?p=3733855&postcount=6)
[http://ubuntuforums.org/showpost.php?p=3733964&postcount=4](http://ubuntuforums.org/showpost.php?p=3733964&postcount=4)
[http://ubuntuforums.org/showthread.php?t=610647](http://ubuntuforums.org/showthread.php?t=610647)
[http://ubuntuforums.org/showthread.php?t=617248](http://ubuntuforums.org/showthread.php?t=617248)

I fully sympathize with this entity, negative attitude towards life hence mourning.

---

### Post by edm1 on 2007-11-20
> **dhtseany said:**
> Then maybe specifying that would help.

But you know what? Now that I know you're using a static IP **I know exactly what's wrong**. However, since you're being a dick get support from someone else. I'm not here to help elitist jerks like yourself.

Sean

Well if you do know a solution would you mind telling me because i seem to experiencing the same problem on my gusty desktop edition. Thanks.

---

### Post by ukripper on 2007-11-21
Try disabling ipv6 - [http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html)

---

