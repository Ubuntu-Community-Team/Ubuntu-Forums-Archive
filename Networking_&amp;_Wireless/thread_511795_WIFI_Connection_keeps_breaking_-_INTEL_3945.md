---
title: "WIFI Connection keeps breaking - INTEL 3945"
date: 2007-07-28
forum: Networking &amp; Wireless
---

### Post by hindukush on 2007-07-28
Hi Guys,
Ive read so many topics and searched around the net but i cant seem to fix this problem. Hope someone can help me please........
I have a Dell XPS M1210 Laptop which has an Interl Wireless 3945 card. 
The problems i face are as follows:
1. Sometimes the wifi green light on the laptop does not turn on at all and therefore am not able to connect to my wireless network.
2. Sometimes the light does turn on and then just dissapears in between and therefore the internet connection is broken.
3. Sometimes even when the  wifi light is on it not able to start th einternet connection until i do a swith off/on on my DSL router.

How can i fix this problem...... please help
Thnaks guys i would appreciate any help........

---

### Post by hindukush on 2007-07-28
cmon guys pleaseeeeeeeeeeeeeee
i need help!!!!!!!!!!!

---

### Post by hindukush on 2007-07-28
oh cmonnnnnnnnnnnnnnnnnnnnnnnnnnn
pleaseeeeeeee

---

### Post by hindukush on 2007-07-29
nobody has had this sort of problem?????????/
cmon guys i know u can help...............

---

### Post by hindukush on 2007-07-29
cmonnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnn

---

### Post by lindau on 2007-07-29
Tell us what you have done so far, 
How did you set your wireless  connection up):P

---

### Post by noob12 on 2007-07-29
What driver are you using with the 3945?  If you are using the ipw3945 drivers, is the regulatory daemon ipw3945d starting properly?  

Can you post the output of these commands?

```
lshw -C network
```

```
ps -ef | grep ipw3945d
```

```
iwconfig
```

from which we'll see what kind of signal strengths your driver thinks it is seeing

and

```
iwlist *yourwirelessinterface* scan
```

Replace *yourwirelessinterface* by the name that shows up in the left-hand column of **iwconfig** next to your wireless interface.


Regarding the problems with the device not being on at boot, can you check your BIOS settings.  Check that the setting is Enabled (and under Application control if that setting is there).

---

### Post by hindukush on 2007-07-30
Thanks for the attention! 
Yes, i am using the 3945 drivers for linux. 
the output of the commands you asked for are as follows:


ag@ubuntu:~$ lshw -C network 
WARNING: you should run this program as super-user. 
  *-network                
       description: Ethernet interface 
       product: PRO/Wireless 3945ABG Network Connection 
       vendor: Intel Corporation 
       physical id: 0 
       bus info: pci@0c:00.0 
       logical name: eth1 
       version: 02 
       serial: 00:18:de:94:6f:e8 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0 () latency=0 multicast=yes 
       resources: iomemory:efdff000-efdfffff irq:17 
  *-network 
       description: Ethernet interface 
       product: BCM4401-B0 100Base-TX 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@03:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:15:c5:56:b8:d2 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=b44 driverversion=1.01 latency=64 multicast=yes 
       resources: iomemory:ef9fe000-ef9fffff irq:17 
Code:
ps -ef | grep ipw3945d
ag@ubuntu:~$ ps -ef | grep ipw3945d 
root      4639     1  0 11:22 ?        00:00:00 /sbin/ipw3945d-2.6.20-16-generic --quiet 
root      5996     1  0 11:22 ?        00:00:00 /sbin/ipw3945d --quiet --pid-file=/var/run/ipw3945d/ipw3945d.pid 
ag        7056  6899  0 11:28 pts/0    00:00:00 grep ipw3945d 
Code:
iwconfig
ag@ubuntu:~$ iwconfig 
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
eth1      no wireless extensions. 
from which we'll see what kind of signal strengths your driver thinks it is seeing

