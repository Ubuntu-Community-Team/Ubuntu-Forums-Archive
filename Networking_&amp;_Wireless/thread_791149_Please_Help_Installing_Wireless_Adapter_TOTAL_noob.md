---
title: "Please Help Installing Wireless Adapter TOTAL noob with linux"
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by mechanicalmetal on 2008-05-11
Hey guys,

First off, I am sick an tired of Windows. Saying that name makes me spit fire. I am very eager to learn linux so I finally decided to install Ubuntu on my laptop that I use frequently. I decided that making Ubuntu work better than windows is my ONLY option as I have broken all of my windows cds. I am stuck now and linux is now my only option, and I will never go back! I don't care what it takes, I will learn linux or die trying.

First off before I go into a whole bio of my entire life, I am highly computer savvy, but when it comes to linux, im like a 75 yrold grandma that got her first computer yesturday. I can feel the basics, and I love the interface, I just want to make everything work. 

I ran a command under terminal to show a list of drivers installed on my laptop (cannot remember command) and I veiwed all drivers. Everythings their accept my wlan card! I am running a Toshiba Satellite a205-s5800 and I go to the toshiba webpage to search for wlan drivers for my system and it comes up with about 5 different models of wlan cards. DAMMIT I cannot remember for the life of me what brand of wlan I have in my computer. I wanted to get a rough estimate of what kind of card im running so that I can google search my driver for linux. I really need yalls help!!!!!! Please if you can, explain to me step by step what I need to do. I am very slow with linux and I get lost easy, lol.......

Also, I installed google earth and cannot find where the installed program is. (kinda tells you how much of a noob I am).

Your help is much appriciated and I look forward to hearing from you.


Take care guys!!!!!!!!!

---

### Post by ladr0n on 2008-05-11
Try ```
lspci | grep wlan
```
That should return all devices with "wlan" in their description.  

AFAIK most Toshiba laptops use Atheros wireless, which is usually pretty well supported by Linux.  If there isn't a Linux driver available for your chipset, however, you can use a windows driver through NDISwrapper.  I know there was a good tutorial for this on the forums a little while ago, I'm looking for it now.

---

### Post by mechanicalmetal on 2008-05-11
> **ladr0n said:**
> Try ```
lspci | grep wlan
```
That should return all devices with "wlan" in their description.  

AFAIK most Toshiba laptops use Atheros wireless, which is usually pretty well supported by Linux.  If there isn't a Linux driver available for your chipset, however, you can use a windows driver through NDISwrapper.  I know there was a good tutorial for this on the forums a little while ago, I'm looking for it now.

Yeah didn't come up with anything... gotta find the driver for it. I thank you so much and I would litterally buy you a drink for helping me right now.... 


THANKS!!!!

---

### Post by ladr0n on 2008-05-12
Do ```
lspci
``` and post the output here.  Figuring out which card you're using will help greatly

---

### Post by Ripfox on 2008-05-12
> First off, I am sick an tired of Windows. Saying that name makes me spit fire. I am very eager to learn linux so I finally decided to install Ubuntu on my laptop that I use frequently. I decided that making Ubuntu work better than windows is my ONLY option as I have broken all of my windows cds. I am stuck now and linux is now my only option, and I will never go back! I don't care what it takes, I will learn linux or die trying.


Can I put this in my sig? This is hilarious. I wish everyone came out of the gate with that kind of enthusiasm...:twisted:

---

### Post by HunterThomson on 2008-05-12
> **ripfox said:**
> Can I put this in my sig? This is hilarious. I wish everyone came out of the gate with that kind of enthusiasm...:twisted:

:guitar:

---

### Post by Six_Digits on 2008-05-12
Maybe using hardinfo you could find your card?

[http://ubuntuforums.org/showthread.php?t=788879](http://ubuntuforums.org/showthread.php?t=788879)

---

### Post by Ripfox on 2008-05-12
> **Six_Digits said:**
> Maybe using hardinfo you could find your card?

[http://ubuntuforums.org/showthread.php?t=788879](http://ubuntuforums.org/showthread.php?t=788879)

Hmmm...never knew that was in the repos. NICE!

---

### Post by mechanicalmetal on 2008-05-12
> **ripfox said:**
> Can I put this in my sig? This is hilarious. I wish everyone came out of the gate with that kind of enthusiasm...:twisted:

lol, yeah man... Feel free. Its the truth.

---

### Post by mechanicalmetal on 2008-05-12
im going to mess with this when I get home, please let me know if yall have any suggestions.

Thanks guys

---

### Post by Six_Digits on 2008-05-12
> **ripfox said:**
> Hmmm...never knew that was in the repos. NICE!

Just ran into it myself last night. Thought it would be good for this thread and possibly newer users intimidated by the command line.

---

