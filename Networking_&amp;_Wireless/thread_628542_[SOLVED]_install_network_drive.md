---
title: "[SOLVED] install network drive"
date: 2007-12-01
forum: Networking &amp; Wireless
---

### Post by Marco_Polo on 2007-12-01
I have a Lacie Ethernet Disk Mini ([http://www.lacie.com/us/products/product.htm?pid=10843](http://www.lacie.com/us/products/product.htm?pid=10843)) which I would like to use access through my home network to backup my machine.  The manual says to plug the drive into the router, then access its configuration pages by entering "http://edmini" in a browser.  This page is not found, though.  Has it been assigned an IP?  How would I discover that address?  Thanks for any help.

---

### Post by victorbrca on 2007-12-01
You could check your router for lease IPs. It will probably be under status and DHCP clients.

if you want to get fancy you can also run nmap on your LAN. I don't think the shell version came installed by default on Dapper, and the GUI interface doesn't scan the whole subnet.

Install nmap:
```
sudo apt-get install nmap
```

Search for the device:
```
nmap <your subnet>/<mask numeral>
# e.g.:
nmap 192.168.1.0/24
```


Vic.

---

### Post by Marco_Polo on 2007-12-04
Thanks, Victor.  I'll try that tonight.  I guess what I'm trying to do is to use the drive as a server which I can log into (with ssh?) to store big tar files.  Is that the way that network drives are generally used?  After searching this topic I see a lot of talk about Samba.  But my understanding is that I won't need Samba since it's not a Windows drive.  Is that right?  Anyway, I'm not sure how to configure this guy yet.  I'll search for the IP and go from there.

---

### Post by timcredible on 2007-12-04
go to your router and find out what dhcp addresses it's handed out, that will tell you the ip address of your network drive.

---

### Post by victorbrca on 2007-12-04
> **Marco_Polo said:**
> Thanks, Victor.  I'll try that tonight.  I guess what I'm trying to do is to use the drive as a server which I can log into (with ssh?) to store big tar files.  Is that the way that network drives are generally used?  After searching this topic I see a lot of talk about Samba.  But my understanding is that I won't need Samba since it's not a Windows drive.  Is that right?  Anyway, I'm not sure how to configure this guy yet.  I'll search for the IP and go from there.

For this device you can not use SSH, it's not supported. You have to logon via a browser to do any configuration that you may want, and use Samba for file sharing. 

Samba can be used either for Linux or Windows. 

Check "Network protocols" under the specification tab on the link that you posted.

> **timcredible said:**
> go to your router and find out what dhcp addresses it's handed out, that will tell you the ip address of your network drive.

I agree, this is the best option. The device is pre-configured for DHCP as per Lacie's website


Vic.

---

### Post by Marco_Polo on 2007-12-05
Thanks a lot.  After crashing my network by resetting my router, then reconfiguring it I am now transferring my backup files via ftp.  Great!

---

