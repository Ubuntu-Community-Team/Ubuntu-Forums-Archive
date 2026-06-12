---
title: "[SOLVED] Can't get xp to boot in grub"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by oliwood2 on 2009-01-05
i have a 10gig ntfs partition with windows xp and the rest of my drive ubuntu so i would like to be able to boot up xp from grub so i was told to write:

title		Windows Xp Pro
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

but i just get "Grub Error 13: "Invalid or unsupported executable format"




heres som info on my partitions



Disk /dev/sda: 160.0 Gb, 160041885696 byte
255 heads, 63 sectors/track, 19457 cylinders
Units = cylindre of 16065 * 512 = 8225280 bytes
Disk identifier: 0x61d67b26

    Enhed Opstart   Start         Slut     Blokke   Id  System
/dev/sda1   *           1       18115   145508706   83  Linux
/dev/sda2           18182       19458    10248192    7  HPFS/NTFS
Partition 2 slutter ikke på en cylindergrænse.
/dev/sda3           18157       18181      200812+   5  Udvidet
/dev/sda4           18116       18156      329332+  82  Linux swap / Solaris
/dev/sda5           18157       18181      200781   83  Linux

Partitionstabellens indgange er ikke i disk-rækkefølge

Disk /dev/sdb: 1000.2 Gb, 1000204886016 byte
255 heads, 63 sectors/track, 121601 cylinders
Units = cylindre of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ffc810

    Enhed Opstart   Start         Slut     Blokke   Id  System
/dev/sdb1   *           1      121601   976760001    7  HPFS/NTFS
oliwood2@oliwood2-laptop ~ $ 



and heres my menu.lst or al least what i think is relevant



title		Windows Xp Pro
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

title		Linux Mint 6, kernel 2.6.27-7-generic
root		(hd0,4)
kernel		/vmlinuz-2.6.27-7-generic root=/dev/sda1 ro quiet splash 
initrd		/initrd.img-2.6.27-7-generic
quiet

title		Linux Mint 6, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,4)
kernel		/vmlinuz-2.6.27-7-generic root=/dev/sda1 ro single
initrd		/initrd.img-2.6.27-7-generic

title		Linux Mint 6, kernel Last successful boot
root		(hd0,4)
kernel		/last-good-boot/vmlinuz root=/dev/sda1 ro quiet splash  last-good-boot
quiet

title		Linux Mint 6, memtest86+
root		(hd0,4)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

please help i have been trying for 2 weeks

---

### Post by caljohnsmith on 2009-01-05
How about trying instead:
```
title Windows Xp Pro
rootnoverify (hd0,1)
savedefault
makeactive
chainloader +1
```
Let me know if that works, or if not, what exactly happens when you try it from the Grub menu.

---

### Post by oliwood2 on 2009-01-05
it says:
starting up...
BOOTMGR is missing
press Ctrl+Alt+Delete to restart


i guess thats good somehow

---

### Post by caljohnsmith on 2009-01-05
Did you have an NTFS or FAT partition that you deleted in order to install Ubuntu? Because that error message you got would indicate that Windows is probably missing its boot files at this point. In order to get a clearer picture of your setup, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your Vista booting problem might be.

---

### Post by bumanie on 2009-01-05
At present you have windows trying to boot from sda2 and linux is booting from sda5. Is your bootable xp on the second hard drive (sdb)? The ntfs partition on sda2 looks like a data partition. I think the xp bootloader is on sdb1. If so you need to modify your boot/grub/menu.lst like this. 

