---
title: "DESPARATE!! Please can someone in the know answer these posts,"
date: 2006-07-20
forum: Networking &amp; Wireless
---

### Post by dgrafix on 2006-07-20
Sorry to keep posting this but im desparate for a response:

**THE PROBLEM:**
SMB/SAMBA. Basically looking at the transfer rates using firestarter(yes its disabled) or systemmonitor im seeing transfer rates of just KiBs sometimes i get 5MiBs but thats rare. Sometimes it flatlines for a long time.
There is no other network activity on any machine. And are all connected theough a Netgear WRGsomethingV6 router with the latest firmware.
On a 100Mb lan i would expect to see speeds of at least 5-10MB/s
Originally i thought it was because it was 1000s of image files but this is not the case, it also is the same with big 1 gig files too.
There is no problem between the 2 win pcs and no viruses/spywares were found

**These are the unanswered posts of myself and others regarding this:**
[http://www.ubuntuforums.org/showthread.php?t=219099](http://www.ubuntuforums.org/showthread.php?t=219099)
[http://www.ubuntuforums.org/showthread.php?t=131025](http://www.ubuntuforums.org/showthread.php?t=131025)
[http://www.ubuntuforums.org/showthread.php?t=218373&highlight=slow+network](http://www.ubuntuforums.org/showthread.php?t=218373&highlight=slow+network)
[http://www.ubuntuforums.org/showthread.php?t=218615&highlight=slow+network](http://www.ubuntuforums.org/showthread.php?t=218615&highlight=slow+network)
[http://www.ubuntuforums.org/showthread.php?t=197438&page=3&highlight=mii-tool](http://www.ubuntuforums.org/showthread.php?t=197438&page=3&highlight=mii-tool)

**THE SETUP:**
Im on a 100Mb lan with my main PC (ubuntu dapper gnome etc) which is also acting as a simple SMB fileserver for my windows laptops.

I keep all my files on the linux box, windows is just a OS with no files on them. This is to keep them consistent when working either in house or in the garden/bed etc.

(This problem is not a wireless issue if thats what youre thinking, its the same problem when on cable with all wireless disabled)

**THE SCREENSHOT:**

Here is a shot of a typical transfer from my LINUX2WINDOWS. As you can see the transfer rate fluctuates wildly and flatlines for long periods. I get the same problem in the other direction too.
[IMG]http://www.d-grafix.com/image.jpg[/IMG]

SOME DATA:
Network card is o/b sis900 (which i think is fduplex?!?)

```


dan@linuxpc:~$ mii-tool
SIOCGMIIPHY on 'eth0' failed: Operation not permitted
SIOCGMIIPHY on 'eth1' failed: Operation not permitted
SIOCGMIIPHY on 'eth2' failed: Operation not permitted
SIOCGMIIPHY on 'eth3' failed: Operation not permitted
SIOCGMIIPHY on 'eth4' failed: Operation not permitted
SIOCGMIIPHY on 'eth5' failed: Operation not permitted
SIOCGMIIPHY on 'eth6' failed: Operation not permitted
SIOCGMIIPHY on 'eth7' failed: Operation not permitted
no MII interfaces found

dan@linuxpc:~$ /sbin/ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:6C:F8:0E:99
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:125703 errors:0 dropped:0 overruns:0 frame:0
          TX packets:361974 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:30676391 (29.2 MiB)  TX bytes:451083617 (430.1 MiB)
          Interrupt:217 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:340 (340.0 b)  TX bytes:340 (340.0 b)


```

---

### Post by OpsVentus on 2006-07-20
Some stuff I find when searching the web about samba and performance:
**Network Collisions**

"Excessive network activity causes NetBIOS network timeouts. Timeouts may result in blue screen of death (BSOD) experiences. High collision rates may be caused by excessive UDP broadcast activity, by defective networking hardware, or through excessive network loads (another way of saying that the network is poorly designed).

The use of WINS is highly recommended to reduce network broadcast traffic, as outlined in ???.

Under no circumstances should the facility be supported by many routers, known as NetBIOS forwarding, unless you know exactly what you are doing. Inappropriate use of this facility can result in UDP broadcast storms. In one case in 1999, a university network became unusable due to NetBIOS forwarding being enabled on all routers. The problem was discovered during performance testing of a Samba server. The maximum throughput on a 100-Base-T (100 MB/sec) network was less than 15 KB/sec. After the NetBIOS forwarding was turned off, file transfer performance immediately returned to 11 MB/sec. "

**Preallocating space**
"It is trying to preallocate space for this file by writing forward in 32kb
blocks where value 0 (zero) is written to the first byte of this 32kb block (

in my case it is ext3 filesystem with 4kb inodes so it is 8 inodes). This wastes 1 inode separated by 7 unused inodes between another used inode. Windows XP starts to write real data when cca 20MB of space is prealocated and it causes that this data is not written exactly to that prealloced space. It is prealocating this space parallely with writting of data 20MB or so ahead and it causes fragmentation of file data. This peallocation causes that 7 inodes of one part of file are followed by one inode of another part of file. I know that it can be eliminated by dissabling sparse files but that can cause other problems too."

**Configuration**
"There are two parameters that can cause severe network performance degradation: socket options  and socket address. The socket options parameter was often necessary when Samba was used with the Linux 2.2.x kernels. Later kernels are largely self-tuning and seldom benefit from this parameter being set. Do not use either parameter unless it has been proven necessary to use them.

 Another smb.conf parameter that may cause severe network performance degradation is the strict sync parameter. Do not use this at all. There is no good reason to use this with any modern Windows client. The strict sync is often used with the sync always parameter. This, too, can severely degrade network performance, so do not set it; if you must, do so with caution.

Finally, many network administrators deliberately disable opportunistic locking support. While this does not degrade Samba performance, it significantly degrades Windows client performance because this disables local file caching on Windows clients and forces every file read and written to invoke a network read or write call. If for any reason you must disable oplocks (opportunistic locking) support, do so only on the share on which it is required. That way, all other shares can provide oplock support for operations that are tolerant of it. See ??? for more information. "

**Large directory's**
"There exist applications that create or manage directories containing many thousands of files. Such applications typically generate many small files (less than 100 KB). At the best of times, under UNIX, listing of the files in a directory that contains many files is slow. By default, Windows NT, 200x, and XP Pro cause network file system directory lookups on a Samba server to be performed for both the case preserving file name as well as for the mangled (8.3) file name. This incurs a huge overhead on the Samba server that may slow down the system dramatically.

In an extreme case, the performance impact was dramatic. File transfer from the Samba server to a Windows XP Professional workstation over 1 Gigabit Ethernet for 250-500 KB files was measured at approximately 30 MB/sec. But when tranferring a directory containing 120,000 files, all from 50KB to 60KB in size, the transfer rate to the same workstation was measured at approximately 1.5 KB/sec. The net transfer was on the order of a factor of 20-fold slower.

The symptoms that will be observed on the Samba server when a large directory is accessed will be that aggregate I/O (typically blocks read) will be relatively low, yet the wait I/O times will be incredibly long while at the same time the read queue is large. Close observation will show that the hard drive that the file system is on will be thrashing wildly.

Samba-3.0.12 and later, includes new code that radically improves Samba perfomance. The secret to this is really in the case sensitive = True line. This tells smbd never to scan for case-insensitive versions of names. So if an application asks for a file called FOO, and it can not be found by a simple stat call, then smbd will return "file not found" immediately without scanning the containing directory for a version of a different case. "

Maybe one of these help?

Cheers,
Bart.

---

### Post by dgrafix on 2006-07-20
Ok, ive taken out the socket options line and it seems to have stabilized the transfer as far as im no longer getting flatlines & timeouts.

Im still getting updowns between 10KB and 1024KB transfer rates though!!!

This is really crazy is there some kind of throttle in effect somewhere? ive no idea what could be causing this.

---

### Post by dgrafix on 2006-07-20
Actually, spoke too soon its failed again.

Put back in the Notcpdelay bit as default.


Booted machine into widows and tested the transfer and it was ok so its definitely a ubuntu problem.

I dont think i had this problem with hoary (not the time outs anyway although it was slow on that too)

---

### Post by dgrafix on 2006-07-20
Ive fixed it....

the old classic one of....

ripping an old PCI net card from an old machine and whacking it in.

Im getting 3MB/s fairly stable now, slower than windows it seems but at least i can trust it again.

Anyone with a onboard sis900 may need to watch out, and i suggest a serious look at the way ubuntu talks to it as its one of the most common onboarders.

GRR 4 days down the drain.. O well its not so bad, funny how when something works again you feel the anger lifting :mad: :-| :)

---

### Post by OpsVentus on 2006-07-21
Well yes that's the other thing, check your hardware. Not every device is working as well under Linux as under Windows. This becauss some hardware are made for Windows and not how they should work.

Cheers,
Bart.

---

### Post by peachy on 2006-08-02
I'm getting the same on my dell d820, using Kubuntu dapper with the ipw3945 driver. I'm typically getting about 100kb/s over a 54mbps wireless lan using samba. Since I have only recently installed Kubuntu I haven't tried the gigabit ethernet yet, nor tried NFS etc. apt-get is typically downloading at about 600kb/s on my 6mb broadband connection so at first glance it seems to be samba specific.

Using Mandriva with the windows driver through ndiswrapper i don't get the same problem.

---

### Post by SuperLou on 2007-02-11
I believe the problem may have something to do with the SiS900 and PHY transceiver.  I'm not sure how to fix it, but I've got the same problem with onboard ethernet in linux and not windows (not just ubuntu).  Check your dmesg and see if you get something similar:

[17179589.472000] sis900.c: v1.08.09 Sep. 19 2005
[17179589.472000] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 209
[17179589.476000] 0000:00:04.0: Unknown PHY transceiver found at address 0.
[17179589.484000] 0000:00:04.0: Using transceiver found at address 0 as default


I don't know how to fix it.  If anyone has ideas I would greatly appreciate it.

---

