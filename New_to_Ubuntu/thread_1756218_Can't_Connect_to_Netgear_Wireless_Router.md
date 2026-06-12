---
title: "Can't Connect to Netgear Wireless Router"
date: 2011-05-12
forum: New to Ubuntu
---

### Post by nastypants on 2011-05-12
Hey, 

I'm still pretty new to Linux, and pretty stupid about computers.  So, I run Ubuntu 10.10 on my Dell Gx270.  Up until I got this new Netgear (WNR2000v3) router it's connected to the internet pretty ok through a modem.  But so I got this new Netgear router, and it connects fine with the computer I run XP on, but even when I try to hook my computer that I run Ubuntu on to it directly with an ethernet cable, it doesn't seem to recognize any connection.  I threw all the numbers available into the network manager thing (you know, name, password, IP address, netmask IP or whatever... all the secret numbers.  all of them) and on the issue of connecting my computer still says, "Nope!"

It can't seem to find the device for my wireless connection when I try the whole "ifconfig" command thing.

Am I doing something wrong?  Is there something else I could do to make this work?  Please help a stupid recent Windows convert.

---

### Post by garvinrick4 on 2011-05-12
You should not really have had to do anything. And you say you cannot connect wired
or wireless. Try stopping and restarting the network manager. Should find if you set the
router up right, which is more or less plug and play. Can put your default route # into URL and
will bring router settings up. Did you right click on network applet and enable wired and wireless?
Here is to turn on and off network manager to try and reset. Open a terminal and copy and paste one at a time.```

sudo service network-manager stop
``````
sudo rm /var/lib/NetworkManager/NetworkManager.state
``````
sudo service network-manager start
```

---

### Post by nastypants on 2011-05-12
Thank you for your quick reply and your help!

Restarting the network manager didn't seem to do anything.

I do not know how to find default route number.  Could you help me with that?

---

### Post by taseedorf on 2011-05-12
default route is usually 192.168.1.0 or 192.168.0.1 .   that will let you log into the router through a wired connection.  Make sure all settings are set to default in network manager and make sure you're using DHCP and not manual settings.

---

### Post by grahammechanical on 2011-05-12
My router/modem came with a User Guide. Sure, it gave instructions for MS Windows but there was enough information to identify what Ubuntu needed to get a secure wireless connection to the router. Here is a quote:

