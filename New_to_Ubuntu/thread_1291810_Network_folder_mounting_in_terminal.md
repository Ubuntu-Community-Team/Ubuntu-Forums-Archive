---
title: "Network folder mounting in terminal"
date: 2009-10-15
forum: New to Ubuntu
---

### Post by Hygaphunkik on 2009-10-15
First off, when I say I am an absolute beginer I really mean it. I am not sure what half of the stuff I read here actually means.

That being said I have played with a few very simple things in command line and thought that what I am trying to do would be very simple.

If I click on Places > Network > DD-IWB > mini-hal > Pupil Zone 

I can get to the folder I want on a remote pc. However when typing

mount smb://dd-iwb/mini-hal/Pupil%20Zone

I get the following error

mount: can't find smb://dd-iwb/mini-hal/Pupil%20Zone in /etc/fstab or /etc/mtab

So the question is how can I do this in command line, so that I can then write a bash script to mount it automatically on boot?

Remember just pointing me to a tutorial may not be helpful because talk of permissions and mounts and devs are confusing.

---

### Post by tarps87 on 2009-10-15
```

mkdir ~/PupilZone
sudo mount -t smbfs //dd-iwb/mini-hal/Pupil%20Zone ~/PupilZone

```

Note: You may need to use sudo

This makes a directory in you home/user space (~)
mkdir ~/PupilZone

If the above does not work this should

```
sudo apt-get install smbfs smbclient
sudo mkdir /media/PupilZone
sudo smbmount //**dd-iwb**/mini-hal/Pupil%20Zone /home/dbott/music -o username=**username**,password=**passord**
```

This will check if the relevent parts of samba are install and if not it will install them.
Next it will make a directory to mount the share to
Then it will mount it. If you don not have a username or password remove the part -o username=**username**,password=**passord**

This will show if it has mounted
```
ls /media/PupilZone
```

If it still does not work repalce **dd-iwb** with the ip address of the machine which the share is on.

To unmount
```
sudo umount /media/PupilZone
```

Note:
Sudo gives you root (admin) rights.

This command will only work if you have permission to mount the share and it is in the fstab file
mount smb://dd-iwb/mini-hal/Pupil%20Zone ~/PupilZone

This page gives you detailed info on mounting shares including auto mounting the share and adding it to the fstab file.
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

If you need help or a more detail explanation just post back

More notes:
Mounting is basically loading a device so you can use it.
Dev is short of device
Well permission can be complex, from the top level each user has permission to view edit and run their own files but usually can not edit or run other users files. The system file are owned by root.

---

### Post by Hygaphunkik on 2009-10-15
> **tarps87 said:**
> ```

mkdir ~/PupilZone
mount smb://dd-iwb/mini-hal/Pupil%20Zone ~/PupilZone

```

Note: You may need to use sudo

This makes a directory in you home/user space (~)
mkdir ~/PupilZone

If the above does not work this should

```
sudo apt-get install smbfs smbclient
sudo mkdir /media/PupilZone
sudo smbmount //**dd-iwb**/mini-hal/Pupil%20Zone /home/dbott/music -o username=**username**,password=**passord**[code]

This will check if the relevent parts of samba are install and if not it will install them.
Next it will make a directory to mount the share to
Then it will mount it. If you don not have a username or password remove the part username=**username**,password=**passord**

This will show if it has mounted
[code]ls /media/PupilZone
```

If it still does not work repalce **dd-iwb** with the ip address of the machine which the share is on.

To unmount
```
sudo umount /media/PupilZone
```

Note:
Sudo gives you root (admin) rights.

This command will only work if you have permission to mount the share and it is in the fstab file
mount smb://dd-iwb/mini-hal/Pupil%20Zone ~/PupilZone

This page gives you detailed info on mounting shares including auto mounting the share and adding it to the fstab file.
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

If you need help or a more detail explanation just post back

More notes:
Mounting is basically loading a device so you can use it.
Dev is short of device
Well permission can be complex, from the top level each user has permission to view edit and run their own files but usually can not edit or run other users files. The system file are owned by root.

Thanks very much for taking the time to help.

I tried going through what was said here and looked at that link ( I think I might have understood about 10% of it) but I still cannot get the thing to mount through terminal. I have no problem doing it through the GUI but that does not stick, so it is not mounted when I reboot, hence the fact that I want to be able to write a script that I can tell startup manager to look at.

Anyhow I managed to get a list of errors which I don't fully understand, perhaps I should clarify. The script must be installed on a load of machines so that they can all access the same files. 

Oh yeah that list of errors and the few commands I followed.

