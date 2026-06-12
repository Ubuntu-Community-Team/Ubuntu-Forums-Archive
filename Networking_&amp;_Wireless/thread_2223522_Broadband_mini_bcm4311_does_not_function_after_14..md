---
title: "Broadband mini bcm4311 does not function after 14.04 upgrade. Dell"
date: 2014-05-11
forum: Networking &amp; Wireless
---

### Post by s9032g@comcast.net on 2014-05-11
Every time I do an upgrade the same ting happens. Old solutions don't seem to work. I an get online wired or by using a Edimax plug in, but noot with the built in Broadband. I would like an opinion before I make anything worse

Does this fix make sense??

first add this to your software repository (using synaptic for example)
deb [http://ftp.us.debian.org/debian](http://ftp.us.debian.org/debian) testing main contrib non-free

then do the rest in a root termin (sudo -s)


apt-get update
apt-get install module-assistant wireless-tools
m-a a-i broadcom-sta
echo blacklist brcm80211 >> /etc/modprobe.d/broadcom-sta-common.conf
update-initramfs -u -k $(uname -r)
modprobe -r b44 b43 b43legacy ssb brcm80211
modprobe wl


should be done :D

---

### Post by Hadaka on 2014-05-11
Hi, the commands have changed...they are...

```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo modprobe b44
```
then do
```
suo apt-get update
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
thanks.

and for next time..here is a cheat sheet how to -> [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by s9032g@comcast.net on 2014-05-11
Thanks. exactly what do I need to add to my software repository before I do the terminal commands. At the moment (without adding to the repository) all I get is "not found" responses. I am trying to use Synaptic to do this.

---

### Post by Hadaka on 2014-05-11
hi, open a terminal
ctl/alt/t....copy and paste the commands
one at a time...even if you get an error...do all the commands
I have never used synaptic or intend to..
...........................................................
ok...just for you i went into the ubuntu software center [Synaptic]
which i have no idea why it is called that, as i did not see any where
the word "Synaptic". However...both driver packages related to your
card are present..First..the correct dirver is   linux-firmware-nonfree
for your bcm4311 card. while that card is listed in the software center
broadcom-kernel-source and broadcom-sta-common ?  they are not correct
and the broadcom kernel source driver also black lists ssb and a couple other
dirver fields that are needed for your b44 ethernet driver. so...bottom line is
you can remove broadcom-kernel-source in the "Synaptic" center..but it wont
un blacklist ssb,,,,so you still need to use the terminal.....i hope i have not made
this more confuseing than it already is..good luck....use the terminal !!!
thanks.

---

### Post by s9032g@comcast.net on 2014-05-12
hi, open a terminal
ctl/alt/t....copy and paste the commands
one at a time...even if you get an error...do all the commands

I already did this before I asked about the repository. In each case I got message that the information was missing. HOWEVER I will do it again with great care and see what happens. I will let you know.

Some time back, when I attempted to move from 12.04 to 12.10 I had this same problem. It was never solved despite reams of advice. Eventually I went back to 12.04 and was fine until now.

This time I hope to solve the problem.

---

### Post by s9032g@comcast.net on 2014-05-12
HADAKA

  I did as you suggested again with no results. Here are the responses to each of the 6 command lines you suggested

1. unable to locate package bcmwl-kernel-source

2. cannot remove 'etc/modprobe.d/blacklist-bcm43.conf' no such file in directory

3. this one got no message and no action

4. this one does run at the end it says duplicate sources and suggests running apt-get update to resolve it???

5. unable to locate package

6. does nothing at all

---

### Post by Hadaka on 2014-05-12
Hi, if you are using the commands you posted from  some other source
they will not work...bcm4311 will not function with the wl driver.
please refer to the sticky at the top of the wireless page to verify
thanks. sorry i was unable to help you...GOOD LUCK

---

### Post by s9032g@comcast.net on 2014-05-12
I did look at the sticky earlier. My broadcom works out to 14e4:4315 (rev 1) which is not listed. looks like I am SOL

---

### Post by chili555 on 2014-05-12
> **s9032g@comcast.net said:**
> I did look at the sticky earlier. My broadcom works out to 14e4:4315 (rev 1) which is not listed. looks like I am SOLI always hesitate to step on toes but sometimes i am horrified by what I read and can't stop myself. More meds, maybe.

Of course you are not SOL. Hook up the ethernet. Open a terminal. Then do:```
sudo apt-get update
sudo apt-get install linux-firmware-nonfree
```Tell Hadaka the result as I am off to the pharmacy.

---

### Post by s9032g@comcast.net on 2014-05-12
chili 555.  You and Hadaka gave me this same advice when I had the same problem after upgrading from 12.04 to 12.10. Nothing ever worked then and it isn't working now. I am however grateful for the effort. 

I have done what you suggest and the results are much the same as stated earlier basically "Not Available"

---

### Post by s9032g@comcast.net on 2014-05-12
Once again I did the commands suggested.

The first does the update as requested.

The second command brings this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-firmware-nonfree

---

### Post by Hadaka on 2014-05-12
ok..this message..
---->>>E: Unable to locate package linux-firmware-nonfree                 
means you were not online. you were not online because you
removed module ssb and b44
so.. I will attempt to help you with this, an hopefully you can
get this going... please do..
```
sudo modprobe b44
sudo modprobe ssb
```
boot
**Connect the ethernet cable...then do..
```
ping -c3 8.8.8.8
```

***IF you can ping with no errors then while still connected with the ethernet cable
run the command chili555 and i have given you.
thanks.

---

### Post by s9032g@comcast.net on 2014-05-13
Good Morning Helpers!

    Over night I figured this out myself. It was not, in the end, either complicated or something that required any terminal commands.

     The solution goes back to my first query in this thread suggesting that enabling the necessary repository information was the key. Using the Ubuntu software called "Software & Updates" I checked off "Proprietary drivers for devices" (quite obvious really) and ran an update. Then, using the same  "Software & Updates" I checked for proprietary drivers and it found by Broadcom driver, saying it was"not in use". I put a check mark next to it, the necessary software was installed (note that this was all automatic i.e. no terminal commands on my part). 

    Now my built in wi-fi is operating like a champ.

     Thanks for sticking with me. You made me sure that there was a solution to be found.:)

---

### Post by Hadaka on 2014-05-13
Glad you were able to find a solution.
please mark this thread SOLVED
how to -> [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

