---
title: "ERROR: Module iwl4965 does not exist in /proc/modules"
date: 2008-03-26
forum: Networking &amp; Wireless
---

### Post by omidomid on 2008-03-26
I installed Gutsy and am trying to get the wireless to work. I have the intel 4965 AGN and used[ this tutorial]("http://kuscsik.blogspot.com/2007/06/how-to-install-intel-4965-wireless.html") to try to get it working. 

When I run  sudo modprobe iwl4965 it gives me
```
$ sudo modprobe iwl4965
FATAL: Error inserting iwl4965 (/lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/iwl4965.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

and when I try rmmod iwl4965 it says
```
$ rmmod iwl4965
ERROR: Module iwl4965 does not exist in /proc/modules

```

My laptop is a VAIO VGN-FZ190.
Can anyone help??

---

### Post by prshah on 2008-03-26
> **omidomid said:**
> 
When I run  sudo modprobe iwl4965 it gives me
```
$ sudo modprobe iwl4965
FATAL: Error inserting iwl4965 (/lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/iwl4965.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```
My laptop is a VAIO VGN-FZ190.
Can anyone help??

Try it again, then see ```
dmesg | tail -10
``` and post result here...

---

### Post by omidomid on 2008-03-26
```
omidomid@omid-PC:~$ sudo modprobe iwl4965
[sudo] password for omidomid:
FATAL: Error inserting iwl4965 (/lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/iwl4965.ko): Unknown symbol in module, or unknown parameter (see dmesg)
omidomid@omid-PC:~$ dmesg | tail -10
[   50.552000] ata1: soft resetting port
[   50.724000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   50.724000] ata1.00: configured for UDMA/100
[   50.724000] ata1: EH complete
[   50.724000] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   50.724000] sd 0:0:0:0: [sda] Write Protect is off
[   50.724000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   50.724000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  116.332000] iwl4965: Unknown symbol ieee80211_stop_BA_session
[  116.332000] iwl4965: Unknown symbol ieee80211_start_BA_session
omidomid@omid-PC:~$ 
```

---

### Post by omidomid on 2008-03-30
Find any solution yet Prshah? I'm still having this problem.

---

### Post by prshah on 2008-03-30
> **omidomid said:**
> Find any solution yet Prshah? I'm still having this problem.

When you refer to the tutorial, he says that the tutorial is outdated and NOT applicable for gutsy, which is what I see you are using. Did you run through the whole tutorial or just try modprobe?

---

### Post by omidomid on 2008-03-30
I ran through the whole tutorial... guess I missed the part about gutsy :( Is there a way to undo what I've done? I remember when I had a fresh install, the wifi thing would detect networks but wouldn't connect when I tried. Now it doesn't even show a wifi connection as an option (using nm-applet 0.6.5 or wifi-radar)

---

### Post by prshah on 2008-03-30
> **omidomid said:**
> I ran through the whole tutorial... guess I missed the part about gutsy :( Is there a way to undo what I've done? I remember when I had a fresh install, the wifi thing would detect networks but wouldn't connect when I tried. Now it doesn't even show a wifi connection as an option (using nm-applet 0.6.5 or wifi-radar)

My iwl module details are as below:
```

ls -l /lib/modules/2.6.22-14-generic/ubuntu/wireless/iwlwifi/iwlwifi/origin/iwl4965.ko
-rw-r--r-- 1 root root 119380 2007-10-13 11:13 /lib/modules/2.6.22-14-generic/ubuntu/wireless/iwlwifi/iwlwifi/origin/iwl4965.ko

