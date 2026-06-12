---
title: "Running this script is failing  :("
date: 2009-02-10
forum: New to Ubuntu
---

### Post by ericeclifford on 2009-02-10
The script is getting this when I try to run it and I set the permissions to chmod 755 to it so i dont know whats wrong here it is in Gedit the name is ultralivecd and its a picture of a peice of paper and a blue square in the middle of it, if that means anything.  

HERES the error im gettin,

eric@eric:~$ '/home/eric/Desktop/ultralivecd' 
/home/eric/Desktop/ultralivecd: line 55: syntax error near unexpected token `fi'
/home/eric/Desktop/ultralivecd: line 55: `		fi'



HERES the script I have,














#!/bin/bash
##############################################################################
#    This file is part of Ultra-LiveCD.
# Copyright 2008 Chris Talley and some code by Peter Garrett
# Ultra-LiveCD is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# Ultra-LiveCD is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with Ultra-LiveCD.  If not, see <http://www.gnu.org/licenses/>.
#
# Contact [email]chris4585@gmail.com[/email] for more information
##############################################################################

# You can change WORK, and CD, keep FORMAT and FS_DIR the same.
export WORK=~/livecd
export CD=~/livecd/cd-tree
export FORMAT=squashfs
export FS_DIR=casper
# There will be a question that will ask to install the variable EXTRA_TOOLS programs.
export EXTRA_TOOLS="xfsprogs reiserfsprogs jfsutils testdisk wipe ntfs-3g ntfsprogs dosfstools mtools"
# Some suggestions
# gparted:	patitioning tool. It is automatically installed as a dependecy of ubiquity.
# ms-sys:	writing a Microsoft compatible boot record (MBR).
# testdisk:	Partition scanner and disk recovery tool.
# wipe:		Secure file deletion.
# partimage:	backup partitions into a compressed image file (like norton ghost).
# xfsprogs reiserfsprogs jfsutils: Tools for handling different filesystems.
# mtools: 	Tools for manipulating MSDOS files
menu_ () {
	clear
	echo "You should go in order, or start with the second option."
	echo
	echo "1. Take the tutorial."
	echo "2. Make a LiveCD."
	echo "3. Chroot."
	echo "4. Update initramfs."
	echo "5. Settings."
	echo "6. Make the ISO."
	echo
	echo "hit \"x\" to Exit."
	read -s -n 1 MENU
	case $MENU in
		1)
		tutorial_
		;;
		2)
		make_everything_function
		fi
		;;
		3)
		chroot_
		;;
		4)
		initramfs_menu
		;;
		5)
		settings_function
		;;
		6)
		makeiso
		;;
		x)
		echo "Exiting..."
		sleep 1s;
		exit
		;;
		*)
		menu_
		;;
	esac
	}
# Option 1
tutorial_ () {
	clear
	echo "Welcom to the Ultra-LiveCD tutorial."
	echo
	echo "This small tutorial is designed to help you understand"
	echo "how the LiveCD is created and all the steps that are"
	echo "envolved into making the the LiveCD."
	echo
	echo "To go forward hit any key and to go back hit \"b\" do this"
	echo "through out the tutorial, and to return to the menu hit \"m\"."
	read -s -n 1 NEXT
	case $NEXT in
		b)
		clear
		tutorial_
		;;
		m)
		clear
		menu_
		;;
		*)
		clear
		slid_1
		;;
	esac
	}
# Part of option 1
slid_1 () {
	echo "You might ask what you can do with this script, well you"
	echo "can do a lot of things but here's a small list:"
	echo
	echo "1. Show off a particular application"
	echo "2. Localize to a certain language"
	echo "3. Remove software packages"
	echo "4. Add software packages"
	echo "5. Update software packages"
	echo "6. Change system defaults (theme, icons, desktop background,"
	echo "   panels, browser homepage, etc)"
	echo "7. Edit the system 100%"
	echo
	echo "How though?  Hit any key to find out."
	read -s -n 1 NEXT_1
	case $NEXT_1 in
		b)
		clear
		tutorial_
		;;
		m)
		clear
		menu_
		;;
		*)
		clear
		slid_2
		;;
	esac
	}
