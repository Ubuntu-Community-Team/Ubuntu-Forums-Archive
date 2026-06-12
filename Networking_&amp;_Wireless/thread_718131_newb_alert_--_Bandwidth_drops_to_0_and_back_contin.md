---
title: "newb alert -- Bandwidth drops to 0 and back continuously"
date: 2008-03-07
forum: Networking &amp; Wireless
---

### Post by Alajjana on 2008-03-07
On all of the several bandwidth monitors that i have used the bandwidth drops to zero and back to normal every update. (updates occur every second) Also when i say zero i mean zero, not close too or almost ... zero. I uploaded a picture that shows it pretty clearly.

ie 32k,0k,34k,0k,29k,0k, ... etc. 

I am using Ubuntu 7.10 (gutsy) on an Intel dg33fb with d2c quad q6600. 

I should also mention that this didnt happen under windows ... but as soon as i figure out how to dual-boot my system i will be re-installing windows and will test it again.

---

### Post by SpaceTeddy on 2008-03-08
this probably means that your programm is grabing the information too quick or too slowly, resulting in the drops. since there is either no new data available or, in the case of too slow, it show you timeslots where it did not check, resulting in 0 mesaure points. 

have a look with the programm "iptraf" to confirm the drops...

---

### Post by Alajjana on 2008-03-08
I took a look at eth0 with iptraf and everything seemed perfect. No errors or dropped packets and the xfer rates were rock solid.

But the problem is not just one program, but every traffic graphing program i have tried so far. rell monitor, screenlets netmon, and even the system monitor that comes with ubuntu (and others).

Could there be something between the two (iptraf and system monitor et al) where iptraf is being updated in fractions of a second and this 'something' is only being updated every two seconds ... leaving a zero result when system monitor asks for more data?

When i tell system monitor to update every 2 seconds the graphs look fairly normal, when i change the updates to 0.25 seconds the other graphs in system monitor are fine but the network history only has data once every 4 updates showing about 4x higher xfer rate.


very strange.

---

### Post by Alajjana on 2008-03-09
After some walking away and poking around and walking away and poking around ... i installed the gnome applet 'Network connection". This is what is going on...

In perfect sync with all my graphs Network connection applet shows my eth0 going idle for 1 second, collecting data for 1 second, going idle 1 second, collecting data for 1 second, etc.. 

I checked iptraf again to compare and it is updating all its data continuously, many times a second without any pause or glitch.

ifconfig shows no loss of packets or errors.

