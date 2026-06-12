---
title: "Internet Connection Sharing Withou A Router!"
date: 2007-07-10
forum: Networking &amp; Wireless
---

### Post by Del Piero on 2007-07-10
First of all hello, i am a newbie to the linux world and i need help. I have 2 computers, the one i am using which is a dual boot machine (Win XP, Ubuntu) and another XP machine. The Ubuntu machine is connected to the Internet through a usb speedtouch modem and connected to the other machine with a direct cable (2 x 10/100 cards no router). I have set up a windows network with the other xp machine from my xp (file sharing, Internet sharing). And i want to do the same when i am on ubuntu share files and the internet connection or at least the connection. Note that i am a complete newbie with linux. thanks for reading this....:)

Edit: can someone please correct the thread name?

---

### Post by scrooge_74 on 2007-07-10
Maybe this will help, check the community documents

[https://help.ubuntu.com/community/InternetConnectionSharing?highlight=%28internet%29](https://help.ubuntu.com/community/InternetConnectionSharing?highlight=%28internet%29)

---

### Post by Del Piero on 2007-07-10
> **scrooge_74 said:**
> Maybe this will help, check the community documents

[https://help.ubuntu.com/community/InternetConnectionSharing?highlight=%28internet%29](https://help.ubuntu.com/community/InternetConnectionSharing?highlight=%28internet%29)

Thanks man, but this is talks about internet sharing from Ubuntu to Ubuntu as far as i understand..:confused:

---

### Post by Mr. C. on 2007-07-10
To share your connection, you enable routing on your system:

```
echo 1 > /proc/sys/net/ipv4/ip_forward    
```

Bring up both interfaces.
Ensure there is only 1 default route (it will be the IP address of your internet connection's interface).  The command:

```
netstat -rn
```

will show you the route table.

MrC

---

