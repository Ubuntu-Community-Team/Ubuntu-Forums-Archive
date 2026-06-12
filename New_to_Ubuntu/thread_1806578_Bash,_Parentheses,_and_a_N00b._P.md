---
title: "Bash, Parentheses, and a N00b. :P"
date: 2011-07-17
forum: New to Ubuntu
---

### Post by mardose on 2011-07-17
So here is the deal my good fellows, I'm currently in the middle of writing a Bash script for automating softRAID1 setup on existing Ubuntu installs, I've picked up a little sed, if and then functions, and some of those other commands that just make you "look smart" lol. What I seem to be having trouble with now is most likely a simple one, but yet again Google fails me. :{ So here's the dig, my objective is for sed to automatically write some lines into a file, however because one of the lines includes set root='(md0)' naturally Bash tries to interpret the parentheses. My problem? The text that is to be imparted is parameters for a GRUB2 configuration file, I unfortunately can't just lose the parentheses... Here's what we're looking at:

sed '6 i\menuentry 'Ubuntu, with Linux 2.6.32-21-server' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod raid
        insmod mdraid
        insmod ext2
        set root='(md0)'
        linux   /vmlinuz-2.6.32-21-server root=/dev/md2 ro   quiet
        initrd  /initrd.img-2.6.32-21-server' -i /etc/grub.d/09_swraid1_setup

And there you have it, I haven't really done hardcore Bash scripting before so I must admit it has been something of a brain stretcher, but I honestly appreciate your answers and advice in advance. Thank you very much and God bless. :)

---

### Post by bodhi.zazen on 2011-07-17
sed will work, with or without the parenthesis

```
sed -i -e 's_(foo)_(text)_' file
```

```
sed -i -e 's_foo_text_' txt
```

In the future, you need to post the file you wish to change and the exact command or commands you use in your script.

---

### Post by Zebediah49 on 2011-07-18
Why does sed have to do that?

Why not just use echo?

If you're trying to insert it at a certain line (line 6, it looks like from that), I suppose that's a way to do it, but it still feels kinda messy.

Depending on what, exactly, you're trying to do, it very well might be easier to construct the file with a {extract, write new} structure as opposed to an {epic replacements} structure.  I have used both for various things (I have a sed expression that, when the variables are fully expanded, is a couple thousand characters, and also have used nohing more than echo to create small header files for c.), so it really depends on your application.

Back to what you have there, the parenthesis are the least of your worries.  Fix the single quotes (surround the expression with double quotes?, so that you can have singles in your expression), and you'll be fine.  If that doesn't work, look up HEREDOC.

---

### Post by mardose on 2011-07-18
bohdi, the problem I seem to be running into is Bash trying to interpret the "set root='(md0)' " line instead of letting sed format and output the text to the /etc/grub.d/09_swraid1_setup file. The /etc/grub.d/09_swraid1_setup file is mainly empty with the exception of a few commented out lines, thus translated from Bash to English it would go something like:

sed, insert the following text above line 6 in the empty file /etc/grub.d/09_swraid1_setup:

menuentry 'Ubuntu, with Linux 2.6.32-21-server' --class ubuntu --class gnu-linux --class gnu --class os {
         recordfail
         insmod raid
         insmod mdraid
         insmod ext2
         set root='(md0)'
         linux   /vmlinuz-2.6.32-21-server root=/dev/md2 ro   quiet
        initrd  /initrd.img-2.6.32-21-server


Zebediah, I will attempt the double parentheses option. To be honest, my code is pretty sloppy indeed (first time doing stuff other than CSS, JavaScript, and XHTML lol), I think I may have run into the problem because i've put a ton of code between an "if then" function. I will go ahead and post the part of the script that I've already completed when I'm able to get back to my Ubuntu install (dual booted with Windows 7 64-bit). What I'm attempting to do is to have the script ask the user if the script has been run before (the script requires a reboot in the middle of configuring the softRAID1 array) and if so, go to the last half of the script, and of course if not, to start from the beginning of the script...

---

### Post by bodhi.zazen on 2011-07-18
Post your code ;)

---

### Post by mardose on 2011-07-18
Okay, here we are...

#!/bin/bash
# Script Created by the Diamond Linux Team
# Released under GPL

# Disclaimer
echo "***************************************************************************"
echo "WARNING: THIS SCRIPT CAN CAUSE DEBILITATING DAMAGE TO YOUR SYSTEM, PLEASE
ENSURE THAT YOUR PRIMARY HARD DISK HAS BEEN FORMATTED CORRECTLY (THIS IS 
EXPLAINED FURTHER ON) AND THAT YOU HAVE MADE A BACKUP OF ALL FILES AND 
DOCUMENTS ON YOUR SYSTEM PREVIOUS TO RUNNING THIS SCRIPT. THERE IS NO WARRANTY, 
EXPRESSED OR IMPLIED, ASSOCIATED WITH THIS SCRIPT."
echo "***************************************************************************"
echo "Are you running this setup again after rebooting your system?"
OPTIONS="Yes No"
           select opt in $OPTIONS; do
               if [ "$opt" = "No" ]; then
echo "==========================================================================="
echo "|||||||||||||||| Diamond Linux softRAID1 Installer v0.168 |||||||||||||||||"
echo "==========================================================================="

echo "---------------------------------------------------------------------------"
echo "The setup will attempt to auto-configure a softRAID1 array on your system. 
For this setup to run properly, your primary hard disk (/dev/sda) should be 
partitioned as: /dev/sda1 (55MB, mountpoint /boot), /dev/sda2 (100MB - 500MB, 
swap), and /dev/sda3 (the remaining disk space, mountpoint /)"
echo "---------------------------------------------------------------------------"
read -p "Press any key to continue..."
echo "---------------------------------------------------------------------------"
apt-get install initramfs-tools mdadm
echo "---------------------------------------------------------------------------"
echo "Loading required kernel modules..."
echo "---------------------------------------------------------------------------" 
modprobe linear
modprobe multipath
modprobe raid0
modprobe raid1
modprobe raid5
modprobe raid6
modprobe raid10
echo "---------------------------------------------------------------------------"
echo "Setup is now copying the partition table from the primary hard disk to
the secondary hard disk. This may take a few minuets..."
echo "---------------------------------------------------------------------------"
sfdisk -d /dev/sda | sfdisk --force /dev/sdb
for partition in 1 2 3; do sfdisk --change-id /dev/sdb $partition fd; done 
echo "---------------------------------------------------------------------------"
echo "Checking for and removing any remains from previous RAID configurations..."
echo "---------------------------------------------------------------------------"
mdadm --zero-superblock /dev/sdb1
mdadm --zero-superblock /dev/sdb2
mdadm --zero-superblock /dev/sdb3
echo "---------------------------------------------------------------------------"
echo "Creating initial arrays..."
echo "---------------------------------------------------------------------------"
mdadm --create /dev/md0 --level=1 --raid-disks=2 missing /dev/sdb1
mdadm --create /dev/md1 --level=1 --raid-disks=2 missing /dev/sdb2
mdadm --create /dev/md2 --level=1 --raid-disks=2 missing /dev/sdb3
echo "---------------------------------------------------------------------------"
echo "Building filesystem on new array..."
echo "---------------------------------------------------------------------------"
mkfs.ext4 /dev/md0
mkswap /dev/md1
mkfs.ext4 /dev/md2
echo "---------------------------------------------------------------------------"
echo "Backing up /etc/mdadm/mdadm.conf to /etc/mdadm/mdadm.conf_orig and 
preparing to edit configuration files..."
echo "---------------------------------------------------------------------------"
cp /etc/mdadm/mdadm.conf /etc/mdadm/mdadm.conf_orig
mdadm --examine --scan >> /etc/mdadm/mdadm.conf
mkdir /mnt/md0
mkdir /mnt/md2
echo "---------------------------------------------------------------------------"
echo "Mounting new array..."
echo "---------------------------------------------------------------------------"
mount /dev/md0 /mnt/md0
mount /dev/md2 /mnt/md2
echo "---------------------------------------------------------------------------"
echo "The setup will now create a backup of the /etc/fstab and /etc/mtab files 
before editing and replacing the old drive entries with the newer RAID ones. If 
something should go wrong, you will find the backups in /etc marked as 
fstab.backup and mtab.backup respectively."
echo "---------------------------------------------------------------------------"
read -p "Press any key to initiate backup and update of fstab and mtab..."
cp /etc/fstab /etc/fstab.backup
# Editing fstab entries
# Commenting out old entries
sed "s*UUID=*#UUID=*g" -i /etc/fstab
# Writing new entries
sed '11 i\/dev/md2 /               ext4    errors=remount-ro 0       1' -i /etc/fstab 
sed '14 i\/dev/md0 /boot           ext4    defaults        0       2' -i /etc/fstab
sed '17 i\/dev/md1 none            swap    sw              0       0' -i /etc/fstab
# Backing up and editing /etc/mtab
cp /etc/mtab /etc/mtab.backup
sed "s*/dev/sda1*/dev/md0*g" -i /etc/mtab
sed "s*/dev/sda3*/dev/md2*g" -i /etc/mtab
# GRUB boot loader
cp /etc/grub.d/40_custom /etc/grub.d/09_swraid1_setup
sed '6 i\menuentry 'Ubuntu, with Linux 2.6.32-21-server' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod raid
        insmod mdraid
        insmod ext2
        set root='(md0)'
        linux   /vmlinuz-2.6.32-21-server root=/dev/md2 ro   quiet
        initrd  /initrd.img-2.6.32-21-server' -i /etc/grub.d/09_swraid1_setup
apt-get install leafpad
echo "---------------------------------------------------------------------------"
echo "Setup is configuring GRUB2. After pressing any key, an entry will be appear
below, '2.6.32-28-server' for example. This is your kernel version. The setup 
will also open a menu file in the text editor after waiting for 5 seconds. You 
will have to manually replace any instance of '2.6.32-21-server' with your kernel 
version. After you have edited and closed the text editor the setup will continue."
echo "---------------------------------------------------------------------------"
read -p "Press any key to continue..."
echo "---------------------------------------------------------------------------"
echo "= Your kernel version is: ="
uname -r
echo "---------------------------------------------------------------------------"
sleep 5s && leafpad /etc/grub.d/09_swraid1_setup
echo "The setup is updating the GRUB bootloader and adjusting the ramdisk..."
update-grub
update-initramfs -u
cp -dpRx / /mnt/md2
cd /boot
cp -dpRx . /mnt/md0
echo "---------------------------------------------------------------------------"
echo "The setup is entering final stages..."
echo "---------------------------------------------------------------------------"
grub-install /dev/sda
grub-install /dev/sdb
echo "---------------------------------------------------------------------------"
echo "For the changes to take effect your system must be rebooted."
echo "---------------------------------------------------------------------------"
read -p "Press any key to restart your system..."
reboot

# Setup after reboot
elif [ "$opt" = "Yes" ]; then
                echo This is as far as I have gotten...
               else
                clear
                echo Please enter either the number 1 or 2.
               fi
           done

I'm not sure if there is an easier way to accomplish the pre/post reboot setup option... If there were a way to make this function automated that would be nice... I had thought about creating another bash file, that way all that would be needed is an "if then" command with the variable "No" simply continuing the script (pre reboot) and "Yes" to the second bash file with the post reboot configurations, but then it wouldn't be as tidy as a single script... Which is kinda what I'm going for. Thanks for your time, I know this is a lot to read through. :R

---

### Post by FormatSeize on 2011-07-18
Wouldn't using:
```
set root='\(md0\)'
```
with the sed command make it so that the parentheses are interpreted as you want them to be?

---

