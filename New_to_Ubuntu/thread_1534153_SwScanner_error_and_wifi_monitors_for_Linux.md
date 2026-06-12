---
title: "SwScanner error and wifi monitors for Linux"
date: 2010-07-19
forum: New to Ubuntu
---

### Post by beew on 2010-07-19
Hi,

I downloaded and installed the SWScanner from the Ubuntu (Lucid)Repo along with the kde dependencies.

At first "scan as root" didn't work because it could not run kdesu. After searching the forum a bit I managed to solve the problem by running in the terminal

cd/usr/bin
sudo ln -s gksudo kdesu 

Finally I was able to get it running. But a few seconds into scanning, I was hit with the error message "failed to read scan data".

Does anyone have an idea of what might have caused this?

I am looking for a simple wifi monitor that can display the channels, frequencies and connection strength of nearby networks like Xirrus is windows.
I know about kismet but it is too complicated to configure and it may not work with my wireless card (I am using a usb wireless card I bought for $10) I am not looking for anything too fancy. Wifi radar is simple, but it doesn't even give any information about connection strength.

Also,  I tried 

sudo iwlist wlan0 scan

I get the error message

wlan0 Interface doesn't support scanning: Device or Resource busy.

Any help would be appreciated.

P.S. I know there is a Linux version for Xirrus. However it seems that it is no longer supported. I couldn't find it on their download page any more, the last time they had a log entry about it was in 2008. Now all they offer are downloads for windows and Mac. I have downloaded it from softpedia and it works fine on my Ubuntu box, but I would prefer something which is still being supported and updated.

---

### Post by beew on 2010-07-23
bump??!!

---

### Post by beew on 2010-08-03
bump?!

---

### Post by beew on 2010-09-23
bump!!!

---

### Post by OooBuntuRox on 2010-11-23
[SIZE=3]Hello,

Has anyone solved this? and what does BUMP mean? Does it mean the program is going to be dropped due to lack of support?[/SIZE]

[SIZE=2]BTW, I was able to use SWScanner in Ubuntu 9.10. I may have even been using gnome but don't recall for certain. I also remember having to use an older version of SWscanner. I think it might have been 2.0

Thanks[/SIZE]

---

