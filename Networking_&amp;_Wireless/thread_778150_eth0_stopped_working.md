---
title: "eth0 stopped working"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by wagb278 on 2008-05-01
My eth0 seems to have stopped working and I need help to determine if I have a hardware problem or software configuration issue.  The computer is a week old and Ubuntu 8.04 installed like a dream and all was well until I booted today. I booted twice thinking something just didn't start correctly. 

I have an Intel DP35DP motherboard with one on-board Ethernet port.  But, like I said all (including the network) has been working.  Today the browser couldn't connect so I tried to pinged the gateway and was told the Network is not reachable.  

So I tried sudo /etc/init.d/networking restart and receive failure notices like:
   eth0: ERROR while getting interface flags: no such device
   < -- other lines reporting errors -- >

Checked my /etc/network/interfaces file which is untouched (not modified) from when the interface was working. I have eth0 as a static IP address and "auto eth0" is the last line in the file.

I just happen to have saved the output of a working ifconfig (three days ago) which is: 

eth0      Link encap:Ethernet  HWaddr 00:1c:c0:35:03:e6  
          inet addr:192.168.0.205  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:c0ff:fe35:3e6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:699887 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1183117 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:220339244 (210.1 MB)  TX bytes:1549147136 (1.4 GB)
          Memory:e3200000-e3220000

Two other computers on this LAN are working just fine.  So I know the LAN is operational.

/sbin/ifconfig eth0 only gives info on the loopback (127.0.0.1) and nothing on my static IP.  I guess this is just confirmiing the eth0 is not running - but why not?

Ping to 127.0.0.1 works, but is this just a software loopback?  Or is it telling me something else?

So what can I do to determine if I have a malfunctioning Ethernet  port on this motherboard or some other cause?

Any - all ideas welcome.  Thanks

**SOLVED** - I think because of installing Intel e1000 driver for the Ethernet controller.  but I cannot be sure just what was the critical action that made the problem go away.

**NOT SOLVED** - The problem is back, Sat 10 May 2008. 
Appears to be the same symptoms.
  ping 192.168.0.1 returns - Network is unreachable 
  The 'e1000' module not in output of lsmod | grep 'e1000'
  Output of lspci shows Ethernet Controller as an unknown Intel device

  Performed sudo modprobe e1000 - Installed driver, now shows in lsmod
  Perfomed sudo /etc/init.d/networking restart - No Good!

---

### Post by Aearenda on 2008-05-01
As you suspect, 127.0.0.1 is a loopback, it doesn't involve the network hardware.

Suggestions:
If you look through the output of ```
dmesg | more
``` is there anything useful about eth0, or by name about the network interface?

Does ```
lspci
``` list the network interface?

Has the BIOS lost its settings and disabled the interface?

Are there any lights on the socket, and if so, are they lit?

---

### Post by The Cog on 2008-05-02
Two indications that you don't have a hardware problem are the word RUNNING and the fact that you have many transmitted and received packets showing in ifconfig.

Can you ping your own address - 192.168.0.205? You should be able to.

Try running the command:
sudo tcpdump -i eth0 -n
for a while and see if you get packets captured.

I wonder if you have the same IP address as something else, and all the packets are going to the other machine instead?

---

### Post by wagb278 on 2008-05-02
I used the same LAN Port and Cable to connect a laptop, which connects to the Internet just fine - so my problem is within my new  computer.

I reviewed the log (dmesg | more) and there are no "eth0" entries.
There are a couple of entries relating to Network:
  net_namespace: 120 bytes
  audit: initializing netlink socket (disabled)
dmesg | grep 'TCP' reveals (in summary):
  Hash tables established and configured. & "TCP reno registered"

There are two lights on the RJ45. Reading from the mobo book they are telling me that the LAN Link is established* and that I have 100 Mb/s (not 10 and not 1000).
  * "Established" I think is bad wording by Intel. This indicator turns green when a cable is connected - even when the computer is turned off.  Unplugging the Ethernet cable makes this light go out. This indicator will blink to indicate traffic - It is on solid.

I inspected the BIOS and the LAN port is Enabled.

Results of "tcpdump" command reports:
  tcpdump: SIOCGIFHWADDR: No Such Device

Results of the "lspci" command shows that the Ethernet Controller is "Intel Unknown Device 0000 (rev 02).

The mobo book says the LAN controller is the Intel 82566DC.

This looks to me like I might need a driver - BUT THIS CONFIGURATION WORKED BEFORE - and I have changed nothing; I have not installed any third-party drivers.  Whatever came with Ubuntu 8.04 had worked.  

I will check Intel for Linux drivers, but I am reluctant to change drivers because this was working before.  I have even installed LAMP and had that working.

Any further suggestions?  Thanks Guys!

---

### Post by wagb278 on 2008-05-02
I found old Ubuntu forum threads (pre-version 8.04) suggesting I should install a driver from Intel.  I did so but with no change to my symptoms. The driver was dated 4 APR 2008 (just about a month old).  Following Intel's instructions I received no noticeable errors during the process. After updating the driver - before and after a reboot my symptoms are the same.