# Part of option 1
slid_2 () {
	echo "A short discription of what goes on are laid out in the menus of"
	echo "this script, but what do they mean?"
	echo
	echo "Start - Prepares everything, and then runs debootstrap.  Debootstrap"
	echo "in a nutshell installs a debian base into a folder.  From there we"
	echo "use a tool called chroot, to enter into that folder and do all the"
	echo "work in chroot.  Once you're in chroot whatever you type does not"
	echo "effect your system, so essentually its as if you was working on a"
	echo "virtual machine, but in console.  I hope I didn't lose you there..."
	echo
	echo "To get anywhere though you must run the 2nd option for the 3rd, 4th"
	echo "5th, and 6th options to work."
	read -s -n 1 NEXT_2
	case $NEXT_2 in
		b)
		clear
		slid_1
		;;
		m)
		clear
		menu_
		;;
		*)
		clear
		slid_3
		;;
	esac
	}
# Part of option 1
slid_3 () {
	echo "What this script does, is automate a few of these processes such as"
	echo "installing the kernel in the chroot environment.  You have a few"
	echo "options such as setting the user name, or host of the LiveCD from"
	echo "the easy LiveCD menu."
	echo
	echo "Its not required that you have to set the user name, or host, but its"
	echo "a option.  You have a few other options which are useful such as"
	echo "automatically chrooting, automatically making the ISO, or updating"
	echo "the initramfs, which in some instances are very useful."
	echo
	echo "Overall these scripts try to make things easier, but not to limit the"
	echo "things the user can do.  For example, the user doesn't need to know how"
	echo "to install a kernel, so why let them, when they don't need to?  Of course"
	echo "the script can be changed very easily to allow the user to install"
	echo "the kernel they want."
	read -s -n 1 NEXT_3
	case $NEXT_3 in
		b)
		clear
		slid_2
		;;
		m)
		clear
		menu_
		;;
		*)
		clear
		slid_4
		;;
	esac
	}
# Part of option 1
slid_4 () {
	echo "Once you have ran the 2nd option from the menu you'll have the option to"
	echo "install ubiquity.  This is important because if you want to install your"
	echo "LiveCD to a computer you will have to install ubiquity (or use a specialized"
	echo "script (such as the inxtaller))."
	echo
	echo "Ubiquity is the installer used for Ubuntu."
	echo ""
	read -s -n 1 NEXT_4
	case $NEXT_4 in
		b)
		clear
		slid_3
		;;
		m)
		clear
		menu_
		;;
		*)
		clear
		slid_5
		;;
	esac
	}
# Part of option 1
slid_5 () {
	echo "slid 3"
	read -s -n 1 NEXT_5
	case $NEXT_5 in
		b)
		clear
		slid_4
		;;
		m)
		clear
		menu_
		;;
		*)
		clear
		slid_6
		;;
	esac
	}
# Option 2 from the main menu
make_everything_function () {
		if ! make_everything ; then
		echo -e "\nOh no!  Something must of went wrong.\n"
		sleep 2s;
		sudo rm -rf ${WORK}
		sudo rm -rf ${CD}
		umount_
		exit 1
		fi
		debootstrap_
		initramfs_
		initrd_vmlinuz
		to_chroot_or_not_to_chroot
	}
