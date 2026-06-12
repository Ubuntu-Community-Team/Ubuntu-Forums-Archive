---
title: "Need a way to overcome Samba ports being blocked by ISP. Very frustrated."
date: 2010-06-29
forum: New to Ubuntu
---

### Post by Chaser98 on 2010-06-29
Alright here's the problem. I have a VPS running ubuntu. I need to access some files via windows file sharing on that machine. My ISP blocks the filesharing ports 139, 443, and 445 unfortunately. So I've tried overcoming that by using VPNs. I've tried hamachi, but it says permission is denied for /dev/net/tun. I've tried openvpn, however I cannot get java installed because it pulls up some memory errors when it tries to configure the packages.

So really I am clueless and very frustrated here. I have searched this forum, and google repeatedly. Tried a number of tips that fixed other people's problems, but it didn't fix mine.


So I ask of you guys, what other ways do you know of how to overcome the port block by my ISP, to access the file shares securely?

Any help and suggestions would be greately appreciated.

---

### Post by sandyd on 2010-06-29
> **Chaser98 said:**
> Alright here's the problem. I have a VPS running ubuntu. I need to access some files via windows file sharing on that machine. My ISP blocks the filesharing ports 139, 443, and 445 unfortunately. So I've tried overcoming that by using VPNs. I've tried hamachi, but it says permission is denied for /dev/net/tun. I've tried openvpn, however I cannot get java installed because it pulls up some memory errors when it tries to configure the packages.

So really I am clueless and very frustrated here. I have searched this forum, and google repeatedly. Tried a number of tips that fixed other people's problems, but it didn't fix mine.


So I ask of you guys, what other ways do you know of how to overcome the port block by my ISP, to access the file shares securely?

Any help and suggestions would be greately appreciated.easy. FTP, by default uses port 21. Just FTP into the vps. If that port is blocked, change it to use another port.

---

### Post by Chaser98 on 2010-06-29
I really would like to use the built-in windows file sharing interface, or something really similar. I don't wanna use FTP because I don't want to start the client and connect every time. I already have access to the VPS. I just want to make a portion of it into a file sharing server for my business.

---

### Post by bodhi.zazen on 2010-06-30
You can share files vis ssh , the windows client is scp. 

Samba is less then ideal over the internet and I would not advise it.

---

### Post by dtfinch on 2010-06-30
[http://winscp.net/eng/index.php](http://winscp.net/eng/index.php)

Edit: I missed the part where you said "make a portion of it into a file sharing server for my business". There's webdav, which goes over http and which you can map as a drive in Windows without installing anything extra, but I have zero experience setting it up.

---