:(

---

### Post by Alajjana on 2008-03-11
Anybody???

---

### Post by SpaceTeddy on 2008-03-11
sorry, forgot to answer - but i am also at loss with this. I personally would just ignore it, since it is a minor bug/flaw which does not affect the workings of the system.

If anybody else has an idea... i don't have any anymore :(

---

### Post by Alajjana on 2008-03-13
You are right, this is hardly a serious problem ... thanks for trying!

---

### Post by Alajjana on 2008-03-13
[http://ubuntuforums.org/showthread.php?t=473966](http://ubuntuforums.org/showthread.php?t=473966)
[http://ubuntuforums.org/showthread.php?p=4507576](http://ubuntuforums.org/showthread.php?p=4507576)

(This is more for my reference ... )

These two people are having the exact same problem that i am. They are both  using the Intel Gigabit NIC that i am but on a different mother boards... davidallan is using the exact same NIC.

davidallan :
description: Ethernet interface
product: 82566DC Gigabit Network Connection
vendor: Intel Corporation
physical id: 19
bus info: pci@0000:00:19.0
logical name: eth0
version: 02
serial: 00:19:d1:8a:e3:f4
size: 100MB/s
capacity: 1GB/s
width: 32 bits
clock: 33MHz
capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI duplex=full firmware=1.1-0 ip=192.168.0.4 latency=0 link=yes module=e1000 multicast=yes port=twisted pair speed=100MB/s

vanhoudn:
Intel Corporation 82541PI Gigabit Ethernet Controller 


Here is a message about compiling a new driver( old):
[http://ubuntuforums.org/showpost.php?p=741635&postcount=16](http://ubuntuforums.org/showpost.php?p=741635&postcount=16)
[http://sourceforge.net/projects/e1000](http://sourceforge.net/projects/e1000)

[ 1801956 ] Link flapping on 82566DC(relivence?):
[http://sourceforge.net/tracker/index.php?func=detail&aid=1801956&group_id=42302&atid=447449](http://sourceforge.net/tracker/index.php?func=detail&aid=1801956&group_id=42302&atid=447449)

'sall for now.

---

### Post by Alajjana on 2008-03-29
Download the latest drivers from intel. Google search e1000 intel driver.

Followed the instructions found on this message board about installing the drivers. There are a couple but there is one message devoted to updating the driver follow it. simple and works.

REBOOT after install.

Throughput jumped from .5Mb/s to 8Mb/s+ (havent tested the top end.)

---

### Post by drsox1899 on 2008-05-21
> **Alajjana said:**
> Download the latest drivers from intel. Google search e1000 intel driver.

Followed the instructions found on this message board about installing the drivers. There are a couple but there is one message devoted to updating the driver follow it. simple and works.

REBOOT after install.

Throughput jumped from .5Mb/s to 8Mb/s+ (havent tested the top end.)

I have exactly this with a network of Intel Pro/1000 MT cards. Pulsing and low(ish) throughput.  I get 8MBPS in Linux vs 25MBPS in WinXp - BOO!

The SourceForge website lists the latest driver as : e1000-7.6.15.5.  
Is this the one I should be using ?  
How do I check what driver the U 7.10 IS using ?  
How do I stop them autonegotiating back to 100mbps ?
Exactly where and how do I recompile this driver - if I have to ?

Thanx

---

### Post by Alajjana on 2008-05-21
> **drsox1899 said:**
> I have exactly this with a network of Intel Pro/1000 MT cards. Pulsing and low(ish) throughput.  I get 8MBPS in Linux vs 25MBPS in WinXp - BOO!

The SourceForge website lists the latest driver as : e1000-7.6.15.5.  
Is this the one I should be using ?  
How do I check what driver the U 7.10 IS using ?  
How do I stop them autonegotiating back to 100mbps ?
Exactly where and how do I recompile this driver - if I have to ?

Thanx

First. I have no idea.
Second. You can use dmesg to see what drivers are load. Its a long list and 
dmesg | more
will probably help.
Find out of you are using e1000 or e1000e. Download it and follow the instructions. Although i thought e1000 was at 8.0. e1000e was 0.2.95...

good luck..

---

### Post by drsox1899 on 2008-05-22
> **Alajjana said:**
> First. I have no idea.
Second. You can use dmesg to see what drivers are load. Its a long list and 
dmesg | more
will probably help.
Find out of you are using e1000 or e1000e. Download it and follow the instructions. Although i thought e1000 was at 8.0. e1000e was 0.2.95...

good luck..

Thanks.

I must have missed this but is the one you used e1000 or e1000e ?

dmesg told me that I have Intel Pro/1000 V 7.3.20-k2-NAPI and I know that I'm using the e1000 driver.

I have answered my own question - e1000e is for PCIe - not relevant for me.

---

### Post by Alajjana on 2008-05-25
> **drsox1899 said:**
> Thanks.

I must have missed this but is the one you used e1000 or e1000e ?

dmesg told me that I have Intel Pro/1000 V 7.3.20-k2-NAPI and I know that I'm using the e1000 driver.

I have answered my own question - e1000e is for PCIe - not relevant for me.

In 7.1 i used e1000. For some reason when i upgraded to 8.04 it switched to e1000e automatically. caused a great deal of confusion until i figured it out.

e1000 stable  	8.0.1  	April 16, 2008:
[http://sourceforge.net/project/showfiles.php?group_id=42302](http://sourceforge.net/project/showfiles.php?group_id=42302)

---

