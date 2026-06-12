---
title: "Installed properly, but not working !"
date: 2007-03-25
forum: Networking &amp; Wireless
---

### Post by Ephemeral on 2007-03-25
Hello !
SO I reinstalled, I now have Ubuntu 6.06.1 LTS.
Now, I installed ndiswrapper and installed the driver for my usb device, which is an Inventel UR054g (R01) V1.1, the driver is called Prisma02.
So I installed it properly, so when I type :

```
ndiswraper -l
```

I get :

```
eternal@eternal-desktop:~$ ndiswrapper -l
Installed ndis drivers:
prisma02                driver present, hardware present
```

So, it seems ok there.

I tried ifconfig and iwconfig :

```
eternal@eternal-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth2      IEEE 802.11b  ESSID:"Wanadoo_7271"
          Mode:Managed  Channel=1  Access Point: Invalid
          Sensitivity=0/200
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


eternal@eternal-desktop:~$ ifconfig
eth2      Link encap:Ethernet  HWaddr 00:0B:6B:9C:8F:7B
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:167 errors:0 dropped:0 overruns:0 frame:0
          TX packets:167 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:12180 (11.8 KiB)  TX bytes:12180 (11.8 KiB)
```

Finnaly, I blacklisted the following :

```
blacklist prism54
blacklist islsm_usb
blacklist islsm_pci
blacklist islsm_device
blacklist islsm_pci
```

Yet, I still can't get ANY internet !
I did the same thing as here using Kubuntu 6.10, until it crashed, and it worked fine, any help ?

---

### Post by teaker1s on 2007-03-25
first make sure you have latest ndiswrapper-utils installed (may be 1.8 or 1.9)
reboot
```
sudo modprobe ndiswrapper
```
```
lwconfig
```

---

### Post by Kobalt on 2007-03-25
Did you enter your ssid and wireless key in the /etc/network/interfaces file ?

---

### Post by Ephemeral on 2007-03-25
I have already done sudo modprobe ndiswrapper, and I installed ndiswrapper from the CD (added CD to repositories and added it with Synaptic package manager).
And yes, essid is in the interfaces file, but I don't have a WEK key (I disable it ^_____^ )
Anyways, I heard of a program called Wi-Fi Radar, is that any good, and where can I find it ?

---

### Post by teaker1s on 2007-03-25
could also be that you need later ndiswrapper and compile it, the broadcom link in my signature will get you going

---

### Post by Ephemeral on 2007-03-25
Well, I tried doing :
cd /home/eternal/Desktop/ndiswrapper-1.38
then I did :
make

But it said that it wasn't a valid operation, is it that I haven't got build-essentials, or something like that ?

---

### Post by teaker1s on 2007-03-25
yes
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show")

---

### Post by Ephemeral on 2007-03-25
Ok, well I have done EVERYTHING thatw as there, but when I do : iwconfig, it's still eth1 that shows up, wlan0 isn't even there.
Any suggestions ?

---

### Post by Ephemeral on 2007-03-25
So... I'm gonna have to bump this up once again...

---

### Post by teaker1s on 2007-03-26
you may find that your wireless is recognised as ethernet
```
sudo modprope ndiswrapper
```
```
iwconfig
``` post output

---

### Post by Ephemeral on 2007-03-30
Back from germany, and yeah, I'll try that, but I think I already did it
**be right back**

---

### Post by Ephemeral on 2007-03-30
Ok, did the whole tutorial again, and again, and again, yet I am still stuch with eth1, and I can't see wlan0 ANYWHERE !
Need helppppp !!!

---

### Post by teaker1s on 2007-03-30
f your device shows up as wlan0 then you should be able to put your data in through the System-->Administration-->Networking applet.

(If your wireless device initially shows up as eth1, go back to step 2 and comment out the eth1 line in /etc/iftab. Then resume the rest of the instructions. If you don't comment out the eth1 entry, ndiswrapper won't be able to alias the device as wlan0.)

If it is eth1 or some other name then you should put in the data in interfaces using the gedit editor as explained below and fix the name as is described later in the procedure as well.





Critical Notice: Check the file /etc/modprobe.d/ndiswrapper file and make sure that the ndiswrapper alias is wlan0 an not something else such as eth1.

Use cat to look at /etc/modprobe.d/ndiswrapper and ensure that it contains the line "alias wlan0 ndiswrapper" and nothing else:

user@ubuntu:~/bcm4311$ cat /etc/modprobe.d/ndiswrapper

Make sure that it contains only the wlan0 identifier and no other:

alias wlan0 ndiswrapper

If it contains anything else edit /etc/modprobe.d/ndiswrapper and ensure that it contains the line "alias wlan0 ndiswrapper" and nothing else:

user@ubuntu:~/bcm4311$ gksudo gedit /etc/modprobe.d/ndiswrapper

Save the file.

---

### Post by Ephemeral on 2007-03-30
I have done the 
sudo modprobe ndiswrapper
And HAVE commented out eth0 and eth1

I have done everything written, but still, nothing

---

