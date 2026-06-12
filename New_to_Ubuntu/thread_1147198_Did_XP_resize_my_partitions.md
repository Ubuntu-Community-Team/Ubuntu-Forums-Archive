---
title: "Did XP resize my partitions?"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by mlwalter on 2009-05-03
I recently (within the last week) did a clean install of both Windows XP and Ubuntu 9.04 to my laptop (Dell Inspiron 8600, 2GB RAM, 80G hard drive).  I've found in the past that installing XP first eases the dual boot setup process.  So I installed it, gave it 40GB of the hard drive and left the rest open for Ubuntu.  I thought I had installed Unbuntu on the rest of the hard drive, but when I tried to update this morning I found that I had only 120MB of space left on the Ubuntu partition and that the NTFS partition was taking up far greater than 40GB.  Is there any remedy for this that doesn't require me to reinstall everything again?

---

### Post by distroaddict on 2009-05-03
i've never heard of xp doing this.however a gparted screenshot may prove usefull

---

### Post by Spiritous on 2009-05-03
Type output of:

```
df
```

Please

---

### Post by Belgatom on 2009-05-03
I'm in the same predicament. I know the cause. I choose the side by side option in the install window. It wasn't all that clear that this would end up being a sort of Wubi install. I also created a windows installation first of 100Gb leaving me with 150Gb. Alas, now windows has over 246Gb and Ubuntu only 2-4Gb. I am used to working a lot in my home directory so 120Mb is definetely not enough. I am in the first stages, Ubuntu 9.04 is only hours old but I would love not having to redo the whole installation process (including windows). 

I thought about using Partition Magic and removing the Ubuntu partitions but the Grub will probably give me some trouble. Although I have been using Ubuntu for a couple of years now, I am still a beginner and the Grub scares me plenty. 

Help needed.

---

### Post by blueridgedog on 2009-05-03
> **mlwalter said:**
> I found that I had only 120MB of space left on the Ubuntu partition and that the NTFS partition was taking up far greater than 40GB.  Is there any remedy for this that doesn't require me to reinstall everything again?

You probably made a typo of some sort setting up Ubuntu and have a smaller / partition than you think.  The df command suggested by Spiritous will tell the tale.  You could also post 

```
sudo fdisk -l
```

---

### Post by Belgatom on 2009-05-03
Df produces this:

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5              2403420   2209884     71444  97% /
tmpfs                  1030956         0   1030956   0% /lib/init/rw
varrun                 1030956        92   1030864   1% /var/run
varlock                1030956         0   1030956   0% /var/lock
udev                   1030956       144   1030812   1% /dev
tmpfs                  1030956       488   1030468   1% /dev/shm
lrm                    1030956      2392   1028564   1% /lib/modules/2.6.28-11-generic/volatile

```

Sudo fdisk -l produces this:

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b336a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30075   241577406    7  HPFS/NTFS
/dev/sda2           30076       30401     2618595    5  Extended
/dev/sda5           30076       30379     2441848+  83  Linux
/dev/sda6           30380       30401      176683+  82  Linux swap / Solaris

```


Sorry to hijack the thread but I assume we have the same problem.

---

### Post by Spiritous on 2009-05-03
Boot into LIVE CD and go ALT+F2 and type: Gparted, Resize the NTFS to whatever and the Linux to Whatever :)

---

### Post by Belgatom on 2009-05-03
Well, I can resize the ntfs partition but both ext3 partitions are within an extended partition and the swap partition is being used by the live cd. I tried taking screenshot within live but does not seem to let me, i get an error.

Could it be that I need root priveleges to do this and that Live Session Users can not?

---

### Post by Spiritous on 2009-05-03
Ahh, I forgot! Open a terminal in LIVE CD and type:

```
sudo gparted &
``` Sorry :)

---

### Post by Belgatom on 2009-05-03
What is & supposed to do? I tried it but same result.

Both sda5 and sda6 are within sda2 and it will not let me resize sda2.

Busy (At least one logical partition is mounted), that is what it says when I get info on extende partition.

---

### Post by mlwalter on 2009-05-03
What is the normal allotment of each partition?

> **Spiritous said:**
> Ahh, I forgot! Open a terminal in LIVE CD and type:

```
sudo gparted &
``` Sorry :)

---

### Post by caljohnsmith on 2009-05-03
Belgatom, in gparted try right-clicking your sda6 swap partition and selecting "swapoff". Then you should be able to make whatever partition changes you want. 

John

---

### Post by Spiritous on 2009-05-03
Gawd... I don't know :S?! I've never seen this before..

---

### Post by Belgatom on 2009-05-03
> **caljohnsmith said:**
> Belgatom, in gparted try right-clicking your sda6 swap partition and selecting "swapoff". Then you should be able to make whatever partition changes you want. 