```

Use ```
ls -l `slocate iwl4965`
``` and paste the result of your iwl4965 module. Note that " ' "  means single quote (With " ~ " key), NOT apostrophe (with **"** key)

If you think it will help, PM me your email address and I will send you the module file I have; you can replace what you have and let's see where it will get us.

---

### Post by omidomid on 2008-04-02
```
root@omid-PC:/home/omidomid# ls -l /lib/modules/2.6.22-14-generic/ubuntu/wireless/iwlwifi/iwlwifi/origin/iwl4965.ko-rw-r--r-- 1 root root 119380 2007-12-07 13:43 /lib/modules/2.6.22-14-generic/ubuntu/wireless/iwlwifi/iwlwifi/origin/iwl4965.ko
root@omid-PC:/home/omidomid# 
```

and

```
root@omid-PC:/home/omidomid# ls -l `slocate iwl4965`
-r--r--r-- 1 root root  274488 2008-03-26 12:01 /home/omidomid/Desktop/iwlwifi-1.2.25/compatible/iwl4965-base.c
-r--r--r-- 1 root root  274452 2008-03-26 12:01 /home/omidomid/Desktop/iwlwifi-1.2.25/compatible/iwl4965-base.c.orig
-rw-r--r-- 1 root root  628684 2008-03-29 22:18 /home/omidomid/Desktop/iwlwifi-1.2.25/compatible/iwl4965-base.o
-rw-r--r-- 1 root root   22325 2008-03-29 22:18 /home/omidomid/Desktop/iwlwifi-1.2.25/compatible/.iwl4965-base.o.cmd
-rw-r--r-- 1 root root 1205949 2008-03-29 22:18 /home/omidomid/Desktop/iwlwifi-1.2.25/compatible/iwl4965.ko
-rw-r--r-- 1 root root     282 2008-03-29 22:18 /home/omidomid/Desktop/iwlwifi-1.2.25/compatible/.iwl4965.ko.cmd
-rw-r--r-- 1 root root    4575 2008-03-26 12:01 /home/omidomid/Desktop/iwlwifi-1.2.25/compatible/iwl4965.mod.c
-rw-r--r-- 1 root root   32644 2008-03-29 22:18 /home/omidomid/Desktop/iwlwifi-1.2.25/compatible/iwl4965.mod.o
-rw-r--r-- 1 root root   12125 2008-03-29 22:18 /home/omidomid/Desktop/iwlwifi-1.2.25/compatible/.iwl4965.mod.o.cmd
-rw-r--r-- 1 root root 1174443 2008-03-29 22:18 /home/omidomid/Desktop/iwlwifi-1.2.25/compatible/iwl4965.o
-rw-r--r-- 1 root root     346 2008-03-29 22:18 /home/omidomid/Desktop/iwlwifi-1.2.25/compatible/.iwl4965.o.cmd
-rw-r--r-- 1 root root     247 2008-03-29 22:18 /home/omidomid/Desktop/iwlwifi-1.2.25/compatible/.tmp_versions/iwl4965.mod
-rw-rw-r-- 1 1005 1005  272859 2008-02-04 16:55 /home/omidomid/Desktop/iwlwifi-1.2.25/origin/iwl4965-base.c
-rw-r--r-- 1 root root 1205949 2008-03-29 22:22 /lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/iwl4965.ko
-rw-r--r-- 1 root root  119380 2007-12-07 13:43 /lib/modules/2.6.22-14-generic/ubuntu/wireless/iwlwifi/iwlwifi/origin/iwl4965.ko
root@omid-PC:/home/omidomid# 
```

Sending you my email right now.

---

### Post by prshah on 2008-04-03
> **omidomid said:**
> ```
root@omid-PC:/home/omidomid# -rw-r--r-- 1 root root [color=red]1205949[/color] 2008-03-29 22:22 /lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/iwl4965.ko
-rw-r--r-- 1 root root  [color=red]119380[/color] 2007-12-07 13:43 /lib/modules/2.6.22-14-generic/ubuntu/wireless/iwlwifi/iwlwifi/origin/iwl4965.ko
root@omid-PC:/home/omidomid# 
```


I see that the module you have compiled is 10 (!!) times the size of the shipped module. That's strange.

In any case, you have the original module on your system, so me sending it to you won't help.

Let's try this: Move out your compiled module so that when you modprobe only the original gets loaded. Do you still ge the same error? ```
sudo rmmod iwl4965 
sudo mv /lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/iwl4965.ko ~/iwl_module
sudo modprobe iwl4965

