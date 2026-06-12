---
title: "Harddrive is a mess; installed ubuntu, no grub!!"
date: 2011-01-08
forum: New to Ubuntu
---

### Post by adamogardner on 2011-01-08
I tried to install Windows7 today with an already cluttered hardrive.  I succeeded but lost ubuntu, so I reinstalled Ubuntu alonside the existing operating systems and lost Windows7,  I tried to reinstall windows 7 and there is nowhere on the partition to install it.  Now what?  

I'd like to have only two operating systems here;  Windows 7, and Ubuntu.  Thanks for your help.

---

### Post by adamogardner on 2011-01-08
1 character

---

### Post by adamogardner on 2011-01-08
I tried to fix it myself.  Rebooted it reads "no boot signature found in partition, operating system not found.  I know there are more operating systems than I want though.  Unfortunately I can't continue repairs until I have an operating system to work with.  Suggestions?
It won't boot off of disk either now.

---

### Post by coglist on 2011-01-08
can you post your system specs that you are using? not certain I will be able to help you, but if your computer isn't booting the grub bootloader, it may be an issue specific to your hardware. :popcorn:
 
I should be more specific on what should be posted.  system board model number if not a generic prebuilt system.  also confirm what version of ubuntu you are attempting to istall, ie 10.10 netbook etc.  I know there are issues if you try to install windows ontop of a system if you aren't careful, but usually installing ubuntu ontop of windows is easy.

---

### Post by amjjawad on 2011-01-08
> **adamogardner said:**
> Suggestions?

On my signature, check "Dual-Booting Guide".
It will tell you how to Dual-Boot with Windows. Don't worry about XP (in that guide), it should be the same concept.

If you have any question, let me know!

---

### Post by adamogardner on 2011-01-09
I think it's lucid lynx.  I don't know what those other things you asked for are.  I've had everything working on it already, so I seriously doubt it's hardware.
is there a command to get the info you need, or do I need to flip my laptop over?

---

### Post by adamogardner on 2011-01-09
Dual booting guide does not show my situation as described below.

---

### Post by adamogardner on 2011-01-09
Dual booting guide does not show my situation as described below.

---

### Post by kansasnoob on 2011-01-09
Are you able to boot any Live CD or Live USB?

We need to gather some info, specifically the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

But you'll obviously need to be able to run some Live media.

---

### Post by adamogardner on 2011-01-09
Okay,  I can't boot Windows,  I just booted Lucid though from the live disk.  I can attempt to install or...?

---

### Post by kansasnoob on 2011-01-09
> **adamogardner said:**
> Okay,  I can't boot Windows,  I just booted Lucid though from the live disk.  I can attempt to install or...?

Post the output requested in my last post.

---

### Post by mike555 on 2011-01-09
you might start gparted to see what you have ,it will show if you have Windows ntfs partition and/or ext4 linux partition ... maybe you could post a screenshot ..

---

### Post by adamogardner on 2011-01-09
sure,  but right now it wants to know if i want to install alongside other operating systems (there are too many) or instead of other operating systems.  Do I do that or run it live?  I'll try it live until I here otherwise.  be right back with info.

---

### Post by kansasnoob on 2011-01-09
> **adamogardner said:**
> sure,  but right now it wants to know if i want to install alongside other operating systems (there are too many) or instead of other operating systems.  Do I do that or run it live?  I'll try it live until I here otherwise.  be right back with info.

Just run the Live CD until we can see what you have.

---

### Post by adamogardner on 2011-01-09
okay,,says ive included 17 images but I'm limited to 8.  No idea what that means.  working on it.

---

### Post by adamogardner on 2011-01-09
it's not allowing me to post.
But I have the information you request.  something about the use of these being subject to an administrator.  I simply copied and pasted from gedit, so what's the problem?

---

### Post by kansasnoob on 2011-01-09
Here's some alternative instructions for the Boot Info Script:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

If you use code tags to post the output there should be zero "images".

---

### Post by adamogardner on 2011-01-09
Here's the first half:

!# /bin/bash
VERSION=0.55
DATE="February 15th, 2010"
#to use this script:
#
#     sudo bash boot_info_script055.sh
#or
#     su -
#     bash boot_info_script055.sh
#
#
### last-modified 
#
#author  Ulrich Meierfrankenfeld (aka meierfra.) 
# with  contributions from caljohnsmith
# (both members of ubuntuforums.org)
# and Gert Hulselmans
#
#hosted at: [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
# 
#The birth of the boot info script:
#   [http://ubuntuforums.org/showthread.php?t=837791](http://ubuntuforums.org/showthread.php?t=837791)
#
#Looks at all MBRs and identifies the boot loader. 
#   For Grub and Supergrub:  displays the controlling partition.
#   If the  MBR is unknown, displays the whole MBR.
#Looks at all  partitions:
#   Determines their type
#   Identifies their boot sectors.
#         For grub: displays the controlling partition and the offset
#         of the stage2 file as recorded in the boot sector.
#         For NTFS and Fat, examines the Boot Parameter Block for errors.
#   Identifies the operating system
#   Lists  boot programs.
#   Displays the partition table
#   Displays "blkid -c /dev/null"
#   Finds  boot directories and displays their contents.
#   Looks in "/" and "NST" for  bootpart codes  and displays the offset
#                and boot drive it is trying to chainload
#   Looks on "/" and "/NST" for stage1 files and displays the offset
#         and bootdrive of the stage 2  files is trying to chainload.
#   Displays  boot configuration files.
#   Is able to search LVM partitions if  the LVM2 package is install
#      ("apt-get install lvm2"  in debian based  distros)
#   Is able to search Linux Software Raid partitions (MD Raids) if
#       the "mdadm" package is installed.
#   If dmraid is installed, searches all raid drives, detected by dmraid.
#All information is written to the file "RESULTS.txt" in the
#    same folder as the script. But  when run from /bin, /sbin, /usr/bin,
#    or  other system folder the file "RESULTS.txt" is written to the
#    home directory of the user who runs this script.


###### Display version and date of the script when asked:
# ./boot_info_script -v
# ./boot_info_script -V
# ./boot_info_script --version 
if [ x"$1" = x'-v' ] || [ x"$1" = x'-V' ] || [ x"$1" = x'--version' ] ;
then 
    echo "boot_info_script version $VERSION"
    echo "Dated , $DATE"
    exit 0
fi 


###### Check if all necessary programs are available

Programs="
    awk
    basename
    blkid
    cat
    dd
    dirname
    expr
    fdisk
    filefrag
    fold
    grep
    hexdump
    losetup
    ls
    mkdir
    mount
    pwd
    rm
    sed
    sort
    umount
    wc
    whoami"

Check_Prog=1;

for Program in $Programs ; do

    if ! type $Program > /dev/null 2>&1 ; then
    echo \"$Program\" could not be found. >&2
    Check_Prog=0;
    fi
done

if [ $Check_Prog -eq 0 ];
then
   echo "Please install the  missing program(s) and run boot_info_script again." >&2
   exit 1;
fi;




###### check whether user is root

if [ $(whoami) != "root" ];
then 
   echo  Please use \"sudo\" or become \"root\" to run this script. >&2;
   exit 1;
fi;  

########  List of folders which might contained files used for chainloading
Boot_Codes_Dir="
    /
    /NST/
    "
#################  List of folders whose content will be displayed
################# Since all the important files in these folder are already displayed
################# it doesn't seem necessary to display the contents of these folders.
#Boot_Dir="
#   /Boot
#    /boot
#    /BOOT
#    /boot/grub
#    /grub
#    /ubuntu/disks
#    /ubuntu/disks/boot/
#    /ubuntu/disks/boot/grub
#    /ubuntu/disks/install/boot
#    /ubuntu/disks/boot/grub
#    /NST
#    "


##############  List of files whose names will be displayed (if they exists)
Boot_Prog_Normal="
     /bootmgr /BOOTMGR
     /boot/bcd /BOOT/bcd /Boot/bcd  /boot/BCD /BOOT/BCD  /Boot/BCD
     /Windows/System32/winload.exe /WINDOWS/system32/winload.exe /WINDOWS/SYSTEM32/winload.exe /windows/system32/winload.exe
     /Windows/System32/Winload.exe /WINDOWS/system32/Winload.exe /WINDOWS/SYSTEM32/Winload.exe /windows/system32/Winload.exe
     /grldr /GRLDR
     /ntldr /NTLDR
     /NTDETECT.COM    /ntdetect.com
     /NTBOOTDD.SYS    /ntbootdd.sys
     /wubildr.mbr    /ubuntu/winboot/wubildr.mbr
     /wubildr    /ubuntu/winboot/wubildr
     /ubuntu/disks/root.disk
     /ubuntu/disks/home.disk
     /ubuntu/disks/swap.disk
     /core.img   /grub/core.img     /boot/grub/core.img
     /boot/map      /map
     /DEFAULT.MNU /default.mnu
     /IO.SYS /io.sys
     /MSDOS.SYS /msdos.sys 
     /COMMAND.COM /command.com
     "
Boot_Prog_Fat="
      /bootmgr
     /boot/bcd
     /Windows/System32/winload.exe
     /grldr
     /ntldr 
     /NTDETECT.COM 
     /NTBOOTDD.SYS
     /wubildr.mbr 
     /wubildr  
     /ubuntu/winboot/wubildr
     /ubuntu/winboot/wubildr.mbr
     /ubuntu/disks/root.disk
     /ubuntu/disks/home.disk
     /ubuntu/disks/swap.disk
     /core.img   /grub/core.img     /boot/grub/core.img
     /boot/map      /map
     /DEFAULT.MNU
     /IO.SYS 
     /MSDOS.SYS
     /COMMAND.COM
     "



############### List of files whose contents will be displayed.
Boot_Files_Normal="
    /boot/grub/menu.lst /grub/menu.lst  /NST/menu.lst    /menu.lst
    /grub.cfg    /grub/grub.cfg    /boot/grub/grub.cfg
    /ubuntu/disks/boot/grub/menu.lst /ubuntu/disks/install/boot/grub/menu.lst /ubuntu/winboot/menu.lst
    /boot/grub/grub.conf    /grub/grub.conf    /grub.conf
    /boot.ini  /BOOT.INI
    /etc/fstab
    /etc/lilo.conf  /lilo.conf
    "

Boot_Files_Fat="
    /boot/grub/menu.lst /grub/menu.lst  /NST/menu.lst    /menu.lst
    /grub.cfg    /grub/grub.cfg    /boot/grub/grub.cfg
    /ubuntu/disks/boot/grub/menu.lst /ubuntu/disks/install/boot/grub/menu.lst /ubuntu/winboot/menu.lst
    /boot/grub/grub.conf    /grub/grub.conf    /grub.conf
    /boot.ini  
    /etc/fstab
    /etc/lilo.conf  /lilo.conf
    "

############### List of files whose end point (in GB) will be displayed.
GrubError18_Files="
    boot/grub/menu.lst    grub/menu.lst    menu.lst /NST/menu.lst
    ubuntu/disks/boot/grub/menu.lst
    boot/grub/grub.conf    grub/grub.conf    grub.conf
    grub.cfg    grub/grub.cfg    boot/grub/grub.cfg
    core.img    grub/core.img   boot/grub/core.img
    boot/grub/stage2    grub/stage2    stage2
    boot/vmlinuz*  vmlinuz*    ubuntu/disks/boot/vmlinuz*
    boot/initrd*  initrd*    ubuntu/disks/boot/initrd*
    boot/kernel*.img
    initramfs* boot/initramfs*
    "


#######  Directory containing the script.

Dir=$(cd "$(dirname "$0")";pwd);

# Set $Dir to the home folder of the current user if the script is in one of the
# system folders
# This allows placement of the script in /bin, /sbin, /usr/bin, ...
# while still having a normal location to write the output file.
for systemdir in /bin /boot /cdrom /dev /etc /lib /lost+found /opt /proc /sbin /selinux /srv /sys /usr /var; do
    if [ $(expr "$Dir" : $systemdir) -ne 0 ]; then
	Dir="$HOME"
	break
    fi
done

