---
title: "wifi networks are not detecting my lenovo b490"
date: 2015-05-02
forum: Networking &amp; Wireless
---

### Post by navajyothms1989 on 2015-05-02
hi,
    my wifi is not detecting after i tried 
**_sudo apt-get install linux-image-generic-lts-trusty_** for docker installtion.My driver details are given and i already enbled the broadcom proprietary driver from software center additional driver, then also no use

02:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Lenovo Device [17aa:0611]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 19
    Region 0: Memory at f0500000 (64-bit, non-prefetchable) [size=32K]
    Capabilities: <access denied>
    Kernel driver in use: wl

then i tried ifconfig wlan0 up
 i got "SIOCSIFFLAGS: Operation not permitted" this message.
  
  please help

---

### Post by chili555 on 2015-05-02
> Kernel driver in use: wlLet's make sure it is actually loaded:```
lsmod | grep wl
```If not, load it:```
sudo modprobe wl
```Any errors or warnings?

Is the switch set to turn the wireless radio on or off?```
rfkill list all
```If there is any block, move the switch.

Are there any helpful clues in the log?```
dmesg | grep wl
```Thanks.

---

### Post by navajyothms1989 on 2015-05-02
here is my screenshot  i tried those too.

---

### Post by chili555 on 2015-05-02
Everything looks perfect so far. Do you see networks when you click the Network manager icon? [http://www.eui.eu/Images-2011/ServicesAdmin/ComputingService/eduroam/eduroamUbuntu%281%29.png](http://www.eui.eu/Images-2011/ServicesAdmin/ComputingService/eduroam/eduroamUbuntu%281%29.png)

When you click on yours and try to connect, what happens?

---

### Post by navajyothms1989 on 2015-05-02
here is the screenshot when disconnect ethernet.it shows no networks and shows wifi is enabled

---

### Post by chili555 on 2015-05-02
Let's dig deeper:```
iwconfig
```If you see no wlan0, then do:```
sudo modprobe wl
dmesg | grep wlan
sudo iwlist wlan0 scan
```Thanks.

---

### Post by navajyothms1989 on 2015-05-02
here is the results.

---

### Post by chili555 on 2015-05-02
> my wifi is not detecting after i tried
sudo apt-get install linux-image-generic-lts-trusty for docker installtion.What does this mean; 'docker installation'?

May we see:```
lsb_release -a
uname -r
```Thanks.

---

### Post by navajyothms1989 on 2015-05-02
latest results.
docker details:[https://www.docker.com/](https://www.docker.com/)

---

### Post by chili555 on 2015-05-02
I don't see anything wrong to try to fix so far. The correct driver seems to be installed, Network Manager seems to be present and working. The switch is set to enable wireless. 

Let's dig even deeper:```
sudo iwlist wlan0 freq

```Can you tell from other devices what channel the router is on? Hopefully a channel the Broadcom wireless receives!!```
sudo iw reg get

```

---

### Post by navajyothms1989 on 2015-05-03
here is the results.

---

### Post by navajyothms1989 on 2015-05-04
latest results

---