Running the lspci command still reports Ethernet controller as an unknown device 0000 (rev2).

To an extent, this is re-assuring that a different driver gives the same results (maybe it is the same driver delivered in Ubuntu 8.04) - which used to work. 

Just for grins - I tried the Ubuntu 8.04 LiveCD (64-bit) and I am getting the same results; lspci = unknown device, No pings to the LAN, and of course Firefox cannot connect.  I can't be sure - but I thought the LiveCD did connect to the Internet prior actually installing. I don't have another 64-bit machine to test with.  The Ubuntu 7.10 LiveCD (64-bit) will not run on this machine at all. Nor will the 7.10 LiveCD (32-bit).  I believe these don't run due to graphics card incompatibilities. 

So I can't think of anymore options to try.  

Anyone else have any ideas?

---

### Post by wagb278 on 2008-05-02
Forgot to mention - I looked in System-->Admin-->Hardware Drivers to see if the Ethernet driver e1000 I installed was reported.  It is not.  There are no proprietary drivers in use by the system.  Did I not install one of these?  Guess I am confused.

Maybe another clue is that I used to get a sound when I start and when shutdown, but that no longer happens too!  Could there be a connection here?  

I also noticed that I had to use "insmod" command to get 'e1000' module to show up in a lsmod output.  'modprobe' did not work.  After a reboot lsmod no longer shows 'e1000' module present. But regardless of the presence of the e1000 module, the network is not "reachable" and the Ethernet controller is not recognized. 

I went looking for a eth0 file and can't find one - it is not in /dev; where should such a file be located?

The recent changes that were made to this computer (that should have nothing to do with this problem) include configuring Evolution (email) and changes to my Samba configuration. Those changes were done a week ago and the network has been working since those were made.

---

### Post by Aearenda on 2008-05-02
The Cog: The RUNNING marker in ifconfig was from before it failed.

wagb278: I think it is a hardware fault. It's not an e1000 - that's a gigabit NIC, but the 82556 is only 100Mbits as far as I can see. CORRECTION: I misread the number - it's 82566, which IS a gigabit interface. But it will operate at 100Mbits if the other end of the cable is incapable of going faster.

The next thing I would try is allowing the BIOS to reconfigure the PCI settings. After that, assuming no change, since it is just a week old, I'd take it back to the shop and ask them to test it.

What does ```
cat /etc/udev/rules.d/70-persistent-net.rules
``` show?

Have there been any thunderstorms in your area? I have one PC with a mobo NIC that has failed after a power glitch caused by a lightning strike. The net switch was blown too. The rest of the PC works fine. I worked around it by adding a separate NIC.

BTW, the Intel drivers are not 'proprietary' in the same sense as NVIDIA closed-source ones are.
Drivers loded manually don't stay loaded over a reboot unless added to the list in /etc/modules. But I don't think you need to do this.
No sound all of a sudden reinforces my suspicion about the hardware being faulty.

---

### Post by wagb278 on 2008-05-03
PROBLEM GONE

When I booted today the LAN port is working. Not sure if the solution was the "e1000" driver - Hope so!

The 'lsmod' command shows e1000 in the list. This is the Driver for the Intel Ethernet controller.

Running the 'lspci -nn' command shows that the Ethernet controller is recognized as the Intel 82566DC-2.

I looked at /etc/udev/rules.d/70-persistent-net.rules and there is a valid entry for eth0.  I also checked the date on that file and it was the same date as when Ubuntu was first installed. So nothing recent was done to that file. 

Inspecting /etc/modules I see nothing relating to the LAN port. It includes only fuse, lp, rtc, sbp2 entries.

Where would I look in log files to see an action that relates to starting the LAN?  I would like to understand more if this happens again.  I looked in /var/log but there are so many files there I am confused.

Thanks for all your assistance with this.

---

### Post by Aearenda on 2008-05-03
Let's hope it stays that way! Maybe the e1000 driver in Hardy (which my pc uses too) isn't as up to date as the downloaded one.

You should see entries in dmesg for the LAN (just type ```
dmesg | more
```to see what goes in there) or use the System Log viewer to look at kern.log, or syslog, and also at daemon.log for Network Manager events.

---

### Post by wagb278 on 2008-05-10
Problem has returned.  Same symptoms.

I was using the system just fine - trying to configure Apache2 to serve up from a different document root from /var/www when I noticed I kept getting "Browser Offline" notices from Firefox (going to localhost).  So I ping the gateway and receive "network is unreachable". Darn! 

lspci says the ethernet Controller in "unknown"
lsmod | grep 'e1000' returns nothing
sudo modprobe e1000 installs Ok, lsmod verifies that
sudo /etc/init.d/networking restart - can't find eth0

Checked /etc/modules and the file is unchanged since installation of Ubuntu 8.04 (64-bit) and does _not_ contain e1000.  So I think e1000 does not need to be an external module (if that is the right terminology). 

I looked around in some of the log files but these are too cryptic for me to comprehend.

I need more help.  Please!

**UPDATE**: Started working again after a few hours.  I'm going to talk with the Hardware shop to see if I might have a cooling problem.

---

