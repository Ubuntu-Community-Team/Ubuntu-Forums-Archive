---
title: "Network Stops Working After Sleep"
date: 2014-03-21
forum: Networking &amp; Wireless
---

### Post by spanner2 on 2014-03-21
Since upgrading to Ubuntu 13.10, whenever I wake the computer up from sleep, it loses its network. It's wired via ethernet to the router and works fine after restarting.

After coming out of sleep, a wifi "fan" symbol appears in the top status bar, as though ubuntu thinks it's connected wirelessly (which it isn't) and clicking "enable networking" doesn't help. I have to restart to get it connected again. 

Any help would be appreciated. Thanks in advance!

---

### Post by praseodym on 2014-03-22
Please show both terminal outputs of
```

lsmod
lsmod | grep -iE '802|ndiswr|forced|8139|hci|usb|1394|hid|..tv' 
```

---

### Post by spanner2 on 2014-03-22
> **praseodym said:**
> Please show both terminal outputs of
```

lsmod
lsmod | grep -iE '802|ndiswr|forced|8139|hci|usb|1394|hid|..tv' 
```

Hi there, thanks for the reply. Okay, we've got:

```
"**lsmod**" :[INDENT]Module                  Size  Used by
nfsv3                  34001  1 
bnep                   18959  2 
rfcomm                 53664  0 
bluetooth             323656  10 bnep,rfcomm
rpcsec_gss_krb5        30799  0 
nfsv4                 215911  0 
binfmt_misc            13140  1 
nfsd                  247847  2 
auth_rpcgss            48552  2 nfsd,rpcsec_gss_krb5
nfs_acl                12733  2 nfsd,nfsv3
nfs                   156370  3 nfsv3,nfsv4
lockd                  78549  3 nfs,nfsd,nfsv3
sunrpc                230213  23 nfs,nfsd,rpcsec_gss_krb5,auth_rpcgss,lockd,nfsv3,nfsv4,nfs_acl
snd_hda_codec_hdmi     40402  1 
fscache                55868  2 nfs,nfsv4
ppdev                  17391  0 
joydev                 17097  0 
snd_hda_codec_via      23156  1 
kvm_amd                50537  0 
kvm                   368975  1 kvm_amd
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25094  1 snd_seq_midi
radeon               1312332  3 
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_hda_intel          42658  5 
snd_hda_codec         164003  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
microcode              18894  0 
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                89488  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
ttm                    75982  1 radeon
psmouse                90642  0 
drm_kms_helper         46867  1 radeon
serio_raw              13189  0 
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
drm                   242400  5 ttm,drm_kms_helper,radeon
k10temp                12958  0 
snd_timer              24447  2 snd_pcm,snd_seq
i2c_algo_bit           13197  1 radeon
snd                    60790  21 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_via,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12600  1 snd
i2c_nforce2            13037  0 
parport_pc             31981  1 
mac_hid                13037  0 
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
hid_generic            12492  0 
usbhid                 47361  0 
hid                    87370  2 hid_generic,usbhid
pata_acpi              12886  0 
forcedeth              62099  0 
sata_nv                23004  0 
pata_amd               13761  2 
[/INDENT]

"**lsmod | grep -iE '802|ndiswr|forced|8139|hci|usb|1394|hid|..tv'**" :[INDENT]mac_hid                13037  0 
hid_generic            12492  0 
usbhid                 47361  0 
hid                    87370  2 hid_generic,usbhid
forcedeth              62099  0
[/INDENT]
```

---

### Post by praseodym on 2014-03-23
Force the necessary modules being unloaded for SUSPEND/HIBERNATE and being reloaded during wake-up:
```

sudo touch /etc/pm/config.d/00sleep_module
sudo chmod +x /etc/pm/config.d/00sleep_module
```
Open the file

```
gksudo gedit /etc/pm/config.d/00sleep_module
```
and add:
```

SUSPEND_MODULES="$SUSPEND_MODULES mac_hid hid_generic usbhid hid forcedeth" 

```
Save, close the editor and check S/H.

---

### Post by spanner2 on 2014-03-23
Went through this procedure, and double checked that the code was saved into the 00.sleep_module file, but no joy unfortunately. The same thing is still happening after waking up from suspending/hybernating. Any other advice is very welcome, and thanks for helping so far.

---

### Post by praseodym on 2014-03-23
Check the BIOS-settings, if S/H is possible, and please run the command:

```
echo; for i in --suspend --hibernate --suspend-hybrid; do pm-is-supported $i && echo "$(echo $i | tr [:lower:] [:upper:] | tr -d -) is supported"; done; echo 
```
Do you wish to use Suspend-to-RAM or Suspend-to-Disc? If "Disc", should it be on a separate partition or SWAP?

---

### Post by spanner2 on 2014-03-23
Hi again. It looks like both are available. Here's the reply I got in terminal@

SUSPEND is supported
HIBERNATE is supported


Unfortunately I'm an Ubuntu noob, and I'm not really sure about suspending to RAM or to disk. It used to work fine, but I'm not sure which method was being used to suspend the computer. I'd be happy with whichever worked :-)

---