# Part of option 2
make_everything () {
	clear
	echo "Welcome to  Ultra-LiveCD!"
	echo 
	echo "You can create a LiveCD of your choice, using this program."
	echo "The process is very easy and straight forward."
	echo
	echo "Hit any key to continue."
	read -s -n 1
	clear
	echo "This step will create some folders needed."
	echo
	echo "Which are:"
	echo "${WORK}/rootfs"
	echo "${CD}"
	echo "${CD}/${FS_DIR}"
	echo "${CD}/boot/grub"
	echo
	echo "If you don't like this setup you can change the work dirs in the"
	echo "script variables at the top of creation."
	echo -e "Proceed? [y/n]\n"
	read -s -n 1 DIRS
	case $DIRS in
		y)
		echo -e "\nContinuing..."
		sleep 2s;
		;;
		*)
		echo -e "See you soon."
		echo
		echo -e "Hit any key to exit."
		read -s -n 1
		exit 0
		;;
	esac
	if [ -d "${CD}" ] ; then
		echo "${CD}"
		echo "already exists, change the variables at the"
		echo "top of the script then rerun the script."
		echo
		echo "Hit any key to exit."
		read -s -n 1
		exit 1
		else
		sudo mkdir -p ${CD}/{${FS_DIR},boot/grub}
		fi
	if [ -d "${WORK}/rootfs" ] ; then
		echo "${WORK}/rootfs"
		echo "already exists, change the variables at the"
		echo "top of the script then rerun the script."
		echo
		echo "Hit any key to exit."
		read -s -n 1
		exit 1
		else
		sudo mkdir -p ${WORK}/rootfs
		fi
		sudo apt-get update
		sudo apt-get -y install mkisofs grub debootstrap squashfs-tools linux-ubuntu-modules-$(uname -r)
	echo
	echo "Hit any key to continue."
	read -s -n 1

	}
# Part of option 2
debootstrap_ () {
	clear
	echo "Type the number you want the LiveCD to be based on."
	echo
	echo "1. Hardy i386"
	echo "2. Intrepid i386"
	read -s -n 1 CHOICES_CHOICES
	case $CHOICES_CHOICES in
		1)
		clear
		sure_1
		;;
		2)
		clear
		sure_2
		;;
		*)
		debootstrap_
		;;
	esac
	}
# Part of option 2
sure_1 () {
	echo
	echo "You chose Hardy i386."
	echo
	echo -e "Are you sure you want to continue with what you chose?"
	echo -e "Proceed? [y/n]\n"
	read -s -n 1 YOU_SURE
	case $YOU_SURE in
		y)
		echo "		[ok]"
		echo
		echo "This may take a while."
		echo
		echo -e "Hit any key to continue.\n"
		read -s -n 1
		hardy_i386
		;;
		n)
		debootstrap_
		;;
		*)
		sure_1
		;;
	esac
	}
# Part of option 2
sure_2 () {
	echo
	echo "You chose Intrepid i368."
	echo
	echo -e "Are you sure you want to continue with what you chose?"
	echo -e "Proceed? [y/n]\n"
	read -s -n 1 YOU_SURE
	case $YOU_SURE in
		y)
		echo "		[ok]"
		echo
		echo "This may take a while."
		echo
		echo -e "Hit any key to continue.\n"
		read -s -n 1
		intrepid_i386
		;;
		n)
		debootstrap_
		;;
		*)
		sure_2
		;;
	esac
	}
# Part of option 2
hardy_i386 () {
	if ! sudo debootstrap --arch=i386 hardy ${WORK}/rootfs ; then
		echo -e "\nOh no!  Something must of went wrong.\n"
		sleep 2s;
		sudo rm -rf ${WORK}
		sudo rm -rf ${CD}
		exit 1
	fi
	mount_
	sudo cp apt/hardy/sources.list ${WORK}/rootfs/etc/apt/sources.list
	proceed
	}
# Part of option 2
intrepid_i386 () {
	if ! sudo debootstrap --arch=i386 intrepid ${WORK}/rootfs ; then
		echo -e "\nOh no!  Something must of went wrong.\n"
		sleep 2s;
		sudo rm -rf ${WORK}
		sudo rm -rf ${CD}
		exit 1
	fi
	mount_
	sudo cp apt/intrepid/sources.list ${WORK}/rootfs/etc/apt/sources.list
	proceed
	}
# Part of option 2
proceed () {
		sudo chroot ${WORK}/rootfs apt-get update
		# The LiveCD needs casper and a kernel at least, if you want to compile your own kernel
		# then you should remove the kernel, if you do compile your own kernel you should
		# have support for:
		# 1. Support of loopback device.
		# 2. Support for the filesystem format you are using (e.g. squashfs ).
		# 3. Support for unionfs.
		# 4. Support for initramfs.
		sudo chroot ${WORK}/rootfs apt-get -y install linux-generic linux-headers-generic casper
		ubiquity_
	echo "Upgrading..."
	sleep 2s;
		sudo chroot ${WORK}/rootfs apt-get -y upgrade
		sudo chroot ${WORK}/rootfs apt-get clean
		sudo find /boot /usr/lib/grub/ -iname 'stage2_eltorito' -exec cp -v {} ${CD}/boot/grub \;
		sudo cp grub-menu.txt ${CD}/boot/grub/menu.lst
		# Removing some cruft
		FILES="${WORK}/rootfs/etc/timezone ${WORK}/rootfs/etc/mtab ${WORK}/rootfs/etc/fstab"
		for i in $FILES
		do		
		sudo rm $i
		done
	}
