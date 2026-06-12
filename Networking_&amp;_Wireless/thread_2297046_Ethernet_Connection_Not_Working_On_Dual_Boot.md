---
title: "Ethernet Connection Not Working On Dual Boot"
date: 2015-09-30
forum: Networking &amp; Wireless
---

### Post by adam164 on 2015-09-30
I just dual booted my system with Windows 10 and Ubuntu 14.04.3 and while my wired connection works perfectly when booted into Windows, Ubuntu refuses to connect. It sees there is a wired connection available and tries to connect repeatedly but always comes back with a failed to connect message.

results from ifconfig
```
ifconfig
eth0      Link encap:Ethernet  HWaddr e0:3f:49:7d:19:c1  
          inet6 addr: fe80::e23f:49ff:fe7d:19c1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7813 (7.8 KB)  TX bytes:11423 (11.4 KB)
          Interrupt:20 Memory:ef300000-ef320000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:151 errors:0 dropped:0 overruns:0 frame:0
          TX packets:151 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10785 (10.7 KB)  TX bytes:10785 (10.7 KB)

```
and sudo lshw -C network
```
*-network               
       description: Ethernet interface
       product: Ethernet Connection I217-V
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 05
       serial: e0:3f:49:7d:19:c1
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k duplex=full firmware=0.13-4 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:28 memory:ef300000-ef31ffff memory:ef339000-ef339fff ioport:f040(size=32)

```

---

### Post by SeijiSensei on 2015-10-01
That's a pretty bog-standard device so it's a bit puzzling that you cannot connect.

Let's try the manual approach.  First, determine what IP network your router is configured for.  Usually it will be something like 192.168.1.0/24.  If you're not sure what it is, boot into Windows, then run cmd.exe from the Start menu and type the command "ipconfig /all".  You'll see an entry for the Ethernet adapter with its address.  Write that down, and write down the "netmask" and "default gateway" entries as well.  I'll use 255.255.255.0 for the first of those and 192.168.1.1 for the second.

Now boot into Linux and see if you can use the same address there. Suppose your machine received the address 192.168.1.50.  Open a terminal in Linux and run the command
```
sudo ifconfig eth0 192.168.1.50 netmask 255.255.255.0
```
What happens? Can you ping the router with "ping 192.168.1.1"?  If that works, run the command
```
sudo ip route add default via 192.168.1.1
```
Can you ping Google's DNS server at 8.8.8.8?

Obviously if your router gives you a different set of addresses, substitute those in the commands above.

---

### Post by adam164 on 2015-10-01
Here are my results

In Windows, I got the following addresses:
```

IPv4 Address. . . . . . . . . . . : 192.168.0.107(Preferred)
Subnet Mask . . . . . . . . . . . : 255.255.255.0
Default Gateway . . . . . . . . . : 192.168.0.1

```

I followed your instructions in ubuntu here:
```
adam@Darla:~$ sudo ifconfig eth0 192.168.0.107 netmask 255.255.255.0
[sudo] password for adam: 
adam@Darla:~$ ping 192.168.0.1
connect: Network is unreachable
adam@Darla:~$ ping 8.8.8.8
connect: Network is unreachable
adam@Darla:~$ sudo ip route add default via 192.168.0.1
RTNETLINK answers: Network is unreachable

```

It doesn't seem happy about it. Is it that my router is seeing the dual boot as two separate computers fighting for the same IP and denying one? I'm pretty novice at networking so any knowledge you got to share is appreciated.

---

### Post by SeijiSensei on 2015-10-01
I'm as puzzled as you.  After you run the ifconfig command to set the address, run "ifconfig eth0" again (with or without sudo) to see if the adapter accepted the address.

I [checked at Intel]("https://downloadcenter.intel.com/product/71305/Intel-Ethernet-Connection-I218-V") and it recommends the e1000 driver that your machine says it is using.  Let's also make sure the driver was loaded.  Run the command 
```
lsmod | grep e1000
```
You should get a result like
```
e1000                 145174  0
```
Don't worry if the numbers are somewhat different.  We're just checking to make sure the driver was loaded.

In a dual-boot arrangement, each OS is entirely ignorant of the other, so there shouldn't be any contention over the device.