and
Code:
iwlist yourwirelessinterface scan
[B]
what should i enter here??/? the output of iwconfig is above.[/B]


Thanks, and awaiting your reply!

---

### Post by noob12 on 2007-07-30
OK.  You seem to have the right ipw3945 driver associated.  The wireless is eth1.  

However, I'm seeing two odd things already. I'm expecting that eth1 should show wireless extensions and information in **iwconfig**.  

Also, I don't think it is normal to have two regulatory daemon processes, but I have to research that more.


Was this done at a time when wireless was not working at all?

Can you please try the following?

[LIST=1]
[*]Check that you have wireless Enabled unconditionally in the BIOS settings.  Then
show us the output of the following
[*]```
dmesg | egrep '(ipw|eth1)'
```
[*]```
modprobe ipw3945
```
[*]```
iwlist scan
```
[/LIST]

---

### Post by hindukush on 2007-07-30
Yes, this was done at a time when the green light of wifi was not on. It just does not turn on anymore at all when i load Ubuntu. My system is dual boot with windows xp. but wifi works fine when i start windows xp. 
the bios setting seem fine aswell. Wifi on ubuntu used to work ok earlier but just suddenly one day the green light stopped coming on. i wonder why??
any ways i ran the following commands and here are the outputs:

ag@ubuntu:~$ dmesg | egrep '(ipw|eth1)' 
[   20.268000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp 
[   20.268000] ipw3945: Copyright(c) 2003-2006 Intel Corporation 
[   20.272000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection 
[   22.176000] ipw3945: Detected geography ABG (13 802.11bg channels, 4 802.11a channels) 
[   37.720000] eth1: no IPv6 routers present 
[   53.504000] ipw3945: Detected geography ABG (13 802.11bg channels, 4 802.11a channels) 
[   76.448000] ipw3945: Radio Frequency Kill Switch is On: 
[  140.548000] ipw3945: Detected geography ABG (13 802.11bg channels, 4 802.11a channels) 
[  200.972000] ipw3945: Detected geography ABG (13 802.11bg channels, 4 802.11a channels) 
[  261.288000] ipw3945: Microcode SW error detected.  Restarting. 
[  261.288000] ipw3945: XXXL we have skipped command 
[  261.500000] ipw3945: Detected geography ABG (13 802.11bg channels, 4 802.11a channels) 
[  261.500000] ipw3945: Can't stop Rx DMA. 
[  262.084000] ipw3945: Microcode SW error detected.  Restarting. 
[  263.288000] ipw3945: Can't stop Rx DMA. 
[  263.568000] ipw3945: Detected geography ABG (13 802.11bg channels, 4 802.11a channels) 
[  324.112000] ipw3945: Detected geography ABG (13 802.11bg channels, 4 802.11a channels) 

ag@ubuntu:~$ modprobe ipw3945 
ag@ubuntu:~$  

The above command does not give any output.


ag@ubuntu:~$ iwlist scan 
lo        Interface doesn't support scanning. 
 
eth0      Interface doesn't support scanning. 
 
eth1      Interface doesn't support scanning. 
 


Awaiting your reply!
Thanks

---

### Post by noob12 on 2007-07-30
> 
[ 76.448000] ipw3945: Radio Frequency Kill Switch is On:


This means you have the wireless radio disabled.  This is often a slider switch on the side
of the laptop.  It is sometimes a FN key.  If you are not sure, check your user manual.
Please do take a bit of time to check your BIOS settings that wireless is Enabled (not Restore or
something conditional) on startup, even if booting in Windows works.

> 
[ 261.288000] ipw3945: Microcode SW error detected. Restarting.
[ 261.288000] ipw3945: XXXL we have skipped command
[ 261.500000] ipw3945: Detected geography ABG (13 802.11bg channels, 4 802.11a channels)
[ 261.500000] ipw3945: Can't stop Rx DMA.
[ 262.084000] ipw3945: Microcode SW error detected. Restarting.
[ 263.288000] ipw3945: Can't stop Rx DMA. 


Also a problem.  Can you do
> 
aptitude show firmware-3945


The rest is failing due to these problems.

---

### Post by hindukush on 2007-07-31
I know where the switch is located on my laptop but it is not turned to off. It is definitely on! Because when i boot windows without doing anything to the swtich the green wifi light turns on and everything works fine.
I also checked the BIOS settings and wireless is set to enabled.
Also, when i select to load Ubuntu from the GRUB menu and Ubuntu starts to load and the progress bar is shown. The wifi light turns on during this time. But when the screen for the username comes up its gone again. Very weird...............

ag@ubuntu:~$ aptitude show firmware-3945  
E: Unable to locate package firmware-3945

---

### Post by noob12 on 2007-07-31
OK.  Sorry.  It appears there's an issue with 7.04 when it checks the power state on some wireless devices.

Can you please show the output of each of the following
```

ls -l /sys/class/net/eth1/device/rf_kill
ls -l /sys/class/net/eth1/device/power/state

```
and
```

cat /sys/class/net/eth1/device/rf_kill
cat /sys/class/net/eth1/device/power/state

```

---

### Post by hindukush on 2007-07-31
ag@ubuntu:~$ ls -l /sys/class/net/eth1/device/rf_kill 
-rw-r--r-- 1 root root 4096 2007-07-31 12:32 /sys/class/net/eth1/device/rf_kill 

ag@ubuntu:~$ ls -l /sys/class/net/eth1/device/power/state 
-rw-r--r-- 1 root root 4096 2007-07-31 12:33 /sys/class/net/eth1/device/power/state 

ag@ubuntu:~$ cat /sys/class/net/eth1/device/rf_kill 
0 

ag@ubuntu:~$ cat /sys/class/net/eth1/device/power/state 
0

---

### Post by noob12 on 2007-07-31
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/108090](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/108090) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				These values look ok (not rf_killed or disabled).

There are a couple of bugs on launchpad and on the ipw3945 bug site about the microcode errors similar to the ones seen in dmesg. No resolution yet.

It would also be helpful if you posted
```

find /lib/firmware/ -name "ipw3945*"

```

---

### Post by hindukush on 2007-07-31
ag@ubuntu:~$ find /lib/firmware/ -name "ipw3945*" 
/lib/firmware/2.6.20-16-generic/ipw3945.ucode 
/lib/firmware/2.6.20-15-generic/ipw3945.ucode

---

### Post by noob12 on 2007-07-31
There are reports of this problem in the driver and the current version of the microcode.  

[http://www.bughost.org/bugzilla/show_bug.cgi?id=1085#c56](http://www.bughost.org/bugzilla/show_bug.cgi?id=1085#c56)  (see comment 56)
[http://www.bughost.org/bugzilla/show_bug.cgi?id=1271](http://www.bughost.org/bugzilla/show_bug.cgi?id=1271)

You might want to follow up there with your information.  They will probably ask you to load the driver with debug flags to get more logging.  This will help them fix it in a future release.

Whenever this problem occurs on your box, the driver apparently doesn't end up initializing successfully and you see no wireless extensions on your interface. 

On the other hand, there are several people who report using the driver successfully on the Dell XPS M1210; both AMD and Intel-based ones.  I don't know why you are affected.  

These are both stabs and I'm not sure they will work for you:
[LIST]
[*]If there are any BIOS updates available from Dell for your laptop, you might try to install them; this is probably easiest by booting Windows, and downloading the update from Dell and doing  to do the BIOS upgrade.

[*]If that doesn't pan out, you can also try to use the Dell-supplied Windows drivers together with ndiswrapper, but I don't see evidence of a lot of people doing this, and I'm not sure it will be successful.
[/LIST]

Someone else on the forum might have better suggestions or more to add.

---

