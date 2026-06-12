---
title: "my first own server!"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by filzuslausus on 2010-03-22
dear forum!
I asked in another forum for help about ubuntu servers, because i wanna set up my first own server and i wanna use ubuntu as os, but i dont know which one...ubuntux, ubuntu...
So my wishes to the server are:
1.he should go to an energy saving mode when n0t in use, and wake up as quickly as possible!
2. I would like to use it as a fileserver, so people in my house can put files on it and load them down via wireless lan!
3. I also would like to use a tv-card, dvb-t, and and record movies etc., he should save them. Then i wanna download them on a other pc and watch them, even after download or on stream! But i also wanna watch them on tv, which i would use per hdmi from the server
4. He should be very safe so i would like to built a raid1.

Is that possible?
And are there any driver problems on ubuntu, about tv-cards, graphic cards or usb-sticks?

Im sorry for my english its not the best, but i hope you understand!

Best wishes!

---

### Post by r-senior on 2010-03-22
> 1.he should go to an energy saving mode when n0t in use, and wake up as quickly as possible!
2. I would like to use it as a fileserver, so people in my house can put files on it and load them down via wireless lan!
3. I also would like to use a tv-card, dvb-t, and and record movies etc., he should save them. Then i wanna download them on a other pc and watch them, even after download or on stream! But i also wanna watch them on tv, which i would use per hdmi from the server
4. He should be very safe so i would like to built a raid1.
You could install Ubuntu Server Edition, or you could do this with standard Desktop Edition, retaining the GUI for configuration but removing applications you don't need. It depends how minimal or functional you want the server to be, and whether it will have a monitor/keyboard attached?

If you run the box headless, i.e. no monitor, you can administer it remotely using ssh into the terminal, remote desktop (a bit slow), or a web interface like Webmin.

1. You can do things like spinning down hard disks, or set up the standard power management. Obviously the more aggressive your power management, the slower it is to wake up.

2. Samba if you have any Windows clients. NFS is an option if all clients are Unix-based.

3. Pass

4. Some motherboards come with hardware RAID support built in. Alternatively you can use mdtools on Ubuntu to build software RAID arrays including RAID1.

You might also consider adding something like DNSMasq to the server to provide local DNS, DHCP and caching for upstream DNS? Maybe also a simple web proxy? Not sure if that would help you with downloaded video, etc.

---

### Post by eriktheblu on 2010-03-22
Sounds to me like you want to try [Mythbuntu](http://www.mythbuntu.org/). It is specifically designed for TV recording and network streaming.

It may not be the best OS for a file server, but for most home networks it should be adequate.

I have a Mythbunu machine that records cable TV (standard definition for me). I normally watch the recordings directly from that computer on my TV, but I can also stream them to my other Ubuntu computer over the network. My wife can access the recordings on her Windows 7 computer as well.

You will want to carefully research the hardware. Nvidia graphics cards have very good Linux drivers. ATI cards have historically had very bad drivers, but dramatic improvements have been made recently. Hauppauge video capture cards are also known to work well. 

My Mythbuntu machine uses the Hauppaguge HVR 1600 card and a Nvidia card. There is an unfortunate driver conflict between those two that I overcame by making a minor modification to the boot loader.

---

### Post by Iowan on 2010-03-23
For a sort of "shopping guide" you can check the [Server Guide]("https://help.ubuntu.com/9.10/serverguide/C/index.html").

---

