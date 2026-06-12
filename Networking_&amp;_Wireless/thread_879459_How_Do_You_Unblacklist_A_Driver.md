---
title: "How Do You Unblacklist A Driver"
date: 2008-08-04
forum: Networking &amp; Wireless
---

### Post by super_nerd on 2008-08-04
Hi,
     I just swichted over from Windows to Ubuntu last week[and am a complete noob to linux and most things beyond basic computer using]. Unfortunately at the time I didn't know that there weren't any drivers for the wireless USB network card I was using at the time so I did some research and, after some difficulty, managed to installed ndiswrapper the right Windows driver but for some reason could not get the driver to realize the hardware was on my computer and to use the network card with that driver. The point of all this is that when I was in the process of doing the above I read somwhere that I should blacklist all my other network card drivers so they don't interfere with my Windows driver(I did this by typing some wierd command that I don't remember or understand, but it repeated the same thing for each of the drivers I blacklisted and had the word modprobe, I think). However I recently got an RTL8151 pci card from a friend for cheap and put that in on my motherboard(I know it's in right becuase I can find it using the command lspci) however becuase all my drivers are blacklisted I can't use my new card, which I think has a Linux driver. Can someone please tell me either:

a)how to unblacklist the driver I need for my **RTL8151 pci card**
b)where to get a driver for the pci card that will work(I have Hardy Heron)
c)how to get my windows driver for my usb card to use the card
d)if there is some other solution
e)all of the above

I apologize if this is a stupid question, I am unclear/inarticulate, or the solution is really obvious and it is idioticly stupid that I haven't figuerd it out yet, but I am only fourteen and still getting over the learning curve of Ubuntu.

If anyone has any answers or advice I would greatly appreciate it.

Thanks,
super_nerd(mabye it should be super_noob instead)

---

### Post by cariboo on 2008-08-04
To edit blacklist open a text editor as root and delete the entries you made like this:

```
gksu gedit /etc/modprobe.d/blaclist
```

Jim

---

### Post by epiphonygirl on 2008-08-04
Lets get what you want to do straight first, you need to...
a. unblacklist a wireless driver (usb, right)
b. find the windows driver to install with ndiswrapper
c. and how to get your usb driver for your usb wireless card to
   be recognized.

answers:

A. to unblacklist a driver you need to know what the driver is first which I assume that you know or have some inkling of what it is. So open up terminal and type in 
```
sudo gedit /etc/modprobe.d/blacklist
```
This should open a window with a list of drivers that are blacklisted, now all that you need to do is look for the driver that you blacklisted and delete the entry for it.

i.e.
if it is listed as
"blacklist ath_pci"
then just delete it so that it is no longer there then save the file and restart.

B. If your friend gave you a driver disk with that card then I would use the one off of that. Otherwise you can just download the windows driver and then search for the appropriate .inf or sometimes .INF file located in one of the folders. This is the file that you will use, you may need to use the windows 2000 driver instead of Xp to make it work.

C. Make sure that the other wireless drivers are blacklisted and that the one that you install is not otherwise it should in theory use the card.

D. if you this does not work you can always look into using madwifi possibly depending upon your card and the card's drivers. However, I would try to work it out with ndiswrapper first.

---

### Post by super_nerd on 2008-08-05
Hi,
 I typed the command you gave me but unfornuately I can't find any of the drivers I blacklisted, only ones already blacklisted by default, and I have no idea what driver I need either, which probably means I didn't succeed in blacklisting them do to a typo or something. I thought just about every pci card was supported by Linux but mabye RTL8151 is one of the few that doesn't. If this is the case I guess I should try to find a Linux driver or Windows driver and try using ndiswrapper. But I already used ndiswrapper on my usb card and got it installed but when I type: ndiswrapper -l, it says the driver is there but not hardware(the usb card) even when its plugged in. I'd rather get the usb card to work becuase the driver is already installed and then find the pci driver on my own computer once I have internaet access from it again.
So how do I get my usb card to use the driver I already have installed?
Thanks for the previous info.

---

### Post by dmizer on 2008-08-06
It will really help if you can determine what command you used to blacklist the drivers.

Fortunately, there is a log of the commands you use in the terminal. Take a look in your bash history with this command:
```
gedit ~/.bash_history
```
Look through the file and see if you can find the command you used to blacklist the drivers.

---

### Post by super_nerd on 2008-08-11
Hi,
   It's me again. I got my pci card working by using ndiswrapper on the Windows driver(It turns out I did not blacklist the driver I needed like I originally thought I did) and my problem is fixed. Thank you all for responding to my question. Unfortunately, I am afraid I wasted some of your time because learning how to unblacklist a driver did nothing to solve my problem except narrow out one of the possible causes. However, I did learn something that might come in handy someday. Once again, thank you for answering my (somewhat dumb)question so well and being so patient. I will try to avoid having to post more dumb questions in the future so as not to wast other peoples time.

Thanks,
super_nerd

P.S. Sorry for not saying this when I got my driver working last week but I've been really busy and it slipped my mind.

---

