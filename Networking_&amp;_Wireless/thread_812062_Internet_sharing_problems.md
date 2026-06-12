---
title: "Internet sharing problems"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by johannesleung on 2008-05-29
ok, first hello to all linux users.

Iam starting the migrating progress from linux, windows platform, for now Iam able to achieve everything I achieved on windows without problem following the hundreds howto and tutorias around the internet, but one task is giving me a really really hard time, and its sharing my internet. without sucess I folowed hundreds of configurations, tried firestarted, learned how to fix some firestarter problems, tried masquerading, dhcp3-server, webmin, I think I may be leaving something behing cause I just cant achieve it, since Iam running out of ideas and the diferents faqs Iam findidng on internet are pointing the same things that I tried already Iam asking help here.

my internet is setup like this

modem pppoe, cant route
modem connected on eth0
eth1 connects to a hub
3 computers connect to that hub
they are running windows xp, for the xp configurations I know what to do, setup static ips, subnet and gateway, I just cant configure ubuunt properly to share the internet. Hope I dont need to go back into windows cause of internet isue :(

---

### Post by SpaceTeddy on 2008-05-29
this [[COLOR="Blue"]thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=713874") explains how to turn ubuntu into a gateway. Check if you have done all the steps :)

you probably want to take a good look at the secionts 
 - Enable IP forwarding
 - Configuring iptables (paket filter)

which is where i would assume your problem.

hope it helps :)

---

