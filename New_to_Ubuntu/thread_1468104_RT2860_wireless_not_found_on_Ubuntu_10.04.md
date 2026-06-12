---
title: "RT2860 wireless not found on Ubuntu 10.04"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by kajjot on 2010-05-01
Hi

I just moved from XP to ubuntu on my netbook.
I have MSI Wind U130 with Ralink RT2860 Wireless N adapter.
I have installed the source package from debian.org ([http://packages.debian.org/sid/all/rt2860-source/download](http://packages.debian.org/sid/all/rt2860-source/download))
But i still have no wireless devices found.
Prior to this i tried the ndiswhatever it's called (windows drivers)
It found my wireless but in RutlIT it said adapter "down" and if i clicked on it to enable it i just gor error.

Please help. :)

---

### Post by clhsharky on 2010-05-01
HI kajjot

Known problem, I don,t have that card, but please
Search this forum for 'RT2860' you will find many threads.

Sharky

---

### Post by kajjot on 2010-05-01
After 2 days of frustration i've put windows 7 on it :D
Sorry

---

### Post by Naggobot on 2010-05-01
There are multiple bugs reported for RT2860 in the[ launchpad]("https://bugs.launchpad.net/bugs/+bugs?field.searchtext=rt2860&search=Search+Bug+Reports&field.scope=all&field.scope.target="). Check if your problem is specifically one of those already there.

Edit: Sorry, I was searching through launchpad while you posted. Good if everything works now.

---

### Post by clhsharky on 2010-05-01
HI kajjot

Your first post was 1 hr, ago don,t give up so easy. You will learn a lot from this experience. I,m not saying to give up W7,I still have a MS partition. I payed for it i'm going to use it to my benefit, that said my OS of choice is Ubuntu.
It is all about choice.

Sharky

---

### Post by ctbarker32 on 2010-05-01
Hi. 

I have written up a tutorial specifically aimed at getting the Ralink RT2860 chipset working with wifi, WPA security, and Ubuntu 10.04. I think I have made it understandable for the novice. I am not a Linux expert by any means so that's where I'm coming from. 

Hope this helps.

[RT2860 and Ubuntu 10.04 wireless tutorial]("http://www.ctbarker.info/2010/05/ubuntu-1004-wireless-chipsets-and-wpa.html")

-CB

---

### Post by RyanBFS on 2010-05-01
Yah I wish I hadn't given up the first time I'd looked into linux... Try and Dual boot for a while, Ubuntu can read windows ntfs partitions so you'll still have access to anything that you do on your windows partiton. [http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony]("http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony") 

lots of tutorials on it, and 10.4 is only a few days old so driver specific problems will be worked out.  Theirs a lot of hardware out there and the manufacturers make the drivers _for_ windows. I remember when win 98 came out and a good chunk of my computers couldn't shut down for a year :)

---

### Post by dmp1ce on 2010-05-03
> **ctbarker32 said:**
> Hi. 

I have written up a tutorial specifically aimed at getting the Ralink RT2860 chipset working with wifi, WPA security, and Ubuntu 10.04. I think I have made it understandable for the novice. I am not a Linux expert by any means so that's where I'm coming from. 

Hope this helps.

[RT2860 and Ubuntu 10.04 wireless tutorial]("http://www.ctbarker.info/2010/05/ubuntu-1004-wireless-chipsets-and-wpa.html")

-CB
It helps!  This fixed my problem.  I had to do the same thing back in 9.04 but the steps are slightly different now.

---

### Post by agm. on 2010-05-12
Hi, 

The blog post really was very helpful in trying to fix the problem, but before I go about trying to do it that way, I was wondering something.

I just "upgraded" from 9.04 -> 9.10 -> 10.04

As I was updating, I saw that 9.10 immediately saw and loaded my wireless network and that gave me hope that it would work similarly in 10.04.  (I figured if I was upgrading, I might as well do it to the latest release).

The netbook dual boots and basically, I have been having to use the Windows partition pretty heavily because in 9.04 the lack of wifi (in a password protected environment).

While the instructions are really nice, I saw in one of the comments that someone offered the following sollution:

> 
sudo apt-get install linux-backports-modules-wireless-karmic-generic
The problem is that when I type this into terminal and enter my password, I get an error saying that it cannot find that package.

Is there some step that I am missing?  I think this would fix the problem and would be an easier fix (if it works).

Any suggestions?

Thanks!

---

### Post by bgiannes on 2010-05-18
i found that i needed to have the dat file in place for the ra2860 to work see this link


[http://ubuntuforums.org/showpost.php?p=8346399&postcount=9](http://ubuntuforums.org/showpost.php?p=8346399&postcount=9)

---

