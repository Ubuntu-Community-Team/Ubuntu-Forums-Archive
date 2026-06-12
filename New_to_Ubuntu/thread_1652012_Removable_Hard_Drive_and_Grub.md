---
title: "Removable Hard Drive and Grub"
date: 2010-12-24
forum: New to Ubuntu
---

### Post by diggingeagle on 2010-12-24
Well, I have a seagate removable hard drive, and I thought to myself, "I would very much like to have my own little computer everywhere I go, and have my things available to me." So I downloaded the ubuntu .iso, and I selected my seagate hard drive to be installed to. I partitioned it in half, if it matters, so 1 half of it could still be used for normal storage.
 
How it went wrong:
There was a boot list and It let me select whether I wanted to boot linux or windows xp, which is on the computer's hard drive. I want it so that when I plug in my portable drive, it takes boot priority and boots linux. But it seems like the computer thinks they are one hard drive now.
 
And, when I remove this portable hard drive, nothing will boot. It says something of "Grub"
 
I am obviously very new to Ubuntu, and not extremely good at computers as a whole. I hope the answer's obvious, for my sake. Thanks for any answers.

---

### Post by amjjawad on 2010-12-24
> **diggingeagle said:**
> Well, I have a seagate removable hard drive, and I thought to myself, "I would very much like to have my own little computer everywhere I go, and have my things available to me." So I downloaded the ubuntu .iso, and I selected my seagate hard drive to be installed to. I partitioned it in half, if it matters, so 1 half of it could still be used for normal storage.
 
How it went wrong:
There was a boot list and It let me select whether I wanted to boot linux or windows xp, which is on the computer's hard drive. I want it so that when I plug in my portable drive, it takes boot priority and boots linux. But it seems like the computer thinks they are one hard drive now.
 
And, when I remove this portable hard drive, nothing will boot. It says something of "Grub"
 
I am obviously very new to Ubuntu, and not extremely good at computers as a whole. I hope the answer's obvious, for my sake. Thanks for any answers.

Hello and welcome :)

In my signature, check the last link "How to avoid Wubi". There's step by step how to install Ubuntu on an external HDD.

Your problem is very easy to fix.
Most likely, you have installed Ubuntu's boot loader (GRUB2) in the MBR of your internal HDD. Having the said, Ubuntu's boot loader has over written Windows Boot Loader. Thus, every time you need to boot both, you need to plug your external HDD.

Just to make sure my theory is correct, kindly post the result of the boot script and wrap up the text with "CODE" tags or use "#".

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Most likely all what you need is to fix Windows Boot Loader and re-install GRUB2 in the MBR of your external HDD. But, let's see the boot script result first.
Don't forget to plug your external HDD, make sure your BIOS will boot from it and run that script using the LiveCD.

Good luck ;)

---

### Post by diggingeagle on 2010-12-24
Sorry if this is excess and hard to read, but I started copying at the first sight of grub.
 
[HTML]################################ If Grub is in the MBR   #########################
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
[/HTML]

---

### Post by amjjawad on 2010-12-24
Please read the instructions in this link carefully:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

You have posted the script that you suppose to run :)
We need to see the result not the script.

---

### Post by diggingeagle on 2010-12-24
Oh, so sorry. Here it is.

[HTML]Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107861504 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   967,561,215   967,559,168  83 Linux
/dev/sdb2         967,563,262   976,771,071     9,207,810   5 Extended
/dev/sdb5         967,563,264   976,771,071     9,207,808  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        909C26A9F4C700EA                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        f8ece369-d72c-41f5-8838-29a5d0d4bd2b   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        baab7256-b8f6-4362-a6ee-725757c5dcd3   swap                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

