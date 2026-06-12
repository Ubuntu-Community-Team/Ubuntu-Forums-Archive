---
title: "wireless problems"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by squire_uk on 2009-02-08
Hi, brand new to ubuntu, just managed to get it insalled tonight, & can't connect to my wireless internet connection.

I'm running it on a dual boot system laptop.

the intel wireless thingy (my technical term should show you my level of experience) seems to be working fine, as soon as it logged on it started searching for available networks in range, it found 2, but didn't see mine.

I've tried creating a new wireless network, but it isn't working, even when the laptop is closer to the netgear router.

one thing I'm thinking is, the wireless security, gives the choice of WEP 40/128-bit Key my wep key is 64-bit (has to be 64-bit, for the wii to connect to the network.)

is that part of my problem?

---

### Post by halitech on 2009-02-08
one thing to check on your router, is it set to not broadcast the SSID?

---

### Post by squire_uk on 2009-02-08
no it's set to broadcast that..... it doesnt matter where i am in the house, i get somebody elses coming into range as I move around, so I know it's finding them, but it isn't finding mine.

my ssid is 1234bethan, the one time i moved upstairs, (to where the router is) it found "netgear" - which is the make of my router, could that have been mine? couldn't connect to it tho, and now that one isn't popping up....

---

### Post by ugm6hr on 2009-02-08
> **squire_uk said:**
> the intel wireless thingy (my technical term should show you my level of experience) seems to be working fine, as soon as it logged on it started searching for available networks in range, it found 2, but didn't see mine.

Assuming you are in the UK, and do, in fact, have an Intel wifi card, and are using Intrepid - this might be the problem:
[http://www.ubuntu.com/getubuntu/releasenotes/810#Only%20US%20wireless%20channels%20enabled%20by%20default%20on%20Intel%203945](http://www.ubuntu.com/getubuntu/releasenotes/810#Only%20US%20wireless%20channels%20enabled%20by%20default%20on%20Intel%203945)

Other possibilities:
Your wifi shares a channel with a neighbour's.
Hidden SSID (unlikely - given you expect it to be found - so presumably Windows finds it OK).

EDIT: No - Netgear is not yours - it will appears as your SSID only

---

### Post by halitech on 2009-02-08
is your SSID 1234bethan or is that your password to acquire an IP address? Since you are picking up other routers we should be able to safely assume the wireless card is working properly.

---

### Post by squire_uk on 2009-02-08
Wireless Network  
Name (SSID):   1234bethan
Region:  Europe 
Channel:  13
Mode:  g & b

Wireless Access Point 
(ticked) -  Enable Wireless Access Point  
(ticked) -  Allow Broadcast of Name (SSID)  




WEP Security Encryption 
Authentication Type:   Automatic
Encryption Strength:   64 bit 
WEP Key 
      
Key 1:  ********** < (i've got the key, just blanked it out here)

---

### Post by squire_uk on 2009-02-08
there's a few wireless networks in the houses around me, all encrypted.

in my house, we've got a vista laptop, my old desktop, our wii, and even my new phone that can find and access the connection, after typing in the wep key.

the laptop ive just installed ubuntu on was once connected to it as well via XP pro, after a few problems, i removed everything, re-installed windows, and just use it for Cubase. the idea being i can still get online on it when need be by using ubuntu.

can't really be the channel issue, as no probs on the other computers using it.

---

### Post by ugm6hr on 2009-02-08
> **squire_uk said:**
> Wireless Network  
Name (SSID):   1234bethan
Region:  Europe 
**Channel:  13**
Mode:  g & b

As I suspected.  From my earlier link

> To work around this, add the following line to the /etc/modprobe.d/options file if you use this driver and need to use European wireless channels:

```
options cfg80211 ieee80211_regdom=EU
```
So:

```
sudo cp /etc/modprobe.d/options /etc/modprobe.d/options.bkp
gksudo gedit /etc/modprobe.d/options
```

Add at bottom of this file (and then save):
```
#Add European wifi channel support for Intel chipsets
options cfg80211 ieee80211_regdom=EU
```

Then reboot.

---

### Post by squire_uk on 2009-02-08
ok cheers, I couldn;t see the relevent bit in your link earlier, so got a bit lost, that;s why i posted all the info from the router.

I'll give the code thing a go in a sec an let you know how i do, I'm not used to changing/messing with computers, to me they're like cars, I know how to drive 'em, don;t know how to fix 'em....

thanks for helping.

---

### Post by squire_uk on 2009-02-08
rite, sorry for being a total nnob, can't help it.

squire@ubuntu:~$ sudo cp /etc/modprobe.d/options /etc/modprobe.d/options.bkp
gksudo /etc/modprobe.d/options

cp: target '/etc/modprobe.d/options' is not a directory

nnob/ noob/ nob - all amounts to the same! :)

---

### Post by halitech on 2009-02-08
did you try running both commands at the same time or 
```
sudo cp /etc/modprobe.d/options /etc/modprobe.d/options.bkp
```
then
```
gksudo /etc/modprobe.d/options
```

---

### Post by ugm6hr on 2009-02-08
I've re-edited the post - sorry my mistake - missed a word.

It's gksudo **gedit**...

Try it again.

Remember it's one line at a time (press Enter at the end of each line - if it asks for a password, enter your Ubuntu password)

---

### Post by halitech on 2009-02-08
> **ugm6hr said:**
> I've re-edited the post - sorry my mistake - missed a word.

It's gksudo **gedit**...

Try it again.

Remember it's one line at a time (press Enter at the end of each line - if it asks for a password, enter your Ubuntu password)

d'oh, missed that as well

---

### Post by squire_uk on 2009-02-08
hi, halitech & ugm6hr......

thankyou much, I'm now online on my ubuntu laptop, after the reboot, it found my connection straight away. cheers again.

---

### Post by ugm6hr on 2009-02-08
No problem.

It's unfortunate that the Intel driver developers decided to default to US channels only.

Welcome to Ubuntu.

---