title Windows Xp Pro
rootnoverify (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

If you think the boot partitions are different don't modify the list, but post back with how you believe the setup is.

---

### Post by oliwood2 on 2009-01-05
```
#!/bin/bash
#to use this script:
#
#sudo bash boot_info_script.txt
#
#date  1/2/09
#authors  meierfra.  and  caljohnsmith
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
#   Displays "fdisk -lu
#   Displays "blkid -c /dev/null"
#   Displays "sfdisk -V"
#   Finds  boot directories and displays their contents.
#   Looks in "/" and "NST" for  bootpart codes  and displays the offset
#                and boot drive it is trying to chainload
#   Looks on "/" and "/NST" for stage1 files and displays the offset
#         and bootdrive of the stage 2  files is trying to chainload.
#    displays  boot configuration files.
#All information is written to the file "RESULTS.txt" in the
#    same folder as the script


########  List of folders which might contained files used for chainloading
Boot_Codes_Dir="
    /
    /NST/
    "
#################  List of folders whose content will be displayed
Boot_Dir="
    /Boot
    /boot
    /BOOT
    /boot/grub
    /grub
    /ubuntu/disks
    /ubuntu/disks/boot/
    /ubuntu/disks/boot/grub
    /ubuntu/disks/install/boot
    /ubuntu/disks/boot/grub
    /NST
    "


##############  List of files whose names will be displayed (if they exists)
Boot_Prog="
    /bootmgr
    /BOOTMGR
    /grldr
    /GRLDR
    /ntldr
    /NTLDR
    /NTDETECT.COM
    /ntdetect.com
    /NTBOOTDD.SYS
    /ntbootdd.sys
    /wubildr.mbr
    /ubuntu/winboot/wubildr.mbr
     "

############### List if files whose contents will be displayed.
Boot_Files="
    /boot/grub/menu.lst
    /grub/menu.lst
    /NST/menu.lst
    /menu.lst
    /ubuntu/disks/boot/grub/menu.lst
    /ubuntu/disks/install/boot/grub/menu.lst
    /boot/grub/grub.conf
    /grub/grub.conf
    /grub.conf
    /boot.ini
    /etc/fstab
    "


## "titlebar_gen" generates the $name$file title bar to always be either 79 or 80 chars total in length:
titlebar_gen () {
		name_file="$1$2:"; name_file_length=${#name_file}
		equal_signs_line_length=$(((80-name_file_length)/2-1)); equal_signs_line=""
		for length in $(seq $equal_signs_line_length); do
  			equal_signs_line='='$equal_signs_line
		done
		echo "$equal_signs_line $name_file $equal_signs_line" >> $Log1; }


#######  Directory containing the script.

Dir=$(cd $(dirname $0);pwd);

########  To avoid overwriting existing file, look for a non-existing file 
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

Log1=$Folder/Log1               #  Most of the information which is not part of
                                #the summary is recorded in this file.
Error_Log=$Folder/Error_Log     #  File to catch all unusal Standar Errors 
Trash=$Folder/Trash             #   File to catch all usual Standard Errors
                                #these messagges will not be included in the RESULTS       
Mount_Error=$Folder/Mount_Error # File to catch Mounting Errors
Unknown_MBR=$Folder/Unknown_MBR # File to record all unknown MBR and Boot sectors. 
Tmp_Log=$Folder/Tmp_Log         #File to temporarily hold some information.

exec 2>$Error_Log              #Redirect all standard error to the file Error_Log


All_Hard_Drives=$(ls /dev/hd? /dev/sd? 2>>$Trash );   ### List of all Hard drives.

echo '============================= Boot Info Summary: =============================='; echo

#####   Search  hard drives which don't exists   or have  corrupt partition tables
#####   All hard drives which a valid partition table are stored   in $Hard_Drives

for drive in  $All_Hard_Drives;
do
        size=$(sfdisk -s $drive);        
        if [ 0 -lt $size 2>>$Trash ];
	then
	 Hard_Drives=$Hard_Drives" "$drive; 
        else
          echo " => Drive $(basename $drive) does not have a valid partition table."
    fi;
done;


############ Identify the MBR of each  hard drive.

for drive in $Hard_Drives;
  do 
    Message=$(echo is installed in the MBR of $drive)
    case $(hexdump -v -n  2 -e '/1 "%x"' $drive) in
	eb48) BL=Grub
             dr=$(hexdump -s 0x40 -n 1 -e '"%d"' $drive);
             offset=$(hexdump -s 0x44 -n 4 -e '"%u"' $drive);
              if  [ "$offset" != 1 ];
	      then
                  pa=-1
                  for hdd in $Hard_Drives;
		  do
                      if [ $offset -lt $((2*$(sfdisk -s $hdd))) ]
			      then
		      tmp=$(dd if=$hdd skip=$offset count=1 2>>$Trash | hexdump    -n 4 -e '"%x"');
                      if [ "$tmp" = 3be5652 ]; then
                      pa=$(dd if=$hdd skip=$((offset+1)) count=1 2>>$Trash | hexdump  -s 0xa  -n 1 -e '"%d"');
                      stage2_hdd=$hdd
                      fi;
                      fi;
                  done;
                  let dr-127
                  Message=$(echo $Message and looks at sector $offset)         
                  if [ "$dr" = 128 ];
                      then
                          Message=$(echo $Message of the same hard drive) 
                      else
                           Message=$(echo $Message on boot drive \#$dr)
		  fi;
                    Message=$(echo $Message for the stage2 file);
                    
                        if [ "$pa" = -1  ]
		     then
		         Message=$(echo $Message, but no stage2 files can be found at this location); 
                     else
                       pa=$((pa+1))
                        Message=$(echo $Message \(a stage2 file is at this location on $stage2_hdd\) and on)
                        if [ $pa = 256 ];
                        then
                            Message=$(echo $Message the same partition) 
                        else
                           Message=$(echo $Message partition \#$pa) 
	                fi;
                       Message=$(echo $Message for menu.lst.)
                     fi;
		 
	      else
	      pa=$(hexdump -s 0x419 -n 1 -e '"%d"' $drive);
              dr=$(hexdump -s 0x41a -n 1 -e '"%d"' $drive);
              if [ $pa$dr = 4649 ]; 
		then
		BL=SuperGrub
                pa=$(hexdump -s 0x41e -n 1 -e '"%d"' $drive);
                dr=$(hexdump -s 0x41f -n 1 -e '"%d"' $drive);
 	      fi
              dr=$((dr-127))
              pa=$((pa+1))
              if [ $dr = 128 ];
               then
                Message=$(echo $Message and looks on the same drive in partition \#$pa for its boot files.)
              else
               Message=$(echo $Message and looks  on boot drive \#$dr in partition \#$pa for its boot files.)
            fi;
	    fi;; 
 	33c0) BL=Windows;;
	fa31) BL=Syslinux;;
	faeb) BL=Lilo;; 
	fc31) BL=Testdisk;;
	eb5e) BL=Grub4Dos;;
	b800) BL=Plop;;
	33ff) BL='HP/Gateway';;
         ebe) BL=ThinkPad;;
        fa33) BL="No boot loader";; 
        fabe) BL="No boot loader?";;
        fab8) BL="No boot loader";;   
	fceb) BL=BootIt;;
          00) BL="No boot loader";;
	   *) BL="No known boot loader"
              echo "Unknown MBR on $drive" >> $Unknown_MBR;
              echo >> $Unknown_MBR;
              hexdump -n 512 -C $drive >> $Unknown_MBR;
              echo >> $Unknown_MBR;;
        esac;
        ##Output message at beginning of summary that gives MBR info for each drive:
        echo -n " => "
        echo "$BL $Message" | fold -s -w 75 | sed -e '2~1s/.*/    &/'   
 
    done
    echo;

for drive in $Hard_Drives;
 do
for part  in  $(ls $drive?* 2>>$Trash)
   do
      BSI=""      
      part_number=${part:8}
      part_type=$(sfdisk -c $drive $part_number)
      name=$(basename $part);
      echo $name: _________________________________________________________________________; echo
      mkdir $name 
      type=$( /lib/udev/vol_id -t $part 2>$Tmp_Log );
      if [ $part_type = 5 ] || [ $part_type = f ] && [ "$type" = "" ] ;
         then
	 type="Extended Partition";
	 cat $Tmp_Log>>$Trash;
	 else
         cat $Tmp_Log>>$Error_Log
      fi;
      echo "    File system:       "$type;
      if [ "$type" != "swap" ]  && [ "$type" != "Extended Partition"  ] && [ "$type" != "unknown volume type" ] && [ "$type" != "LVM2_member" ]  && [ "$type" != "linux_raid_member" ] && [ "$type" != "crypto_Luks" ] ;
       then 

          Bytes8081=$(hexdump -v -s 0x80 -n  2 -e '/1 "%x"'  $part)
          case $Bytes8081  in
             8cd) BST="Windows XP";;
            b6d1) BST="Windows XP: Fat32";;
            fa33) BST="Windows XP";;
	    55aa) BST="Windows Vista";;
            e9d8) BST="Windows Vista";;
            100f) BST="HP Recovery";;
            3a5e) BST="Recovery:Fat 32";;
            89e) BST="MSDOS5.0: Fat 16";;
            bd0) BST="MSWIN4.1: Fat 32";;
            7405) BST="Vista:  Fat 32";;
            e00) BST="Dell Utility: Fat16";;           
	    5272) BST=Grub;
                  offset=$(hexdump -s 0x44 -n 4 -e '4 "%u"' $part 2>>$Trash);
                  dr=$(hexdump -s 0x40 -n 1 -e '"%d"' $part);
                  pa="T"
                  for hdd in $Hard_Drives;
		  do
                      if [ $offset -lt  $((2*$(sfdisk -s $hdd))) ];
			      then
		      tmp=$(dd if=$hdd skip=$offset count=1 2>>$Trash | hexdump    -n 4 -e '"%x"');
                      if [ "$tmp" = 3be5652 ]; then
                      pa=$(dd if=$hdd skip=$((offset+1)) count=1 2>>$Trash | hexdump  -s 0xa  -n 1 -e '"%d"');
                      stage2_hdd=$hdd
                      fi;
		      fi;
                  done;
                  dr=$((dr-127))
                  BSI=$(echo $BSI Grub is installed to the boot sector of $part and looks at sector $offset )        
                  if [ "$dr" = 128 ];
                      then
                          BSI=$(echo $BSI of the same hard drive) 
                      else
                          BSI=$(echo $BSI on boot drive \#$dr)
		  fi;
                  BSI=$(echo $BSI for the stage2 file);
                    
                        if [ "$pa" = "T"  ]
		     then
		        BSI=$(echo $BSI, but no stage2 files can be found at this location); 
                     else
                       pa=$((pa+1))
                       BSI=$(echo $BSI  \(a  stage2 file is  at this location on $stage2_hdd\)  and on )                       
                        if [ "$pa" = 256 ];
                        then
                           BSI=$(echo $BSI the same partition) 
                        else
                            BSI=$(echo $BSI  partition \#$pa )
	                fi;
                      BSI=$(echo $BSI for menu.lst.)
                     fi;;
                  
                   
            7cc6) BST=Win_98;;
            7304) BST=Dos_1.0;;
            2d5e) BST=Dos_1.1;;
	    7815) BST=Fat32;;
            6f74) BST=Fat32;;
            696e) BST=Fat16;;
            6616) BST=Fat16;;
 	      00) sig2=$(hexdump -v -s 0x80 -n  2 -e '/1 "%x"'  $part)
                      if [ "$sig2" = 00 ];
		      then
                      BST="No Boot Loader";
		      else
		      BST="Unknown"
                      echo "Unknown BootLoader  on $part" >> $Unknown_MBR;
                      echo >> $Unknown_MBR;
                      hexdump -n 512 -C $part >> $Unknown_MBR;
                      echo >> $Unknown_MBR;
                  fi;;
                *) BST="Unknown"
                   echo "Unknown BootLoader  on $part" >> $Unknown_MBR;
                   echo >> $Unknown_MBR;
                   hexdump -n 512 -C $part >> $Unknown_MBR;
                   echo >> $Unknown_MBR;
            esac;
######################   Display the boot sector type.
           echo "    Boot sector type:  "$BST  

####################### Investigate the Boot Parameter Block of an NTFS partition.

           if [[ "$type" = "ntfs" ]]
           then
           offset=$(hexdump -s 0x1c -n 4 -e '"%u"' $part);
           real_offset=$(fdisk -lu $drive | grep "$part "| sed s/*// |awk '{print $2}');
           BPB_Part_Size=$(hexdump -s 0x28 -n 4 -e '"%u"' $part)
           Real_Part_Size=$(sfdisk -s $part);
           Real_Part_Size=$((Real_Part_Size * 2));
           Comp_Size=$(( (BPB_Part_Size - Real_Part_Size)/256 ))
           SectorsPerCluster=$(hexdump -s 0xd -n 1 -e '"%d"' $part);
           MFT_Cluster=$(hexdump -s 0x30 -n 4 -e '"%d"' $part);
           MFT_Sector=$(( MFT_Cluster * SectorsPerCluster ));

           if [[ "$MFT_Sector" -lt "$Real_Part_Size" ]];
           then
               MFT_FILE=$(dd if=$part skip=$MFT_Sector count=1 2>>$Trash | hexdump    -n 4 -e '"%_u"');
              MFT_MFT=$( dd if=$part skip=$MFT_Sector count=1 2>>$Trash| hexdump -e '4/1 "%x"' | grep "432404d046054")
               
	   else 
               MFT_FILE="";
               MFT_MFT="";
           fi;
           MFT_Mirr_Cluster=$(hexdump -s 0x38 -n 4 -e '"%d"' $part);
           MFT_Mirr_Sector=$(( MFT_Mirr_Cluster * SectorsPerCluster ));
           if [[ "$MFT_Mirr_Sector" -lt "$Real_Part_Size" ]];
           then
           MFT_Mirr_FILE=$(dd if=$part skip=$MFT_Mirr_Sector count=1 2>>$Trash | hexdump    -n 4 -e '"%_u"');
  
           MFT_Mirr_MFT=$(dd if=$part skip=$MFT_Mirr_Sector count=1 2>>$Trash |hexdump -e '4/1 "%x"' | grep "432404d046054")
           else 
               MFT_Mirr_FILE="";
               MFT_Mirr_MFT="";
           fi;
           if [[ "$offset" = "$real_offset"  && "$MFT_FILE" = "FILE"  &&  "$MFT_MFT" != "" && "$MFT_Mirr_FILE" = "FILE"  &&  "$MFT_Mirr_MFT" != "" && "$Comp_Size" = "0"  ]];
	    then
	       BSI=$(echo $BSI" "No errors found in the  Boot Parameter Block.);
	    if [[ "$offset" != "$real_offset" ]] 
            then
                BSI=$(echo $BSI"  "According to the info in the boot sector, $name starts at sector $offset.)
                if [[ "$offset" != "63" ||  $part_number -lt 5 ]]
                then
                    BSI=$(echo $BSI" "But according to the info  from fdisk, $name starts at sector   $real_offset.);
                 fi;
            fi;
            if  [[ "$MFT_FILE" != "FILE"  ||  "$MFT_MFT" = "" ]]; 
	    then 
                BSI=$(echo $BSI" "The info in boot sector  on  the starting sector of the MFT is wrong.);
                echo MFT Sector of $part >> $Unknown_MBR;
                echo >> $Unknown_MBR
                dd if=$part skip=$MFT_Sector count=1 2>>$Trash| hexdump -C >>$Unknown_MBR;
             fi;
             if [[ "$MFT_Mirr_FILE" != "FILE"  ||  "$MFT_Mirr_MFT" = "" ]];
	     then
		 BSI=$(echo $BSI" "The info in the boot sector on  the starting sector of the MFT Mirror  is wrong.);
             fi;

             if  [[ "$Comp_Size" != "0"  ]];
             then  
                   BSI=$(echo $BSI"  "According to the info in the boot sector, $name has    $BPB_Part_Size sectors, but according to the info  from fdisk, it has  $Real_Part_Size sectors.);
              dd if=$part skip=$BPB_Part_Size count=2 2>>$Trash |hexdump -C
             fi;
           fi;
          fi;

######################## Investigate the Boot Parameter Block of some Fat partitions

  if [[ "$Bytes8081" = "7cc6" ||  "$Bytes8081" = "7815"  ||  "$Bytes8081" = "B6D1"  || "$Bytes8081" =  "7405" || "$Bytes8081" = "bd0" ||  "$Bytes8081" =  "89e"  ]] ;
           then
           offset=$(hexdump -s 0x1c -n 4 -e '"%d\n"' $part);
           real_offset=$(fdisk -lu $drive | grep "$part "| sed s/*// |awk '{print $2}');
           BPB_Part_Size=$(hexdump -s 0x20 -n 4 -e '"%d"' $part);
           Real_Part_Size=$(sfdisk -s $part);
           Real_Part_Size=$((Real_Part_Size * 2));  
           Comp_Size=$(( (BPB_Part_Size - Real_Part_Size)/256 ))    
           if [[ "$offset" = "$real_offset" && "$Comp_Size" = "0"  ]];
	    then
	       BSI=$(echo $BSI" "No errors found in the  Boot Parameter Block.);
	    else
            if [[ "$offset" != "$real_offset" ]] 
            then
                BSI=$(echo $BSI"  "According to the info in the boot sector, $name starts at sector $offset.)
                if [[ "$offset" != "63" ||  $part_number -lt 5 ]]
                then
                    BSI=$(echo $BSI" "But according to the info  from fdisk, $name starts at sector   $real_offset.);
                fi;
            fi;         
            [[ "$Comp_Size" = "0"  ]]  ||  BSI=$(echo $BSI"  "According to the info in the boot sector, $name has    $BPB_Part_Size sectors, but according to the info  from fdisk, it has  $Real_Part_Size sectors.);
              
            fi; 
          fi;

         
    
       if  mount $part $name 2>$Mount_Error;     ####### Try to mount partition
       then     ############  if partition was mounted
       OS=""
       [ -e $name"/Windows/System32/config/BCD-Template" ] ||  [ -e $name"/windows/system32/config/bcd-template" ] || [ -e $name"/WINDOWS/System32/config/BCD-Template" ] ||
  [ -e $name"/WINDOWS/system32/config/BCD-Template" ] && OS="Windows Vista"

       [ -e $name"/Windows/System32/config/SecEvent.Evt" ] ||  [ -e $name"/WINDOWS/system32/config/SecEvent.Evt" ] || [ -e $name"/WINDOWS/system32/config/secevent.evt" ] || [ -e $name"/windows/system32/config/secevent.evt" ] && OS="Windows XP"
  
       [ -e $name"/etc" ] && OS=$(cat $name/etc/issue) && OS=${OS%%\\*}
     

       BootFiles=""
       for file in $Boot_Files;
       do
           if [ -f $name$file ];
              then BootFiles=$(echo $BootFiles"  "$file);
	      echo >> $Log1
              titlebar_gen $name $file	##generates a titlebar above each file/dir listed
              echo >> $Log1
              if ! [ -h $name$file ];
              then
                 cat $name$file >> $Log1;
              fi;
	   fi;
       done;

       for file in $Boot_Prog;
       do
           if [ -f $name$file ];
              then BootFiles=$(echo $BootFiles"  "$file);          
	   fi;
       done;


       for file in $Boot_Dir;
       do
          if [ -d $name$file ];
          then
	      BootFiles=$(echo $BootFiles"  "$file); 
	      echo >> $Log1
              titlebar_gen $name $file	##generates a titlebar above each file/dir listed
              echo >> $Log1
              ls -la  $name$file >> $Log1 ; 
             
	  fi;
       done;

       for file in $Boot_Codes_Dir
       do
	   if [ -d $name$file ];
	   then  
		  for loader in $( ls  $name$file );
		  do
                   if [ -f $name$file$loader ];
		   then		     
                      sig=$(hexdump -s 0x101 -n 8  -e '8/1 "%_p"' $name$file$loader)
                      if [ "$sig"  = "BootPart" ]
			  then
                          offset=$(hexdump -s 0xf1 -n 4 -e '"%d"' $name$file$loader);
                              dr=$(hexdump -s 0x6f -n 1 -e '"%d"' $name$file$loader);
			      dr=$((dr -127))
 			  BSI=$(echo $BSI "  "BootPart in the file $file$loader is trying to chain load sector \#$offset on boot drive \#$dr);
		       fi;
		      sig=$(hexdump -s 0x17f -n 4  -e '4/1 "%_p"' $name$file$loader)
                      if [ "$sig"  = "GRUB" ];
                      then
                          offset=$(hexdump -s 0x44 -n 4 -e '4 "%u"' $name$file$loader 2>>$Trash);
                          dr=$(hexdump -s 0x40 -n 1 -e '"%d"' $name$file$loader);
                          pa="T"
                          for hdd in $Hard_Drives;
		          do
                             if [ $offset -lt  $((2*$(sfdisk -s $hdd))) ];
			     then
		                  tmp=$(dd if=$hdd skip=$offset count=1 2>>$Trash | hexdump    -n 4 -e '"%x"');
                                  if [ "$tmp" = 3be5652 ];
                                  then
                                      pa=$(dd if=$hdd skip=$((offset+1)) count=1 2>>$Trash | hexdump  -s 0xa  -n 1 -e '"%d"');
                                       stage2_hdd=$hdd
                                   fi;
		              fi;
                           done;
                           dr=$((dr-127))
                            BSI=$(echo $BSI Grub in the file $file$loader  looks at sector $offset )        
                           if [ "$dr" = 128 ];
                           then
                                BSI=$(echo $BSI of the same hard drive) 
                           else
                                BSI=$(echo $BSI on boot drive \#$dr)
		           fi;
                           BSI=$(echo $BSI for the stage2 file);
                    
                           if [ "$pa" = "T"  ]
		           then
		                BSI=$(echo $BSI, but no stage2 files can be found at this location); 
                           else
                                 pa=$((pa+1))
                                 BSI=$(echo $BSI  \(a stage2 file is at this location on $stage2_hdd\)  and on )                       
                                 if [ "$pa" = 256 ];
                                 then
                                     BSI=$(echo $BSI the same partition) 
                                 else
                                       BSI=$(echo $BSI partition \#$pa )
	                         fi;
                                 BSI=$(echo $BSI for menu.lst.)
                            fi;
                         fi;
 		       fi;
		  done; ## End of loop through the files in particular  Boot_Code_Directory
              fi;
           done   ## End of the loop through the Boot_Code_Directories.
 
      echo -n "    Boot sector info:  "
      echo $BSI | fold -s -w 55 |  sed -e '2~1s/.*/                       &/'
      echo "    Operating System:  "$OS
      echo -n "    Boot files/dirs:   "
      echo $BootFiles | fold -s -w 55 |  sed -e '2~1s/.*/                       &/'
     
     umount $name || umount -l $name; 
     else     ############### if partition failed to mount
       echo -n "    Boot sector info:  "
       echo $BSI | fold -s -w 55 |  sed -e '2~1s/.*/                       &/'  
       echo "    Mounting failed:";  
     cat $Mount_Error 
     fi;  ### end of Mounting "if then else"
     fi;  ### end of Partition Type "if then else"
     echo;
 
     done;  ### end of partition loop
     done;  ### end of hard drive loop

echo '=========================== Drive/Partition Info: ============================='; echo
for drive in $All_Hard_Drives;
 do
     echo "Drive $(basename $drive): _____________________________________________________________________"
     echo
     echo "fdisk -lu $drive:"
     fdisk -lu $drive;
     echo;
     echo "sfdisk -V $drive:"; echo
     sfdisk -V $drive 2>&1
     echo   
 done
echo "blkid -c /dev/null: ____________________________________________________________";
echo; blkid -c /dev/null
echo;
echo '=============================== "mount" output: ===============================';
echo; mount
echo >> $Log1

#################   Write the content of Log1 to the RESULTS file
cat $Log1  

if [ -e $Unknown_MBR ]; 
then
 echo "=========================== Unknown MBRs or Boot Sectors =======================";
 echo;
 cat $Unknown_MBR;
 echo
fi;

  

#####################  Write the Error Log to the RESULT file
echo "=============================== StdErr Messages: ==============================="
echo
[ -s $Error_Log ] && cat $Error_Log || echo "No errors were reported."

#####   Make the  user the owner of Result file
chown $(basename ~) $LogFile    

#######  Reset the Standard Output to the Terminal 
exec 1>&-
exec 1>&6
exec 6>&-

echo Finished. The results are in the file $(basename $LogFile) located in $Dir
exit
```

---

### Post by caljohnsmith on 2009-01-05
It looks like you accidentally posted the boot_info_script.txt file; please post the contents of the RESULTS.txt file. :)

