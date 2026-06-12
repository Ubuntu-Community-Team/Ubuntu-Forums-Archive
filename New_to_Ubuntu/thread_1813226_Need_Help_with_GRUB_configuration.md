---
title: "Need Help with GRUB configuration"
date: 2011-07-27
forum: New to Ubuntu
---

### Post by prashks on 2011-07-27
Hi All,

I have just started exploring first linux OS - Ubuntu 11.04 and so far it has been a great experience. 

However now I have a concern with the default boot configuration. While  installation I chose to install Ubuntu alongside with Windows 7. Now  after the installation I found that the default OS is set to Ubuntu in  the GRUB menu.

Let me first tell you what I have tried so far:

1. Installed Startup-Manager 
I installed the startup-manager and changed the default OS to Windows 7. But still I see the default option is set to Ubuntu.[attached the screenshot]

2. Edited the /etc/default/grub file and checked that GRUB_DEFAULT=6. [attached the file]

3. Opened the grub.cfg using command "sudo gedti /boot/grub/grub.cfg" and closed it immediately as I wasn't sure if I have the correct skills to edit this one :redface:. [attached the file]

Can you please let me know what can be done to change the boot order to Windows 7? 

Thanks

---

### Post by prashks on 2011-07-27
> **prashks said:**
> Hi All,

I have just started exploring first linux OS - Ubuntu 11.04 and so far it has been a great experience. 

However now I have a concern with the default boot configuration. While  installation I chose to install Ubuntu alongside with Windows 7. Now  after the installation I found that the default OS is set to Ubuntu in  the GRUB menu.

Let me first tell you what I have tried so far:

1. Installed Startup-Manager 
I installed the startup-manager and changed the default OS to Windows 7. But still I see the default option is set to Ubuntu.[attached the screenshot]

2. Edited the /etc/default/grub file and checked that GRUB_DEFAULT=6. [attached the file]

3. Opened the grub.cfg using command "sudo gedti /boot/grub/grub.cfg" and closed it immediately as I wasn't sure if I have the correct skills to edit this one :redface:. [attached the file]

Can you please let me know what can be done to change the boot order to Windows 7? 

Thanks

Sorry guys it seems I cannot upload the "/etc/default/grub" and  "/boot/grub/grub.cfg" files

---

### Post by thefasterblueone on 2011-07-27
You could try:

```
sudo update-grub
``` 

and see if that fixes it.

---

### Post by oldfred on 2011-07-27
I think startup manager does not totally work with grub2 v1.99. The newest version of grub has sub menus and that has confused some of the gui tools.

If the number is not correct you can manually edit it as you started to do, just change number to correct entry in menu.

With grub2 you can now use a title instead of a number (But it has to be exact, so copy it).

But Grub 2 also lets you use the title. Suppose your Windows title is "Windows Vista (on /dev/sda1)". Then you can use in /etc/grub/default, and you won't have to edit Grub after kernel updates.

find your windows entry in grub.cfg and copy to grub default like this Vista entry - If you edit your windows command use the edited copy as this must match the title exactly:
gedit /boot/grub/grub.cfg
and copy into grub_default line here:
gksudo gedit /etc/default/grub
GRUB_DEFAULT=0
change to comment # or delete old and add new line:
#GRUB_DEFAULT=0
GRUB_DEFAULT="Windows Vista (on /dev/sda1)"
Then do:
sudo update-grub

---

### Post by prashks on 2011-08-07
> **thefasterblueone said:**
> You could try:

```
sudo update-grub
```and see if that fixes it.

Thanks for the suggestion... but this didn't worked :(

---

### Post by x-D on 2011-08-07
Try boot repair, install it by doing this in the Terminal:

```

sudo add-apt-repository ppa:yannubuntu/boot-repair

sudo apt-get update && sudo apt-get install -y boot-repair-ubuntu

sudo update-grub

```Search for the Program in Unity or go to System ----> Administration ----> Boot Repair and load the Program, go to advanced options and press default OS as whatever you want it to be. Then you need to reinstall GRUB and it will do it for you!