########  To avoid overwriting existing files, look for a non-existing file 
########  RESULT.txt RESULTS1.txt  RESULTS2.txt ... 

LogFile="${Dir}/RESULTS"
while ( [ -e "${LogFile}${j}.txt" ] )
    do 
       if [ "j" = "" ]; then j=0; fi;
       j=$((j+1));
      wait;
    done
LogFile="${LogFile}${j}.txt"  #### The RESULTS file.

######  Redirect stdout to RESULT File
#exec 6>&1   
#exec > "$LogFile"

########### Create previously non-existing  folder of the form
##########  /tmp/BootInfo  /tmp/BootInfo1, /tmp/BootInfo2 ... 

Folder=/tmp/BootInfo
i=0;
while (! mkdir ${Folder}${i} 2>/dev/null)
    do  
      i=$((i+1));
      wait;
    done
Folder=${Folder}${i}

cd $Folder
Log=$Folder/Log                 #File to record the summary.
Log1=$Folder/Log1               #  Most of the information which is not part of
                                #the summary is recorded in this file.
Error_Log=$Folder/Error_Log     #  File to catch all unusal Standar Errors 
Trash=$Folder/Trash             #  File to catch all usual Standard Errors
                                #     these messagges will not be included in the RESULTS       
Mount_Error=$Folder/Mount_Error # File to catch Mounting Errors
Unknown_MBR=$Folder/Unknown_MBR # File to record all unknown MBR and Boot sectors. 
Tmp_Log=$Folder/Tmp_Log         # File to temporarily hold some information.
PartitionTable=$Folder/PT       # File to store the Partition   Table
FakeHardDrives=$Folder/FakeHD   # File to list devices which seem to have  no corresponding drive.
BLKID=$Folder/BLKID             # File to store the output of blkid
exec 2>$Error_Log               #Redirect all standard error to the file Error_Log

All_Hard_Drives=$(ls /dev/hd? /dev/sd? 2>>$Trash );   ### List of all Hard drives.


if type dmraid >>$Trash 2>>$Trash;
then
  InActiveDMRaid=$(dmraid -si -c);
  if  [ "$InActiveDMRaid" = "no raid disks" ];
  then 
      InActiveDMRaid="";
  fi;
  if  [ "$InActiveDMRaid" != "" ];
  then
      dmraid -ay $InActiveDMRaid >>$Trash;
  fi;
  if [ "$(dmraid -sa -c)" != "no raid disks" ];
  then
       All_DMRaid=$(dmraid -sa -c|awk '{print "/dev/mapper/"$0}');
       All_Hard_Drives=${All_Hard_Drives}" "${All_DMRaid};
  fi;   
fi;

####Arrays to hold information about Partitions: name, starting sector, ending sector, size in sector, Partition Type, Filesystem typ, UUID, Kind(Logical, Primary, Extended), HardDrive, boot flag,  parent (for logical partitions), label, system(the partition id according the partition table), the device associate to the partition.

declare -a NamesArray StartArray EndArray SizeArray TypeArray  FileArray UUIDArray KindArray DriveArray BootArray ParentArray LabelArray SystemArray DeviceArray  


#####Arrays to hold information about the harddrives.
declare -a HDName  FirstPartion LastPartition  HDSize HDMBR HDHead HDTrack HDCylinder HDPT HDStart HDEnd HDUUID;

####Array for Hard drives formated as Filesystem 
declare -a FilesystemDrives;


PI=-1 ## Counter for the identification number of a partition. (each partition gets unique number)
HI=0 ## Counter for the identification number of a hard drive. (each hard drive gets unique number)
PTFormat='%-10s %4s%14s%14s%14s %3s %s\n';  ### standard format to use for Partition table,


####  fdisk -s seems to malfunction sometimes. So use sfdisk -s if available
function fdisks (){
if type sfdisk >>$Trash 2>>$Trash
then
   sfdisk -s "$1" 2>>$Trash;
else
   fdisk -s "$1" 2>>$Trash;
fi;
}
   


#####  A function which checks whether a file is on a mounted partition 
MountPoints=$(mount | grep -e ^/dev |awk '{print $3}' |grep -v  ^/$); ##list of mountpoints for devices
 
function FileNotMounted (){
local File=$1 curmp=$2;      
for mp in $MountPoints; 
do 
 if [ $(expr match "$File" "$mp""/" ) -ne 0 ] && [ "$mp" != "$curmp" ]
 then 
   return 1; 
 fi;
done;
return 0;
}

##### A function which converts the  two digit hexcode of a partition type 
# The following list is taken from sfdisk -T  and 
#  [http://www.win.tue.nl/~aeb/partitions/partition_types-1.html](http://www.win.tue.nl/~aeb/partitions/partition_types-1.html)
#  work in progress
function HexToSystem () {
local type=$1 system
case $type in 
0) system="Empty";;
1) system="FAT12";;
2) system="XENIX root";;
3) system="XENIX usr";;
4) system="FAT16 <32M";;
5) system="Extended";;
6) system="FAT16";;
7) system="HPFS/NTFS";;
8) system="AIX";;
9) system="AIX bootable";;
a) system="OS/2 Boot Manager";;
b) system="W95 FAT32";;
c) system="W95 FAT32 (LBA)";;
e) system="W95 FAT16 (LBA)";;
f) system="W95 Ext d (LBA)";;
10) system="OPUS";;
11) system="Hidden FAT12";;
12) system="Compaq diagnostics";;
14) system="Hidden FAT16 <32M";;
16) system="Hidden FAT16";;
17) system="Hidden HPFS/NTFS";;
18) system="AST SmartSleep";;
1b) system="Hidden W95 FAT32";;
1c) system="Hidden W95 FAT32 (LBA)";;
1e) system="Hidden W95 FAT16 (LBA)";;
24) system="NEC DOS";;
27) system="Hidden HPFS/NTFS";;
32) system="NOS";;
35) system="JFS on OS2";;
38) system="Theos";;
39) system="Plan 9";;
3a) system="Theos";;
3b) system="Theos Extended";;
3c) system="PartitionMagic recovery";;
40) system="Venix 80286";;
41) system="PPC PReP Boot";;
42) system="SFS";;
45) system="Boot-US boot manager";;
4d) system="QNX4.x";;
4e) system="QNX4.x 2nd part";;
4f) system="QNX4.x 3rd part";;
50) system="OnTrack DM";;
51) system="OnTrack DM6 Aux1";;
52) system="CP/M";;
53) system="OnTrack DM6 Aux3";;
54) system="OnTrackDM6";;
55) system="EZ-Drive";;
56) system="Golden Bow";;
5c) system="Priam Edisk";;
61) system="SpeedStor";;
63) system="GNU HURD or SysV";;
64) system="Novell Netware 286";;
65) system="Novell Netware 386";;
70) system="DiskSecure Multi-Boot";;
75) system="PC/IX";;
80) system="Old Minix";;
81) system="Minix / old Linux";;
82) system="Linux swap / Solaris";;
83) system="Linux";;
84) system="OS/2 hidden C: drive";;
85) system="Linux extended";;
86) system="NTFS volume set";;
87) system="NTFS volume set";;
88) system="Linux plaintext";;
8e) system="Linux LVM";;
93) system="Amoeba/Accidently Hidden Linux";;
94) system="Amoeba BBT";;
9f) system="BSD/OS";;
a0) system="IBM Thinkpad hibernation";;
a5) system="FreeBSD";;
a6) system="OpenBSD";;
a7) system="NeXTSTEP";;
a8) system="Darwin UFS";;
a9) system="NetBSD";;
ab) system="Darwin boot";;
af) system="HFS";;
b0) sytem="Boot Star";;
b1 | b2 | b3 | b4 | b6) system="SpeedStor";; 
b7) system="BSDI fs";;
b8) system="BSDI swap";;
bb) system="Boot Wizard hidden";;
bc) system="Acronis BackUp";;
be) system="Solaris boot";;
bf) system="Solaris";;
c0) system="CTOS";;
c1) system="DRDOS/sec (FAT-12)";;
c2) system="Hidden Linux/PowerBoot";;
c3) system="Hidden Linux Swap /PowerBoot";;
c4) system="DRDOS/sec (FAT-16 < 32M)";;
c6) system="DRDOS/sec (FAT-16)";;
c7) system="Syrinx";;
cb) system="DR-DOS  FAT32 (CHS)";;
cc) system="DR-DOS  FAT32 (LBA)";;
cd) system="CTOS Memdump?";;
ce) system="DR-DOS FAT16X (LBA)";;
cf) system=" DR-DOS EXT DOS (LBA)";;
d0) system=" REAL/32 secure big partition";;
da) system="Non-FS data";;
db) system="CP/M / CTOS / ...";;
dd) system="Dell Media Direct";;
de) system="Dell Utility";;
df) system="BootIt";;
e1) system="DOS access";;
e3) system="DOS R/O";;
e4) system="SpeedStor";;
eb) system="BeOS fs";;
ee) system="GPT";;
ef) system="EFI (FAT-12/16/32)";;
f0) system="Linux/PA-RISC boot";;
f1) system="SpeedStor";;
f4) system="SpeedStor";;
f2) system="DOS secondary";;
fb) system="VMware VMFS";;
fc) system="VMware VMKCORE";;
fd) system="Linux raid autodetect";;
fe) system="LANstep";;
ff) system="BBT";;
 *) system="Unknown";;
esac;
echo $system;
}

##### Function to convert GPT's Partition Type.
####  ABCDEFGH-IJKL-MNOP-QRST-UVWXYZabcdef is stored as
####  GHEFCDAB-KLIJ-OPMN-QRST-UVWXYZabcdef (without the dashes)
function UUIDToSystem() {
local type=$1 system
case $type in
    00000000000000000000000000000000)  system="Empty";;
    41ee4d02e733d3119d690008c781f39f)  system="MBR partition scheme";;
    28732ac11ff8d211ba4b00a0c93ec93b)  system="System/Boot Partition";;
    a2a0d0ebe5b9334487c068b6b72699c7)  system="Linux or Data";; 
    6dfd5706aba4c44384e50933c84b4f4f)  system="Linux Swap";;
    16e3c9e35c0bb84d817df92df00215ae)  system="Microsoft Windows";;
    79d3d6e607f5c244a23c238f2a3df928)  system="LVM";;
    005346480000aa11aa1100306543ecac)  system="HFS+";;
    4861682149646f6e744e656564454649)  system="Bios Boot Partition";;
                                   *)  system="-";
                                       echo Unknown GPT Partiton Type>>$Unknown_MBR;
                                       echo  $type >>$Unknown_MBR;;   
esac;
echo $system;
   }

##### Function which insert a comma every  third digit of a number
function InsertComma () {
echo $1 |sed -e :a -e 's/\(.*[0-9]\)\([0-9]\{3\}\)/\1,\2/;ta'
}

##### Function to read 4 bytes starting at $1 of device $2 and convert to decimal.
function Read4Bytes () {
echo $(hexdump -v -s  $1  -n 4 -e '4 "%u"'  $2);
}

##### Function to read 8 bytes starting at $1 of device $2 and convert to decimal.
function Read8Bytes () {
local start=$1 device=$2;
local first4 second4;
first4=$(hexdump -v -s  $start  -n 4 -e '4 "%u"'  $device);
second4=$(hexdump -v -s  $((start+4))  -n 4 -e '4 "%u"'  $device);
echo $((second4*1073741824+first4));
}

#### Functions to pretty print blkid output ######
BlkidFormat='%-16s %-38s %-10s %-30s\n'
BlkidTag (){
echo $(blkid -c /dev/null -s $2 -o value $1 2>>$Trash)
}

PrintBlkid (){
local part=$1;
if  [  "$(blkid -c /dev/null $part  2>$Tmp_Log)"  != "" ];
then
printf "$BlkidFormat" "$part"  "$(BlkidTag $part UUID)"  "$(BlkidTag  $part TYPE)" "$(BlkidTag $part LABEL)">>$BLKID;
else blkid  -p "$part"  2>&1 |grep "$part" >>$BLKID; #blkid -p is not avaible all all systems. This contructs makes sure the "usage" message is not displayed, but catches the "ambivalent" error.
fi;
}


