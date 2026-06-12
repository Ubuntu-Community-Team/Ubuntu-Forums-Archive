---
title: "network card help"
date: 2010-06-19
forum: New to Ubuntu
---

### Post by superninjapanda on 2010-06-19
i am trying to install the driver for my network card. It is a newgate WG311 v3. i followed [this guide]("http://ja.meswilson.com/blog/2007/03/11/wg311v3-64-bit-driver/") exactally. everything works, until i try to scan for networks, when it tells me that the wlan0 interface doesn't support scanning. does anybody know what my problem is?

---

### Post by doas777 on 2010-06-19
have you rebooted or restarted networking after running the modprobe line? it isn;t usually needed, (modprobe is used to try to avoid rebooting) but can be a little iffy. did you confirm that the driver is loaded via dmesg?

do any messages show up when you try to restart networking like so?
```

sudo /etc/init.d/networking restart

```

what is the output of 
```
lshw -C network
```

---

### Post by superninjapanda on 2010-06-19
> **doas777 said:**
> have you rebooted or restarted networking after running the modprobe line? it isn;t usually needed, (modprobe is used to try to avoid rebooting) but can be a little iffy. did you confirm that the driver is loaded via dmesg?

do any messages show up when you try to restart networking like so?
```

sudo /etc/init.d/networking restart

```what is the output of 
```
lshw -C network
```


the dmesg return said that it was working. At first, i was having a lot of trouble running the modprobe prompt, until i restarted. I just rebooted, and it still says that scanning is not supported. i don't know how to do the little code boxes, im a noob, but i can copy and paste what those prompts gave me (I've removed the first part of each prompt line, as its my name):
-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
-desktop:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 48:5b:39:5f:05:f8
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.5 latency=0 multicast=yes
       resources: irq:28 ioport:d800(size=256) memory:fbeff000-fbefffff memory:cfff0000-cfffffff(prefetchable) memory:fbec0000-fbedffff(prefetchable)
  *-network UNCLAIMED
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=64
       resources: memory:fbcf0000-fbcfffff memory:fbce0000-fbceffff

thanks

i also tried the command "iwconfig" because another guide said to check if the driver worked. It returns -desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

 I also tried disconecting the ethernet cable and running these prompts, and they still did not work.

---

### Post by doas777 on 2010-06-19
what do you get from 
```

sudo ndiswrapper -l
cat /etc/network/interfaces

```

does the card appear in network-manager or show in 'ifconfig'?

I've seen some references to the error you're getting, but I'm seeing a followup message like "Network is down" or "Hardware not present". does anything additional show in dmesg after trying to scan?

---

### Post by superninjapanda on 2010-06-19
~$ sudo ndiswrapper -l
wg311v3 : driver installed
    device (11AB:1FAA) present

-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 48:5b:39:5f:05:f8  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::4a5b:39ff:fe5f:5f8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2379 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2245 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2159152 (2.1 MB)  TX bytes:384265 (384.2 KB)
          Interrupt:29 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

---

### Post by doas777 on 2010-06-19
I've only ever seen modprobe used at install, but some of the ndiswrapper folks do make wider use of it. I haven't used ndiswrapper in some years, but it would surprise me if you had to run it more than once. 

add a line to /etc/network/interfaces like this:
```

auto wlan0

```and restart networking. do you get any messages? does it start to show up in network manager?

also if you install wifi-radar, does it pick up the card?

---

### Post by superninjapanda on 2010-06-19
it says it does not recognize the "auto" command. And wifi radar does not recognize any card. Where would it be in the network manager? I can't find it, but i don't know where to look.

---