Hope this helps....

x-D :guitar:

---

### Post by prashks on 2011-08-07
> **x-D said:**
> Try boot repair, install it by doing this in the Terminal:

```

sudo add-apt-repository ppa:yannubuntu/boot-repair

sudo apt-get update && sudo apt-get install -y boot-repair-ubuntu

sudo update-grub

```Search for the Program in Unity or go to System ----> Administration ----> Boot Repair and load the Program, go to advanced options and press default OS as whatever you want it to be. Then you need to reinstall GRUB and it will do it for you!

Hope this helps....

x-D :guitar:

Thanks but I do not see Windows 7 entry in the "Boot Repair". See the screenshot attached.

---

### Post by Blasphemist on 2011-08-07
Please look at these instructions. There must be some part of this that you are overlooking. If you have more that one distro installed, do remember that grub from one of them will be in control. Make sure you aren't working with the wrong grub if there are multiple installed.
> Configuring GRUB 2
Important note: Configuration changes are normally made to /etc/default/grub and to the custom files located in /etc/grub.d. Any changes made directly to the /boot/grub/grub.cfg are overwritten whenever update-grub is executed either by the user or when called automatically by various system functions.

After editing /etc/default/grub or the scripts in the /etc/grub.d folder the user should run sudo update-grub to incorporate the changes into the GRUB 2 menu.

 Some of the most common changes, such as the default OS/kernel and menu timeout, can be changed from within a GUI applications such as StartUp-Manager or Grub Customizer. See the community doc StartUpManager for information about how to install and use this application.

/etc/default/grub (file)
The main configuration file for changing default settings. The following lines are available for alteration by the user.
GRUB_DEFAULT - Sets the default menu entry. Entries may be numeric, a complete menuentry quotation, or "saved"
GRUB_DEFAULT=0 Sets the default menu entry by menu position. Counting of entries is the same as in GRUB - the first "menuentry" in grub.cfg is 0, the second is 1, etc.
Note: Grub 1.99 introduces a submenu menu structure. For a menu item in a submenu, the entry becomes a two-digit entry. The first entry is the position of the submenu title in the main menu. The second entry is the position within the submenu. If the submenu is the 3rd entry in the main entry, and the user wishes to boot the first entry in the submenu, it would be designated as "2>0"
GRUB_DEFAULT="xxxx" An exact menu entry, including the quotation symbols, may also be used. In this case, location in the menu will not matter. Example: GRUB_DEFAULT="Ubuntu, Linux 2.6.31-9-generic"
In a Grub 1.99 submenu, the format would first include the submenu number, followed by the title. Example: "2>Ubuntu, Linux 2.6.38-8-generic"
GRUB_DEFAULT=saved
The information in this section applies to GRUB 1.98 and later.
Enables the "grub-reboot" and "grub-set-default" commands to set the default OS.
The default OS will not be set by an interactive selection of an OS from the menu.
grub-set-default Sets the default boot entry until changed.
The format is sudo grub-set-default X, with X being the menu entry position (starting with 0 as the first entry) or the exact menu string.
Examples: sudo grub-set-default 3 or sudo grub-set-default "Ubuntu, Linux 2.6.32-15-generic"
To obtain the existing menu entry choice number (starting from 0) or the menu entry "string", run grep menuentry /boot/grub/grub.cfg
grub-reboot This command sets the default boot entry for the next boot only. The format of the command is the same as for grub-set-default (see above).
GRUB_SAVEDEFAULT= If set to true this setting will automatically set the last selected OS from the menu as the default OS on the next boot.
No commands need be run to set the default OS.
Any time a menu entry is manually selected from the GRUB 2 menu, it becomes the default OS.
This option currently does not work if your /boot directory resides on an LVM partition or RAID.

---

### Post by prashks on 2011-08-07
> **oldfred said:**
> I think startup manager does not totally work with grub2 v1.99. The newest version of grub has sub menus and that has confused some of the gui tools.

If the number is not correct you can manually edit it as you started to do, just change number to correct entry in menu.