## Reads and display the  a partition table of an extended partitons    ###########
#############  and check the partition  check for errors         #####################
#  This function can be applied iteratively  to read the extended partiton table           
# Variable 1:  HI of hard drive 
# Variable 2:  Start Sector of the extended Partition,
# Variable 3:  Number of partitions in table (4 for regular PT, 2 for logical
# Variable 4:  File for storing the partitions table.
# Variable 5:  Format to use for displaying the partition table.  
# Variable 6:  PI of the primary extended partition containing the extended partition.
#              ( equals ""  for hard drive)
# Variable 7:  Last Linux Index assigned (the number in sdXY).

ReadPT (){
local HI=$1 StartEx=$2   N=$3 PT_file=$4 format=$5  EPI=$6 Base_Sector  
local   LinuxIndex=$7  boot  size   start end type drive system;
local i=0  boot_hex label limit MBRSig
drive=${HDName[$HI]};
limit=${HDSize[$HI]};
$(dd if=$drive skip=$StartEx of=$Tmp_Log count=1 2>>$Trash);
MBRSig=$(hexdump -v -s 510  -n 2 -e '"%x"'  $Tmp_Log);
[[ "$MBRSig" != "aa55" ]]  && echo  Invalid MBR Signature found >> $PT_file;
if [[ $StartX -lt $limit ]];
then  # set Base_Sector to 0 for HardDrive, and to the start
      # sector  of primary extended partition otherwise
    [[ "$EPI" = "" ]] && Base_Sector=0 || Base_Sector=${StartArray[$EPI]}
    for (( i=0; i < N; i++ ));
    do
	$(dd if=$drive skip=$StartEx of=$Tmp_Log count=1 2>>$Trash);
        boot_hex=$(hexdump -v -s  $((446+16*i))  -n  1 -e '"%02x"'  $Tmp_Log)
	case $boot_hex  in
	    00) boot=" ";;
	    80) boot="* ";;
	    *) boot="?";;
	esac;
	start=$(hexdump -v -s  $((454+16*i))  -n 4 -e '4 "%u"'  $Tmp_Log);
	size=$(hexdump -v -s  $((458+16*i))  -n 4 -e '4 "%u"'  $Tmp_Log);
	type=$(hexdump -v  -s  $((450+16*i))  -n 1 -e '4 "%x"' $Tmp_Log);
	if  [[ $size != 0 ]];
	then
	    if  [[ ( "$type" = "5" || "$type" = "f" )  && $Base_Sector != 0 ]];
	    then
		start=$((start+Base_Sector))  #start sector of an extended partition is 
                # relative to the start sector of an primary extended partition.
               if [[  $i = 0 ]];
                   then
                      echo "Extended  partition  linking to another extended partition" >>$PT_file;
                   fi;
		ReadPT $HI $start  2  $PT_file "$format"  $EPI $LinuxIndex;
	    else  
		((PI++))  
		if  [[ "$type" = "5" || "$type" = "f" ]];
		then
                    KindArray[$PI]="E";
		else
		    start=$((start+StartEx)); #Start sector of a logical partition is
            # relative to the start sector of directly assocated  extented partition.
		    [[ $Base_Sector = 0 ]] && KindArray[$PI]="P" || KindArray[$PI]="L";
		fi;
		LinuxIndex=$((LinuxIndex+1));
		end=$((start+size-1));
		[[ "${HDPT[$HI]}"  = "BootIt"  ]] &&  label="${NamesArray[$EPI]}""_" || label=$drive;
		system=$(HexToSystem $type)

		printf "$format" "$label$LinuxIndex" "$boot" $(InsertComma $start) "$(InsertComma $end)"  "$(InsertComma $size)"  "$type" "$system" >> $PT_file;
		NamesArray[$PI]="$label"$LinuxIndex;
		StartArray[$PI]=$start;
		EndArray[$PI]=$end;
		TypeArray[$PI]=$type;
		SystemArray[$PI]="$system";
		SizeArray[$PI]=$size;
		BootArray[$PI]="$boot";
		DriveArray[$PI]=$HI;
		ParentArray[$PI]=$EPI;
                ( [[ "$EPI" = "" ]] || [[ ${DeviceArray[$EPI]} != "" ]] ) && DeviceArray[$PI]=$drive$LinuxIndex; 

		if [[ "$type" = "5" || "$type" = "f" ]];
		then
                      ReadPT $HI $start  2  $PT_file "$format"  $PI 4;
		fi;
	    fi;
       
	elif [[ $Base_Sector != 0  &&  $i = 0  ]];
	then
	    echo "Empty Partition">>$PT_file;
	else 
	    LinuxIndex=$((LinuxIndex+1));
	fi;
    done;
else
    echo "EBR refers to a  location outside the Hard drive" >>$PT_file;
fi;  
}
############### Read partition table of type GPT (GUID, EFI)##########################
######  Variable 1:  HI of hard drive
######  Variable 2:  File to store the PartitionTable
function ReadEFI() {
    local HI=$1 drive file=$2 Size N=0 i=0  format Label PRStart Start End  Type Size System;
    drive="${HDName[$HI]}";
    format='%-10s %14s%14s%14s %s\n';
    printf "$format"  Partition Start End Size  System >> $file;
    HDStart[$HI]=$(Read8Bytes  552   $drive);
      HDEnd[$HI]=$(Read8Bytes  560   $drive);
     HDUUID[$HI]=$(hexdump -v -s 568   -n 16 -e '/1 "%02x"'  $drive); 
         PRStart=$(Read8Bytes  584    $drive);
               N=$(Read4Bytes  592   $drive);
          PRStart=$((PRStart*512));
          PRSize=$(Read4Bytes 596    $drive);
    for (( i = 0; i< N; i++ ))
    do
        Type=$(hexdump -v -s $((PRStart+PRSize*i))  -n 16 -e '/1 "%02x"'  $drive);
    if [ "$Type" != "00000000000000000000000000000000" ];
    then
        ((PI++))
        Start=$(Read8Bytes $((PRStart+32+PRSize*i))   $drive);
	  End=$(Read8Bytes $((PRStart+40+PRSize*i))   $drive);
        Size=$((End-Start+1));
        System=$(UUIDToSystem $Type);
        Label=$drive$((i+1));
        printf "$format"  "$Label"  "$(InsertComma $Start)" "$(InsertComma $End)" "$(InsertComma $Size)"  "$System"  >>$file;
        NamesArray[$PI]=$Label;
        DeviceArray[$PI]=$Label;
        StartArray[$PI]=$Start;
        TypeArray[$PI]=$Type;
        SizeArray[$PI]=$Size;
        SystemArray[$PI]=$System;
        EndArray[$PI]=$End;
        DriveArray[$PI]=$HI;
        KindArray[$PI]="P";
        ParentArray[$PI]=""; 
     fi;        
     done;
}

