---
title: "[SOLVED] No wired connection"
date: 2008-02-14
forum: Networking &amp; Wireless
---

### Post by songhk on 2008-02-14
Hi  I installed Ubuntu 7.04 at my computer(Window vista)
at Window vista I can use Internet. I use road runner.
But at ubuntu  Network Settings, I can't see the wired connection.
Please help me. thannks....


 some information from my pc
------------------------------------------------------------------
click -> Network Settings

Connection:
 wireless connection (wmaster0)
 wireless connection (wlan0)
 modem connection.

ifconfig:

l0  Link encap:Local Loopback
     inet addr: 127.0.0.1 Mask: 255.0.0.0
     inet6 addr: ::1/128 Scope:Host
     UP LOOPBACK RUNNING MTU:16436 Metric:1
     RX packets:0 errors:0 dropped:0 overruns:0 frame:0
     TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
     collisions:0 txqueuelen:0
     RX bytes:0 (0.0b)  TX bytes:0 (0.0 b)

wlan0  Link encap:Ethernet HWaddr 00:C0:A8:FF:76:54
     inet6 addr: fe80::2c0:a8ff:feff:7654/64 Scope:Link
     UP LOOPBACK RUNNING MULTICAST MTU:1500 Metric:1
     RX packets:0 errors:0 dropped:0 overruns:0 frame:0
     TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
     collisions:0 txqueuelen:0
     RX bytes:0 (0.0b)  TX bytes:576 (576.0 b)

wmaster0  Link encapUNSPEC HWaddr 00:C0-A8-FF-76-54-00-00--00-00-00-00-00-00-00-00
     UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
     RX packets:0 errors:0 dropped:0 overruns:0 frame:0
     TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
     collisions:0 txqueuelen:1000
     RX bytes:0 (0.0b)  TX bytes:576 (0.0 b)


~$ route
Kernet IP routing table
Destination Gateway Genmask Flags Metric Ref  Use Ifac

---

### Post by lawentzel on 2008-02-15
Is your cable modem connected via USB or network port?  If USB, try hooking it up to the network card.  (Don't have both hooked up at the same time.)  Then see where you are at.

---

### Post by songhk on 2008-02-15
Thanks for reply
My cable modem is connected by wire to the network port - ETHERNET (not USB).
and still I can't use Internet. please help me.

-----------------------------------------------------------------------------------------------------------------
and My device information

Network device: Loopback Interface(lo)
IP information
   Protocol: IPv4, IP Address: 127.0.0.1, Netmask/Prefix: 255.0.0.0, 
   Brodcast: none, scope: none
   Protocol: IPv6, IP Address: ::1, Netmask/Prefix: 128 
   Brodcast: none, scope: Host

Network device: Unknown Interface(wmaster0)
   IP Information: none

Network device: Wireless Interface(wlan0)
IP information
   Protocol: IPv6, IP Address: fe80::2c0:a8ff:feff:7654,  Netmask/Prefix: 64
   Brodcast: none, scope: Link

---

### Post by songhk on 2008-02-16
Thanks lawentzel for reply.

Eventually I got it.

1. Ubuntu couldn't recognize Intel(R) 82566 DC-2Gigabit Network Connection
    
2. [http://downloadcenter.intel.com/Detail_Desc.aspx?s%20trState=LIVE&ProductID=983&DwnldID=9180&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?s%20trState=LIVE&ProductID=983&DwnldID=9180&lang=eng)
from this site, I downloaded the driver(e1000) for my Intel ethernet controller and installed as the manual(README). 

  a. Move the base driver tar file to the directory of your choice.  For
     example, use /home/username/e1000 or /usr/local/src/e1000.
  
  b. Untar/unzip archive:
       tar zxf e1000-x.x.x.tar.gz

  c. Change to the driver src directory:
       cd e1000-x.x.x/src/

  d. Compile the driver module:
  (make sure you should log in as root, otherwise manythings can't be installed or removed.)
        make install

   The binary will be installed as:
     /lib/modules/<KERNEL VERSION>/kernel/drivers/net/e1000/e1000.[k]o

   The install locations listed above are the default locations.  They
   might not be correct for certain Linux distributions. 

  e. Load the module using either the insmod or modprobe command:
  (log in as root, otherwise you can see 'Fatal Error inseting e1000, operation not permitted')
     modprobe e1000
     insmod e1000

3. and then I saw wired network connection signal

------------------------------------------------------------------------------------------------------------------
I got hint from below site.
[http://ubuntuforums.org/archive/index.php/t-533825.html](http://ubuntuforums.org/archive/index.php/t-533825.html)

---