# Part of option 2
ubiquity_ () {
	clear
	echo "Would you like to install ubiquity onto the LiveCD?"
	echo "(The Ubuntu installer)"
	echo
	echo "If so then hit \"y\", and hit anything else to continue."
	read -s -n 1 SET_UBIQUITY
	case $SET_UBIQUITY in
		y)
			sudo chroot ${WORK}/rootfs apt-get -y ${EXTRA_TOOLS} ubiquity
			sudo chroot ${WORK}/rootfs dpkg-query -W --showformat='${Package} ${Version}\n' | sudo tee ${CD}/${FS_DIR}/filesystem.manifest
			sudo cp -v ${CD}/${FS_DIR}/filesystem.manifest{,-desktop}
		REMOVE="${EXTRA_TOOLS}"
		for i in $REMOVE 
			do
		sudo sed -i "/${i}/d" ${CD}/${FS_DIR}/filesystem.manifest-desktop
		done
		;;
		*)
		echo "Continuing without applying changes for ubiquity..."
		sleep 2s;
		;;
	esac
	}
# Part of option 2
initramfs_ () {
	clear
	echo "please wait..."
	sudo cp initramfs ${WORK}/rootfs/
	sudo chroot ${WORK}/rootfs sh initramfs
	sudo chroot ${WORK}/rootfs rm initramfs
	echo
	echo "Done."
	echo
	echo -e "Hit any key to continue."
	read -s -n 1
	}
# Part of option 2
initrd_vmlinuz () {
	echo "Copying intitrd.img and vmlinuz..."
	sleep 2s;
		find ${WORK}/rootfs/boot -iname 'vmlinuz*' -exec sudo cp -vp {} ${CD}/boot/vmlinuz \;
		find ${WORK}/rootfs/boot -iname 'initrd.img*' -exec sudo cp -vp {} ${CD}/boot/initrd.gz \;
		sudo cp -vp ${WORK}/rootfs/boot/memtest86+.bin ${CD}/boot
	echo
	echo -e "Hit any key to continue."
	read -s -n 1
	}
# Part of option 2
to_chroot_or_not_to_chroot () {
	sudo chroot ${WORK}/rootfs apt-get clean
	for i in /etc/resolv.conf /etc/hosts /etc/hostname; do sudo cp -pv $i ${WORK}/rootfs/etc/; done
	clear
	echo "Here you can chroot into the chroot environment."
	echo
	echo "If you don't chroot now, and go ahead and make a ISO, you will have"
	echo "a very minimal command line LiveCD.  You can do both chroot and make"
	echo "a ISO later if you want and just exit now."
	echo
	echo "Type the number of what you want to do."
	echo
	echo "1. Return to menu."
	echo "2. Chroot - install packages, edit the LiveCD, etc..."
	echo "3. Make a ISO - creates a ISO of what you just built, (bare bones LiveCD)"
	echo "4. Exit."
	read -s -n 1 AUTO_CHROOT
	case $AUTO_CHROOT in
		1)
		menu_
		;;
		2)
		clear
		echo "Install the packages/edit the system now, you must use \"exit\""
		echo "when finished.  What you do within chroot does not effect your"
		echo "own system."
		echo
		echo -e "Hit any key to chroot\n"
		read -s -n 1
		sudo chroot ${WORK}/rootfs
		clear
		echo "We're finished here."
		echo
		echo -e "Hit any key to continue."
		read -s -n 1
		exit_or_iso
		;;
		3)
		clear
		makeiso
		;;
		4)
		umount_
		echo -e "Exiting...\n"
		echo
		echo -e "Hit any key to exit."
		read -s -n 1
		exit 0
		;;
		*)
		to_chroot_or_not_to_chroot
		;;
	esac
	}
