---
title: "NFS mount mystery"
date: 2008-09-25
forum: Networking &amp; Wireless
---

### Post by Helge on 2008-09-25
I have two computers with 99.5 % identical installations of Ubuntu.
The directory /proj/cds_libs is automatically mounted on computer A, but not on computer B. /proj/raic is automatically mounted on both computers.

In addition, when A (which is a dual-boot machine) is started with Suse, it works OK.

A is an HP xw6200.
B is an HP xw9400.

I made the installation on computer B by inserting an Ubuntu live-CD and copy the whole relevant partition from the IDE disk to a new SATA disk. (Computer B has no IDE available). Tools used: dd and gparted. Then I moved the SATA disk to computer B and it booted without problems.

The computers are connected via a hub/switch to the same ethernet. It is in a mixed Solaris/Linux environment, with mostly Suse for Linux. NIS is used for user accounts and mounting of NFS disks. 

The relevant line in /etc/auto.master is:
 /proj auto_proj
The file is identical on both machines.
/etc/nsswitch.conf is also identical.

Directories that are to be mounted at /proj are found using NIS. There is no information in /etc about the existance of, e.g., /proj/raic.

ypcat auto.master yields:
auto_proj
auto_misc
auto_org
auto_cc

ypcat auto_proj yields a lot of lines, including:
-nosuid,intr	esekina601.rnd.ki.sw.ericsson.se:/vol/vol0105/u05001/cds_libs
-nosuid,intr kia8.al.sw.ericsson.se:/vol/vol151/unix-group/ERAX/raic

This seems to be the same, regardless of if the command is issued from an Ubuntu (A or B), Suse or Solaris machine.

Several reboots have not helped. 
"/etc/init.d/autofs restart" has not helped
"/etc/init.d/nis restart" has not helped
"/etc/init.d/nfs-common restart" has not helped


The only things that are different between the machines A and B is:
- different MAC addressed
- different hostname (because the MAC addresses, given by DHCP, I think)
- different network cards (B has two contacts). A connects via eth1; B via eth2.

Have I missed something essential? How can A and B behave so differently?

---

### Post by Helge on 2008-09-25
A colleague reported a similar problem when he changed from Suse 10 to Suse 9. It appears that the IP address as reported by ifconfig is different as that reported by "nslookup `hostname`". 

I seem to have the wrong IP address according to ifconfig, when I run Ubuntu but not when I run Suse. 

The recommendation from the IT support guy (for my colleagues machine), was to turn off the computer overnight. How would that help? Would it be possible to change some local file instead?

---

