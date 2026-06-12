---
title: "I'm trying"
date: 2010-09-28
forum: New to Ubuntu
---

### Post by Timboshenko on 2010-09-28
Hey..one day I had the bright idea to try ubuntu on my mini-9. I have never liked xp on the netbook because it was taking up too much space. I also like the idea of learning to do things myself and gaining some knowledge.I installed ubuntu 10.4 and the book will not pick up any networks in the area so now I can't connect at all with the mini. I have tried many things and nothing works.The fn 2 key doesn't work and the tilde is also on a fn key and it doesn't work either. I really want to use ubuntu but this has been very challenging. any ideas?

---

### Post by Magnavox on 2010-09-28
connect your mini to a LAN cable, so you have internet, then 

sytem/admin/hardwaredrivers

it should prompt you to install wireless drivers

---

### Post by Megaptera on 2010-09-28
Have you tried this? It says Karmic but also works on Lucid 10.04. Don't forget the reboot step.

[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

Hope this helps

---

### Post by Timboshenko on 2010-09-28
Magnavox, my hardware drivers icon has a lock on it. Is this normal? and what should I do?

---

### Post by Rubi1200 on 2010-09-28
See the post above by Megaptera.

---

### Post by Timboshenko on 2010-09-28
> **Magnavox said:**
> connect your mini to a LAN cable, so you have internet, then 

sytem/admin/hardwaredrivers

it should prompt you to install wireless drivers

Magnavox, thanks for the reply. My hardware drivers icon has a lock on it. is this normal?

---

### Post by lswartz on 2010-09-28
A little gold lock on what looks like a green PCI card??? Mine does too & yes it is normal.

---

### Post by Timboshenko on 2010-09-28
> **lswartz said:**
> A little gold lock on what looks like a green PCI card??? Mine does too & yes it is normal.
I click on this icon and nothing happens.

---

### Post by lswartz on 2010-09-28
I get 'Searching for available drivers' but it takes a little while to start.

---

### Post by Timboshenko on 2010-09-28
> **Timboshenko said:**
> I click on this icon and nothing happens.
I just retried and the icon worked this time. It scanned and then gave a message 'proprietary drivers not in use on this system. The ethernet was connected during this scan.

---

### Post by Rubi1200 on 2010-09-28
Guys, someone kindly posted a possible solution; at least take a look!
[http://ubuntuforums.org/showpost.php?p=9900986&postcount=3](http://ubuntuforums.org/showpost.php?p=9900986&postcount=3)

---

### Post by Timboshenko on 2010-09-28
> **Timboshenko said:**
> I just retried and the icon worked this time. It scanned and then gave a message 'proprietary drivers not in use on this system. The ethernet was connected during this scan.
I have tried everything on this thread and am getting nothing. I think I'll try starting from scratch and making a new install cd and redoing the os. Thanks for your input.

---

### Post by lswartz on 2010-09-28
> **Timboshenko said:**
> I just retried and the icon worked this time. It scanned and then gave a message 'proprietary drivers not in use on this system. The ethernet was connected during this scan.

I'm glad you got it working. Mine found the propriety drivers once I connected to the Internet (as I recall). Since yours does not, Rubi1200 has posted a good link for you *tips hat to Rubil1200*.

---

### Post by lswartz on 2010-09-28
> **Timboshenko said:**
> I have tried everything on this thread and am getting nothing. I think I'll try starting from scratch and making a new install cd and redoing the os. Thanks for your input.

Gee :(. I just saw this after I posted. Maybe you should get the Ubuntu updates first. I remember getting them via Ethernet & then getting the broadcom driver.

---

### Post by Timboshenko on 2010-09-30
> **lswartz said:**
> Gee :(. I just saw this after I posted. Maybe you should get the Ubuntu updates first. I remember getting them via Ethernet & then getting the broadcom driver.I did everything from scratch and still nothing. I've tried everything on this thread. Some of the things seem to require internet connection and I can't even connect on ethernet. I don't know how to install things from the pen drive etc. I read somewhere that I could have a problem with my airplane mode being deactivated and Ubuntu can't activate it. My xp is gone. I should have installed side by side but I didn't. I'm going nuts finding my router numbers etc. but I get the feeling it shouldn't be this hard. I'm out of ideas.

---

### Post by hekastos on 2010-09-30
I just stumpled in here, but did you see this =>

Currently the proprietary “wl”  driver by Broadcom works best (see notes). b43 kernel module doesn't  seem to work (yet). Ndiswrapper + Windows driver is also an option.

The proprietary 'wl' driver is not (and will never be) part of the  mainline kernel. Check your distribution's repository if you can find it  there, otherwise you can use my [self-explaining shell script]("http://p173.de/f/build_and_install_broadcom_wl.sh") which will apply a patch from Ubuntu, build and install the module.

[found here]("http://www.linlap.com/wiki/dell+inspiron+mini+9")

---

### Post by lswartz on 2010-10-01
> **Timboshenko said:**
> I get the feeling it shouldn't be this hard.

You are right, it shouldn't be. 

At one time you were able to connect to the Internet via Ethernet cable. Does your Ethernet still work & can you get the updates using update manager?

---

### Post by Megaptera on 2010-10-01
> **Rubi1200 said:**
> Guys, someone kindly posted a possible solution; at least take a look!
[http://ubuntuforums.org/showpost.php?p=9900986&postcount=3](http://ubuntuforums.org/showpost.php?p=9900986&postcount=3)

Have you tried this?

---

### Post by Timboshenko on 2010-10-02
> **Megaptera said:**
> Have you tried this?

yes I tried both of these and still nothing.Someday, maybe not today and maybe not tomorrow, I will have Ubuntu on my netbook. I need to free myself from the tyranny of Windows and take control of my own netbook.

---

### Post by Timboshenko on 2010-10-03
> **Timboshenko said:**
> yes I tried both of these and still nothing.Someday, maybe not today and maybe not tomorrow, I will have Ubuntu on my netbook. I need to free myself from the tyranny of Windows and take control of my own netbook.I have a few files in my home folder but nothing is working with them. One is a tar gz file that if i try to extract it's greyed out. then I try putting stuff in the terminal and errors occur. It's a mess. Plus I'm an idiot. not a good mix

---

### Post by Guilden_NL on 2010-10-03
Timboshenko,
Might I suggest that if you have tried a suggestion, that you post that you have done so, along with the results?

I stumbled across this thread and you're ignoring several people that reached out to you and offered suggestions.

For instance someone posted a suggestion, you didn't mention it, then Rubi1200 highlighted this, and you didn't mention it, and it finally took Megaptera asking yet again until you stated that you tried it.

Have you tried hekastos' suggestion?

When people see suggestions apparently being ignored, they are reluctant to step in.  I was going to just skip over your thread and let you hang, but decided to help you by pointing out that your ignoring suggestions is hurting your chances of getting additional help.

---

### Post by Timboshenko on 2010-10-03
> **Guilden_NL said:**
> Timboshenko,
Might I suggest that if you have tried a suggestion, that you post that you have done so, along with the results?

I stumbled across this thread and you're ignoring several people that reached out to you and offered suggestions.

For instance someone posted a suggestion, you didn't mention it, then Rubi1200 highlighted this, and you didn't mention it, and it finally took Megaptera asking yet again until you stated that you tried it.

Have you tried hekastos' suggestion?

When people see suggestions apparently being ignored, they are reluctant to step in.  I was going to just skip over your thread and let you hang, but decided to help you by pointing out that your ignoring suggestions is hurting your chances of getting additional help.Sorry about the ignorance of the protocol. I thought I posted that I tried all of the suggestions and had no success. I didn't know I had to put something up for each entry. Thank you all for your help.

---

