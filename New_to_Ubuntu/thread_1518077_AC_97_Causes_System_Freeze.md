---
title: "AC 97 Causes System Freeze"
date: 2010-06-26
forum: New to Ubuntu
---

### Post by sathiskumarmsk on 2010-06-26
I am using Sony Vaio Laptop with 512MB ram.The problem is whenever i try to use internet, the system will freeze within around 10 minutes.If i dont use internet it works fine for hours.So i thought IPV6 is the problem.So i disabled it.But the system freeze continued.Then i turned off DHCP.no use.The processor or ram usage never goes above 50% at the time of freezing. From the system log  the last Log message is as follows

**Ac'97 doesnt respond: RESET**

As for as i know ac97 is sound related(correct me if i am wrong).Why it causes problem while i am using internet(PS:im not playing any youtube video or flash).

At the time of booting ubuntu gives one error message.

**AC'97 1 access is not valid [0xffffffff], removing mixer**

Inspite of that error message the system boots fine.

Is there any solution to fix this?..
May be the following bug is related to what i am posting here.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/576511]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/576511")

---

### Post by mapes12 on 2010-06-26
How is your machine set up? That is, are you dual booting with Ubu on its own partition and windoze (or whatever) on another, running Ubu inside Wubi, clean install with just Ubu on the HDD or some kind of virtual environment?

---

### Post by sathiskumarmsk on 2010-06-28
> **mapes12 said:**
> How is your machine set up? That is, are you dual booting with Ubu on its own partition and windoze (or whatever) on another, running Ubu inside Wubi, clean install with just Ubu on the HDD or some kind of virtual environment?
Yes..i am dual booting with Ubuntu on its own partition..And My assumption was wrong.AC 97 isnt the audio codec..It is Agere Systems AC'97 Modem..The kernel log says the modem doesnt respond.I removed Ubuntu and installed RHEL 5.1(using kernel 2.16.8) and now its working fine without any niggles.Is it kernel related bug?..Or ubuntu related bug?.. Is there any fix available?..

---