> If you couldn't connect during step 4, go to your web browser's address bar, type **[http://192.168.1.254](http://192.168.1.254)** and click **Go** or press **Enter** on your keyboard. You'll be asked to enter a **Username** & **Password**. The **Username** is **admin** and the **Password** is the **Serial Number** (found on the bottom of your Thomson Gateway). Check the **Setup Sticker** for confirmation of these. Once you have entered the **Username** and **Password** you'll be taken to the Thomson Gateway Configuration page.

If you did not get information like this when you purchased the router, then you did not get good customer service. Accessing the router configuration page with a web browser will let you confirm if you have set Network Manager to the same encryption method as the router is set to. You will also need what is variously called the wireless key, the network security key, the WPA-PSK key or the pass phrase to allow network manager to connect securely to the router.

Regards.

---

### Post by jtarin on 2011-05-12
Let's look at a couple of parameters and see what's going on.
I'm gong to ask you to enter some commands in a terminal and post the output here.

First one:```
lspci
```Second one:```
lsmod
```Third one:```
ifconfig
```copy the readouts from the terminal and post here.....use the # on the message board to wrap your results in code tags.

---

### Post by nastypants on 2011-05-12
Thank you again for all your help.  I really do appreciate it.

For lspci I got: 
```
  00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
   
  00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
   
  00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
   
  00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
   
  00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
   
  00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
   
  00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
   
  00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
   
  00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
   
  00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
   
  00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
   
  00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
   
  00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
   
  00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
   
  01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
   
  02:08.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
  
```For lsmod, the second one, I got: 
```
  Module                  Size  Used by
   
  nls_iso8859_1           3261  1 
   
  nls_cp437               4931  1 
   
  vfat                    9201  1 
   
  fat                    48240  1 vfat
   
  usb_storage            40204  1 
   
  binfmt_misc             6599  1 
   
  snd_intel8x0           25664  3 
   
  snd_ac97_codec         99227  1 snd_intel8x0
   
  ac97_bus                1014  1 snd_ac97_codec
   
  nouveau               517434  2 
   
  snd_pcm                71475  3 snd_intel8x0,snd_ac97_codec
   
  snd_seq_midi            4588  0 
   
  snd_rawmidi            17783  1 snd_seq_midi
   
  ttm                    56633  1 nouveau
   
  snd_seq_midi_event      6047  1 snd_seq_midi
   
  snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
   
  drm_kms_helper         30200  1 nouveau
   
  snd_timer              19067  2 snd_pcm,snd_seq
   
  snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
   
  drm                   168060  4 nouveau,ttm,drm_kms_helper
   
  ppdev                   5556  0 
   
  parport_pc             26058  1 
   
  dcdbas                  5402  0 
   
  snd                    49038  12 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
   
  intel_agp              26566  1 
   
  joydev                  8767  0 
   
  psmouse                59033  0 
   
  i2c_algo_bit            5168  1 nouveau
   
  soundcore                880  1 snd
   
  serio_raw               4022  0 
   
  snd_page_alloc          7120  2 snd_intel8x0,snd_pcm
   
  shpchp                 29886  0 
   
  agpgart                32011  3 ttm,drm,intel_agp
   
  lp                      7342  0 
   
  parport                31492  3 ppdev,parport_pc,lp
   
  usbhid                 36882  0 
   
  3c59x                  32011  0 
   
  hid                    67742  1 usbhid
   
  floppy                 54311  0 
   
  [FONT=Arial]mii                     4425  1 3c59x[/FONT]
```And for ifconfig, I got: 
```
  eth0      Link encap:Ethernet  HWaddr 00:01:03:2d:92:b5  
   
            UP BROADCAST MULTICAST  MTU:1500  Metric:1
   
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
   
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
   
            collisions:0 txqueuelen:1000 
   
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
   
            Interrupt:17 Base address:0x6f80 
   
   
   
  lo        Link encap:Local Loopback  
   
            inet addr:127.0.0.1  Mask:255.0.0.0
   
            inet6 addr: ::1/128 Scope:Host
   
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
   
            RX packets:192 errors:0 dropped:0 overruns:0 frame:0
   
            TX packets:192 errors:0 dropped:0 overruns:0 carrier:0
   
            collisions:0 txqueuelen:0 
   
            RX bytes:15096 (15.0 KB)  TX bytes:15096 (15.0 KB)
   
  
```

---

### Post by jtarin on 2011-05-12
My bad. Do the lspci one again only this time add -k. ```
lspci -k
```

---

### Post by nastypants on 2011-05-12
Ok, for that new one I got: 

```
  00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
        Subsystem: Dell Device 0151
        Kernel driver in use: agpgart-intel
        Kernel modules: intel-agp
  00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
        Kernel modules: shpchp
  00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
  00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
        Subsystem: Dell Device 0151
        Kernel driver in use: uhci_hcd
  00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
        Subsystem: Dell Device 0151
        Kernel driver in use: uhci_hcd
  00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
        Subsystem: Dell Device 0151
        Kernel driver in use: uhci_hcd
  00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
        Subsystem: Dell Device 0151
        Kernel driver in use: uhci_hcd
  00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
        Subsystem: Dell Device 0151
        Kernel driver in use: ehci_hcd
  00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
        Kernel modules: shpchp
  00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
        Kernel modules: iTCO_wdt, intel-rng
  00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
        Subsystem: Dell Device 0151
        Kernel driver in use: ata_piix
  00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
        Subsystem: Dell Device 0151
        Kernel driver in use: ata_piix
  00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
        Subsystem: Dell Device 0151
        Kernel modules: i2c-i801
  00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
        Subsystem: Dell Device 0151
        Kernel driver in use: Intel ICH
        Kernel modules: snd-intel8x0
  01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
        Subsystem: Giga-byte Technology Device 3414
        Kernel driver in use: nouveau
        Kernel modules: nouveau, nvidiafb
  02:08.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
        Subsystem: 3Com Corporation 3C905CX-TX/TX-M Fast Etherlink for PC Management NIC
        Kernel driver in use: 3c59x
        Kernel modules: 3c59x

  
```

---

### Post by jtarin on 2011-05-12
OK then this shows all is good up to and including your ethernet card. So problem is router.
Did you follow the instructions:"default route is usually 192.168.1.0 or 192.168.0.1 . that will let you log into the router through a wired connection". Try those IP numbers in a browser for router access.

---

### Post by dFlyer on 2011-05-12
using your web brower enter [http://192.168.1.1](http://192.168.1.1)

Enter your user name.

Enter you user password.

You now have access to your router.

---

### Post by nastypants on 2011-05-12
Nothing showed up.  Firefox just reminded me it's in offline mode when I tried both the numbers.

---

### Post by jtarin on 2011-05-12
> **dFlyer said:**
> using your web brower enter [http://192.168.1.1](http://192.168.1.1)

Enter your user name.

Enter you user password.

You now have access to your router.That was suggested in a previous post and awaiting response. It's beneficial to read the post completetly before answering....I have found by experience.

---

### Post by jtarin on 2011-05-12
> **nastypants said:**
> Nothing showed up.  Firefox just reminded me it's in offline mode when I tried both the numbers.Try the terminal and ping those numbers.

---

### Post by nastypants on 2011-05-12
Oh, looks like I spoke too soon.  I didn't even see that post, I'm sorry. Thank you for pointing it out, jtarin.

 I unchecked "Work Offline" as Firefox was kind enough to suggest, and typed in "http://192.168.1.1" but it still did nothing.

I mean, it works on the computer that has connectivity with the router (the one running Windows), but not the one running Ubuntu.  Is there something I can change on the Netgear page while I'm on this computer that would help the computer without connectivity play nice with the wireless internet?

---

### Post by nastypants on 2011-05-12
...And again I spoke too soon.  Thank you again for your patience.  Trying to ping those numbers just gets me a message that says the network is unreachable.

---

### Post by astex on 2011-05-12
In Router Settings  (192.168.0.1 or something like that):

1.  Make sure the DHCP server is.

2.  Make sure the IP pool offers more than one address (the starting IP address is not equal to the ending IP address).  You can check if this is the case by trying to access the network with a third device.

---

### Post by dFlyer on 2011-05-12
> **jtarin said:**
> That was suggested in a previous post and awaiting response. It's beneficial to read the post completetly before answering....I have found by experience.

Not really, they suggested to try 192.168.1.0 or 192.168.0.1 and I said to try 192.168.1.1 as the other two never worked for me on NetGEAR.

---

### Post by dFlyer on 2011-05-12
> **nastypants said:**
> Oh, looks like I spoke too soon.  I didn't even see that post, I'm sorry. Thank you for pointing it out, jtarin.

 I unchecked "Work Offline" as Firefox was kind enough to suggest, and typed in "http://192.168.1.1" but it still did nothing.

I mean, it works on the computer that has connectivity with the router (the one running Windows), but not the one running Ubuntu.  Is there something I can change on the Netgear page while I'm on this computer that would help the computer without connectivity play nice with the wireless internet?

are you plugged into your router or are you trying to run wifi?

---

### Post by jtarin on 2011-05-12
> **dFlyer said:**
> Not really, they suggested to try 192.168.1.0 or 192.168.0.1 and I said to try 192.168.1.1 as the other two never worked for me on NetGEAR.Well...now I look stupid for overlooking the obvious. A regular neon sign.:P

---

### Post by jtarin on 2011-05-12
Trying swapping connection ports with the working computer.

---

### Post by nastypants on 2011-05-12
I'm trying to run wifi, and I am beginning to feel very, very stupid for not being able to make it go.

---

### Post by dFlyer on 2011-05-12
Under ubuntu can you connect to the network while your plugged into your router? When you tried to enter [http://192.168.1.1](http://192.168.1.1) were you hard wired to your router? I have the exact same router you have and it works great with ubuntu. Do you have a Desktop CD handy? if so make sure your hardwired your router to the computer and book off the Desktop live CD. See if you can connect to the network off the live cd while hardwired to the router. See if wifi show up when you book from hardwire live CD. If everything works check to see what drivers are load for you network.

---

### Post by dFlyer on 2011-05-12
Here are my settings for this Router

Basic Settings:
Does internet connection require a login - NO
Account Name: WNR2000
Domain Name: 
Internet IP Address: Get Dynamically from ISP
Domain Name Server DNS Address: Get automatic from server
Router MAC address: Use default address.

Wifi Settings:
Wireless setting: NetGEAR
Region: US
Channel: Auto
Mode: Up to 145 mbps
Security Options: wpa-psk (tkip) + wpa2 - psk (aes)
Pass Phrase: (What every you created)

---

### Post by jtarin on 2011-05-12
Good point. I have been under the assumption this entire time you were hardwired. You must be harwired the first time you try to connect for the proper drivers to be installed.

---

### Post by nastypants on 2011-05-13
Ok, so I hard wired it to the router, whereas it was not hard wired previously.  It says it's connected now, but still can't actually connect to anything (including [http://192.168.0.1](http://192.168.0.1) or any variation of the last two numbers).

dFlyer, I copied your settings for my router, it still seems to not help.  The cd that came with the router doesn't seem to do a whole lot when I run it.  But maybe that's just because I don't see a "MAKE IT GO" button, and I'm both tired and stupid about computers.

What am I doing wrong?

---

### Post by nastypants on 2011-05-13
Ok, so this time I swapped the actual set up with the computer that was working and everything is going fine.  How do I make the wifi go from this point?

---

### Post by nastypants on 2011-05-15
I still feel a little lost as to how to transition from having the Ubuntu-running computer usurp the internet set-up from the Windows-running computer to having the Ubuntu-running computer fly freely over the internet on the wings of wireless internet.

---

### Post by nastypants on 2011-05-25
Well, thanks for the help anyway.

---