############### Read the Master Partition Table of  BootIt NG##########################
######  Variable 1:  HI of hard drive
######   Variable 2:  File to store the MPT.
function ReadEMBR() {
    local HI=$1 drive MPT_file=$2 Size N=0 i=0  BINGIndex  Label   Start End  Type BINGUnknown format Size System StoredPI FirstPI=FirstPartition[$1] LastPI=$PI New;
    drive="${HDName[$HI]}";
    format='%-18s %4s%14s%14s%14s %3s %-15s %3s %2s\n';
    printf "$format"  Partition Boot Start End Size Id System  Ind "?">> $MPT_file; 
    N=$(hexdump -v -s 534  -n 1 -e  '"%u"' $drive); 
    while [[ $i -lt "$N" ]]
	do
        New=1;
        BINGUnknown=$(hexdump -v -s  $((541+28*i))  -n 1 -e '"%x"'  $drive)
	Start=$(hexdump -v -s  $((542+28*i))  -n 4 -e '4 "%u"'  $drive);
	  End=$(hexdump -v -s  $((546+28*i))  -n 4 -e '4 "%u"'  $drive);
	BINGIndex=$(hexdump -v -s  $((550+28*i))  -n 1 -e '"%u"'  $drive);
	Type=$(hexdump -v -s  $((551+28*i))  -n 1 -e '"%x"'  $drive);
        Size=$((End-Start+1));
	Label=$(hexdump -v -s  $((552+28*i))  -n 15 -e '"%_u"'  $drive| sed -e  s/nul[^$]*//);
        System=$(HexToSystem $Type);
        printf "$format"  "$Label" "-" "$(InsertComma $Start)" "$(InsertComma $End)" "$(InsertComma $Size)" "$Type" "$System"  "$BINGIndex" "$BINGUnknown">>$MPT_file;
         StoredPI=$PI;
         for ((j = FirstPI; j<=LastPI; j++ ));
           do
              if (( ${StartArray[$j]} == $Start ));
	      then 
                    PI=$j;
                    New=0; 
                    break;
              fi;
           done;
         
         if (( $New  == 1 ));
         then
           ((PI++));
           StoredPI=$PI;
           StartArray[$PI]=$Start;
           TypeArray[$PI]=$Type;
           SizeArray[$PI]=$Size;
           SystemArray[$PI]=$System;
           EndArray[$PI]=$End;
           DriveArray[$PI]=$HI;
         fi;
         NamesArray[$PI]=$Label;
  
         if [[ $Type = "f" || $Type = "5" ]];
	    then
                 KindArray[$PI]="E";
                 ParentArray[$PI]=$PI;
		 ReadPT $HI  $Start  2  $MPT_file "$format"  $PI  4 ;  
            else
                KindArray[$PI]="P";
                ParentArray[$PI]="";
	    fi;
          PI=$StoredPI;
         ((i++));
       	done;
}

#################   Check partition table for errors  ################################
###  
###  This function checks whether any two partitions  overlap
###  and the logical partitions are inside the extended partition.
###  Variable 1:        PI of First partition to consider
###  Variable 2:        PI of Last Partition to consider
###  Variable 3:        File for the error messages.
###  Variable 4:        HI of containing hard drive
 CheckPT () {
    local  first=$1 last=$2 file=$3;  hi=$4;
    local  Si Ei Sj Ej Ki  Kj i j k cyl track head cyl_bound sec_bound
    cyl=${HDCylinder[$hi]};
    track=${HDTrack[$hi]};
    head=${HDHead[$hi]};
    cyl_bound=$((cyl*track*head));
    sec_bound=${HDSize[$hi]};
    for (( i=$first; i <= last; i++ ));
    do
         Si=${StartArray[$i]};
         Ei=${EndArray[$i]};
         Ki=${KindArray[$i]};
         Ni=${NamesArray[$i]};
         if [[ "$Ei" -gt "$sec_bound"  ]];
	 then
	     echo $Ni  ends after the last sector of ${HDName[$hi]}>>$file;
         elif  [[ "$Ei" -gt "$cyl_bound"  ]]
	 then
	     echo $Ni ends after the last cylinder of ${HDName[$hi]}>>$Trash;
         fi;
         if [[ $Ki = "L" ]];
	 then
	     k=${ParentArray[$i]};
            Sk=${StartArray[$k]};
            Ek=${EndArray[$k]};
            Nk=${NamesArray[$k]};
            [[ $Si -le $Sk || $Ei -gt $Ek ]] &&  echo  the logical partition  $Ni is not contained in the extended partition  $Nk>>$file;
         fi;
         for (( j = i+1; j <= last; j++ ));
	 do 
            Sj=${StartArray[$j]};
            Ej=${EndArray[$j]};
            Kj=${KindArray[$j]};
            Nj=${NamesArray[$j]};
            [[ !( ( $Ki = "L" && $Kj = "E"  )  || ( $Ki = "E" && $Kj = "L"  ) ) && ( ( $Si -lt $Sj &&   $Sj  -lt $Ei )  || ($Sj  -lt $Si && $Si -lt $Ej ) )]] && echo   $Ni overlaps with   $Nj >>$file;
          done;
    done
}

#############################################################################################
##########  Determine the embeded location of stage 2  in a stage 1 file,
##########  look  for the stage 2 and, if found, determine the
#########$  the location and the path of the embedded menu.lst

stage2_loc (){
  local stage1=$1 hi;
  offset=$(hexdump -v -s 68 -n 4 -e '4 "%u"' $stage1 2>>$Trash);
  dr=$(hexdump -v -s 64 -n 1 -e '"%d"' $stage1);
  pa="T"
  Grub_Version="";
  for hi in ${!HDName[@]};
  do
     hdd=${HDName[$hi]};
     if [ $offset -lt  ${HDSize[hi]}  ];
     then
	 tmp=$(dd if=$hdd skip=$offset count=1 2>>$Trash | hexdump -v    -n 4 -e '"%x"');
         if [[ "$tmp" = 3be5652 || "$tmp" =  bf5e5652  ]];  ###  If stage2 files was found.
         then
              dd if=$hdd skip=$((offset+1)) count=1 of=$Tmp_Log 2>>$Trash;
              pa=$(hexdump -v  -s 10  -n 1 -e '"%d"' $Tmp_Log);
              stage2_hdd=$hdd;
              Grub_String=$(hexdump -v -s 18 -n 94 -e '"%_u"' $Tmp_Log);
              Grub_Version=$(echo $Grub_String|sed -e  s/nul[^$]*//);
              BL=$BL$Grub_Version;
              menu=$(echo $Grub_String |sed -e  s/[^\/]*// -e s/nul[^$]*//);
              menu=${menu%% *};
         fi;
     fi;
 done;
 dr=$((dr-127))
 Stage2_Msg=$(echo  looks at sector $offset )        
 if [ "$dr" = 128 ];
 then
      Stage2_Msg=$(echo $Stage2_Msg of the same hard drive) 
 else
      Stage2_Msg=$(echo $Stage2_Msg on boot drive \#$dr)
 fi;
 Stage2_Msg=$(echo $Stage2_Msg for the stage2 file);
                    
 if [ "$pa" = "T"  ]   #### no stage 2 file found.
 then
      Stage2_Msg=$(echo $Stage2_Msg, but no stage2 files can be found at this location.); 
 else
     pa=$((pa+1))
     Stage2_Msg=$(echo $Stage2_Msg.  A stage2 file is at  this location on $stage2_hdd.  Stage2 looks on )                       
     if [ "$pa" = 256 ];
     then
         Stage2_Msg=$(echo $Stage2_Msg the same partition) 
     else
         Stage2_Msg=$(echo $Stage2_Msg  partition \#$pa )
     fi;
     Stage2_Msg=$(echo $Stage2_Msg for  $menu.)
  fi;
}
#######################################################################################

#############################################################################################
##########  Determine the embeded location of core.img  for a Grub2 boot.img file,
##########  look  for the core.img and,  the path of the Grub Folder.
#############################################################################

core_loc (){
  local stage1=$1  grub2_version=$2  hi offset_loc dr_loc dir_loc;
  case $grub2_version in
  1.96) offset_loc=68;  dr_loc=76; dir_loc=32;;
  1.97) offset_loc=92;  dr_loc=91; dir_loc=28;;
  esac;
  offset=$(hexdump -v -s $offset_loc -n 4 -e '4 "%u"' "$stage1" 2>>$Trash);
  dr=$(hexdump -v -s $dr_loc -n 1 -e '"%d"' "$stage1");
  pa="T"
    for hi in ${!HDName[@]};
  do
     hdd=${HDName[$hi]};
     if [ $offset -lt  ${HDSize[hi]}  ];
     then
	 tmp=$(dd if="$hdd" skip=$offset count=1 2>>$Trash | hexdump -v    -n 4 -e '"%x"');
         if [ "$tmp" = 1bbe5652 ];  ###  If conf.img  file was found.
         then
              dd if=$hdd skip=$((offset+1)) count=1 of=$Tmp_Log 2>>$Trash;
              pa=$(hexdump -v  -s 20  -n 1 -e '"%d"' $Tmp_Log);
              core_hdd=$hdd;
	      Grub_String=$(hexdump -v -s $dir_loc -n 64 -e '"%_u"' $Tmp_Log);
              Core_Dir=$(echo  $Grub_String | sed s/nul[^$]*//);
         fi;
     fi;
 done;
 Core_Msg=$(echo  looks at sector $offset of the same hard drive for core.img) 

 if [ "$pa" = "T"  ]   
 then  #### core.img not  found.
     Core_Msg=$(echo $Core_Msg, but core.img can not be found at this location.); 
 else  #### core.img  found.            
     pa=$((pa+1))
     Core_Msg=$(echo $Core_Msg,  core.img is  at this location on $core_hdd and looks  )                       
     if [ "$pa" = 255 ];
     then
         Core_Msg=$(echo $Core_Msg for $Core_Dir.) 
     else
         Core_Msg=$(echo $Core_Msg on  partition \#$pa  for  $Core_Dir.)
     fi;
  
  fi;
}
#####################################

---

### Post by adamogardner on 2011-01-09
here's some more.  won't let me post it all:
      Core_Msg=$(echo $Core_Msg on  partition \#$pa  for  $Core_Dir.)
     fi;
  
  fi;
}
#######################################################################################

###############  Get_Partition_Info search a partition for information relevant for booting.
####Variables:
####  log         $1  local version of RESULT.txt####  log1        $2  local version of log1
####  part        $3  device for the partition
####  name        $4  descriptive name for the partition
####  mountname   $5  path where  partition will be mounted.
###   kind        $6  kind of the partition
###   start       $7  starting sector of the partition
###   end         $8  ending sector of the partition
###   system      $9  system of the partition
###   pi          $10  pi of the partition, (equal to "" if not a regular partition. 
Get_Partition_Info(){
local Log="$1" Log1="$2" part="$3" name="$4" mountname="$5"  kind="$6"  start="$7"  end="$8" system="$9" pi="${10}";
local size=$((end-start)) BST=""  BSI=""  BFI=""  OS="" BootFiles="";


       echo "Searching $name for information... ";
       PrintBlkid $part;
       type=$(BlkidTag $part TYPE);  ##### type of file system according to blkid

       [[ "$system" == "Bios Boot Partition" ]] && type="Bios Boot Partition"
       [[ $pi != "" ]] && FileArray[$pi]=$type;
      echo "$name: _________________________________________________________________________" >>"$Log"; echo>> "$Log"
      mkdir -p "$mountname"    ####  Directory where the partition will be mounted.
      if [[ "$kind" = "E"  &&  "$type" = "" ]] ;  #### Check for extended partion.
         then
	 type="Extended Partition";
	 cat $Tmp_Log>>$Trash;  ### Don't display  the error message from blkid for extended partition
	 else
         cat $Tmp_Log>>$Error_Log
      fi;
      echo "    File system:       "$type>>"$Log";  ### Display the File System Type

     
          Bytes8081=$(hexdump -v -s 128 -n  2 -e '/1 "%x"'  $part)   #### Use bytes 0x80,81 to idendtify Boot sectors
          case    $Bytes8081    in
             10f) BST="HP Recovery";;
             19d)  BST="BSD4.4: Fat32";;
             211) BST="Dell Utility: Fat16";;
             734)  BST=Dos_1.0;;
             745)  BST="Vista:  Fat 32";;
             89e)  BST="MSDOS5.0: Fat 16";;
             8cd) BST="Windows XP";;
             488) BST="Grub 2's core.img";;
             b60) BST="Dell Utility: Fat16";; 
             bd0) BST="MSWIN4.1: Fat 32";;
             e00) BST="Dell Utility: Fat16";;
            2d5e) BST=Dos_1.1;;
            3a5e) BST="Recovery:Fat 32";;
            4445) BST="DEll Restore: Fat32";; 
	    55aa) BST="Windows Vista/7";;
            55cd) BST="Fat32";;
            6616) BST=Fat16;;
            696e) BST=Fat16;;
            6974) BST="BootIt: Fat16";;
            6f65) BST="BootIt: Fat16";;
            6f74) BST=Fat32;; 
            6f6e) BST="-";;  #MSWIN4.1: Fat 32"
            7815) BST=Fat32;;
 	    7cc6) BST="MSWIN4.1: Fat 32";;
          # 7cc6) BST=Win_98;;
            8a56) BST="Acronis SZ: Fat32";;
            8ec0) BST="Windows XP";;
            8ed0) BST="DEll Recovery: Fat32";;
            b6d1) BST="Windows XP: Fat32";;
            e2f7) BST="Fat32, Non Bootable";;
            e9d8) BST="Windows Vista/7";;
            fa33) BST="Windows XP";;
               ####### if Grub, Grub 2 or Lilo  is  in the boot sector,  ########
               ####### investigate the embedded information              ########
            48b4) BST="Grub 1.96";    
                  core_loc $part 1.96;
                  BSI=$(echo $BSI Grub 1.96 is installed in the boot sector of $name  and $Core_Msg);;
            7c3c) BST="Grub 2";    
                  core_loc $part 1.97;
                  BSI=$(echo $BSI Grub 2 is installed in the boot sector of $name  and $Core_Msg);;
     aa75 | 5272) BST=Grub;
                  stage2_loc $part;
                  BSI=$(echo $BSI Grub $Grub_Version is installed in the boot sector of $name  and $Stage2_Msg);;
     #############  If Lilo look for map file  ##############################################
 	    8053) BST=LILO;
                   offset=$(hexdump -v -s 32 -n 4 -e '"%u"' $part);  ### 0x20-23 contains the offset
                                                                    #####  of  /boot/map         
                   BSI=$(echo $BSI" "LILO  is installed in boot sector of $part and looks at sector $offset of $drive for the \"map\"  file,); 
                   if [ $offset -lt  $size ];   ### check whether offset
                                                                    #### is on the had drive.
                   then
	                 tmp=$(dd if=$drive skip=$offset count=1 2>>$Trash | hexdump -v -s 508  -n 4 -e '"%_p"');                     
                         if [[ "$tmp" = "LILO" ]];
			 then
			     BSI=$(echo $BSI" "and the \"map\" file was found at this location.);
	                 else
                             BSI=$(echo $BSI" "but the \"map\" file was not found at this location.);
                         fi;
                    else
                        BSI=$(echo $BSI" "but the \"map\" file was not found at this location.);
                    fi;;
     #########################################################################################
              00)   sig2=$(hexdump -v -s 128 -n  2 -e '/1 "%x"'  $part)
                      if [ "$sig2" = 00 ];    #### If the first two bytes are zero, the boot sector does not contain any boot loader.
		      then
                      BST="-";
		      else   ###### Otherwise, display the boot sector, so we that we might identify it and add it to the list of known boot sectors.
		      BST="Unknown"
                      echo "Unknown BootLoader  on $name" >> $Unknown_MBR;
                      echo >> $Unknown_MBR;
                      hexdump  -n 512 -C $part >> $Unknown_MBR;
                      echo >> $Unknown_MBR;
                  fi;;
                *) BST="Unknown"
                   echo "Unknown BootLoader  on $name" >> $Unknown_MBR;
                   echo >> $Unknown_MBR;
                   hexdump -n 512 -C $part >> $Unknown_MBR;
                   echo >> $Unknown_MBR;
            esac;
######################   Display the boot sector type.
           echo "    Boot sector type:  "$BST>>"$Log" 

####################### Investigate the Boot Parameter Block of an NTFS partition.

           if [[ "$type" = "ntfs" ]]
           then
           offset=$(hexdump -v -s 28 -n 4 -e '"%u"' $part);
           BPB_Part_Size=$(hexdump -v -s 40 -n 4 -e '"%u"' $part)
           Comp_Size=$(( (BPB_Part_Size - size)/256 ))
           SectorsPerCluster=$(hexdump -v -s 13 -n 1 -e '"%d"' $part);
           MFT_Cluster=$(hexdump -v -s 48 -n 4 -e '"%d"' $part);
           MFT_Sector=$(( MFT_Cluster * SectorsPerCluster ));
         #  Track=$(hexdump -v -s 24 -n 2 -e '"%u"' $part)''  ### Number of sectors per track.
         #  Heads=$(hexdump -v -s 26 -n 2 -e '"%u"' $part)''  ### Number of heads
         #  if [[ "$Heads" != 255  || "$Track" != 63 ]]
	 #  then
         #     BSI=$(echo $BSI" "Geometry: $Heads Heads and $Track sectors per Track.)
	 #  fi;           
           if [[ "$MFT_Sector" -lt "$size" ]];
           then
               MFT_FILE=$(dd if=$part skip=$MFT_Sector count=1 2>>$Trash | hexdump -v    -n 4 -e '"%_u"');               
	   else 
               MFT_FILE="";
           fi;
           MFT_Mirr_Cluster=$(hexdump -v -s 56 -n 4 -e '"%d"' $part);
           MFT_Mirr_Sector=$(( MFT_Mirr_Cluster * SectorsPerCluster ));
           if [[ "$MFT_Mirr_Sector" -lt "$size" ]];
           then
                MFT_Mirr_FILE=$(dd if=$part skip=$MFT_Mirr_Sector count=1 2>>$Trash | hexdump -v    -n 4 -e '"%_u"');
  
           else 
               MFT_Mirr_FILE="";
           fi;
           if [[ "$offset" = "$start"  && "$MFT_FILE" = "FILE"  && "$MFT_Mirr_FILE" = "FILE"  && "$Comp_Size" = "0"  ]];
	    then
	       BSI=$(echo $BSI" "No errors found in the  Boot Parameter Block.);
           else
	    if [[ "$offset" != "$start" ]] 
            then
                BSI=$(echo $BSI"  "According to the info in the boot sector, $name starts at sector $offset.)
                if [[ "$offset" != "63" && "$offset" != "2048"  && "offset" != "0" ||  "$kind" != "L" ]]
                then
                    BSI=$(echo $BSI" "But according to the info  from fdisk, $name starts at sector   $start.);
                 fi;
            fi;
            if  [[ "$MFT_FILE" != "FILE"  ]]; 
	    then 
                BSI=$(echo $BSI" "The info in boot sector  on  the starting sector of the MFT is wrong.);
                echo MFT Sector of $name >> $Unknown_MBR;
                echo >> $Unknown_MBR
                dd if=$part skip=$MFT_Sector count=1 2>>$Trash| hexdump -C >>$Unknown_MBR;
             fi;
             if [[ "$MFT_Mirr_FILE" != "FILE" ]];
	     then
		 BSI=$(echo $BSI" "The info in the boot sector on  the starting sector of the MFT Mirror  is wrong.);
             fi;

             if  [[ "$Comp_Size" != "0"  ]];
             then  
                   BSI=$(echo $BSI"  "According to the info in the boot sector, $name has    $BPB_Part_Size sectors, but according to the info  from fdisk, it has  $size sectors.);
             fi;
           fi;
          fi;

######################## Investigate the Boot Parameter Block (BPB)of some Fat partitions
 #####  Identifies Fat Bootsectors which are used for booting.

##  if [[ "$Bytes8081" = "7cc6" ||  "$Bytes8081" = "7815"  ||  "$Bytes8081" = "B6D1"  || "$Bytes8081" =  "7405" || "$Bytes8081" = "6974" || "$Bytes8081" = "bd0" ||  "$Bytes8081" =  "89e"  ]] ;

        if [[ "$type" = "vfat" ]];
           then
           offset=$(hexdump -v -s 28 -n 4 -e '"%d\n"' $part); #### Starting sector the partition  according to BPP
           BPB_Part_Size=$(hexdump -v -s 32 -n 4 -e '"%d"' $part); ### Partition Size in sectors accoring to BPB 
           Comp_Size=$(( (BPB_Part_Size - size)/256 )) ### This number will be unequal to zero  if the two partions size  differ by more than 255 sectors.  
           #Track=$(hexdump -v -s 24 -n 2 -e '"%u"' $part)''  ### Number of sectors per track.
           #Heads=$(hexdump -v -s 26 -n 2 -e '"%u"' $part)''  ### Number of heads
           #if [[ "$Heads" != 255  || "$Track" != 63 ]] ###  Checks for an usual geometry. 
	   #then
           #   BSI=$(echo $BSI" "Geometry: $Heads Heads and $Track sectors per Track.)  ### Report unusal geometry
	   #fi;     
           if [[ "$offset" = "$start" && "$Comp_Size" = "0"  ]];  ### Check whether Partitons starting sector  and  the Partition Size of BPB and fdisk agree. 
	    then
	       BSI=$(echo $BSI" "No errors found in the  Boot Parameter Block.);  ##If they agreee
	    else      ######   if they  don't agree
            if [[ "$offset" != "$start" ]]   ###  if partition starting sector disagree 
            then
                BSI=$(echo $BSI"  "According to the info in the boot sector, $name starts at sector $offset.)   ### display the starting sector accoding to BPB
                if [[ "$offset" != "63" && "$offset" != "2048" ||  "$kind" != "L" ]]  ### check whether partition is logcial partition and starting sector is a 63.
                then  ### if not, display starting sector according to fdisk.
                    BSI=$(echo $BSI" "But according to the info  from fdisk, $name starts at sector   $start.);
                fi; ### If not, don't display.  (This is quite common occurence, and only matters if one tries to boot Windows from a logical partition. So I decided not to display a warning message in this case. 
            fi;  
#### If Partition sizes from BPB and FDISK differ by more than 255 sector, display both sizes.       
            if [[ "$Comp_Size" != "0"  ]];
            then    
		BSI=$(echo $BSI"  "According to the info in the boot sector, $name has    $BPB_Part_Size sectors.)
                if [[ "$BPB_Part_Size" != 0 ]];
                then 
                BSI=$(echo "$BSI"." " But according to the info  from the partition table , it has  $size sectors.);
                fi;  ## Don't display warning message in the common case BPB_Part_Size=0. 
            fi; 
              
            fi;   #### End of BPB Error if then else 
          fi;   ###### End of Investigation of the BPB of vfat partitions. 
################################################################################################
      #####  Display boot sector info
      echo -n "    Boot sector info:  ">>"$Log"
      echo $BSI | fold -s -w 55 |  sed -e '2~1s/.*/                       &/'>>"$Log"

      ####Exclude Partitions which contain no information,     #########
      ##### or which we (currently) don't know how to  accces. #########  
      if [ "$type" != "swap" ]  && [ "$type" != "Extended Partition"  ] && [ "$type" != "unknown volume type" ] && [ "$type" != "LVM2_member" ]  && [ "$type" != "linux_raid_member" ] && [ "$type" != "crypto_Luks" ] && [ "$system" != "Bios Boot Partition" ] ; 
      then     
 
         CheckMount=$(mount| grep "$part " |sed '2,$ d');
         CheckMount=${CheckMount% type*};
         CheckMount=${CheckMount#* on };   
          ### Check whether partition is already mounted
         if  [ "$CheckMount" != "" ] ;
         then 
             if  [ "$CheckMount" = "/" ];
             then mountname="";
             else
                mountname=$CheckMount;  #### if yes,use existing mount point.
             fi;
         fi;
         if  [ "$CheckMount" != "" ] || mount -r  -t "$type" $part "$mountname" 2>>$Mount_Error  || ( [ "$type" = ntfs ] &&  ntfs-3g -o ro  $part "$mountname" 2>>$Mount_Error )   ;     ####### Try to mount partition
         then     ############  if partition is  mounted.
         #####Try to identify the Operating  System (OS) by  looking for files specific to the OS
       OS=""

        grep -q "W.i.n.d.o.w.s. .V.i.s.t.a"  "$mountname"/{windows,Windows,WINDOWS}/{System32,system32}/{Winload,winload}.exe 2>>$Trash && OS="Windows Vista";

       grep -q "W.i.n.d.o.w.s. .7" "$mountname"/{windows,Windows,WINDOWS}/{System32,system32}/{Winload,winload}.exe 2>>$Trash && OS="Windows 7";
       for  WinOS in  "MS-DOS"  "MS-DOS 6.22" "MS-DOS 6.21" "MS-DOS 6.0" "MS-DOS 5.0" "MS-DOS 4.01" "MS-DOS 3.3" "Windows 98" "Windows 95"; do grep -q "$WinOS" "$mountname"/{IO.SYS,io.sys} 2>>$Trash && OS="$WinOS"; done;
        

       [ -s "$mountname/Windows/System32/config/SecEvent.Evt" ] ||  [ -s "$mountname/WINDOWS/system32/config/SecEvent.Evt" ] || [ -s "$mountname/WINDOWS/system32/config/secevent.evt" ] || [ -s "$mountname/windows/system32/config/secevent.evt" ] && OS="Windows XP";

       [ -s "$mountname/etc/issue" ] && OS=$(sed -e 's/\\. //g' -e 's/\\.//g' -e 's/^[ \t]*//' "$mountname"/etc/issue);

        [ -s "$mountname/etc/slackware-version" ] && OS=$(sed -e 's/\\. //g' -e 's/\\.//g' -e 's/^[ \t]*//' "$mountname"/etc/slackware-version);


####################################  search for  the files in $Bootfiles   ########################
#################################### and if found, display there contained ########################
       BootFiles="" 
       if [ "$type" = "vfat" ];
       then
           Boot_Files=$Boot_Files_Fat;
       else
           Boot_Files=$Boot_Files_Normal;  
       fi;
       
       for file in $Boot_Files;
       do
           if [ -f "$mountname"$file ] && [ -s "$mountname"$file ] && FileNotMounted "$mountname"$file "$mountname"
           then
               BootFiles=$(echo $BootFiles"  "$file);
              if ! [ -h "$mountname"$file ];  ### check whether file is  symlink
              then                            ### if not a symlink, display content.
                 titlebar_gen "$name" $file; ##generates a titlebar above each file/dir listed      
                 cat "$mountname"$file  >> "$Log1"; 
              fi;
	   fi;
       done;
################# Search for Wubi partitions

---

### Post by adamogardner on 2011-01-09
almost finished:

################# Search for Wubi partitions  ###################################
if [ -f "$mountname""/ubuntu/disks/root.disk" ];
      then          
          Wubi=$(losetup -a|awk '$3 ~ "(/host/ubuntu/disks/root.disk)"{print $1; exit}'|sed s/.$//)
                    #check whether Wubi already has a loop device.
          if [[ "$Wubi" = "" ]];
          then
              Wubi=$(losetup -f --show  "$mountname""/ubuntu/disks/root.disk" );
              WubiDev=0;
          else
              WubiDev=1;
          fi;
          if [ "$Wubi" != "" ];
          then
              Get_Partition_Info "$Log"x "$Log1"x "$Wubi" "$name""/Wubi" "Wubi/""$mountname" "Wubi" 0 0 "Wubi" "";
          [[ $WubiDev = 0 ]] && losetup -d "$Wubi";  #delete Wubu loop device, if created by BIS
          else 
             echo "Found Wubi on $name. But could not create a loop device">>$Error_Log;
          fi;      
        fi;            
                    
                      
             
#################################### Search for the programs in $Boot_Prog, ###############
################################### if found displays their names.           ###############
        if [ "$type" = "vfat" ];
       then
           Boot_Prog=$Boot_Prog_Fat;
       else
           Boot_Prog=$Boot_Prog_Normal;  
       fi;

       for file in $Boot_Prog;   
       do
           if [ -f "$mountname"$file ] && [ -s "$mountname"$file ]  && FileNotMounted "$mountname"$file "$mountname";
              then 
              BootFiles=$(echo $BootFiles"  "$file);          
	   fi;
       done;


################### Search for the directories related to Booting ########################
##################, if found display the list of files             #######################

#       for file in $Boot_Dir;  #directories in that directory.
#       do
#          if [ -d "$mountname"$file ];
#          then
#	      BootFiles=$(echo $BootFiles"  "$file); 
#              titlebar_gen "$name" $file	##generates a titlebar above each file/dir listed
#              ls -la  "$mountname"$file >> "$Log1" ; 
#             
#	  fi;
#       done;

####################  Search for files containing boot codes #################################

       for file in $Boot_Codes_Dir    #####  loop through all directories which might contain boot_code files
       do
	   if [ -d "$mountname"$file ] && FileNotMounted "$mountname"$file "$mountname";   ##### if such directory exist
	   then  
	       for loader in $( ls  "$mountname"$file );  ##### look at the content of that directory 
	       do
                  if [ -f "$mountname$file$loader" ] && [ -s "$mountname$file$loader" ];  ####  it its a file
		  then		     
                      sig=$(hexdump -v -s 257 -n 8  -e '8/1 "%_p"' "$mountname"$file$loader);
                      if [ "$sig"  = "BootPart" ]    ##### Bootpart code has "BootPart" written at0x101
		      then
                          offset=$(hexdump -v -s 241 -n 4 -e '"%d"' "$mountname"$file$loader);
                              dr=$(hexdump -v -s 111 -n 1 -e '"%d"' "$mountname"$file$loader);
			      dr=$((dr -127))
 			  BFI=$(echo $BFI "  "BootPart in the file $file$loader is trying to chain load sector \#$offset on boot drive \#$dr);
		      fi;
		      sig=$(hexdump -v -s 383 -n 4  -e '4/1 "%_p"' "$mountname"$file$loader);
                      if [ "$sig"  = "GRUB" ];   ##### Grub and Grub1.96  have "Grub" written at 0x17f
                      then
                          sig2=$(hexdump -v -n  2 -e '/1 "%x"' "$mountname"$file$loader);
                          if [[ "$sig2" = "eb48" ]] ### distinguish Grub and Grub 2 by the
                                                    ##### first two bytes.
                          then
                               stage2_loc  "$mountname"$file$loader;
                               BFI=$(echo $BFI" "Grub $Grub_Version in the file  $file$loader $Stage2_Msg);
                          else 
                               core_loc  "$mountname"$file$loader 1.96;
                               BFI=$(echo $BFI" "Grub 1.96  in the file  $file$loader $Core_Msg); 
                          fi;    
                      fi;
                      sig=$(hexdump -v -s 392 -n 4  -e '4/1 "%_p"' "$mountname"$file$loader);#### Grub1.97 has "Grub" writtem at 0x188
                      if [ "$sig"  = "GRUB" ];   ##### Grub 2  have "Grub" written at 0x188
                      then  
                          core_loc  "$mountname"$file$loader 1.97;
                          BFI=$(echo $BFI" "Grub 2  in the file  $file$loader $Core_Msg); 
                      fi;
                      
 		  fi;
	        done; ## End of loop through the files in a particular  Boot_Code_Directory
            fi;
        done   ## End of the loop through the Boot_Code_Directories.

---

### Post by adamogardner on 2011-01-09
last of it:

 ## End of the loop through the Boot_Code_Directories.

######### Determine the end point of all files in the GrubError18_Files list
    
     echo >$Tmp_Log;
     counter=0;
     cd "$mountname"/;
     for file in $(ls $GrubError18_Files 2>>$Trash);
     do
     if [[ -f $file ]] && [[ -s $file ]] && FileNotMounted "$mountname""/"$file "$mountname"
     then
         EndGB="??";
         BlockSize=$(filefrag -v $file| grep "Blocksize" |awk '{print $6}');
         if [ "$BlockSize" != "" ];
         then
             LastBlock=$(filefrag -v "$file"| grep "Last block"  |awk '{print $3}');
             if [ "$LastBlock" != "" ];
             then
 	              EndGB=$(echo $(((BlockSize*LastBlock + 512*start)/100000000 ))|sed 's/\(.\)$/\.\1/')
	     fi;  
         fi; 
         BlockSize=$(filefrag -v "$file"| grep "blocksize" |awk '{print $NF}'| sed 's/)//');
         if [ "$BlockSize" != "" ];
         then
             LastBlock=$(filefrag -v "$file" | grep 'eof'  |awk '{print $3}');
             if [ "$LastBlock" != "" ];
             then
 	        EndGB=$(echo $(((BlockSize*LastBlock + 512*start)/100000000 ))|sed 's/\(.\)$/\.\1/')
	     fi;  
         fi; 
         printf "%6sGB: %-s\n" $EndGB "$file" >>$Tmp_Log;
         ((counter++));
     fi;
     done;
     cd $Folder;
     if [ $counter != 0 ];
     then
	  titlebar_gen "$name"  ": Location of files loaded by Grub";
          cat $Tmp_Log>>"$Log1";
     fi;
     echo >$Tmp_Log;

      if [[ $BFI != "" ]];
      then
          echo -n "    Boot file info:     ">>"$Log"
          echo $BFI | fold -s -w 55 |  sed -e '2~1s/.*/                       &/'>>"$Log"
      fi;
      echo "    Operating System:  "$OS | fold -s -w 55 | sed -e '2~1s/.*/                       &/'>>"$Log"    
      echo -n "    Boot files/dirs:   ">>"$Log"
      echo $BootFiles | fold -s -w 55 |  sed -e '2~1s/.*/                       &/'>>"$Log"
     
        if [ "$CheckMount" = "" ];  ## if partition was mounted by the script
        then
            umount "$mountname" || umount -l "$mountname";          
        fi;
     else     ############### if partition failed to mount  
       echo "    Mounting failed:">>"$Log";  
       cat $Mount_Error>>"$Log"; 
     fi;  ### end of Mounting "if then else"
     fi;  ### end of Partition Type "if then else"
     echo>>"$Log";
     if [[ -e "$Log"x ]];
     then cat "$Log"x>>"$Log";
          rm "$Log"x;
     fi;
     if [[ -e "$Log1"x ]];
     then cat "$Log1"x>>"$Log1";
          rm "$Log1"x;
     fi;

      }  ## end Get_Partition_Info function



## "titlebar_gen" generates the $name$file title bar to always be either 79 or 80 chars total in length:
titlebar_gen () {
		name_file="$1$2:"; name_file_length=${#name_file}
		equal_signs_line_length=$(((80-name_file_length)/2-1)); equal_signs_line=""
		for length in $(seq $equal_signs_line_length); do
  			equal_signs_line='='$equal_signs_line
		done;
                echo >> "$Log1";
		echo "$equal_signs_line $name_file $equal_signs_line" >> "$Log1";
                echo >> "$Log1";
                }


echo "                Boot Info Script $VERSION    dated $DATE                    ">>"Log";
echo>>"Log";
echo '============================= Boot Info Summary: =============================='>>"$Log"; 
echo>>"$Log";

#####   Search  for  hard drives which don't exist,have a  corrupted partition table
#####  or  don't have a parition table(whole drive is a file system) 
#####  Information on all  hard drives which a valid partition table are stored in the 
#####  Hard drives arrays: HD?????
FSD=0;  #id for Filesystem Drives
for drive in  $All_Hard_Drives;
do
     size=$(fdisks $drive);
     PrintBlkid $drive;        
     if [ 0 -lt $size 2>>$Trash ];
     then
          if  [ "$(blkid  $drive)" = "" ] || [ "$(blkid  | grep $drive:)" = "" ]; #Check whether drive is a filesystem
          then  #if drive is  not a filesytem
             size=$((2*size));
 # (not used) Hard_Drives=$Hard_Drives" "$drive;
            HDName[$HI]=$drive;
            HDSize[$HI]=$size;
            geometry=$(fdisk  -lu $drive 2>>$Trash | grep "head");
            HDHead[$HI]=$(echo $geometry | awk '{print $1}');
            HDTrack[$HI]=$(echo $geometry | awk '{print $3}');
            HDCylinder[$HI]=$(echo $geometry | awk '{print $5}');
 ###Look at the first 4 bytes of the second sector to identify type of partition table;
            case $(hexdump -v -s 512 -n 4 -e '"%_u"' $drive) in
            "EMBR")  HDPT[$HI]="BootIt";;
            "EFI ")  HDPT[$HI]="EFI";;
                 *)  HDPT[$HI]="MSDos";;
            esac; 
            HI=$((HI+1));
          else   #if drive is  filesystem
              if [ $( expr match "$(BlkidTag "$drive" TYPE)" '.*raid') -eq 0 ] || [ "$(BlkidTag "$drive" UUID)" != "" ];
              then
                   FilesystemDrives[$FSD]="$drive";
                   ((FSD++));
              fi;
          fi;
      else
            echo -n "$(basename $drive) " >>$FakeHardDrives;
      fi;
done;
############ Identify the MBR of each  hard drive.
echo "Identifying MBRs..." ;
for hi in ${!HDName[@]};
  do 
    drive="${HDName[$hi]}";
    Message=$(echo is installed in the MBR of $drive)
    case $(hexdump -v -n  2 -e '/1 "%x"' $drive) in   ####Look at the first two bytes of the hard drive  to identify the boot code installed in the MBR
 
################################ If Grub is in the MBR   #########################

	eb48) offset=$(hexdump -v -s 68 -n 4 -e '"%u"' $drive);### 0x44 contains the offset of the next stage
              if  [ "$offset" != 1 ];   ###if  Grub is installed without stage1.5 files 
	      then
                  stage2_loc $drive;
                  Message=$(echo $Message and  $Stage2_Msg)
 	      else                         ### if grub is installed with stage1.5 files
                  Grub_String=$(hexdump -v -s 1042 -n 94 -e '"%_u"' $drive);
                  Grub_Version=${Grub_String%%nul*};
                  tmp='/'${Grub_String#*/};
                  tmp=${tmp%%nul*};
                  stage=$(echo $tmp| awk '{print $1}');
                  menu=$(echo $tmp| awk '{print $2}');
                  [[ "$menu" = "" ]] || stage=$(echo $stage and $menu);
                  part_info=$((1045 + ${#Grub_Version}));
	          pa=$(hexdump -v -s $part_info  -n 1 -e '"%d"' $drive);
                  part_info=$((part_info+1));
                  dr=$(hexdump -v -s $part_info -n 1 -e '"%d"' $drive);
                  dr=$((dr-127));
		  pa=$((pa+1));
		  if [ $dr = 128 ];
                  then
                       Message=$(echo $Message and looks on the same drive in partition \#$pa for $stage.)
                  else
                      Message=$(echo $Message and looks  on boot drive \#$dr in partition \#$pa for $stage.)
              fi;
	    fi;
              BL="Grub "$Grub_Version;;
###############################  If Grub 1.96 is in the MBR   #####################################

        eb4c ) BL="Grub 1.96";
              offset=$(hexdump -v -s 68 -n 4 -e '"%u"' $drive);### 0x44 contains the offset of the next stage
              if  [ "$offset" != 1 ];   ###if  Grub2 is  installed without  Core. 
	      then
                  core_loc $drive 1.96;
                  Message=$(echo $Message and  $Core_Msg)
 	      else                      ### if Grub2  is installed with Core
                  Grub_String=$(hexdump -v -s 1056 -n 64 -e '"%_u"' $drive);
                  Core_Dir=$(echo  $Grub_String | sed s/nul[^$]*//);
	          pa=$(hexdump -v -s 1044  -n 1 -e '"%d"' $drive);
                  dr=$(hexdump -v -s 77  -n 1 -e '"%d"' $drive);
                  dr=$((dr-127));
		  pa=$((pa+1));
		  if [ $dr = 128 ];
                  then
                       Message=$(echo $Message and looks on the same drive in partition \#$pa for $Core_Dir.)
                  else
                      Message=$(echo $Message and looks  on boot drive \#$dr in partition \#$pa for $Core_Dir.)
              fi;
	    fi;;

################### If  Grub 2 in the MBR###################################
        eb63 ) BL="Grub 2"
             offset=$(hexdump -v -s 92 -n 4 -e '"%u"' $drive);### 0x5c contains the offset of the core 
             if  [ "$offset" != 1 ];   ###if  Grub2 is  installed without embeded  Core. 
	     then
                 core_loc $drive 1.97;
                  Message=$(echo $Message and  $Core_Msg)
 	     else                      ### if Grub2  is installed with Core
                  Grub_String=$(hexdump -v -s 1052 -n 64 -e '"%_u"' $drive);
                  Core_Dir=$(echo  $Grub_String | sed s/nul[^$]*//);
	          pa=$(hexdump -v -s 1044  -n 1 -e '"%d"' $drive);
                  dr=$(hexdump -v -s 77  -n 1 -e '"%d"' $drive);
                  dr=$((dr-127));
		  pa=$((pa+1));
		  if [ $pa = 255 ];
                  then
                      Message=$(echo $Message and looks  for $Core_Dir.)
                  else
                       Message=$(echo $Message and looks on the same drive in partition \#$pa for $Core_Dir.)
                  
                  fi;
	    fi;;
##############################################################################################
	 ebe) BL=ThinkPad;;
	31c0) BL="Acer 3";;
	33c0) BL=Windows;;
	33ff) BL='HP/Gateway';;
	b800) BL=PloP;;
	ea1e) BL="Truecrypt Boot Loader";; 
	eb04) BL=Solaris;;
	eb31) BL=Paragon;;
        eb5e) case $(hexdump -v -n  3 -e '/1 "%x"' $drive) in   ####Look at the first three bytes of the hard drive to identify the boot code installed in the MBR
		eb5e00) BL=fbinst;;
		eb5e80) BL=Grub4Dos;;
	      esac;;
	fa31) case $(hexdump -v -n  3 -e '/1 "%x"' $drive) in   ####Look at the first tree bytes of the hard drive to identify the boot code installed in the MBR
		fa31c0) BL=Syslinux;;
		fa31c9) BL="Master Boot LoaDeR";;   
	      esac;;

	fa33) BL="No boot loader";; 
	fab8) BL="No boot loader";;   
	fabe) BL="No boot loader?";;
	faeb) BL=Lilo;; 
	fc31) BL=Testdisk;;
	fc33) BL=GAG;;
	fceb) BL="BootIt NG";;
          00) BL="No boot loader";;
	   *) BL="No known boot loader"
              echo "Unknown MBR on $drive" >> $Unknown_MBR;
              echo >> $Unknown_MBR;
              hexdump -v -n 512 -C $drive >> $Unknown_MBR;
              echo >> $Unknown_MBR;;
        esac;
        ##Output message at beginning of summary that gives MBR info for each drive:
        echo -n " => ">>"$Log"
        echo "$BL $Message" | fold -s -w 75 | sed -e '2~1s/.*/    &/' >>"$Log"  
        HDMBR[$hi]=$BL;
    done;
    echo>>"$Log";
