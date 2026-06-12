---
title: "Can't connect 2 ubuntu PC's"
date: 2007-06-10
forum: Networking &amp; Wireless
---

### Post by shanerdaner on 2007-06-10
Hi I am running Feisty on 2 PC's the desktop is a HP With a 64 bit AMD and 1 GB of ram the desktop is a Compaq F500 laptop my router is a Dlink VWR from vonage.  I can't seemd to get these PC's to see each other.  Any idea how to get them to see each other?  Do I have to get Samba?  I have windows drives in NFTS hooked to the desktop but the machine is Ubuntu so it shouldn't matter.  Is it the router?  I am a little frustrated but i know with everyones help I can get it running!

---

### Post by conjur3r on 2007-06-10
The first thing to check is to make sure both computers have an IP address.  I am assuming your dlink router has DHCP and is issuing addresses to machines connected to the network.

On both machines, open up a terminal and enter:
# ifconfig

Paste the contents here.

---

### Post by Mr. C. on 2007-06-10
Please define "see each other".

MrC

---

### Post by shanerdaner on 2007-06-10
Mr, C I can't locate shared folders on the other machine.  That's what I mean.

---

### Post by Mr. C. on 2007-06-10
Before you have windows network shares working, you have to have a properly configured network.  conjur3r asked about your IP information; have you verified that basic TCP/IP networking is functional ?

MrC

---

### Post by shanerdaner on 2007-06-10
I will follow his instructions and post in the am

---

### Post by shanerdaner on 2007-06-11
> **conjur3r said:**
> The first thing to check is to make sure both computers have an IP address.  I am assuming your dlink router has DHCP and is issuing addresses to machines connected to the network.

On both machines, open up a terminal and enter:
# ifconfig

Paste the contents here.
Laptop
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1B:24:03:84:9D  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Base address:0xa000 

