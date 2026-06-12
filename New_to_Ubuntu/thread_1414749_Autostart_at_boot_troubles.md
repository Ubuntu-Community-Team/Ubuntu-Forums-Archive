---
title: "Autostart at boot troubles"
date: 2010-02-24
forum: New to Ubuntu
---

### Post by Name User on 2010-02-24
hi all. i was wondering if somebody more wise and with a bigger mastering of script-fu then me could enlighten me.
having the following problem:
i made this script "autostart.vbox"

```

#!/bin/bash
###################################
### Start-up script for vbox    ###
### by true for =SJ=            ###
###################################
	
################################################################################

# vbox-settings

VBOX_USER="example"
VBOX_USER_PATH="/home/example/"
VBOX_ROOT="/home/example/"

## virtual machine name : testvm

################################################################################
# config ends here
################################################################################

# check user
CURRENTUSER=`id -nu | tr -d "[:blank:]"`
if [ "${CURRENTUSER}" != "${VBOX_USER}" ] ; then
	echo "/bin/sh ${0} ${1}" | su "${VBOX_USER}"
	exit
fi

# action-switch
case "${1}" in
	start)
		echo "Starting virtualbox..."
		HOME="${VBOX_USER_PATH}"
		export HOME
		VBoxHeadless -s testvm >/dev/null 2>&1 </dev/null &
		;;
	stop)
		echo "Saving virtualbox..."
		VBoxManage controlvm testvm savestate 
		;;
	restart)
		echo "Rebooting virtualbox hard..."
		VBoxManage controlvm testvm poweroff
		VBoxManage discardstate testvm
		echo "Starting virtualbox..."
		HOME="${VBOX_USER_PATH}"
		export HOME
		VBoxHeadless -s testvm >/dev/null 2>&1 </dev/null & 
		;;
	poweroff)
		echo "Powering off virtualbox..."
		VBoxManage controlvm testvm poweroff 
		;;
	force-reload)
		echo "Resetting virtualbox hard..."
		VBoxManage controlvm testvm reset
		VBoxManage discardstate testvm 
		killall -9 VBoxHeadless
		VBoxManage discardstate testvm 
		echo "Starting virtualbox..."
		VBoxHeadless -s testvm >/dev/null 2>&1 </dev/null & 
		;;
	*)
		echo "Usage: `basename ${0}` {start|stop|restart|poweroff|force-reload}"
		exit 1
		;;
esac

exit

```

copied it to /etc/init.d
chmod +x autostart.vbox
update-rc.d -f autostart.vbox defaults
problem is it works nice enough if you start it at the CLI as root or any other user. works as expected, runs as user example etc.
but at boot it does not work and i havent figured out why :confused:
it would be really appreciated if somebody could shine some light on this.
oh yeah  i need this because im running a headless server and virtualbox has to start by himself at boot. and it has to be in init.d because i want to save the virtual machine states at shutdown.
oh great gods of F.O.S.S. hear my prayers ;)

---

### Post by Name User on 2010-03-02
Please delete.
Reason : RTFM´d enough.
sorry #-o

---

