---
title: "Why wont my bluetooth work properly?"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by kn100 on 2009-02-14
I just went into town and bought myself a  Bluetooth adapter from argos. It's branded as Mikomi, and on the back it says BD-01A. Ubuntu detected it, and it looked normal, but if i try to do anything from the computer to the phone (send stuff, browse the device, pair with the device) it just says error connecting. I can send stuff from my phones to the pc fine (after i installed gnome-obex server. Any ideas?

---

### Post by johnjohn2 on 2009-02-15
If your device is paired then it should be working.

What brand of mobile are you using?

---

### Post by Kevbert on 2009-02-15
Sending files to the phone can be a bit of a problem.  Depending on your make of phone it may/may not be 100% bluetooth compatible. For example SonyEricsson and Ericsson phones are 100% compatible, but HTC phones will generally not receive files from a PC via bluetooth.  Another problem is how you send a file to the phone (I've raised bugs on this). Once the phone is seen by the PC, if you right-click on a file in Nautilus and select Send to (the phone) this may not work depending on which version of Ubuntu you're using.  You may have an option, you need to set, on the phone to accept incoming files (from the PC).  
The best way to send a file to the phone is when the bluetooth icon is showing on in the top righthand corner of your desktop and right-click and select browse device (select your phone). There should now be a Nautilus Window showing your phone folders. Open another window (via Places), so that the file you wish to send to the phone is displayed and use drag and drop to send the file.
You may not be able to see all directories in the phone as some will be (copywrite) protected (for example over-the-air downloaded games).
Good luck.

---

### Post by kn100 on 2009-02-15
The pc sees my HTC, but wont send files to it, Same problem with my Samsung, My sony erricson, and my good old motorola V3. Im using ubuntu 8.10, and i an trying to send a picture that is not copy protected, it says connecting to phone, but then says connecting failed. The PC sees the phones, but will not pair with them at all. Just says connecting failed. Ive sent files to my HTC using windows, so thats not the problem.

With windows it needed Bluesoleil to work, but Bluesoleil doesnt install in wine, so im sort of stuck haha.

I send files to it by right clicking the little bluetooth icon, and clicking send file to device. Ive tried 'Browse files on device' But no go.

Any help? I DO NOT want to install XP, I loved ubuntu up until this point..

---

### Post by Kevbert on 2009-02-15
The V3 and Sony Ericsson should both work (I have an old one too).  Do you get to set up a passcode on the phone ?  Regarding bluetooth programs, one I have is Bluetooth file sharing which occurs under Applications-Accessories (in 8.04 which I'm currently running, I can't remember if it's the same in 8.10). It's one of the following which you should be able to install via Synaptic: obex-data-server, gnome-vfs-obexftp, bluez-utils, bluez-gnome.  You may need to run it prior to sending a file.
Bluetooth worked fine in 7.10 until the updates started and ever since it has been problematic. I've yet to try it in Jaunty...
Regarding the HTC phone, was the software used written by HTC for Windows ?

---

### Post by kn100 on 2009-02-15
Its a htc blue angel, which normally runs WM2003 but i hacked it up to version 6.1, but there is an application that allows it to recieve data files, if you want it i can link it.

---

### Post by Kevbert on 2009-02-15
> **kn100 said:**
> Its a htc blue angel, which normally runs WM2003 but i hacked it up to version 6.1, but there is an application that allows it to recieve data files, if you want it i can link it.

Yes, please. I'm using a Virgin lobster. Where do you get your HTC hacks from ? If you want software/applications for Motorola phones you can get them from [[COLOR="Red"]here[/COLOR]]("http://www.modmymoto.com/guides/"). I used to use motomodders.net, but it seems their site is no longer available.

---

### Post by kn100 on 2009-02-16
I been a member at modmymoto.com for YEARS, got over 2000 posts there, made loads of guides for the MotoRIZR Z3. Im part of Team RIZR if you've heared of them.
Hacks for HTC/Winmo Devices: [http://www.xda-developers.com/](http://www.xda-developers.com/)

[http://www.modmymoto.com/forums/member.php?u=48231](http://www.modmymoto.com/forums/member.php?u=48231)

---

### Post by Kevbert on 2009-02-16
Thanks for the link, now registered.:P:P:P

---

