---
title: "ipv6 doens't enable in ubuntu 13.10"
date: 2014-11-13
forum: Networking &amp; Wireless
---

### Post by neuber on 2014-11-13
When I tried: cat /proc/sys/net/ipv6/conf/all/disable_ipv6: ***_no such file or directory_***. In the paste /proc/sys/net I have pastes : *_core  ipv4  netfilter  unix_*, but I don't have ipv6 paste

When I tried:  dmesg |grep IPv6[    1.160694] IPv6:***_ Loaded, but administratively disabled, reboot required to enable_***

In /etc/sysctl.conf I don't have lines with ipv6=1 

ping6 -c5 ::1
socket: Address family not supported by protocol

Please

---

### Post by TheFu on 2014-11-13
Support for 13.10 ended last June. Please move to a supported release.
The best way that I know to disable ipv6 is to blacklist the module: 
/etc/modprobe.d/blacklist.conf
with line
```
blacklist ipv6
```
I blacklist IPv6 on all our machines by default. We just aren't ready to handle the firewall rules needed to properly protect the network, so this is best in our location.

Anyway - hope that's how yours was disabled.

---

### Post by neuber on 2014-11-13
I said: I need enable ipv6 

I not said: I need disable ipv6

anyway thank you

---

### Post by TheFu on 2014-11-13
Yes, I understood that - did you check that file to see if ipv6 was blacklisted? Just remove that blacklist line ... or it could be in a separate blacklist file inside that directory.

I'm not positive that is how it is disabled on your system - just something to check.

---

### Post by neuber on 2014-11-13
I see now the file *** /etc/modprobe.d/blacklist.conf*** and not see blacklist ipv6

anything else please

---

### Post by coffeecat on 2014-11-13
@neuber, the most important advice TheFu gave you was:

> **TheFu said:**
> Support for 13.10 ended last June. Please move to a supported release.

If you back up your personal files and make a fresh installation of a supported version you won't have to worry about enabling IPv6, as it will be by default. You will also avoid the increasing security risk that the unsupported 13.10 represents.

---

### Post by neuber on 2014-11-13
I can not do a new install on this machine

I'm upgrading Ubuntu to version 14.04

---

### Post by Doug S on 2014-11-13
> **TheFu said:**
> Support for 13.10 ended last June. Please move to a supported release.
The best way that I know to disable ipv6 is to blacklist the module: 
/etc/modprobe.d/blacklist.conf
with line
```
blacklist ipv6
```
I blacklist IPv6 on all our machines by default. We just aren't ready to handle the firewall rules needed to properly protect the network, so this is best in our location.

Anyway - hope that's how yours was disabled.I was not aware of that method. I do it in grub:```
GRUB_CMDLINE_LINUX_DEFAULT="[COLOR=#ff0000]ipv6.disable=1[/COLOR] intel_pstate=enable crashkernel=384M-:128M"
```So, for the OP, check if it is dsiabled in /etc/default/grub.

---

### Post by neuber on 2014-11-13
Now I have ubuntu 14.04 lts

I do this [B][I][U]GRUB_CMDLINE_LINUX_DEFAULT="[COLOR=#ff0000]ipv6.disable=1[/COLOR] intel_pstate=enable crashkernel=384M-:128M"

[/U][/I][/B]but don't solved

---

### Post by TheFu on 2014-11-13
I'm confused. If you tell grub to disable it - like above, why would it be enabled?

Also, the rest of the network equipment has to support IPv6 for this to be useful too. Has that been validated?  Sure, you can run IPv6 for internal system stuff, but that doesn't make the switches, routers and ISP support it.

The Ubuntu IPv6 help page: [https://wiki.ubuntu.com/IPv6](https://wiki.ubuntu.com/IPv6)

---

### Post by neuber on 2014-11-13
I did not say to grub disable ipv6

I exclude: "[COLOR=#545454][FONT=arial]**ipv6**[/FONT][/COLOR][COLOR=#545454][FONT=arial].[/FONT][/COLOR][COLOR=#545454][FONT=arial]**disable**[/FONT][/COLOR][COLOR=#545454][FONT=arial]=1"

My router is dir 825. I have ipv6 on windws 8.1

But real problem now, I guess, is

In ubuntu 14.04 lts I don't see ipv6 paste in /proc/sys/net[/FONT][/COLOR]

[http://ubuntuforums.org/showthread.php?t=1839150](http://ubuntuforums.org/showthread.php?t=1839150)

I see that of the 2011

no command works for me, including***_ ip a | grep inet_***6

please, help me to edit file***_ /proc/cmdline,_*** because I need change***_ 1_*** to***_ 0_*** in this file:
***_cat /proc/cmdline _***
BOOT_IMAGE=/boot/vmlinuz-3.13.0-39-generic root=UUID=9a182809-ba2b-4339-a73d-b61864c51b18 ro ipv6.disable=1 quiet splash vt.handoff=7

---

### Post by coffeecat on 2014-11-15
I don't think that's the way to do it. You confused us by saying this in post #10

> I do this GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1 intel_pstate=enable crashkernel=384M-:128M"

And then this in post #12:

> I did not say to grub disable ipv6

I exclude: "ipv6.disable=1"

Which seems to be contradictory, or it's certainly unclear.

Post the complete contents of /boot/grub/grub.cfg and /etc/default/grub. When you post them, do not simply post them into your post otherwise you will get an unreadable wall of text. Post them between [noparse]```
 and 