# Used for option 3, and part of to_chroot_or_not_to_chroot
exit_or_iso () {
	clear
	echo "Would you like to exit now, or create a ISO?"
	echo
	echo "1. Return to the menu."
	echo "2. Make a ISO."
	echo "3. Exit."
	read -s -n 1 ISO_TIME
	case $ISO_TIME in
		1)
		umount_
		menu_
		;;
		2)
		clear
		makeiso
		;;
		3)
		echo
		echo -e "Hit any key to exit."
		read -s -n 1
		umount_
		exit 0
		;;
		*)
		exit_or_iso
		;;
	esac
	}
# Option 3
chroot_ () {
	clear
	logical_order_check
	echo "Copying files needed for chroot..."
	for i in /etc/resolv.conf /etc/hosts /etc/hostname; do sudo cp -pv $i ${WORK}/rootfs/etc/; done
	sleep 2s;
	clear
	echo "Install the packages/edit the system now, you must use \"exit\""
	echo "when finished.  What you do within chroot does not effect your"
	echo "own system."
	echo
	echo -e "Hit any key to chroot\n"
	read -s -n 1
	mount_
	sudo chroot ${WORK}/rootfs
	clear
	echo "We're finished here."
	echo
	echo -e "Hit any key to continue.\n"
	read -s -n 1
	exit_or_iso
	}
# Option 4
initramfs_menu () {
	clear
	logical_order_check
	echo "Please wait..."
	sudo cp initramfs ${WORK}/rootfs/
	sudo chroot ${WORK}/rootfs sh initramfs
	sudo chroot ${WORK}/rootfs rm initramfs
	menu_
	}
# Option 5
settings_function () {
	settings_
	settings_options
	umount_
	}
# part of option 5
settings_ () {
	clear
	logical_order_check
	echo "Here you can set your user name, user full name, hostname, and"
	echo "build system of the LiveCD."
	echo
	echo "Note: These are not permanent and only apply to the LiveCD."
	echo
	echo -e "Hit any key to continue."
	read -s -n 1
	}
# Part of option 5
settings_options () {
	clear
	echo "Type the number you want to edit."
	echo
	echo "1. User Name"
	echo "2. Full User Name"
	echo "3. Hostname"
	echo "4. Build system"
	echo "5. Apply changes"
	read -s -n 1 CHOICES_CHOICES
	case $CHOICES_CHOICES in
		1)
		username
		;;
		2)
		full_name
		;;
		3)
		hostname
		;;
		4)
		build_system
		;;
		5)
		continue_settings
		;;
		*)
		settings_options
		;;
	esac
	}
	settings ()
		{	
		
			printf "You have set:" ; printf "\t$CHOICE\n"
		
			echo -e "Is this what you want? Just hit <enter> if yes, otherwise type \"n\"\n"
		
			read -s -n 1 CONFIRM
			case $CONFIRM in
				n | N)
					$HERE
					;;
				
				*)
					#Let's move on then...
					:
					;;
			esac
		}
			username ()
				{
				HERE=username
					clear
					echo "The user name will be the user for the LiveCD.  The user"
					echo "can only be small letters and one word."
					echo "Examples: live, bob, joe, computer, linux"
					echo
					printf "Type a user name:    "
				
					read user
				CHOICE=$user
					echo
				settings
				sudo sed -i "s/$(grep "export USERNAME" ${WORK}/rootfs/etc/casper.conf)/export USERNAME=${user}/g" ${WORK}/rootfs/etc/casper.conf
				choose_another_setting
				}
			full_name ()
				{
				HERE=full_name
					clear
					echo "The full name of the user can be more than one word."
					echo "Examples: Live Session User, Jim Bob, Live User"
					echo
					printf "Type the full name of the user:    "
				
					read full_name
				CHOICE=$full_name
					echo
				settings
				sudo sed -i "s/$(grep "export USERFULLNAME" ${WORK}/rootfs/etc/casper.conf)/export USERFULLNAME=${full_name}/g" ${WORK}/rootfs/etc/casper.conf
				choose_another_setting
				}
			hostname ()
				{
				HERE=hostname
					clear
					echo "The hostname should be one word"
					echo "Examples: Computer, computer, Desktop-computer"
					echo
					printf "Type a hostname :    " 
				
					read host
				CHOICE=$host
					echo
				settings
				sudo sed -i "s/$(grep "export HOST" ${WORK}/rootfs/etc/casper.conf)/export HOST=${host}/g" ${WORK}/rootfs/etc/casper.conf
				choose_another_setting
				}
			build_system ()
				{
				HERE=build_system
					clear
					echo "The build system should be one word."
					echo "Examples: Ubuntu, kubuntu, Debian"
					echo
					printf "Type a build system name:    "
				
					read build
				CHOICE=$build
					echo
				settings
				sudo sed -i "s/$(grep "export BUILD_SYSTEM" ${WORK}/rootfs/etc/casper.conf)/export BUILD_SYSTEM=${build}/g" ${WORK}/rootfs/etc/casper.conf
				choose_another_setting
				}
