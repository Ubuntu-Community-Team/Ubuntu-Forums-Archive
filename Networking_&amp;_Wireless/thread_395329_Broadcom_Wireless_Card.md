---
title: "Broadcom Wireless Card"
date: 2007-03-28
forum: Networking &amp; Wireless
---

### Post by doppely on 2007-03-28
Hi!
I am right doing the exciting step of trying xubuntu, and I would like to eventually switch completely (from winXP). There are two things that are keeping me from it, however, one minor and one major:
Minor: There is a game I like playing, Spring TA. I don't know if I could run it on xubuntu, but that is as I said just a minor thing I could easily live without.
Major: The bigger problem for me is that my wireless network card doesn't seem to be working. It has a little orange/blue indicator to show if it is activated, and when I try the xubuntu CD it doesn't show its working. I am afraid the OS doesn't recognize the wireless network card. What can I do? 

Here is the computer I am using:
Compaq Presario V6101US Notebook PC.

Unfortunately, all I could find about the wireless network card in windows was that it is a Broadcom network card.

Can someone help me?
- Joshua Moore.

---

### Post by bmt on 2007-03-28
Yes, it's possible to get the Broadcom card working.  Have a look [here]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)") for a sample.

The procedure is quite easy to do -- it looks more complicated than it really is.

---

### Post by itzpapalotl on 2007-03-30
Ya know, It's very very likely that you are running the bcm43xx firmware on your Broadcom card. I had a degree of luck with my HP nx9600 WITHOUT using ndiswrapper, by following the directions found here:
[http://designedfor.wordpress.com/2007/03/20/finally-wireless-broadcom-43xx-solution/](http://designedfor.wordpress.com/2007/03/20/finally-wireless-broadcom-43xx-solution/)
It's outside the stadndard Ubuntu forums, so use with caution, but it worked for me, and I'll becha it's the same internal card.

You may still have a fiddley time with your fiddley switch button, which can be... fiddley.
Good luck! If you get it working report back!

---

### Post by Floppyjoe on 2007-03-30
> **doppely said:**
> Hi!
I am right doing the exciting step of trying xubuntu, and I would like to eventually switch completely (from winXP). There are two things that are keeping me from it, however, one minor and one major:
Minor: There is a game I like playing, Spring TA. I don't know if I could run it on xubuntu, but that is as I said just a minor thing I could easily live without.
Major: The bigger problem for me is that my wireless network card doesn't seem to be working. It has a little orange/blue indicator to show if it is activated, and when I try the xubuntu CD it doesn't show its working. I am afraid the OS doesn't recognize the wireless network card. What can I do? 

Here is the computer I am using:
Compaq Presario V6101US Notebook PC.

Unfortunately, all I could find about the wireless network card in windows was that it is a Broadcom network card.

Can someone help me?
- Joshua Moore.
To find out more about your wireless card type the following command into the terminal:
```
lspci
```
and look for the broadcom line.
There is a great howto in the tutorial section of this forum on how to install VMware server and Windows. If "Spring TA" is a windows program you should probably be able to get it working there(but I'm not totally positive).

---

