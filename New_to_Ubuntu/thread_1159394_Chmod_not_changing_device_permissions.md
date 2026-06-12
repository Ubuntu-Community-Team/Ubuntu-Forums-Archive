---
title: "Chmod not changing device permissions"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by radiocognition on 2009-05-14
Hey Everyone:

I am setting up an astronomy camera on a system that runs Ubuntu Linux.  I have all of the drivers and firmware successfully compiled and installed.  The device management is handled through the udev daemon - so that every time the camera's usb cable is plugged into the machine, udev automatically runs a script to load the drivers.

My problem is with the script that udev executes to set the device up.  The script is supposed to simultaneously upload the drivers and change the permissions of the device so that any user can operate it.  Here is the script that I wrote.
```

#!/bin/bash                                                                                                      

# Name:     sbig_init_permission.sh                                                                              
# Version:  1.0                                                                                                  

# Author:   True Merrill (true.merrill@gatech.edu)                                                               
#     Copyright (C) 2009 True Merrill                                                                            
#     Georgia Institute of Technology                                                                            
#     Released under the terms of GPLv3 or later                                                                 

# Synopsis: Simple shell script to give SBIG ST-3200ME camera correct permissions                                

# History:                                                                                                       
# 2009-05-13   Initial release                                                                                   

DEVICE_NAME=$1
/sbin/fxload -I /lib/firmware/sbigfcam.hex -D $DEVICE_NAME -t fx2

BUS_NUMBER=$2
DEV_NUMBER=$[$3+1]
# Append on zeros to make strings the correct length                                                             
if [[ ${#BUS_NUMBER} == 1 ]]; then
   BUS_NUMBER="00"$BUS_NUMBER
elif [[ ${#BUS_NUMBER} == 2 ]]; then
   BUS_NUMBER="0"$BUS_NUMBER
fi
if [[ ${#DEV_NUMBER} == 1 ]]; then
   DEV_NUMBER="00"$DEV_NUMBER
elif [[ ${#DEV_NUMBER} == 2 ]]; then
   DEV_NUMBER="0"$DEV_NUMBER
fi

sudo /bin/chmod 666 /dev/bus/usb/$BUS_NUMBER/$DEV_NUMBER

```

Here is the relevant piece of the /etc/udev/rules.d/ file that runs the script:
```

ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0d97", ATTR{idProduct}=="0003", \
RUN+="/usr/local/bin/sbig_init_permission.sh $env{DEVNAME} $attr{busnum} $attr{devnum}"
```

The script automatically runs when the device is plugged in (udev is working) and successfully loads the drivers using fxload.  The rest of the script takes the bus number and device number and uses it to change the permissions of the device.  The script correctly formats the chmod command (I saved the output to text while I was debugging) but for some reason the permissions are not changed! However, when I run the command on my own, the permissions are changed (I have to have root access to do this).

I need this to execute automatically without requiring root access.  I've tried everything I could - including changing the permissions on the script so that it always executes as root
```
chown root scriptname.sh
chmod 4755 scriptname.sh
```
with no success.  Any ideas?

---

### Post by GMachine_24 on 2009-05-14
Hi:

I'm no good at code, however . . . are you sure this line is correct?

```


sudo /bin/chmod 666 /dev/bus/usb/$BUS_NUMBER/$DEV_NUMBER


```

Whenever I've used 'chmod' the command has been 

```


sudo chmod 777 /name of directory_or_device/you want to change permissions


```

Perhaps it's my ignorance - is sudo /bin/chmod an executable command -- perhaps it should be


```


usr/bin/sudo /bin/chmod 666 /dev/bus/usb/$BUS_NUMBER/$DEV_NUMBER


```



GM

---

### Post by radiocognition on 2009-05-14
chmod 777 gives executable permissions to the file to all users.  This is a device (I can't execute it) - so I just want to give read / write permissions (hence chmod 666).

When I execute chmod 666 /dev/bus/usb/$BUS_NUMBER/$DEV_NUMBER manually, the permissions apply correctly

---

### Post by GMachine_24 on 2009-05-14
Right, I understood that you can execute your chmod command in a terminal. I was just asking if 

```


sudo /bin/chmod 666 /dev/bus/usb/$BUS_NUMBER/$DEV_NUMBER


```

is correct or if it should be 

```


usr/bin/sudo /bin/chmod 666 /dev/bus/usb/$BUS_NUMBER/$DEV_NUMBER


```

in your script as I did some research and this seems to be the command structure others use.

In other words, instead of starting with "sudo" you begin with "usr/bin/sudo" and the rest is the same.

--GM

---

### Post by radiocognition on 2009-05-15
Has anyone ever seen this kind of problem where they write a script using chmod and it doesn't successfully apply the permissions?

---

### Post by GMachine_24 on 2009-05-15
Perhaps this will help:

[http://ubuntuforums.org/showpost.php?p=3768173&postcount=7](http://ubuntuforums.org/showpost.php?p=3768173&postcount=7)

---

### Post by radiocognition on 2009-05-15
Well, I worked a hack around using sudo, although I am not particularly happy with the result from a security standpoint.  Thanks for the link

---

### Post by GMachine_24 on 2009-05-18
Sorry I couldn't be of more help. I looked for a long time as I wanted the answer to this problem, too.

I was thinking: Your question is fairly advanced, so you might want to post it in one of the other forums (i.e. not the beginner forum).

Hope it works out.

gm

---

### Post by theDaveTheRave on 2009-05-19
> **radiocognition said:**
> chmod 777 gives executable permissions to the file to all users.  This is a device (I can't execute it) - so I just want to give read / write permissions (hence chmod 666).

When I execute chmod 666 /dev/bus/usb/$BUS_NUMBER/$DEV_NUMBER manually, the permissions apply correctly

it is probably a daft observation but I'm going to make it anyway :p

is the script you are running definately working with root permisions?
ensure that is it owned by root:root

I only really ask this as I have a script that didn't work unless I ran it  under <sudo ./doThis.sh>, and it took me a while to drop to the reason for the failure, when the rest of the script was working appart from one line!

a good way to check, is get it too write something to a drive that only root has access too, if that works then it is running as root.

hope that helps, or at least may reduce the possibilities by 1 ):P

David

---