######################################################################################
#############   Store and Display all the partitions tables.##########################
for HI in ${!HDName[@]};
    do
    drive=${HDName[$HI]};
    echo "Computing Partition Table of $drive...";
    FP=$((PI+1)); #used if non-MS_DOS partition table is not in use.
    FirstPartition[$HI]=$FP;
    PTType=${HDPT[$HI]};
    HDPT[$HI]="MSDos";
    echo "Drive: $(basename $drive ) ___________________ _____________________________________________________" >>$PartitionTable;
    fdisk  -lu $drive 2>>$Trash |sed '/omitting/ d'|sed '6,$ d' >>$PartitionTable;
    echo >>$PartitionTable;
    printf "$PTFormat" "Partition" "Boot" "Start" "End"  "Size"  "Id" "System">>$PartitionTable;
    echo >>$PartitionTable;
    ReadPT $HI 0  4 $PartitionTable "$PTFormat" "" 0;
    echo >>$PartitionTable;
    LastPartition[$HI]=$PI;
    LP=$PI;
    CheckPT  ${FirstPartition[$HI]} ${LastPartition[$HI]}  $PartitionTable $HI;
    echo >>$PartitionTable;
    HDPT[$HI]=$PTType;
    case $PTType in
      BootIt)  echo -n  BootIt NG Partition Table detected>>$PartitionTable;
              [[ "${HDMBR[$HI]}" = "BootIt NG" ]] && echo . >>$PartitionTable || echo , but does not seem to be used. >>$PartitionTable;
              echo>>$PartitionTable;
              ReadEMBR  $HI $PartitionTable;
	      echo >>$PartitionTable;
              if [ "${HDMBR[$HI]}" = "BootIt NG" ];
	      then
                   LastPartition[$HI]=$PI;
                   CheckPT  ${FirstPartition[$HI]} ${LastPartition[$HI]}  $PartitionTable $HI; 
	      else
                   FirstPartition[$HI]=$FP;
              fi;;
         EFI) FirstPartition[$HI]=$((PI+1));
              EFIee=$(hexdump -v -s 450 -n 1 -e '"%x"' $drive);
              echo -n  GUID Partition Table detected>>$PartitionTable;
              [[ "$EFIee" = "ee" ]] && echo . >>$PartitionTable || echo , but does not seem to be used. >>$PartitionTable ;
              echo >>$PartitionTable;
              ReadEFI  $HI $PartitionTable;
              echo >>$PartitionTable;
              if [ "$EFIee" = "ee" ];
	      then
                   LastPartition[$HI]=$PI;
                   CheckPT  ${FirstPartition[$HI]} ${LastPartition[$HI]}  $PartitionTable $HI;
	      else
                   FirstPartition[$HI]=$FP;
              fi;;
      esac;    
