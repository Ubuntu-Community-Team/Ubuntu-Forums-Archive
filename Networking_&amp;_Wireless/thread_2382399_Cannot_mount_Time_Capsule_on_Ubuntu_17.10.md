---
title: "Cannot mount Time Capsule on Ubuntu 17.10"
date: 2018-01-12
forum: Networking &amp; Wireless
---

### Post by nadaeck on 2018-01-12
Hello

This is not new. I cannot access our Time Capsule. Nothing works, neither in Nautilus or in command line.

I've searched extensively, found several documented posts, including [https://ubuntuforums.org/showthread.php?t=2333119&highlight=time+capsule](https://ubuntuforums.org/showthread.php?t=2333119&highlight=time+capsule), and [https://askubuntu.com/questions/524328/ubuntu-14-04-how-to-connect-to-apples-time-capsule](https://askubuntu.com/questions/524328/ubuntu-14-04-how-to-connect-to-apples-time-capsule), and I couldn't have anything working.

Here are the result of many tries...

                        [I]sudo mount.cifs vers=1.0 "//Time_Capsule_de_Anesthesie/Time_Capsule_Anesthesie" /mnt/ -o password=PASSWORD,file_mode=0777,dir_mode=0777,sec=ntlm
[/I]
[I]Couldn't chdir to //Time_Capsule_de_Anesthesie/Time_Capsule_Anesthesie: No such file or directory
[/I]
*sudo mount.cifs "//Time_Capsule_de_Anesthesie/Time_Capsule_Anesthesie" /mnt/ -o password=PASSWORD,file_mode=0777,dir_mode=0777,sec=ntlm*
[I]mount error: could not resolve address for Time_Capsule_de_Anesthesie: Unknown error
[/I]
* sudo mount.cifs vers=2.0 "//Time_Capsule_de_Anesthesie/Time_Capsule_Anesthesie" /mnt/ -o password=PASSWORD,file_mode=0777,dir_mode=0777,sec=ntlm,uid=victor*
*Couldn't chdir to //Time_Capsule_de_Anesthesie/Time_Capsule_Anesthesie: No such file or directory*

*sudo mount -t cifs //10.102.1.91/Data -o username=macbook,passwd=PASSWORD,sec=ntlm /mnt*
*Password for macbook@//10.102.1.91/Data:  ***********
*mount error(22): Invalid argument*
[I]Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
[/I]
*sudo mount -t cifs //10.102.1.91/Data -o username=macbook,passwd=PASSWORD,sec=ntlm*
*[sudo] password for victor:  *
[I]mount: //10.102.1.91/Data: can't find in /etc/fstab.
[/I]
*sudo mount -t cifs //10.102.1.91/Data -o username=macbook,passwd=PASSWORD,sec=ntlm /mnt*
*Password for macbook@//10.102.1.91/Data:  ***********
*mount error(22): Invalid argument*
*Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)*

*sudo mount.cifs vers=1.0 //10.102.1.91/Data /mnt/ -o password=PASSWORD,file_mode=0777,dir_mode=0777,sec=ntlm*
[I]Couldn't chdir to //10.102.1.91/Data: No such file or directory
[/I]
*sudo mount.cifs vers=1.0 //10.102.1.91/Time_Capsule_Anesthesie /mnt/ -o password=PASSWORD,file_mode=0777,dir_mode=0777,sec=ntlm*
[I]Couldn't chdir to //10.102.1.91/Time_Capsule_Anesthesie: No such file or directory
[/I]
A few comments : 
 - I'm not sure about the usernam : "macbook" seems to be the default one on my Apple system; is it necessary?
 - 10.102.1.91 is the IPV4 address of the time Capsule (named "Time Capsule de Anesthesie") and "Time_Capsule_Anesthesie" seems to be the root directory on the Time Capsule - PASSWORD is replaced by the actual password

Nothing I have found actually works.

Is there something I can try please?

Victor

---

### Post by Wi11iwaw on 2018-01-20
Victor,
I'm not an expert and it took me some time, but I did get it to work using "[HOW TO AUTOMATICALLY MOUNT AND UMOUNT APPLE TIME CAPSULE ON LINUX]("https://ineed.coffee/418/how-to-automatically-mount-and-umount-apple-time-capsule-on-linux/")" on 16.04 LTS. From your first couple of examples it looks like you're not downloading the script, or that you are calling it incorrectly?  I started off by going to *Computer>>usr>>local>>bin* and then right clicking (not sure how you do that on your Mac) and selecting *Open in Terminal*.  In the terminal I immediately *Sudo* for privileges and then I followed the tutorial that's linked above.  Also, read the comments on that tutorial because their are some good pointers and one that I think maybe(?) critical where you need to add *vers=1.0 *toward the end of the script. It seemed to help me anyway.

---