---

### Post by pyromanic123boom on 2009-01-05
> **oliwood2 said:**
> i have a 10gig ntfs partition with windows xp and the rest of my drive ubuntu so i would like to be able to boot up xp from grub so i was told to write:

title		Windows Xp Pro
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

but i just get "Grub Error 13: "Invalid or unsupported executable format"




heres som info on my partitions



Disk /dev/sda: 160.0 Gb, 160041885696 byte
255 heads, 63 sectors/track, 19457 cylinders
Units = cylindre of 16065 * 512 = 8225280 bytes
Disk identifier: 0x61d67b26

    Enhed Opstart   Start         Slut     Blokke   Id  System
/dev/sda1   *           1       18115   145508706   83  Linux
/dev/sda2           18182       19458    10248192    7  HPFS/NTFS
Partition 2 slutter ikke på en cylindergrænse.
/dev/sda3           18157       18181      200812+   5  Udvidet
/dev/sda4           18116       18156      329332+  82  Linux swap / Solaris
/dev/sda5           18157       18181      200781   83  Linux

Partitionstabellens indgange er ikke i disk-rækkefølge

Disk /dev/sdb: 1000.2 Gb, 1000204886016 byte
255 heads, 63 sectors/track, 121601 cylinders
Units = cylindre of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ffc810

    Enhed Opstart   Start         Slut     Blokke   Id  System