```[/noparse] BBCode tags to maintain formatting. You can simply type out the code tags or use the icon that looks like # in the toolbar of the advanced editor.

---

### Post by neuber on 2014-11-16
gedit /boot/grub/grub.cfg

```

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
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

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
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos
insmod ext2
set root='hd0,msdos3'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  9a182809-ba2b-4339-a73d-b61864c51b18
else
  search --no-floppy --fs-uuid --set=root 9a182809-ba2b-4339-a73d-b61864c51b18
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=pt_BR
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=-1
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=10
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=10
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-9a182809-ba2b-4339-a73d-b61864c51b18' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos3'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  9a182809-ba2b-4339-a73d-b61864c51b18
    else
      search --no-floppy --fs-uuid --set=root 9a182809-ba2b-4339-a73d-b61864c51b18
    fi
    linux    /boot/vmlinuz-3.13.0-39-generic root=UUID=9a182809-ba2b-4339-a73d-b61864c51b18 ro  ipv6.disable=1 quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-39-generic
}
submenu 'Opções avançadas para Ubuntu' $menuentry_id_option 'gnulinux-advanced-9a182809-ba2b-4339-a73d-b61864c51b18' {
    menuentry 'Ubuntu, com Linux 3.13.0-39-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-39-generic-advanced-9a182809-ba2b-4339-a73d-b61864c51b18' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  9a182809-ba2b-4339-a73d-b61864c51b18
        else
          search --no-floppy --fs-uuid --set=root 9a182809-ba2b-4339-a73d-b61864c51b18
        fi
        echo    'Carregando Linux 3.13.0-39-generic ...'
        linux    /boot/vmlinuz-3.13.0-39-generic root=UUID=9a182809-ba2b-4339-a73d-b61864c51b18 ro  ipv6.disable=1 quiet splash $vt_handoff
        echo    'Carregando ramdisk inicial ...'
        initrd    /boot/initrd.img-3.13.0-39-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-39-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-39-generic-recovery-9a182809-ba2b-4339-a73d-b61864c51b18' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  9a182809-ba2b-4339-a73d-b61864c51b18
        else
          search --no-floppy --fs-uuid --set=root 9a182809-ba2b-4339-a73d-b61864c51b18
        fi
        echo    'Carregando Linux 3.13.0-39-generic ...'
        linux    /boot/vmlinuz-3.13.0-39-generic root=UUID=9a182809-ba2b-4339-a73d-b61864c51b18 ro recovery nomodeset 
        echo    'Carregando ramdisk inicial ...'
        initrd    /boot/initrd.img-3.13.0-39-generic
    }
    menuentry 'Ubuntu, com Linux 3.11.0-26-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-26-generic-advanced-9a182809-ba2b-4339-a73d-b61864c51b18' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  9a182809-ba2b-4339-a73d-b61864c51b18
        else
          search --no-floppy --fs-uuid --set=root 9a182809-ba2b-4339-a73d-b61864c51b18
        fi
        echo    'Carregando Linux 3.11.0-26-generic ...'
        linux    /boot/vmlinuz-3.11.0-26-generic root=UUID=9a182809-ba2b-4339-a73d-b61864c51b18 ro  ipv6.disable=1 quiet splash $vt_handoff
        echo    'Carregando ramdisk inicial ...'
        initrd    /boot/initrd.img-3.11.0-26-generic
    }
    menuentry 'Ubuntu, with Linux 3.11.0-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-26-generic-recovery-9a182809-ba2b-4339-a73d-b61864c51b18' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  9a182809-ba2b-4339-a73d-b61864c51b18
        else
          search --no-floppy --fs-uuid --set=root 9a182809-ba2b-4339-a73d-b61864c51b18
        fi
        echo    'Carregando Linux 3.11.0-26-generic ...'
        linux    /boot/vmlinuz-3.11.0-26-generic root=UUID=9a182809-ba2b-4339-a73d-b61864c51b18 ro recovery nomodeset 
        echo    'Carregando ramdisk inicial ...'
        initrd    /boot/initrd.img-3.11.0-26-generic
    }
    menuentry 'Ubuntu, com Linux 3.8.0-34-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-34-generic-advanced-9a182809-ba2b-4339-a73d-b61864c51b18' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  9a182809-ba2b-4339-a73d-b61864c51b18
        else
          search --no-floppy --fs-uuid --set=root 9a182809-ba2b-4339-a73d-b61864c51b18
        fi
        echo    'Carregando Linux 3.8.0-34-generic ...'
        linux    /boot/vmlinuz-3.8.0-34-generic root=UUID=9a182809-ba2b-4339-a73d-b61864c51b18 ro  ipv6.disable=1 quiet splash $vt_handoff
        echo    'Carregando ramdisk inicial ...'
        initrd    /boot/initrd.img-3.8.0-34-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-34-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-34-generic-recovery-9a182809-ba2b-4339-a73d-b61864c51b18' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  9a182809-ba2b-4339-a73d-b61864c51b18
        else
          search --no-floppy --fs-uuid --set=root 9a182809-ba2b-4339-a73d-b61864c51b18
        fi
        echo    'Carregando Linux 3.8.0-34-generic ...'
        linux    /boot/vmlinuz-3.8.0-34-generic root=UUID=9a182809-ba2b-4339-a73d-b61864c51b18 ro recovery nomodeset 
        echo    'Carregando ramdisk inicial ...'
        initrd    /boot/initrd.img-3.8.0-34-generic
    }
    menuentry 'Ubuntu, com Linux 3.8.0-19-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-19-generic-advanced-9a182809-ba2b-4339-a73d-b61864c51b18' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  9a182809-ba2b-4339-a73d-b61864c51b18
        else
          search --no-floppy --fs-uuid --set=root 9a182809-ba2b-4339-a73d-b61864c51b18
        fi
        echo    'Carregando Linux 3.8.0-19-generic ...'
        linux    /boot/vmlinuz-3.8.0-19-generic root=UUID=9a182809-ba2b-4339-a73d-b61864c51b18 ro  ipv6.disable=1 quiet splash $vt_handoff
        echo    'Carregando ramdisk inicial ...'
        initrd    /boot/initrd.img-3.8.0-19-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-19-generic-recovery-9a182809-ba2b-4339-a73d-b61864c51b18' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  9a182809-ba2b-4339-a73d-b61864c51b18
        else
          search --no-floppy --fs-uuid --set=root 9a182809-ba2b-4339-a73d-b61864c51b18
        fi
        echo    'Carregando Linux 3.8.0-19-generic ...'
        linux    /boot/vmlinuz-3.8.0-19-generic root=UUID=9a182809-ba2b-4339-a73d-b61864c51b18 ro recovery nomodeset 
        echo    'Carregando ramdisk inicial ...'
        initrd    /boot/initrd.img-3.8.0-19-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos3'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  9a182809-ba2b-4339-a73d-b61864c51b18
    else
      search --no-floppy --fs-uuid --set=root 9a182809-ba2b-4339-a73d-b61864c51b18
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos3'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  9a182809-ba2b-4339-a73d-b61864c51b18
    else
      search --no-floppy --fs-uuid --set=root 9a182809-ba2b-4339-a73d-b61864c51b18
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 8 (loader) (em /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-5638A22A38A20957' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  5638A22A38A20957
    else
      search --no-floppy --fs-uuid --set=root 5638A22A38A20957
    fi
    parttool ${root} hidden-
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry 'Windows 8 (loader) (em /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-chain-EC26A55726A52414' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  EC26A55726A52414
    else
      search --no-floppy --fs-uuid --set=root EC26A55726A52414
    fi
    parttool ${root} hidden-
    drivemap -s (hd0) ${root}
    chainloader +1
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

```

gedit /etc/default/grub

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

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

> **neuber said:**
> please, help me to edit file***_ /proc/cmdline,_*** because I need change***_ 1_*** to***_ 0_*** in this file:
***_cat /proc/cmdline _***
BOOT_IMAGE=/boot/vmlinuz-3.13.0-39-generic root=UUID=9a182809-ba2b-4339-a73d-b61864c51b18 ro ipv6.disable=1 quiet splash vt.handoff=7


I tried edit /proc/cmdline in windows 8.1 (using linux reader) but the file (cmdline) not appear in the paste /proc

---

### Post by Doug S on 2014-11-16
Have you run:```
sudo update-grub
```on that version of /etc/default/grub? If not do so, and observe, and/or post, any differences in the resulting /boot/grub/grub.cfg

---

### Post by coffeecat on 2014-11-16
> **neuber said:**
> I tried edit /proc/cmdline in windows 8.1 (using linux reader) but the file (cmdline) not appear in the paste /proc

You cannot edit anything in /proc. It is a virtual filesystem, created when you boot up.

It looks as though perhaps you added *ipv6.disable=1 * to the GRUB_CMDLINE_LINUX_DEFAULT line in /etc/default/grub and then removed it? Simply run the command that Doug S has posted, tell us whether this line in your grub.cfg changes:

```
linux    /boot/vmlinuz-3.13.0-39-generic root=UUID=9a182809-ba2b-4339-a73d-b61864c51b18 ro  ipv6.disable=1 quiet splash $vt_handoff
```

And then reboot.

---

### Post by neuber on 2014-11-16
update-grub

solved

---

### Post by mörgæs on 2014-11-16
Please use thread tools for marking a thread solved.

---

