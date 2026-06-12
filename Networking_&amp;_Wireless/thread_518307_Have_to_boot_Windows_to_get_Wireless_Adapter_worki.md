---
title: "Have to boot Windows to get Wireless Adapter working"
date: 2007-08-05
forum: Networking &amp; Wireless
---

### Post by derek.gtalk on 2007-08-05
Hi,

I got a Buffalo wireless adapter for my desktop. If I boot my computer into Ubuntu directly, I can't see wireless section in the Network Manager GUI. If I restart the computer into Windows, after the wireless connection is established, restart it into Ubuntu. the wireless connection will be established automatically, and there is a wireless section in the network manager. Any idea? I really hate the idea to boot windows first then reboot to linux to get wireless working.

Thanks,
Derek

---

### Post by noob12 on 2007-08-06
Can you tell us what card and driver precisely?  Is this a usb device?  Can you provide  **lshw -C network** and **iwconfig** output captured both when you have wireless working and when you don't.

Ideally we would also get a **dmesg** captured on an initial boot and one on your reboot just after using Windows.

---

### Post by derek.gtalk on 2007-08-06
Yes, it's a usb device from Buffalo AirStation. I got the following output by running those two commands. If it's not enough, i will try to find out more info. thanks.

derek@ubuntu:~$ sudo lshw -C network
Password:
  *-network               
       description: Ethernet interface
       product: 82801G (ICH7 Family) LAN Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@03:08.0
       logical name: eth0
       version: 01
       serial: 00:13:72:e5:11:88
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: iomemory:efbff000-efbfffff ioport:ccc0-ccff irq:21
  *-network
       description: Wireless interface
       physical id: 1
       bus info: firewire@1
       logical name: rausb1
       serial: 00:0d:0b:35:b7:75
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RT2500USBSTA driverversion=1.0.0 - BETA2 ip=192.168.0.2 link=yes multicast=yes wireless=RT2500USB WLAN


derek@ubuntu:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

rausb1    RT2500USB WLAN  ESSID:"183 Angelica"  Nickname:""
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:18:4D:10:FB:38   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=86/100  Signal level:-55 dBm  Noise level:-198 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by noob12 on 2007-08-08
Sorry.  I lost this thread and didn't respond.  Did you solve the problem?  If not, what we really need to see is some comparative information when wireless doesn't work and when it does work after your Windows reboot.  

Do this both on a cold boot when you didn't have wireless and after your Windows boot when you do.  If you don't have networking initially, save the output in files and post after you do.
```

lsusb

lshw -C network

ifconfig -a

dmesg

```

---

### Post by derek.gtalk on 2007-08-09
no, the problem is still there. I attached the output.

---

### Post by derek.gtalk on 2007-08-09
can't see if the attachments were attached successfully. let me try again.

---

### Post by noob12 on 2007-08-10
It looks like you have the Buffalo WLI-U2-KG54-AI.  Please confirm.  If so, this thing has the property that it looks like a drive as well as a wireless; this is for the Windows auto-install feature.  It appears what is happening is that on warm boots it's already in a mode where it is behaving like the wireless, while on cold it is looking like a drive.

There's a small switch on the device which you have to manipulate.  Here's a quote from their user manual.  You'll have to locate the switch and interpret the details.
> 
To disable the Auto Install feature, use a paperclip of other pointed object to move the small
switch to the far left. If the small switch is on the right side over the black circle, Auto
Install is enabled (default setting).


(To the far far left is the "dessert topping" mode.  :-) )

Try switching the auto-install feature off following those instructions.  See if this helps.

Note that you may also find you want to install more recent drivers from serialmonkey.  Let's take it a step at a time though.

---

### Post by derek.gtalk on 2007-08-10
probably you are right. when I cold boot the computer into ubuntu, a 'file explorer' keeps popping up, like the system is infected by a virus. I will give it a go tonight.

---

### Post by derek.gtalk on 2007-08-10
well the switch is too damn small, and I think I broke it. I also have a usb wireless adapter which does not have the auto-install feature, and it works straightaway when I plug it in.

Thanks for your help,
Derek

---

