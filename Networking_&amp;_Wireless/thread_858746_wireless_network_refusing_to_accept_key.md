---
title: "wireless network refusing to accept key"
date: 2008-07-13
forum: Networking &amp; Wireless
---

### Post by Deep fried ice-cream on 2008-07-13
I'm running Ubuntu 8.04 and aside for wireless networking (currently using cat5 and being hated for it), everything is going nicely.
However, the wireless network is refusing to accept the key, I'm trying to connect to a WPA-PSK network, please tell me what I'm doing wrong.
If you need more info I'll be happy to post it.

---

### Post by tl3000 on 2008-07-13
Not sure of your situation but it seems similar to the following bug report:

[https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/207446](https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/207446)

Read through the posts and see if the problem is the same.

---

### Post by Deep fried ice-cream on 2008-07-13
Ummm, I'm not running ndswrapper, is that relevant?

---

### Post by tl3000 on 2008-07-14
> **Deep fried ice-cream said:**
> Ummm, I'm not running ndswrapper, is that relevant?

The bug report deals with wireless cases when NDISwrapper and WPA are used with 8.04... 

If you want any help from this forum in debugging your situation, you need to provide more info about your setup (i.e., brand and type of wireless adapter, driver used, configuration settings, steps you've taken to troubleshoot, etc.)

---

### Post by nickdbliss on 2008-07-14
Ok try this.
in the terminal do:
wpa_passphrase <your SSID> <Yourpassword>

Example:
nick@nick-laptop:~$ wpa_passphrase Home-network nick
network={
	ssid="Home-network"
	#psk="nickwilson"
	psk=451cf39c218277434ee4de8abe66240b5efc538f9feb781eb8cd5f3c4f77b288
}

Copy the psk code. in the example it is:
451cf39c218277434ee4de8abe66240b5efc538f9feb781eb8cd5f3c4f77b288

Paste it when it asks for key. Try 3-4 times if refuses. it should work for you.thanks

---

### Post by Deep fried ice-cream on 2008-07-14
In terms of troubleshooting, I yelled at the computer.
also, the psk termanal thing dosnt work, tried it 10 times,
I think I have a ralink wirless card, but im not 100% sure.
Every thing esle is as it came out of the box.

---

### Post by nickdbliss on 2008-07-15
> **Deep fried ice-cream said:**
> In terms of troubleshooting, I yelled at the computer.
also, the psk termanal thing dosnt work, tried it 10 times,
I think I have a ralink wirless card, but im not 100% sure.
Every thing esle is as it came out of the box.

Post the output of code:
cat /etc/network/interfaces 
and 
ifconfig

---

### Post by Deep fried ice-cream on 2008-07-15
Look, sorry about the fuss, it seems I was putting in the password for the previous network, I've found the right one and everything just goes perfectly with no fiddling.
Thanks for the help anyway.
:lolflag:

---

### Post by nickdbliss on 2008-07-15
> **Deep fried ice-cream said:**
> Look, sorry about the fuss, it seems I was putting in the password for the previous network, I've found the right one and everything just goes perfectly with no fiddling.
Thanks for the help anyway.
:lolflag:

You crack me up man. Next time be calm. Cheers

---

