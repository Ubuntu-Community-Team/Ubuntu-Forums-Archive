---
title: "Wifi Adapter (Realtek d723) Not Recognized"
date: 2019-05-17
forum: Networking &amp; Wireless
---

### Post by persler06 on 2019-05-17
I get a "Wifi network device not ready" error. Please help me. 

I share the network outputs below.

[http://paste.ubuntu.com/p/psR7g56Csd/](http://paste.ubuntu.com/p/psR7g56Csd/)

```
sudo ifconfig wlo1 up
```


```
sudo iwlist wlo1 scan
wlo1      Interface doesn't support scanning : Network is down

```

---

### Post by jeremy31 on 2019-05-17
```
cd /lib/firmware/rtlwifi
sudo wget https://github.com/lwfinger/rtlwifi_new/raw/extended/firmware/rtlwifi/rtl8723defw.bin
```
Reboot

---

### Post by bilkay on 2019-05-18
Having the same problem. Installed the firmware as instructed and it still doesn't work.
```
sudo ifconfig wlo1 up
wlo1: ERROR while getting interface flags: No such device
```

---

### Post by persler06 on 2019-05-20
worked, thank you.

---

### Post by bilkay on 2019-05-20
Still no luck!

[http://paste.ubuntu.com/p/QJhPGbqdh6/](http://paste.ubuntu.com/p/QJhPGbqdh6/)

---

### Post by luks911 on 2019-05-20
> **bilkay said:**
> Still no luck!

[http://paste.ubuntu.com/p/QJhPGbqdh6/](http://paste.ubuntu.com/p/QJhPGbqdh6/)

Hi, 

What's the output of

```
ifconfig -a  
``` ?

---

### Post by bilkay on 2019-05-20
```
$ ifconfig -a
enp2s0    Link encap:Ethernet  HWaddr c4:65:16:92:40:53  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::360b:1eec:c348:56d7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:933159 errors:0 dropped:0 overruns:0 frame:0
          TX packets:222817 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1234418973 (1.2 GB)  TX bytes:38409942 (38.4 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:26367 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26367 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2778819 (2.7 MB)  TX bytes:2778819 (2.7 MB)

```

---

### Post by bilkay on 2019-05-20
I'm drowning in Ubuntu!

---

### Post by luks911 on 2019-05-20
Hum... I thought that maybe the wireless interface had other name than wlo1, but it's not the case.

What's the output of 

```
lsmod
``` ?

You should see rtl8723de in at least one of the lines.

---

### Post by jeremy31 on 2019-05-20
Have you done ```
sudo apt-get install dkms git build-essential
git clone -b extended https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
sudo cp -r rtlwifi_new/firmware/rtlwifi/ /lib/firmware/rtlwifi/
echo "options rtl8723de ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723de.conf
```
Then reboot

---

### Post by bilkay on 2019-05-20
These are the only listings with "rtl" in them:

```
btrtl                  16384  1 btusb
bluetooth             557056  12 btrtl,btintel,btbcm,bnep,btusb
```

---

### Post by luks911 on 2019-05-20
> **bilkay said:**
> These are the only listings with "rtl" in them:

```
btrtl                  16384  1 btusb
bluetooth             557056  12 btrtl,btintel,btbcm,bnep,btusb
```

So you are not loading the wifi module you need.

Try what jeremy31 sugest in his last post.

---

### Post by bilkay on 2019-05-20
> **jeremy31 said:**
> Have you done ```
sudo apt-get install dkms git build-essential
git clone -b extended https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
sudo cp -r rtlwifi_new/firmware/rtlwifi/ /lib/firmware/rtlwifi/
echo "options rtl8723de ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723de.conf
```
Then reboot

Did that and now it shows wi-fi available. Here's ifconfig:

```
$ ifconfig
enp2s0    Link encap:Ethernet  HWaddr c4:65:16:92:40:53  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:267 errors:0 dropped:0 overruns:0 frame:0
          TX packets:143 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33036 (33.0 KB)  TX bytes:15819 (15.8 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:328 errors:0 dropped:0 overruns:0 frame:0
          TX packets:328 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23170 (23.1 KB)  TX bytes:23170 (23.1 KB)

wlo1      Link encap:Ethernet  HWaddr 48:5f:99:d3:a5:7d  
          inet addr:10.42.0.1  Bcast:10.42.0.255  Mask:255.255.255.0
          inet6 addr: fe80::4a5f:99ff:fed3:a57d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:110 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:14844 (14.8 KB)
```

It looks like it's connected to itself. I don't see any other available sources.

UPDATE: It took a while but now it's showing available networks! Thanks a TON! You can have some of my excess Ubuntu.

---

### Post by bilkay on 2019-05-20
Initially, it only showed the wi-fi network "Laptop". I had to edit the connection and uncheck "Automatically connect," and then disconnect it. After that, the available networks showed up.

I have one additional question: Is this fix going to survive a kernel change?

---

### Post by luks911 on 2019-05-20
I think it is because it's using DKMS [0]

[0] [https://en.wikipedia.org/wiki/Dynamic_Kernel_Module_Support](https://en.wikipedia.org/wiki/Dynamic_Kernel_Module_Support)

---

### Post by bilkay on 2019-07-06
Just thought I'd pass on a further experience. I had to do a reinstallation (for an unrelated reason). The first time I installed 16.04, I didn't have any internet connection. I followed the instructions here and it worked fine. This time, I did the installation with an ethernet connect and checked the box for doing an update. When I went through the steps here, the step "sudo dkms install rtlwifi-new/0.6" failed because of an outdated compiler. I had to do an upgrade in order to get past that step.

---

