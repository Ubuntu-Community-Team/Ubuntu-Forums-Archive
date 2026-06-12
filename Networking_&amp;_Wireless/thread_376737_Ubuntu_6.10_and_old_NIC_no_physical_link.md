---
title: "Ubuntu 6.10 and old NIC no physical link"
date: 2007-03-05
forum: Networking &amp; Wireless
---

### Post by dbauer3851 on 2007-03-05
I have an old pc that I use for playing with different OSes and testing stuff.  Today I threw Ubuntu 6.10 desktop on there and I've run into an issue with the NIC.  Its an old HP nic from the pavilion desktop that the pc was before it became a frankenstein kind of machine.  The nic worked perfectly fine this morning when the box was running vista but under ubuntu I don't even get a physical connection indicator on the switch or pc.  The wiring and switch port are verified good and as I said the nic worked fine under vista this morning.  DMESG, LSPCI, IFCONFIG, and /etc/network/interfaces dumps follow:

```
dave@dave-desktop:~$ sudo dmesg | grep eth0
[17179599.276000] eth0: RealTek RTL8139 at 0xe09a0000, 00:10:b5:7c:b7:12, IRQ 12
[17179599.276000] eth0:  Identified 8139 chip type 'RTL-8139B'
[17179599.592000] eth0: link down
[17179627.992000] ADDRCONF(NETDEV_UP): eth0: link is not ready

dave@dave-desktop:~$ sudo lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
00:09.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)
00:0a.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
00:0a.1 Input device controller: Creative Labs SB Audigy MIDI/Game port (rev 03)
00:0a.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port
00:11.0 ISA bridge: VIA Technologies, Inc. VT8233 PCI to ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
00:11.4 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 30)
01:00.0 VGA compatible controller: nVidia Corporation NV20 [GeForce3 Ti 200] (rev a3)

dave@dave-desktop:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:10:B5:7C:B7:12  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:12 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1284 (1.2 KiB)  TX bytes:1284 (1.2 KiB)

dave@dave-desktop:~$ sudo cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet dhcp
address 192.168.1.220
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto eth0
```

I'm pretty much at a loss here, any help would be greatly appreciated.

---

### Post by n00b@linux on 2007-03-05
Doesn't 'auto eth0' have to come immediately before 'iface eth0 inet dhcp' in your /etc/network/interfaces config file?  That may explain the 'eth0: link down' error in dmesg.  Also, what's with the dhcp+static IP info :confused:  You should have 'iface eth0 inet static' if you want to use a static IP address.
 
I'd recommend you tidy up your config file and restart the networking script (sudo /etc/init.d/networking restart) and see if that fixed things.

---

### Post by dbauer3851 on 2007-03-05
That stuff is all relics of the gui network configuration applet.  Fixed it all and restarted networking then tried restarting the entire machine both with the same results as before.  It looks to me like for some reason the kernal isn't even initializing the hardware b/c even with layer 3 configured wrong I should still see a layer 1 link on theinterface.

---

### Post by netztier on 2007-03-05
> **dbauer3851 said:**
> 
```
dave@dave-desktop:~$ sudo dmesg | grep eth0
[17179599.276000] eth0: RealTek RTL8139 at 0xe09a0000, 00:10:b5:7c:b7:12, IRQ 12
[17179599.276000] eth0:  Identified 8139 chip type 'RTL-8139B'
[17179599.592000] eth0: link down
[17179627.992000] ADDRCONF(NETDEV_UP): eth0: link is not ready
```


Well, if there's no link up, networking won't start properly - no DHCP client, no IP address, no adapter for the services to bind to, etc. 

Which module is loaded for that card? can you please append the output of **lsmod**? Check **modinfo <modulename>** to see if it will accept some parameters, maybe we can force the "link up" somehow.

Still - no link LED is a bad sign in itself. Can you still verify that cable an switch/hub port are ok, by connecting some other device to it? Another test might be: shutdown the system but leave it connected to power. Some NICs will draw some standby power and stay "link up", e.g. to listen for WakeOnLAN magic packets.

best regards

Marc

---

### Post by dbauer3851 on 2007-03-05
I just manually configured the port on the switch to 100fdx and that got everything working so it seems like the issue is ubuntu is not properly handling the layer 2 auto-negotiation.  Where in ubuntu would I set that up for the interface?  I'd rather not have a device specific config in the switch.  

DHCP wasn't the issue because once I set the switch up to dictate the 802.3 communication mode and restarted the interface on the pc I pulled an address no problem.

---

### Post by dbauer3851 on 2007-03-05
Its loading the 8139too module to control the board, FC7 used the same module without issue so I think that much is correct.

---

### Post by netztier on 2007-03-05
> **dbauer3851 said:**
> I just manually configured the port on the switch to 100fdx and that got everything working so it seems like the issue is ubuntu is not properly handling the layer 2 auto-negotiation. 

