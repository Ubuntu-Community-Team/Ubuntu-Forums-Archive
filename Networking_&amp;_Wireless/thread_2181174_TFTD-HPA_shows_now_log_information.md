---
title: "TFTD-HPA shows now log information"
date: 2013-10-16
forum: Networking &amp; Wireless
---

### Post by ylafont on 2013-10-16
Recently is have been unable to pxe boot and started to receive the following errors. 

PXE-E11: ARP timeout
PXE-E11: ARP timeout
PXE-E38: TFTP cannot open connection
PXE-M0F: Exiting intel PXE ROM

The strangest part here is that syslog has not recorded any entries concerning TFTP-HPA leaving to wonder what the problem is. 

syslog - [https://dl.dropboxusercontent.com/u/58850968/syslog](https://dl.dropboxusercontent.com/u/58850968/syslog)


**sudo service tftpd-hpa status**
tftpd-hpa start/running, process 4470



**ps aux|grep tftp**


root      4470  0.0  0.0  15092   176 ?        Ss   15:11   0:00 /usr/sbin/in.tftpd --listen --user tftp --address 0.0.0.0:69 --secure --ipv4 --map-file /etc/tftpd.map --verbose /srv/pxeboot
xbmc      6665  0.0  0.0   9388   932 pts/0    S+   16:03   0:00 grep --color=auto tftp



**/etc/default/tftpd-hpa**


RUN_DAEMON="YES"
TFTP_USERNAME="tftp"
TFTP_DIRECTORY="/srv/pxeboot"
TFTP_ADDRESS="0.0.0.0:69"
TFTP_OPTIONS="--secure --ipv4 --map-file /etc/tftpd.map --verbose"
#TFTP_OPTIONS="--secure"
OPTIONS="-l -s /var/lib/tftpboot"


assistance is appreciated. thank you.

---

### Post by newbie-user on 2013-10-16
It looks like there's a conflict in your TFTP directories.

Try removing the TFTP_DIRECTORY line and changing the OPTIONS line to OPTIONS="-l -s /srv/pxeboot"

---

### Post by ylafont on 2013-10-16
Thanks for the reply Newbiw, however, that change in the config file did nothing.

still no log entries in syslog. which makes this that much harder to troubleshoot.

Just in case, i removed tftpd-hpa  and re-installed it without success.

---

### Post by newbie-user on 2013-10-16
what are the contents of /srv/pxeboot and what are the permissions?

---

### Post by ylafont on 2013-10-16
/srv/pxeboot contains syslinux and windows source. 

xbmc@PlexOne:/srv$ ls -l
total 4
drwxrwxrwx 8 root root 4096 Oct 15 17:34 pxeboot

BTW - i have also turn off the firewall to see if it was a problem.

---

### Post by newbie-user on 2013-10-16
Does the pxeboot folder have anything in it? And permissions for those?

---

### Post by ylafont on 2013-10-16
contents of /srv/pxeboot

xbmc@PlexOne:/srv/pxeboot$ ls -l
total 1708
-rwxrwxrwx 1 root root    439 Jul  2  2012 altmbr.bin
-rwxrwxrwx 1 root root    439 Jul  2  2012 altmbr_c.bin
-rwxrwxrwx 1 root root    439 Jul  2  2012 altmbr_f.bin
-rwxrwxrwx 1 xbmc xbmc  12288 Oct 15 16:05 BCD.LOG
-rwxrwxrwx 1 xbmc xbmc      0 Oct 15 16:05 BCD.LOG1
-rwxrwxrwx 1 xbmc xbmc      0 Oct 15 16:05 BCD.LOG2
drwxrwxr-x 3 xbmc xbmc   4096 Oct 15 17:43 Boot
-rwxrwxrwx 1 xbmc xbmc    315 Oct 15 17:31 b.sh
-rwxrwxrwx 1 root root   5824 Jul  2  2012 cat.c32
-rwxrwxrwx 1 root root  20704 Jul  2  2012 chain.c32
-rwxrwxrwx 1 root root    800 Jul  2  2012 cmd.c32
drwxrwxrwx 3 root root   4096 Oct 12 22:24 com32
-rwxrwxrwx 1 root root   4748 Jul  2  2012 config.c32
-rwxrwxrwx 1 root root   5516 Jul  2  2012 cpuid.c32
-rwxrwxrwx 1 root root  15448 Jul  2  2012 cpuidtest.c32
drwxr-xr-x 2 root root   4096 Oct 12 22:24 diag
-rwxrwxrwx 1 root root   5516 Jul  2  2012 disk.c32
-rwxrwxrwx 1 root root  37016 Jul  2  2012 dmitest.c32
drwxr-xr-x 2 root root   4096 Oct 12 22:24 dosutil
-rwxrwxrwx 1 root root  28752 Jul  2  2012 elf.c32
-rwxrwxrwx 1 root root  29008 Jul  2  2012 ethersel.c32
-rwxrwxrwx 1 root root  21948 Jul  2  2012 gfxboot.c32
-rwxrwxrwx 1 root root    440 Jul  2  2012 gptmbr.bin
-rwxrwxrwx 1 root root    440 Jul  2  2012 gptmbr_c.bin
-rwxrwxrwx 1 root root    440 Jul  2  2012 gptmbr_f.bin
-rwxrwxrwx 1 root root   2320 Jul  2  2012 gpxecmd.c32
-rwxrwxrwx 1 root root  89469 Jul  2  2012 gpxelinux.0
-rwxrwxrwx 1 root root  89375 Jul  2  2012 gpxelinuxk.0
-rwxrwxrwx 1 root root 342708 Jul  2  2012 hdt.c32
-rwxrwxrwx 1 root root   4492 Jul  2  2012 host.c32
-rwxrwxrwx 1 root root   1312 Jul  2  2012 ifcpu64.c32
-rwxrwxrwx 1 root root  19936 Jul  2  2012 ifcpu.c32
-rwxrwxrwx 1 root root   2444 Jul  2  2012 ifplop.c32
-rwxrwxrwx 1 root root     55 Jul  2  2012 int18.com
-rwxrwxrwx 1 root root    432 Jul  2  2012 isohdpfx.bin
-rwxrwxrwx 1 root root    432 Jul  2  2012 isohdpfx_c.bin
-rwxrwxrwx 1 root root    432 Jul  2  2012 isohdpfx_f.bin
-rwxrwxrwx 1 root root    432 Jul  2  2012 isohdppx.bin
-rwxrwxrwx 1 root root    432 Jul  2  2012 isohdppx_c.bin
-rwxrwxrwx 1 root root    432 Jul  2  2012 isohdppx_f.bin
-rwxrwxrwx 1 root root  24576 Jul  2  2012 isolinux.bin
-rwxrwxrwx 1 root root  24576 Jul  2  2012 isolinux-debug.bin
-rwxrwxrwx 1 root root   5212 Jul  2  2012 kbdmap.c32
-rwxrwxrwx 1 root root  16872 Jul  2  2012 linux.c32
-rwxrwxrwx 1 root root   9388 Jul  2  2012 ls.c32
-rwxrwxrwx 1 root root 249420 Jul  2  2012 lua.c32
-rwxrwxrwx 1 root root  34396 Jul  2  2012 mboot.c32
-rwxrwxrwx 1 root root    440 Jul  2  2012 mbr.bin
-rwxrwxrwx 1 root root    440 Jul  2  2012 mbr_c.bin
-rwxrwxrwx 1 root root    440 Jul  2  2012 mbr_f.bin
-rwxr--r-- 1 root root  26140 Jul  2  2012 memdisk
-rwxrwxrwx 1 root root   5912 Jul  2  2012 memdump.com
-rwxrwxrwx 1 root root   5300 Jul  2  2012 meminfo.c32
-rwxrwxrwx 1 root root  56164 Jul  2  2012 menu.c32
-rwxrwxrwx 1 root root  32740 Jul  2  2012 pcitest.c32
-rwxrwxrwx 1 root root  13148 Jul  2  2012 pmload.c32
-rwxrwxrwx 1 root root    239 Jul  2  2012 poweroff.com
-rwxrwxrwx 1 root root   1932 Jul  2  2012 pwd.c32
-rwxrwxrwx 1 root root    998 Jul  2  2012 pxechain.com
-rwxrwxrwx 1 root root  26461 Jul  2  2012 pxelinux.0
drwxrwxrwx 2 root root   4096 Oct 12 23:57 pxelinux.cfg
-rwxrwxrwx 1 root root    800 Jul  2  2012 reboot.c32
-rwxrwxrwx 1 root root  21384 Jul  2  2012 rosh.c32
-rwxrwxrwx 1 root root   2448 Jul  2  2012 sanboot.c32
-rwxrwxrwx 1 root root  26192 Jul  2  2012 sdi.c32
-rwxrwxrwx 1 root root  40432 Jul  2  2012 sysdump.c32
-rwxrwxrwx 1 root root   1300 Jul  2  2012 ver.com
-rwxrwxrwx 1 root root   5260 Jul  2  2012 vesainfo.c32
-rwxrwxrwx 1 root root 155792 Jul  2  2012 vesamenu.c32
-rwxrwxrwx 1 root root   6052 Jul  2  2012 vpdtest.c32
-rwxrwxrwx 1 root root   2960 Jul  2  2012 whichsys.c32
drwxrwxr-x 4 xbmc xbmc   4096 Oct 12 20:51 windows
-rwxrwxrwx 1 root root   9616 Jul  2  2012 zzjson.c32

---

### Post by newbie-user on 2013-10-16
Not really a fix, but have you tried symlinking /srv/pxeboot to /var/lib/tftpboot and just using the default settings of the tftpd-hpa service?

---

### Post by ylafont on 2013-10-16
i guess i could do that, but don't it will help since nothing is being reported in syslog. not even a blip that tftp-hpa is alive.

---

### Post by newbie-user on 2013-10-16
I just noticed there's nothing in my syslog about tftpd-hpa either. Interesting, I don't know where it logs to. Anyway, you can check /var/log/boot.log to see if your tftp service started up.

---

### Post by ylafont on 2013-10-16
That is strange, i know there were entries in the syslog, especially, once i placed the "--verbose" option in the config file.  it displayed the mapfile entries and other items.

Bootlog - shows nothing.

---

### Post by ylafont on 2013-10-17
I am literally at a loss, here anyone else have other suggestions on how to get TFTD-HPA to respond? or find out what is the problem?

machine get ip via dhcp, 
firwall is off, 
tftpd-hpa service is running
config files look to be ok.

but i get  **tftp pxe-e11 arp timeout** on the work station. or can this be a bug?

thanks,.

---

### Post by ylafont on 2013-10-17
Eureka, 

shortly after the last posting, i reboot the workstation and realized that the DHCP address was incorrect. The dhcp server was on a DHCP reservation that was home how mysteriously removed on the router.

once i made the change the workstation came right up!

this was harder to troubleshoot since there was to log entries reported.

---

