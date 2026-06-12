---
title: "Internet connection problem"
date: 2011-07-10
forum: New to Ubuntu
---

### Post by lyni on 2011-07-10
the other night I was on the internet when for no apparent reason the websites I was on all said 'Server Not Found' 
I tried restarting the computer but I still could not reconnect to the internet. then I noticed that the PPP light on the modem was turned off. I tried turning the modem on and off but that didn't work.

next day I tried again with the same results- no PPP light on the modem. I tried a different cable but that didn't work either.

I then rang my service provider and they were able to get the PPP light to come on. my computer then showed that it was connected to the internet but each time I went to any website it just said 'Loading' for quite a while and then 'Server Not Found'

my service provider said it must be some communication problem between the modem and the computer and couldn't help any further.
then I plugged the modem into my laptop and I was able to connect to the internet straight away. so I am now on my laptop but cannot get a connection on my desktop computer.

is there something I can do to check if there is a communication problem between my modem and my desktop computer?

I have Ubuntu 10.4 installed on my desktop and I have a wired connection.
thanks 
lyn

---

### Post by s1baker on 2011-07-11
Were you using a proxy by chance that went bad?

---

### Post by lyni on 2011-07-11
> **s1baker said:**
> Were you using a proxy by chance that went bad?

no. I did nothing different. I didn't download anything. I didn't go to any new websites. I didn't get any funny emails that might have done any damage.

