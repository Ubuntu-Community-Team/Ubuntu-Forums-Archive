---
title: "awus036h not lighting up in ubuntu mini xfce 16.04 64 bit"
date: 2016-12-11
forum: Networking &amp; Wireless
---

### Post by Chris1965 on 2016-12-11
Once I plug the usb wifi (awus036h) in the light doesn't blink, I have tried several usb extension cables and it didn't make a difference. For the network manager I am running wicd. I am new to linux so the jibber jabber in the script txt file means very little to me presently. :) Any help in this matter would be greatly appreciated. I need this device for range as I have an outdoor antenna to connect with my brothers house down the lane.

The laptop is a Dell M6400 workstation fully loaded: SSD , 16 gig memory, 2.53 GHz 2 Duo core, usb 2.

---

### Post by chili555 on 2016-12-12
I suspect that the internal drivers are conflicting; let's blacklist it:```
sudo -i
echo "blacklist iwlwifi"  >>  /etc/modprobe.d/blacklist.conf
exit
```Reboot.> the light doesn't blinkThat may not mean that it isn't working, just that the driver may not drive the LED correctly.

I suggest that you set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

---

### Post by Chris1965 on 2016-12-12
I did it all, the blacklist iwlwifi cut off my internal wifi card so I just undid that change and my usb wifi card (awus036h) now shows up as wlx00c0ca72014c which I found weird as in 14.04 it used to show up as wlan0 (internal) and wlan1 (usb). I'm starting to think perhaps I installed a non-US version of Ubuntu as I most definately don't live in Iceland but I did download it off the Ubuntu site. Anyway the card does now function however the light still doesn't show on the device. 

Should I leave things be anyway or should I install the ALFA's driver? And if I should ......... what is the process for installing or upgrading this new driver since the OS comes with one already built in the kernel which I am presently using? Surely the kernel driver is up to date as this is an old device.

---

### Post by chili555 on 2016-12-12
>  the blacklist iwlwifi cut off my internal wifi card so I just undid that change Why?? Isn't it your intent to use the USB only? Are you saying the USB doesn't show up at all with iwlwifi blacklisted? Or...what??>  as I most definately don't live in Iceland I clearly said:> Of course, substitute your country code if not Iceland. :confused:

---

### Post by Chris1965 on 2016-12-12
Ok this is a laptop which refers to mobile computer and if I take it out which I do often then if my internal driver is shut off then unless I take the usb with me then I will have no wifi unless I keep going in and setting up this setting for every event for the internal chip. So what you are saying is I can't have two different wifi cards in one computer? Wouldn't the switch on the side to disable the built in be so much easier? I bought the awus036h just to connect at home with my brothers home due to it's ability to connect a long range antenna to the exterior of the house.

What I was initially saying was lsusb was showing the device but not showing up via wlan to connect to it and that the light on the device wasn't working. What I was to understand was plugging in the device should make the light come on automatically showing it was properly working. And as for the unusual names of the devices that I didn't understand because they were normally listed as wlan1 and wlan2.

I am learning linux as a newbie as most refer to and am no professor by any means which is why I am in here trying to ask my questions to get a clear answer.

---

### Post by chili555 on 2016-12-12
> So what you are saying is I can't have two different wifi cards in one computer? Wouldn't the switch on the side to disable the built in be so much easier? It would be very easy except that, due to air transportation regulations, changing the physical switch on the computer disables *ALL* wireless, including USB. You can easily try it yourself. Flip the switch and plug in the USB. Does it work? What does this tell you?```
rfkill list all
```If the USB is not "hardblocked:yes", then I will be very surprised. If the USB actually works, then you are all set and the problem is solved!

If it were me, I'd leave iwlwifi blacklisted. When you go out and want to connect, open the terminal and do:```
sudo modprobe iwlwifi
```If and when you get tired of that, carry the USB always.

I am quite confident that the drivers conflict.

---