With grub2 you can now use a title instead of a number (But it has to be exact, so copy it).

But Grub 2 also lets you use the title. Suppose your Windows title is "Windows Vista (on /dev/sda1)". Then you can use in /etc/grub/default, and you won't have to edit Grub after kernel updates.

find your windows entry in grub.cfg and copy to grub default like this Vista entry - If you edit your windows command use the edited copy as this must match the title exactly:
gedit /boot/grub/grub.cfg
and copy into grub_default line here:
gksudo gedit /etc/default/grub
GRUB_DEFAULT=0
change to comment # or delete old and add new line:
#GRUB_DEFAULT=0
GRUB_DEFAULT="Windows Vista (on /dev/sda1)"
Then do:
sudo update-grub


Not sure if I have "GRUB_DEFAULT" in my grub.cfg. Have a look:

[COLOR=RoyalBlue][I]#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###[/I] [I]
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="6"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {[/I] [I]
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {[/I] [I]
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {[/I] [I]
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos[/I] [I]
insmod ext2
set root='(/dev/sda,msdos7)'
search --no-floppy --fs-uuid --set=root cdc611ef-ac2b-4e7e-8010-ef7bba0f3dc7
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1600x1200
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos7)'
search --no-floppy --fs-uuid --set=root cdc611ef-ac2b-4e7e-8010-ef7bba0f3dc7
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###[/I] [I]
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###[/I] [I]
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-10-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root cdc611ef-ac2b-4e7e-8010-ef7bba0f3dc7
    linux    /boot/vmlinuz-2.6.38-10-generic-pae root=UUID=cdc611ef-ac2b-4e7e-8010-ef7bba0f3dc7 ro  vga=799  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root cdc611ef-ac2b-4e7e-8010-ef7bba0f3dc7
    echo    'Loading Linux 2.6.38-10-generic-pae ...'
    linux    /boot/vmlinuz-2.6.38-10-generic-pae root=UUID=cdc611ef-ac2b-4e7e-8010-ef7bba0f3dc7 ro single  vga=799
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root cdc611ef-ac2b-4e7e-8010-ef7bba0f3dc7
    linux    /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=cdc611ef-ac2b-4e7e-8010-ef7bba0f3dc7 ro  vga=799  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root cdc611ef-ac2b-4e7e-8010-ef7bba0f3dc7
    echo    'Loading Linux 2.6.38-8-generic-pae ...'
    linux    /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=cdc611ef-ac2b-4e7e-8010-ef7bba0f3dc7 ro single  vga=799
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###[/I] [I]
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###[/I] [I]
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root cdc611ef-ac2b-4e7e-8010-ef7bba0f3dc7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root cdc611ef-ac2b-4e7e-8010-ef7bba0f3dc7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###[/I] [I]
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 66940E15940DE7FF
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###[/I] [I]
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###[/I] [I]
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###[/I][/COLOR]

---

### Post by x-D on 2011-08-07
> **prashks said:**
> Thanks but I do not see Windows 7 entry in the "Boot Repair". See the screenshot attached.

Click on the box where it says Ubuntu 11.04 and it will show you Windows 7!

---

### Post by oldfred on 2011-08-07
You posted grub.cfg not grub.

[COLOR=RoyalBlue]*"Windows 7 (loader) (on /dev/sda2)"*[/COLOR]

find your windows entry in grub.cfg and copy to grub default like this  Vista entry - If you edit your windows command use the edited copy as  this must match the title exactly:
gedit /boot/grub/grub.cfg
and [COLOR=Red]copy into grub_default[COLOR=Black] l[/COLOR][/COLOR]ine here:
[COLOR=DarkRed]gksudo gedit /etc/default/grub[/COLOR]
GRUB_DEFAULT=0
change to comment # or delete old and add new line:
#GRUB_DEFAULT=0
#
GRUB_DEFAULT=[COLOR=RoyalBlue]*"Windows 7 (loader) (on /dev/sda2)"*[/COLOR]
Then do:
sudo update-grub

---

