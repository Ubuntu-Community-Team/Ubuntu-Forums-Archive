---
title: "Hotel LAN Problems"
date: 2007-01-26
forum: Networking &amp; Wireless
---

### Post by willbur on 2007-01-26
Hello everyone

I've set up my Edgy installation on a new hard disk in my IBM T40 laptop, and followed these instructions

[http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html)

and lots of help from members of this forum (thanks!) to get my Speedtouch 300 USB modem to connect automatically when I boot up at home.

I'm now in a hotel room in Tokyo and am trying to connect to the web using their LAN. Could anyone give me some clues as to how to do this? I'm connected using Windows at the moment, and will have to swap over the HDD's to try anything out in Ubuntu. I know the IP address, subnet mask and default gateway figures, but I can't get any further.

Can anyone please help this newbie?

---

### Post by lhtown on 2007-01-27
I forget the name of it, since it is not installed on this computer, but there are one or two programs (maybe more) that will search for available wireless networks in the area and show the results in the taskbar.

---

### Post by RandomJoe on 2007-01-27
Do you actually have to do anything special?  The hotels I've stayed at use DHCP, and maybe a captive portal that redirects your first web access to a login screen (to give you the "rules" and verify you are a customer) which puts a cookie on your machine to then give you full access.  Just plug in the cable, boot up and you're good.

If you have to manually enter info, if you have your IP, subnet and gateway IP that's a start - but you would also need a DNS server IP at the least.  That would all be entered under System -> Administration -> Networking, then select your Ethernet card and hit Properties.  DNS entries go on the DNS tab of the main Network Settings window.

If you are talking about using a _wireless_ network, that's another layer on top of all this.  In my case, I have Network Manager installed and it shows all the available wireless APs in range, just select what I want and (if needed) it asks for an encryption key.

---

### Post by willbur on 2007-01-28
Thanks, everyone - I'll install Network Manager and see how I go for wireless. As for the wired network, I just plugged the ethernet cable into my computer, started my browser and I was in - under Windows. No matter what I did, I couldn't get my Ubuntu installation to perform the same trick. Could it be because of my speedtouch logon script I mentioned in my first post? Could that stop the system looking for and accepting any other wired networks? :-k

---

### Post by willbur on 2007-01-28
Tried Network Manager (installed via add/remove in Applications list) and it works wonders in finding and connecting to any wireless network in range. However, I find I'm then unable to connect to my Speedtouch 330 USB modem. The 'wired network' field is greyed out, and unticking 'wireless' or even 'networking' in the network manager options has no effect on my speedtouch connection, even if I restart x or the entire system. Can anyone help, please? I've uninstalled Network Manager for the moment, but it'd be great to get it working when I want it to, and to be able to boot with it disabled, so my speedtouch has a chance to connect. Better still, is there a way to tell it to recognise the usb modem as a wired connection?

Many thanks in advance, fellas...

---

