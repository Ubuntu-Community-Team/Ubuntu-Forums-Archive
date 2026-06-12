---
title: "Can't see my wireless home network"
date: 2008-09-12
forum: Networking &amp; Wireless
---

### Post by youboontwo on 2008-09-12
Hi, ultra noob here. Minor linux experience, eager to learn :)

I installed Ubuntu right over Windows Vista on my HP laptop last night, and I'm pleased as punch. However, I'm having some issues connecting to my home wireless network. I ran the hardware test and it stated that my wireless network device is working, however, I cannot connect. 

First I ran the liveCD version of Ubuntu and when I did, it mentioned that the driver for my wireless device was not supported, but offered me the chance to enable it anyway. So I did. Now that I have the OS installed I'm noticeing that the wireless device passes the necessary tests, but it doesn't seem to find my network at home in roaming mode. I also tried to manually configure it, but no dice. Should I invest in a Ubuntu friendly wireless device this weekend? Is there a place to find the Ubuntu friendly driver for the device I already own? 

Thanks in advance. My previous experience with Linux dudes has been great!

---

### Post by TSupra88 on 2008-09-12
If it doesn't work out of the box, 80% chance it might be a broadcom. check this out for further reference: [http://tsupra88.blogspot.com](http://tsupra88.blogspot.com)

---

### Post by timcredible on 2008-09-12
find out the brand/model of your wireless card/chip, then do a search about it, there's a very good chance you'll find a complete how-to on this forum for it.

---

### Post by superprash2003 on 2008-09-12
in your terminal type lshw -C network and post output here

---

### Post by youboontwo on 2008-09-13
Results of lshw on my workstation (copied by hand)

module=snd_atiixp_modem
  *-network DISABLED
[INDENT]description: Wireless Interface[/INDENT]
[INDENT]physical is: 1[/INDENT]
[INDENT]logical name: wlan0[/INDENT]
[INDENT]serial: 00:90:4b:92:a8:e0[/INDENT]
[INDENT]capabilities: ethernet physical wireless[/INDENT]
[INDENT]configuration: broadcast=yes multicast=yes wirless=IEEE 802.11g[/INDENT]

Hope this helps somehow.

---

### Post by youboontwo on 2008-09-13
Ok here is an update of how I've been f'n around all morning with this thing, and no dice.

So I looked into the article posted here, and some of the Broadcom threads as well. They seem to all pertain to me, but they don't seem to actually help.

My HP laptop has a Broadcom 54 wireless card. It tests just fine, but I see no netwrok. I downloaded and installed the B43fwcutter program and attempted to run it with the wl_apast.o file, but I get the following message:

"Sorry, the input file is either wrong or not supported by b43-fwcutter.
This file has an unknown MD5sum 80c7bb743de4025f57ac7166dac7bc4a"

Do I have the wrong ".o" file? Do I need to do something else? Can I simply buy a wireless card which works with Linux happily and make myself happy in the process?

---

### Post by youboontwo on 2008-09-13
Ok, so I found the right ".o" file, turned out to be the wl_apast_mimo.o" and extracted it and ran just as the directions specified, but I still cannot see any wireless networks despite the fact that my laptop is sitting directly next to my desktop PC running Vista which does see the network. Also, when running Windows on the laptop, I never had a problem seeing the network anywhere in my house, so I know it's not a wireless signal issue here.

Can anyone provide help?

---

### Post by youboontwo on 2008-09-13
To be clear this is a "Broadcom BCM4306 802.11b/g"

---

### Post by superprash2003 on 2008-09-22
have you tried this ? [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

