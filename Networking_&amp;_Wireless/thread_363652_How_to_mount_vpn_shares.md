---
title: "How to mount vpn shares?"
date: 2007-02-17
forum: Networking &amp; Wireless
---

### Post by foxy123 on 2007-02-17
I am sorry for a stupid question, which I have already asked,but I still cannot figure it out. I can connect my work network through a vpn link. It is very easy with my work Windows laptop. I run Cisco client and everything is mounted and working.

But sometimes I either leave the laptop at work or am lazy to take it out of the case. So I want to use my personal laptop which runs Ubuntu only.

I figured out how to connect my work network using vpnc. But I cannot mount the shares now. If I run
```
route
``` I have
```
~$ route
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
mailgate.mywork 192.168.1.1     255.255.255.255 UGH   0      0        0 wlan0
100.100.100.318 *               255.255.255.255 UH    0      0        0 tun0
100.100.100.158 *               255.255.255.255 UH    0      0        0 tun0
100.100.100.0   *               255.255.255.0   U     0      0        0 tun0
174.13.100.0    *               255.255.255.0   U     0      0        0 tun0
192.168.1.0     *               255.255.255.0   U     0      0        0 wlan0
192.168.41.0    *               255.255.255.0   U     0      0        0 tun0
192.168.45.0    *               255.255.255.0   U     0      0        0 tun0
10.1.0.0        *               255.255.0.0     U     0      0        0 tun0
default         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

```

So what I should do next?

---

### Post by GrammatonCleric on 2007-02-17
Are these SMB shares or somthing else?  How are you trying to mount them?  Are you using your fstab file?  Are you using the server names (i.e. //mercury/foo)?


-GC

---

### Post by foxy123 on 2007-02-17
I tried something like that:
```
$ sudo mount -t smbfs -o username=username,password=pass //100.100.100.158/folder /home/username/rem
timeout connecting to 100.100.100.158:445
timeout connecting to 100.100.100.158:139
Error connecting to 100.100.100.158 (Operation already in progress)
11009: Connection to 100.100.100.158 failed
SMB connection failed

```

I am not sure about //100.100.100.158/folder path, but I do not know if it is possible to look up.

---

### Post by GrammatonCleric on 2007-02-17
Try this....

Create a credentials file for your login and pass:

```


sudo nano /root/.work


```Add your username and password:


```


username=your-user-name
password=your-password


```Save the file.  (i.e. crtl+x)

Make the following folder.

[CODE

sudo mkdir   /media/work/ && sudo mkdir  /media/work/folder  

[/code]


Now edit your fstab file:

```


sudo nano /etc/fstab


```Added the following.

```


//100.100.100.158/folder        /media/work/folder       smbfs           credentials=/root/.work,dmask=777,fmask=777,noatuo 0 0


```Connect to your vpn and try mounting the share.


```


sudo mount /media/work/folder   


```-GC

---

