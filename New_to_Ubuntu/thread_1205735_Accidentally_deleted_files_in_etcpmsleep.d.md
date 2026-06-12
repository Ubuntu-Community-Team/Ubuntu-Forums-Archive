---
title: "Accidentally deleted files in /etc/pm/sleep.d"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by nealh149 on 2009-07-06
Title says it all...I feel stupid.

Anyway, I deleted files 99laptop-mode and action_wpa.  Are these important, and if so, how can I replace them?

Thank you.

---

### Post by lavinog on 2009-07-06
Is this on a laptop or desktop?
laptop-mode is mainly for power saving features of laptops. I don't think it is needed for desktops

action_wpa is for wireless, if you don't have wireless you should be fine
if you would like to replace them:
99laptop-mode:
```

#!/bin/sh
#
# 99laptop-mode: Re-apply laptop mode tools settings

case "$1" in
	hibernate|suspend)
		# Stopping is not required.
		;;
	thaw|resume)
		# Make laptop mode tools forcibly re-apply the hardware settings
		# that laptop mode tools applies.			
		if [ -e /usr/sbin/laptop_mode ] ; then
			/usr/sbin/laptop_mode auto force
		fi
		;;
	*) exit $NA
		;;
esac

```

action_wpa:
```

#!/bin/sh

# Action script to enable/disable wpa-roam interfaces in reaction to
# pm-action or ifplugd events.
#
# Copyright: Copyright (c) 2008, Kel Modderman <kel@otaku42.de>
# License:   GPL-2
#

PATH=/sbin:/usr/sbin:/bin:/usr/bin

if [ ! -x /sbin/wpa_action ]; then
	exit 0
fi

SELF=action_wpa
COMMAND=
IFPLUGD_IFACE=

# pm-action(8) - <action> <suspend method>
#
# On suspend|hibernate, disconnect any wpa-roam managed interfaces,
# reconnect it on resume.

case "${1}" in
        suspend|hibernate)
                COMMAND=disconnect
                ;;
        resume|thaw)
                COMMAND=reconnect
                ;;
esac

if [ -z "$COMMAND" ]; then
	# ifplugd(8) - <iface> <action>
	#
	# If an ifplugd managed interface is brought up, disconnect any
	# wpa-roam managed interfaces so that only one "roaming" interface
	# remains active on the system.

	IFPLUGD_IFACE="${1}"

	case "${2}" in
		up)
			COMMAND=disconnect
			;;
		down)
			COMMAND=reconnect
			;;
		*)
			echo "${SELF}: unknown $0 arguments: ${@}" >&2
			exit 1
			;;
        esac
fi

if [ -z "$COMMAND" ]; then
	echo "${SELF}: unknown arguments: ${@}" >&2
	exit 1
fi

for CTRL in /var/run/wpa_supplicant/*; do
	[ -S "${CTRL}" ] || continue

	IFACE="${CTRL#/var/run/wpa_supplicant/}"

	wpa_action "${IFACE}" check || continue

	if [ "${IFPLUGD_IFACE}" ] && [ "${IFPLUGD_IFACE}" = "${IFACE}" ]; then
		# if ifplugd is managing this interface (not likely but..)
		# do nothing
		continue
	fi

	wpa_cli -i "${IFACE}" "${COMMAND}"
done

```
to replace them
alt-f2
```

gksudo gedit /etc/pm/sleep.d/99laptop-mode /etc/pm/sleep.d/action_wpa

```
copy and past the above code into the respective file
and save each

---

### Post by nealh149 on 2009-07-06
Thank you, I have a laptop and use wireless so I definitely needed these.

One more question though...Do you know what permissions these files should be given and for what groups?

---

### Post by nothingspecial on 2009-07-06
```
ls -l /etc/pm/sleep.d
total 4
-rwxr-xr-x 1 root root 366 2009-03-30 09:37 99laptop-mode
lrwxrwxrwx 1 root root  34 2009-05-17 14:41 action_wpa -> ../../wpa_supplicant/action_wpa.sh
```

---

### Post by nealh149 on 2009-07-06
Thanks, all set now.

---

