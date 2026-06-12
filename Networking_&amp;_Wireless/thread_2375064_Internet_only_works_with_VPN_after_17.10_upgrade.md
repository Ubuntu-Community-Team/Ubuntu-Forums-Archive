---
title: "Internet only works with VPN after 17.10 upgrade"
date: 2017-10-21
forum: Networking &amp; Wireless
---

### Post by cjohns38 on 2017-10-21
After updating to 17.10 if I restart my computer the internet doesn't work (wireless / ethernet).  However, I noticed beameup on this post ([https://ubuntuforums.org/showthread.php?t=2374857](https://ubuntuforums.org/showthread.php?t=2374857)) mentioned that when he flipped on his VPN (Private Internet Access - aka PIA) things started working.  I have PIA so I flipped it on and I was able to connect to the net as well.  In fact, if I'm connected to the VPN my wireless shows up as a normal working icon.  If the VPN is off it shows up as a question mark and nothing works.  Unlike beameup the "sudo dpkg-reconfigure resolveconf" didn't do the trick for me.  How do I get this resolved?

Steps I've tried....
[LIST]
[*]dpkg-reconfigure resolveconf
[*]dnsmasq - [https://askubuntu.com/questions/966743/no-internet-after-upgrading-from-17-04-to-17-10](https://askubuntu.com/questions/966743/no-internet-after-upgrading-from-17-04-to-17-10)
[*]Hadaka's steps redoing interfaces file ([https://ubuntuforums.org/showthread.php?t=2374838](https://ubuntuforums.org/showthread.php?t=2374838))
[*]Set IP4 values to 8.8.8.8, 8.8.4.4 turned off IP6
[/LIST]

Config output (No VPN) 
[eth0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500        ether 00:90:f5:ea:54:c7  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 20  memory 0xf7e00000-f7e20000  


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 7623  bytes 693829 (693.8 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 7623  bytes 693829 (693.8 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlan0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.86.135  netmask 255.255.255.0  broadcast 192.168.86.255
        inet6 fe80::ba76:3fff:fe78:e9f3  prefixlen 64  scopeid 0x20<link>
        ether b8:76:3f:78:e9:f3  txqueuelen 1000  (Ethernet)
        RX packets 896  bytes 261407 (261.4 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 665  bytes 142825 (142.8 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0]

iwonconfig
[wlan0     IEEE 802.11  ESSID:"ShadowsAlley"            Mode:Managed  Frequency:5.745 GHz  Access Point: 70:3A:CB:63:8F:B3   
          Bit Rate=243 Mb/s   Tx-Power=17 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:120   Missed beacon:0]

ping test to 8.8.8.8 (no VPN) 
[PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.64 bytes from 8.8.8.8: icmp_seq=1 ttl=56 time=75.3 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=56 time=266 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=56 time=26.4 ms


--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 26.440/122.745/266.437/103.550 ms]

---

### Post by pat-pathmanathan on 2017-10-22
I have the same problem whether the connection is wired or wireless it will not connect to the Internet unless vpn is connected.

wireless-info (**with vpn** connected and **access to internet**)
[http://paste.ubuntu.com/25794988/](http://paste.ubuntu.com/25794988/)

wireless-info (**without vpn** connected and **no access to internet**)
[http://paste.ubuntu.com/25795041/](http://paste.ubuntu.com/25795041/)

Thanks

---

### Post by cjohns38 on 2017-10-22
Are you using PIA as well?

---

### Post by pat-pathmanathan on 2017-10-22
Yes

---

### Post by wondringaloud on 2017-10-22
I have the same issue. Using Wired connection. Works after I start PIA.

---

### Post by jeremy31 on 2017-10-22
Some of you should try [https://ubuntuforums.org/showthread.php?t=2374857&p=13700631#post13700631](https://ubuntuforums.org/showthread.php?t=2374857&p=13700631#post13700631) even if it didn't work for cjohns38

---

### Post by pat-pathmanathan on 2017-10-23
> **jeremy31 said:**
> Some of you should try [https://ubuntuforums.org/showthread.php?t=2374857&p=13700631#post13700631](https://ubuntuforums.org/showthread.php?t=2374857&p=13700631#post13700631) even if it didn't work for cjohns38

Thanks you for your help **jeremy31**, but unfortunately it **did not work**.:sad:

---

### Post by cjohns38 on 2017-10-23
I wonder if it has something to do with the PIA software?

---

### Post by ghoracek on 2017-10-24
This worked for me.  I'm not on PIA.  I'm on expressvpn.  
Both a desktop and a laptop were affected.  
deleting /etc/resolv.conf and recreating the symbolic link allows me to connect both by ethernet and wireless without signing on to vpn first.  

Mixed emotions: the problem insured that I always had to use vpn; the fix lets me connect without vpn which is maybe not as good (but increases my flexibility).

Thanks to all.  I was expecting to fight this for a week instead of a couple of hours.

glh

---

### Post by pat-pathmanathan on 2017-10-24
I have managed to successfully ping the **bbc.com** website using the ip address **without the vpn** connection.

```
PING 212.58.246.78 (212.58.246.78) 56(84) bytes of data.
64 bytes from 212.58.246.78: icmp_seq=1 ttl=53 time=21.1 ms
64 bytes from 212.58.246.78: icmp_seq=2 ttl=53 time=22.3 ms
64 bytes from 212.58.246.78: icmp_seq=3 ttl=53 time=20.1 ms
64 bytes from 212.58.246.78: icmp_seq=4 ttl=53 time=20.2 ms
64 bytes from 212.58.246.78: icmp_seq=5 ttl=53 time=20.4 ms
64 bytes from 212.58.246.78: icmp_seq=6 ttl=53 time=20.4 ms
64 bytes from 212.58.246.78: icmp_seq=7 ttl=53 time=19.6 ms
64 bytes from 212.58.246.78: icmp_seq=8 ttl=53 time=20.1 ms
64 bytes from 212.58.246.78: icmp_seq=9 ttl=53 time=20.8 ms
64 bytes from 212.58.246.78: icmp_seq=10 ttl=53 time=20.5 ms
64 bytes from 212.58.246.78: icmp_seq=11 ttl=53 time=20.1 ms
64 bytes from 212.58.246.78: icmp_seq=12 ttl=53 time=20.1 ms
64 bytes from 212.58.246.78: icmp_seq=13 ttl=53 time=20.1 ms
64 bytes from 212.58.246.78: icmp_seq=14 ttl=53 time=19.6 ms
64 bytes from 212.58.246.78: icmp_seq=15 ttl=53 time=19.9 ms
64 bytes from 212.58.246.78: icmp_seq=16 ttl=53 time=20.1 ms
^C
--- 212.58.246.78 ping statistics ---
16 packets transmitted, 16 received, 0% packet loss, time 15021ms


```

If tried to ping using the domain name **without the vpn** connection the following message displayed.


```
ping: bbc.com: Name or service not known
```

So I think the problem is not finding the dns without the vpn connection. I do not know how to fix this.

---

### Post by pat-pathmanathan on 2017-10-24
I tried the steps in the link **jeremy31** posted again and it worked. There is a mistake in the second step.

```
sudo rm /etc/resolv.conf
sudo ln -s ../run/resolvconf/resolv.conf /etc/resolv.conf
sudo resolvconf -u
```

It should be ```
sudo ln -s /run/resolvconf/resolv.conf /etc/resolv.conf

```

---

### Post by beameup on 2017-10-24
But does it stick? Tried running the VPN and turning it off? Or rebooting?
I've had it revert a couple times. But I know what to do now.

What's not helping me is my ISP has been intermittent lately :(

---

### Post by pat-pathmanathan on 2017-10-25
> **beameup said:**
> But does it stick? Tried running the VPN and turning it off? Or rebooting?
I've had it revert a couple times. But I know what to do now.

What's not helping me is my ISP has been intermittent lately :(

It seems to work for all the above situations.

---

### Post by beameup on 2017-10-25
> **pat-pathmanathan said:**
> It seems to work for all the above situations.

Adding the dnsmasq to Networkmanager.conf seems to have worked for me.

So should we consider this a bug? Looks like it's not isolated to PIA users, and I also had that vanilla Ubuntu VM on a Mac that lost connectivity too.

---

### Post by pat-pathmanathan on 2017-10-26
> **beameup said:**
> Adding the dnsmasq to Networkmanager.conf seems to have worked for me.

So should we consider this a bug? Looks like it's not isolated to PIA users, and I also had that vanilla Ubuntu VM on a Mac that lost connectivity too.

I never reported a bug and don't know where to start. You seem to be very knowledgable so up to you.

---

### Post by beameup on 2017-10-26
> **pat-pathmanathan said:**
> I never reported a bug and don't know where to start. You seem to be very knowledgable so up to you.

Well thanks for that! :D  A bug has already been filed. I need to jump on a "me too" addition.

See this post
```
https://ubuntuforums.org/showthread.php?t=2374857&p=13702946#post13702946
```

---

### Post by cjohns38 on 2017-10-26
I've done some additional digging based on the other posts.  Seems like it has something to do with the /etc/resolv.conf.  When I'm not connected to the VPN the nameserver resolves to localhost (127.0.0.1).  Which is why you can ping but not load any sites. When you connect to the VPN and it loads a proper nameserver and then the sites resolve.  Digging through some different posts it seems like this was also a problem with 17.04 ([https://github.com/cpriego/valet-linux/issues/7](https://github.com/cpriego/valet-linux/issues/7)).

---

### Post by pat-pathmanathan on 2017-10-27
> **cjohns38 said:**
> I've done some additional digging based on the other posts.  Seems like it has something to do with the /etc/resolv.conf.  When I'm not connected to the VPN the nameserver resolves to localhost (127.0.0.1).  Which is why you can ping but not load any sites. When you connect to the VPN and it loads a proper nameserver and then the sites resolve.  Digging through some different posts it seems like this was also a problem with 17.04 ([https://github.com/cpriego/valet-linux/issues/7](https://github.com/cpriego/valet-linux/issues/7)).

Have you still not get it working? Did you try removing the /etc/resolv.conf and recreating the symbolic links as in:

> pat-pathmanathan[INDENT]                              Re: Internet only works with VPN after 17.10 upgrade
                          I tried the steps in the link **jeremy31** posted again and it worked. There is a mistake in the second step.

     Code:
     sudo rm /etc/resolv.conf
[COLOR=#ff0000]sudo ln -s ../run/resolvconf/resolv.conf /etc/resolv.conf[/COLOR]
sudo resolvconf -u 
**It should be** 
     Code:
     [COLOR=#00ff00]sudo ln -s /run/resolvconf/resolv.conf /etc/resolv.conf [/COLOR]
         [/INDENT]
    


---

### Post by jeremy31 on 2017-10-27
Another way is to ```
sudo dpkg-reconfigure resolvconf
```and answer yes to enable dynamic updates

---

### Post by pat-pathmanathan on 2017-10-27
> **jeremy31 said:**
> Another way is to ```
sudo dpkg-reconfigure resolvconf
```and answer yes to enable dynamic updates
  
I tried to see the above way will work for me but unfortunately it didn't :frown:

---

### Post by beameup on 2017-10-27
To clarify: You reboot after?

---

### Post by pat-pathmanathan on 2017-10-28
> **beameup said:**
> To clarify: You reboot after?

Silly me! I didn't **reboot**. Thanks **beameup**

---

### Post by cjohns38 on 2017-11-01
No go on the reset either way (including reboot).  Other ideas?

---

### Post by cjohns38 on 2017-11-02
I used the unbound method outlined here: [https://www.hecticgeek.com/2017/04/ubuntu-17-04-systemd-dns-issues/](https://www.hecticgeek.com/2017/04/ubuntu-17-04-systemd-dns-issues/) and it appears to be working. 

Note: Started here is says...."[COLOR=#3A3A3A][FONT=&quot]Now I actually completely re-wrote this entire article, because the previous answer (content) that I put here was not the most optimal one...." I ran through those steps and its working. [/FONT][/COLOR]

---