```

_IF_ you get the same error, lets reverse the process to ensure that ONLY your compiled module gets loaded ```
sudo rmmod iwl4965
sudo mv iwl_module /lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/iwl4965.ko
sudo mv /lib/modules/2.6.22-14-generic/ubuntu/wireless/iwlwifi/iwlwifi/origin/iwl4965.ko ~/orig_iwl_module
sudo modprobe iwl4965

```

If it still doesn't work, post any error messages and output of ```
dmesg | tail -15
``` and we'll try a different tack.

---

### Post by omidomid on 2008-04-04
```
omidomid@omid-PC:~$ sudo rmmod iwl4965 
[sudo] password for omidomid:
ERROR: Module iwl4965 does not exist in /proc/modules
omidomid@omid-PC:~$ sudo mv /lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/iwl4965.ko ~/iwl_module
omidomid@omid-PC:~$ sudo modprobe iwl4965
FATAL: Could not open '/lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/iwl4965.ko': No such file or directory
omidomid@omid-PC:~$ sudo rmmod iwl4965
ERROR: Module iwl4965 does not exist in /proc/modules
omidomid@omid-PC:~$ sudo mv iwl_module /lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/iwl4965.ko
omidomid@omid-PC:~$ sudo mv /lib/modules/2.6.22-14-generic/ubuntu/wireless/iwlwifi/iwlwifi/origin/iwl4965.ko ~/orig_iwl_module
omidomid@omid-PC:~$ sudo modprobe iwl4965
FATAL: Error inserting iwl4965 (/lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/iwl4965.ko): Unknown symbol in module, or unknown parameter (see dmesg)
omidomid@omid-PC:~$
```

dmesg shows:
```
omidomid@omid-PC:~$ dmesg | tail -15
[ 3285.292000] ata1.00: cmd 61/08:30:db:3c:f5/00:00:10:00:00/40 tag 6 cdb 0x0 data 4096 out
[ 3285.292000]          res 50/00:08:23:3d:f5/00:00:10:00:00/40 Emask 0x2 (HSM violation)
[ 3285.292000] ata1.00: cmd 61/08:38:eb:3c:f5/00:00:10:00:00/40 tag 7 cdb 0x0 data 4096 out
[ 3285.292000]          res 50/00:08:23:3d:f5/00:00:10:00:00/40 Emask 0x2 (HSM violation)
[ 3285.604000] ata1: soft resetting port
[ 3285.776000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 3285.776000] ata1.00: configured for UDMA/100
[ 3285.776000] ata1: EH complete
[ 3285.776000] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[ 3285.776000] sd 0:0:0:0: [sda] Write Protect is off
[ 3285.776000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 3285.776000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 3415.996000] audit(1207298865.455:4):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=7055 profile="/usr/sbin/cupsd"
[ 3515.612000] iwl4965: Unknown symbol ieee80211_stop_BA_session
[ 3515.612000] iwl4965: Unknown symbol ieee80211_start_BA_session
omidomid@omid-PC:~$ 

```

Almost thinking that reinstalling Ubuntu might be worth it... I really don't want to set up everything again though =(

---

### Post by prshah on 2008-04-04
> **omidomid said:**
> 
Almost thinking that reinstalling Ubuntu might be worth it... I really don't want to set up everything again though =(

Ok, One LAST desperate attempt before chucking the whole installation out;

```

sudo rmmod iwl4965
sudo mv -f ~/orig_iwl_module /lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/iwl4965.ko
sudo modprobe iwl4965

```

This should definately clear up the issue.

the "rmmod" command may give an error "...not found in..", that can be ignored since it just means that the module is not loaded in the first place.

---

### Post by omidomid on 2008-04-07
Still haven't done anything wit this.. no wifi on ubuntu for weeks now =(. And the worst part is I've been booting into XP instead :O (shame, I know).

---

