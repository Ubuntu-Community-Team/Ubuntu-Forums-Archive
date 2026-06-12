---
title: "disappearing wireless"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by Aisthesis on 2010-05-24
just installed ubuntu 10.04 clean, and now the machine doesn't see the wireless network. machine is a dell laptop (studio something or other), and the wireless connection switch is in the on position.
 
i tried manually configuring, using the settings from this (windows) machine, but still no connect.
 
any ideas?

---

### Post by TheUnwiseman on 2010-05-24
What kind of wireless card does your laptop have?  Does it see any other wireless networks besides your own?

---

### Post by Aisthesis on 2010-05-24
no, doesn't see any networks at all, but should see 3. checking on network card.

---

### Post by TheGnomeOfMetal on 2010-05-24
is your wireless card on? it sounds like it isnt.

---

### Post by Aisthesis on 2010-05-24
i'll bet it's the card. in trying to find out, i looked under hardware drivers and got the message that they're missing because i can't connect...

---

### Post by TheUnwiseman on 2010-05-24
First make sure that it is turned on in the BIOS.  If it is, I'm going to guess there's something wrong with the drivers for your wireless card.  I've got a Dell Studio 1537 laptop with a Broadcom wireless card, and when I tried out Karmic on a different hard drive, I had to disable the native driver and manually install Broadcom's driver.

---

### Post by Aisthesis on 2010-05-24
Broadcom BCM 4322 802.11a/b/g/n wireless LAN controller
 
that should be the relevant device, but also listed is Broadcom Netlink ... Gigabit Ethernet, which is presumably just my ethernet connection port.

---

### Post by Aisthesis on 2010-05-24
yeah, i think we have the same laptop. i'll double check BIOS (still F2 with ubuntu like windows?).
 
do you think i could download the driver on my windows machine, then put it on my flash drive to get it over to the linux machine?

---

### Post by TheUnwiseman on 2010-05-24
Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller

That's mine too!  Exact same one.  Let me see if I can find you the link to their proprietary drivers...

Edit:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
There you go.  You'll also need to disable the current driver.  I think there's an archived thread on this somewhere in the forum.  Let me look for that, too.

---

### Post by Aisthesis on 2010-05-24
yes, all the wireless settings are enabled in the BIOS

---

### Post by Aisthesis on 2010-05-24
will my ubuntu 10.04 install be 64-bit or 32-bit? it didn't ask me, so it just installed the way i got it. or, in case of doubt, where do i go to see whether i'm 64- or 32-bit in linux (sorry, still very new to navigating it)?

---

### Post by TheUnwiseman on 2010-05-24
I don't quite remember where the driver settings are in 9.10/10.04 (I'm still using 9.04).  Maybe someone who has a little more experience can help us out?

I know that you'll want to add the old driver to the blacklist in /modprobe.d and, after doing a make install of the new driver, set up a startup script in /init.d to enable the good driver every time you boot.

---

### Post by Aisthesis on 2010-05-24
sigh, just running the downloads under the link you gave won't do the trick?
 
in any case, how do i determine whether i'm 32-bit or 64-bit? broadcom does say that's important to know? (i was running 64-bit windows 7 before, if that has any significance, although it really shouldn't since i did a clean wipe)

---

### Post by TheUnwiseman on 2010-05-24
> **Aisthesis said:**
> will my ubuntu 10.04 install be 64-bit or 32-bit? it didn't ask me, so it just installed the way i got it. or, in case of doubt, where do i go to see whether i'm 64- or 32-bit in linux (sorry, still very new to navigating it)?

You can type:
```
uname -m
```
into your terminal to find out. If it's got '64' in what it prints out, you're running 64-bit.  I'm running 32-bit, and I get back i686.

---

### Post by Aisthesis on 2010-05-24
yeah, i get back i686, too.
 
when i look under system monitor, i see T6400, though, for both processors, and then ext4 for the file system...
 
but you're sure that means 32-bit?

---

### Post by TheUnwiseman on 2010-05-24
Unless the guide I read told me wrong.  And T6400 is just the model of the CPU.  It bears no effect on whether it's 32-bit or 64-bit.  It just so happens to be 64-bit.  But you *installed* 32-bit Ubuntu.  That's what is important.

---

### Post by TheUnwiseman on 2010-05-24
Found the original lines of code I was looking for!

[http://ubuntuforums.org/showpost.php?p=7191219&postcount=3](http://ubuntuforums.org/showpost.php?p=7191219&postcount=3)

"wl" is the driver you'll need to black list, and get your computer to modprobe b43 and ssb on startup.

---

### Post by Aisthesis on 2010-05-24
ok, i'm surprized that a new release of ubuntu is 32-bit, but i'll just do it that way. so, i've got the driver, and installed it (actually tried both and rebooted). no change.
 
so, what do i do next?

---

### Post by Aisthesis on 2010-05-24
when i type in 'blacklist wl' in the terminal, i get the message 'command not found'

---

### Post by Aisthesis on 2010-05-24
in etc/modprobe.d/ there are 7 different blacklist files: blacklist.conf (probably the one to use?), blacklist-ath_pci.conf, blacklist-watchdog.conf, etc.

---

### Post by Aisthesis on 2010-05-24
moreover, when i try to edit blacklist.conf, it tells me that i don't haved the necessary permissions, hence can't edit ... :(

---

### Post by TheUnwiseman on 2010-05-24
Sorry, I just took a big nap.  Yes, blacklist.conf is the one you want to edit.  You'll want to edit it from the command line:
```
sudo gedit blacklist.conf
```
or, if you prefer vim:
```
sudo vim blacklist.conf
```

---

### Post by Aisthesis on 2010-05-25
well, in the meantime, i thought i'd try fedora, but i'm still having the same problem. so, i thought i'd check back here for ideas.
 
here's where i'm at so far:
 
1) enter 'blacklist wl' in the file blacklist.conf
2) get the driver at the link you gave.
 
then how do i go about installing the good driver?
what exactly do you mean by modprobe-ing something or other?
 
i've never used linux at all before, so i really need detailed instructions.

---

