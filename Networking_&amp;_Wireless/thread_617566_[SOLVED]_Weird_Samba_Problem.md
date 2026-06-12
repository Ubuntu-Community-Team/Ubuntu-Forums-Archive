---
title: "[SOLVED] Weird Samba Problem"
date: 2007-11-19
forum: Networking &amp; Wireless
---

### Post by chrisinspace on 2007-11-19
I have been using Ubuntu for over a year now, but have never posted before.  I have always been able to research my problem in the forums and find an adequate solution.  This time I have been searching for 2 days and can't find any issues similar to mine.

I recently upgraded from Feisty to Gutsy.  In my Feisty install, I had a shared folder from a Windows server mounted on my Linux box.  To achieve this, I added the following line to my fstab file:

//servername/Media	/media/media smbfs  credentials=/root/.smbcredentials,dmask=777,fmask=777  0    0 

This worked for months with no problem.  Yesterday, I did a clean install of Gutsy and one of the first things I did once things were up and running was to modify my fstab file so I could see files on my server.  I recreated my.smbcredentials file and created the 'media' directory inside of /media.  I then used 'sudo mount -all' and it worked perfectly.  I was able to browse and open files from the shared directory on my server.

The problem began when I rebooted.  I got an error during shutdown about the share not dismounting.  Then when the reboot completed, I tried to browse to my files on the network, but the mounted folder was gone.  Not empty, but completely invisible.  I tried to recreate it, but got a message that it already exists.  So, I viewed the contents of the /media folder in the terminal and it did indeed list it there.

I repeated the process using the the /mnt folder, but the exact some thing happened.  

So, the symptoms are this:

1. When I initally set up the mounted folder, everything works fine.
2. After a reboot, I can't even see the folder anymore through the file manager.  When I select the /media folder, I get an hour glass and eventually my floppy and cdrom folders show up, but the folder I created is not visible.
3. The mount folder can be seen if I view the contents of /media using the 'ls' command from the terminal.
4. I cannot delete the /media/Media directory using the 'rmdir' command. I get an error that tells me the directory is busy

Can anyone help?  This is killing me...

---

### Post by newlinux on 2007-11-19
There may be a probably mounting it at boot for some reason and it is getting stuck. Before trying to mount it maybe try to umount it first, forcefully, and remount:

```
sudo umount -lf /media/media
sudo mount -a
```

otherwise, you probably need to look in your logs to see what is happening. Are you having any problems with any other shares?

Also, I recommend you switch over to using CIFS instead of SMBFS for mounting. 
```

//servername/Media /media/media cifs credentials=/root/.smbcredentials,file_mode=0777,dir_mode=0777 0 0

```
smbfs has been deprecated and for me CIFS works better for me...

---

### Post by jetsam on 2007-11-19
I had a similar, but not identical, problem which turned out to be related to Network Manager not playing nice with my wired connection.  One symptom was that mounts were being left as open connections on my Samba server after I shut down the client machine.  I also had warnings coming up on system shut down.
Try ```
gedit /var/log/syslog
```
Are there a bunch of warnings in your syslog from Network Manager?

---

### Post by chrisinspace on 2007-11-19
Thanks for your responses.

newlinux, I think you are right.  If I comment out the line I added to fstab, then reboot, the folders are visibile again, but empty.  I can then edit the fstab again to make my line active, run 'sudo mount -all' and it works.  So, it must be hanging up during the boot.  I am having this exact same issue with another share on the same server.  I'll try cifs.  

jetsam, I'm only running a wireless card, so my eth0 isn't even enabled.  There could be some issue with the network card, though.  I'm just getting all this stuff set up.  I haven't had a chance to get back on my linux box yet, but I'll check the error log.

---

### Post by dmizer on 2007-11-20
definitely use cifs, but smbfs is not your problem.

you may have to edit your credentials file to meet the requirements for cifs.  for cifs, the credentials should not have a space before or after the equal ( "=" ) sign.

to fix your actual problem, try adding:
```
mount /media/media
```

to the /etc/rc.local file just before the "exit 0" line.

---

### Post by chrisinspace on 2007-11-20
> **dmizer said:**
> definitely use cifs, but smbfs is not your problem.

you may have to edit your credentials file to meet the requirements for cifs.  for cifs, the credentials should not have a space before or after the equal ( "=" ) sign.

to fix your actual problem, try adding:
```
mount /media/media
```

to the /etc/rc.local file just before the "exit 0" line.

Would that be in conjunction with the modified fstab file or in place of it?

I'm not currently using any spaces around the '=' in my credentials file.

---

### Post by chrisinspace on 2007-11-20
So, should the credential file look like this?

```
username=myusername
password=mypassword
```

This is how it looks now.  Is it ok to have the hard return or should that be a space or a tab?

---

### Post by newlinux on 2007-11-20
> **chrisinspace said:**
> So, should the credential file look like this?

```
username=myusername
password=mypassword
```

This is how it looks now.  Is it ok to have the hard return or should that be a space or a tab?

I'd get rid of the hard return just in case. I don't have one in mine. Otherwise this is correct.

And yes, the instructions above (mount in rc.local) are in addition to having an fstab entry. test the fstab entry by itself first  (make sure the device is fully unmounted and then sudo mount -a).

---

### Post by dmizer on 2007-11-20
> **chrisinspace said:**
> So, should the credential file look like this?

```
username=myusername
password=mypassword
```

This is how it looks now.  [...]
that is exactly how your credentials file should look.  the hard return is desirable.

yes, as newlinux indicates, the /etc/rc.local edit would be in addition to editing fstab.

---

### Post by newlinux on 2007-11-20
> **dmizer said:**
> that is exactly how your credentials file should look.  the hard return is desirable.

yes, as newlinux indicates, the /etc/rc.local edit would be in addition to editing fstab.

Not to challenge your assertion, but I am genuinely curious - why is the hard return desirable?

---

### Post by dmizer on 2007-11-20
always good to ask why if you don't know.

from "man mount.cifs"

>        credentials=filename
          specifies a file that contains a username and/or password. The  for&#8208;
          mat of the file is:

                    username=value
                    password=value
          This  is  preferred  over  having passwords in plaintext in a shared
          file, such as /etc/fstab. Be sure to protect  any  credentials  file
          properly.

---

### Post by chrisinspace on 2007-11-20
Thank you all so much!  

I changed smbfs to cifs and edited the /etc/rc.local file.  Everything appears to be working now.

---