### Post by praseodym on 2014-03-23
I recommend STD. Lets check
```

sudo fdisk -l 
sudo blkid
ls -l /dev/disk/by-uuid 
cat /etc/initramfs-tools/conf.d/resume
cat /etc/uswsusp.conf
cat /etc/default/grub
```

---

### Post by spanner2 on 2014-03-23
I'm not entirely sure what that code does for me (whether it's an attempt at fixing the problem, or for gathering more info). I put it all in and tested hibernation, but the problem persists. So just in case it's for the latter purpose, here's what Terminal offered after each line:
```
[B]
sudo fdisk -l
[/B][INDENT]Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4632f051

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   630887044   315443491    7  HPFS/NTFS/exFAT
/dev/sda2       630888446   976771071   172941313    5  Extended
/dev/sda5       630888448   959995903   164553728   83  Linux
/dev/sda6       959997952   976771071     8386560   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfd523fb1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sdb2          206848   976771071   488282112    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa6663233

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63    20466809    10233373+  27  Hidden NTFS WinRE
/dev/sdc2   *    20467712  1250263727   614898008    7  HPFS/NTFS/exFAT

[/INDENT]
**sudo blkid**[INDENT]/dev/sda1: UUID="2A9C291A9C28E255" TYPE="ntfs" 
/dev/sda5: UUID="452b163a-9a97-4d00-b45f-1f49e23aced5" TYPE="ext4" 
/dev/sda6: UUID="283c054b-30ce-4b14-aeae-08ae8e7a706c" TYPE="swap" 
/dev/sdb1: LABEL="System Reserved" UUID="22FC68E6FC68B5A7" TYPE="ntfs" 
/dev/sdb2: UUID="424C6B204C6B0E4B" TYPE="ntfs" 
/dev/sdc1: LABEL="PQSERVICE" UUID="44305AD5E49BED2A" TYPE="ntfs" 
/dev/sdc2: LABEL="FILES" UUID="AE08A61708A5DF19" TYPE="ntfs"
[/INDENT]
[B]
ls -l /dev/disk/by-uuid[/B] [INDENT]total 0
lrwxrwxrwx 1 root root 10 Mar 23 17:06 22FC68E6FC68B5A7 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Mar 23 17:06 283c054b-30ce-4b14-aeae-08ae8e7a706c -> ../../sda6
lrwxrwxrwx 1 root root 10 Mar 23 17:06 2A9C291A9C28E255 -> ../../sda1
lrwxrwxrwx 1 root root 10 Mar 23 17:06 424C6B204C6B0E4B -> ../../sdb2
lrwxrwxrwx 1 root root 10 Mar 23 17:06 44305AD5E49BED2A -> ../../sdc1
lrwxrwxrwx 1 root root 10 Mar 23 17:06 452b163a-9a97-4d00-b45f-1f49e23aced5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Mar 23 17:06 AE08A61708A5DF19 -> ../../sdc2

[/INDENT]
**cat /etc/initramfs-tools/conf.d/resume**[INDENT]RESUME=UUID=283c054b-30ce-4b14-aeae-08ae8e7a706c

[/INDENT]
**cat /etc/uswsusp.conf**[INDENT]cat: /etc/uswsusp.conf: No such file or directory

[/INDENT]
**cat /etc/default/grub**[INDENT]# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="rootdelay=60"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```
[/INDENT]

---

### Post by praseodym on 2014-03-23
sda6 is the SWAP partition:
```
 /dev/sda6: UUID="283c054b-30ce-4b14-aeae-08ae8e7a706c" TYPE="swap" 
```

Control```

cat /etc/fstab
```

S/H with the SWAP-partition.

Open the file:

```
gksudo gedit /etc/default/grub
```
and change the line

```
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
to
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash resume=UUID=283c054b-30ce-4b14-aeae-08ae8e7a706c"
```
Save, close the editor and run
```

sudo update-grub
```
Reboot and check S/H

---

### Post by spanner2 on 2014-03-23
Hi there, thanks for your continued support. When I put the first line in ( /dev/sda6: UUID="283c054b-30ce-4b14-aeae-08ae8e7a706c" TYPE="swap") Terminal returns, "/dev/sda6:: No such file or directory"

I thought I'd better stop and report that before going any further.

---

### Post by praseodym on 2014-03-23
That is not a command line, thats the output of one.

Check
```

cat /etc/fstab
```
first

---

### Post by spanner2 on 2014-03-23
No luck, I'm afraid. Same thing is still happening after waking it up.

---

### Post by bapoumba on 2014-03-23
@spanner2 : I have edited a couple of your posts to add [code] tags, please see here how it works : http://ubuntuforums.org/misc.php?do=bbcode
It does help readers when you have large terminal outputs to post, thanks.

---

### Post by praseodym on 2014-03-23
Have you checked the BIOS settings for the runlevels S4 or S3? Sometimes its named STR or similar.

---

### Post by spanner2 on 2014-03-24
I found a Suspend to RAM setting (STR?) in the BIOS, which was set to "Auto." The only other option for it was "Disable." I've left it at "Auto" for the time being.

---

### Post by praseodym on 2014-03-24
Which BIOS version is shown? Is there a new one available?

---