---

### Post by adam164 on 2015-10-01
Results:
```

adam@Darla:~$ sudo ifconfig eth0 192.168.0.107 netmask 255.255.255.0
[sudo] password for adam: 
Sorry, try again.
[sudo] password for adam: 
adam@Darla:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr e0:3f:49:7d:19:c1  
          inet addr:192.168.0.107  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::e23f:49ff:fe7d:19c1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:37 errors:0 dropped:0 overruns:0 frame:0
          TX packets:102 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7948 (7.9 KB)  TX bytes:20519 (20.5 KB)
          Interrupt:20 Memory:ef300000-ef320000 


adam@Darla:~$ lsmod | grep e1000
e1000e                237568  0 
ptp                    20480  1 e1000e

```

---

### Post by SeijiSensei on 2015-10-02
Look at the results of the command "route -n".  You should see an entry like
```

192.168.0.0   0.0.0.0   255.255.255.0   U  0 0 0 eth0

```
That route should be set up automatically.  If it's not there, run the command
```
sudo ip route add 192.168.0.0/24 dev eth0
```
then try pinging 192.168.0.1 again.  Any better?

The e1000e driver is the correct one for your hardware.  I read the entry at Intel too quickly and didn't see the trailing "e", so that's not the problem.

I've not seen that "ptp" module before. A quick check says it implements the [Precision Time Protocol](http://linuxptp.sourceforge.net/).  Is that something you're running purposely?  Maybe it's affecting the packet timestamps in a way incompatible with your router.  I don't have a machine that uses the e1000e driver.  The machines I own with Intel adapters are using the e1000 driver and don't have an associated ptp module like yours does.  If this is the source of the problem, I'm afraid I may not be of any further help.

You could try to solve the problem by brute force with
```
sudo rmmod ptp
```
but I don't know what other processes that might break.

---

### Post by adam164 on 2015-10-02
Here are the results
```

adam@Darla:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
adam@Darla:~$ sudo ip route add 192.168.0.0/24 dev eth0
[sudo] password for adam: 
adam@Darla:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
adam@Darla:~$ ping 192.168.0.1
connect: Network is unreachable
adam@Darla:~$ sudo rmmod ptp
rmmod: ERROR: Module ptp is in use by: e1000e

```

The route wasn't there so I added it then tried pinging, no luck. ptp seems to also be stubborn. I tried turning off networking so I could try deleting it, but it didn't work. As a regular windows user my knowledge ended right about there.

When I was first setting up the dual boot system, my internet connected automatically no problem on ubuntu. But as soon as I finished the process and booted into windows then back into ubuntu, these problems arose. That's why i think it was attributable to the dual booting in some way. I read earlier that windows 8 had an issue with dual booting where it used "dynamic start" or something that made boot times much faster, but left windows in partial control of the kernel. Could it somehow be grabbing onto the networking?

---

### Post by SeijiSensei on 2015-10-02
I don't know.  I haven't used any versions of Windows beyond Win7.  But if Windows 8 leaves some piece of itself behind ever after a reboot, then that certainly could be a problem.  Can you disable that "dynamic start" option in Windows?  What if you turn off power to the machine before booting again?

Can you boot Ubuntu from the installation media and connect to the network after choosing "Try Ubuntu?"

The result for the ptp module shows it is using the e1000e driver; as I said that isn't the case for the older e1000 driver for Intel gigabit adapters.

---

### Post by adam164 on 2015-10-02
I disabled the startup, no luck. Turned off machine and then booted into ubuntu, no luck. Tried the same with the try ubuntu option from my usb stick, no luck.

Though I did find [this guy]("https://bbs.archlinux.org/viewtopic.php?id=191981") who seems to have had the same issue, never popped up in any of my googling until now. I'll go through his steps and report back, although he's dealing with Windows 7, not 10.

Back with results. I find that fully shutting down and unplugging my computer for a few seconds before booting into ubuntu "solves" this. Which gives credit to the theory that somehow windows is wresting control of the driver/kernel somehow. I've tried going about disabling wake on lan like the guy suggests, but so far haven't had any luck.

---

