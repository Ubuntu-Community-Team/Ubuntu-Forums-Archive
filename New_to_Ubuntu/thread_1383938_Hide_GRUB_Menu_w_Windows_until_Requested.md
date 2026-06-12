---
title: "Hide GRUB Menu w/ Windows until Requested"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by dmaxel on 2010-01-17
Hi all,

I currently have a dual-boot setup between Ubuntu 9.10 and Windows 7, using GRUB 2. Although this may defeat the purpose of the dual-boot, I do not really need my Windows 7 on a constant basis (with exceptions). I would like to know if it would be possible to make it so that the GRUB menu is completely hidden (aka never shows up) unless I ask for it by pressing F8 or F10 (whatever the button for it is). Would this be possible even though I have Windows on my system? Thanks

---

### Post by raymondh on 2010-01-17
> **dmaxel said:**
>  I would like to know if it would be possible to make it so that the GRUB menu is completely hidden (aka never shows up) unless I ask for it by pressing F8 or F10 (whatever the button for it is). Would this be possible even though I have Windows on my system? Thanks

Hello,

Unless I misunderstood you, what you're wanting is possible in virtualization but not in a dual-boot scenario.

One option for you is to set windows as the default boot and reduce the waiting time to boot windows.  I believe startup manager can now work with GRUB2 ... but do research on that as I do not use GRUB2 at the moment and have not verified that.

Another option, if you have 2HD's, is to separate both OS' per HD and have each OS controlled by their respective bootloaders.  With this set-up, you now control boot using BIOS.

Regards,

Raymond

---

### Post by dmaxel on 2010-01-17
Well, this is on a laptop, so it's only one HDD. Also, I want to "hide" GRUB so that it can boot straight into Ubuntu, unless I request the GRUB menu to be shown at boot by pressing F8/10/whatever so that I can choose Windows instead. Not the other way around.

---

### Post by admiralspark on 2010-01-17
Well, you're right, that would defeat the purpose of Grub. The closest thing you can have to what you're looking for would be to set Ubuntu as the default, and lower the boot screen time to 2~3 seconds. This would give you enough time to choose the windows install if you needed to, but otherwise will only tack on a couple extra seconds to booting into ubuntu. 
The usage of the f8, f10 etc keys is for the BIOS, not Grub. It would take strong programming skills to make it work otherwise (and it would still show SOME screen that would take place of the Grub menu with the option to press f8 etc).

---

### Post by raymondh on 2010-01-17
> **admiralspark said:**
> Well, you're right, that would defeat the purpose of Grub. The closest thing you can have to what you're looking for would be to set Ubuntu as the default, and lower the boot screen time to 2~3 seconds. This would give you enough time to choose the windows install if you needed to, but otherwise will only tack on a couple extra seconds to booting into ubuntu. 
The usage of the f8, f10 etc keys is for the BIOS, not Grub. It would take strong programming skills to make it work otherwise (and it would still show SOME screen that would take place of the Grub menu with the option to press f8 etc).

+ 1

My apologies ... I was under the impression that you wanted access to both (or either) OS' using a keystroke, after a default OS has booted up.  And, I thought you wanted windows as the default.

As admiralsparks has said, set Ubunutu as default and lower the time to about 2-3 secs.  That will give you enough time to hit the space key and stop the boot and select the other OS.

Raymond

---

### Post by dmaxel on 2010-01-17
I guess I'll just have to do that then. Thanks for clarifying.

---

### Post by drs305 on 2010-01-17
dmaxel,

To boot the system into Linux (or whatever the GRUB_DEFAULT=0 value points to) without ever displaying a menu:

1. Edit /etc/default/grub and use these values. Once changed and saved, update grub.cfg with "sudo update-grub".

> 
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=1
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="0"


This will boot to the first menuentry in /boot/grub/grub.cfg.
The GRUB_HIDDEN_TIMEOUT value can be 0 if you wish.
Pressing any key won't display the menu since it would revert to the GRUB_TIMEOUT value of 0, which would go straight into the default boot without displaying the menu.
*Holding down the SHIFT key as the system boots will reveal the menu, which will stay visible until a selection is made.*

2. For this to work, the keystatus check must be available. I believe (at least as of Grub 1.97~beta-1ubuntu5) that this is still only contained in /etc/grub.d/30_os-prober. If you deactivate this file you will need to copy the keystatus check into /etc/grub.d/00_header or a custom file to ensure the check is still accomplished.


*If this is the solution you were looking for, please mark the thread solved via the Thread Tools link near the upper right of the original post.*

---

### Post by dmaxel on 2010-01-17
> **drs305 said:**
> dmaxel,