John

Thx, if I ever get in dat predicament again, I will. I had some time to kill seeing as it was sunday, so I started from scratch. This time, I understood the partition question better. I decided to extend my current windows partition to the full extent of my disk and then used the slider to get the correct partition size. 

I'm where I want to be now and have learned something new. Made my day interesting.

---

### Post by mlwalter on 2009-05-03
Thanks all for your help.  I was able to resize my Windows XP partition, but never quite figured out resizing/moving my Ubuntu partition.  So I just cleared out that partition and did a clean install of Ubuntu.  I'm back up and running with my newly resized partitions.

---

### Post by Eld.Raven on 2009-05-03
> **mlwalter said:**
>   I've found in the past that installing XP first eases the dual boot setup process.

Ive been told that its easier to install ubuntu before windows.

I have just installed ubuntu but I would like to dual-boot it with windows without reinstalling windows (since I got ******** of programs and games installed to my current windows installation). Is there anyway to dualboot without reinstalling windows?

---

### Post by Random-penguin on 2009-05-03
I'm sorry to say you've been misinformed. It's far easier to have Windows installed first then install Linux. Use gparted from you live disc to set up your NTFS partition and linux partitions (swap, / and /home....makes life easier). Then reinstall Windows, followed by Ubuntu to the linux partions you've already created. Hope this helps!

---

### Post by Eld.Raven on 2009-05-03
Sweet.. so all I need to do is find a program that I can use to dual-boot windows with right?

Cuz I havent reinstalled windows or something. But when I tried VirtualBox it told me that I needed to reinstall windows.

this is how I have done.
Windows installed (since long time ago)
Made a new partion (had some freespace over that I used) for Linux and installed it

and now all I want to do is dual boot them =P

---

### Post by caljohnsmith on 2009-05-03
> **Eld.Raven said:**
> Ive been told that its easier to install ubuntu before windows.

I have just installed ubuntu but I would like to dual-boot it with windows without reinstalling windows (since I got ******** of programs and games installed to my current windows installation). Is there anyway to dualboot without reinstalling windows?
You shouldn't need to reinstall Windows in order to get your dual-boot working. If you want help setting up your dual-boot, how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup so we can determine how best to set up your dual boot between Windows and Ubuntu.

Cheers,
John

---

### Post by Eld.Raven on 2009-05-03
Hmm this was a lot of code =O