/dev/sdb1   *           1      121601   976760001    7  HPFS/NTFS
oliwood2@oliwood2-laptop ~ $ 



and heres my menu.lst or al least what i think is relevant



title		Windows Xp Pro
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

title		Linux Mint 6, kernel 2.6.27-7-generic
root		(hd0,4)
kernel		/vmlinuz-2.6.27-7-generic root=/dev/sda1 ro quiet splash 
initrd		/initrd.img-2.6.27-7-generic
quiet

title		Linux Mint 6, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,4)
kernel		/vmlinuz-2.6.27-7-generic root=/dev/sda1 ro single
initrd		/initrd.img-2.6.27-7-generic

title		Linux Mint 6, kernel Last successful boot
root		(hd0,4)
kernel		/last-good-boot/vmlinuz root=/dev/sda1 ro quiet splash  last-good-boot
quiet

title		Linux Mint 6, memtest86+
root		(hd0,4)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

please help i have been trying for 2 weeks

You're on the right track. REMOVE your Windows XP entry from the top, and go down to the bottom, after ###

```

EXAMPLE

### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows XP
root (hd0,0)
makeactive
chainloader +1


```

Make sure it's at the very bottom.
Where it says "root (hd0,0)" hd0 means harddrive, 0 means partition.

More information here: [http://www.newlinuxuser.com/adding-other-operating-systems-to-grub/](http://www.newlinuxuser.com/adding-other-operating-systems-to-grub/).

I just set up a triple boot Windows Linux and Macintosh laptop using grub, so it works!

---

### Post by oliwood2 on 2009-01-06
> **caljohnsmith said:**
> It looks like you accidentally posted the boot_info_script.txt file; please post the contents of the RESULTS.txt file. :)