```
fosil@Fad_GrpYr3:~$ sudo mkdir /media/PupilZone
fosil@Fad_GrpYr3:~$ sudo smbmount //dd-iwb/mini-hal/Pupil%20Zone /home/dbott/music -o
fosil@Fad_GrpYr3:~$ ls /media/PupilZone
fosil@Fad_GrpYr3:~$ mount smb://dd-iwb/mini-hal/Pupil%20Zone ~/PupilZone
mount: only root can do that
fosil@Fad_GrpYr3:~$ sudo mount smb://dd-iwb/mini-hal/Pupil%20Z0ne ~/PupilZone
mount: wrong fs type, bad option, bad superblock on smb://dd-iwb/mini-hal/Pupil%20Z0ne,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

fosil@Fad_GrpYr3:~$ dmesg | tail
[ 7112.382212] end_request: I/O error, dev sr0, sector 11764968
[ 7112.412085] end_request: I/O error, dev sr0, sector 11764968
[ 7112.457231] end_request: I/O error, dev sr0, sector 11764968
[ 7112.492298] end_request: I/O error, dev sr0, sector 11764968
[ 7112.516578] end_request: I/O error, dev sr0, sector 11764968
[ 7112.558664] end_request: I/O error, dev sr0, sector 11764968
[ 7112.607153] end_request: I/O error, dev sr0, sector 11764968
[ 7112.874791] end_request: I/O error, dev sr0, sector 11764968
[ 9510.450964] RPC: Registered udp transport module.
[ 9510.450968] RPC: Registered tcp transport module.
fosil@Fad_GrpYr3:~$ 

```

---

### Post by tarps87 on 2009-10-15
What response did you get from these two commands?

sudo smbmount //dd-iwb/mini-hal/Pupil%20Zone /home/dbott/music -o
ls /media/PupilZone

Sorry made a mistake with the first set of commands it should be

```

mkdir ~/PupilZone
sudo mount -t cifs //dd-iwb/mini-hal/Pupil%20Zone ~/PupilZone

```
(-t = type)
If this fails try
```
sudo mount -t smbfs //dd-iwb/mini-hal/Pupil%20Zone ~/PupilZone
```
If this does work replace cifs with smbfs below

If you can use the mount -t smbfs command to mount the share you will not need a script to load it instead you can add it to the fstab file, this file contains all the drives/shares to mount on boot.

More documentation :)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Don't worry you usually only need to understand a little about what is said

The important bit in this documentation is

> 
# Samba
//server/share  /media/samba  cifs  user=user,uid=1000,gid=100  0  0
# "Server" = Samba server (by IP or name if you have an entry for the server in your hosts file
# "share" = name of the shared directory
# "user" = your samba user
# This set up will ask for a password when mounting the samba share. If you do not want to enter a password, use a credentials file.
# replace "user=user" with "credentials=/etc/samba/credentials" In the credentials file put two lines
# username=user
# password=password
# make the file owned by root and ro by root (sudo chown root.root /etc/samba/credentials && sudo chmod 400 /etc/samba/credentials)


If you don't use a username or password all you need is this bit
//dd-iwb/mini-hal/Pupil%20Zone  **/media/PupilZone**  cifs uid=1000,gid=100  0  0

cifs is supost to be a replacment for smbfs.

To edit the fstab file

```
sudo gedit /etc/fstab
```

Note: dd-iwb may need replacing with the ip
You can also change where you want to mount it **/media/PupilZone**
Don't use ~ in the fstab file as it is run as root and will atempt to mount it in root home folder which doesn't exist in Ubuntu

I have a feeling some of this won't make sense so please post back and I will try to explain that part better.

---

### Post by Hygaphunkik on 2009-10-15
Thanks for the help. I am back at home now, so I will try this on the work machine I am working on tommorrow. I will make sure I let you know what happens, I think I am slowly starting to get this and I guess it will be clearer when I can see it in action.

Off to play at customizing a log in window now.

---

### Post by Hygaphunkik on 2009-10-16
Tarps 87 thanks so much

I am getting so close I can almost taste it. Just need to find the IP address and then I think I am there

This command:
sudo mount -t cifs //dd-iwb/mini-hal/Pupil%20Zone ~/PupilZone

Gave this error:
mount error: could not resolve address for dd-iwb: No address associated with hostname
No ip address specified and hostname not found


So as soon as I get the IP address I will try using that instead of dd-iwb


Thanks again.

---

### Post by tarps87 on 2009-10-16
As long as the ip is fixed you can then add it to the fstab file which will auto mount it for you.
Can you lest us know how it goes

---