```
#!/bin/bash
#to use this script:
#
#     sudo bash boot_info_script_028.sh
#or
#     su -
#     bash boot_info_script_028.sh
#
#date  3/20/09
#
#author  meierfra. 
# with  contributions from caljohnsmith
# (bothmembers of ubuntuforums.org)
#
#version 0.28
#
#hosted at: http://sourceforge.net/projects/bootinfoscript/
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
#    displays  boot configuration files.
#All information is written to the file "RESULTS.txt" in the
#    same folder as the script

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
################# Since all the important files in these folder are alreadt displayed
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
Boot_Prog="
     /bootmgr /BOOTMGR
     /boot/bcd /BOOT/bcd /Boot/bcd  /boot/BCD /BOOT/BCD  /Boot/BCD
     /Windows/System32/winload.exe /WINDOWS/system32/winload.exe /WINDOWS/SYSTEM32/winload.exe /windows/system32/winload.exe
     /Windows/System32/Winload.exe /WINDOWS/system32/Winload.exe /WINDOWS/SYSTEM32/Winload.exe /windows/system32/Winload.exe
     /grldr /GRLDR
     /ntldr /NTLDR
     /NTDETECT.COM    /ntdetect.com
     /NTBOOTDD.SYS    /ntbootdd.sys
     /wubildr.mbr    /ubuntu/winboot/wubildr.mbr
     /ubuntu/disks/root.disk
     /ubuntu/disks/
     /ubunut/disks/swap.disk
     /core.img   /grub/core.img     /boot/grub/core.img
     /boot/map      /map
     /DEFAULT.MNU /default.mnu
     "

############### List of files whose contents will be displayed.
Boot_Files="
    /boot/grub/menu.lst /grub/menu.lst  /NST/menu.lst    /menu.lst
    /grub.cfg    /grub/grub.cfg    /boot/grub/grub.cfg
    /ubuntu/disks/boot/grub/menu.lst /ubuntu/disks/install/boot/grub/menu.lst /ubuntu/winboot/menu.lst
    /boot/grub/grub.conf    /grub/grub.conf    /grub.conf
    /boot.ini  /BOOT.INI
    /etc/fstab
    /etc/lilo.conf  /lilo.conf
    "

############### List of files whose end point (in GB) will be displayed.
GrubError18_Files="
    boot/grub/menu.lst    grub/menu.lst    menu.lst /NST/menu.lst
    ubuntu/disks/boot/grub/menu.lst
    boot/grub/grub.conf    grub/grub.conf    grub.conf
    grub.cfg    grub/grub.cfg    boot/grub/grub.cfg
    boot/grub/stage2    grub/stage2    stage2
    boot/vmlinuz*  vmlinuz*    ubuntu/disks/boot/vmlinuz*
    boot/initrd*  initrd*    ubuntu/disks/boot/initrd*
    boot/kernel*.img
    "


#######  Directory containing the script.

Dir=$(cd $(dirname $0);pwd);

########  To avoid overwriting existing files, look for a non-existing file 
########  RESULT.txt RESULTS1.txt  RESULTS2.txt ... 

LogFile=$Dir/RESULTS
while ( [ -e $LogFile$j.txt ] )
    do  
      ((j++))
      wait;
    done
LogFile=$LogFile$j.txt  #### The RESULTS file.

######  Redirect stdout to RESULT File
exec 6>&1   
exec >$LogFile

########### Create previously non-existing  folder of the form
##########  /tmp/BootInfo  /tmp/BootInfo1, /tmp/BootInfo2 ... 

Folder=/tmp/BootInfo
while (! mkdir $Folder$i 2>/dev/null)
    do  
      ((i++))
      wait;
    done
Folder=$Folder$i

cd $Folder
Wubi=$Folder/Wubi
mkdir Wubi                      # Folder to mount Wubi installs.
Log1=$Folder/Log1               #  Most of the information which is not part of
                                #the summary is recorded in this file.
Error_Log=$Folder/Error_Log     #  File to catch all unusal Standar Errors 
Trash=$Folder/Trash             #  File to catch all usual Standard Errors
                                #these messagges will not be included in the RESULTS       
Mount_Error=$Folder/Mount_Error # File to catch Mounting Errors
Unknown_MBR=$Folder/Unknown_MBR # File to record all unknown MBR and Boot sectors. 
Tmp_Log=$Folder/Tmp_Log         # File to temporarily hold some information.
PartitionTable=$Folder/PT       #  File to store the Partition   Table
FakeHardDrives=$Folder/FakeHD   # File to list devices which seem to have correspinding drives.
exec 2>$Error_Log               #Redirect all standard error to the file Error_Log

All_Hard_Drives=$(ls /dev/hd? /dev/sd? 2>>$Trash );   ### List of all Hard drives.

####Arrays to informattion about Partition hold the name, starting sector, ending sector, size in sector, Partition Type, Filesystem typw, UUID, Kind( Logical, Primary Extended), Hardrive, boot flag of the paritions.

declare -a NamesArray StartArray EndArray SizeArray TypeArray  FileArray UUIDArray KindArray DriveArray BootArray ParentArray LabelArray SystemArray


#####Arrays to hold information about the hardrives.
declare -a HDName  FirstPartion LastPartition  HDSize HDMBR HDHead HDTrack HDCylinder HDPT HDStart DEnd HDUUID;

PI=-1 ## Counter for the identification number of a partition. (each partition gets unique number)
HI=0 ## Counter for the identification number of a hard drive. (each hardrive gets unique number)
PTFormat='%-10s %4s%14s%14s%14s %3s %s\n';  ### standard format to use for Partition table,
           


##### A function which converts to two digit hexcode of a partition type 
#function HexToSystem() {
#echo $(sfdisk -T 2>>$Trash | grep -e '^[ ]*'$1' ' |  sed 's/[ ]*[^ ]*  //')    
#}
# The follwing list is taken from sfdisk -T  and 
#  http://www.win.tue.nl/~aeb/partitions/partition_types-1.html
#  work in progress
function HexToSystem() {
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
dd) sysetm="Dell Media Direct";;
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
function UUIDToSystem() {
local type=$1 system
case $type in
    00000000000000000000000000000000)  system="Empty";;
    41ee4d02e733d3119d690008c781f39f)  system="MBR partition scheme";;
    28732ac11ff8d211ba4b00a0c93ec93b)  system="System/Boot Partition";;
    a2a0d0ebe5b9334487c068b6b72699c7)  system="Linux (usually)";; 
    6dfd5706aba4c44384e50933c84b4f4f)  system="Linux Swap";;
    16e3c9e35c0bb84d817df92df00215ae)  system="Microsoft Windows";;
    79d3d6e607f5c244a23c238f2a3df928)  system="LVM";;
    005346480000aa11aa1100306543ecac)  system="HFS+";;
                                   *)  system="-";
                                       echo Unknown GPT Partiton Type>>$Unknown_MBR;
                                       echo  $type >>$Unknown_MBR;;   
esac;
echo $system;
   }

##### Function which insert a comma every  third digits of a number
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




## Reads and display the  a partition table of an extended partitons    ###########
#############  and check it for errors                       #####################
#  This function can be applied iteratively  to read the extended partiton table           
# Variable 1:  HI of hard drive 
# Variable 2:  Start Sector of the extended Partition,
# Variable 3:  Number of partitions in table (4 for regular PT, 2 for logical
# Variable 4:  File for storing the partitions table.
# Variable 5:  Format to use for displaying the partition table.  
# Variable 6:  PI of the primary extended partition containing the extended partition.
#              ""  for hard drive
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
      # sector  of primary extented partition otherwise
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
        [[ "${HDPT[$HI]}"  = "BootIt"  ]] && label="${NamesArray[$EPI]}""_" || label=$drive;
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
    local HI=$1 drive MPT_file=$2 Size N=0 i=0  BINGIndex  Label   Start End  Type BINGUnknown format Size System;
    drive="${HDName[$HI]}";
    format='%-18s %4s%14s%14s%14s %3s %-15s %3s %2s\n';
    printf "$format"  Partition Boot Start End Size Id System  Ind "?">> $MPT_file; 
    N=$(hexdump -v -s 534  -n 1 -e  '"%u"' $drive); 
    while [[ $i -lt "$N" ]]
    do
        ((PI++))
        BINGUnknown=$(hexdump -v -s  $((541+28*i))  -n 1 -e '"%x"'  $drive)
    Start=$(hexdump -v -s  $((542+28*i))  -n 4 -e '4 "%u"'  $drive);
      End=$(hexdump -v -s  $((546+28*i))  -n 4 -e '4 "%u"'  $drive);
    BINGIndex=$(hexdump -v -s  $((550+28*i))  -n 1 -e '"%u"'  $drive);
    Type=$(hexdump -v -s  $((551+28*i))  -n 1 -e '"%x"'  $drive);
        Size=$((End-Start+1));
    Label=$(hexdump -v -s  $((552+28*i))  -n 15 -e '"%_u"'  $drive| sed -e  s/nul[^$]*//);
        System=$(HexToSystem $Type);
        printf "$format"  "$Label" "-" "$(InsertComma $Start)" "$(InsertComma $End)" "$(InsertComma $Size)" "$Type" "$System"  "$BINGIndex" "$BINGUnknown">>$MPT_file;
           NamesArray[$PI]=$Label
           StartArray[$PI]=$Start;
           TypeArray[$PI]=$Type;
           SizeArray[$PI]=$Size;
           SystemArray[$PI]=$System;
           EndArray[$PI]=$End;
           DriveArray[$PI]=$HI;
  
           
            if [[ $Type = "f" || $Type = "5" ]];
        then
                 KindArray[$PI]="E";
                 ParentArray[$PI]=$PI;
         ReadPT $HI  $Start  2  $MPT_file "$format"  $PI  4 ;  
            else
                KindArray[$PI]="P";
                ParentArray[$PI]="";
        fi;
         ((i++))
         
    done;
}

#################   Check partition table for errors  ################################
###  
###  This function checks whether any two partitions  overlap.
###  and the logical partitions are inside the extended parition.
###  Variable 1:        First partition to consider
###  Variable 2:        Last Partition to consider
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
##########  Determine the embeded location of core.img  for a Grub2 stage1 file,
##########  look  for the core.img and,  the path of the Grub Folder.
#############################################################################

core_loc (){
  local stage1=$1  hi;
  offset=$(hexdump -v -s 68 -n 4 -e '4 "%u"' $stage1 2>>$Trash);
  dr=$(hexdump -v -s 76 -n 1 -e '"%d"' $stage1);
  pa="T"
    for hi in ${!HDName[@]};
  do
     hdd=${HDName[$hi]};
     if [ $offset -lt  ${HDSize[hi]}  ];
     then
     tmp=$(dd if=$hdd skip=$offset count=1 2>>$Trash | hexdump -v    -n 4 -e '"%x"');
         if [ "$tmp" = 1bbe5652 ];  ###  If conf.img  file was found.
         then
              dd if=$hdd skip=$((offset+1)) count=1 of=$Tmp_Log 2>>$Trash;
              pa=$(hexdump -v  -s 20  -n 1 -e '"%d"' $Tmp_Log);
              core_hdd=$hdd;
          Grub_String=$(hexdump -v -s 32 -n 64 -e '"%_u"' $Tmp_Log);
              Core_Dir=$(echo  $Grub_String | sed s/nul[^$]*//);
         fi;
     fi;
 done;
 dr=$((dr-127))
 Core_Msg=$(echo  looks at sector $offset )        
 if [ "$dr" = 128 ];
 then
      Core_Msg=$(echo $Core_Msg of the same hard drive) 
 else
      Core_Msg=$(echo $Core_Msg on boot drive \#$dr)
 fi;
 Core_Msg=$(echo $Core_Msg for core.img);
                    
 if [ "$pa" = "T"  ]   #### core.img  found.
 then
      Core_Msg=$(echo $Core_Msg, but core.img can not be found at this location.); 
 else
     pa=$((pa+1))
     Core_Msg=$(echo $Core_Msg  and on )                       
     if [ "$pa" = 256 ];
     then
         Core_Msg=$(echo $Core_Msg the same partition) 
     else
         Core_Msg=$(echo $Core_Msg  partition \#$pa )
     fi;
     Core_Msg=$(echo $Core_Msg for  $Core_Dir.)
  fi;
}
#######################################################################################


## "titlebar_gen" generates the $name$file title bar to always be either 79 or 80 chars total in length:
titlebar_gen () {
        name_file="$1$2:"; name_file_length=${#name_file}
        equal_signs_line_length=$(((80-name_file_length)/2-1)); equal_signs_line=""
        for length in $(seq $equal_signs_line_length); do
              equal_signs_line='='$equal_signs_line
        done;
                echo >> $Log1;
        echo "$equal_signs_line $name_file $equal_signs_line" >> $Log1;
                echo >> $Log1;
                }



echo '============================= Boot Info Summary: =============================='; echo

#####   Search  for  hard drives which don't exists   or have a  corrupt partition table
#####   All hard drives which a valid partition table are stored   in $Hard_Drives
for drive in  $All_Hard_Drives;
do
        size=$(fdisk -s $drive 2>>$Trash);        
        if [ 0 -lt $size 2>>$Trash ];
    then
            size=$((2*size));
            Hard_Drives=$Hard_Drives" "$drive;
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
            
        else
            echo -n "$(basename $drive) " >>$FakeHardDrives;
    fi;
done;
############ Identify the MBR of each  hard drive.
echo "Identifying MBRs..." >&6;
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
              BL=Grub$Grub_Version;;
###############################  If Grub2 is in the MBR   #####################################

        eb4c) BL=Grub2;
              offset=$(hexdump -v -s 68 -n 4 -e '"%u"' $drive);### 0x44 contains the offset of the next stage
              if  [ "$offset" != 1 ];   ###if  Grub2 is  installed without  Core. 
          then
                  core_loc $drive;
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
############################################################################################## 
     33c0) BL=Windows;;
    fa31) BL=Syslinux;;
    faeb) BL=Lilo;; 
        eb04) BL=Solaris;;
    fc31) BL=Testdisk;;
        fc33) BL=Gag;;
    eb5e) BL=Grub4Dos;;
    b800) BL=Plop;;
    33ff) BL='HP/Gateway';;
        31c0) BL="Acer 3";;
         ebe) BL=ThinkPad;;
        fa33) BL="No boot loader";; 
        fabe) BL="No boot loader?";;
        fab8) BL="No boot loader";;   
    fceb) BL="BootIT NG";;
              #PT_Kind="BootIT";
              #PT_Location=$hi;;
          00) BL="No boot loader";;
       *) BL="No known boot loader"
              echo "Unknown MBR on $drive" >> $Unknown_MBR;
              echo >> $Unknown_MBR;
              hexdump -v -n 512 -C $drive >> $Unknown_MBR;
              echo >> $Unknown_MBR;;
        esac;
        ##Output message at beginning of summary that gives MBR info for each drive:
        echo -n " => "
        echo "$BL $Message" | fold -s -w 75 | sed -e '2~1s/.*/    &/'   
        HDMBR[$hi]=$BL;
    done
    echo;
######################################################################################
#############   Store and Display all the partitions tables.##########################
for HI in ${!HDName[@]};
    do
    drive=${HDName[$HI]};
    echo "Computing Partition Table of $drive..." >&6;
    FirstPartition[$HI]=$((PI+1));
    FP=$PI;
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
      BootIt) FirstPartition[$HI]=$((PI+1));
               echo -n  BootIT NG Partition Table detected>>$PartitionTable;
              [[ "${HDMBR[$HI]}" = "BootIT NG" ]] && echo . >>$PartitionTable || echo , but does not seem to be used. >>$PartitionTable;
              echo>>$PartitionTable;
              ReadEMBR  $HI $PartitionTable;
          echo >>$PartitionTable;
              if [ "${HDMBR[$HI]}" = "BootIT NG" ];
          then
                   LastPartition[$HI]=$PI;
                   CheckPT  ${FirstPartition[$HI]} ${LastPartition[$HI]}  $PartitionTable $HI; 
          else
                   FirstPartition[$HI]=$FP;
              fi;;
         EFI) FirstPartition[$HI]=$((PI+1));
              EFIee=$(hexdump -v -s 450 -n 1 -e '"%x"' $drive);
              echo -n  GUID Partition Table detected>>$PartitionTable;
              [[ "$EFIee" = "ee" ]] && echo . >>$PartitionTable || echo ,but does not seem to be used. >>$PartitionTable ;
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
for (( pi = FirstPartition[$hi]; pi <= LastPartition[$hi]; pi++ ));  ## And then loop through                                                                      ###the partition  on that drive
do
      BSI="";
      BFI="";    
      part_type=${TypeArray[$pi]};  #### Type of the partition according to fdisk
      start=${StartArray[$pi]};
      size=${SizeArray[$pi]};
      end=${EndArray[$pi]};
      kind=${KindArray[$pi]};
      if [[ "${HDPT[$hi]}" = "BootIt" ]];
      then
          name="${NamesArray[$pi]}";
          mountname=$(basename $drive)$pi;
          part=$(losetup -f --show  -o $((start*512)) $drive)
         #### --sizelimit $((size*512))    --sizelimit seems to be a recently added option for losetup.  Failed on Hardy 
      else
          part=${NamesArray[$pi]};
          name=$(basename $part);  ####  Name of the partition (/dev/sda8 -> sda8)
        
          mountname=$name;      
fi;
       echo "Searching $name for information... " >&6;
       type=$(blkid -c /dev/null -s TYPE $part 2>$Tmp_Log);  ##### type of file system according to blkid
       type=${type#*=\"};
       type=${type%\"*};
       FileArray[$pi]=$type;
       # part_number=${part:8} 

      echo $name: _________________________________________________________________________; echo
      mkdir "$mountname"    ####  Directory where the partition will be mounted.
      if [[ "${KindArray[$pi]}" = "E"  &&  "$type" = "" ]] ;  #### Check for extended partion.
         then
     type="Extended Partition";
     cat $Tmp_Log>>$Trash;  ### Don't display  the error message from blkid for extended partition
     else
         cat $Tmp_Log>>$Error_Log
      fi;
      echo "    File system:       "$type;  ### Display the File System Type

     
          Bytes8081=$(hexdump -v -s 128 -n  2 -e '/1 "%x"'  $part)   #### Use bytes 0x80,81 to idendtify Boot sectors
          case    $Bytes8081    in
   fa33|8ec0|8cd) BST="Windows XP";;
            b6d1) BST="Windows XP: Fat32";;
        55aa) BST="Windows Vista";;
            e9d8) BST="Windows Vista";;
            55cd) BST="Fat32";;
             10f) BST="HP Recovery";;
            3a5e) BST="Recovery:Fat 32";;
            89e)  BST="MSDOS5.0: Fat 16";;
            bd0)  BST="MSWIN4.1: Fat 32";;
            6f6e) BST="-";;  #MSWIN4.1: Fat 32"
            7cc6) BST="MSWIN4.1: Fat 32";;
            745)  BST="Vista:  Fat 32";;
            19d)  BST="BSD4.4: Fat32";;
 b60 | 211 | e00) BST="Dell Utility: Fat16";; 
            8ed0) BST="DEll Recovery: Fat32";;
            4445) BST="DEll Restore: Fat32";; 
            6974) BST="BootIt: Fat16";;
            6f65) BST="BootIt: Fat16";;
            7cc6) BST=Win_98;;
            734)  BST=Dos_1.0;;
            2d5e) BST=Dos_1.1;;
        7815) BST=Fat32;;
            6f74) BST=Fat32;;
            696e) BST=Fat16;;
            6616) BST=Fat16;;
     ####### if Grub, Grub 2 or Lilo  is  in the boot sector,  ########
     ####### investigate the embedded information              ########
            48b4) BST=Grub2;    
                  core_loc $part;
                  BSI=$(echo $BSI Grub2 is installed in the boot sector of $name  and $Core_Msg);;
     aa75 | 5272) BST=Grub;
                  stage2_loc $part;
                  BSI=$(echo $BSI Grub$Grub_Version is installed in the boot sector of $name  and $Stage2_Msg);;
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
              else           ###### Otherwise, display the boot sector, so we that we might identify it and add it to the list of known boot sectors.
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
           echo "    Boot sector type:  "$BST  

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
             # MFT_MFT=$( dd if=$part skip=$MFT_Sector count=1 2>>$Trash| hexdump -v -e '4/1 "%x"' | grep "432404d046054")
               
       else 
               MFT_FILE="";
              # MFT_MFT="";
           fi;
           MFT_Mirr_Cluster=$(hexdump -v -s 56 -n 4 -e '"%d"' $part);
           MFT_Mirr_Sector=$(( MFT_Mirr_Cluster * SectorsPerCluster ));
           if [[ "$MFT_Mirr_Sector" -lt "$size" ]];
           then
           MFT_Mirr_FILE=$(dd if=$part skip=$MFT_Mirr_Sector count=1 2>>$Trash | hexdump -v    -n 4 -e '"%_u"');
  
         #  MFT_Mirr_MFT=$(dd if=$part skip=$MFT_Mirr_Sector count=1 2>>$Trash |hexdump -v -e '4/1 "%x"' | grep "432404d046054")
           else 
               MFT_Mirr_FILE="";
            #   MFT_Mirr_MFT="";
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
      echo -n "    Boot sector info:  "
      echo $BSI | fold -s -w 55 |  sed -e '2~1s/.*/                       &/'

      ####Exclude Partitions which contain no information,     #########
      ##### or which we (currently) don't know how to  accces. #########  
      if [ "$type" != "swap" ]  && [ "$type" != "Extended Partition"  ] && [ "$type" != "unknown volume type" ] && [ "$type" != "LVM2_member" ]  && [ "$type" != "linux_raid_member" ] && [ "$type" != "crypto_Luks" ] ; 
      then     
 
         CheckMount=$(mount| grep "$part " |sed '2,$ d');
         CheckMount=${CheckMount% type*};
         CheckMount=${CheckMount#* on };   
          ### Check wether partition is already mounted
         [[ "$CheckMount" != "" ]]  &&  mountname=$CheckMount;  #### if yes,use existing mount point.
         if  [ "$CheckMount" != "" ] || mount -t "$type" $part "$mountname" 2>$Mount_Error  || ( [ "$type" = ntfs ] && ntfs-3g  $part "$mountname" 2>>$Mount_Error  ) ;     ####### Try to mount partition
         then     ############  if partition is  mounted.
         #####Try to identify the Operating  System (OS) by  looking for files specific to the OS
       OS=""
       [ -e "$mountname/Windows/System32/config/BCD-Template" ] ||  [ -e "$mountname/windows/system32/config/bcd-template" ] || [ -e "$mountname/WINDOWS/System32/config/BCD-Template" ] ||
  [ -e "$mountname/WINDOWS/system32/config/BCD-Template" ] && OS="Windows Vista"

       [ -e "$mountname/Windows/System32/config/SecEvent.Evt" ] ||  [ -e "$mountname/WINDOWS/system32/config/SecEvent.Evt" ] || [ -e "$mountname/WINDOWS/system32/config/secevent.evt" ] || [ -e "$mountname/windows/system32/config/secevent.evt" ] && OS="Windows XP"

       [ -e "$mountname/etc" ] && OS=$(sed -e 's/\\. //g' -e 's/\\.//g' -e 's/^[ \t]*//' "$mountname"/etc/issue)
  
    

##OS=$(cat /etc/lsb-release | grep "DISTRIB_DESCRIPTION"|awk -F = '{print $2}')
     
 ####################################  search for  the files in $Bootfiles   ########################
###################################### and if found, display there contained ########################
       BootFiles=""    
       for file in $Boot_Files;
       do
           if [ -f "$mountname"$file ];
              then BootFiles=$(echo $BootFiles"  "$file);
              if ! [ -h "$mountname"$file ];  ### check whether file is  symlink
              then
                 titlebar_gen "$name" $file;    ##generates a titlebar above each file/dir listed
                 cat "$mountname"$file >> $Log1;  ### if not a symlink, display content.
              fi;
       fi;
       done;
################# Search for Wubi   and if found display fstab  ###################################

if [ -f "$mountname""/ubuntu/disks/root.disk" ];
      then          
          if mount -o loop  "$mountname""/ubuntu/disks/root.disk"  $Wubi;
      then
              titlebar_gen "$name"  Wubi;
              echo -n "Operating System: " >>$Log1;
              [ -e "$Wubi/etc/lsb-release" ] && cat $Wubi/etc/lsb-release | grep "DISTRIB_DESCRIPTION"|awk -F = '{print $2}' >>$Log1
          if [ -f "$Wubi/etc/fstab" ];
          then
                  echo >>$Log1;
          cat "$Wubi/etc/fstab" >> $Log1;
              else
                 echo "/etc/fstab was not found" >> $Log1;
              fi;
       else
             titlebar_gen "$name" " Wubi";
             echo ubuntu/boot/root.disk was found, but could not be mounted >> $Log1;
           fi;
           umount "$Wubi" || umount -l "$Wubi"; 
       fi;            
             
#################################### Search for the programs in $Boot_Prog, ###############
################################### if found disply where names.           ###############

       for file in $Boot_Prog;   
       do
           if [ -f "$mountname"$file ];
              then BootFiles=$(echo $BootFiles"  "$file);          
       fi;
       done;


################### Search for the directories related to Booting ########################
##################, if found display the list of files             #######################

#       for file in $Boot_Dir;  #directories in that directory.
#       do
#          if [ -d "$mountname"$file ];
#          then
#          BootFiles=$(echo $BootFiles"  "$file); 
#              titlebar_gen "$name" $file    ##generates a titlebar above each file/dir listed
#              ls -la  "$mountname"$file >> $Log1 ; 
#             
#      fi;
#       done;

####################  Search for files containing boot codes #################################

       for file in $Boot_Codes_Dir    #####  loop through all directories which might conatin boot_code files
       do
       if [ -d "$mountname"$file ];   ##### if such directory exits
       then  
           for loader in $( ls  "$mountname"$file );  ##### look at the content of that directory 
           do
                  if [ -f "$mountname$file$loader" ];  ####  it its a file
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
                      if [ "$sig"  = "GRUB" ];   ##### Grub and Grub2  have "Grub" written at 0x17f
                      then
                          sig2=$(hexdump -v -n  2 -e '/1 "%x"' "$mountname"$file$loader);
                          if [[ "$sig2" = "eb48" ]] ### distinguish Grub and Grub 2 by the
                                                    ##### first two bytes.
                          then
                               stage2_loc  "$mountname"$file$loader;
                               BFI=$(echo $BFI" "Grub$Grub_Version in the file  $file$loader $Stage2_Msg);
                          else 
                               core_loc  "$mountname"$file$loader;
                               BFI=$(echo $BFI" "Grub2  in the file  $file$loader $Core_Msg); 
                          fi;    
                      fi;
                      
           fi;
            done; ## End of loop through the files in a particular  Boot_Code_Directory
            fi;
        done   ## End of the loop through the Boot_Code_Directories.

######### Determine the end point of all files in the GrubError18_Files list
    
     echo >$Tmp_Log;
     counter=0;
     cd "$mountname";
     for file in $(ls $GrubError18_Files 2>>$Trash);
     do
     if [[ -f $file ]]
     then 
     BlockSize=$(filefrag -v $file| grep "Blocksize" |awk '{print $6}');
     LastBlock=$(filefrag -v $file| grep "Last block"  |awk '{print $3}');
     EndGB=$(echo $(((BlockSize*LastBlock + 512*start)/100000000 ))|sed 's/\(.\)$/\.\1/')
     printf "%6sGB: %-s\n" $EndGB "$file" >>$Tmp_Log;
         ((counter++)); 
     fi;
     done;
     cd $Folder;
     if [ $counter != 0 ];
     then
      titlebar_gen "$name"  ": Location of files loaded by Grub";
          cat $Tmp_Log>>$Log1;
     fi;
     echo >$Tmp_Log;

      if [[ $BFI != "" ]];
      then
          echo -n "    Boot file info:     "
          echo $BFI | fold -s -w 55 |  sed -e '2~1s/.*/                       &/'
      fi;
      echo "    Operating System:  "$OS | fold -s -w 55 | sed -e '2~1s/.*/                       &/'     
      echo -n "    Boot files/dirs:   "
      echo $BootFiles | fold -s -w 55 |  sed -e '2~1s/.*/                       &/'
     
        if [ "$CheckMount" = "" ];  ## if partition was mounted by the script
        then
            umount "$mountname" || umount -l "$mountname";          
        fi;
     else     ############### if partition failed to mount  
       echo "    Mounting failed:";  
     cat $Mount_Error; 
     fi;  ### end of Mounting "if then else"
     fi;  ### end of Partition Type "if then else"
     echo;
     [[ "${HDPT[$hi]}" = "BootIt" ]] && losetup -d $part;
     done;  ### end of partition loop
     done;  ### end of hard drive loop



echo '=========================== Drive/Partition Info: ============================='; echo
 
[ -e $PartitionTable ] && cat $PartitionTable || echo no valid partition table found ;

echo "blkid -c /dev/null: ____________________________________________________________";
echo; blkid -c /dev/null
echo;
echo '=============================== "mount" output: ===============================';
echo;
mount;
echo;

#################   Write the content of Log1 to the RESULTS file
[ -e $Log1 ] && cat $Log1; 

if [ -e $Unknown_MBR ]; 
then
 echo "=========================== Unknown MBRs/Boot Sectors/etc =======================";
 echo;
 cat $Unknown_MBR;
 echo;
fi;

if [ -e $FakeHardDrives ];
then 
 echo "=======Devices which don't seem to have a corresponding hard drive==============";
 echo;
 cat $FakeHardDrives;
 echo;
fi;
  

#####################  Write the Error Log to the RESULT file
if [ -s $Error_Log ];
then
    echo "=============================== StdErr Messages: ===============================";
    echo;
    cat $Error_Log;
fi;

#####   Make the  user the owner of Result file
chown $(basename ~) $LogFile;   

#######  Reset the Standard Output to the Terminal 
exec 1>&-;
exec 1>&6;
exec 6>&-;

echo Finished. The results are in the file $(basename $LogFile) located in $Dir;
exit



```

---