sorry it was pretty late when i wrote it

and i had forgotten that i installed ubuntu over a vista installation

```
============================= Boot Info Summary: ==============================

 => Grub is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for its boot files.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Linux Mint 6 Felicia
    Boot files/dirs:   /etc/fstab /boot

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition

sda4: _________________________________________________________________________

    File system:       swap

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst /grub/menu.lst /boot /boot/grub 
                       /grub

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 160.0 Gb, 160041885696 byte
255 heads, 63 sectors/track, 19457 cylinders, i alt 312581808 sektorer
Units = sektorer of 1 * 512 = 512 bytes
Disk identifier: 0x61d67b26

    Enhed Opstart   Start         Slut     Blokke   Id  System
/dev/sda1              63   291017474   145508706   83  Linux
/dev/sda2   *   292081664   312578047    10248192    7  HPFS/NTFS
Partition 2 slutter ikke på en cylindergrænse.
/dev/sda3       291676140   292077764      200812+   5  Udvidet
/dev/sda4       291017475   291676139      329332+  82  Linux swap / Solaris
/dev/sda5       291676203   292077764      200781   83  Linux

Partitionstabellens indgange er ikke i disk-rækkefølge

sfdisk -V /dev/sda:

Advarsel: partition 2 når ud over diskens slutning

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 1000.2 Gb, 1000204886016 byte
255 heads, 63 sectors/track, 121601 cylinders, i alt 1953525168 sektorer
Units = sektorer of 1 * 512 = 512 bytes
Disk identifier: 0x41ffc810

    Enhed Opstart   Start         Slut     Blokke   Id  System
/dev/sdb1   *          63  1953520064   976760001    7  HPFS/NTFS

sfdisk -V /dev/sdb:

/dev/sdb: O.k.

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="f87e09f7-168b-496e-9272-995ee09c5d8b" TYPE="ext3" 
/dev/sda2: UUID="0E44271F44270953" LABEL="XP" TYPE="ntfs" 
/dev/sda4: UUID="54c934ed-33f5-4f76-b4e3-b9ba20bb374f" TYPE="swap" 
/dev/sda5: UUID="bdcd5726-c8c8-43cb-a6f3-fa492682ab08" TYPE="ext3" 
/dev/sdb1: UUID="067C34E17C34CD65" LABEL="Syviel" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
/dev/sda5 on /boot type ext3 (rw,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/oliwood2/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=oliwood2)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=oliwood2)
/dev/sdb1 on /media/Syviel type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f87e09f7-168b-496e-9272-995ee09c5d8b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=bdcd5726-c8c8-43cb-a6f3-fa492682ab08 /boot           ext3    relatime        0       2
# /dev/sda4
UUID=54c934ed-33f5-4f76-b4e3-b9ba20bb374f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda1/boot: ==================================

totalt 8
drwxr-xr-x  2 root root 4096 2008-12-24 00:36 .
drwxr-xr-x 20 root root 4096 2008-12-24 00:43 ..

=========================== sda5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## Graphical boot menu location
gfxmenu=/boot/gfxmenu/default.message

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

# Pretty colours
color cyan/blue white/blue

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/sda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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
##      altoptions=(single-user) single
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

title		Windows Xp Pro
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1

title		Linux Mint 6, kernel 2.6.27-7-generic
root		(hd0,4)
kernel		/vmlinuz-2.6.27-7-generic root=/dev/sda1 ro quiet splash 
initrd		/initrd.img-2.6.27-7-generic
quiet

title		Linux Mint 6, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,4)
kernel		/vmlinuz-2.6.27-7-generic root=/dev/sda1 ro single
initrd		/initrd.img-2.6.27-7-generic

title		Linux Mint 6, kernel Last successful boot
root		(hd0,4)
kernel		/last-good-boot/vmlinuz root=/dev/sda1 ro quiet splash  last-good-boot
quiet

title		Linux Mint 6, memtest86+
root		(hd0,4)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST





============================= sda5/grub/menu.lst: =============================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## Graphical boot menu location
gfxmenu=/boot/gfxmenu/default.message

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

# Pretty colours
color cyan/blue white/blue

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/sda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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
##      altoptions=(single-user) single
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

title		Windows Xp Pro
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1

title		Linux Mint 6, kernel 2.6.27-7-generic
root		(hd0,4)
kernel		/vmlinuz-2.6.27-7-generic root=/dev/sda1 ro quiet splash 
initrd		/initrd.img-2.6.27-7-generic
quiet

title		Linux Mint 6, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,4)
kernel		/vmlinuz-2.6.27-7-generic root=/dev/sda1 ro single
initrd		/initrd.img-2.6.27-7-generic

title		Linux Mint 6, kernel Last successful boot
root		(hd0,4)
kernel		/last-good-boot/vmlinuz root=/dev/sda1 ro quiet splash  last-good-boot
quiet

title		Linux Mint 6, memtest86+
root		(hd0,4)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST





================================== sda5/boot: ==================================

lrwxrwxrwx 1 root root 1 2008-12-24 00:36 sda5/boot -> .

=============================== sda5/boot/grub: ===============================

totalt 210
drwxr-xr-x 2 root root   1024 2009-01-06 01:28 .
drwxr-xr-x 5 root root   1024 2008-12-24 01:38 ..
-rw-r--r-- 1 root root    197 2008-12-24 00:44 default
-rw-r--r-- 1 root root     30 2008-12-24 00:44 device.map
-rw-r--r-- 1 root root   9440 2008-12-24 00:44 e2fs_stage1_5
-rw-r--r-- 1 root root   9120 2008-12-24 00:44 fat_stage1_5
-rw-r--r-- 1 root root     19 2008-12-24 00:44 installed-version
-rw-r--r-- 1 root root   8224 2008-12-24 00:44 iso9660_stage1_5
-rw-r--r-- 1 root root  10144 2008-12-24 00:44 jfs_stage1_5
-rw-r--r-- 1 root root   4319 2009-01-06 01:28 menu.lst
-rw-r--r-- 1 root root   4233 2008-12-30 04:42 menu.lst_backup
-rw-r--r-- 1 root root   8480 2008-12-24 00:44 minix_stage1_5
-rw-r--r-- 1 root root  11296 2008-12-24 00:44 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-24 00:44 stage1
-rw-r--r-- 1 root root 125674 2008-12-24 00:44 stage2
-rw-r--r-- 1 root root  10856 2008-12-24 00:44 xfs_stage1_5

================================== sda5/grub: ==================================

totalt 210
drwxr-xr-x 2 root root   1024 2009-01-06 01:28 .
drwxr-xr-x 5 root root   1024 2008-12-24 01:38 ..
-rw-r--r-- 1 root root    197 2008-12-24 00:44 default
-rw-r--r-- 1 root root     30 2008-12-24 00:44 device.map
-rw-r--r-- 1 root root   9440 2008-12-24 00:44 e2fs_stage1_5
-rw-r--r-- 1 root root   9120 2008-12-24 00:44 fat_stage1_5
-rw-r--r-- 1 root root     19 2008-12-24 00:44 installed-version
-rw-r--r-- 1 root root   8224 2008-12-24 00:44 iso9660_stage1_5
-rw-r--r-- 1 root root  10144 2008-12-24 00:44 jfs_stage1_5
-rw-r--r-- 1 root root   4319 2009-01-06 01:28 menu.lst
-rw-r--r-- 1 root root   4233 2008-12-30 04:42 menu.lst_backup
-rw-r--r-- 1 root root   8480 2008-12-24 00:44 minix_stage1_5
-rw-r--r-- 1 root root  11296 2008-12-24 00:44 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-24 00:44 stage1
-rw-r--r-- 1 root root 125674 2008-12-24 00:44 stage2
-rw-r--r-- 1 root root  10856 2008-12-24 00:44 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by caljohnsmith on 2009-01-06
Thanks oliwood2, but it doesn't look like you pasted the entire contents of the RESULTS.txt file; please try again, and the results should start with the "Boot Info Summary" title bar.

---

### Post by oliwood2 on 2009-01-06
is it a problem that some of it is in danish?

---

### Post by caljohnsmith on 2009-01-06
A little Danish is not the problem, it's just that when you edit one of your posts, I don't get an email alert letting me know, unlike when you create a new post (since I'm subscribed to the thread). So I didn't know you had updated your post. :) Anyway, it looks like the issue is you are unfortunately missing your Windows boot files. So to save you the hassle of digging them off of a Windows Install CD that you may or may not have, I've attached the boot files you need to this post. How about downloading the attached "WinXP_boot_files.zip" to your Ubuntu desktop and do:
```

