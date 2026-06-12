---
title: "Samba - Upload speed to share very hectic"
date: 2017-04-18
forum: Networking &amp; Wireless
---

### Post by rickyb667 on 2017-04-18
Hi there!

I am experiencing a strange behaviour of samba share, which might have something to do with cache, but i got stuck in debugging.
This happens when i am uploading large files (2+ GB) to the samba share from a windows machine.

My NIC is:

[    2.020064] e1000 0000:02:00.0: eth0: (PCI:66MHz:32-bit) 00:0c:29:dc:38:7f
[    2.020077] e1000 0000:02:00.0: eth0: Intel(R) PRO/1000 Network Connection
[   27.176169] e1000: eth0 changing MTU from 1500 to 9000
[   27.229813] e1000: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None

And my current smb.conf looks like:

[global]
  browseable = yes
  case sensitive = true
  deadtime = 15
  enable core files = yes
  fake oplocks = yes
  guest account = root
  large readwrite = yes
  max connections = 65535
  max open files = 65535
  max protocol = SMB2
  name resolve order = lmhosts bcast host
  netbios name = %h
  passdb backend = smbpasswd
  printable = no
  printcap name = /dev/null
  read raw = yes
  security = share
  server string = Home Store
  smb encrypt = disabled
  smb ports = 445
  socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=65536 SO_SNDBUF=65536 SO_KEEPALIVE
  strict sync = no
  sync always = no
  use sendfile = Yes
  wide links = yes
  workgroup = WORKGROUP
  write cache size = 65535
  write raw = yes
  writeable = yes


[terrastore]
    comment = Terra Store
    path = /terrastore
    browseable = Yes
    read only = No
    writable = yes
    force create mode = 0777
    force directory mode = 0777
    guest ok = yes
    public = yes



This is what the network receive rate looks like for the VM which runs the samba share. It shifts between 0 and 10MBps like a roller coaster ride:

[ATTACH=CONFIG]274613[/ATTACH]

I have a gigabit network for this with proper NICs in all PCs and machines and proper switches, routers, etc.
Still can't figure out what could be the problem. Why it is not climbing above 10MBps and why is acting so strange.
Been searching for solutions and doing try and error for a long time now.
I am thinking about caching issues, but don't know where to start with that.

Please if you have any suggestions or advice or you find problems in my config, don't hesitate to enlighten me!

Thank you for your great help!

---

### Post by TheFu on 2017-04-18
guest account = root

!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!  Allowing a guest to have root to a server **is** a terrible idea.

**testparm** output would be appreciated. I've learned to avoid trusting text files when I can get the program to show what it sees instead.
I'd begin by verifying all file transfer protocol speeds - to narrow down if this is a system issue or just a samba issue.  If you use **sftp**, what is the transfer rate?  Try from the same and different clients. What does **iperf** show?

---

### Post by Morbius1 on 2017-04-18
You also might want to tell people what version of samba you are using.

The reason I ask is because you have an option:
> security = share
On a fairly modern version of samba ( >= 4.3.x ) having that option set that way would stop smbd from running so your samba server would be inoperable.

---

### Post by rickyb667 on 2017-04-18
> **TheFu said:**
> guest account = root

!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! Allowing a guest to have root to a server **is** a terrible idea.

**testparm** output would be appreciated. I've learned to avoid trusting text files when I can get the program to show what it sees instead.
I'd begin by verifying all file transfer protocol speeds - to narrow down if this is a system issue or just a samba issue. If you use **sftp**, what is the transfer rate? Try from the same and different clients. What does **iperf** show?

Yes, thank you for the headsup. To be honest this is a home setup for me and me only. Noone else is using this and i am behind a firewall.
But thanks again for pointing this out!

testparm:


Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[terrastore]"
WARNING: The security=share option is deprecated
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions


[global]
        server string = Home Store
        security = SHARE
        passdb backend = smbpasswd
        guest account = root
        smb ports = 445
        max protocol = SMB2
        name resolve order = lmhosts bcast host
        deadtime = 15
        max open files = 65535
        socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=65536 SO_SNDBUF=65536 SO_KEEPALIVE
        printcap name = /dev/null
        idmap config * : backend = tdb
        read only = No
        smb encrypt = No
        max connections = 65535
        use sendfile = Yes
        write cache size = 65535
        case sensitive = Yes
        fake oplocks = Yes
        wide links = Yes


[terrastore]
        comment = Terra Store
        path = /terrastore
        force create mode = 0777
        force directory mode = 0777
        guest ok = Yes


SFTP from the same Windows computer with 5+ GB file did start up with 157 Mbps and then fell back to arouond 60 Mbps constant speed

---

### Post by rickyb667 on 2017-04-18
I am actually running Version 3.6.6

---

### Post by rickyb667 on 2017-04-18
Okay, nevermind this. I have narrowed the problem down to a probable misconfiguration in esxi with the virtual hard disks.
Tha transfer rate between the mounted disks is slow and probably nothing to do with samba.
SFTP transfer went to the OS' disk's home directory, and that was fast enough. But when i tried to copy that file from /home into the directory which samba is using (/terrastore) and which is a separate mounted disk, it slowed down again.
I guess i will have to find solutions in a different topic.

---

### Post by TheFu on 2017-04-18
Thank you for taking the time to provide the root issue.  Plus, since there wasn't any mention of any hypervisor, we'd never have come up with that.

Yes, I suspect ESXi performance issues would be best solved by VMware guys who are familiar with the current tools. There are many subtle options available, outside the vsphere GUI, BTW.

Lots of us here do virtualization, though I dropped all VMware products in 2011, so my knowledge of any VMware-anything is dated and fading. If you are interested in switching, just drop a question over in the virtualization subforum. I had to try. ;)

