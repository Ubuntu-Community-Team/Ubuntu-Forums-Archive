---
title: "Share many USB drives to one share"
date: 2014-09-24
forum: Networking &amp; Wireless
---

### Post by petermoffat on 2014-09-24
I have a machine running server 14.04 as a media server and backup machine.

I originally started headless, but installed x and lightdm a while ago to run XBMC on it in order to update the SQL database of my shared library (In case this matters).

I have installed automount, and it does what I expect. plug in a USB device, and it mount it to some place in /media/ , and has a symbolic link to /media/usb/ . 

I have created a share of that folder, so that when I'm on a windows machine in the network, I have access to the USB stick or drive connected to the server, which is mounted on /media/usb(through the symbolic link), which I mostly use for backing up personal data from the server, or more often, someone brings around a flash disk and wants a 'linux iso'.

At the moment, the system does not work as intended. The first time after a reboot of the server, a USB device is mounted and shared and I can access it from the windows machine, however, if i remove that device and replace with another, the system breaks. my //Server/USB share is empty, even though /media/usb shows the correctly automounted drive on the ubuntu machine.

I assume it has something to do with just unplugging the device and not unmounting it, that Samba has an iddue with? is there a way to fix this?

---

### Post by petermoffat on 2014-09-24
Is this on the correct section?

---

### Post by sudodus on 2014-09-24
I think this thread is in the correct section,

and I think linux is working better with ***ssh*** (with an openssh server) than with samba. You can use WinSCP or Filezilla from Windows to connect and share files. I hope this link will get you started

[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

---

### Post by petermoffat on 2014-09-24
To be honest, I hadn't thought of ssh  for it. I do ssh into the server for updates etc.

I actually figured out that I don't actually want to do what i said I did in this thread though:)

doing the transfer from windows from a drive in the server to a usb conencted to the server still runs at LAN speed, so I'm not getting the increased transfer speeds I was hoping for.. I'm going to try to remote desktop in and do it that way instead. Will start a new thread on the issue I'm having there..

---

### Post by petermoffat on 2014-09-24
Just some final feedback. I installed xfce and use that for xrdp. Got the server stuck in a login loop for my user, but figured out the chown .Xauthority from a quick search and sorted it.

Previously, when copying files in wimdows from a shared drive on the server to a usb on the server I was getting around 9-10MB/s, basically topping out the 100Mb LAN.

Now I can Remote Desktop into the machine and copy directly at around 40MB/s to an external USB drive.

The reason I don't just ssh in and copy from the command line is that I often need to do multiple files at a time, and selecting and copying is just simpler from a file browser. With the desktop interface, the wife can now do it as well, so,added bonus.

---

### Post by sudodus on 2014-09-25
Congratulations to a good solution :-)

---

