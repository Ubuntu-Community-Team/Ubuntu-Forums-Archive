---
title: "Building home server, looking for advice"
date: 2014-03-02
forum: Networking &amp; Wireless
---

### Post by christian12 on 2014-03-02
Hi all,

I am looking to build a server at my parent's home, as I want to sync their data to my server, same thing for my data. I already have my serverm which will be switch to a Ubuntu server, as soon as I am able to control it :)

So here's basically, what I want the server to do:

VPN
FTPS
Teamspeak
File Server, with user/password security, has I will have to control some folder (admin, non admin, etc..)
Print server (My parents still have 1 or 2 Brother USB printer)
Can send monitoring email: CPU temperature, RAID failure
Cyberpower UPS Software for Power outages

The server will be built on a Intel Raid Array, RAID 1, with 2x 1Tb. All computer that works with the server is Windows based.


I am working on ubuntu server in a Virtual machine, for testing first, how works some of the feature. Configured GUI, and already figured it out to work with PPTPD, but will change to L2TP or OpenVPN.
Next I am working now, is file server. I tried using Samba, but I can't get the permissions working.

Already looked some tutorial, but if anyone can link me some tutorial, cause I might be an IT Tech (on Windows server based system), I am new to Linux Server (Ubuntu server here :D). and while looking for some tutorial, I am lost on the procedure as sometimes, they are not the same from site to site :/

Any help will be appreciate. I have confidence that I will get these servers working :)

Thanks ):P

---

### Post by xicarusx on 2014-03-02
Use WEBMIN as a web based frontend. [www.webmin.com]("http://www.webmin.com")

It will help greatly with your SAMBA issues. For SAMBA you need to make sure the directory is owned by the group or user that is going to write to it. If the folder is owned by root, UserA wont be able to write to it unless the permissions are set to 777, and that is not recommended.

**Change Owner**
```
sudo chown userA:userA -R /path/to/your/share
```
**Change Attributes**
```
sudo chmod 755 -R /path/to/your/share
```

**To create a SAMBA share based on group.**
```
[Raspberry Pi]        comment = Raspberry Pi Files Share
        valid users = @raspberrypi
        path = /srv/raspberrypi
        write list = @raspberrypi



```

**To create a SAMBA share based on user**
```
[Raspberry Pi]
        comment = Raspberry Pi Files Share
        valid users = robert, bill, jeff, corey
        path = /srv/raspberrypi
        write list = robert, bill

```

Hope this is helpful to your project, and help to setup SAMBA properly.

---

### Post by christian12 on 2014-03-04
Thanks buddy!

I'll try and work hard on this :D

---