I just don't know what the connection problem between the computer and modem would be.
as I said in my post I have connected the modem to my laptop (which is what I'm on now) and I get onto the internet straightaway.

thanks
lyn

---

### Post by wep940 on 2011-07-11
Is this a DSL connection?  How do you connect the DSL modem to your computer?
 
Is this a dial-up modem connection?  If so, have you checked things like the baud rate, parity, etc., to be sure they still match?
 
Do you have things like the DNS server, gateway, etc., all defined correctly?

---

### Post by wildmanne39 on 2011-07-11
Hi, run these commands with your wireless card plugged in from the computer with the problem.
```
sudo lshw -C network 
```
```
lspci -nn
```
```
iwconfig
```
```
lsmod
```
```
lsusb
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by lyni on 2011-07-11
I have a wired DSL connection. I have a cable that plugs into the modem at one end and the computer on the other.

I do not have a wireless card because I am on a wired connection.

when I was disconnected from the internet I had been on for several hours.

the icon on the top panel shows that I am connected to the internet but when I go to any web page it just says 'Loading' for ages then it says 'Server Not Found'

thanks for your replies. is there something simple I can check on to see why the web pages won't load?

lyn

---

### Post by wildmanne39 on 2011-07-11
Hi, have your checked in your browser to make sure you are  not working in off line mode? Also run these commands they will tell us the status of your connection.
```
 lshw -C network
```
```
ifconfig
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by lyni on 2011-07-11
hi Wildmanne39, I had to go to my computer that I can't connect to the internet to go into the terminal and because I can't just copy and paste it directly over from that computer to this one I had to print it.

lshw -C network
WARNING: you should run this program as super-user.
*-network
    description: Ethernet interface
    product: L1 Gigabit Ethernet Adapter
    vendor: Atheros Communications
    physical id: 0
    bus info: pci@0000:02:00.0
    logical name: ethO
    version: bO
    serial:00:1e:8c:7f:8c:bb
    width: 64 bits
    clock: 33MHz
    capabilities: bus_master cap_list rom ethernet physical
    configuration: broadcast=yes driver=atl1 driverversion=2.1.3 firmware=N/A latency=0 multicast=yes
    resources:irq:28 memory:feac0000-feabffff(prefetchable)

---

### Post by lyni on 2011-07-11
Wildmanne39 here is the other printout

ifconfig

eth0   Link encap:Ethernet  HWaddr 00:1e:8c:7f:8c:bb
     UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
     RX packets:0 errors:0 dropped:0 overruns:0 frame:0
     TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
     collisions:0 bcqueuelen:1000
     RX bytes:0 (0.0B) TX bytes:0 (0.0B)

lo   Link encap:Local Loopback
     inet addr:127.0.0.1 Mask:255.0.0.0
     inet6 addr: ::1/128 Scope:Host
     UP LOOPBACK RUNNING MTU:16436 Metric:1
     RX packets:4568 errors:0 dropped:0 overruns:0 frame:0
     TX packets:4568 errors:0 dropped:0 overruns:0 carrier:0
     collisions:0 bcqueuelen:0
     RX bytes:153616 (153.6 KB)  TX bytes:153616 (153.6 KB)


sorry this has been so convoluted but I had to go from one computer to the other.

---

### Post by wep940 on 2011-07-11
Did you check the DNS server, gateway, etc., as I suggested earlier?  If the DNS is wrong, you can be connected all you want to but you'll never get to a site online.

---

### Post by lyni on 2011-07-11
> **wep940 said:**
> Did you check the DNS server, gateway, etc., as I suggested earlier?  If the DNS is wrong, you can be connected all you want to but you'll never get to a site online.

no I have not checked because when I spoke to my internet provider they said its not the DNS.
could you let me know how I check it? I haven't done it for some time.

thanks again
lyn

---

### Post by Wim Sturkenboom on 2011-07-11
> **lyni said:**
> 

```

eth0   Link encap:Ethernet  HWaddr 00:1e:8c:7f:8c:bb
     UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
     RX packets:0 errors:0 dropped:0 overruns:0 frame:0
     TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
     collisions:0 bcqueuelen:1000
     RX bytes:0 (0.0B) TX bytes:0 (0.0B)

```

You don't have an IP address; I guess you have to set it up using network manager or pppoeconf.

---

### Post by lyni on 2011-07-11
> **Wim Sturkenboom said:**
> You don't have an IP address; I guess you have to set it up using network manager or pppoeconf.

how do I do that? in simple steps please.

thank you
lyn

---

### Post by wildmanne39 on 2011-07-11
> **lyni said:**
> how do I do that? in simple steps please.

thank you
lynHi, I am not an expert on this but here are the instructions I have.
```
sudo pppoeconf
```
once you have executed the command enter any information it asks for. When completed the next command will be 
```
sudo pon -dsl provider
```
Once this command is executed if you have no errors open a browser and navigate to a site. If you have errors or questions post back. I have not manually setup an internet connection in years because they just work on my computer, good luck.

---

### Post by arena001 on 2011-07-11
I am not an expert and I can see many people helping. You can just try to ping in order to get the information. If it's pinging and you are not able to connect to Internet then it's a DNS problem. Just open the terminal and type 

```
ping www.google.com
```

Again I am not a expert. It was just a normal information that may help you.

---

### Post by wep940 on 2011-07-11
> **arena001 said:**
> I am not an expert and I can see many people helping. You can just try to ping in order to get the information. If it's pinging and you are not able to connect to Internet then it's a DNS problem. Just open the terminal and type 
 
```
ping www.google.com
```
 
Again I am not a expert. It was just a normal information that may help you.Just remember - if DNS is not working, it can't translate a www domain name to an IP address.  So, in order to really test this, get the IP address of something you know (like perhaps yahoo).  First try pinging that IP address - if that doesn't work there is another problem.  If it works, then try pinging [www.yahoo.com]("http://www.yahoo.com") (or whatever the IP address is for).  If that fails, then there are DNS problems like the DNS server not being defined.  
 
The ppp config will let you set those up.

---

### Post by arena001 on 2011-07-12
> **wep940 said:**
> Just remember - if DNS is not working, it can't translate a www domain name to an IP address.  So, in order to really test this, get the IP address of something you know (like perhaps yahoo).  First try pinging that IP address - if that doesn't work there is another problem.  If it works, then try pinging [www.yahoo.com]("http://www.yahoo.com") (or whatever the IP address is for).  If that fails, then there are DNS problems like the DNS server not being defined.  
 
The ppp config will let you set those up.

As I told you I am not a expert was just trying to help the way I can.

---

### Post by lyni on 2011-07-12
thanks to everyone for their suggestions. before I try those things I'd like to ask another question please.
when I did those readouts from the Terminal my computer was not plugged into the modem because I have the modem plugged into this laptop that I'm using to come onto the forum.
would that have made a difference if I had the affected computer connected to the modem? would it have said I do have an IP address if it was connected to the modem?
lyn

---

### Post by arena001 on 2011-07-12
> **lyni said:**
> thanks to everyone for their suggestions. before I try those things I'd like to ask another question please.
when I did those readouts from the Terminal my computer was not plugged into the modem because I have the modem plugged into this laptop that I'm using to come onto the forum.
would that have made a difference if I had the affected computer connected to the modem? would it have said I do have an IP address if it was connected to the modem?
lyn


Big LOL...Hahaha

Yes of course you need to connect.

---

### Post by jtarin on 2011-07-12
Open your /etc/resolv.conf in gedit....copy and post the results here.
In a terminal:
```
gksudo gedit /etc/resolv.conf
```

---

### Post by lyni on 2011-07-12
> **arena001 said:**
> Big LOL...Hahaha

Yes of course you need to connect.

thank you arena001. it didn't occur to me until after I'd posted the readings from the terminal.
I think I may have to do it all again - this time with the affected computer connected to the modem.
I wish I was a tech head!
thanks again
lyn

---

### Post by lkraemer on 2011-07-12
I'd suggest starting with a quick look at your router and the back of your computer where
the Ethernet cable plugs in.  Your Ethernet Port (on Motherboard or Network Card) has some
LED's.  A Power LED and a Connection LED.  The POWER LED is TYPICALLY GREEN, and the 
Connection (LINK) LED is TYPICALLY YELLOW when everything is GOOD from the Computer to the
Router or DSL/Cable Modem.  Now follow the Ethernet cable to the DSL/Cable Modem and
it should be plugged into a Port (1 thru 4).  Look on the front of the DSL/Cable Modem
and see if there is a Link LED that is "ON" (TYPICALLY GREEN) for a connection to that Port.

Next, I'd use the ping command.  Open a Terminal and try a ping to
google.com's IP address for 3 pings ONLY.....................Please:
```

ping -c 3 74.125.225.18

```
You should see something like:
```

PING www.l.google.com (74.125.225.18) 56(84) bytes of data.
64 bytes from 74.125.225.18: icmp_req=1 ttl=54 time=21.4 ms
64 bytes from 74.125.225.18: icmp_req=2 ttl=54 time=23.2 ms
64 bytes from 74.125.225.18: icmp_req=3 ttl=54 time=23.5 ms

--- www.l.google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 10132ms
rtt min/avg/max/mdev = 21.490/22.779/23.588/0.929 ms

```

Then repeat the command for:
```

ping -c 3 www.google.com

```
This tells you that the DNS Servers correctly located and found the IP address
of Google at 74.125.225.18.........So, every thing is working properly!

To get more information you can also use the following commands:
```

route
route -nee
netstat -r

```

and don't forget about these commands in a Terminal:
```

man ping
man route
man netstat

```


Larry

---

### Post by lyni on 2011-07-12
for some reason this computer is now working. I thought I'd just try it and the internet connected straightaway. 
but I have done a print out of the terminal information that I originally got wrong. I'd appreciate anyone comment on anything that may be wrong because I don't understand the readout.

lyn@lyn-desktop:~$ lshw 
WARNING: you should run this program as super-user. 
lyn-desktop               
    description: Computer 
    width: 32 bits 
  *-core 
       description: Motherboard 
       physical id: 0 
     *-memory 
          description: System memory 
          physical id: 0 
          size: 2012MiB 
     *-cpu 
          product: Intel(R) Core(TM)2 Duo CPU     E8200  @ 2.66GHz 
          vendor: Intel Corp. 
          physical id: 1 
          bus info: cpu@0 
          version: 6.7.6 
          serial: 0001-0676-0000-0000-0000-0000 
          size: 1998MHz 
          capacity: 1998MHz 
          width: 64 bits 
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm tpr_shadow vnmi flexpriority cpufreq 
          configuration: id=0 
        *-logicalcpu:0 
             description: Logical CPU 
             physical id: 0.1 
             width: 64 bits 
             capabilities: logical 
        *-logicalcpu:1 
             description: Logical CPU 
             physical id: 0.2 
             width: 64 bits 
             capabilities: logical 
     *-pci 
          description: Host bridge 
          product: 82G33/G31/P35/P31 Express DRAM Controller 
          vendor: Intel Corporation 
          physical id: 100 
          bus info: pci@0000:00:00.0 
          version: 02 
          width: 32 bits 
          clock: 33MHz 
        *-pci:0 
             description: PCI bridge 
             product: 82G33/G31/P35/P31 Express PCI Express Root Port 
             vendor: Intel Corporation 
             physical id: 1 
             bus info: pci@0000:00:01.0 
             version: 02 
             width: 32 bits 
             clock: 33MHz 
             capabilities: pci bus_master cap_list 
             configuration: driver=pcieport 
             resources: irq:24 ioport:d000(size=4096) memory:fa000000-fe9fffff ioport:d0000000(size=268435456) 
           *-display 
                description: VGA compatible controller 
                product: G86 [GeForce 8400 GS] 
                vendor: nVidia Corporation 
                physical id: 0 
                bus info: pci@0000:01:00.0 
                version: a1 
                width: 64 bits 
                clock: 33MHz 
                capabilities: bus_master cap_list rom 
                configuration: driver=nouveau latency=0 
                resources: irq:16 memory:fd000000-fdffffff memory:d0000000-dfffffff(prefetchable) memory:fa000000-fbffffff ioport:dc00(size=128) memory:fe9e0000-fe9fffff(prefetchable) 
        *-usb:0 
             description: USB Controller 
             product: 82801I (ICH9 Family) USB UHCI Controller #4 
             vendor: Intel Corporation 
             physical id: 1a 
             bus info: pci@0000:00:1a.0 
             version: 02 
             width: 32 bits 
             clock: 33MHz 
             capabilities: bus_master cap_list 
             configuration: driver=uhci_hcd latency=0 
             resources: irq:16 ioport:c800(size=32) 
        *-usb:1 
             description: USB Controller 
             product: 82801I (ICH9 Family) USB UHCI Controller #5 
             vendor: Intel Corporation 
             physical id: 1a.1 
             bus info: pci@0000:00:1a.1 
             version: 02 
             width: 32 bits 
             clock: 33MHz 
             capabilities: bus_master cap_list 
             configuration: driver=uhci_hcd latency=0 
             resources: irq:21 ioport:c880(size=32) 
        *-usb:2 
             description: USB Controller 
             product: 82801I (ICH9 Family) USB UHCI Controller #6 
             vendor: Intel Corporation 
             physical id: 1a.2 
             bus info: pci@0000:00:1a.2 
             version: 02 
             width: 32 bits 
             clock: 33MHz 
             capabilities: bus_master cap_list 
             configuration: driver=uhci_hcd latency=0 
             resources: irq:18 ioport:cc00(size=32) 
        *-usb:3 
             description: USB Controller 
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2 
             vendor: Intel Corporation 
             physical id: 1a.7 
             bus info: pci@0000:00:1a.7 
             version: 02 
             width: 32 bits 
             clock: 33MHz 
             capabilities: bus_master cap_list 
             configuration: driver=ehci_hcd latency=0 
             resources: irq:18 memory:f9fffc00-f9ffffff 
        *-multimedia 
             description: Audio device 
             product: 82801I (ICH9 Family) HD Audio Controller 
             vendor: Intel Corporation 
             physical id: 1b 
             bus info: pci@0000:00:1b.0 
             version: 02 
             width: 64 bits 
             clock: 33MHz 
             capabilities: bus_master cap_list 
             configuration: driver=HDA Intel latency=0 
             resources: irq:22 memory:f9ff8000-f9ffbfff 
        *-pci:1 
             description: PCI bridge 
             product: 82801I (ICH9 Family) PCI Express Port 1 
             vendor: Intel Corporation 
             physical id: 1c 
             bus info: pci@0000:00:1c.0 
             version: 02 
             width: 32 bits 
             clock: 33MHz 
             capabilities: pci bus_master cap_list 
             configuration: driver=pcieport 
             resources: irq:25 ioport:1000(size=4096) memory:80000000-803fffff ioport:f8f00000(size=1048576) 
        *-pci:2 
             description: PCI bridge 
             product: 82801I (ICH9 Family) PCI Express Port 5 
             vendor: Intel Corporation 
             physical id: 1c.4 
             bus info: pci@0000:00:1c.4 
             version: 02 
             width: 32 bits 
             clock: 33MHz 
             capabilities: pci bus_master cap_list 
             configuration: driver=pcieport 
             resources: irq:26 ioport:e000(size=4096) memory:feb00000-febfffff memory:80400000-805fffff(prefetchable) 
           *-ide 
                description: IDE interface 
                product: 88SE6121 SATA II Controller 
                vendor: Marvell Technology Group Ltd. 
                physical id: 0 
                bus info: pci@0000:03:00.0 
                version: b2 
                width: 32 bits 
                clock: 33MHz 
                capabilities: ide bus_master cap_list 
                configuration: driver=pata_marvell latency=0 
                resources: irq:16 ioport:ec00(size=8) ioport:e880(size=4) ioport:e800(size=8) ioport:e480(size=4) ioport:e400(size=16) memory:febffc00-febfffff 
        *-pci:3 
             description: PCI bridge 
             product: 82801I (ICH9 Family) PCI Express Port 6 
             vendor: Intel Corporation 
             physical id: 1c.5 
             bus info: pci@0000:00:1c.5 
             version: 02 
             width: 32 bits 
             clock: 33MHz 
             capabilities: pci bus_master cap_list 
             configuration: driver=pcieport 
             resources: irq:27 ioport:2000(size=4096) memory:fea00000-feafffff memory:80600000-807fffff(prefetchable) 
           *-network 
                description: Ethernet interface 
                product: L1 Gigabit Ethernet Adapter 
                vendor: Atheros Communications 
                physical id: 0 
                bus info: pci@0000:02:00.0 
                logical name: eth0 
                version: b0 
                serial: 00:1e:8c:7f:8c:bb 
                width: 64 bits 
                clock: 33MHz 
                capabilities: bus_master cap_list rom ethernet physical 
                configuration: broadcast=yes driver=atl1 driverversion=2.1.3 firmware=N/A ip=192.168.1.3 latency=0 multicast=yes 
                resources: irq:28 memory:feac0000-feafffff memory:feaa0000-feabffff(prefetchable) 
        *-usb:4 
             description: USB Controller 
             product: 82801I (ICH9 Family) USB UHCI Controller #1 
             vendor: Intel Corporation 
             physical id: 1d 
             bus info: pci@0000:00:1d.0 
             version: 02 
             width: 32 bits 
             clock: 33MHz 
             capabilities: bus_master cap_list 
             configuration: driver=uhci_hcd latency=0 
             resources: irq:23 ioport:c080(size=32) 
        *-usb:5 
             description: USB Controller 
             product: 82801I (ICH9 Family) USB UHCI Controller #2 
             vendor: Intel Corporation 
             physical id: 1d.1 
             bus info: pci@0000:00:1d.1 
             version: 02 
             width: 32 bits 
             clock: 33MHz 
             capabilities: bus_master cap_list 
             configuration: driver=uhci_hcd latency=0 
             resources: irq:19 ioport:c400(size=32) 
        *-usb:6 
             description: USB Controller 
             product: 82801I (ICH9 Family) USB UHCI Controller #3 
             vendor: Intel Corporation 
             physical id: 1d.2 
             bus info: pci@0000:00:1d.2 
             version: 02 
             width: 32 bits 
             clock: 33MHz 
             capabilities: bus_master cap_list 
             configuration: driver=uhci_hcd latency=0 
             resources: irq:18 ioport:c480(size=32) 
        *-usb:7 
             description: USB Controller 
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1 
             vendor: Intel Corporation 
             physical id: 1d.7 
             bus info: pci@0000:00:1d.7 
             version: 02 
             width: 32 bits 
             clock: 33MHz 
             capabilities: bus_master cap_list 
             configuration: driver=ehci_hcd latency=0 
             resources: irq:23 memory:f9fff800-f9fffbff 
        *-pci:4 
             description: PCI bridge 
             product: 82801 PCI Bridge 
             vendor: Intel Corporation 
             physical id: 1e 
             bus info: pci@0000:00:1e.0 
             version: 92 
             width: 32 bits 
             clock: 33MHz 
             capabilities: pci bus_master cap_list 
        *-isa 
             description: ISA bridge 
             product: 82801IB (ICH9) LPC Interface Controller 
             vendor: Intel Corporation 
             physical id: 1f 
             bus info: pci@0000:00:1f.0 
             version: 02 
             width: 32 bits 
             clock: 33MHz 
             capabilities: isa bus_master cap_list 
             configuration: latency=0 
        *-ide:0 
             description: IDE interface 
             product: 82801IB (ICH9) 2 port SATA IDE Controller 
             vendor: Intel Corporation 
             physical id: 1f.2 
             bus info: pci@0000:00:1f.2 
             version: 02 
             width: 32 bits 
             clock: 66MHz 
             capabilities: ide bus_master cap_list 
             configuration: driver=ata_piix latency=0 
             resources: irq:22 ioport:b000(size=8) ioport:ac00(size=4) ioport:a880(size=8) ioport:a800(size=4) ioport:a480(size=16) ioport:a400(size=16) 
        *-serial UNCLAIMED 
             description: SMBus 
             product: 82801I (ICH9 Family) SMBus Controller 
             vendor: Intel Corporation 
             physical id: 1f.3 
             bus info: pci@0000:00:1f.3 
             version: 02 
             width: 64 bits 
             clock: 33MHz 
             configuration: latency=0 
             resources: memory:f9fff400-f9fff4ff ioport:400(size=32) 
        *-ide:1 
             description: IDE interface 
             product: 82801I (ICH9 Family) 2 port SATA IDE Controller 
             vendor: Intel Corporation 
             physical id: 1f.5 
             bus info: pci@0000:00:1f.5 
             version: 02 
             width: 32 bits 
             clock: 66MHz 
             capabilities: ide bus_master cap_list 
             configuration: driver=ata_piix latency=0 
             resources: irq:22 ioport:c000(size=8) ioport:bc00(size=4) ioport:b880(size=8) ioport:b800(size=4) ioport:b480(size=16) ioport:b400(size=16) 
lyn@lyn-desktop:~$

---

### Post by lyni on 2011-07-12
this is the second terminal readout. I appreciate any comments that may help me prevent this problem in future.

lyn@lyn-desktop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1e:8c:7f:8c:bb  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0 
          inet6 addr: fe80::21e:8cff:fe7f:8cbb/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:38819 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:21091 errors:0 dropped:0 overruns:0 carrier:1 
          collisions:0 txqueuelen:1000 
          RX bytes:56825540 (56.8 MB)  TX bytes:1767196 (1.7 MB) 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:151 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:151 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:12329 (12.3 KB)  TX bytes:12329 (12.3 KB)

---

### Post by wildmanne39 on 2011-07-12
Hi, I am glad you got it working, there is nothing in that information that can show what caused it or how too prevent it from happening again,would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

### Post by lyni on 2011-07-12
> **wildmanne39 said:**
> Hi, I am glad you got it working, there is nothing in that information that can show what caused it or how too prevent it from happening again,would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

thanks again wildmanne39 for looking at that information. 
do you think I should mark it Solved? I don't know what caused the problem and I don't know what fixed it. when I turned the computer on today it connected straightaway without me doing anything.
lyn

---

### Post by wildmanne39 on 2011-07-12
Hi, you can give it a couple of days if you want or mark it solved and if this problem happens again start a new thread. The first information you posted that was your system specs it tell us what hardware you have, and the second command just confirms that you do have a internet connection now.

---

### Post by jtarin on 2011-07-12
> **lyni said:**
>  I don't know what caused the problem and I don't know what fixed it. when I turned the computer on today it connected straightaway without me doing anything.
lyn

Refer to my [post.]("http://ubuntuforums.org/showpost.php?p=11039169&postcount=20")

---

### Post by wep940 on 2011-07-13
> **arena001 said:**
> As I told you I am not a expert was just trying to help the way I can.
Hey - hope you understand no insult or anything was intended.  I just wanted to point out what could be added to your suggestion to make it a more reliable test.
 
Dave ;)

---

### Post by Wim Sturkenboom on 2011-07-13
> **lyni said:**
> 
```

lyn@lyn-desktop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1e:8c:7f:8c:bb  
          **[COLOR="Red"]inet addr:192.168.1.3[/COLOR]**  Bcast:192.168.1.255  Mask:255.255.255.0 
          inet6 addr: fe80::21e:8cff:fe7f:8cbb/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:38819 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:21091 errors:0 dropped:0 overruns:0 carrier:1 
          collisions:0 txqueuelen:1000 
          RX bytes:56825540 (56.8 MB)  TX bytes:1767196 (1.7 MB) 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:151 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:151 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:12329 (12.3 KB)  TX bytes:12329 (12.3 KB)
```
In red one of the first things you can check the next time that something like this happens. It does not have to be the same ip address but there should be one.

---

### Post by arena001 on 2011-07-14
> **wep940 said:**
> Hey - hope you understand no insult or anything was intended.  I just wanted to point out what could be added to your suggestion to make it a more reliable test.
 
Dave ;)


Hay wep940,

No problem at all, I can understand. :D

---

