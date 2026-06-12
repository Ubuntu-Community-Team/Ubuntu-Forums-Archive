---
title: "modems"
date: 2010-04-07
forum: New to Ubuntu
---

### Post by Chad Olson on 2010-04-07
I just installed ubuntu a couple days ago I use a blackberry pearl for internet.
I need to load blackberry destop manager to use the internet but I cant figure out how to install wine without an internet connection so it seams that i cant get on the internet untill i load wine and blackberry destop manager but i cant load that untill i get on the internet. please help

---

### Post by SlickRick on 2010-04-07
[hhttp://wine.budgetdedicated.com/archive/index.html](hhttp://wine.budgetdedicated.com/archive/index.html)

download the deb package appropriate to your system/the version you want, transfer it from where ever you're posting from to ubuntu and run it

I've never used a blackberry but you may be able to use the internet without the desktop manager. Are you connecting the blackberry through a USB calbe or setting it up as a wireless access point. If you're setting it up as a wifi spot, you should be able to connect to it normally. If by usb then you could try looking around for a setting which would connect the USB but not mount the filesystem. On my phone, when I connect a USB cable, I'm given four choices
Mass storage - mount the memory stick

Webcam - use the camera as a webcam
PictBridge - something to do with printers
COM port - not entirely sure what it is but when I choose this setting, the network manager lets me set up a mobile internet connection, which is what you need to look for.

Hope this vague answer helps and maybe someone can correct me if I'm wrong.

---

### Post by HDave on 2010-04-07
You are going to have find a traditional internet connection to install some software.  There is no way around that.

However, there are simpler ways to use the blackberry and other devices as a modem.  Check it out:

[http://lmgtfy.com/?q=ubuntu+blackberry+pearl+%20as+modem]("http://lmgtfy.com/?q=ubuntu+blackberry+pearl+%20as+modem")

---

### Post by 3rdalbum on 2010-04-07
Linux is not Windows; you don't use the Windows software to tether your phone. Check out what HDave linked you to.

---

### Post by shazbut on 2010-04-08
Don't know about blackberries, but I can use my nokia's 3g data connection via bluetooth tethering in network manager.  Just go through "setup new device" under the bluetooth tray icon, and on the last page of that there's an option to access the internet using your mobile phone.

---

### Post by HDave on 2010-04-09
shazbut is right -- I did the same thing with my Treo, my verizon usb device, and my LG Env Touch.  I just pugged it in and viola...it just worked.  Try using the network manager first...if that fails follow the link i provided.

---

### Post by Chad Olson on 2010-04-10
I am using a usb I just installed ubuntu so I don't know how it works yet looks like it could take me a while to figure it out I've tried bluetooth but I can't find the phone. I think Ill just take my computer somewhere I can use my Ethernet port.

---

### Post by codemaniac on 2010-04-11
click the "nm-applet" on the panel...if it is not there in command prompt type "nm-applet"
vpn connections->configure vpn->mobile broadband..your modem should be listed there
just fill up your internet subcription details.Now you are good to go..:)

---

### Post by ubun2warrior on 2010-04-11
connect your blackberry to the pc, then open the network manager and select mobile broadband from there. then add new connection and follow the steps. i think you will configure it easily.

---

### Post by Chad Olson on 2010-06-07
> **codemaniac said:**
> click the "nm-applet" on the panel...if it is not there in command prompt type "nm-applet"
vpn connections->configure vpn->mobile broadband..your modem should be listed there
just fill up your internet subcription details.Now you are good to go..:)


I have done this but ubuntu doesn't find my modem I've asked a tec at us cellular they said that blackberry protects their software  that is why black berry is hard to get working in linux, I've downloaded berry4all tar file but have no idea how to install it.

---

### Post by Chad Olson on 2010-06-14
I've got it now I got a friend of mine to look at it tethering using usb was way to complicated but we got it with bluetooth the standard bluetooth manager wouldn't work so we installed blueman bluetooth manager and then it worked. thanks for the help

---