done;

for hi in ${!HDName[@]};  ############Loop through all Hard Drives
 do
 drive=${HDName[$hi]}
for (( pi = FirstPartition[$hi]; pi <= LastPartition[$hi]; pi++ ));  ## And then loop through                                                                      ###the partitions  on that drive
do
         
      part_type=${TypeArray[$pi]};  #### Type of the partition according to fdisk
      start=${StartArray[$pi]};
      size=${SizeArray[$pi]};
      end=${EndArray[$pi]};
      kind=${KindArray[$pi]};
      system=${SystemArray[$pi]};
      if [[ "${DeviceArray[$pi]}" = "" ]];
      then
          name="${NamesArray[$pi]}";
          mountname=$(basename $drive)"_"$pi;
          part=$(losetup -f --show  -o $((start*512)) $drive);
         #### --sizelimit $((size*512))    --sizelimit seems to be a recently added option for losetup.  Failed on Hardy 
      else
          part="${DeviceArray[$pi]}";
          name=$(basename $part);  ####  Name of the partition (/dev/sda8 -> sda8)
          mountname=$name;      
      fi;

      Get_Partition_Info "$Log" "$Log1" "$part" "$name" "$mountname" "$kind" "$start" "$end" "$system" "$pi";
     
     [[ "${DeviceArray[$pi]}" = ""  ]] && losetup -d $part;
     done;  ### end of partition loop
     done;  ### end of hard drive loop


