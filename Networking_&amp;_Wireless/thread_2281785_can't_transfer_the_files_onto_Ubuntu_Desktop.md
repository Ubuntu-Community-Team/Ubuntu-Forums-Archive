---
title: "can't transfer the files onto Ubuntu Desktop"
date: 2015-06-09
forum: Networking &amp; Wireless
---

### Post by houmingc on 2015-06-09
I like to transfer files from my Z3 Sony phone to my ubuntu Desktop.
On ubuntu Desktop, i downloaded bareFTP & Filezilla
On Sony Phone, i downloaded My FTP server & AndFTP

Next, i need help setting static ip on both device

Sony Phone- 192.168.1.102:9090
Ubuntu Desktop- 192.168.1.10

When ifconfig on PC, it shows p4p1 instead of eth0
On PC, using Filezilla or BareFTP i can see the phone directory, but i can't transfer the files onto Desktop

---

### Post by papibe on 2015-06-09
Hi houmingc.

Is this an Android phone? If you are using Ubuntu 14.04, just plug it in with a USB cable. It will be mounted, and then you could just copy and paste the files you want using Nautilus (file manager).

If that does now work, you can change a setting on the phone so it uses a different protocol when connected to a computer (from mtp to mass storage, or the other way around).

If you want to go the way of an app on the phone, I'd recommend SSHelper. It create a sftp server on your phone, so you can connect from your Linux machine using sftp.

I hope it helps. Let us know how it goes.
Regards.

---

### Post by TheFu on 2015-06-09
It is best to have the PC be a "server" - I'd us sftp. It is secure.
The server needs to have a static IP, the client does not.
There are many sftp clients for Android and popular cell OSes.

The server needs to run openssh-server - best to install fail2ban with that.
**sudo apt-get install openssh-server fail2ban** - the default configs are reasonable.

If you setup your router to forward the ssh port to the server and know the public IP for your internet connection, you'll be able to access the "server" from anywhere in the world.  Be certain you do not have a trivial password, if you do this.  20 characters OR, better, use key-based ssh authentication.

It may be easier to have the router use "dhcp reservations" to make the server get the same IP every time. If you do, make the reserved IP outside the normal DHCP IP range. That is important.

IMHO, nobody should be using plain FTP anymore for anything.

---

### Post by houmingc on 2015-06-10
I did many amendments, should i unamend those change?
When i plug into usb, the picture is not display on shotwell.
I try it on my colleguee PC (ubuntu also), shotwell work??

---

### Post by Bucky Ball on 2015-06-10
Are you using the same release and flavour of Ubuntu as your friend?

---