eth0:avah Link encap:Ethernet  HWaddr 00:1B:24:03:84:9D  
          inet addr:169.254.5.142  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:19 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2245 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2245 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:222216 (217.0 KiB)  TX bytes:222216 (217.0 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:1A:73:34:BB:28  
          inet addr:192.168.15.3  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:73ff:fe34:bb28/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:240419 errors:0 dropped:0 overruns:0 frame:0
          TX packets:247330 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:261592294 (249.4 MiB)  TX bytes:28127784 (26.8 MiB)
          Interrupt:21 Memory:b8000000-b8004000

---

### Post by shanerdaner on 2007-06-11
> **conjur3r said:**
> The first thing to check is to make sure both computers have an IP address.  I am assuming your dlink router has DHCP and is issuing addresses to machines connected to the network.

On both machines, open up a terminal and enter:
# ifconfig

Paste the contents here.

DESKTOP
 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:D4:D4:20:EA  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0x4000 

eth0:avah Link encap:Ethernet  HWaddr 00:13:D4:D4:20:EA  
          inet addr:169.254.9.74  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:21 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:284 errors:0 dropped:0 overruns:0 frame:0
          TX packets:284 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:26589 (25.9 KiB)  TX bytes:26589 (25.9 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:0F:B5:01:98:72  
          inet addr:192.168.15.6  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b5ff:fe01:9872/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:550118 errors:0 dropped:0 overruns:0 frame:0
          TX packets:535396 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:790093572 (753.4 MiB)  TX bytes:49097576 (46.8 MiB)

wmaster0  Link encap:UNSPEC  HWaddr 00-0F-B5-01-98-72-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by Mr. C. on 2007-06-11
Seems ok.

Ensure each machine can ping the other, or connect to the internet.

I'll presume you already have the drive mounted and it is visible from your desktop machine.  If not, you need to mount the NTFS drive first.

Note:  writing to the NTFS file systems requires the ntfs-3g file system package.

Since you are mounting the drive directly into the file system, you do not need Samba.  You need to install/configure NFS.

Right click on the folder you want to share, and select Share folder.  This will ask if you want to install NFS and Samba (if not already installed).  Complete the wizard.

MrC

---

### Post by conjur3r on 2007-06-11
Basically we've just determined that your networking configuration is ok and they should have no problems talking to one another.

The problem should now be down to the desired sharing.  Essentially, before any other computer on the network can see a share, you must first configure the computer hosting the share.  Follow Mr C's instructions above to set it up and you should be able to navigate those shares in no time.

Just out of curiosity, do you have a ssh server on any of those computers?  If you have, then you can connect to the computers and navigate the files/folders using ssh.

---

### Post by shanerdaner on 2007-06-11
how do I ping the other machine and how can I share my entire Linux machines?  All i see is share folders not share drives.  TIA

---

### Post by merlinus on 2007-06-11
I use ssh on three ubuntu machines, and as long as I have a user account on each, I can read and write to any folders and files.

I use static IP addresses for each, and there are no problems with Internet access.

Very easy -- no files to tweak, no need for workarounds, etc.

-merlin

---

### Post by shanerdaner on 2007-06-12
> **conjur3r said:**
> Basically we've just determined that your networking configuration is ok and they should have no problems talking to one another.

The problem should now be down to the desired sharing.  Essentially, before any other computer on the network can see a share, you must first configure the computer hosting the share.  Follow Mr C's instructions above to set it up and you should be able to navigate those shares in no time.

Just out of curiosity, do you have a ssh server on any of those computers?  If you have, then you can connect to the computers and navigate the files/folders using ssh.

How do I seup SSH I wan to share these 2 machines and another laptop for a total of 2 laptops 1 amd desktop.  Thanks

---

### Post by Mr. C. on 2007-06-12
shanerdaner,

Let's get some terminology straight, as your loose language is making difficult to know exactly what you want to accomplish.

You don't share "machines".  A system's resources may be shared, such as a file system.

You don't share entire disks; file systems are divided into partitions, and each partition has a file system on it.  File systems are shared, or a sub-directory tree.

You likely have little reason to share the root file system to another system, and certainly not unless you understand what you are doing.

You do not need SSH to share a file system.  You use NFS to export and share ext3 (linux) file systems, and Samba to share resources (folders, printers) between *nix and Windows machines.

So what folder, directory, resource are you trying to share.  Be specific (type of file system, directory to share, etc.).

To ping another system, use the command line:
```

ping IP_or_hostname
```

where IP_or_hostname is the IP address of the remote system, or its hostname if you have properly configured you /etc/hosts file to know the remote systems by name.

SSH allows you to perform remote logins, and a bit more.

Please clarify what you are trying to do, and indicate to us that your network between the systems is functional.

MrC

---

### Post by shanerdaner on 2007-06-12
> **Mr. C. said:**
> shanerdaner,

Let's get some terminology straight, as your loose language is making difficult to know exactly what you want to accomplish.

You don't share "machines".  A system's resources may be shared, such as a file system.

You don't share entire disks; file systems are divided into partitions, and each partition has a file system on it.  File systems are shared, or a sub-directory tree.

You likely have little reason to share the root file system to another system, and certainly not unless you understand what you are doing.

You do not need SSH to share a file system.  You use NFS to export and share ext3 (linux) file systems, and Samba to share resources (folders, printers) between *nix and Windows machines.

So what folder, directory, resource are you trying to share.  Be specific (type of file system, directory to share, etc.).

To ping another system, use the command line:
```

ping IP_or_hostname
```

where IP_or_hostname is the IP address of the remote system, or its hostname if you have properly configured you /etc/hosts file to know the remote systems by name.

SSH allows you to perform remote logins, and a bit more.

Please clarify what you are trying to do, and indicate to us that your network between the systems is functional.

MrC

sorry about that I am trying to share files between the machines I want to transfer my music drive to my ubuntu laptop from the desktop AMD64 to the laptops

---

### Post by Mr. C. on 2007-06-12
Read this NFS thread:

[http://ubuntuforums.org/showthread.php?t=249889&highlight=NFS](http://ubuntuforums.org/showthread.php?t=249889&highlight=NFS)

MrC

---

### Post by shanerdaner on 2007-06-12
I don't understand this part please help me thanks!  I want to share all of my files between the 2 machines i hope this helps explain what I need thanks again!!!

Editing /etc/exports
the /etc/exports file is used for creating a share on the NFS server

invoke your favorite text editor or
sudo vi /etc/exports

Here are some quick examples of what you could add to your /etc/exports

For Full Read Write Permissions allowing any computer from 192.168.1.1 through 192.168.1.255

    * /files 192.168.1.1/24(rw,no_root_squash,async)


Or for Read Only from a single machine

    * /files 192.168.1.2 (ro,async)

save this file and then in a terminal type
sudo /etc/init.d/nfs-kernel-server restart

Also aftter making changes to /etc/exports in a terminal you must type
sudo exportfs -a

Install NFS client support
sudo apt-get install portmap nfs-common

---

### Post by Mr. C. on 2007-06-13
Which part of "this part" don't you understand ?

If you are stuck on opening an editor, I think we're in trouble here...

MrC

---

### Post by Robin T Cox on 2007-06-16
Perhaps my notes will help?

[http://ubuntuforums.org/showthread.php?t=463836&page=4]("http://ubuntuforums.org/showthread.php?t=463836&page=4")

---

### Post by domer on 2007-06-26
I want to connect my PC running Ubuntu Dapper with my laptop running Ubuntu Fiesty Fawn. I need to transfer a file that is almost 3 GB. Could someone help?

---

### Post by shanerdaner on 2007-07-03
> **Mr. C. said:**
> Which part of "this part" don't you understand ?

If you are stuck on opening an editor, I think we're in trouble here...

MrC

Look DUDE...... I am not an idiot here I used to have the machines networked by right clicking the folder and selecting share folder however I cant get this 2 work on any of machines since I installed feisty on all of them.  u don't need to make people feel like idiots that isn't helping them at all....

---

### Post by Mr. C. on 2007-07-03
I have no idea or concerns about your intelligence.  It is your ability to communicate precisely how and where you need help that can use some work.

We're not mind readers, and nobody but you can explain what you mean by "this 2 work" and "this part".

If you want help, spend more time formulating a clear and articulate request.  Others won't spend more time on your issue than you are willing to spend articulating it.

MrC

---

### Post by shanerdaner on 2007-07-03
> **Mr. C. said:**
> I have no idea or concerns about your intelligence.  It is your ability to communicate precisely how and where you need help that can use some work.

We're not mind readers, and nobody but you can explain what you mean by "this 2 work" and "this part".

If you want help, spend more time formulating a clear and articulate request.  Others won't spend more time on your issue than you are willing to spend articulating it.

MrC

I did I am just trying to get the 64 bit fiesty on the desktop to share folders with the 32 bit laptop It cannot be this hard..I can already share a printer.

---

