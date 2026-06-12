---
title: "No internet after upgrade to 17.10"
date: 2017-10-19
forum: Networking &amp; Wireless
---

### Post by beameup on 2017-10-19
I'm a sitting duck over here too after the upgrade. The only thing in my network interfaces file is 

auto lo
iface lo inet loopback

I can ping the router but that's it. I'm not getting any DNS resolve

Should I have auto eth0 in there too?

---

### Post by chili555 on 2017-10-19
We'd like to see the actual reply to:```
ping -c3 8.8.8.8
```> Should I have auto eth0 in there too?Not usually; Network Manager should do the job quite well.

---

### Post by beameup on 2017-10-19
ifconfig -a
```
 eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.28  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::290:f5ff:fef9:7088  prefixlen 64  scopeid 0x20<link>
        ether 00:90:f5:f9:70:88  txqueuelen 1000  (Ethernet)
        RX packets 4650  bytes 775566 (775.5 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 4396  bytes 491696 (491.6 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 6795  bytes 513537 (513.5 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 6795  bytes 513537 (513.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlan0: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether a0:88:69:39:b3:45  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
 
```

ping results
```
 ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=56 time=31.3 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=56 time=39.7 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=56 time=37.9 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 31.358/36.343/39.750/3.603 ms

ping -c3 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=7.83 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=6.03 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=3.97 ms

ping -c3 [www.ubuntu.com](www.ubuntu.com)
ping: [www.ubuntu.com:](www.ubuntu.com:) Name or service not known

```

iwconfig
```
iwconfig
wlan0     IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

eth0      no wireless extensions.

```

Thanks.

---

### Post by chili555 on 2017-10-19
> 
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   62893167-6aa4-3d7e-a6f4-423ca687cb5f | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.178/24
IP4.GATEWAY:                            192.168.1.1
[COLOR="#FF0000"]IP4.DNS[1]:                             8.8.8.8
IP4.DNS[2]:                             8.8.4.4
[/COLOR]Do these settings come from the router; i.e. is Network Manager set for DHCP or are there custom settings that you've added?> 
ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=56 time=31.3 ms
You are getting to the internet, but no names are resolved.

Interesting.

BTW, I have upgraded to 17.10 and everything works as expected. I don't suspect a systemic issue or bug, so far.

---

### Post by beameup on 2017-10-19
No custom settings, DHCP is set to automatic. 
I get a ? across my network icon. Wireless doesn't work either. 
But I can get across my internal network OK :)
I rebooted the router for good measure. 

the broadcast IP is internal, that should be my external IP.

---

### Post by beameup on 2017-10-19
Now it gets interesting. 
I use PIA vpn. Just turned it on and I'm connected to the internet. Go figure.

---

### Post by wildmanne39 on 2017-10-19
Please do not hijack someone else's thread it is better to start your own so both of you can get the help you deserve.

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Thanks

---

### Post by beameup on 2017-10-19
> **wildmanne39 said:**
> Please do not hijack someone else's thread it is better to start your own so both of you can get the help you deserve.

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Thanks

My apologies. It looked like the same issue to me.

---

### Post by beameup on 2017-10-20
Well this just keeps getting weirder for me.
I removed PIA and it didn't change anything. I removed the network connection via NM and added another.
I tried OpenDNS in the settings. Reboot, reboot, still no connection.
What's really strange is that I can open a Kubuntu Virtual Machine on the same laptop (System76 Kudo) and it will connect to the internet no problem.
VirtualBox using a bridged connection. Settings are identical to the main machine.
So something is blocking that network adapter mac address maybe?

I also have a vanilla Ubuntu installed on a virtual machine on my MacMini. Just testing the beta out. Guess what? No network connection today.
Totally different machine. I have no idea? But that one is easy. I can just remove it.

So in the meantime, I'll just put PIA back on and let it load at startup until I can sort it out.

---

### Post by beameup on 2017-10-20
Fixed!  This link
```
https://askubuntu.com/questions/622470/dns-probe-finished-bad-config-error-in-ubuntu-14-04/622493#622493
```

These commands
```


sudo dpkg-reconfigure resolvconf

Say yes to "prepare /etc/resolve.conf for dynamic updates?"

sudo reboot


```

---

### Post by Kris_M on 2017-10-20
credit beameup: This link:```
https://askubuntu.com/questions/622470/dns-probe-finished-bad-config-error-in-ubuntu-14-04/622493#622493
```


Which says:
> I solved this error by deleting /etc/resolv.conf and recreating the symbolic link.


You can do that using the following commands:


```
sudo rm /etc/resolv.conf
sudo ln -s ../run/resolvconf/resolv.conf /etc/resolv.conf
sudo resolvconf -u
```


execute those lines one at a time
I added 
```
sudo service network-manager restart
```

---

### Post by offers-hopefamily on 2017-10-21
> **Kris_M said:**
> Thanks!
execute those lines one at a time
I added 
sudo service network-manager restart

Worked for me wthout the network-manager restart
Desktop machine upgrade without problem (no wifi)  but lost all network connectivity on laptop. Thank goodness I had a desktop to troubleshoot.

---

### Post by Kris_M on 2017-10-21
Yup!!! Thanks to @beameup for finding and posting that!!!

---

### Post by beameup on 2017-10-24
Let me add this little tidbit of info that may help someone. (Compliments to the PIA forum)

```


edit /etc/NetworkManager/NetworkManager.conf as root. 
under the [main] section, if there is no dns setting, add:

dns=dnsmasq

Save
Then restart NetworkManager:  sudo systemctl restart NetworkManager

```

---

### Post by Zoot_Nerper on 2017-10-25
I had wifi with 17.04, but not after a clean install of Ubuntu 17.10  with all updates and Intel microcode additional driver installed.

If  I try the 3 lines above after the first two I lose my wired LAN, then  for the third it says resolvconf does not exist. Nor can I install it  (no internet)

Reinstalled clean 17.10. Installed resolvconf.  Three lines and a restart of NerworkManager and wifi was on, I could see  local networks, but I could not connect to mine. Restarted the router  and still no connect. 

After a reboot, no wifi and it will not turn on. Ran the commands again and it still will not turn on.

Any additional suggestions?

---

### Post by Zoot_Nerper on 2017-10-25
I just tried this:

sudo dpkg-reconfigure resolvconf

Now, after a reboot, I have wifi on but I still cannot connect.

---

### Post by beameup on 2017-10-25
you tried the dnsmasq fix too?

---

### Post by dankegel on 2017-10-25
Thanks!  This was driving me nuts.

The suggestion "sudo dpkg-reconfigure resolvconf, answering 'yes'" fixed it for me.

Unfortunately it comes back every time I use openvpn.

Filed [https://bugs.launchpad.net/ubuntu/+source/openvpn/+bug/1727368](https://bugs.launchpad.net/ubuntu/+source/openvpn/+bug/1727368)

---

### Post by ja-muguerza on 2017-10-28
Thanks a lot! The solution  of recreating the symbolic link to /etc/resolv.conf and restarting network manager worked perfectly fro me!  :D 
It was driving me crazy, I was even considering to downgrade to last Ubuntu LTS version...

---

