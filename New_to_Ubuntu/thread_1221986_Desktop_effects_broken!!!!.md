---
title: "Desktop effects broken!!!!"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by steigerjb on 2009-07-24
hey!, what happened???? I noticed there was no desktops effects so I went in visual effects to check and it was turned off. So I tried turning it back on...it said desktop effects could not be enabled....NOOOOOOO!!!!! What now??? 

:confused::confused::confused::confused::confused::confused::confused:

---

### Post by OffAxis on 2009-07-24
do you have the Proprietary Driver enabled for your hardware?

---

### Post by steigerjb on 2009-07-24
> **OffAxis said:**
> do you have the Proprietary Driver enabled for your hardware?

yes

[http://i29.tinypic.com/w9flop.png](http://i29.tinypic.com/w9flop.png)

---

### Post by Ratscallion on 2009-07-24
Try going 
```
gedit /usr/bin/compiz
```
Check if your card is blacklisted, if it is, unblacklist it by shoving a # in front of that line.

---

### Post by steigerjb on 2009-07-24
> **Ratscallion said:**
> Try going 
```
gedit /usr/bin/compiz
```
Check if your card is blacklisted, if it is, unblacklist it by shoving a # in front of that line.

umm, can you check. I don't know what you mean

```

#!/bin/sh
# Compiz Manager wrapper script
# 
# Copyright (c) 2007 Kristian Lyngstøl <kristian@bohemians.org>
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 51 Franklin St, Fifth Floor, Boston, MA  02110-1301  USA
#
#
# Contributions by: Treviño (3v1n0) <trevi55@gmail.com>, Ubuntu Packages
#
# Much of this code is based on Beryl code, also licensed under the GPL.
# This script will detect what options we need to pass to compiz to get it
# started, and start a default plugin and possibly window decorator.
# 


COMPIZ_BIN_PATH="/usr/local/bin/" # For window decorators and compiz
PLUGIN_PATH="/usr/local/lib/compiz/" 
GLXINFO="/usr/bin/glxinfo"
KWIN="/usr/bin/kwin"
METACITY="/usr/bin/metacity"
XFWM="/usr/bin/xfwm"
COMPIZ_NAME="compiz" # Final name for compiz (compiz.real) 

# For Xgl LD_PRELOAD
LIBGL_NVIDIA="/usr/lib/nvidia/libGL.so.1.2.xlibmesa"
LIBGL_FGLRX="/usr/lib/fglrx/libGL.so.1.2.xlibmesa"

# Minimum amount of memory (in kilo bytes) that nVidia cards need
# to be allowed to start
# Set to 262144 to require 256MB
NVIDIA_MEMORY="65536" # 64MB
NVIDIA_SETTINGS="nvidia-settings" # Assume it's in the path by default

# For detecting what driver is in use, the + is for one or more /'s
XORG_DRIVER_PATH="/usr/lib/xorg/modules/drivers/+"
FALLBACKWM="xterm"
if [ x"$KDE_FULL_SESSION" = x"true" ]; then 
        FALLBACKWM="${KWIN}";
elif [ x"$GNOME_DESKTOP_SESSION_ID" != x"" ]; then 
        FALLBACKWM="${METACITY}"
elif xprop -root _DT_SAVE_MODE | grep ' = \"xfce4\"$' >/dev/null 2>&1; then 
        FALLBACKWM="${XFWM}"
fi

FALLBACKWM_OPTIONS="--replace $@"

# Driver whitelist
WHITELIST="nvidia intel ati radeon i810 fglrx"

# blacklist based on the pci ids 
# See http://wiki.compiz-fusion.org/Hardware/Blacklist for details
#T="   1002:5954 1002:5854 1002:5955" # ati rs480
#T="$T 1002:4153" # ATI Rv350
#T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965
#T="$T 8086:2e02 " # Intel Eaglelake
T="$T 8086:3577 8086:2562 " # Intel 830MG, 845G (LP: #259385)
BLACKLIST_PCIIDS="$T"
unset T

COMPIZ_OPTIONS="--ignore-desktop-hints --replace"
COMPIZ_PLUGINS="core"
ENV=""

# Use emerald by default if it exist
USE_EMERALD="yes"

# No indirect by default
INDIRECT="no"

# Default X.org log if xset q doesn't reveal it
XORG_DEFAULT_LOG="/var/log/Xorg.0.log"

# Set to yes to enable verbose
VERBOSE="yes"

# Echos the arguments if verbose
verbose()
{
	if [ "x$VERBOSE" = "xyes" ]; then
		printf "$*"
	fi
}

# abort script and run fallback windowmanager
abort_with_fallback_wm()
{
	if [ "x$SKIP_CHECKS" = "xyes" ]; then
		verbose "SKIP_CHECKS is yes, so continuing despite problems.\n"
		return 0;
	fi
	
	if [ "x$CM_DRY" = "xyes" ]; then
		verbose "Dry run failed: Problems detected with 3D support.'n"
		exit 1;
	fi

	verbose "aborting and using fallback: $FALLBACKWM \n"

	if [ -x $FALLBACKWM ]; then
		exec $FALLBACKWM $FALLBACKWM_OPTIONS
	else
		printf "no $FALLBACKWM found, exiting\n"
		exit 1
	fi
}

# Check if we run with the Software Rasterizer, this happens e.g.
# when a second screen session is opened via f-u-a on intel
check_software_rasterizer()
{
	verbose "Checking for Software Rasterizer: "
	if glxinfo 2> /dev/null | egrep -q '^OpenGL renderer string: Software Rasterizer' ; then
		verbose "present. \n";
		return 0;
	else
		verbose "Not present. \n"
		return 1;
	fi

}

# Check for non power of two texture support
check_npot_texture()
{
	verbose "Checking for non power of two support: "
	if glxinfo 2> /dev/null | egrep -q '(GL_ARB_texture_non_power_of_two|GL_NV_texture_rectangle|GL_EXT_texture_rectangle|GL_ARB_texture_rectangle)' ; then
		verbose "present. \n";
		return 0;
	else
		verbose "Not present. \n"
		return 1;
	fi

}

# Check for presence of FBConfig
check_fbconfig()
{
	verbose "Checking for FBConfig: "
	if [ "$INDIRECT" = "yes" ]; then
		$GLXINFO -i | grep -q GLX.*fbconfig 
		FB=$?
	else
		$GLXINFO | grep -q GLX.*fbconfig 
		FB=$?
	fi

	if [ $FB = "0" ]; then
		unset FB
		verbose "present. \n"
		return 0;
	else
		unset FB
		verbose "not present. \n"
		return 1;
	fi
}


# Check for TFP
check_tfp()
{
	verbose "Checking for texture_from_pixmap: "
	if [ $($GLXINFO 2>/dev/null | grep -c GLX_EXT_texture_from_pixmap) -gt 2 ] ; then
		verbose "present. \n"
		return 0;
	else
		verbose "not present. \n"
		if [ "$INDIRECT" = "yes" ]; then
			unset LIBGL_ALWAYS_INDIRECT
			INDIRECT="no"
			return 1;
		else
			verbose "Trying again with indirect rendering:\n";
			INDIRECT="yes"
			export LIBGL_ALWAYS_INDIRECT=1
			check_tfp;
			return $?
		fi
	fi
}

# Check wether the composite extension is present
check_composite()
{
	verbose "Checking for Composite extension: "
	if xdpyinfo -queryExtensions | grep -q Composite ; then
		verbose "present. \n";
		return 0;
	else
		verbose "not present. \n";
		return 1;
	fi
}

# Detects if Xgl is running
check_xgl()
{
	verbose "Checking for Xgl: "
	if xvinfo | grep -q Xgl ; then
		verbose "present. \n"
		return 0;
	else
		verbose "not present. \n"
		return 1;
	fi
}

# Check if the nVidia card has enough video ram to make sense
check_nvidia_memory()
{
    if [ ! -x "$NVIDIA_SETTINGS" ]; then
	return 0
    fi

	MEM=$(${NVIDIA_SETTINGS} -q VideoRam | egrep Attribute\ \'VideoRam\'\ .*: | cut -d: -f3 | sed 's/[^0-9]//g')
	if [ $MEM -lt $NVIDIA_MEMORY ]; then
		verbose "Less than ${NVIDIA_MEMORY}kb of memory and nVidia";
		return 1;
	fi
	return 0;
}

# Check for existence if NV-GLX
check_nvidia()
{
	if [ ! -z $NVIDIA_INTERNAL_TEST ]; then
		return $NVIDIA_INTERNAL_TEST;
	fi
	verbose "Checking for nVidia: "
	if xdpyinfo | grep -q NV-GLX ; then
		verbose "present. \n"
		NVIDIA_INTERNAL_TEST=0
		return 0;
	else
		verbose "not present. \n"
		NVIDIA_INTERNAL_TEST=1
		return 1;
	fi
}

# Check if the max texture size is large enough compared to the resolution
check_texture_size()
{
	# Check how many screens we've got and iterate over them
	N=$(xdpyinfo | grep -i "number of screens" | sed 's/.*[^0-9]//g')
	for i in $(seq 1 $N); do
	    verbose "Checking screen $i"
	    TEXTURE_LIMIT=$(glxinfo -l | grep GL_MAX_TEXTURE_SIZE | sed -n "$i s/^.*=[^0-9]//g p")
	    RESOLUTION=$(xdpyinfo | grep -i dimensions: | sed -n -e "$i s/^ *dimensions: *\([0-9]*x[0-9]*\) pixels.*/\1/ p")
	    VRES=$(echo $RESOLUTION | sed 's/.*x//')
	    HRES=$(echo $RESOLUTION | sed 's/x.*//')
	    verbose "Comparing resolution ($RESOLUTION) to maximum 3D texture size ($TEXTURE_LIMIT): ";
	    if [ $VRES -gt $TEXTURE_LIMIT ] || [ $HRES -gt $TEXTURE_LIMIT ]; then
		verbose "Failed.\n"
		return 1;
	    fi
	    verbose "Passed.\n"
	done
	return 0
}

# check driver whitelist
running_under_whitelisted_driver()
{
	LOG=$(xset q|grep "Log file"|awk '{print $3}')
	if [ "$LOG" = "" ]; then
	    verbose "xset q doesn't reveal the location of the log file. Using fallback $XORG_DEFAULT_LOG \n"
	    LOG=$XORG_DEFAULT_LOG;
	fi
	if [ -z "$LOG" ];then
		verbose "AIEEEEH, no Log file found \n"
		verbose "$(xset q) \n"
	return 0
	fi
	for DRV in ${WHITELIST}; do
		if egrep -q "Loading ${XORG_DRIVER_PATH}${DRV}_drv\.so" $LOG &&
		   ! egrep -q "Unloading ${XORG_DRIVER_PATH}${DRV}_drv\.so" $LOG; 
		then
			return 0
		fi
	done
	verbose "No whitelisted driver found\n"
	return 1
}

# check pciid blacklist
have_blacklisted_pciid()
{
	OUTPUT=$(lspci -n)
	for ID in ${BLACKLIST_PCIIDS}; do
		if echo "$OUTPUT" | egrep -q "$ID"; then
			verbose "Blacklisted PCIID '$ID' found \n"
			return 0
		fi
	done
	OUTPUT=$(lspci -vn | grep -i VGA)
	verbose "Detected PCI ID for VGA: $OUTPUT\n"
	return 1
}

build_env()
{
	if check_nvidia; then
		ENV="__GL_YIELD=NOTHING "
	fi
	if [ "$INDIRECT" = "yes" ]; then
		ENV="$ENV LIBGL_ALWAYS_INDIRECT=1 "
	fi
	if check_xgl; then
		if [ -f ${LIBGL_NVIDIA} ]; then
			ENV="$ENV LD_PRELOAD=${LIBGL_NVIDIA}"
			verbose "Enabling Xgl with nVidia drivers...\n"
		fi
		if [ -f ${LIBGL_FGLRX} ]; then
			ENV="$ENV LD_PRELOAD=${LIBGL_FGLRX}"
			verbose "Enabling Xgl with fglrx ATi drivers...\n"
		fi
	fi

	ENV="$ENV FROM_WRAPPER=yes"

	if [ -n "$ENV" ]; then
		export $ENV
	fi
}

build_args()
{
	if [ "x$INDIRECT" = "xyes" ]; then
		COMPIZ_OPTIONS="$COMPIZ_OPTIONS --indirect-rendering "
	fi
	if [ ! -z "$DESKTOP_AUTOSTART_ID" ]; then
		COMPIZ_OPTIONS="$COMPIZ_OPTIONS --sm-client-id $DESKTOP_AUTOSTART_ID"
	fi
	if check_nvidia; then
		if [ "x$INDIRECT" != "xyes" ]; then
			COMPIZ_OPTIONS="$COMPIZ_OPTIONS --loose-binding"
		fi
	fi
}

####################
# Execution begins here.

# Read configuration from XDG paths
if [ -z "$XDG_CONFIG_DIRS" ]; then
	test -f /etc/xdg/compiz/compiz-manager && . /etc/xdg/compiz/compiz-manager
	for f in /etc/xdg/compiz/compiz-manager.d/*; do
		test -e $f && . $f
	done
else
        OLD_IFS=$IFS
        IFS=:
        for CONFIG_DIR in $XDG_CONFIG_DIRS
        do
                test -f $CONFIG_DIR/compiz/compiz-manager && . $CONFIG_DIR/compiz/compiz-manager
		for f in $CONFIG_DIRS/compiz/compiz-manager.d/*; do
                    test -e $f && . $f
		done
        done
        IFS=$OLD_IFS
        unset OLD_IFS
fi

if [ -z "$XDG_CONFIG_HOME" ]; then
	test -f $HOME/.config/compiz/compiz-manager && . $HOME/.config/compiz/compiz-manager
else
	test -f $XDG_CONFIG_HOME/compiz/compiz-manager && .  $XDG_CONFIG_HOME/compiz/compiz-manager
fi

# Don't use compiz when running the failsafe session
if [ "x$GNOME_DESKTOP_SESSION_ID" = "xFailsafe" ]; then
	abort_with_fallback_wm
fi

if [ "x$LIBGL_ALWAYS_INDIRECT" = "x1" ]; then
	INDIRECT="yes";
fi

# if we run under Xgl, we can skip some tests here
if ! check_xgl; then
	# if vesa or vga are in use, do not even try glxinfo (LP#119341)
	if ! running_under_whitelisted_driver || have_blacklisted_pciid; then
		abort_with_fallback_wm
	fi
	# check if we have the required bits to run compiz and if not, 
	# fallback
	if ! check_tfp || ! check_npot_texture || ! check_composite || ! check_texture_size; then
		abort_with_fallback_wm
	fi

	# check if we run with software rasterizer and if so, bail out
	if check_software_rasterizer; then
		verbose "Software rasterizer detected, aborting"
		abort_with_fallback_wm
	fi

	if check_nvidia && ! check_nvidia_memory; then
		abort_with_fallback_wm
	fi

	if ! check_fbconfig; then
		abort_with_fallback_wm
	fi
fi

# load the ccp plugin if present and fallback to plain gconf if not
if [ -f ${PLUGIN_PATH}libccp.so ]; then
	COMPIZ_PLUGINS="$COMPIZ_PLUGINS ccp"
elif [ -f ${PLUGIN_PATH}libgconf.so ]; then
	COMPIZ_PLUGINS="$COMPIZ_PLUGINS glib gconf"
fi

# enable gnomecompat if we run under gnome
if [ x"$GNOME_DESKTOP_SESSION_ID" != x"" ] && [ ! -e ~/.compiz-gnomecompat ]; then 
        verbose "running under gnome seesion, checking for gnomecompat\n"
	if ! gconftool -g /apps/compiz/general/allscreens/options/active_plugins|grep -q gnomecompat; then
	    verbose "adding missing gnomecompat\n"
	    V=$(gconftool -g /apps/compiz/general/allscreens/options/active_plugins|sed s/mousepoll,/mousepoll,gnomecompat,/)
           if ! echo $V|grep -q gnomecompat; then
               verbose "can not add gnomecompat, reseting\n"
               gconftool --unset /apps/compiz/general/allscreens/options/active_plugins
           else
	        gconftool -s /apps/compiz/general/allscreens/options/active_plugins --type list --list-type=string $V
           fi
           touch ~/.compiz-gnomecompat
	fi
fi

# get environment
build_env
build_args

if [ "x$CM_DRY" = "xyes" ]; then
	verbose "Dry run finished: everything should work with regards to Compiz and 3D.\n"
	verbose "Execute: ${COMPIZ_BIN_PATH}${COMPIZ_NAME} $COMPIZ_OPTIONS "$@" $COMPIZ_PLUGINS \n"
	exit 0;
fi

${COMPIZ_BIN_PATH}${COMPIZ_NAME} $COMPIZ_OPTIONS "$@" $COMPIZ_PLUGINS || exec $FALLBACKWM $FALLBACKWM_OPTIONS

```

---

### Post by OffAxis on 2009-07-24
what video card do you have?

---

### Post by steigerjb on 2009-07-24
> **OffAxis said:**
> what video card do you have?

beats me

---

### Post by Ratscallion on 2009-07-24
Go to this part of /usr/bin/compiz
> 
# blacklist based on the pci ids 
# See [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist) for details
#T="   1002:5954 1002:5854 1002:5955" # ati rs480
#T="$T 1002:4153" # ATI Rv350
#T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965
#T="$T 8086:2e02 " # Intel Eaglelake
T="$T 8086:3577 8086:2562 " # Intel 830MG, 845G (LP: #259385)
BLACKLIST_PCIIDS="$T"

And put a # in front of the final line beginning with T="
Might work then?

---

### Post by Ratscallion on 2009-07-24
Try an lspci, paste the result here.

---

### Post by steigerjb on 2009-07-24
putting the # didn't work

> **Ratscallion said:**
> Try an lspci, paste the result here.

here's the result of lspci

```
joe@joe-ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
```

---

### Post by steigerjb on 2009-07-24
if i reinstall compiz, will I lose the extra plugins I compiled?

---

### Post by Ratscallion on 2009-07-24
Urm... Probably.

---

### Post by steigerjb on 2009-07-24
> **Ratscallion said:**
> Urm... Probably.

k, nevermind then

---

### Post by wpshooter on 2009-07-24
> **steigerjb said:**
> putting the # didn't work



here's the result of lspci

```
joe@joe-ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
```

Did you restart the computer ?

---

### Post by steigerjb on 2009-07-24
> **wpshooter said:**
> Did you restart the computer ?

k, just tried restarting. Still get message...desktop effects can not be enabled

:confused:

---

### Post by m_ad on 2009-07-24
Sorry, looked at your lspci wrong :lolflag:

---

### Post by steigerjb on 2009-07-24
> **m_ad said:**
> Have you been running Jaunty for a while? And did your Intel video card work with it? I'm pretty sure Intel video cards are blacklisted under compiz in Jaunty.

I don't think deleting the # sign in front of your video card in compiz will fix your problem.. it's blacklisted for a reason. This is one of the reasons I'm sticking with 8.04.

I've had jaunty since it came out. Desktop effects were working fine til yesterday.

My card is a nvidia something

---

### Post by brookie on 2009-07-24
hi,
do you have a virtual desktop set up, or dual monitors set up in your xorg.conf file? 
i experienced the same thing in the past and lost compiz effects after adding a virtual (extended) desktop. 
see this: [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2")

its an xorg randr wiki stating: 
"Note that the maximum supported size of the virtual desktop for the Intel 945GM series of chipset with 3D acceleration enabled, is 2048x2048. The virtual screen can be larger but DRI will be disabled. This may matter if you like games and compiz desktop effects, or if you want Google Earth to display in better than geological time. Obviously the larger the virtual desktop, the more graphics memory is used. So for good performance with a shared graphics system such as Intel the Virtual should be no larger than necessary."

i need dual monitors with and virtual desktop of 2800 by 1050 and since 2800 > 2048 compiz was disabled automatically by xserver. 

just a thought. 

cheers,
brook 

ps you can list the contents of xorg.conf by typing 
cat /etc/X11/xorg.conf 
into your terminal

---

### Post by steigerjb on 2009-07-24
> **brookie said:**
> hi,
do you have a virtual desktop set up, or dual monitors set up in your xorg.conf file? 
i experienced the same thing in the past and lost compiz effects after adding a virtual (extended) desktop. 
see this: [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2")

its an xorg randr wiki stating: 
"Note that the maximum supported size of the virtual desktop for the Intel 945GM series of chipset with 3D acceleration enabled, is 2048x2048. The virtual screen can be larger but DRI will be disabled. This may matter if you like games and compiz desktop effects, or if you want Google Earth to display in better than geological time. Obviously the larger the virtual desktop, the more graphics memory is used. So for good performance with a shared graphics system such as Intel the Virtual should be no larger than necessary."

i need dual monitors with and virtual desktop of 2800 by 1050 and since 2800 > 2048 compiz was disabled automatically by xserver. 

just a thought. 

cheers,
brook 

ps you can list the contents of xorg.conf by typing 
cat /etc/X11/xorg.conf 
into your terminal

Contents of cat /etc/X11/xorg.conf :
```
joe@joe-ubuntu:~$ cat /etc/X11/xorg.conf 
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

joe@joe-ubuntu:~$ 

```

I did have Karmic Koala installed via VirtualBox. I deleted it yesterday cuz it died when I tried formating it as Ext4.

---

### Post by steigerjb on 2009-07-24
this can't be good:

```
joe@joe-ubuntu:~$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0







```

---

### Post by brookie on 2009-07-24
my idea was off but it was a thought. hopefully someone else here can help figure this out cause there's gotta be an answer.
good luck.

---

### Post by steigerjb on 2009-07-24
> **brookie said:**
> hopefully someone else here can help figure this out 

I sure hope so. I miss desktop effects :sad:

---

### Post by steigerjb on 2009-07-24
anybody????

---

### Post by steigerjb on 2009-07-25
bump :frown:[-o<:sad:

---

### Post by steigerjb on 2009-07-26
> **steigerjb said:**
> bump :frown:[-o<:sad:

anybody????

---

### Post by Ratscallion on 2009-07-26
Make sure Metacity isn't compositing.
gconf-editor -> Apps -> Metacity -> General -> Compositor -> Un-Checked/0/No

---

### Post by steigerjb on 2009-07-26
> **Ratscallion said:**
> Make sure Metacity isn't compositing.
gconf-editor -> Apps -> Metacity -> General -> Compositor -> Un-Checked/0/No

dont see it

---

### Post by steigerjb on 2009-07-26
fyi everyone, I tried:

```
sudo apt-get remove compizconfig-settings-manager
```

and then

```
sudo apt-get install compizconfig-settings-manager
```

still no desktop effects :confused:

---

### Post by overdrank on 2009-07-26
I have briefly read the thread but have you tried reinstalling the nvidia drivers?

---

### Post by steigerjb on 2009-07-26
> **overdrank said:**
> I have briefly read the thread but have you tried reinstalling the nvidia drivers?

if you mean disabling them in hardware drivers, yes.  Someone had recommended disabling them, restarting my computer, then enable them. No luck :(

---

### Post by overdrank on 2009-07-26
Ok I do not have much experience with 
> VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]
But witch driver are you using? are you offered more than one?

---

### Post by Ratscallion on 2009-07-27
> **steigerjb said:**
> if you mean disabling them in hardware drivers, yes.  Someone had recommended disabling them, restarting my computer, then enable them. No luck :(

Disable -> Restart -> Keep them disabled.

As for the gconf thingy, you want to UNCHECK the box you had selected in the screenshot. That should fix it.

---

### Post by steigerjb on 2009-07-27
> **Ratscallion said:**
> As for the gconf thingy, you want to UNCHECK the box you had selected in the screenshot. That should fix it.

Ok, I am confused by the second part

editing: oh i see...the gconf thing. You want me to uncheck compositing_manager ???

you want me to disable my NVIDIA Accelerated graphics driver (version 180) [Recommended] in hardware drivers and not enable them.  Don't I need them enabled to get desktop effects?

---

### Post by steigerjb on 2009-07-27
> **overdrank said:**
> Ok I do not have much experience with 

But witch driver are you using? are you offered more than one?

I am using:

**NVIDIA Accelerated graphics driver (version 180) [Recommended]**


they also have:


NVIDIA Accelerated graphics driver (version 173)

NVIDIA Accelerated graphics driver (version 96)

---

### Post by Ratscallion on 2009-07-27
> **steigerjb said:**
> Ok, I am confused by the second part

editing: oh i see...the gconf thing. You want me to uncheck compositing_manager ???


Yup, disable it. Basically, that tells compiz to let metacity do the compositing. Disable it and metacity will hand the compositing to compiz.

> 
you want me to disable my NVIDIA Accelerated graphics driver (version 180) [Recommended] in hardware drivers and not enable them.  Don't I need them enabled to get desktop effects?

Yup.. I think so.

---

### Post by steigerjb on 2009-07-27
> **Ratscallion said:**
> Yup, disable it. Basically, that tells compiz to let metacity do the compositing. Disable it and metacity will hand the compositing to compiz.



Yup.. I think so.

so do I, or do I not disable my NVIDIA driver?

---

### Post by argos3016 on 2009-07-27
Maybe it was only a crash , you tryied to write compiz in a run dialog? My help is a **** but probably you not do it.

---

### Post by steigerjb on 2009-07-27
> **Ratscallion said:**
> Yup, disable it. Basically, that tells compiz to let metacity do the compositing. Disable it and metacity will hand the compositing to compiz.



Yup.. I think so.

It got my desktop effects working, kinda. As you can see, they are not smooth:

[http://www.youtube.com/watch?v=mImi8hlJWzI]("http://www.youtube.com/watch?v=mImi8hlJWzI")

---

### Post by steigerjb on 2009-07-27
> **Ratscallion said:**
> tells compiz to let metacity do the compositing. Disable it and metacity will hand the compositing to compiz.

do I even have metacity? maybe thats why desktop effects are not smooth?

---

### Post by Ratscallion on 2009-07-27
Metacity is the window manager, and it has a hidden compositor. And yes, disable your driver. If they're choppy, you can try enabling it (reboot after you change it). If that helps, keep it, otherwise, disable it again and reboot.

---

### Post by steigerjb on 2009-07-27
> **Ratscallion said:**
> Metacity is the window manager, and it has a hidden compositor. And yes, disable your driver. If they're choppy, you can try enabling it (reboot after you change it). If that helps, keep it, otherwise, disable it again and reboot.

what happened was, I unchecked that compositer thing, then disabled my driver. Rebooted my computer. Went to appearance=>visual effects=>enabled desktop effect. however, it then reinstalled my driver, giving me what I have now, choppy effects

---

### Post by Ratscallion on 2009-07-27
Ok... You need the drivers enabled. That's sorted that problem out.

---

### Post by steigerjb on 2009-07-27
> **Ratscallion said:**
> Ok... You need the drivers enabled. That's sorted that problem out.

yeah, i know drivers need to be enabled, they are but it is choppy.

---

### Post by steigerjb on 2009-07-27
> **Ratscallion said:**
> Make sure Metacity isn't compositing.
gconf-editor -> Apps -> Metacity -> General -> Compositor -> Un-Checked/0/No

ok, now it's really weird. I rechecked the compositor box.  Still have desktop effects, still choppy.

errr:confused:

I'm gonna cry :lolflag:

---

### Post by Ratscallion on 2009-07-27
Hmm... Strange...

---

### Post by steigerjb on 2009-07-27
> **Ratscallion said:**
> Hmm... Strange...

i'd say

---

### Post by Ratscallion on 2009-07-27
Usually compiz won't composite if metacity is checked...

---

### Post by steigerjb on 2009-07-27
Me = Puzzled

---

### Post by Ratscallion on 2009-07-27
Me = Slightly more puzzled than yourself.

---

### Post by steigerjb on 2009-07-27
> **Ratscallion said:**
> Me = Slightly more puzzled than yourself.

I don't know how were gonna solve this one ](*,)

---

### Post by steigerjb on 2009-07-31
anybody know how to make it perfect again?

---

### Post by Ratscallion on 2009-07-31
Bump!

---

### Post by cgb on 2009-07-31
Have you tried installing the latest nvidia driver manually?  Not entirely sure if it would help but worth a shot.  

[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

---

### Post by steigerjb on 2009-08-01
> **cgb said:**
> Have you tried installing the latest nvidia driver manually?  Not entirely sure if it would help but worth a shot.  

[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

"Note: Follow this instructions at your own risk"

egh :confused:

---

