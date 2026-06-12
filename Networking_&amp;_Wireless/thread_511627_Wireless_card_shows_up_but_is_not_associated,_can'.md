---
title: "Wireless card shows up but is not associated, can't find Internet"
date: 2007-07-28
forum: Networking &amp; Wireless
---

### Post by dorfird on 2007-07-28
When my computer was running Windows Vista Premium I was able to connect to our home wireless network with my wireless card (on my HP Pavilion laptop). I installed Feisty Fawn and the wireless card can't find the network - or something like that. I've been working through the [Wireless Troubleshooting Guide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#lshw"). When I get to step 3.2.4.2 and check my driver with iwconfig, I see the following:

```
eth1 unassociated  ESSIID:off/any
     Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated
     Bit Rate:0 kb/s   Tx-Power:16 dBm
     Retry Limit: 15   RTS thr:off   Fragment thr:off
     Power Management:off
     Link Quality:0  Signal level:0  Noise level:0
     Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
     Tx excessive retries:0  Invalid misc:47   Missed beacon:0
```

I suspect that I want to associate this. How do I do so?

When I did lsmod the driver was loaded.

Incidentally, is there a way to copy text from the terminal? I took a screenshot but I haven't set up my FTP on this machine yet and copy-and-paste would have been much faster than typing.

Thanks in advance. I'm about to go to bed but hope to have time to check the forum in the morning and answer any clarifying questions you all have.

---

### Post by cruzer45 on 2007-07-28
Hey there i know how you feel.... I just got mine working after 2 weeks of wired connection sifting through the forums.   Thank goodness today i found this documentation and it solved my problems. i used the fwcutter tool......

Just follow the documentation from section 1.3 and you should be clear... wne your done don't forget to reboot and make sure your wireless button is on. 

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty")http://

---

### Post by dorfird on 2007-07-28
Thank you for the tip, however it did not help.

Forgot to mention it last time but I am using a PRO/Wireless 3945ABG Network Connection card. ```
Logical name: eth1 Driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0 () latency=0 multicast=yes wireless=unassociated
```

---

### Post by chili555 on 2007-07-28
Association involves telling your interface which network, or ESSID you want to connect to, supplying any encryption details, WEP, WPA, etc. and then then commanding it to connect, either DHCP or static. Network Manager is supposed to simplify all these details, but I prefer the command line. Lets go!

```
sudo iwlist eth1 scan
```This will give you a list of the available networks your interface can see, for example:```
Cell 01 - Address: 99:9C:41:19:58:77
                    ESSID:"myrouter1"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=83/100  Signal level=-51 dBm  Noise level=-51 dBm
                    Extra: Last beacon: 260ms ago
``````
sudo iwconfig eth1 essid myrouter1
sudo iwconfig eth1 key 0123456789
sudo dhclient eth1
```You should then connect.

---

### Post by dorfird on 2007-07-28
> **chili555 said:**
> 

```

sudo iwconfig eth1 key 0123456789

```
```
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "0123456789".

```

The key is the same as the password for the wireless network, right? I double checked the password spelling with my husband, who set up the network, but I still get the above error.

---

### Post by fizikz on 2007-07-29
I'm in exactly the same situation, and I get the same error as the OP. I'll be keeping an eye on this thread. If I find a solution, I'll post.

---

### Post by fizikz on 2007-07-30
I got my problem solved. I don't know if it will help your specific problem, but here's what worked for me. I had to enable SSID broadcasting on my router. I had previously turned this feature off as a security measure. Now with it enabled everything is working fine. FYI, I'm using Ubuntu 6.06 and Intel's drivers ipw3945 as well as wpasupplicant and gnome network manager. I hope it gets worked out for you.

---

### Post by dorfird on 2007-08-28
I just got a new router for other reasons and SSID is enabled on it. But I still get the above error message. Also, my new password includes spaces - how would I designate the string in the terminal? Enclose it in quotes?

Thanks.

---

### Post by dorfird on 2007-09-02
> **fizikz said:**
> I'm in exactly the same situation, and I get the same error as the OP. I'll be keeping an eye on this thread. If I find a solution, I'll post.

The error associated with the key was because I was entering my password in ascii. A fter reviewing the man file, I learned that you have to enter it in hex or else put s: before it (s:password).

---

### Post by Zorael on 2007-09-02
So did you get it to work? I end up in an unassociated state and then it can't even discover networks through a sudo iwlist scan. I have to reboot or stop and reload the ipw3945 driver module. Copy/paste from another post of mine:

```
$ sudo modprobe -r ipw3945
$ sudo modprobe ipw3945
```


It works effortlessly for some, and just awful for us others.


[http://ubuntuforums.org/showthread.php?t=533331](http://ubuntuforums.org/showthread.php?t=533331)
[http://ubuntuforums.org/showthread.php?p=3297574](http://ubuntuforums.org/showthread.php?p=3297574)

[https://bugs.launchpad.net/ipw3945/+bug/134515](https://bugs.launchpad.net/ipw3945/+bug/134515)

---

### Post by dorfird on 2007-09-15
Well, I seem to be connected but there is no IP address assigned. I looked at 3.4 of the [Wireless troubleshooting doc]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#config") and tried to assign the same IP address as I see assigned to my wired connection.

```
$ sudo ifconfig eth1 down
$ sudo ifconfig ip addr 192.168.1.7 netmask 255.255.255.0 broadcast 192.168.1.255 up
addr: Unknown host
ifconfig: `--help' gives usage information.

```

Also, if I try ifconfig --help it gives me a > prompt, which I don't know what to do with.

Looking at man ifconfig, I didn't see the **ip addr** argument documented, but rather the correct syntax seems to be **address**. But when I tried it that way, I got a lot more error messages:

```
ada@Ada-laptop:~$ sudo ifconfig address 192.168.1.7 netmask 255.255.255.0 broadcast 192.168.1.255 up
SIOCSIFADDR: No such device
address: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
SIOCSIFBRDADDR: No such device
address: ERROR while getting interface flags: No such device
address: ERROR while getting interface flags: No such device

```

---

### Post by kevdog on 2007-09-16
This:

```
sudo ifconfig address 192.168.1.7 netmask 255.255.255.0 broadcast 192.168.1.255 up
```

should be:

```
sudo ifconfig *eth1 *address 192.168.1.7 netmask 255.255.255.0 broadcast 192.168.1.255 up
```

---

### Post by dorfird on 2007-09-16
```
$ sudo ifconfig eth1 address 192.168.1.7 netmask 255.255.255.0 broadcast 192.168.1.255 up
address: Unknown host

```

---

### Post by dorfird on 2007-09-18
I wondered if it was a problem that I used the exact same IP address in the above command as my wired connection was using. I also tried an IP address with the last digit offset by one, and got the same error,

---

### Post by kevdog on 2007-09-18
Check the syntax of the above command b/c it seems that error is suggesting a syntax problem.  I looked at the man pages but it didnt help me.  Try googling around for some similar examples

---

### Post by dorfird on 2007-09-18
Correct syntax is below. It does not include the word *address*.

> **dorfird said:**
> ```
$ sudo ifconfig eth1 192.168.1.7 netmask 255.255.255.0 broadcast 192.168.1.255 up
address: Unknown host

```

---

### Post by dorfird on 2007-09-18
So I have the correct syntax now to use ifconfig to assign an IP address, but I still get no joy from my wireless connection.

```
eth1      Link encap:Ethernet  HWaddr 00:18:DE:7F:7C:FC  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:127 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0xe000 Memory:d8000000-d8000fff 


```

What should I try next?

---

### Post by johnn1949 on 2007-09-29
I have a iwp3945 on a Dell6400 that saw the network but would not connect.  I notice there was no eth1 entry in the /etc/network/interfaces .
-----------------------------
auto lo
iface lo inet loopback


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
---------------------------------------

I added this to the end of the list.

auto eth1
iface eth1 inet dhcp
------------------------------------
new file is
-----------------------------

auto lo
iface lo inet loopback


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto eth1
iface eth1 inet dhcp
--------------------------------



Everthing works now

---

### Post by dorfird on 2007-10-06
I invited a friend over who helped me get my wireless connection working. We switched the router's encryption type from WPA to WEP and it works now.

---

