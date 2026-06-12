---
title: "Realtek RTL-8169 only running at 10 Mb/s?"
date: 2007-09-18
forum: Networking &amp; Wireless
---

### Post by onebelo on 2007-09-18
I have an onboard realtek Rtl-8169 that i'm using on my ubuntu machine.  I just realized today that its connecting at only 10 Mb/s.  I've been running ubuntu for a couple months now and didnt notice before, speed of transferring files over the network seem normal but just recently i noticed its been going slow and today I finally bothered to check the speed of the connection.

Any ideas why it is only running at 10 Mb/s instead of Gigabit or even 100 Mb/s? I been searching through google and here but to no avail.  Even tried installing R1000 drivers but cant seem to get that installed correctly.  Are there any guides or link to download and install it properly? I also tried doing the force command to run at 100 or 1000 but it keeps going back to 10 Mb/s

here are some info:

sudo lshw -C network
>   *-network               
       description: Ethernet interface
       product: RTL-8169SC Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@02:05.0
       logical name: eth0
       version: 10
       serial: 00:1a:4d:6f:d6:32
       size: 10MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=6.002.00 duplex=half ip=192.168.1.37 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=twisted pair speed=10MB/s


ifconfig -a
> 
eth0      Link encap:Ethernet  HWaddr 00:1A:4D:6F:D6:32  
          inet addr:192.168.1.37  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:4dff:fe6f:d632/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29187 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30380 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6360891 (6.0 MiB)  TX bytes:17805176 (16.9 MiB)
          Interrupt:21 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)


---

### Post by noob12 on 2007-09-18
You're running at 10 with half duplex.  Check cables and the other port.  Make sure you are plugged in to the port right at boot.  Assuming the other side is capable of 1000, 
```

sudo ifdown eth0
sudo ethtool -s eth0 speed 1000 duplex full autoneg off
sudo ifup eth0

```

After that, **sudo ethtool eth0** will tell you the current situation.

You can put this in a **pre-up** if it works for you

---

### Post by onebelo on 2007-09-18
tried the above commands but still getting 10Mb/s @ half duplex

tried diff CAT6 cable, tried plugging it into a diff port on the gigabit switch. same thing. i get an orange light while my vista machine thats also plugged into the switch gets a green light which means gigabit connection. 

any other ideas?

---

### Post by onebelo on 2007-09-18
just tried other configurations .. testing other ports on the switch with vista machine and gigabit works on that.

i did get it to work with 100 Mb/s and Full duplex though .. but it seems like everytime i try to set it to 1000 Mb/s, it keeps defaulting back to 10 Mb/s Half duplex .. hmmm

---

### Post by noob12 on 2007-09-18
Are there any errors in **dmesg** or **/var/log/kern.log**  during boot or when you try to push the speed to 1000?

---

### Post by onebelo on 2007-09-19
towards the end of **dmesg** i get this:

> 
[  216.624064] r8169: eth0: link up
[  224.958825] r8169: eth0: link down
[  226.655262] r8169: eth0: link up
[  226.655275] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  241.355025] eth0: no IPv6 routers present


does the IPv6 have any effect on that? what about the motherboard I'm using? is there something in BIOS possibly that i need to enable for gigabit? gigabyte ga-945gcm-s2

---

### Post by noob12 on 2007-09-19
That's all normal.  Try reloading with the debug option and seeing if it says anything interesting in those same logs.
```

sudo ifdown eth0
sudo modprobe -r r8169
sudo modprobe r8169 debug=16
sudo ethtool -s eth0 speed 1000 duplex full autoneg off
sudo ifup eth0

```

---

### Post by onebelo on 2007-09-19
i did the above with debug and this is what i get with dmesg