################ Deactivate dmraid's activated by the script#############

if [ "$InActiveDMRaid" != "" ];
then
   dmraid -an $InActiveDMRaid
fi; 

##################### Search LVM partitions for information.             #########
##################### only works if the "LVM2"-package is installed     #########
if type lvscan >>$Trash 2>>$Trash && type lvdisplay >>$Trash 2>>$Trash && type lvchange >>$Trash 2>>$Trash;

then   ###  if LVM2 is installed
   
   LVM_Partitions=$(lvscan| awk '{print $2}'| awk -F / '{print "/dev/mapper" "/" $3 "-" $4}'|sed s/.$//)

   for LVM in $LVM_Partitions;
   do 
      LVM_Size=$(lvdisplay -c $LVM  |awk -F : '{print $7}');
      LVM_Status=$(lvdisplay $LVM |grep "LV Status"|awk '{print $3}');
      lvchange -ay $LVM;
      name=${LVM:12};
      mountname="LVM/""$name";
      kind="LVM";
      start=0;
      end=$LVM_Size;
      system="";
      pi="";
     
      Get_Partition_Info "$Log" "$Log1" "$LVM" "$name" "$mountname" "$kind" "$start" "$end" "$system" "$pi";
      
  [[ "$LVM_Status" = "NOT" ]] && lvchange -an "$LVM";
                         #deactivate all LVM's,which were not active. 
  
     
    done;
fi;


####################### Search MDRaid Partitons for Information##############################
######################  Only works if "mdadm" is installed     #############################
if type mdadm >>$Trash 2>>$Trash;
then
    MD_Active_Array=$(mdadm --detail --scan |awk '{print $2}');
                   ## all arrays which are already assembled
    mdadm --assemble  --scan  #assemble all arrays
    MD_Array=$(mdadm --detail --scan|awk '{print $2}');
                    ## all arrays.
    for MD in $MD_Array;
    do
        MD_Size=$(fdisks $MD); #size in blocks
        MD_Size=$((2*MD_Size)); #size in sectors
        MD_Active=0;
        for MDA in $MD_Active_Array;  ## check whether MD is active
        do
          if [[ "$MDA" = "$MD" ]]
          then
              MD_Active=1;
              break;
          fi;
	done;
      name=${MD:5};
      mountname="MDRaid/""$name";
      kind="MDRaid";
      start=0;
      end=$MD_Size;
      system="";
      pi="";
     
      Get_Partition_Info "$Log" "$Log1" "$MD" "$name" "$mountname" "$kind" "$start" "$end" "$system" "$pi";
      
  [[ "$MD_Active" = 0 ]] && mdadm --stop $MD

                         #deactivate all MD_Raid's,which were not active.
   done;
fi; 

####################### Search Filessystem hard drive for information########################

    for FD  in ${FilesystemDrives[@]};
    do
      FD_Size=$(fdisks $FD); #size in blocks
      FD_Size=$((2*FD_Size)); #size in sectors
      name=${FD:5};
      mountname="FD/""$name";
      kind="FD";
      start=0;
      end=$FD_Size;
      system="";
      pi="";
     
      Get_Partition_Info "$Log" "$Log1" "$FD" "$name" "$mountname" "$kind" "$start" "$end" "$system" "$pi";
    done;
  

###############################################################################################

echo '=========================== Drive/Partition Info: ============================='>>"$Log";
echo>>"$Log";
 
[ -e $PartitionTable ] && cat $PartitionTable>>"$Log" || echo no valid partition table found>>"$Log";


echo "blkid -c /dev/null: ____________________________________________________________">>"$Log";
echo>>"$Log";
printf "$BlkidFormat" Device  UUID TYPE LABEL>>"$Log";
echo>>"$Log"
for dev in $(blkid -o device);do PrintBlkid $dev;done;
sort -u $BLKID>>"$Log";
echo>>"$Log";

if [ $(ls -R /dev/mapper 2>>$Trash | wc -l) -gt 2 ]
then

  echo '=============================== "ls -R /dev/mapper/" output: ==============================='>>"$Log";
   ls -R /dev/mapper>>$Log
  echo>>"$Log";
fi;
         




echo '============================ "mount | grep ^/dev  output: ==========================='>>"$Log";
MountFormat='%-16s %-24s %-10s %s\n';
Fis=':x:x:x:x:'
echo>>"$Log";
printf "$MountFormat" "Device" "Mount_Point"  "Type"  "Options" >>"$Log";
echo>>"$Log";
mount | grep ' / '| grep -v '^/'| sed  's/ on /'$Fis'/' |sed 's/ type /'$Fis'/'|sed  's/ (/'$Fis'(/'|awk -F $Fis '{printf "'"$MountFormat"'", $1, $2, $3, $4 }'>>"$Log";
mount | grep '^/dev'|sed  's/ on /'$Fis'/' |sed 's/ type /'$Fis'/' |sed  's/ (/'$Fis'(/'|awk -F $Fis '{printf "'"$MountFormat"'", $1, $2, $3, $4 }'>>"$Log";
echo>>"$Log";


#################   Write the content of Log1 to the log file
[ -e "$Log1" ] && cat "$Log1">>"$Log"; 

if [ -e $Unknown_MBR ]; 
then
 echo "=========================== Unknown MBRs/Boot Sectors/etc =======================">>"$Log";
 echo>>"$Log";
 cat $Unknown_MBR>>"$Log";
 echo>>"$Log";
fi;

if [ -e $FakeHardDrives ];
then 
 echo "=======Devices which don't seem to have a corresponding hard drive==============">>"$Log";
 echo>>"$Log";
 cat $FakeHardDrives>>"$Log";
 echo>>"$Log";
fi;
  

#####################  Write the Error Log to the log file
if [ -s $Error_Log ];
then
    echo "=============================== StdErr Messages: ===============================">>"$Log";
    echo>>"$Log";
    cat $Error_Log>>"$Log";
fi;

#####   Copy the  Log file to RESULTS file and make the  user the owner of Result file
cp "$Log" "$LogFile"
chown $(basename ~) "$LogFile";   

#######  Reset the Standard Output to the Terminal 
#exec 1>&-;
#exec 1>&6;
#exec 6>&-;

echo Finished. The results are in the file $(basename "$LogFile") located in "$Dir";
exit

---

### Post by kansasnoob on 2011-01-09
That's the actual contents of the script itself. You need to "run" the script using the terminal. 

Like if you saved the downloaded script to Desktop:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

Or if you saved it to Downloads:

```
sudo bash ~/Downloads/boot_info_script*.sh
```

When the script is finished running it'll tell you where the results.txt is saved.

It's the results.txt that we need to see.

---

### Post by adamogardner on 2011-01-09
Sorry, I should have worked backwards.

---

### Post by kansasnoob on 2011-01-09
> **adamogardner said:**
> Sorry, I should have worked backwards.

No problem :)

