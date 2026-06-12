---
title: "[SOLVED] Telnet and File Browsing"
date: 2007-12-18
forum: Networking &amp; Wireless
---

### Post by mtn on 2007-12-18
I recently bought a Neuros OSD Linux media player ([www.neurostechnology.com]("www.neurostechnology.com")) and have set it up to access shares from other computers over my home network. When I telnet in to the OSD from my laptop accross the wireless network (I had to setup auto-mounting of the network shares) I can access the USB external hard drive plugged in to the OSD. I would really like to be able to manage the files on the USB external HD over the network using something like Nautilus - instead of managing the files via the terminal. Does anyone know if any graphical file manager apps support telnet for Ubuntu? or if there are an neat ways to do this kind of thing?

---

### Post by trobbins on 2007-12-18
This is from the website's FAQ:

I have a hard drive connected to my OSD, can I copy files to it remotely?
This capability is not built into the OSD by default, but there is an easy 5-minute "hack" that will allow you to add this functionality. crweb has ported an ftp server that can be downloaded and run on the OSD. Follow the README for directions. You should then be able to use any ftp client to connect to your OSD and upload videos, pictures, music... whatever.
     Back to top

Note: work is actively being pursued to add windows file sharing capabilities to the OSD, so the above method will no longer be necessary.
     Back to top

I'm out of my element with these devices but since you brought it up I'm interested in how it's working.  I'm surprised this capability isn't already implemented.

---

### Post by mtn on 2007-12-19
Thanks for pointing out the[ FAQs]("http://www.neurostechnology.com/neuros-osd-faq"). I had been looking in the forums but hadn't been looking for FTP solutions - been searching for telnet - I didn't really understand what I needed to do.

The instructions and FTP server are here [http://open.neurostechnology.com/node/732](http://open.neurostechnology.com/node/732)

It was well easy to set up - took about 2mins.

**Download and Unzip the FTP Server**
1) Plug the USB hard drive in to computer. 
2) Create a new folder on the hard drive called ftp.
3) Download the[ FTP server]("http://www.limesg.com/osd/ftpserver/osd-ftpserver.zip") and then unzip it to the new folder on the hard drive.

**Telnet into the OSD and Start the FTP Server**
4) Open a terminal Applications>Accessories>Terminal and telnet in to the OSD.
5) Type these instructions in to the terminal hitting the return key in between each line of commands.
(NOTE: one way to find the IP of the OSD is to login to the network router and look at the DHCP client list - it shoudl be something like 192.168.2.4)

```
telnet
```
```
open [IP address]
```
User name:```
root
```
Password:```
pablod
```
```
cd /media
```
```
ls
``` 

And then continue with the cd "folder" commands until you come to the location that you unziped osd-ftpserver.zip. For example,
```
cd USB/ftp
```

Then start the FTP server
```
./run-ftpserver.sh
```

For more info have a look at the original [README]("http://www.limesg.com/osd/ftpserver/README.txt")

**Browse to the Hard Drive with Nautilus**
To access the files through Nautilus file browser, open Nautilus>Go>Location and type,
```
ftp://[OSD IP]
```
For example
```
ftp://192.168.2.4
```

User name:```
 root
```
Password:```
 pablod
```

and then browse to the USB hard drive.

---

