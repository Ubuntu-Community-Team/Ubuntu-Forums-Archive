---
title: "Setup wifi hot spot and ftp server on the same PC"
date: 2014-03-12
forum: Networking &amp; Wireless
---

### Post by rusljam on 2014-03-12
Well, this is the question. I want to setup a wifi hotspot on a Raspberry Pi and a ftp server on the same machine. A wifi dongle with AP support is present.  The Raspberry won't be connected to Internet. It is needed only for create a local wifi network and to act as a ftp server.  Is it possible with only one wifi dongle, and if it is, how to do it?.  Thanks in advance.

---

### Post by Lars Noodén on 2014-03-12
You could give the dongle a fixed ip address and then use either isc-dhcp-server or dnsmasq to serve addresses.  As to using [FTP](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp), are you sure you didn't mean a secure way to transfer files back and forth?  If so, then SFTP works and an SFTP server is built into the package openssh-server.

---

### Post by rusljam on 2014-03-12
Thank you. Do you mean "give the dongle a fixed ip address" is to set up an ip address for the wlan interface associated with wifi dongle? And about sftp, in my case ftp is preferable because I need very little security and ftp is more common and it is integrated in many file managers.

---

### Post by Lars Noodén on 2014-03-12
Yes, the interface associated with the dongle needs the fixed ip address.  Then ISC DHCP or Dnsmasq can work from there.  

About [FTP](http://www.openlogic.com/wazi/bid/188103/Stop-Using-FTP-How-to-Transfer-Files-Securely), not only is it incurably insecure, it is very hard to set up.  If you install SFTP (as part of openssh-server) you do not have to fiddle with anything.  Nautilus, PCManFM and the other file managers support SFTP by default and even specialized tools like FileZilla do as well.  Please give it a try first, it should save you a lot of effort as well as meaning a lot for security.

---

### Post by rusljam on 2014-03-12
Thank you very much! This is exactly what I asked for.   You are right. SFTP is included in common android file managers. So I'll try it.

---

