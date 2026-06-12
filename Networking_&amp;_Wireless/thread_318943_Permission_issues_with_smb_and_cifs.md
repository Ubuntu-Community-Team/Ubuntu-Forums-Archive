---
title: "Permission issues with smb and cifs"
date: 2006-12-14
forum: Networking &amp; Wireless
---

### Post by LadFromWales85 on 2006-12-14
Hello all,

Have been using smbfs to mount my windows shares for the past few weeks, with no problems, except from having change permission errors while copying/moving some files to the shares (the shares are on a windows machine).  The files still copied/moved none the less.

Having read about how amazing cifs is compared to smbfs, I decided to give it a try.

Followed the guide at [http://www.ubuntuforums.org/showthread.php?t=288534](http://www.ubuntuforums.org/showthread.php?t=288534) and ended up with access to my shares on the machine.  The username in .smbcredentials has 'full access' to the shares on that PC.

Now with the shares mounted with cifs instead of smbfs, I am having problems copying folders and files to the shares.  If I attempt to do it from the commandline, the cp tool tells me that it is omitting the directory.  Through Konqueror it creates the initial directory, then falls over with "Access Denied to /media/spC/.... (the mountpoint /media/spC is the destination of where the files are headed)

Here is my line for the above share in fstab:
//SHAUNSPOOTA/shaunspoota_c  /media/spC  cifs  credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777  0  0

The share mounts and unmounts fine, and I appear to be able to read from it fine, but I cannot write.  Single files will transfer fine, though Konqueror will inform me that it cannot change the permissions.

Anyone have any ideas?  Accessing samba shares seems to be a nightmare in Linux, but it's probably just me doing something blatently wrong!

Any help will be appreciated and pats on backs issued :mrgreen:

---

### Post by dmizer on 2006-12-15
for some reason some people are experiencing this problem.  the file_mode and dir_mode switches should arrange for the correct permissions, but for some people it's not working correctly.

to fix this, unmount the share, and change the /media/spC folder to 777 permissions:
```
sudo chmod 777 /media/spC
```
remount, and all should be well.

this is because the permissions issue is not on the remote computer, the permissions problem is in the local /media folder.

---

### Post by cracker on 2006-12-15
As for cp "Omitting Directory:", you must use the -r switch to copy recursively (include directories, subdirectories, and contained files).

---

### Post by LadFromWales85 on 2006-12-15
dmizer...yeah I chmod'ed the directory to 777, which didn't solve the issues :(

I ended up putting my UID and GID in fstab, which appears to have sorted it, though I can no longer see samba permissions.  I don't know if this is the ideal way of getting the job done, is there a better way?  If I had other users of this PC, i'd run into problems with the current method I am sure!

Cracker, cheers, silly of me to not try that!  I was stuck in 'damn thing wont copy' mode...

---

### Post by dmizer on 2006-12-16
> **LadFromWales85 said:**
> I ended up putting my UID and GID in fstab, which appears to have sorted it

humm ... when you created the smbcredentials file, you must make sure that there is a blank line after the password line.  a blank line is read as an end of file.  if it does not exist, the user name and password will not be read correctly.

---

### Post by LadFromWales85 on 2006-12-16
If a blank line is added after the username and password lines, as cifs reads the extra line as part of the password.  Before the line was removed, mount.cifs told me that my password was too long.  As far as Kate was concerned, there was no extra line...I had to remove the line in Nano to get it to read the auth file without erroring.

smbfs is happy with the extra line, though, just not cifs...

---

### Post by dmizer on 2006-12-18
nope.  i am positive that every cifs mount i have done has used a blank line after the password.

nano always saves a blank line at the end of every file ... always.  even if you delete the last line with nano, there's still a line there.  the problem is most likely that you created the file in a gui text editor rather than in the cli nano like i suggest in my howto.

as i said before, the blank line in the credentials file is read as an end of file.  without the end of file there, cifs reads the file as infinite.  the problem is in how kate encodes the text.

---

### Post by LadFromWales85 on 2006-12-19
Cheers for that mate!  I've been using nano since for editing config files etc, though apart from this one mishap, I've not had any other problems with Kate.  smbfs was happy reading the .smbcredentials file...I guess cifs is just picky!  All appears to be working fine, apart from when the share goes offline, everything accessing it gets really upset.

---

### Post by c.ovidiu on 2007-08-22
Hi. I've had a similar problem: I migrated from smbfs to cifs and discovered that some of the files were read-only, in spite of the fact that I had full access to the share. And it wasn't the credentials file either, because w/o that username and password I would have had no access at all to the share (not even read access). Turns out cifs tries to translate Windows permissions to the corresponding Linux permissions. And because some of the files were created or modified by other users, cifs thought I should have no write access to them. The solution that worked for me was to add the “noperm” parameter to the line. So my fstab lines ended up looking something like this: 

//server/share    /mnt/something    cifs    credentials=/etc/samba/user,iocharset=utf8,noperm,file_mode=0777,dir_mode=0777    0    0

Hopefully this will help some poor, desperate soul. :)

---

### Post by Telep on 2007-09-18
I just bought a LaCie Ethernet Disk mini (EDmini) and can confirm that the solution below is what did the trick for me. I tried the instructions in the thread [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534), which gained me access to the drive, but I had to change permissions first in the /media directory and then add the "noperm" option as in the quoted post. Now everything seems to work just fine. Just thought I'd add my experience if anyone has the same drive. :)

> **c.ovidiu said:**
> Hi. I've had a similar problem: I migrated from smbfs to cifs and discovered that some of the files were read-only, in spite of the fact that I had full access to the share. And it wasn't the credentials file either, because w/o that username and password I would have had no access at all to the share (not even read access). Turns out cifs tries to translate Windows permissions to the corresponding Linux permissions. And because some of the files were created or modified by other users, cifs thought I should have no write access to them. The solution that worked for me was to add the &#8220;noperm&#8221; parameter to the line. So my fstab lines ended up looking something like this: 

//server/share    /mnt/something    cifs    credentials=/etc/samba/user,iocharset=utf8,noperm,file_mode=0777,dir_mode=0777    0    0

Hopefully this will help some poor, desperate soul. :)

---

### Post by aroddo on 2008-01-03
> **dmizer said:**
> nope.  i am positive that every cifs mount i have done has used a blank line after the password.

nano always saves a blank line at the end of every file ... always.  even if you delete the last line with nano, there's still a line there.  the problem is most likely that you created the file in a gui text editor rather than in the cli nano like i suggest in my howto.

as i said before, the blank line in the credentials file is read as an end of file.  without the end of file there, cifs reads the file as infinite.  the problem is in how kate encodes the text.

i had exactly the same problem. it was the missing extra line that made the password too long.

i installed joe to edit the .smbcredentials and that worked fine.

---