sudo mount /dev/sda2 /mnt
cd ~/Desktop
unzip WinXP_boot_files2.zip
sudo mv boot.ini ntldr NTDETECT.COM /mnt
```
Then use the Grub entry that I gave in post #2, reboot, and let me know exactly what happens when you try to boot Windows from Grub. We can work from there.

---

### Post by drubin on 2009-01-06
> **caljohnsmith said:**
> 
Then use the Grub entry that I gave in post #2, reboot, and let me know exactly what happens when you try to boot Windows from Grub. We can work from there.

Is it legal to give out windows boot files?

---

### Post by boof1988 on 2009-01-06
> **drubin said:**
> Is it legal to give out windows boot files?

Did you do any research before you asked this question?

---

### Post by drubin on 2009-01-06
> **boof1988 said:**
> Did you do any research before you asked this question?

Please enlighten me as to where I would find this "Legal" information I am not a Lawer and wouldn't know the first place to start looking.

Since this forum is not a "Legal Aid Forum" I erred on the side of caution.

---

### Post by oliwood2 on 2009-01-08
> **caljohnsmith said:**
> A little Danish is not the problem, it's just that when you edit one of your posts, I don't get an email alert letting me know, unlike when you create a new post (since I'm subscribed to the thread). So I didn't know you had updated your post. :) Anyway, it looks like the issue is you are unfortunately missing your Windows boot files. So to save you the hassle of digging them off of a Windows Install CD that you may or may not have, I've attached the boot files you need to this post. How about downloading the attached "WinXP_boot_files.zip" to your Ubuntu desktop and do:
```

sudo mount /dev/sda2 /mnt
cd ~/Desktop
unzip WinXP_boot_files2.zip
sudo mv boot.ini ntldr NTDETECT.COM /mnt
```
Then use the Grub entry that I gave in post #2, reboot, and let me know exactly what happens when you try to boot Windows from Grub. We can work from there.

it works!!
I can't thank you enough for your help but I'll try

---

### Post by caljohnsmith on 2009-01-08
> **oliwood2 said:**
> it works!!
I can't thank you enough for your help but I'll try
Glad that worked OK; cheers and enjoy Windows and Ubuntu. :)

---

