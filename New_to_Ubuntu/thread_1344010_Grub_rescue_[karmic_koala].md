---
title: "Grub rescue [karmic koala]"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by dungun on 2009-12-02
Hello,

I'm using dual-boot with grub [karmic koala] version. right now i can't access my grub since i make new partition in windows.

here my fdisk - l 

omitting empty partition (5)

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe60be60b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5205    41809131    7  HPFS/NTFS
/dev/sda2   *        5206       38912   270751477+   f  W95 Ext'd (LBA)
/dev/sda5   ?      103773      273737  1365237833   9e  Unknown
/dev/sda6            6725        8091    10980396   83  Linux
/dev/sda7            8092        8358     2144646   82  Linux swap / Solaris
/dev/sda8            8359       10969    20972826   83  Linux
/dev/sda9           10970       13580    20972826   83  Linux
/dev/sda10          13581       20397    54757521    7  HPFS/NTFS
/dev/sda11          20398       38912   148721706    7  HPFS/NTFS

Partition table entries are not in disk order

*sda10 is new windows partition i make using "manage disk" in windows*

Here my step before posting this thread.

1. boot live cd :)
2. Open terminal >> sudo -i
3. fdisk -l 
4. mkdir /media/root
5  mount /dev/sda8 /media/root
6. ls /media/root

>>>output :

bin
boot
dev
etc
file
home
lib
lib64
lost+found
media
mnt
opt
proc
root
sbin
srv
success
sys
tmp
usr
var
windows

7. sudo grub-install --root-directory=/media/root /dev/sda8

output >>>

grub-probe: error: Cannot find a GRUB drive for /dev/sda8.  Check your device.map.

Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.

8. i'm blank please help me.

Thanks

dungun

---

### Post by oldfred on 2009-12-02
What is sda5? It is outside the parameters of the drive? 38913 cylinders

to fully understand you system set-up run this script. You can download from the liveCD.

Boot Info Script 0.37 courtesy of forum member meierfra 
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/) 
Instructions
  louieb's 
 [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
 [http://ubuntuforums.org/showthread.php?p=8279056#1](http://ubuntuforums.org/showthread.php?p=8279056#1)
  caljohnsmith
 [http://ubuntuforums.org/showpost.php?p=6725571&postcount=3](http://ubuntuforums.org/showpost.php?p=6725571&postcount=3) 
cd to directory saved to: 
chmod 755 boot_info_script037.sh 
sudo ./boot_info_script037.sh 
or as example if on desktop from liveCD download 
sudo bash ~/Desktop/boot_info_script*.sh 
This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by dungun on 2009-12-03
my partition is corrupted.

just clean install both xp and karmic

---

