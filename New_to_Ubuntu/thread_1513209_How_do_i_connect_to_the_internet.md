---
title: "How do i connect to the internet"
date: 2010-06-19
forum: New to Ubuntu
---

### Post by Ramprasath on 2010-06-19
I am an absolute beginner .
I have never used a linux os before. HAve been using windows os.es only.
I have  got a problem that i can't connect to internet automatically.
Wher do i enter my ip, dns , gateway etc.?
[SIZE="1"]
offtopic : The visual effects of window movements are cool. [/SIZE]

---

### Post by Dangger on 2010-06-19
> **Ramprasath said:**
> I am an absolute beginner .
I have never used a linux os before. HAve been using windows os.es only.
I have  got a problem that i can't connect to internet automatically.
Wher do i enter my ip, dns , gateway etc.?
[SIZE="1"]
offtopic : The visual effects of window movements are cool. [/SIZE]

If you plug the cable it should connect automatically. If you have wireless you need to select the network you want to connect to and then provide your password. It will ask you if you want to save your password and details to connect automatically, click yes if you want to.

---

### Post by CharlesA on 2010-06-19
You can use network manager or WICD to enter the IP address info, if need be. Most of the time everything will be configured automatiucally.

---

### Post by wiisg on 2010-06-19
Just installed ubuntu 9.10 this morning. Encountering this problem also. I plug in the cable but still can't connect to internet but on my network card i see LED shines. Is it because of driver something? BTW this is my first time using ubuntu have no prio knowledge about linux and everything hereee.. pls help!!!! tq

---

### Post by Nr90 on 2010-06-19
You could check if you need a proprietary driver.
Go System -> Administration -> hardware drivers.
If it shows a driver for your network card enable that and check again.

---

### Post by CharlesA on 2010-06-19
> **wiisg said:**
> Just installed ubuntu 9.10 this morning. Encountering this problem also. I plug in the cable but still can't connect to internet but on my network card i see LED shines. Is it because of driver something? BTW this is my first time using ubuntu have no prio knowledge about linux and everything hereee.. pls help!!!! tq

Running this from a terminal will tell you if the network card is working or not.

```
sudo ifconfig
```

---

### Post by wiisg on 2010-06-19
it showwsss this what is thiss?


Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by HereInOz on 2010-06-19
If that is all that it shows from ifconfig, then your network adaptor is not properly installed, or is faulty.  

You may need to get hold of a driver for it, or, perhaps easier, get a cheap LAN card with a Realtek chip on it and plug it in to one of your PCI slots.  

Ubuntu will find it and will install the drivers automatically, whereas, at the moment, you do not seem to have a local area connection at all, even though the LEDs are lit.

---

### Post by spook312 on 2010-06-19
First of all, I'm absolutely new to ubuntu.
I've installed ubuntu 10.04 amd64 on my notebook(hp pavilion tx2028au).
The main problem is I can't connect to internet.
I think, that may be because of the lack of driver.
There're lots of problems about drivers, like graphic, fingerprint.
But these could be solve easily if I get online, right?
So, the main problem is wireless driver.
Please help me, where can I find and how can I install?
If you could, please help me in detail! Thankz you.

---

### Post by jeffymarts on 2010-06-19
Generally speaking you would go to the manufacturers website and look there for drivers for your device. Make sure that the drivers are written for Linux or the distro that you're using.

---

### Post by gandaran on 2010-06-19
> **spook312 said:**
> First of all, I'm absolutely new to ubuntu.
I've installed ubuntu 10.04 amd64 on my notebook(hp pavilion tx2028au).
The main problem is I can't connect to internet.
I think, that may be because of the lack of driver.
There're lots of problems about drivers, like graphic, fingerprint.
But these could be solve easily if I get online, right?
So, the main problem is wireless driver.
Please help me, where can I find and how can I install?
If you could, please help me in detail! Thankz you.
it would be easier to help if you post the brand of wireless card.
if you have the possibility of connecting the notebook to ethernet cable internet and update software sources (run *sudo apt-get update* in terminal) then you can have a look in system » administration » hardware drivers if theres a driver you can install for the wireless card

---

### Post by Favux on 2010-06-19
Hi spook312,

With a hp pavilion tx2028au tablet pc your wireless card should be a:
```
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
```
You want to install the Broadcom STA wireless driver in System > Administration > Hardware Drivers.  If not available you'll have to hook up with an ethernet cable and update and then grab it.

---

### Post by michael__p on 2010-06-19
Hi,
I think, I basically have the same problem as WIISG, my ifconfig output is:
 
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0 
inet6 addr: ::1/128 Scope:Host 
UP LOOPBACK RUNNING MTU:16436 Metric:1 
RX packets:12 errors:0 dropped:0 overruns:0 frame:0 
TX packets:12 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:0 
RX bytes:720 (720.0 B) TX bytes:720 (720.0 B)
 
The difference is that my internet was working and then just stopped at some point. Do you have any explanations for that (I mean the driver should have been installed at some point)? It also seems that both ethernet and WLAN connections are not working anymore. I don´t find drivers in the System>Administration>Hardware Drivers, so I had a look at the Lenovo homepage (I have a Lenovo L510) but I don´t find drivers for Linux... Any suggestions?
Thanks, Michael

---