# Part of option 5
initramfs_settings () {
	mount_
	echo
	echo "Please wait..."
	sudo cp initramfs ${WORK}/rootfs/
	sudo chroot ${WORK}/rootfs sh initramfs
	sudo chroot ${WORK}/rootfs rm initramfs
	echo
	echo "Done."
	echo
	echo -e "Hit any key to continue."
	read -s -n 1
	}
# Part of option 5
copy_initrd () {
		clear
		sudo rm ${CD}/boot/initrd.gz
		find ${WORK}/rootfs/boot -iname 'initrd.img*' -exec sudo cp -vp {} ${CD}/boot/initrd.gz \;
	}
# part of option 5
choose_another_setting () {
		echo "Would you like to choose another setting to edit or just edit"
		echo "this setting?"
		echo
		echo "Hit any key to continue or hit \"o\" to edit another setting."
	read -s -n 1 CHOICES_CHOICES
	case $CHOICES_CHOICES in
		o)
		clear
		settings_options
		;;
		*)
		continue_settings
		;;
	esac
	}
# Part of option 5
continue_settings () {
	initramfs_settings
	copy_initrd
	echo
	echo -e "Hit any key to continue."
	read -s -n 1
	clear
	echo "Finished applying changes."
	echo
	echo "If you have already made a ISO You will have to create"
	echo "another ISO for the effects to take place."
	echo
	echo -e "Hit any key to continue."
	read -s -n 1
	clear
	umount_
	menu_
	}
