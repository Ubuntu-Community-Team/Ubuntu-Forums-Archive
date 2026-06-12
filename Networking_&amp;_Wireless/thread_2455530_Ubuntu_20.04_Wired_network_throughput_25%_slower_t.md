---
title: "Ubuntu 20.04 Wired network throughput 25% slower than Windows 7"
date: 2020-12-21
forum: Networking &amp; Wireless
---

### Post by mtbdrew on 2020-12-21
Same hardware dual boot with Windows 7 and Ubuntu 20.04. Gigabit network connection to Synology DS1515+ when transferring large files to NAS under Windows 7 I get 100Mib/sec. However when I reboot into Ubuntu on the same machine and transfer the same file I only get 75Mib/sec.

 NIC is /0/100/15.1/0  enp3s0      network     RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
Settings for enp3s0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supported pause frame use: Symmetric Receive-only
	Supports auto-negotiation: Yes
	Supported FEC modes: Not reported
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised pause frame use: Symmetric Receive-only
	Advertised auto-negotiation: Yes
	Advertised FEC modes: Not reported
	Link partner advertised link modes:  10baseT/Half 10baseT/Full 
	                                     100baseT/Half 100baseT/Full 
	                                     1000baseT/Half 1000baseT/Full 
	Link partner advertised pause frame use: Symmetric
	Link partner advertised auto-negotiation: Yes
	Link partner advertised FEC modes: Not reported
	Speed: 1000Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: Unknown
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
			       drv probe ifdown ifup
	Link detected: yes

I have tried the default R8169 and the R8168 drivers, the first only gives 70Mib/sec instead of the 75Mib/sec with the R8168. Have attempted to manually set network settings but get better throughput when left on automatic.

---

### Post by TheFu on 2020-12-21
Look at the file system connection, not the networking drivers.  Avoid GIO and GVFS, which is what almost all Linux GUIs use.  Use a direct CIFS mount instead with the highest version that is supported by the NAS.  Do that in the /etc/fstab.
[https://gitlab.gnome.org/GNOME/gvfs/-/issues/292](https://gitlab.gnome.org/GNOME/gvfs/-/issues/292)
Is is a common issue across all Linux distros.

If your NAS supports it, use NFS instead.  The storage will appear like local storage when NFS is used. 
[https://www.synology.com/en-us/knowledgebase/DSM/tutorial/File_Sharing/How_to_access_files_on_Synology_NAS_within_the_local_network_NFS](https://www.synology.com/en-us/knowledgebase/DSM/tutorial/File_Sharing/How_to_access_files_on_Synology_NAS_within_the_local_network_NFS)

---

### Post by mtbdrew on 2020-12-31
The nfs method is definitely much faster 250MiB/sec! Thanks for the links i have always wanted to get the nfs working with my DS1515+ but never could figure all the settings out for the NAS and the client. Only issue is I had to use sudo command for the mounting to work otherwise i got and error regarding the -t options only being possible as root.

---

### Post by TheFu on 2020-12-31
CIFS should be similar speed. Both are easiest configured in the fstab. The poor performance was 99% due to using fake mounts. That's a GUI issue and has been for a long time.

If this is solved, please use the thread tools button.

---

### Post by mtbdrew on 2021-01-01
I'm not seeing that kind of transfer speeds with CIFS. I have this set in fstab:

//192.168.101.250/movies  /media/movies  cifs  credentials=/home/master/.smbcredentials,vers=3.0,iocharset=utf8,users	0	0 

But am making out at around 65MB/s

---

### Post by mtbdrew on 2021-01-05
Finally managed to get nfs mount working with etc/fstab and not have it require root access. Transfers speeds are on pare with windows now. Way better than either samba CIFS via etc/fstab.

---

