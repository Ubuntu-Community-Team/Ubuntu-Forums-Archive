---
title: "Easiest way for me to connect to any wireless networks in range!"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by gen_x on 2007-04-24
Here's what I did.

First edit your interfaces file like so:

sudo gedit /etc/network/interfaces

The ouput would like some what similar to:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto wlan0
iface wlan0 inet dhcp

...etc...

Now just comment everything out except for the first two lines which should be the loopback.  It would like somethink like this:

auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

Then download/install network manager if you don't already have it.

sudo apt-get install network-manager-gnome

Once the install completes there should be an icon on the top right corner of your screen indicating that network manager is running.

Then either restart your computer or do sudo /etc/init.d/networking restart.  Viola!  Your computer should be able to pick your wireless device.

This works well for any wireless network (assumption made here).  For the record it works for my network at home which is wpa1 with TKIP, PSK and also at work with WEP.  I'm runny an Acer with Intel 3945ABG on Edgy Eft.  

Hope this will make some of you stop pulling your hair out.  :lolflag:

---

### Post by Jouke74 on 2007-04-24
And exactly that part got a bit changed / screwed in combination with WPA_supplicant and/or Ndiswrapper for, so it seems, many people in Feisty Fawn.... Networks are there but it does not want to connect.

:popcorn:

---

### Post by gen_x on 2007-04-24
> **Jouke74 said:**
> And exactly that part got a bit changed / screwed in combination with WPA_supplicant and/or Ndiswrapper for, so it seems, many people in Feisty Fawn.... Networks are there but it does not want to connect.

:popcorn:

Hmmm...  follow wieman01's how to.  It should work.  But that setup only works for one location at any one time with one wireless device/similar device setup.  His how to is stickied.  Cheers!  :)

---

### Post by gen_x on 2007-04-24
Well folks I have Feisty on my lappy.  Just got the ATI drivers working and the wireless is flawless.  Don't give up hope.  :)   Same exact setup for Edgy as it is on Feisty now.  Refer to post number 1.

Here's a freshly installed pic of my desktop:

[IMG]http://img370.imageshack.us/my.php?image=screenshot1sd6.jpg][IMG]http://img370.imageshack.us/img370/7751/screenshot1sd6.th.jpg[/IMG]

If the above link does not work try this:

[[IMG]http://img370.imageshack.us/img370/7751/screenshot1sd6.jpg[/IMG]](http://imageshack.us)

---

### Post by gen_x on 2007-04-24
Oh, I should mention that if you have Feisty you don't have to install anything!  Good luck.  I hope my pic wasn't too big.  If it is, please resize it mods.

---

