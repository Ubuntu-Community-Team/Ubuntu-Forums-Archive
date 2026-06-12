---
title: "Urgent! not given the option to connect via wireless!"
date: 2008-07-11
forum: Networking &amp; Wireless
---

### Post by Caponetta on 2008-07-11
Im running Ubuntu 8.04 64bit on duel boot with windows XP. I really want to delete the XP partition but I can't until I get wireless working on Ubuntu.

Adapter is the Net Gear WG111t. I followed all the instructions to get the driver on using ndiswrapper. But.. when I boot I get an orange triangle over my network icon. I right click and I can not connect wirelessly.

I even run 
```
sudo modprobe ndiswrapper
```
in the terminal but it wont work. Ive tried booting with out the adapter plugged in than using the command than plugging in.. nothing!

Please help.
Thanks in advance.

---

### Post by mriedel on 2008-07-11
What does

```
iwconfig
```

output for you?

---

### Post by Caponetta on 2008-07-11
> **mriedel said:**
> What does

```
iwconfig
```

output for you?

Hold on im going to sign on ubuntu forums via laptop and bootup in ubuntu. Update in 3 minutes.

---

### Post by Mysterious_Name on 2008-07-11
I'm going to follow along on this as I'm having the same problem in 8.04 with a Broadcom 802.11 b/g WLAN.

---

### Post by Caponetta on 2008-07-11
Sudo iwconfig```

[sudo] password for john:
lo              no wireless extensions.


eth0            no wireless extensions.
```

---

### Post by Mysterious_Name on 2008-07-11
I get the same result from iwconfig.  I'm also on a 64 bit system, although Vista not XP.  Where did you find ndiswrapper to download?

---

### Post by Caponetta on 2008-07-11
> **Mysterious_Name said:**
> I get the same result from iwconfig.  I'm also on a 64 bit system, although Vista not XP.  Where did you find ndiswrapper to download?


packages.ubuntu.com

download the ndisgtk, ndiswrapper common and, ndiswrapper utils

---

### Post by Mysterious_Name on 2008-07-11
do i have to do this with synaptic or aptitude (says to but don't know how) or can I just download them

---

### Post by Mysterious_Name on 2008-07-11
that was a dumb question, i got them downloaded to my desktop

---

### Post by Caponetta on 2008-07-11
> **Mysterious_Name said:**
> do i have to do this with synaptic or aptitude (says to but don't know how) or can I just download them

please don't hi-jack my thread as you are way behind. There are many manuals just google [adapter name] ubuntu.

---

### Post by Caponetta on 2008-07-11
> **mriedel said:**
> What does

```
iwconfig
```

output for you?

  my answer is posted above -_-
no wireless extensions.

---

### Post by Caponetta on 2008-07-11
sudo iwconfig

lo              no wireless extensions.
eth0            no wireless extensions.

---

### Post by mriedel on 2008-07-12
> **Caponetta said:**
> my answer is posted above -_-
no wireless extensions.

Why do you re-quote my question that you've answered before, saying that you've answered it before? ;)

Anyway, please post the output of

```
ndiswrapper -l
```

and

```
ifconfig
```

Do you have an Ethernet/LAN adapter (other than your WLAN device)?

---

### Post by m_ad on 2008-07-19
I'm having the same problem with the same device. I've installed the drivers, and 'ndiswrapper -l' shows the driver as installed. I do have another Ethernet card in the computer, as I did use it at one time for a wired connection. I moved it downstairs and connected it with this device for the wireless connection.

I am running Xubuntu 8.04.1

here is my ifconfig output:

```
eth0    Link encap:Ethernet  HWaddr 00:0f:1f:48:e5:a6
        UP BROADCAST MULTICAST MTU:1500 Metric:1
        RX packets:0 errors:0 dropped:0 overruns:0 frame:0
        TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:1000
        RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
        Interrupt:20


lo      Link encap:Local Loopback
        inet addr:127.0.0.1 Mask:255.0.0.0
        inet6 addr: ::1/128 Scope:Host
        UP LOOPBACK RUNNING  MTU:16436  Metric:1
        RX packets:28 errors:0 dropped:0 overruns:0 frame:0
        TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:0
        RX bytes: 1400 (1.3 KB)  TX bytes:1400 (1.3 KB)
```

and iwconfig:

```
downstairs@ubuntu:~$ iwconfig
lo       no wireless extensions.
eth0     no wireless extensions.
```

hopefully the OP has a solution. If not, anyone please help! :lolflag:

---

### Post by mriedel on 2008-07-19
Your wireless device isn't showing up in ifconfig and iwconfig.

Please post the output of
```
ifconfig -a
```

The results should include another adapter, for example eth1 or wlan0. If so, type

```
ifconfig eth1 up
```

(of course replacing eth1 with whatever additional device showed up in ifconfig -a)

---

### Post by arun170682 on 2008-07-19
Hi All,

I m new to Ubuntu. Today only I installed the ubuntu 8.0.4
After installation everything was working fine and I was able to connect to internet using LAN and wireless(both was working indivisualy).

Then system asked for software upgrade and I allowed to do so. After upgrade system restarted and I lost my connectivity.

Niehter LAN nor wireless is working for me.
Initialy there was wireless connection option present in Network manager but later it was not present in list.

I tried to reinstall Ubuntu but don't know how to do that.

I have Compaq nx6310 business laptop.

I spent whole day to get it sorted but no success.
Please help.
Thanks in advance
AMIT

---

### Post by m_ad on 2008-07-19
thanks for the speedy response, mriedel.

ifconfig -a just gives me the same output as ifconfig. it only shows me eth0 and lo.

---

### Post by m_ad on 2008-07-19
I forgot to mention that I installed the [1.2 drivers]("http://kbserver.netgear.com/release_notes/d102626.asp") (old) because the newer drivers come as a .exe setup file. The 1.2 drivers were a zip file that I could get the .inf out of.

---

### Post by m_ad on 2008-07-19
I've gotten past half the battle (maybe more :lolflag:). I've gotten the Xubuntu to recognize the device and modprobe to turn the lights on. Network Manager shows wireless connections, including mine, but won't accept my network key. In other words, I can't join the network.

And yes, the key is 100% correct, I've entered it at least 5 times.

Also, ifconfig and iwconfig show wlan0 as a device.

---

### Post by mriedel on 2008-07-20
Is it WPA or WEP? At least for WEP, there's a drop-down menu asking you wether you want to enter your key as a passphrase, in hexadecimal or whatever. Check if you've selected the correct setting. What you usually enter when Windows (XP) asks you for a wlan key is hexadecimal.

---