To boot the system into Linux (or whatever the GRUB_DEFAULT=0 value points to) without ever displaying a menu:

1. Edit /etc/default/grub and use these values. Once changed and saved, update grub.cfg with "sudo update-grub".



This will boot to the first menuentry in /boot/grub/grub.cfg.
The GRUB_HIDDEN_TIMEOUT value can be 0 if you wish.
Pressing any key won't display the menu since it would revert to the GRUB_TIMEOUT value of 0, which would go straight into the default boot without displaying the menu.
*Holding down the SHIFT key as the system boots will reveal the menu, which will stay visible until a selection is made.*

2. For this to work, the keystatus check must be available. I believe (at least as of Grub 1.97~beta-1ubuntu5) that this is still only contained in /etc/grub.d/30_os-prober. If you deactivate this file you will need to copy the keystatus check into /etc/grub.d/00_header or a custom file to ensure the check is still accomplished.


*If this is the solution you were looking for, please mark the thread solved via the Thread Tools link near the upper right of the original post.*
I guess that's what I was looking for, but I can keep it simple and just make it wait a mere 2 seconds. Thanks for this though, especially in case anyone else needs it, or if I decide to do that at some point in the future.

---

### Post by hariks0 on 2010-08-03
I have renamed the 30_os-prober to 09_os-prober to avoid messing up the order of windows entry in grub. Can you please tell me which part of my 09_os-prober is to be copied and pasted to 00_header. The contents of my 09_os_prober is :-
```
#! /bin/sh -e

# grub-mkconfig helper script.
# Copyright (C) 2006,2007,2008,2009  Free Software Foundation, Inc.
#
# GRUB is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# GRUB is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.

prefix=/usr
exec_prefix=${prefix}
libdir=${exec_prefix}/lib

. ${libdir}/grub/grub-mkconfig_lib

found_other_os=

adjust_timeout () {
  if [ "x${found_other_os}" = "x" ] ; then
    if [ "x${GRUB_HIDDEN_TIMEOUT}" != "x" ] ; then
      if [ "x${GRUB_HIDDEN_TIMEOUT_QUIET}" = "xtrue" ] ; then
	verbose=
      else
	verbose=" --verbose"
      fi

      if [ "x${GRUB_HIDDEN_TIMEOUT}" = "x0" ] ; then
	cat <<EOF
[I][COLOR="DarkOrange"]if [ \${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep$verbose --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
EOF
      else
	cat << EOF
if [ \${timeout} != -1 ]; then
  if sleep$verbose --interruptible ${GRUB_HIDDEN_TIMEOUT} ; then
    set timeout=0
  fi
fi
EOF
      fi
    fi
  fi
}

if [ "x${GRUB_DISABLE_OS_PROBER}" = "xtrue" ]; then
  adjust_timeout
  exit 0
fi

if [ -z "`which os-prober 2> /dev/null`" -o -z "`which linux-boot-prober 2> /dev/null`" ] ; then
  # missing os-prober and/or linux-boot-prober
  adjust_timeout
  exit 0
fi

OSPROBED="`os-prober | tr ' ' '^' | paste -s -d ' '`"
if [ -z "${OSPROBED}" ] ; then
  # empty os-prober output, nothing doing
  adjust_timeout
  exit 0
fi[/COLOR][/I]

osx_entry() {
        cat << EOF
menuentry "${LONGNAME} (${2}-bit) (on ${DEVICE})" {
EOF
	save_default_entry | sed -e "s/^/\t/"
	prepare_grub_to_access_device ${DEVICE} | sed -e "s/^/\t/"
	cat << EOF
        insmod ${GRUB_VIDEO_BACKEND}
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ \$do_resume == 0 ]; then
           xnu_uuid ${OSXUUID} uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           $1 /mach_kernel boot-uuid=\${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
EOF
}

for OS in ${OSPROBED} ; do
  DEVICE="`echo ${OS} | cut -d ':' -f 1`"
  LONGNAME="`echo ${OS} | cut -d ':' -f 2 | tr '^' ' '`"
  LABEL="`echo ${OS} | cut -d ':' -f 3 | tr '^' ' '`"
  BOOT="`echo ${OS} | cut -d ':' -f 4`"

  if [ -z "${LONGNAME}" ] ; then
    LONGNAME="${LABEL}"
  fi

  echo "Found ${LONGNAME} on ${DEVICE}" >&2
  found_other_os=1

  case ${BOOT} in
    chain)

      cat << EOF
menuentry "${LONGNAME} (on ${DEVICE})" {
EOF
      save_default_entry | sed -e "s/^/\t/"
      prepare_grub_to_access_device ${DEVICE} | sed -e "s/^/\t/"

      case ${LONGNAME} in
	Windows\ Vista*|Windows\ 7*)
	;;
	*)
	  cat << EOF
	drivemap -s (hd0) \${root}
EOF
	;;
      esac

      cat <<EOF
	chainloader +1
}
EOF
    ;;
    linux)
      LINUXPROBED="`linux-boot-prober ${DEVICE} 2> /dev/null | tr ' ' '^' | paste -s -d ' '`"
      prepare_boot_cache=

      for LINUX in ${LINUXPROBED} ; do
        LROOT="`echo ${LINUX} | cut -d ':' -f 1`"
        LBOOT="`echo ${LINUX} | cut -d ':' -f 2`"
        LLABEL="`echo ${LINUX} | cut -d ':' -f 3 | tr '^' ' '`"
        LKERNEL="`echo ${LINUX} | cut -d ':' -f 4`"
        LINITRD="`echo ${LINUX} | cut -d ':' -f 5`"
        LPARAMS="`echo ${LINUX} | cut -d ':' -f 6- | tr '^' ' '`"

        if [ -z "${LLABEL}" ] ; then
          LLABEL="${LONGNAME}"
        fi

	if [ "${LROOT}" != "${LBOOT}" ]; then
	  LKERNEL="${LKERNEL#/boot}"
	  LINITRD="${LINITRD#/boot}"
	fi

        cat << EOF
menuentry "${LLABEL} (on ${DEVICE})" {
EOF
	save_default_entry | sed -e "s/^/\t/"
	if [ -z "${prepare_boot_cache}" ]; then
	  prepare_boot_cache="$(prepare_grub_to_access_device ${LBOOT} | sed -e "s/^/\t/")"
	fi
	printf '%s\n' "${prepare_boot_cache}"
	cat <<  EOF
	linux ${LKERNEL} ${LPARAMS}
EOF
        if [ -n "${LINITRD}" ] ; then
          cat << EOF
	initrd ${LINITRD}
EOF
        fi
        cat << EOF
}
EOF
      done
    ;;
    macosx)
      OSXUUID="`grub-probe --target=fs_uuid --device ${DEVICE} 2> /dev/null`"
      osx_entry xnu_kernel 32
      osx_entry xnu_kernel64 64
    ;;
    hurd)
      cat << EOF
menuentry "${LONGNAME} (on ${DEVICE})" {
EOF
      save_default_entry | sed -e "s/^/\t/"
      prepare_grub_to_access_device ${DEVICE} | sed -e "s/^/\t/"
      grub_device="`${grub_probe} --device ${DEVICE} --target=drive`"
      mach_device="`echo "${grub_device}" | tr -d '()' | tr , s`"
      grub_fs="`${grub_probe} --device ${DEVICE} --target=fs`"
      case "${grub_fs}" in
	*fs)	hurd_fs="${grub_fs}" ;;
	*)	hurd_fs="${grub_fs}fs" ;;
      esac
      cat << EOF
	multiboot /boot/gnumach.gz root=device:${mach_device}
	module /hurd/${hurd_fs}.static ${hurd_fs} --readonly \\
			--multiboot-command-line='\${kernel-command-line}' \\
			--host-priv-port='\${host-port}' \\
			--device-master-port='\${device-port}' \\
			--exec-server-task='\${exec-task}' -T typed '\${root}' \\
			'\$(task-create)' '\$(task-resume)'
	module /lib/ld.so.1 exec /hurd/exec '\$(exec-task=task-create)'
}
EOF
    ;;
    *)
      echo "  ${LONGNAME} is not yet supported by grub-mkconfig." >&2
    ;;
  esac
done

adjust_timeout
```

Is it the highlighted portion in the above?

---

### Post by drs305 on 2010-08-03
haricks0,

This is the portion you would want in your 00_header file to incorporate the keystatus check:

> 
	cat <<EOF
if [ \${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=[COLOR="DarkRed"]3[/COLOR]
    fi
  else
    if sleep$verbose --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
EOF

Change the numeral in [COLOR="DarkRed"]dark red[/COLOR] to a value in seconds.

I have not checked recently to see if Grub2 has changed the conditions under which the keystatus check is accomplished; I don't believe it has. Inserting this section into 00_header should allow the check even when 30_os-prober (or 09_os-prober) isn't run.

Run "sudo update-grub" to make this section effective.

---

### Post by hariks0 on 2010-08-05
Thank you very much. It worked like a charm. BTW, I just modified the seconds of Grub menu waiting in Startup Manager instead of 'sudo update-grub'. The set timeout is still 0 and Grub is displayed if I press and hold 'shift' during boot.

:popcorn:

---

