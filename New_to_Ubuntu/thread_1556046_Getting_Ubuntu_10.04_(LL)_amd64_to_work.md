---
title: "Getting Ubuntu 10.04 (LL) amd64 to work"
date: 2010-08-18
forum: New to Ubuntu
---

### Post by mechanicarts on 2010-08-18
I am a regular windows user. I have been using windows all my life, and at some point I was forced to use mac at my University. Right now, I want to work with Ubuntu. Don't know why, I just woke up one day wanting linux and specifically Ubuntu.

After 2 days of horrible things (like HDD corruption, ~10 formats, tens of bad sectors, total loss of data etc) I'm still stuck with no linux. I tried 3 different Ubuntu CD's (1 i386 and 2 amd64 versions) but none did the thing.

Main problem is the wlan problem. Ubuntu just doesn't find wifi's around. At some point it did find the only unsecure network (there are ~5 secure networks around) in the neighborhood, but it didn't find my own hidden wifi (even when I fed it with MAC, SSID, BSSID and all that stuff).

How do I get it to work on amd64? Please be as specific as possible, with step-by-step if possible.

(to inform you, none of the google solutions helped. I also tried ndiswrapper but I couldn't find any .inf files for my w-adapter. I need some advice from someone that knows first-hand)

My system architecture is x64 ready:

Intel C2D, 2.6GHz
4GB of RAM
nVidia GT240M 1GB
500GB HDD
Realtek RTL8191 SE (wireless adapter)




(PS: I asked about my problem in another community (nothing about linux, mostly school and university students) and they all told me to **** off linux and go back to windows, as I wasn't fit for Linux. I hope this doesn't happen here, as I really want to get involved in Linux)

---

### Post by sandyd on 2010-08-18
> **mechanicarts said:**
> I am a regular windows user. I have been using windows all my life, and at some point I was forced to use mac at my University. Right now, I want to work with Ubuntu. Don't know why, I just woke up one day wanting linux and specifically Ubuntu.

After 2 days of horrible things (like HDD corruption, ~10 formats, tens of bad sectors, total loss of data etc) I'm still stuck with no linux. I tried 3 different Ubuntu CD's (1 i386 and 2 amd64 versions) but none did the thing.

Main problem is the wlan problem. Ubuntu just doesn't find wifi's around. At some point it did find the only unsecure network (there are ~5 secure networks around) in the neighborhood, but it didn't find my own hidden wifi (even when I fed it with MAC, SSID, BSSID and all that stuff).

How do I get it to work on amd64? Please be as specific as possible, with step-by-step if possible.

(to inform you, none of the google solutions helped. I also tried ndiswrapper but I couldn't find any .inf files for my w-adapter. I need some advice from someone that knows first-hand)

My system architecture is x64 ready:

Intel C2D, 2.6GHz
4GB of RAM
nVidia GT240M 1GB
500GB HDD
Realtek RTL8191 SE (wireless adapter)




(PS: I asked about my problem in another community (nothing about linux, mostly school and university students) and they all told me to **** off linux and go back to windows, as I wasn't fit for Linux. I hope this doesn't happen here, as I really want to get involved in Linux)
here you go :)
and don't worry, we got a friendly community here l)
[http://ubuntuforums.org/showpost.php?p=8335065&postcount=2]("http://ubuntuforums.org/showthread.php?t=1329254")

---

### Post by mechanicarts on 2010-08-18
Thanks for the fast response carlee! I am a bit reluctant to do this though. I got the 8191 SE, not the 8192 SE mentioned in the linked thread. Is this safe, or will it mess up my installation? (once more if I may add :P)


UPDATE: I did find the rtl8191SE driver and uploaded it, then followed the instructions in the linked thread. However, it still doesn't show my own protected network, or anything around. Any help?

---

### Post by sandyd on 2010-08-20
> **mechanicarts said:**
> Thanks for the fast response carlee! I am a bit reluctant to do this though. I got the 8191 SE, not the 8192 SE mentioned in the linked thread. Is this safe, or will it mess up my installation? (once more if I may add :P)


UPDATE: I did find the rtl8191SE driver and uploaded it, then followed the instructions in the linked thread. However, it still doesn't show my own protected network, or anything around. Any help?
oops. try this instead
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1469823](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1469823)
and heres the file their refering to
[https://launchpad.net/~matt-price/+archive/mattprice/+files/rtl8192se-dkms_2.6.0015.0127.2010_all.deb](https://launchpad.net/~matt-price/+archive/mattprice/+files/rtl8192se-dkms_2.6.0015.0127.2010_all.deb)

---