> 
[  253.706978] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  253.706983] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  490.362784] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[  490.362790] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[  678.951776] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[  678.951782] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[  680.888331] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  680.888337] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  686.808075] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  686.808081] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  691.678743] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  691.678748] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  696.759538] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  696.759544] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  706.893361] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  706.893366] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  709.946615] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  709.946621] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  726.238989] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  726.238995] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  728.951525] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  728.951530] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  732.586160] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  732.586166] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  734.694208] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  734.694214] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  737.431573] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  737.431578] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  738.340512] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[  738.340517] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[  739.831004] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  739.831010] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  744.815231] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  744.815237] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  821.618948] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[  821.618953] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[  822.323537] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  822.323543] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  945.601279] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[  945.601285] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[  945.836568] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  945.836573] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  950.028628] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  950.028633] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 1143.412327] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 1143.412333] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 1229.846411] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 1229.846416] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 1291.969876] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 1291.969882] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 1292.260413] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 1292.260419] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 1379.719274] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 1379.719280] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 1380.839252] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 1380.839257] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 1577.762550] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 1577.762555] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 1578.994544] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 1578.994550] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 1831.097572] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 1831.097578] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 1972.629017] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 1972.629023] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 1974.569225] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 1974.569231] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 1977.512619] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 1977.512627] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 1980.428551] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 1980.428557] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 1985.807178] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 1985.807183] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 1988.166015] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 1988.166021] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 1990.830184] atkbd.c: Unknown key released (translated set 2, code 0xd9 on isa0060/serio0).
[ 1990.830190] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 2767.343793] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 2767.343798] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 2767.533443] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 2767.533449] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 2937.484586] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 2937.484592] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 3079.447164] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 3079.447170] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 3081.982137] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 3081.982142] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 3086.071515] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 3086.071521] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 3159.407963] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 3159.407969] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 3161.414120] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 3161.414126] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 3248.049003] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 3248.049008] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 3286.461621] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 3286.461627] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 3302.021071] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 3302.021076] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 3305.321080] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 3305.321086] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 3323.352594] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 3323.352600] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 4474.940722] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 4474.940728] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 4476.468515] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 4476.468520] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 4496.106744] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 4496.106750] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 4501.314131] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 4501.314137] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 4502.534309] ACPI: PCI interrupt for device 0000:02:05.0 disabled
[ 4508.619441] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 4508.619447] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 4515.080317] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 4515.080323] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 4516.243969] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 21 (level, low) -> IRQ 21
[ 4516.244360] eth0: RTL8169SC/8110SC at 0xffffc2000001a000, 00:1a:4d:6f:d6:32, IRQ 21
[ 4516.270842] r8169: eth0: link down
[ 4516.270865] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 4521.216513] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 4521.216519] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 4525.993165] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 4525.993171] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 4526.252034] eth0: PHY reset until link up
[ 4529.062734] r8169: eth0: link up
[ 4529.066197] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 4530.728683] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 4530.728688] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 4532.693393] r8169: eth0: link down
[ 4534.418408] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 4534.418414] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 4537.413343] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 4537.413348] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 4539.722215] eth0: no IPv6 routers present
[ 4542.677499] eth0: PHY reset until link up
[ 4544.024334] r8169: eth0: link up
[ 4544.125666] r8169: eth0: link down
[ 4546.147206] r8169: eth0: link up
[ 4558.494083] eth0: no IPv6 routers present
[ 4570.191949] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 4570.191954] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 4576.247201] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 4576.247206] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 4688.461471] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).


does that help any?

---

### Post by noob12 on 2007-09-20
Well, we got no real info from the debug output, but the "PHY reset until link up" message suggests why the ethool command isn't doing anything; I think the settings are getting lost at that point.  
```

[ 4542.677499] eth0: PHY reset until link up
[ 4544.024334] r8169: eth0: link up

```

Maybe running it after the link is up will work?  

I don't see any sign of what's happening and I haven't seen this issue before.  Maybe a wider web search will turn up something.

---

### Post by onebelo on 2007-09-20
yea i tried searching google as well as on here but to no avail ...

would getting a PCI gigabit network card instead of using onboard nic work better? from a quick search, ive read this SMC card works pretty good in linux .. do you know anything about it?

