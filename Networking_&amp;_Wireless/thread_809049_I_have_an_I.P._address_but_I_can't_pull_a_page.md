---
title: "I have an I.P. address but I can't pull a page"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by mike214 on 2008-05-27
So I'm a Newbie and I've had Ubuntu for a couple months now and I've got to say I really like it. I haven't had that many problems with it that I couldn't find the solution for online. However, yesterday out of no where my wired internet connection just stops working. This is really frustrating because I'm getting an I.P. address but I'm not able to pull a page. When I go to network properties (from the panel) I see sent and received packets but when I go to configure it is says that interface doesn't exist. Now when I do an ifconfig it shows up with an i.p. the RX and TX packets look odd  it says RX 1512 errors 0 dropped 0 overruns 0 frames and TX 110 errors 0 dropped 0 overruns 0 frames.Is that normal? When I try to do a sudo  ifconfig eth0 up it says unable to resolve host. I have windows machines on the same network and they all work fine. My laptop worked fine too until yesterday. It might have done some updates since the GUI looks a little diffrent. I've been dealing with this for two days and there's no wireless where i'm at can anyone help??

---

### Post by superprash2003 on 2008-05-27
since you are getting an ip.. try pinging your router and post output here

---

### Post by mike214 on 2008-05-27
mike@mike-laptop:~$ ping -b  192.168.1.1
PING 172.17.98.65 (172.17.98.65) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=255 time=1.44 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=255 time=1.46 ms
64 bytes from 192.168.1.1 : icmp_seq=3 ttl=255 time=1.47 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=255 time=1.87 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=255 time=1.90 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=255 time=0.911 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=255 time=1.94 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=255 time=0.939 ms

I also pinged google and it was successful.

---

### Post by mapes12 on 2008-05-27
> When I try to do a sudo ifconfig eth0 up it says unable to resolve host. 

Have a look at ```
cat /etc/resolv.conf
```

to see if you are being allocated a nameserver by DNS then follow this page for more help:

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#head-1b12c0a8c765a0d0d623e3ee60daf197a5bf2b59](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#head-1b12c0a8c765a0d0d623e3ee60daf197a5bf2b59)

EDIT: On the same page check carefully any issues you may have if you have used ndiswrapper to configure your eth or wifi connection agains any supported drivers loaded in your kernel.

---

### Post by yogo on 2008-05-27
Also try locking fire-starter, I have at times had that get out of sync when switching modes on my router.

---

### Post by superprash2003 on 2008-05-27
try changing DNS servers to opendns [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by mike214 on 2008-05-27
I inputed the command and I received the DNS information no problem. I never installed firestarter does it come in the build and if so where is it located I tried looking but i couldn't find it.

---

### Post by mapes12 on 2008-05-27
```
I never installed firestarter does it come in the build and if so where is it located I tried looking but i couldn't find it.
```

Firestarter is not a default application. You have to install it. So, if you haven't done so then it won't be on your system.

OK. You can see a nameserver = good. BUT the IP address may be cached. Please could you post the output from ```
sudo dhclient
```

---

### Post by kevdog on 2008-05-27
You might make sure that you have a gateway specificed with the route -n statement also.  Likely its either a gateway non specified or dns problem.

---

