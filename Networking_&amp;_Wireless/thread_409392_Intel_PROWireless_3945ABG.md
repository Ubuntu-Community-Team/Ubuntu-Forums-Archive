---
title: "Intel PRO/Wireless 3945ABG"
date: 2007-04-14
forum: Networking &amp; Wireless
---

### Post by Eric the Red on 2007-04-14
Hello, I recently installed Ubuntu and I'm having problems connecting via Wirless. I can't connect via cable to test the connection (because my cable won't reach in the basement), but I do know that the wireless is working right now (because I'm on my other computer in Windows XP using the wireless). The gateway of the router is 192.168.1.31 and I have DHCP enabled. Also its a linksys G wireless router. Please let me know if you need more information.

I've tried a bunch of command and searched the forums to find solutions. My problem is slightly different to others so I'm completely stuck.

When I go to the "Device manager" it does in fact detect my card corectly as the, Intel(R) PRO/Wireless 3945ABG.  I just can't seem to connect to anything. Do any of you have any ideas?

If anyone could help me out it would be well appreciated.

---

### Post by Eric the Red on 2007-04-14
I also tried "ifconfig" and "iwconfig" 

ubuntu@ubuntu:/root$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:13:02:6F:89:B6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:114178 errors:0 dropped:21390 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:74 Base address:0x8000 Memory:edf00000-edf00fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1122 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1122 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:83636 (81.6 KiB)  TX bytes:83636 (81.6 KiB)


//--------------------------------- next command -------------------------------------




ubuntu@ubuntu:/root$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"Zeus"  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:21395   Missed beacon:0

sit0      no wireless extensions.

ubuntu@ubuntu:/root$

---

### Post by dermanus on 2007-04-14
My question is about the same card, so I may as well post it here.

Ok, I too am having wireless card troubles with this make. I am a complete Linux newbie (today is my first time using it). I've ordered books to help, looked through documentation, and read forums like this. I'm pretty sure I've found the problem, but I have no idea how to fix it:

```
sudo lshw -C network
```

yields:
```

  *-network               
       description: Ethernet interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 01
       serial: 00:16:d3:43:9c:3a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r1000 ip=192.168.2.5 multicast=yes
       resources: ioport:2000-20ff iomemory:c8000000-c8000fff irq:177
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@05:00.0
       logical name: eth1
       version: 02
       serial: 00:13:02:bf:a3:4d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.1.0mp firmware=13.0 1:0 () link=no multicast=yes wireless=unassociated
       resources: iomemory:cc000000-cc000fff irq:185

```

I'm not expert, but I'm pretty sure those big DISABLED letters are the issue. I'm sure it's an easy bit of code, but my Linux skills are non-existent as of yet.

---

### Post by chili555 on 2007-04-14
> I'm pretty sure those big DISABLED letters are the issueYes. Is there a little switch on your laptop that turns wireless on and off? Mine does and it's tiny. Make sure it's on.

These are very easy to connect. The steps are:```
sudo iwlist eth1 scan
```This will tell you the ESSID of your access point and whether encryption is in place. It may take a few tries. Here is a sample:```
eth1      Scan completed :
          Cell 01 - Address: 99:13:19:62:8D:F7
                    ESSID:"myrouter1"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key: on

```As you can see, my essid is myrouter1. You will never, ever connect with Myrouter1 orMyRouter1 or myrouter. It must be exact.

Next, see it says encryption is on. It also doesn't say WPA. I know I have WEP and let's say my key is 0123456789. I then do:```
sudo iwconfig eth1 essid myrouter1
sudo iwconfig eth1 key 0123456789
sudo dhclient eth1
```And you will probably connect.

If you use WPA, several of the wireless managers do a great job of managing those details. My favorite is Wicd. [http://compwiz18.blackhole.cx/wicd/wb/](http://compwiz18.blackhole.cx/wicd/wb/)

---

### Post by dermanus on 2007-04-14
> Yes. Is there a little switch on your laptop that turns wireless on and off? Mine does and it's tiny. Make sure it's on.

It is on, or at least it's lit.

---

### Post by chili555 on 2007-04-14
> It is on, or at least it's lit.Try ```
sudo ifconfig eth1 up
iwconfig eth1
```Does it show up? If so, configure as outlined above.

---

### Post by dermanus on 2007-04-14
Just unplugged the hardline. We're in business! Thanks a bunch!

---

### Post by Eric the Red on 2007-04-14
Alright, now that Dermanus is done hikacking this thread I'd like to know if you guys have any ideas to help fix my problem? I followed ur steps with WPA encryption 'on', didn't work. So I tured off the encryption and got it working. 

I would like to get the WPA working again with this and I'm getting a lot of problems. Any ideas?

---