SMC SMC9452TX-1 10/ 100/ 1000Mbps PCI EZ Card Copper Gigabit Card 1 x RJ45 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833129144](http://www.newegg.com/Product/Product.aspx?Item=N82E16833129144)

---

### Post by noob12 on 2007-09-20
No I don't.  Sorry.

I wouldn't abandon your onboard one just yet.  I think there are a lot of people using the 8169 chipset successfully.  Have you tried posting a question / bug report on launchpad?  You'll get the real experts there.

I've used Intel Pro/1000, Marvel Yukon 88E80xx chipsets, and Broadcom BCM5752 based gigabit.  I have only run the Marvel ones on actual gigabit + jumbo frames.  The support level on the Intel ones seems very good with latest e1000 drivers, but I haven't had an opportunity to really test them out.

I'm suspecting some sort of timing issue now, but I don't have concrete suggestions.  I'd be randomly playing with boot flags, hoping to get lucky.  So I can't pretend to lead you there.

---

### Post by zimdba on 2007-09-26
I have the same issue.  Whenever I try to "force" the card to do 1000, duplex full, autoneg off, it goes back down to 10Mbps, half duplex.

I've tried a D-Link card with a Marvell chipset - same behavior.

So I can't get gig-E and I can't bond the cards.

Realtek released a new driver on 2007/09/19 - v. 6.003.00.  I'll try that when I get home - you may want to try it too.

I've also noticed that when I issue "mii-tool eth0" then it states that my switch isn't advertising gig-E.  The switch is a Netgear GS116.  Windows clients have no problems connecting/transferring at gig-E (although without jumbo frames).  Does anyone know if that would be the problem?  Buying a new 16-port Gig-E switch just to see if it works isn't really in the budget.

Thx.

---

### Post by samborambo on 2008-02-01
I've  been having a similar issue. All of a sudden (possibly after a kernel upgrade), my RTL-8169SC (rev 10) would not connect at 100MB full duplex - only 10MB half. ethtool wouldn't let me renegotiate the connection (operation not supported) but mii-tool did. As a kind of "band-aid", I've added a line to the stanza in /etc/network/interfaces :

```
iface eth1 inet static
        address 10.1.1.60
        netmask 255.0.0.0
        network 10.0.0.0
        broadcast 10.255.255.255
        gateway 10.1.1.1
        pre-up mii-tool -r eth1

```
Of course, the same would apply to a dhcp stanza.

This bug may only apply to 2.6.20-16 (Feisty) or there abouts.  I've seen a couple of bug-reports relating to this. Hopefully it's fixed in Gutsy.

---

### Post by moonlightcheese on 2008-02-15
[http://ubuntuforums.org/showthread.php?t=101117](http://ubuntuforums.org/showthread.php?t=101117)
good info there

also:

[quote=ethermanage.com]While Auto-Negotiation can be disabled on 10BASE-T and 100BASE-TX links, it is required on 1000BASE-T systems since Gigabit Ethernet systems use Auto-Negotiation to establish the master-slave signal timing control required to make the link operational.[/quote]
so you can't do this:
```
sudo ifdown eth0
sudo ethtool -s eth0 speed 1000 duplex full **autoneg off**
sudo ifup eth0
```

this may be why you can't set to 1000 because the command is failing because autoneg off is not a valid option for 1000mbps nics.  just a guess??

ipv6 won't affect this.

i've had the same connection issues with both my onboard nics (Marvel Yukon 88E80xx and nForce4 nic) and both of them suffer from slow speeds.  scouring the boards, forums and pages for info trying to find the actual fix...  if anybody finds it... sticky it.  i don't wanna have to look for this again.  no one seems to have the answer to quick throughput on 1Gbps nics :(

read this if your network speeds are slow.  [http://www.hep.ucl.ac.uk/~ytl/tcpip/linux/txqueuelen/datatag-tcp/](http://www.hep.ucl.ac.uk/~ytl/tcpip/linux/txqueuelen/datatag-tcp/)

---