60 Mbps isn't bad for some slower disks.  I never expect go get more than about 80Mbps on my non-enterprise disk hardware.  Transfers are usually fast to start, then slow as the disk buffers fill. At that point, regardless of OS, the spinning disk performance will be the limitation.  You can watch that happen with **free -hm**.  If you want to move more data, faster, buy more RAM, allocate it into the VM, but don't use it.  I have a video transcoding machine that has 8G just for that reason. Because it is heavy CPU, it isn't a VM, but pretty much every other system here **is** a VM, including my desktop (that I'm using right now). The transcoding box only needs ... ```

$ free -hm
             total       used       free     shared    buffers     cached
Mem:          7.8G       2.0G       5.8G       1.6M       217M       1.2G
-/+ buffers/cache:       654M       7.1G
Swap:         6.4G       228M       6.2G

```
Just look at how little swap and RAM is being used. Moving files to that machine is basically as fast as the network can do it.

---

### Post by rickyb667 on 2017-04-18
> **TheFu said:**
> Thank you for taking the time to provide the root issue.  Plus, since there wasn't any mention of any hypervisor, we'd never have come up with that.

Yes, I suspect ESXi performance issues would be best solved by VMware guys who are familiar with the current tools. There are many subtle options available, outside the vsphere GUI, BTW.

Lots of us here do virtualization, though I dropped all VMware products in 2011, so my knowledge of any VMware-anything is dated and fading. If you are interested in switching, just drop a question over in the virtualization subforum. I had to try. ;)

60 Mbps isn't bad for some slower disks.  I never expect go get more than about 80Mbps on my non-enterprise disk hardware.  Transfers are usually fast to start, then slow as the disk buffers fill. At that point, regardless of OS, the spinning disk performance will be the limitation.  You can watch that happen with **free -hm**.  If you want to move more data, faster, buy more RAM, allocate it into the VM, but don't use it.  I have a video transcoding machine that has 8G just for that reason. Because it is heavy CPU, it isn't a VM, but pretty much every other system here **is** a VM, including my desktop (that I'm using right now). The transcoding box only needs ... ```

$ free -hm
             total       used       free     shared    buffers     cached
Mem:          7.8G       2.0G       5.8G       1.6M       217M       1.2G
-/+ buffers/cache:       654M       7.1G
Swap:         6.4G       228M       6.2G

```
Just look at how little swap and RAM is being used. Moving files to that machine is basically as fast as the network can do it.

Thank you for the info, i will continue my research!

And thanks for the help! By myself i wouldn't have tried SFTP which lead to my current conclusions. I needed that external viewpoint. ;)

---

### Post by TheFu on 2017-04-18
> **rickyb667 said:**
> Thank you for the info, i will continue my research!

And thanks for the help! By myself i wouldn't have tried SFTP which lead to my current conclusions. I needed that external viewpoint. ;)

Just trying to help here.  

Feel like rambling ... The general rules for Linux troubleshooting are:
[LIST=1]
[*]benchmark the issue/performance before making any changes; be careful about MBps and Mbps differences. Be consistent.
[*]check the log files (system and application)
[*]turn up the debug output, check the log files again
[*]If you are using a GUI, run the program from a shell and see what output gets generated. Could be helpful.
[*]if those don't help, simplify the problem to find the root issue
[/LIST]

For HW related issues, if it used to work, check the power, all cables, and swap components (1 at a time), until the issue is isolated. 
For HW related issues, if it never worked, check the power, all cables, and swap components to isolate the issue. Also verify that the correct driver and driver options are being used.

Sometimes there isn't a solution. I have a 2010 system with a USB3 addon card. I've never gotten great performance from any USB3 devices connected to it.  There are dmesg entries about it all the time for storage stuff.
```
[888187.637323] usb 4-2.1.2: reset SuperSpeed USB device number 5 using xhci_hcd
[888187.653089] usb 4-2.1.2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[888187.653474] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880423fdd300
[888187.653481] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880423fdd340

```
I googled every error, which lead to many different "solutions" according to others.  Tried multiple kernel options. Multiple USB options. Blacklisting modules, different module options, etc. Different USB3 addon cards, different ports, different storage devices ... they all perform poorly and show similar issues.  
Last year, I was mad and wanted to get to the bottom or replace the motherboard.  I have newer, much, much, cheaper systems which handle USB3 storage great - better than great - they are amazing.  But the CPUs aren't as fast.  Ok, so I pulled down the motherboard architecture diagrams from the vendor's site, MSI.  Since I've worked as a technical architect for decades and have training in reading those things across all the major server vendors, I was prepared.  There was a reason my USB3 performance sucked.  The PCIe slots I'm using is slow. They don't support anywhere near the type of throughput a USB3 device does. Looking at the diagram, I couldn't move it into a different slot to use a different backplane - it is a desktop motherboard - only one backplane available. Ah, how I miss servers (but not their prices).  Then I was on the hunt to replace the system for about $200. That's my normal upgrade for a 5+ yr old system.  Found a used CPU that would make the system 4-5x faster with a $90 used Xeon CPU.  There was hope.  Then I started looking for a motherboard that would work, didn't suck, and would fit into my existing case while using existing RAM and support my other PCIe cards.  There were onyl 2 motherboards that fit my needs, but both were extremely limited supply, had mostly 1-star reviews and were $200 over my price range.  New CPUs aren't to the level of providing enough performance for the $$$ yet.  The problem machine is an i5-750, so not exactly slow.  The motherboards that support that CPU are limited too - few, if any, have good USB3 support.

Which explains why I could post those errors above so easily. I'm still using the same box and it is still spewing errors for the USB devices. ;(

Sorry for rambling. Better than doing what I should be doing - swapping out our WAN router with a new one that can be patched weekly.

---

