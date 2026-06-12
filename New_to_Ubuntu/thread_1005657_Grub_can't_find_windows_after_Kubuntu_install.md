---
title: "Grub can't find windows after Kubuntu install"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by PlayWithFire on 2008-12-08
I am sure it's a simple fix, but i am very new to Linux. 

I installed Kubuntu, restarted the PC and it just went straight into windows. I checked to see that the Linux partition was present, restarted with the Live CD and setup grub though the command line. Now when i boot, i see grub with option to load kubuntu and windows. Kubuntu loads fine, but when trying to load XP, it says drive not found.

How can i configure grub to point to my XP installation?

---

### Post by caljohnsmith on 2008-12-08
How about first posting:
```
sudo fdisk -lu
```
And identify which is your Windows partition. We can work from there if you want.

---

### Post by PlayWithFire on 2008-12-08
here's the output of the command. I am guessing /dev/sda1 is my windows install. 

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes                               
Disk identifier: 0x373de4dc                                          

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63  1953536129   976768033+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000501

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x373de1dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *  3464576781  1610162855  1220276685+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdc2              36    83955747    41977856    0  Empty
Partition 2 does not end on cylinder boundary.
/dev/sdc3      2810839040  1980448561  1732288409    0  Empty
Partition 3 does not end on cylinder boundary.
/dev/sdc4               0    33488915    16744458   3b  Unknown
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/sdd: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3b293b29

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          63   244573559   122286748+   7  HPFS/NTFS
/dev/sdd2       244573560   488279609   121853025    5  Extended
/dev/sdd5       244573623   478287179   116856778+  83  Linux
/dev/sdd6       478287243   488279609     4996183+  82  Linux swap / Solaris

```

---

### Post by caljohnsmith on 2008-12-08
OK, how about downloading the attached "boot_info.sh.txt" file to your desktop, and do:
```
sudo sh ~/Desktop/boot_info.sh.txt
sudo xxd -l 2 -p /dev/sda
sudo xxd -l 2 -p /dev/sdd
sudo xxd -s 1049 -l 2 -p /dev/sdd
cat /boot/grub/menu.lst
```
Note that "-l" is a lowercase L, not a one; please post the output of all the above commands.

---

### Post by PlayWithFire on 2008-12-08
Thank you very much for helping me. Here's the output
```
pasha@Jasmine:~$ sudo sh ~/Desktop/boot_info.sh.txt                         
[sudo] password for pasha:                                                                                                                                               
sda1 ::XP:                                                                                                                                                               
sdc1 ::None:                                                                                                                                                             
sdc2 ::None:                                                                                                                                                             
sdc3 ::None:                                                                                                                                                             
sdc4 ::Grub:                                                                                                                                                             
sdd1 ::Grub:                                                                                                                                                             
sdd2 ::None:                                                                                                                                                             
sdd5 :ext3:None: /boot/grub/menu.lst /boot                                                                                                                               
sdd6 :swap:None:                                                                                                                                                         
pasha@Jasmine:~$ sudo xxd -l 2 -p /dev/sda                                                                                                                               
eb48                                                                                                                                                                     
pasha@Jasmine:~$ sudo xxd -l 2 -p /dev/sdd                                                                                                                               
eb48                                                                                                                                                                     
pasha@Jasmine:~$                                                                                                                                                         
pasha@Jasmine:~$ sudo xxd -s 1049 -l 2 -p /dev/sdd                                                                                                                       
04ff                                                                                                                                                                     
pasha@Jasmine:~$ cat /boot/grub/menu.lst                                                                                                                                 
# menu.lst - See: grub(8), info grub, update-grub(8)                                                                                                                     
#            grub-install(8), grub-floppy(8),                                                                                                                            
#            grub-md5-crypt, /usr/share/doc/grub                                                                                                                         
#            and /usr/share/doc/grub-doc/.                                                                                                                               

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.              
#                                                                            
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.                          
# WARNING: If you are using dmraid do not use 'savedefault' or your           
# array will desync and will not let you boot your system.                    
default         0                                                             

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).                                          
timeout         10                                                             

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu                                            

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the  
# command 'lock'                                                              
# e.g. password topsecret                                                     
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/                        
# password topsecret                                                          

