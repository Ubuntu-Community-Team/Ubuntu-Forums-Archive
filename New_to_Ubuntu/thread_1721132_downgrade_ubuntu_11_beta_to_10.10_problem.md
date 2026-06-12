---
title: "downgrade ubuntu 11 beta to 10.10 problem"
date: 2011-04-04
forum: New to Ubuntu
---

### Post by geiroffenberg on 2011-04-04
Hi, my fantasy about being a beta tester went horribly wrong yesterday and took my whole day to solve. I managed to do a downgrade back to 10.10, but now i get the messags that theres no audio drivers, and worse, it cant recognice my usb mobile internet modem anymore! The message i get about the usb modem is that it cant mount the drive because it don't recognice the file system which it says is vfat.
 
The way i did the downgrading to 10.10 was to use the live install from a usb stick, choose the advanced option, choose my linux partition (sda5) , make it a ext 4, set the mount point to root, i did NOT check the format option, because i wantd to keep the home folder etc.
 
thanks
 
/geir

---

### Post by garvinrick4 on 2011-04-04
I have never downgraded and hope someone comes along that can help you out. My suggestion would be just reinstall with the Ubuntu CD after you of course backup all
your personals in /home. If you have a seperate home still backup but should not affect
a different partition for your home. Install your repositories in Software Sources 
go to file system to /etc to /apt to sources.list and open with right click and Software Sources.
Check all your boxes to open repositories:
Need medibuntu and key:
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
``````
sudo apt-get install ubuntu-restricted-extras libdvdcss2 aptitude gparted chromium-browser vlc && sudo aptitude update && sudo aptitude upgrade
```#Just my suggestion on how to get install upgraded quick and your needed packages.
## this will in the least bump your thread up to start again.
How to link for install below if needed.
[Download Ubuntu | Ubuntu]("http://www.ubuntu.com/getubuntu/download")
Sounds like you know how to install manual and into existing sda# with ext4 and /

---

### Post by geiroffenberg on 2011-04-05
you're right. I was hoping that i could just install 10.10 over the 11 and keep the home dir, since that worked when upgrading from 10.10 to 11 beta.

Did a full install with format and now everything works fine again.

Im NOT doing beta testing again, i lost so much time over it.

---

### Post by searchfgold6789 on 2011-04-05
I might point out that it was not necessarily the beta testing that was the cause of your woes.
I would not be surprised if you tried to do the same thing with non-beta releases, and similar problems started appearing.

---