Hm. That is odd... Autonegotiation is about Duplex Modes, Autosensing is about speed issues.
Autosensing 10/100/1000Mbps is about signal levels, since all three ethernet standards use different electrical encodings. So the issue might have been that the NIC was fixed to a different speed, while the switch port was fixed to different one.

> **dbauer3851 said:**
> Where in ubuntu would I set that up for the interface?  I'd rather not have a device specific config in the switch. 

... and rightly so. 

There should be two ways to influence the module: either by figuring out the correct module parameter and adding this info in /etc/modprobe.d/options (I may be wrong on this, still verifying..),  or by adding a line to the **/etc/network/interfaces** file:

```
[FONT="Courier New"]iface eth0 inet [COLOR="Red"]dhcp[/COLOR]
 address 192.168.1.220
 netmask 255.255.255.0
 gateway 192.168.1.1
[COLOR="DarkGreen"] media <type>[/COLOR]
[/FONT]
```

If you're going for static addressing, there should be "static" instead of "dhcp"
For <media type>, there should be some parameters you can set. The man page for interfaces says that this is "driver specific".. I'm trying to figure out what should go here for the Realtek driver.

best regards

Marc

---

### Post by dbauer3851 on 2007-03-05
Thanks, I think we're going in the right direction here.  I want the interface to pull an address via dhcp, that other stuff was just in there from when I had tested a static address from within the gui to see if that would help early on in the troubleshooting.  The gui simply didn't clear out the static settings when it was changed back to dhcp.  Thanks to everyone that has helped with this, really bizarre issue...

---

### Post by netztier on 2007-03-05
> **dbauer3851 said:**
> Thanks, I think we're going in the right direction here.

Take a few steps more :-)

8139 doesn't seem to support the MII-interface, so mii-diag, mii-tool and ethtool won't work. However, there's a tool called **rtl8139-diag**, and it is found in the package **nictools-pci** which is found in the Universe repositories. I found info about this in this german Forum: [100mbit erzwingen]("http://board.gulli.com/thread/197370-100mbit-erzwingen/?threadid=197370").

In the thread in that forum, the following text is quoted, but the source of it is "404":
```

...
Adjust Speed:
-------------
(1.) Adjusting speed:
     Driver is designed with the gold that no options should be needed
     in most environment. However not all cards and networks can be
     automatically configured, thus allow operational parameters to be
     modify when they are loaded as module. Typically the following
     variables may be set:
     insmod rtl8139 options=0x40
     Hex Decimal Meaning
     0x10 16 ...Force Full-Duplex operation (must be used with 0x20 or 0x40)
     0x20 32 ...Force 100mbps-only operation
     0x40 64 ...Force 10mbps-only

  If loading as a module and configured /etc/conf.modules

  alias eth0 rtl8139
  options options=0x40
 ...
```

Hope that some of it helps to diagnose the problem!

Marc

---

### Post by xTonyx on 2007-03-05
I don't mean to muscle in but I'm having a very similar problem ([here]("http://www.ubuntuforums.org/showthread.php?t=376845")). I installed the diagnosis tool and got:

```
xtonyx@xtonyx-desktop:~$ sudo rtl8139-diag
rtl8139-diag.c:v2.11 4/22/2003 Donald Becker (becker@scyld.com)
 http://www.scyld.com/diag/index.html
Index #1: Found a RealTek RTL8139 adapter at 0xd400.
Realtek station address 00:40:f4:62:4b:5d, chip type 'rtl8139C'.
  Receiver configuration: Normal unicast and hashed multicast
     Rx FIFO threshold 2048 bytes, maximum burst 2048 bytes, 32KB ring
  Transmitter enabled with NONSTANDARD! settings, maximum burst 1024 bytes.
  Flow control: Tx disabled  Rx disabled.
  The chip configuration is 0x10 0x8d, MII half-duplex mode.
  No interrupt sources are pending.
 Use '-a' or '-aa' to show device registers,
     '-e' to show EEPROM contents, -ee for parsed contents,
  or '-m' or '-mm' to show MII management registers.
```

I'm thinking the "NONSTANDARD!" settings looks like it might be linked to the problem. as to the rest of it... I have no idea.

---

### Post by netztier on 2007-03-05
> **xTonyx said:**
> 
```

 Use '-a' or '-aa' to show device registers,
     '-e' to show EEPROM contents, -ee for parsed contents,
  or '-m' or '-mm' to show MII management registers.
```

I'm thinking the "NONSTANDARD!" settings looks like it might be linked to the problem. as to the rest of it... I have no idea.

Well then.. run and copy&paste the suggested command line options, **-e**, **-m**, **-a** and their doubles, I wonder what they'll tell us.

best regards

Marc

---