#
# examples
#         
# title         Windows 95/98/NT/2000
# root          (hd0,0)              
# makeactive                         
# chainloader   +1                   
#                                    
# title         Linux                
# root          (hd0,1)              
# kernel        /vmlinuz root=/dev/hda2 ro
#                                         

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options     
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.  
## e.g. kopt=root=/dev/hda1 ro                                    
##      kopt_2_6_8=root=/dev/hdc1 ro                              
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro                        
# kopt=root=UUID=47264eed-b73f-4cef-995b-6798adf2bceb ro          

## default grub root device
## e.g. groot=(hd0,0)      
# groot=47264eed-b73f-4cef-995b-6798adf2bceb

## should update-grub create alternative automagic boot options
## e.g. alternative=true                                       
##      alternative=false                                      
# alternative=true                                             

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true                                 
##      lockalternative=false                                
# lockalternative=false                                      

## additional options to use with the default boot option, but not with the
## alternatives                                                            
## e.g. defoptions=vga=791 resume=/dev/hda5                                
# defoptions=quiet splash                                                  

## should update-grub lock old automagic boot options
## e.g. lockold=false                                
##      lockold=true                                 
# lockold=false                                      

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=                                                       

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0                                             

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single                     
# altoptions=(recovery mode) single                      

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the     
## alternative kernel options                               
## e.g. howmany=all                                         
##      howmany=7                                           
# howmany=all                                               

## should update-grub create memtest86 boot option
## e.g. memtest86=true                            
##      memtest86=false                           
# memtest86=true                                  

## should update-grub adjust the value of the default booted system
## can be true or false                                            
# updatedefaultentry=false                                         

## should update-grub add savedefault to the default options
## can be true or false                                     
# savedefault=false                                         

## ## End Default Options ##

title           Ubuntu 8.10, kernel 2.6.27-9-generic
uuid            47264eed-b73f-4cef-995b-6798adf2bceb
kernel          /boot/vmlinuz-2.6.27-9-generic root=UUID=47264eed-b73f-4cef-995b-6798adf2bceb ro quiet splash
initrd          /boot/initrd.img-2.6.27-9-generic
quiet

title           Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid            47264eed-b73f-4cef-995b-6798adf2bceb
kernel          /boot/vmlinuz-2.6.27-9-generic root=UUID=47264eed-b73f-4cef-995b-6798adf2bceb ro  single
initrd          /boot/initrd.img-2.6.27-9-generic

title           Ubuntu 8.10, kernel 2.6.27-7-generic
uuid            47264eed-b73f-4cef-995b-6798adf2bceb
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=47264eed-b73f-4cef-995b-6798adf2bceb ro quiet splash
initrd          /boot/initrd.img-2.6.27-7-generic
quiet

title           Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid            47264eed-b73f-4cef-995b-6798adf2bceb
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=47264eed-b73f-4cef-995b-6798adf2bceb ro  single
initrd          /boot/initrd.img-2.6.27-7-generic

title           Ubuntu 8.10, memtest86+
uuid            47264eed-b73f-4cef-995b-6798adf2bceb
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd1
title           Microsoft Windows XP Professional
root            (hd3,0)
savedefault
makeactive
map             (hd0) (hd3)
map             (hd3) (hd0)
chainloader     +1

pasha@Jasmine:~$
```

---

### Post by caljohnsmith on 2008-12-08
Do you happen to know which drive you are booting on start up? Also, it looks like you have sda and sdb in some sort of RAID setup? According to the commands you ran, your XP is installed on sda1, and also you have Grub installed to the MBR (Master Boot Record) of both the sda and sdd drives; thus I can't tell for sure which drive you are booting on start up.

We can work around that though, but it just means there are more possible combinations of Windows entries in Grub that might be correct for your setup. How about opening a terminal (konsole) and do:
```
kdesu kate /boot/grub/menu.lst
```
And then replace your existing Windows entry at the end of the file with:
```
title      Windows XP (hd0)
root       (hd0,0)
chainloader +1

title       Windows XP (hd1)
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title       Windows XP (hd2)
root       (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```
Then reboot, and try each of those Windows entries from the Grub menu; one of them should work, but if not, please let me know exactly what happens when you try each of them and we can work from there. Otherwise let me know how it goes. :)

---

### Post by PlayWithFire on 2008-12-09
Thank you very much, that did it!
I really appreciate your help

---

### Post by caljohnsmith on 2008-12-09
Glad to hear one of those Windows entries worked. Cheers and have fun with Windows and Kubuntu. :)

---

