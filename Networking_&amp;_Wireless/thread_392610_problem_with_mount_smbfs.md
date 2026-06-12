---
title: "problem with mount smbfs"
date: 2007-03-24
forum: Networking &amp; Wireless
---

### Post by mystic-d on 2007-03-24
hey all !
i tryed to use this command to mount a folder from windows (sharing) :
"sudo mount -t smbfs -o username,ip=x.x.x.x //x.x.x.x/foldername /mnt/share"
and i got this messege at the syslog:
"smbfs: mount_data version 1919251317 is not supported"

maybe someone know what is the problem and how can i fix it ?
thanks !

---

### Post by dolphin_oracle on 2007-03-24
if its just a windows share try this

sudo mount -t smbfs -o username=USERNAME //x.x.x.x/foldername /mnt/share

you may also need to specify a password 


sudo mount -t smbfs -o username=USERNAME password=PASSWORD //x.x.x.x/foldername /mnt/share

---

### Post by mystic-d on 2007-03-25
no its not working.. the same error inside dmesg..
and i got this error at the regular consule :
"mount: wrong fs type ,bad option, bad superblock on //x.x.x.x/foldername,
missing codepage or other error"

any one know what is the problem ?

---

### Post by HereInOz on 2007-03-25
You need to install the package smbfs.

You will find it in Synaptic.  Install this and it all should come together, provided everything else is right.  Nothing will work with what you are trying to do without smbfs installed on your Linux machine.

---

### Post by mystic-d on 2007-03-26
i dont have the packege smbfs in my synaptic , how can i installed it anyway ?
(i also tryed: "sudo apt-get install smbfs" but it didnt work... its tell that it cant find the packege.. how can i tell apt-get to serach at the internet and not in the cd-rom source) ?
thanks !

---

### Post by mystic-d on 2007-03-27
can someone help me plz ?  its urgent...
thanks !

---

### Post by notwen on 2007-03-27
I'm still trying to get smbfs working for me, but I've been using the how-to located [here]("http://www.ubuntuforums.org/showthread.php?t=288534").  Hope this helps. =]

---

### Post by mystic-d on 2007-03-27
i sorry but its not work coz i cant installed the smbfs (like i said before)..
maybe someone know how can i download the smbfs packege from the internet and not from the cd source ? (apt-get install smbfs not working..)
thanks !

---

### Post by mystic-d on 2007-03-27
someone ?? plz its urgent...

---

### Post by mssever on 2007-04-05
> **mystic-d said:**
> i sorry but its not work coz i cant installed the smbfs (like i said before)..
maybe someone know how can i download the smbfs packege from the internet and not from the cd source ? (apt-get install smbfs not working..)
thanks !

I came across this thread while I was searching for something else. I don't know if I'm too late, but here goes.

Open up Synaptic and go to the Setings menu > Repositories. On the Ubuntu 6.10 tab (assuming that's the version you're using), make sure that the first four checkboxes are checked. At the minimum, you need the main repository (in parentheses after the verbose descriptions). Close the dialog and hit Synaptic's reload button. Now, you should be able to search for smbfs.

EDIT: You might also be interested in this: [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by mystic-d on 2007-04-10
i just want to say that now everything is working,  so alot of thanks !!!!!!!!!!!!
and again thanks !! :)

---

### Post by HeyItsMatt on 2007-04-10
> **dolphin_oracle said:**
> if its just a windows share try this

sudo mount -t smbfs -o username=USERNAME //x.x.x.x/foldername /mnt/share

you may also need to specify a password 


sudo mount -t smbfs -o username=USERNAME password=PASSWORD //x.x.x.x/foldername /mnt/share

Hey, I just wanted to ask, is USERNAME the Windows username (and likewise for PASSWORD)?  Is "//x.x.x.x/foldername" the IP address and shared folder of the Windows computer/folder?  and is "/mnt/share" the location where I am mounting the Windows XP shared folder to?  Could I specify any location here if I wanted?

Lastly, is this a permanent thing, that will last through restarts?

---

### Post by jdmpike on 2007-04-10
I am currently running Feisty, so this may be the wrong thread for this, but when I try to mount my smbfs share, I get the following:

```

jordan@luckyone:~$ sudo mount -t smbfs -o username=myuser,password=mypass //luckyseven/garage1 /media/garage1
Could not resolve mount point /media/garage1

```

I just tried to do an ls -l on /media and it took a minute or two before coming back with this...

```

jordan@luckyone:~$ ls -l /media/
total 12
lrwxrwxrwx 1 root root    6 2007-04-01 17:48 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2007-04-01 17:48 cdrom0
drwxr-xr-x 2 root root 4096 2007-04-01 17:48 cdrom1
lrwxrwxrwx 1 root root    7 2007-04-01 17:48 floppy -> floppy0
drwxr-xr-x 2 root root 4096 2007-04-01 17:48 floppy0
?--------- ? ?    ?       ?                ? /media/garage1

```

When I tried to remove the mount point with sudo rm -r /media/garage1 it said:

```

jordan@luckyone:~$ sudo rm -r /media/garage1
rm: cannot lstat `/media/garage1': Input/output error

```

Any help getting back to my media share would be a great help!

Thanks,

jdmpike

---

### Post by mssever on 2007-04-11
> **HeyItsMatt said:**
> Hey, I just wanted to ask, is USERNAME the Windows username (and likewise for PASSWORD)?  Is "//x.x.x.x/foldername" the IP address and shared folder of the Windows computer/folder?  and is "/mnt/share" the location where I am mounting the Windows XP shared folder to?  Could I specify any location here if I wanted?

Lastly, is this a permanent thing, that will last through restarts?To make a mount survive between reboots, you need to edit /etc/fstab. See [this howto]("http://ubuntuforums.org/showthread.php?t=283131") for more. You can mount a partition to any empty directory as long as it exists.

---

