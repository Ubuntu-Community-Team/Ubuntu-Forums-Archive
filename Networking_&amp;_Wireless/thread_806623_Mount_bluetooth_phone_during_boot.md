---
title: "Mount bluetooth phone during boot"
date: 2008-05-25
forum: Networking &amp; Wireless
---

### Post by sygard on 2008-05-25
Hi everybody!

Last night I had an idea, fairly good one if I may say so. I have two desktop computers and one laptop, all running Linux. I have all my disks encrypted and my two desktop computers load their encryption key file from an usb device during boot. Now, this is not something I'd like to do on my laptop...

I then had my idea, what if I put my keyfile on my SE phone and fetch it wirelessly over bluetooth? After some scripting I got this script to work: (when system is already booted and bluetooth support is loaded into the kernel).
```
#/bin/sh
# this script will mount your bluetooth phone and pass encryption key to cryptsetup
# author Tor Martin [tor at sygard dot net]

KEYFILE=root.key
MAC=00:3E:48:48:05:EF   # phone mac address.
CHANNEL=7               # phone obex file transfer channel
MNTPOINT=/tmp-usb-mount
FILE=$MNTPOINT/Phone*/Other/$KEYFILE

mkdir -p $MNTPOINT
echo "Trying to get key from bluetooth phone..." >&2

timeout 2 obexfs -b $MAC -B $CHANNEL $MNTPOINT >/dev/null 2>&1
OPENED=0
if [ -f $FILE ]; then
	cat $FILE
	sleep 1
	fusermount -u $MNTPOINT 2>/dev/null
	OPENED=1
fi
if [ $OPENED -eq 0 ]; then
	echo "FAILED to find keyfile on phone" >&2
	echo -n "Try to enter your password" >&2
	read -s -r A
	echo -n "$A"
else
	echo "Successfully loaded keyfile from bluetooth phone" >&2
fi

```
Now, obviously this does not work during boot... My guesses are, the right modules aren't loaded when this script is executed. What do I need to modprobe at the beginning of this script to get bluetooth support running???

/Sygard.

---

