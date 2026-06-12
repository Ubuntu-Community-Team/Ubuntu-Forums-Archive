---
title: "Simulating reconnection USB hard-disk's plug with Linux commands ?"
date: 2010-10-23
forum: New to Ubuntu
---

### Post by ronbarak on 2010-10-23
Hi,

[COLOR="Blue"]Is there a way to simulate in software (e.g., from bash prompt) a USB hard-disk disconnection/reconnection ? [/COLOR]
What I mean by disconnection is pulling the USB plug off the computer, where reconnection is plugging the USB plug back again.

_Why I'm asking_:
On my Ubuntu 10.04 laptop I have an external USB hard-disk formatted with NTFS.
From time to time this disk would become spontaneously unmounted.

I wrote a hack script (below) that I run once this happens, I then physically disconnect/reconnect the USB disk, and run the script again. This usually works and the NTFS disk is mounted correctly again.

However, I'd like to add commands for disconnecting/reconnecting the USB NTFS disk to the script so that the whole process could be automated.

So, to iterate, do you know how to simulate reconnecting a USB hard disk plug with Linux commands ?

Thanks,
Ron.  

Note, the below is an ugly hack, and is still a work in progress that is being continuously optimized as new insights occur:

[FONT="Courier New"]#!/usr/bin/env bash

sync

pid="`ps -ef | grep amule | grep -v grep | awk '{ print $2 }'`"
while [ $pid ]; do
	echo "amule \$pid to kill is:" \"$pid\"
	kill -1 $pid
	pid=`ps -ef | grep amule | grep -v grep | awk '{ print $2 }'`
done

kill `ps -ef | grep '/media/931 GB' | grep -vE 'grep' | awk '{ print $2 }'`

procs_still_accessing_disk=`ps -ef | grep '/media/931 GB' | grep -vE 'grep' | awk '{ print $2 }'`
echo "\$procs_still_accessing_disk:" $procs_still_accessing_disk
if [ ! -n  $procs_still_accessing_disk ]; then
	while [ $procs_still_accessing_disk ]; do
		for p in $procs_still_accessing_disk; do
			kill -1 $p
		done
		#procs_still_accessing_disk=`ps -ef | grep '/media/931 GB' | grep -vE 'grep|mount.ntfs' | awk '{ print $2 }'`
		procs_still_accessing_disk=`ps -ef | grep '/media/931 GB' | grep -vE 'grep' | awk '{ print $2 }'`
	done
fi

ntfs_procs_still_accessing_disk=`ps -ef | grep '/media/931 GB' | grep 'mount.ntfs' | awk '{ print $2 }'`
echo "\$ntfs_procs_still_accessing_disk:" $ntfs_procs_still_accessing_disk
if [ ! -n  $ntfs_procs_still_accessing_disk ]; then
	while [ $ntfs_procs_still_accessing_disk ]; do
		for p in $ntfs_procs_still_accessing_disk; do
			kill -1 $p
		done
		ntfs_procs_still_accessing_disk=`ps -ef | grep '/media/931 GB' | grep -vE 'grep|mount.ntfs' | awk '{ print $2 }'`
	done
fi

disk_dev=`df | grep '/media/931\ GB' | awk '{ print $1 }'`
while [ $disk_dev ]; do
	echo "\$disk_dev to umount is:" \"$disk_dev\"
	umount $disk_dev
	disk_dev=`df | grep '/media/931\ GB' | awk '{ print $1 }'`
done

echo "========================"
echo "disconnect and reconnect disk"
echo "========================"

rw,nosuid,nodev,allow_other"
ls /dev/sdc1 > /dev/null 2>&1
if [ $? = 0 ]; then
        mount /dev/sdc1 /media/931\ GB -t ntfs -o rw,nosuid,nodev,allow_other
        #echo "sdc1: Exit status:" $?	
else
	mount /dev/sdd1 /media/931\ GB -t ntfs -o rw,nosuid,nodev,allow_other
	mount /dev/sde1 /media/931\ GB -t ntfs -o rw,nosuid,nodev,allow_other
fi[/FONT]

---

### Post by mikewhatever on 2010-10-23
For disconnecting, you could use the following:

```
udisks --detach /dev/sdX
```

...not sure how to simulate the connection.

---

### Post by ronbarak on 2010-10-23
> **mikewhatever said:**
> For disconnecting, you could use the following:

```
udisks --detach /dev/sdX
```

...not sure how to simulate the connection.

Thanks for the detach idea, Mike. I'll try and use it, and see if it enhances my script.
I still need to find the detach inverse...  <sigh>

---