# Option 6 (also part of option 2)
makeiso () {
	clear
	logical_order_check
	echo "Making the LiveCD ISO..."
		# Cleaning stuff so we don't have a larger ISO than we need.
		sudo chroot ${WORK}/rootfs apt-get clean
		sudo chroot ${WORK}/rootfs rm -rf /tmp/*
		if ! [ -d ${WORK}/rootfs/etc/hosts ] ; then
		echo
		else
		FILES="${WORK}/rootfs/etc/hosts ${WORK}/rootfs/etc/hostname ${WORK}/rootfs/etc/resolv.conf"
		for i in $FILES
		do		
		sudo rm $i
		done
		fi
		if ! [ -d ${WORK}/rootfs/etc/hosts ] ; then
		echo
		else
		# Removing some cruft
		FILES="${WORK}/rootfs/etc/timezone ${WORK}/rootfs/etc/mtab ${WORK}/rootfs/etc/fstab"
		for i in $FILES
		do		
		sudo rm $i
		done
		fi
		umount_
		# If there's a old filesystem.squashfs it will be deleted
	if [ -f ${CD}/${FS_DIR}/filesystem.${FORMAT} ] ; then
		sudo rm ${CD}/${FS_DIR}/filesystem.${FORMAT}
		sudo mksquashfs ${WORK}/rootfs ${CD}/${FS_DIR}/filesystem.${FORMAT}
	else
		sudo mksquashfs ${WORK}/rootfs ${CD}/${FS_DIR}/filesystem.${FORMAT}
	fi
	echo
	echo -e "Hit any key to continue."
	read -s -n 1
	clear
	# Unless you just want .iso.iso twice in the file name ;)
	# Although leaving this empty and just hitting enter gives you a hidden file
	echo "Type the name of the ISO."
	echo "Do no include \".iso\" in the file name."
	echo "Examples: livecd, my-live-cd, my custom livecd"
	read NAME
	clear
	# You can change the word "LiveCD" with quotes three lines down to whatever you want
		sudo mkisofs -b boot/grub/stage2_eltorito \
		-no-emul-boot -boot-load-size 4 -boot-info-table \
		-V "LiveCD" -cache-inodes -r -J -l \
		-o "${NAME}".iso $CD
	echo "If the size is more than 700 MB then you will need a DVD."
		# Giving the user permissions to use the iso...
		sudo chown $(whoami):$(whoami) "${NAME}".iso
		md5sum "${NAME}".iso > "${NAME}"-md5sum.txt
	echo
	echo -e "Hit any key to continue.\n"
	read -s -n 1
	stamp_it
	echo "Your LiveCD should be in the same folder as the script"
	echo
	echo "Now go and test the LiveCD!"
	echo
	echo -e "Hit any key to continue.\n"
	read -s -n 1
	umount_
	menu_
	}
# Part of option 6
stamp_it () {
	clear
	echo "You have the choice of keeping the ISO name the same"
	echo "or adding a time stamp to it."
	echo
	echo "1. Just keep the name I gave the ISO."
	echo "2. Strap that time stamp on there!"
	read -s -n 1 STAMP_IT
	case $STAMP_IT in
		1)
		# Continuing then
		;;
		2)
		mv "${NAME}".iso $(date +%y%m%d-%H:%M)-"$NAME".iso
		mv "${NAME}"-md5sum.txt $(date +%y%m%d-%H:%M)-md5sum.txt
		echo "Done."
		echo
		;;
		*)
		stamp_it
		;;
	esac
	}
# Used in various parts of the script (checking if the user has actually ran option 2)
logical_order_check () {
	if ! [ -d ${WORK}/rootfs ] ; then
		echo "Looks like you haven't successfully ran option 2 yet, have you?"
		echo
		echo "You might get this is you canceled the script somewhere, or more"
		echo "likely you haven't ran option 2.  If you canceled the script then"
		echo "you have to manually delete the work dirs."
		echo
		echo "which are:"
		echo "${WORK}"
		echo "${CD}"
		echo
		echo -e "Hit any key to continue."
		read -s -n 1
		menu_
	fi
	}
# Used in various parts of the script
mount_ () {
	if ! chroot ${WORK}/rootfs mount /proc /sys /dev/pts > /dev/null 2>&1 ; then
	sudo chroot ${WORK}/rootfs mount -l /proc /sys /dev/pts > /dev/null 2>&1
	fi 
	}
# Used in various parts of the script
umount_ () {
	if ! chroot ${WORK}/rootfs umount /proc /sys /dev/pts > /dev/null 2>&1 ; then
	sudo chroot ${WORK}/rootfs umount -l /proc /sys /dev/pts > /dev/null 2>&1
	fi 
	}
# starts the main menu
menu_
# If you do everything right no body will be sure you did anything at all :)
# - God from Futurama

---

### Post by donkyhotay on 2009-02-10
Line 55 has an fi statement and I can't find any corresponding if staetment to go with it.

---

### Post by Hobgoblin on 2009-02-10
For clarification, it's this bit.

```
case $MENU in
1)
tutorial_
;;
2)
make_everything_function
fi
;;
```

fi doesn't want to be there (or you've got a chunk of code missing).

---

### Post by ericeclifford on 2009-02-11
So should I put a if somewhere or remove it?

---

### Post by Malalo on 2009-02-11
my guess is that the "fi" command has no "if" to associate with. you could try removing the "fi".

---

### Post by ericeclifford on 2009-02-11
I removed the fi command it works somewhat well, thought when I tell it the path of the iso image it seems to be confused as hell.

---

### Post by ericeclifford on 2009-02-11
Is it possible to create a automatically apt-get install and apt-get remove --purge lists in here that it will run auto matically and then do a update and upgrade previous and after the lists of apt-get install and apt-get remove ???
anyone know how this would be worked?

---

