---
title: "Transferring files to unrooted Android phone"
date: 2015-01-03
forum: Networking &amp; Wireless
---

### Post by mollie4168 on 2015-01-03
I have been searching the forums to figure out how to transfer some files to my Android Moto G from Ubuntu 14.10, and I'm just getting more confused about doing it in a simple, secure way for what I need.  My carrier does not allow me to root my phone.  All I want to do is transfer about 150 music files and be able to transfer other files from time to time--I don't need full access to my computer.  It doesn't sound like it's that difficult, but I keep getting stuck at points that are beyond my knowledge.

When I attempt to access my phone via MTP, I get continuously opening windows with the phone/storage device.  They keep opening (I can't do anything) until I disconnect the cord.  I found general instructions for changing MTP settings in Android (theoretically to prevent all the windows), but I couldn't find those settings anywhere on my particular phone.  When I set my phone to open with PTP, I get similar behavior except that the window closes and reopens each time, asking me what I want to do with the camera that's connected.

I tried installing FTPServer on my phone, but I don't know what my port number is. I've searched around the forums and google, and I'm having a hard time figuring out the correct, secure port number to use.  

I found in Google Groups the suggestion:
ftp IP PORT
IP: bad port number-- PORT
usage: ftp host-name [port]
ftp>

...but I don't know enough to know what to do with this.  I've looked at my home connection information, and that doesn't help me.

I keep seeing information on ssh (like [this]("https://help.ubuntu.com/community/SSH/TransferFiles")), but much of it is beyond me, and I think I'd need the ability to root my phone.

Any suggestions?

Thank you for assistance and patience.

---

### Post by ajgreeny on 2015-01-03
It seems to vary from phone/tablet to phone/tablet, and possibly the exact version of Android used but I have just had success by following the info at [http://ubuntuforums.org/showthread.php?t=2226702](http://ubuntuforums.org/showthread.php?t=2226702)  which allows me to use a USB cable to transfer files either direction.

---

### Post by mollie4168 on 2015-01-03
Thank you for the link, ajgreeny.  That's good to know since it's been hard to get clear directions on how to make MTP work.

I just figured out how to do my file transfers through FTP.  My Kindle Fire was also not connecting via MTP, so through that I found an app that presented in a way which helped me comprehend FTP better.  I was also finally able to get a few of my files out of the clutches of Amazon.  I went back to my phone's app + found FileZilla for Ubuntu, so I'm good.

---

