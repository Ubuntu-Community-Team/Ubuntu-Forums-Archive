---
title: "Trying to install WNDA3100v2, Won't Connect to Wireless Network"
date: 2014-12-14
forum: Networking &amp; Wireless
---

### Post by Nathan_Patera on 2014-12-14
Hello I am new to the forums and I have a problem with my USB NetGear WNDA3100v2 Broadcom CM4334.
To install I did:
So I tried to follow this forum:
[http://ubuntuforums.org/showthread.php?t=1964173](http://ubuntuforums.org/showthread.php?t=1964173)
In which @chili555 was responding how to install it.
I started with the command **lsusb** and located this line:
```

Bus 001 Device 009: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]

```
I then downloaded this file via USB which chili555 attached to one of his posts:
[http://ubuntuforums.org/attachment.php?attachmentid=216486&d=1335215580](http://ubuntuforums.org/attachment.php?attachmentid=216486&d=1335215580)
I extracted the files
I then ran **arch** and got:
```
x86_64
```
So I have a 64 bit architecture, and you would have 32 bit architecture if you have gotten **i686**.
So I installed "synaptic" and "ndiswrapper" via USB. (Not sure if synaptic was necessary to install)
Then I installed the driver file bcmn43xx**64**.inf (replace 64 with 32 if you have gotten i686):
```

sudo ndiswrapper -i bcmn43xx64.inf
couldn't find SourceDisksFiles section - continuing anyway...
installing bcmn43xx64 ...

```
I am not sure if it is bad if it couldn't find SourceDiskFiles section, but it says it was installed.


I then verified If it was installed and it was:
```

sudo ndiswrapper -l
bcmn43xx64 : driver installed
    device (0846:9011) present
```


I then went to see if a Network Interface was created and it wasn't:
```

dmesg | grep ndis


iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.

```
**dmesg | grep ndis** returned nothing and went to the next line.


I continued with the forum and they activated it by running the following:
```
sudo modprobe ndiswrapper
```


I ran to see if a Network Interface was created and it was this time:
```

dmesg | grep ndis
[ 2470.689584] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[ 2470.696836] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[ 2470.971476] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[ 2471.517190] usbcore: registered new interface driver ndiswrapper
[ 2542.822095] ndiswrapper: device wlan0 removed
[ 2548.125110] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[ 3387.754716] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
[ 3411.054544] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
[ 5036.595138] ndiswrapper: device wlan0 removed
[ 5062.409315] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
iwconfig
eth0      no wireless extensions.


wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


lo        no wireless extensions.

```


Now Here is the problem, Every time I go up and select a network enter my password and then it tries to connect, it does not connect and it keeps asking for the Wireless Password and it does connect. The wireless Icon above keeps showing its loading and loading. Can anyone help me with my dilemma?

---

### Post by chili555 on 2014-12-14
I suggest you use the amended version from post #6 here: [http://ubuntuforums.org/showthread.php?t=1964173&p=11867790#post11867790](http://ubuntuforums.org/showthread.php?t=1964173&p=11867790#post11867790) My memory is a bit hazy but I believe I changed a line or two for just this issue:> sudo ndiswrapper -i bcmn43xx64.inf
[COLOR="#FF0000"]couldn't find SourceDisksFiles section - continuing anyway...[/COLOR]
installing bcmn43xx64 ...If you need guidance as to how to erase the faulty files you have and install these, please post back.

---

### Post by Nathan_Patera on 2014-12-14
Thank you for responding:
I did try to install the amended ones, but first I removed the driver by running **sudo ndiswrapper -r bcmn43xx64**, and then I repeated the installation process and received the same error:
```
couldn't find SourceDisksFiles section - continuing anyway...
```

Any ideas?

---

### Post by chili555 on 2014-12-14
After you removed the first, what remained in /etc/ndiswrapper? Nothing, I hope.```
sudo rm -rf /etc/ndiswrapper/*
```

---

### Post by Nathan_Patera on 2014-12-14
It returned nothing as you hoped for.

---

### Post by chili555 on 2014-12-14
> **Nathan_Patera said:**
> It returned nothing as you hoped for.If you have installed the inf file from 'v2_amended' and found no success, I fear I have no other suggestions. Sorry.

---

### Post by Nathan_Patera on 2014-12-14
> **chili555 said:**
> If you have installed the inf file from 'v2_amended' and found no success, I fear I have no other suggestions. Sorry.

Thank you for trying anyways chili555, Any other suggestions anyone?

---

### Post by Caysho on 2014-12-17
> Now Here is the problem, Every time I go up and select a network enter my password and then it tries to connect, it does not connect and it keeps asking for the Wireless Password and it does connect. The wireless Icon above keeps showing its loading and loading. Can anyone help me with my dilemma?

Open a terminal window and run
```

sudo tail -f /var/log/syslog

```

Then do the connection.
Post the output from that terminal window, might get a better idea on what is happening.

---