---

### Post by adamogardner on 2011-01-09
Results:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   469,968,895   469,966,848  83 Linux
/dev/sda2         469,970,942   488,396,799    18,425,858   5 Extended
/dev/sda5         469,970,944   488,396,799    18,425,856  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        cf1bdb47-5a1b-4320-9707-88cdf92c8a97   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        ba51e338-4484-4876-9027-94803155c982   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set cf1bdb47-5a1b-4320-9707-88cdf92c8a97
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set cf1bdb47-5a1b-4320-9707-88cdf92c8a97
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set cf1bdb47-5a1b-4320-9707-88cdf92c8a97
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=cf1bdb47-5a1b-4320-9707-88cdf92c8a97 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set cf1bdb47-5a1b-4320-9707-88cdf92c8a97
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=cf1bdb47-5a1b-4320-9707-88cdf92c8a97 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set cf1bdb47-5a1b-4320-9707-88cdf92c8a97
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set cf1bdb47-5a1b-4320-9707-88cdf92c8a97
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ba51e338-4484-4876-9027-94803155c982 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 186.9GB: boot/grub/core.img
 152.6GB: boot/grub/grub.cfg
    .8GB: boot/initrd.img-2.6.35-22-generic
 186.9GB: boot/vmlinuz-2.6.35-22-generic
    .8GB: initrd.img
 186.9GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  75 ac 5c 1f e1 8c a6 98  cf 3c ad f0 4b 51 ff 75  |u.\......<..KQ.u|
00000010  fb bf ea db f7 b5 3b 84  89 7c 44 ab 4a 9d ce df  |......;..|D.J...|
00000020  b6 b9 ed 20 43 41 72 c8  56 70 50 6d 84 22 e2 c9  |... CAr.VpPm."..|
00000030  00 2c a6 38 b7 a9 4d 72  36 d7 fa 2f 0c 31 1c 6e  |.,.8..Mr6../.1.n|
00000040  cd cb 73 8a d0 3f a9 cd  5a d0 b9 e4 e7 0d 13 c3  |..s..?..Z.......|
00000050  ac e2 03 65 cc 63 1f ac  ce 6d 1e 7f af 06 3b 92  |...e.c...m....;.|
00000060  48 55 ba 2b fb 46 bb 83  3e 4c e7 9c f2 f4 52 a0  |HU.+.F..>L....R.|
00000070  13 9c 71 59 58 67 dc 85  59 5f 19 9c 2f 19 0a 15  |..qYXg..Y_../...|
00000080  db e7 e4 67 b3 88 8d 9c  bb 75 f6 71 fd d7 4b 71  |...g.....u.q..Kq|
00000090  ff c6 1a e5 86 d8 69 5d  1d 2d 1b c7 29 d6 6b 6f  |......i].-..).ko|
000000a0  ab 5c 81 72 da 2a 80 b2  90 c1 26 b1 0f 12 62 c3  |.\.r.*....&...b.|
000000b0  e2 ef a4 21 3e 8b f7 57  6e b9 83 3c ac 9b 0a b2  |...!>..Wn..<....|
000000c0  81 d2 8b 3c b9 ed f6 ed  8e 4f 44 57 c4 5a 32 33  |...<.....ODW.Z23|
000000d0  73 a7 ec 6d 1b fe ce 1b  a0 e7 a9 98 c0 1f 2c bd  |s..m..........,.|
000000e0  ad 26 ce 3a 31 7e 76 55  61 6f ec 73 5e 87 7c e6  |.&.:1~vUao.s^.|.|
000000f0  7f b6 32 aa df 9c e7 ed  35 f6 8d b1 e2 76 14 59  |..2.....5....v.Y|
00000100  7b 3f 07 dc d2 66 3e b7  21 fa b2 f5 e5 4f 31 93  |{?...f>.!....O1.|
00000110  bd c8 04 81 a8 99 d4 bc  8d e4 ae 65 20 d7 a6 b5  |...........e ...|
00000120  99 d4 5b 02 67 d2 81 ad  f2 e7 3f 2f 05 94 f0 f1  |..[.g.....?/....|
00000130  5f 7c a5 b2 bd ea c1 a4  7a 95 1b 17 5e a0 c7 3e  |_|......z...^..>|
00000140  f1 cf 9b 8b cb dd 66 0a  5d fe 79 5d b9 2d c9 6a  |......f.].y].-.j|
00000150  83 4f e6 d1 21 b7 c5 40  83 97 54 57 50 cb 92 43  |.O..!..@..TWP..C|
00000160  f8 66 47 38 e7 e8 85 e2  79 a3 0e 7b 75 4d f2 f4  |.fG8....y..{uM..|
00000170  ae e7 16 85 f7 76 d1 75  94 fa 53 68 e7 63 39 bd  |.....v.u..Sh.c9.|
00000180  8d c0 9b d3 2a 7d 63 83  5e 94 24 38 1d 51 98 41  |....*}c.^.$8.Q.A|
00000190  d3 d6 4d 02 bc 67 cf 8c  29 4c 2a 8c 5e 57 c2 35  |..M..g..)L*.^W.5|
000001a0  b0 8c 1f b6 50 12 10 b3  5d 03 3a 1c ce ff 38 c2  |....P...].:...8.|
000001b0  be 14 0c 19 cb 8d e0 20  02 f7 ae 9f dd 08 00 fe  |....... ........|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 28 19 01 00 00  |...........(....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by adamogardner on 2011-01-09
ugly, huh?

---

### Post by Elfy on 2011-01-09
I've removed the script posts and added code tags to the script output.

Please use code tags - if you are doing a New Reply there is a button looks like # , select the text then hit the button.

If you are doing a Quick Reply - you can add the code tags by typing [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Thank you.

---

### Post by kansasnoob on 2011-01-09
> **adamogardner said:**
> ugly, huh?

Give me a little bit. I was just out checking on my goats and their water is frozen due to a failed heater. As soon as I get a propane heater fired up I'll be back in.

---

### Post by adamogardner on 2011-01-09
I'll be here.  thanks.

---

### Post by kansasnoob on 2011-01-09
Well, that's simple to read. You only have one OS installed, Ubuntu 10.10.

Probably because of problems I tried to point out in post #1 and post #15 here:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

Basically the "install alongside" option in the 10.10 installer often results in using the entire disc :(

One of several bug reports:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/659106](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/659106)

You should be able to get that Ubuntu booting by copy-n-pasting these commands using the Live CD:

```
sudo mount /dev/sda1 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo chroot /mnt
```

```
grub-install /dev/sda
```

```
update-grub
```

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt
```

But I assume you still want to install Win7. If so how much space do you want to give it?

---

### Post by hansolo4949 on 2011-01-09
> **adamogardner said:**
> I tried to install Windows7 today with an already cluttered hardrive.  I succeeded but lost ubuntu


Ouch. By installing windows after Ubuntu, you overwrote your grub. I think you should just boot from a livecd, and use gparted to wipe your hdd, install windows 7, THEN install Ubuntu. That should work perfectly:).

I don't think anything can go wrong with this unless you have some important files on there.

hansolo4949

---

### Post by adamogardner on 2011-01-09
My computer is of decent size.  I suppose I want to split it down the middle.  Half for Windows7 and half for ubuntu.

If there is only one operating system what happened to the other 5 or 6 that installed alongside several times?

---

### Post by adamogardner on 2011-01-09
> **hansolo4949 said:**
> Ouch. By installing windows after Ubuntu, you overwrote your grub. I think you should just boot from a livecd, and use gparted to wipe your hdd, install windows 7, THEN install Ubuntu. That should work perfectly:).

I don't think anything can go wrong with this unless you have some important files on there.

hansolo4949

I don't know how to use gparted.  I think that's how I screwed it up in the first place.  But I like the idea of starting fresh.

---

### Post by hansolo4949 on 2011-01-09
[LEFT]Okay, the simplest way to wipe the slate clean is to mount your hdd, (so it appears on your desktop) right-click it, then select "format this drive" or something like that (i'm in windows right now, so I can't verify that). you should be good to go! Remember, install windows first, then Ubuntu.

hansolo4949
[/LEFT]

---

### Post by kansasnoob on 2011-01-09
> **hansolo4949 said:**
> Ouch. **[COLOR="Red"]By installing windows after Ubuntu, you overwrote your grub.[/COLOR]** I think you should just boot from a livecd, and use gparted to wipe your hdd, install windows 7, THEN install Ubuntu. That should work perfectly:).

I don't think anything can go wrong with this unless you have some important files on there.

hansolo4949

But then reinstalling Ubuntu completely wiped Windows :( That's a bad, bad bug!

So, if adamogardner wants to start from scratch he should only use the "Specify partitions manually (advanced)" option. I prefer this method:

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

---

### Post by hansolo4949 on 2011-01-09
No, he/she can do that if they want to preserve data on that drive, but formatting it works just as well, and is a lot easier. All they need to to is install windows 7 after the wipe, then install Ubuntu. It should work!:)

hansolo4949

---

### Post by hansolo4949 on 2011-01-09
Oh, I see what you mean. I wonder why that's an issue... I installed Ubuntu alongside windows 7 without any issue whatsoever. Maybe adamogardner should try it again and see if it works?

hansolo4949

---

### Post by kansasnoob on 2011-01-09
> **adamogardner said:**
> I don't know how to use gparted.  I think that's how I screwed it up in the first place.  But I like the idea of starting fresh.

System > Administration > Gparted:

[ATTACH]180564[/ATTACH]

See where I highlighted Device > Create Partition Table? That'll wipe the drive and let you start fresh.

**[COLOR="Red"]Just don't use the "Install alongside" option from the 10.10 disc again![/COLOR]** I prefer this method:

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

---

### Post by adamogardner on 2011-01-09
Stupid question then, how do I mount the hdd (so it appears on my desktop)?

After rightclick > format this drive, what will happen?  The harddrive becomes wiped like new?  This would be okay with me.

---

### Post by adamogardner on 2011-01-09
> **kansasnoob said:**
> System > Administration > Gparted:

[ATTACH]180564[/ATTACH]

See where I highlighted Device > Create Partition Table? That'll wipe the drive and let you start fresh.

**[COLOR="Red"]Just don't use the "Install alongside" option from the 10.10 disc again![/COLOR]** I prefer this method:

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

Sounds perfect.  I'll let you know.

---

### Post by kansasnoob on 2011-01-09
> **hansolo4949 said:**
> Oh, I see what you mean. I wonder why that's an issue... I installed Ubuntu alongside windows 7 without any issue whatsoever. Maybe adamogardner should try it again and see if it works?

hansolo4949

I did extensive testing and I can assure you that there's a bug in the "Install alongside" option. I filed these bug reports:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/682429](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/682429)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657397](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657397)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950)

The first is the worst and it's actually a duplicate of:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/659106](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/659106)

But they're all related, as is this one:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/652852](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/652852)

Using the "install alongside" option is a real crap-shoot, sometimes you're lucky and sometimes you're not :(

---

### Post by adamogardner on 2011-01-09
It worked.  So I need to install under the method, [http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Thanks a bunch

---

### Post by adamogardner on 2011-01-09
nevermind

---

### Post by hansolo4949 on 2011-01-09
Yes, it will be like a new hdd when you format it:)


hansolo4949

---

