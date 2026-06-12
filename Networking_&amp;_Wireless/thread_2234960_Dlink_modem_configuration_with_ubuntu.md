---
title: "Dlink modem configuration with ubuntu"
date: 2014-07-17
forum: Networking &amp; Wireless
---

### Post by gomathi_sankar on 2014-07-17
hi ,i have been using ubuntu for the last 4 years though i am not a techie.I have a dual booting system with windows 7 and ubuntu 14.04 now ,ubuntu being the prime os.recently i bought a dlink wifi modem and adapter model DSL 2730U.Though the company said it supports only windows and mac i went for it because i read somebody using it with linux  with some manual configuration.I thought i will find some answers on the internet but alas could not find any.my modem configures perfectly with windows but not with ubuntu .ubuntu does not recogonize the modem at all.i am at  loss .i need real help here.and remember i am not a techie.

thanks .

---

### Post by varunendra on 2014-07-19
Welcome to the forums Gomathi Sankar!

Is this your modem : [http://www.dlink.co.in/products/?pid=451](http://www.dlink.co.in/products/?pid=451) ?

How have you connected it to the Ubuntu system? Via cable or wireless?

---

### Post by gomathi_sankar on 2014-07-21
yes varun!atlast!I am trying to connect it through cable.but could not

---

### Post by varunendra on 2014-07-21
While it is connected via cable, please open a terminal (Ctrl-Alt-T) and post back the outputs of -
```
sudo lshw -C network
nm-tool
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by gomathi_sankar on 2014-07-23
code *-network       description:Ethernet interface 
       product:RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller 
       vendor:Realtek Semiconductor Co., Ltd. 
       physical id:0 
       bus info:pci@0000:03:00.0 
       logical name:eth0 
       version: 03 
       serial:00:1c:c0:d8:15:cc 
       size:100Mbit/s 
       capacity:1Gbit/s 
       width: 64bits 
       clock: 33MHz 
       capabilities:pm msi pciexpress msix vpd bus_master cap_list rom ethernet physicaltp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
      configuration: autonegotiation=on broadcast=yes driver=r8169driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-1.fwlatency=0 link=yes multicast=yes port=MII speed=100Mbit/s 
       resources:irq:43 ioport:e000(size=256) memory:d0414000-d0414fffmemory:d0410000-d0413fff memory:d0400000-d040ffff /code 


State: disconnected 


- Device: eth0----------------------------------------------------------------- 
  Type:             Wired 
  Driver:           r8169 
  State:            disconnected 
  Default:          no 
  HW Address:       00:1C:C0:D8:15:CC 


  Capabilities: 
    Carrier Detect: yes 
    Speed:          100 Mb/s 


  Wired Properties 
    Carrier:        on  /code

---

### Post by gomathi_sankar on 2014-07-23
```

*-network       description:Ethernet interface 
       product:RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller 
       vendor:Realtek Semiconductor Co., Ltd. 
       physical id:0 
       bus info:pci@0000:03:00.0 
       logical name:eth0 
       version: 03 
       serial:00:1c:c0:d8:15:cc 
       size:100Mbit/s 
       capacity:1Gbit/s 
       width: 64bits 
       clock: 33MHz 
       capabilities:pm msi pciexpress msix vpd bus_master cap_list rom ethernet physicaltp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
      configuration: autonegotiation=on broadcast=yes driver=r8169driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-1.fwlatency=0 link=yes multicast=yes port=MII speed=100Mbit/s 
       resources:irq:43 ioport:e000(size=256) memory:d0414000-d0414fffmemory:d0410000-d0413fff memory:d0400000-d040ffff /code 


State: disconnected 


- Device: eth0----------------------------------------------------------------- 
  Type:             Wired 
  Driver:           r8169 
  State:            disconnected 
  Default:          no 
  HW Address:       00:1C:C0:D8:15:CC 


  Capabilities: 
    Carrier Detect: yes 
    Speed:          100 Mb/s 


  Wired Properties 
    Carrier:        on 

```

---

### Post by gomathi_sankar on 2014-07-23
varun!sorry !i forgot your code conduct.ignore my first reply

---

### Post by varunendra on 2014-07-23
> **gomathi_sankar said:**
> ```
duplex=full firmware=rtl_nic/rtl8168d-1.fwlatency=0 **[COLOR="#0000CD"]link=yes[/COLOR]** multicast=yes port=MII speed=100Mbit/s
```
The part highlighted above means a physical connection is detected and connected - means Ubuntu HAS recognized that there is a device on the other side of the cable, and is ready to get connected to it. Now to configure the modem, you need to log into its admin web interface. For that, you will have to consult its user manual and find the method to configure it via web interface (being connected via Ethernet cable).

The configuration would be same as in Windows or OSX - that is independent of OS. As soon as you enable the port that the Ethernet cable is connected to, and configure the DHCP in the modem, Ubuntu will get an IP address automatically and will show as connected. To configure WAN (Internet) connection, additional steps would be required - again in the modem itself. All of that should be described with screenshots in the user manual.

Generally, you have to enter an IP address (usually 192.168.1.1, but can be different for some modems/routers) in the address bar of the browser (e.g. firefox in Ubuntu) > press Enter to connect to it. It will then ask for ID, Password to authenticate you. The default ID/PW should be given in either the use manual, or at the bottom sticker of the modem. Enter those correctly to log in to the admin web interface. From here you can do further configuration as required.


> **gomathi_sankar said:**
> varun!sorry !i forgot your code conduct.ignore my first reply
You can always "Edit" your existing posts to make desired changes. In fact it is multiple posting in a row that should be avoided unless necessary. :)

---

### Post by gomathi_sankar on 2014-07-23
the manual just says use the cd  or login into 198.168.1.1 but the cd is useless because it is only windows/mac friendly.when i enter this address on the address bar nothing happens the browser just says this page can not be loaded

---

### Post by varunendra on 2014-07-23
> **gomathi_sankar said:**
> ...or login into 198.168.1.1

This is what you need ^^. Forget the cd, I avoid using it even on Windows, since all it provides can easily be done via the web interface without installing anything on the system.

However, regarding the "page can not be loaded" error, please try this -

In a terminal run the following commands -
```
sudo ifconfig eth0 down
sudo ifconfig eth0 192.168.1.100
```

Then check -
```
ifconfig
```
Does the output show the interface "eth0" to be "UP" and with an IP address "192.168.1.100"? If yes, try connecting to "192.168.1.1" again via the browser. If it still fails, try resetting the modem using the reset button of the modem (check the manual if you can't locate it), then try again.

Once the "Link" is detected on an Ethernet interface, it means half the task is accomplished, only the configuration part is remaining.

---

### Post by gomathi_sankar on 2014-07-24
this is the response i get to your commands .but still i cant login to the router.. i tried resetting the modem too 

```

eth0      Linkencap:Ethernet  HWaddr 00:1c:c0:d8:15:cc  
          inetaddr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0 
          inet6addr: fe80::21c:c0ff:fed8:15cc/64 Scope:Link 
          UPBROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RXpackets:0 errors:0 dropped:0 overruns:0 frame:0 
          TXpackets:125 errors:0 dropped:0 overruns:0 carrier:0 
         collisions:0 txqueuelen:1000 
          RX bytes:0(0.0 B)  TX bytes:25226 (25.2 KB) 


lo        Linkencap:Local Loopback  
          inetaddr:127.0.0.1  Mask:255.0.0.0 
          inet6addr: ::1/128 Scope:Host 
          UPLOOPBACK RUNNING  MTU:65536  Metric:1 
          RXpackets:560 errors:0 dropped:0 overruns:0 frame:0 
          TXpackets:560 errors:0 dropped:0 overruns:0 carrier:0 
         collisions:0 txqueuelen:0 
          RXbytes:44663 (44.6 KB)  TX bytes:44663 (44.6 KB)  

```

---

### Post by varunendra on 2014-07-24
While this manually assigned IP is in effect, can you ping the modem? That is -
```
ping -c4 192.168.1.1
```
..do you get a ping response? From here, I have no idea what to suggest other than confirming with the router manual that you did the reset correctly and checking/replacing cable etc.

As per the modem's manual, its default IP should be 192.168.1.1, and as per the lshw output, you are physically connected to it. So even after assigning a manual IP in the same network segment, if it is not connecting, then either something is not being done correctly, or there is some deeper problem you have to fix first.

Can you try the connection from a Live session (Ubuntu running directly from the Live DVD/USB)?

---

### Post by gomathi_sankar on 2014-09-04
hi varun today i solved this problem in a rather stupid or costlier way.after trying everything you said i bought another tp link which said it was linux savvy.i had to work with windows all the while which i hated.yesterday the tp link modem arrived and it directly connected  into ubuntu but no wifi at all.then i tried to configure it with windows .and it worked  with windows perfectly both wired and wireless now again when i come back to ubuntu it wont work! it .even wont log in to the modem .i was clearly stumped .and again did all the things that was on the web for no avail.then i did accidently did a thing.i changed the connection to ethernet from dsl connection .now it worked !and in a curious mood i tried the old dlink modem too with this method yes it also worked !i feel very stupid and wise at the sametime now.if i have done this earlier!i dont know what i did wrong or what i did right now..posting here only for the future stumblers like me.and i will be thankful if you can explain this to me

---

### Post by varunendra on 2014-09-05
> **gomathi_sankar said:**
> i changed the connection to ethernet from dsl connection

Where? In Network Manager? I'm slightly confused because a DSL connection requires an ID/Password. Usually, it is configured within the router/modem itself in an "Always On" (PPPoE) configuration (means the modem will automatically connect with the ID/Password as soon as it is powered on), and the client computers then only need to connect using a simple Ethernet connection.

If the modem is configured in that way, configuring it in the client (your computer) again won't work (it will give an error something like "ppp is already being used by some other service.."). If configuring it in Network Manager worked, then it means it wasn't configured within the modem, and you must have configured it in Windows too - which if you had done, you should have already been aware that you need to save the ID/password *somewhere* in Ubuntu as well to establish the connection.

---

### Post by gomathi_sankar on 2014-09-06
i just went into the network icon and clicked the edit connections and added an ethernet connection and used it instead of the dsl connection i used previously to connect

---

