---
title: "[SOLVED] NAS mounts rw but documents open read-only"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by u-ben-tu on 2008-05-27
I have a NAS share and I'm having permissions problems when trying to connect:

Navigating to Places > Network > NAS > Media works fine and I can read and write to files and create and delete new files and directories (although don't seem to have permission to cut or copy to my local drive).

What I'd prefer to do is mount the drive by adding a line to fstab. 

So, I've created a folder /home/ben/Media and run:

```
sudo chmod -R 777 /home/ben/Media
```

Then tested:

```
sudo mount nas:/mnt/C /home/ben/Media
```

The NAS mounts OK. I check the permissions by right clicking a document and looking at the Permissions tab of Properties. I have read write access. But when I open the document, it's READ ONLY!

Also tested with CIFS adding options as recommended on other threads: 
```
sudo mount -t cifs //nas/Media /home/ben/Media -o guest,rw,file_mode=0777,dir_mode=0777,uid=1000,gid=1000
```

I get the same result.

For the record, I'm using a Sumvision NetBox NAS with a 250gb drive containing the /home partition of my previous install of Ubuntu 8.04. I expanded it to wipe the existing / and swap partitions. Could any user settings be lurking here that would effect anything?

On the client, I'm running 8.04.  

Any suggestions gratefully received!

---

### Post by dmizer on 2008-05-27
just add the appropriate line to fstab.

the reason you do not have permission is local.  you mounted the share as root (sudo), so only root has permissions to read and write to the mounted directory.  if you mount with fstab, you will not encounter this problem.

---

### Post by u-ben-tu on 2008-05-27
Thanks. 

I tried adding this to fstab:

```
nas:/mnt/C /home/ben/Media nfs rsize=8192,wsize=8192,timeo=14,intr 0 0
```

Then:

```
sudo mount -a
```

It mounts, but documents are still opening as read only. 

Also tried with 'rw' option:

```
nas:/mnt/C /home/ben/Media nfs rw,rsize=8192,wsize=8192,timeo=14,intr 0 0
```

And tried with CIFS:

```
//nas/Media /home/ben/Media cifs guest,rw,file_mode=0777,dir_mode=0777,uid=1000,gid=1000 0 0
```

But again, after:
```
sudo mount -a
```

I've got the same problem. 

Am I right to be using this command, or do I need to reboot?

---

### Post by dmizer on 2008-05-27
after you do "sudo mount -a"

post the output of:
```
vdir /home/ben/Media
```

---

### Post by u-ben-tu on 2008-05-27
```
drwxrwxrwx 10 ben ben 0 2008-03-07 07:44 Backup
drwxrwxrwx  7 ben ben 0 2008-05-14 08:01 Documents
drwxrwxrwx 11 ben ben 0 2008-05-25 00:26 Music
drwxrwxrwx  5 ben ben 0 2008-05-25 02:25 Pictures
-rwxrwxrwx  1 ben ben 0 2008-05-27 15:13 test.odt
drwxrwxrwx  1 ben ben 0 2008-05-27 13:46 ubuntu
drwxrwxrwx  6 ben ben 0 2008-03-08 01:31 Videos
```

---

### Post by dmizer on 2008-05-27
all the permissions look good.  you're mounting as yourself.  it should be working.

double check the permissions on the local folder

unmount:
```
sudo umount /home/ben/Media
```
change permissions:
```
sudo chmod 777 /home/ben/Media
```
remount.

---

### Post by u-ben-tu on 2008-05-27
Weird, huh?

After *chmod*, and then *sudo mount -a*, there's no change. 

If it's any help, I created a test document in .odf format. When I *sudo mount -a* with CIFS line in fstab it shows 'ben' as the owner of this document, but when I mount using NFS, it shows 'root', even with 'rw' in the options. 

Regardless of whether I use CIFS or NFS, it's still opening read-only!

---

### Post by dmizer on 2008-05-27
try mounting in a folder outside of your home directory.

create a directory in /media like so:
```
sudo mkdir /media/Media
sudo chmod 777 /media/Media
```
and change your fstab line to this:
```
//nas/Media /media/Media cifs guest,rw,file_mode=0777,dir_mode=0777,uid=1000,gid=1000 0 0
```
remount and see if that makes a difference.

is the user id on the nas also "ben"?

---

### Post by u-ben-tu on 2008-05-27
OK, I created /media/Media, ran chmod on it, then mounted it via fstab using the line you gave, but no change. 

Not sure about the user id on the nas, so this could be the problem. It uses a web interface for configuring it - I'm not sure how to get anything beneath that. Since it has nfs capability and supports ext3, presumably it is running Linux. Do you know how I might get at it? Thanks.

---

### Post by dmizer on 2008-05-27
if you didn't change the user yourself, it's not ben.

what nas device (make and model number) are you using?

---

### Post by dmizer on 2008-05-27
humm ... another thought, are you using/have installed firestarter?

---

### Post by u-ben-tu on 2008-05-27
1. The NAS is a SumVision NET-Box. It's cheap and cheerful (:wink:) so it isn't very well documented/supported as far as I can see.

The SumVision site lists the specs:

[http://www.sumvision.com.cn/searchResults.aspx?ptype=37]("http://www.sumvision.com.cn/searchResults.aspx?ptype=37")

There's also some info here:
[http://svp.co.uk/product/sumvision_netbox_3_5_inch_nas_network_storage_enclosure_55482]("http://svp.co.uk/product/sumvision_netbox_3_5_inch_nas_network_storage_enclosure_55482")

2. Haven't got Firestarter installed.

---

### Post by dmizer on 2008-05-28
try removing the id options and include the nounix option like so:
```
//nas/Media /media/Media cifs guest,rw,nounix,file_mode=0777,dir_mode=0777 0 0
```

---

### Post by u-ben-tu on 2008-05-28
Thanks dmizer. Sorry for the delay -- can only access my pc in the evenings now until the weekend.

Adding the line you suggest to fstab still results in files opening read only. Permissions for files and folders show up as 'root'.

---

### Post by dmizer on 2008-05-28
it's no problem, i've been rather busy myself.

with your current settings, please post the output of:
```
ls -n
```
and
```
cat /etc/passwd | grep ben
```
(don't worry, this will not expose your password)

after that, let's try removing the file and directory masks:
```
//nas/Media /media/Media cifs guest,rw 0 0
```

see if that makes a difference.

---

### Post by u-ben-tu on 2008-05-29
Hi. 

```
ls -n

drwxr-xr-x 2 1000 1000 4096 2008-05-29 00:07 Desktop
drwxr-xr-x 5 1000 1000 4096 2008-05-29 07:07 Local Documents
drwxrwxrwx 2 1000 1000 4096 2008-05-20 20:10 Media
drwxr-x--- 3 1000 1000 4096 2008-05-19 20:23 Podcasts
```

```
cat /etc/passwd | grep ben

ben:x:1000:1000:Ben,,,:/home/ben:/bin/bash
```

Then after changing the line in fstab to:

```
//nas/Media /media/Media cifs guest,rw 0 0
```

... owner shows as 'root' and files open read only.

Also tried changing the destination folder to /home/ben/Media, rather than media/Media but the result was the same.

---

### Post by dmizer on 2008-05-29
try this line in fstab instead of the cifs one i gave earlier (several changes, please copy/paste):
```
sudo mount -t [COLOR="Red"]smbfs[/COLOR] //nas/Media /media/Media -o guest,rw,fmask=777,dmask=777,uid=1000,gid=1000 0 0
```
be sure to delete or comment out (with "#") the old cifs line.

if this is successful, then i'm afraid the problem is your nas device.

---

### Post by u-ben-tu on 2008-05-30
OK, I pasted the command into the terminal and it printed out instructions for using the mount command, so something was amiss. 

I noticed that you added the two zeros at the end like in an fstab entry. I don't really know what I'm doing(!) but I wasn't sure if they should be there, so I tried without them just in case and it printed the following in the terminal:

```
Warning: mapping 'guest' to 'guest,sec=none'
WARNING: 'fmask' not expressed in octal.
WARNING: CIFS mount option 'fmask' is deprecated. Use 'file_mode' instead.
WARNING: 'dmask' not expressed in octal.
WARNING: CIFS mount option 'dmask' is deprecated. Use 'dir_mode' instead.
```

... then the drive appeared on the desktop, but when I opened it, it was empty.

So I guess, either way, it was unsuccessful.

---

### Post by dmizer on 2008-05-30
sorry for not being clear.  you should try the above line in your fstab.

mounting from the command line will sometimes result in permissions problems because you have to use "sudo" in order to invoke the mount command.

---

### Post by u-ben-tu on 2008-05-31
No, my fault! I didn't read it properly and got confused because it didn't look like the other fstab entries.   

I pasted the line into fstab and after [FONT="Courier New"]sudo mount -a[/FONT], I got: 

```
[mntent]: line 15 in /etc/fstab is bad
```

So I also tried this way:

```
//nas/Media /media/Media smbfs guest,rw,fmask=777,dmask=777,uid=1000,gid=1000 0 0
```

This time, after [FONT="Courier New"]sudo mount -a[/FONT], I get ...

```
Warning: mapping 'guest' to 'guest,sec=none'
WARNING: 'fmask' not expressed in octal.
WARNING: CIFS mount option 'fmask' is deprecated. Use 'file_mode' instead.
WARNING: 'dmask' not expressed in octal.
WARNING: CIFS mount option 'dmask' is deprecated. Use 'dir_mode' instead.

```

Like when I mounted it via the terminal, the drive appears, but it's empty when I open it in nautilus.

---

### Post by dmizer on 2008-05-31
interesting ...

hardy appears to be using cifs even though smbfs is listed.  and according to [this thread](http://ubuntuforums.org/showthread.php?t=707370), you would have to compile samba source to enable smbfs.  it's possible that smbfs will work correctly for you, but it's probably better if we find a way to make cifs work.

let's try a small change in permissions for the mount.  please try this line in fstab (please erase or disable the other smbfs/cifs entries we've added):
```
//nas/Media /media/Media cifs guest,rw,file_mode=0775,dir_mode=0775 0 0
```

---

### Post by u-ben-tu on 2008-05-31
OK. Using this line in fstab, the drive mounts with root as the owner and group and with read-only permissions for others.

---

### Post by dmizer on 2008-05-31
okay, i just received a post in another thread which suggests that the noperm option might fix your problem like so:
```
//nas/Media /media/Media cifs guest,rw,[COLOR="Red"]noperm[/COLOR],file_mode=0775,dir_mode=0775 0 0
```

---

### Post by u-ben-tu on 2008-05-31
No change, I'm afraid.

---

### Post by dmizer on 2008-05-31
and i'm very sorry to say that i have no more answers for you.  your nas device is simply running a samba version that's too old to handle cifs correctly.

does your nas device support ftp?  if so, that may be a viable option for you.

---

### Post by u-ben-tu on 2008-05-31
OK. I can work around this if necessary. I really appreciate all your help and advice so far. 

Just one more thought ...

Could it be a problem with Openoffice? I'd tried opening a test .odt file which was showing up read only. To try and make sure it wasn't specific to that, I tried creating a text file (via Right Click > Create Document > Empty file) and tried to open it with gedit and was experiencing problems. So I thought it was a general issue. 

BUT, I came across an old thread of yours ([http://ubuntuforums.org/showthread.php?t=288534]("http://ubuntuforums.org/showthread.php?t=288534"))which said that gedit was buggy over CIFS.

So, I started to try some other options:

I mounted via fstab using:
```

//nas/Media /home/ben/Media cifs guest,rw,file_mode=0777,dir_mode=0777,uid=1000,gid=1000 0 0
```

Then I tried opening and then deleting some files using some other programs (Rhythmbox, F-Spot.) This worked OK, no 'permission denied' dialogues or such like. 

Is there a more systematic way to test my theory?

---

### Post by dmizer on 2008-05-31
you are not the first person to experience this with openoffice.  someone posted just yesterday in my howto about it: [http://ubuntuforums.org/showpost.php?p=5077646&postcount=479](http://ubuntuforums.org/showpost.php?p=5077646&postcount=479) so i would say your theory is quite likely.  if you look through the bug report i link to, you may find an answer to your problem.

and though the original howto post is old, i still actively support, and update it to the tune of 3 or 4 posts a day.  it's even linked in my sig ;)

---

### Post by u-ben-tu on 2008-06-04
OK. After a bit more experimenting, I'm pretty confident that this is an issue with Openoffice.

Thanks dmizer. Much appreciated as I don't think I could have worked this out without your detailed troubleshooting advice.

I'll look into the OpenOffice problem and post to your other thread if I find a solution.

---

### Post by MacDuff on 2009-07-11
I am trying to figure out an answer to the same problem, not only with OpenOffice but with digiKam, text editor and possibly others.

My system uses a D-Link DNS 323 and works perfectly with Ubuntu 8.04 but only partially with 9.04.

The DNS mounts using the same entry as I used in 8.04 and appears to have read/write permissions for the owner and group.  I can create directories and add files to it but cannot edit those files after creation.    

Oddly NoteCase Pro can read and edit its files with no problem.  It looks like lock files are left in the NAS but perhaps I have not noticed them before.

There would seem to be a bug somewhere but I am not knowledgeable enough to find it.  Any suggestions?

OOPS, I did not notice this thread is marked solved.  I will create a new thread.

---