[boot loader] 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect 

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set f8ece369-d72c-41f5-8838-29a5d0d4bd2b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set f8ece369-d72c-41f5-8838-29a5d0d4bd2b
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
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set f8ece369-d72c-41f5-8838-29a5d0d4bd2b
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=f8ece369-d72c-41f5-8838-29a5d0d4bd2b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set f8ece369-d72c-41f5-8838-29a5d0d4bd2b
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=f8ece369-d72c-41f5-8838-29a5d0d4bd2b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set f8ece369-d72c-41f5-8838-29a5d0d4bd2b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set f8ece369-d72c-41f5-8838-29a5d0d4bd2b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 909c26a9f4c700ea
    drivemap -s (hd0) ${root}
    chainloader +1
}
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=baab7256-b8f6-4362-a6ee-725757c5dcd3 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


 330.9GB: boot/grub/core.img
 391.0GB: boot/grub/grub.cfg
    .8GB: boot/initrd.img-2.6.35-22-generic
 330.9GB: boot/vmlinuz-2.6.35-22-generic
    .8GB: initrd.img
 330.9GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf sdg [/HTML]

---

### Post by amjjawad on 2010-12-24
As I expected.
Do you have Windows XP disk? if yes, boot from it and fix the MBR with fixmbr and fixboot.
Restart and make sure you can login to Windows.

Once done, move to the next step. You need to re-install GRUB2 in the MBR of sdb
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

```

sudo mount /dev/sd[COLOR=Red]b1[/COLOR] /mnt

sudo grub-install --root-directory=/mnt/ /dev/sd[COLOR=Red]b[/COLOR]
```If you don't choose where to install GRUB during installation, it will be installed by default in sda. In your case, it did and it's overwritten Windows Boot Loader.

Again, check the guide in my signature, there are lots of useful screenshots.

---

### Post by diggingeagle on 2010-12-24
Okay, I know how to install grub, but I don't know where.

[HTML]To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -1
fdisk: invalid option -- '1'

Usage:
 fdisk [options] <disk>    change partition table
 fdisk [options] -l <disk> list partition table(s)
 fdisk -s <partition>      give partition size(s) in blocks

Options:
 -b <size>                 sector size (512, 1024, 2048 or 4096)
 -c                        switch off DOS-compatible mode
 -h                        print help
 -u <size>                 give sizes in sectors instead of cylinders
 -v                        print version
 -C <number>               specify the number of cylinders
 -H <number>               specify the number of heads
 -S <number>               specify the number of sectors per track

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x52df0fb1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107861504 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004d2f4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60228   483779584   83  Linux
/dev/sdb2           60229       60802     4603905    5  Extended
/dev/sdb5           60229       60802     4603904   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 
[/HTML]

how do I tell what device boot I should save it to? I don't want to overwrite the windows one again. Thanks.

Oh btw, thanks to you, xp can boot now without my drive in.

---

### Post by amjjawad on 2010-12-24
> **diggingeagle said:**
> 
how do I tell what device boot I should save it to? I don't want to overwrite the windows one again. Thanks.

Oh btw, thanks to you, xp can boot now without my drive in.

Check my previous post. I already wrote the code :)
And don't forget to check out the link I posted.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by oldfred on 2010-12-24
amjjawad gave you the exact commands to type in. You mount partition [COLOR=Red]sdb1[/COLOR] (which is your linux install with the rest of grub)  and install to drive sd[COLOR=Red]b[/COLOR].

It just is sometimes removeable devices get loaded to different device numbers. Boot script has shown it as sdb already, but that could even change. If you unplug it and replug it in, it may change. Sometimes the external device gets promoted to sda, or it may be sde, so we like to check just before installing grub.

---

### Post by amjjawad on 2010-12-24
> **oldfred said:**
> amjjawad gave you the exact commands to type in. You mount partition [COLOR=Red]sdb1[/COLOR] (which is your linux install with the rest of grub)  and install to drive sd[COLOR=Red]b[/COLOR].

It just is sometimes removeable devices get loaded to different device numbers. Boot script has shown it as sdb already, but that could even change. If you unplug it and replug it in, it may change. Sometimes the external device gets promoted to sda, or it may be sde, so we like to check just before installing grub.

Based on the output of "sudo fdisk -l" I proceed without being worried but definitely your advice is needed, my friend :)

To the OP, let's follow oldfred's advice. Better safe than sorry :)

---

