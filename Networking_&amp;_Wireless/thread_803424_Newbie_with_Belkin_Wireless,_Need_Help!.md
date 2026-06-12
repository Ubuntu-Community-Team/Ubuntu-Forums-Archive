---
title: "Newbie with Belkin Wireless, Need Help!"
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by ttmw on 2008-05-22
I have a belking 54g router, and a wireless usb to get the signal on my ubuntu computer.

Im completely new to ubuntu pretty much and have never had internet set up on it. 

Where do i start, what do i click to see if i am receiving a signal etc, and what will i need to download to get it to work(if anything).

thanks in advance.

---

### Post by Peter09 on 2008-05-22
You should have an icon in the top panel which looks like to TV's. Double clicking that will give you some information. Click the configure button to set it up.

If this does not work then open a terminal
Applications->Accessories->terminal

and type

```
ifconfig
```

paste the output in the thread.

PC

---

### Post by ttmw on 2008-05-22
wired network isnt avaiable(greyed out) and manual configuration is full of things i have no idea what they mean lol.

when typing 'ifconfig' it gives me...


eth0      Link encap:Ethernet  HWaddr 00:1C:25:A5:82:E0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by Peter09 on 2008-05-22
Your USB Device has not been recognized by your machine. What type of device is it. Search the forums, there is normally a thread on installing particular devices. 

PC

---

### Post by NullHead on 2008-05-22
Plug in your device and open the terminal window again and type in ```
lsusb
``` and past the output and it might help us figure out the chipset of the device. If you know the model and brand of your USB wireles adapter then that might help us as well.

---

### Post by ttmw on 2008-05-22
ok, the output of the 'lsusb is mainly zeros and belkin 7051, is that of any help? Ive looked for inf o on this but i dont realy understand what they are taling about in the tuts. Any suggestions?

---

### Post by NullHead on 2008-05-22
OK then please tell us the make and model of the device.

---

### Post by chewearn on 2008-05-22
> **ttmw said:**
> ok, the output of the 'lsusb is mainly zeros and belkin 7051, is that of any help? Ive looked for inf o on this but i dont realy understand what they are taling about in the tuts. Any suggestions?

Copy the output for lsusb, and paste it here (enclose the text in code tags).  You don't understand the output; but maybe we do. :smile:  If you don't post the output verbatim, then we have to rely on your interpretation.

---

### Post by Forlong on 2008-05-23
You [should]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/") be able to get it to work with [Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

---

### Post by ttmw on 2008-05-23
Ok heres the output it gives...

```
Bus 001 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 050d:7051 Belkin Components 
Bus 002 Device 001: ID 0000:0000 
```

---

