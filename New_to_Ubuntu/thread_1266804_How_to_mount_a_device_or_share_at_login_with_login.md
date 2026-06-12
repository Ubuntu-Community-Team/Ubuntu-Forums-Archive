---
title: "How to mount a device or share at login with login script"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by Jaapmans on 2009-09-15
Hi,

On my ASROCK 330 system I installed Ubuntu 9.04 (full desktop).

Due to the relative slow hardware of the machine, I want to mount shares or devices only when I log in, so after the system has fully booted.

I have searched several forums but can't find a working solution.

Currently I have the following lines in my .profile file in my home directory:

```

if grep "/media/mediafiles" /etc/mtab > /dev/null 2?&1; then
  mount --rbind /media/mediafiles $HOME/Mediafiles
  echo "mounted"
else
  echo "not mounted"
fi

```It seems that this part of the script doesn't work, I guess because mount doesn't work for a normal user without root priviliges.

Does anyone in here has a suggestion on how to mount a share or device on login in the form of a login script?

Thanks in advance.

---

### Post by blackened on 2009-09-15
Try using chown on the mountpoint.

```
sudo chown -R *username:username* /media/mediafiles
```

Then try your script again.

Whereas you could accomplish the same think by mounting it in a subdirectory of ~.

---

### Post by K7522 on 2009-09-15
Here is the function that I use at login for mounting my drive.

The full code is here: [http://ubuntuforums.org/showthread.php?p=7939780#post7939780](http://ubuntuforums.org/showthread.php?p=7939780#post7939780)

You will need to add those variables to the top of your script, and call the function at the bottom.
```

export mountDir="/media/DATA" # The location of where you want to mount the partition.
export mountPar="/dev/sdb1" # The name of the partition.
export mountPartitionType="ntfs" # The type of filesystem of the partition.
export LOG_FILE="~/Scripts/startup.log" # The location of your log file.

```

```
function mount {
## First we check if the drive is mounted.
 if [ $(mount | grep -c $mountDir) != 1 ]
 then
 	echo "$mountDir is not mounted." >> $logFile
 	## If it is not mounted, check if the folder exists.
 	if [ ! -x $mountDir ];
 		then
 			## The folder does not exist, create it.
 			echo "$mountDir folder does not exist. Creating." >> $logFile
 			echo $password | sudo -S mkdir $mountDir
 		else
 			## The folder exists, move on.
 			echo "$mountDir folder exists." >> $logFile
 	fi
 	## Mount the drive to the folder.
 	echo $password | sudo -S mount -t $mountPartitionType $mountPar $mountDir
 else
 	echo "$mountDir is mounted." >> $logFile
 fi
}
```

---

