---
title: "RT61 install, now locking up"
date: 2006-11-16
forum: Networking &amp; Wireless
---

### Post by wekebu on 2006-11-16
Hi,
Here goes another wireless problem...

I started out with Breezy, upgraded to Dapper.  Everything was fine until I decided to get a router.  After reading several recommendations, I got the Linksys router WRT54G v6 ( ralink RT61 ) and the WMP54G V4.1. That was a week ago and I've spend countless hours trying to get the wireless set up.  Wired works great.  I used the directions on [http://www.ubuntuforums.org/showthread.php?t=132980&highlight=rt61+solved]("http://www.ubuntuforums.org/showthread.php?t=132980&highlight=rt61+solved")
and got the wireless to work!  Then, I tested to see if it would continue to work after a shutdown. Nope. Now, I get the brown screen of death. I do ctrl alt F1 and get to the terminal (sorry if that's not the correct term) and log in.  That part works every time. At first I tried to gedit /etc/network/interfaces but it never listed the contents of the file, only just sat there, blank & locks up. I ended up rebooting. Now, several attempts later, commands are acting flakey. One time I can cd into /etc/network another time it just sits.  I must have done something incorrect.  Is there any hope at this point?  I'm not against doing a fresh install of Dapper. I don't have anything on this machine that needs saving.

Fyi, two desktops: one Windows XP wired, one Ubuntu trying to go wireless.  Using a DirecWay / HughesNet DW6000 modem for pitiful broadband, but no other choices.)

Wendy

---

### Post by wekebu on 2006-11-17
Okay, could it be that I'm only having a problem with sudo commands?  I gotta say, I'm in the best shape of my life trottin' back and forth between machines!

Wendy

---

### Post by wekebu on 2006-11-17
Please disregard my questions, I'm doing a fresh install.  The experience of reinstall codecs will be fun, right?](*,)

---

### Post by raydekok on 2007-02-10
did it work?

---

### Post by lukew on 2007-02-28
> **wekebu said:**
> Please disregard my questions, I'm doing a fresh install.  The experience of reinstall codecs will be fun, right?](*,)

Hay,

I am having the same problem to under Edgy.

Under Dapper My Linksys USB with ndswrapper was the root cause of my unstable system. I moved to PCI D-Link and everything went back solid. (Passphrase had to be hex and not asci and all but my wireless card had to be commented out in my network interfaces - with out these I would often lock up on bringing the interface up)

Upgraded to Edgy a few weeks ago and last weekend moved back onto wireless from eth0. Having   a nasty experience. 

From looking at threads people seem to be struggling with this card in the new kernel ( i am on .10) , even after reinstalling the restricted modules to make it working they are experiencing lock ups.

Let us know how you get on but i doubt a fresh install will do the trick.

Luke

---

