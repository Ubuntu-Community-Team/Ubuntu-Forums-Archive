---
title: "Toshiba T9100 with wireless"
date: 2007-03-28
forum: Networking &amp; Wireless
---

### Post by javaholic on 2007-03-28
I have a ubuntu 6.10 laptop as listed above.  It has inbuilt wireless.  I have seen the card pick up and connect to WPA networks (i.e. mine) before under windows vista so i know it does/can support using the correct driver(s) but alas i can't currently use this wireless to connect via WPA.via the network manager.  I have done some searching and i gather the linux driver currently installed according to device manager is a orinoco_cs. I don't think that is the right driver.  If it were i guess network-manager would have an option to select my preferred authenication (WPAPSK).

I thought i had found the right driver/lkm at:

[http://www.agere.com/mobility/wireless_lan_drivers.html](http://www.agere.com/mobility/wireless_lan_drivers.html)

but after having read the readme it seems i was wrong.

I don't particularly like using iwconfig as it seems like a backdoor to wireless connectivity and can be like tentive when playing around with network manager.  that was true to me as my ubuntu 6.06 desktop system can be touchy at inopportune moments or at least seems that way at times.

I also have two other pc card wireless cards one identifing itself as RT2500 and the other which supports WPA and another identifying itself as acx_pci (which i don't think supports WPA which i can handle)

I don't like the idea of using ndis[whateverItIsCalledAgain]wrapper.  I have dapped in it though.  Just a little though.

In short i have two wireless cards that should support 
WPA that i would like to setup up properly with WPA that aren't at the moment.

What would you guys suggest be my next step?

Finding Better drivers?  If so where from?

---

### Post by chili555 on 2007-03-29
Please do:```
lsmod | grep orinoco
lsmod | grep hostap
lsmod | grep prism
```If the cursor pops back without any output, it means no module with that in it's title is loaded. If you get a few words of text from all three, then *sudo gedit /etc/modprobe.d/blacklist* to add the prism part:```
blacklist  prism_<what_u_found>
```It might be prism2_pci or prism2_cs or otherwise. Just blaclist whatever prism you found.

Reboot and let us know if your in-built springs to life.

---

### Post by javaholic on 2007-03-29
I got output from the after entering the following:

lsmod | grep orinoco


I got this:

orinoco_cs             17540  1 
orinoco                45076  1 orinoco_cs
hermes                  9472  2 orinoco_cs,orinoco
pcmcia                 40380  1 orinoco_cs
pcmcia_core            43924  4 orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic

I'm not sure what that means.

I'll have a look around in the meantime.

---

### Post by chili555 on 2007-03-29
But no output from the other commands? You did not mention them either way.

---

### Post by javaholic on 2007-03-29
yes no output from the other commands

---

### Post by chili555 on 2007-03-29
I noticed the link you posted offered the download of a linux driver. These sometimes work, but I'd like to do better than "sometimes." I extracted the package and noticed a hostap directory. Let's try:```
sudo modprobe hostap hostap_cs
```I have seen insmod work and modprobe not and vice versa, so you may have to try both. If the command is successful, there will be no output from the terminal.

If so, then check iwconfig and see if your shy wireless card has appeared. Post back, please.

---

### Post by javaholic on 2007-03-30
I think you might have me wrong.

network-manager picks up and recognises my wireless cards network manager is doing this but seemingly without WPA support which 2 out of the 3 do.

---

### Post by chili555 on 2007-03-30
Did you install and configure wpa-supplicant? Is your card capable of WPA? In a terminal, do *sudo iwlist <your_wireless_interface> key* and you might see something like:```
chili@LAPTOP:~$ sudo iwlist eth1 key
eth1      2 key sizes : 40, 104bits
          4 keys available :
                [1]: 096C-XXXX-0E2B-XXXX-A115-XXXX-FE (104 bits)
                [2]: off
                [3]: off
                [4]: off
          Current Transmit Key: [1]
          Security mode:restricted
          Authentication capabilities :
                WPA
                WPA2
                CIPHER TKIP
                CIPHER CCMP
          Current key_mgmt:0xBFB28258
          Current cipher_pairwise:0xBFB28258
          Current cipher_group:0xBFB28258
```If your card see the access point but you just can't connect, I doubt you have the wrong driver. Sorry if I misunderstood.

---

