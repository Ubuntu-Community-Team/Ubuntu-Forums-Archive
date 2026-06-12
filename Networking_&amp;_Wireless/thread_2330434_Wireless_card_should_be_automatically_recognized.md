---
title: "Wireless card should be automatically recognized?"
date: 2016-07-11
forum: Networking &amp; Wireless
---

### Post by jenna33 on 2016-07-11
Hi guys

When I install Ubuntu on my laptop, should my wireless card be automatically recognized and ready to work? or do I have to get additional drivers? from where?

---

### Post by jeremy31 on 2016-07-11
*Thread moved to **Networking & Wireless**.*

See the wireless script link in my signature and post your results.  For most cases nothing is needed for wireless to work but there are special cases

---

### Post by grahammechanical on 2016-07-11
You can test this out by running the Try Ubuntu session. If the wireless adapter is recognized and a driver activated then you should be able to use Network Manager to see a list of wireless access points and even connect to them. We can even install a driver in a Try session but the driver will be lost once we shutdown the Try session. As will connection information.

The place to look for a driver if one is needed is System Settings>Software & Updates>Additional Drivers tab. You will need to be connected to the internet otherwise the utility cannot find the additional drivers. Besides, it is much better to install Ubuntu with a wired connection. It lessens the risk of some kind of failure during the installation process.

Regards.

---

### Post by jenna33 on 2016-07-12
> **grahammechanical said:**
> You can test this out by running the Try Ubuntu session. If the wireless adapter is recognized and a driver activated then you should be able to use Network Manager to see a list of wireless access points and even connect to them. We can even install a driver in a Try session but the driver will be lost once we shutdown the Try session. As will connection information.

The place to look for a driver if one is needed is System Settings>Software & Updates>Additional Drivers tab. There is a page [[color=#000000]here[/color]](http://www.lawsuitsettlementfunding.co) that explains it and you can have a look at that. You will need to be connected to the internet otherwise the utility cannot find the additional drivers. Besides, it is much better to install Ubuntu with a wired connection. It lessens the risk of some kind of failure during the installation process.

Regards.

Sorry, I am dumb, what is Try Ubuntu session? I don't know much about this stuff.

---

### Post by him610 on 2016-07-12
> Sorry, I am dumb No, not dumb, just inexperienced.

When you first boot into Ubuntu from the installation media, usually a DVD or USB memory stick, you will be presented with a screen where you have the option to (1) 'try Ubuntu' without installing, or to (2) install Ubuntu on your system.

The wireless card *should* be recognized and the driver should be installed; however, depending on the manufacturer of your wireless card or chip, it may not be recognized which is why it is a good idea to try Ubuntu. Sometimes, newer wireless cards may not be recognized.

Even if you decide to install Ubuntu without your wireless card being recognized, you can always return to this forum seeking help.

---

### Post by Bucky Ball on 2016-07-13
Welcome. Boot from install media, USB or disk, you will see a bunch of options, 'Try Ubuntu' 'Install Ubuntu', etc.

Choose 'Try Ubuntu'. That will get you to a desktop. There, you will either see a little window pop up saying 'Wireless networks available' or you won't. It might take a minute or two to pick things up.

If it doesn't pick up any wireless networks, then let us know and get back with the script output jeremy31 has requested. Thanks. (See the green link in my signature at the bottom of this post and put the output between code tags, please.)

(PS: Also, if it doesn't offer networks, click the network icon, don't worry, you'll see it when you're there, and see if there are any wireless networks listed there.)

(PPS: There are occasionally oddities. The wireless works in a 'live' session (running from install media) then not on a full install or vice versa. In that case, further digging is necessary sometimes, but see how you go this time before any of that. :))

---

