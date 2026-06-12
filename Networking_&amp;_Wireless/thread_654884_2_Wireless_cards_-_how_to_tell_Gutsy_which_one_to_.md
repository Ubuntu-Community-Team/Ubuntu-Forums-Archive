---
title: "2 Wireless cards - how to tell Gutsy which one to use"
date: 2007-12-31
forum: Networking &amp; Wireless
---

### Post by jellytree on 2007-12-31
Hi all, I've searched other posts and couldn't find an answer to my question. Some others have asked similar questions, but none have had answers given.

I have a notebook with a built-in wireless adapter which is working with ndiswrapper (bcm43xx).  I also have a USB wireless adapter (marvell) that I have installed and is working using ndiswrapper as well. What I am looking for is is a way for me to tell the system which adapter i want to use:

[B][INDENT]1) an icon to be placed on the desktop which will disable the broadcom adapter and enable the usb adapter. 
2) an icon to be placed on the desktop which will enable the broadcom adapter and disable the usb adapter.[/INDENT][/B]
I am a noob when it comes to linux -- surprised that I managed to get both cards working, but I think it has a lot to do with Gutsy as I lost a lot of hair with Feisty.  I have no clue about scripts and such, though I'm pretty sure that is what I need.  I will post any additional information required.
Thanks in advance for your time.

---

### Post by teryowen on 2007-12-31
not sure if this will work but hey give it a try, make 2 bash scripts with the following:

```
sudo ifconfig eth0 down
sudo ifconfig eth1 up
```

and the second one
```
sudo ifconfig eth1 down
sudo ifconfig eth0 up
```

try that out might work. i useally run my scripts in terminal so i dont know how its gonna actually work of gui interms of the password prompt but should work

Also change eth1 and eth0 accordingly to wat ever your devices are. (it can be en0 ath0 wifi0 can be alot of stuff)

EDIT:

Oh and once you creat these files chmod them 700 through terminal so:

chmod 700 file1
chmod 700 file2

---

### Post by jeffus_il on 2007-12-31
I use system->administration->network and choose the device by clicking one to enable and the other to disable.

---

### Post by Predator[23rd] on 2007-12-31
answers have been given ...

---

### Post by jellytree on 2007-12-31
Kudos to two fast responses!

**teryowen **- that was pretty much what I was looking for. The scripts were'nt working, so I used your commands manually and checked iwconfig and ifconfig after each to check all was as it should be -- and it was.  I could use the built-in broadcom adapter no problem.  I could not get the usb adapter to obtain an IP address no matter what I tried.

**jeffus**_il - Thanks for that tip - it definitely is one step better than what I asked for. I had been looking for a tool like that and I must have had my USB adapter unplugged the last time I looked at it because right now I can enable/disable which card I want easily.  However, I have the same problem as above -- I cannot get the usb adapter to obtain an IP address, though the built-in wireless adapter can do that no problem.

I don't know if this will help or make a difference but I never got the built-in broadcom adapter to work with network-manager and have successfully used *wifi-radar* and *wicd *in its place. I am currently utilizing *wicd* which uninstalls *network-manager*.

I have a feeling that perhaps I may need to essentially "remove" the broadcom drivers while the USB adapter is in use, and then "reload" the broadcom drivers when the USB adapter is not in use. Of course, I have no idea how to achieve this.  

The USB adapter, in case it matters, is an **ASUS Super Speed N USB 2.0 Adapter, model WL-160W, chipset Marvell 88W8362 **.

---

### Post by jellytree on 2007-12-31
Bump...?

---

