---
title: "can't use ./ to run csh scripts"
date: 2011-08-15
forum: New to Ubuntu
---

### Post by ppallett on 2011-08-15
I've got #!/bin/csh at the top of the script, and it worked just fine when I had lucid install, but now I've got nancy installed and it's not working.  I have installed both csh and tcsh.  The scrip WILL run if I type: csh scriptname in the command line.  It just won't work if I use ./scriptname. 

Also, if I right click on the file and go to the permissions page, it won't let me check "run as executable".  I can check the box, but it immediately automatically unticks.    I also have adminstrative rights.

 Anyone know what's going on?

---

### Post by AlphaLexman on 2011-08-15
> **ppallett said:**
> I've got #!/bin/csh at the top of the script, and it worked just fine when I had lucid install, but now I've got nancy installed and it's not working.  I have installed both csh and tcsh.  The scrip WILL run if I type: csh scriptname in the command line.  It just won't work if I use ./scriptname. 

Also, if I right click on the file and go to the permissions page, it won't let me check "run as executable".  I can check the box, but it immediately automatically unticks.    I also have adminstrative rights.

 Anyone know what's going on?
Is the script in your $HOME directory or a sub-directory ??
Which shell are you using to run the script ??

You should at least see [csh-programming-considered-harmful]("http://www.faqs.org/faqs/unix-faq/shell/csh-whynot/")

---

### Post by wojox on 2011-08-15
Did you source it:

```
source ~/.cshrc
```

---

### Post by ppallett on 2011-08-16
It's in neither - it's on a external hard drive, but again didn't have a problem running it from there before the reinstall/upgrade.  It's a script I wrote to help with neural imaging data analysis - it's safe.  

No I haven't sourced it, but I haven't had to  do that before either.

It is a bash shell, but I figured if I had csh installed, it should still be able to run the csh script despite the differences in shell.  

Basically, I have a link to a folder on my external hard drive that exists in my home folder.  So I cd in the terminal to the desired directory on my external.  The script also exists in that directory, which is why I've been able to run it in the past without adding it to cshrc.

---

### Post by The Cog on 2011-08-16
I wonder if the mount options don't allow executing programs. Can you post the output of the command **mount** and tell us which drive the file is on?

---

### Post by ppallett on 2011-08-16
The file is on the drive with LaCie (dev/sdb1, last line below).  Here's the output from **mount**:

/dev/sda6 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/menglab/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=menglab)
/dev/sda3 on /media/OS type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1 on /media/LaCie type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

---

### Post by decoherence on 2011-08-16
I'm afraid I don't have an Ubuntu box handy to check this on but could you tell me the output of

which csh

just wondering if it moved somewhere else in the upgrade?

Ironic that you're using a csh script in the context of medical imaging since the surgeon general considers the language harmful to one's health. In any case, good luck!

---

### Post by The Cog on 2011-08-16
> **ppallett said:**
> /dev/sdb1 on /media/LaCie type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
Well, that blows me out. I don't recognise the mount type or the options. I have no idea whether that's the problem or not. Sorry.

---

### Post by ppallett on 2011-08-16
which csh produces /bin/csh

Actually, it's to work with AFNI which is sponsored by the government (NIH).  They recommend t-shell, but I kind of go back and forth between t-shell and c-shell.

---

### Post by ppallett on 2011-08-17
So to check if it's a mounting problem, I took a simple script for making a brain maskand pasted it as well as all the required files into my home folder.  I still had the problem with Permission Denied, but this time it let me manually change the permission options so that it could run as an executable.  So now it's able to run with ./.  However, the problem still remains for running off my external hard drive and it won't let me change the permissions.  So it seems it does have something to do with the mounting settings.

---

### Post by pi.boy.travis on 2011-08-17
I have this problem with my external drives. I change the ownership of the drives from the default to my user. Just make yourself the owner of the /media/LaCie directory and you should be good to go.

---

### Post by ppallett on 2011-08-18
Unfortunately, the default owner is my user.  For what it's worth when I check the permissions by right-clicking on the icon for the drive and selecting permissions, it says "the permissions for LaCie cannot be determined".  But if I do the same thing for the LaCie folder under media, it gives permissions.  Although I am already the owner, it also does not allow me to make any changes to permissions...  as in, I make them, click apply to enclosed files/folders, and once that finishes applying, it automatically resets itself to its initial unaltered state.  And since at that level it says "allow files to run as executable" (or something to that effect), it also hasn't applied that option to the enclosed files/folders.

---

### Post by pi.boy.travis on 2011-08-18
> **ppallett said:**
> Unfortunately, the default owner is my user.  For what it's worth when I check the permissions by right-clicking on the icon for the drive and selecting permissions, it says "the permissions for LaCie cannot be determined".  But if I do the same thing for the LaCie folder under media, it gives permissions.  Although I am already the owner, it also does not allow me to make any changes to permissions...  as in, I make them, click apply to enclosed files/folders, and once that finishes applying, it automatically resets itself to its initial unaltered state.  And since at that level it says "allow files to run as executable" (or something to that effect), it also hasn't applied that option to the enclosed files/folders.

In order to change the permissions you must be using Nautilus as root. Give this a shot, it a terminal:

```
gksu nautilus
```

That should open up a new file browser window. BE CAREFUL, you're using the file browser as root, you could accidentally screw things up if you aren't careful. Using that window you should be able to change the permissions.

---

### Post by ppallett on 2011-09-02
Sorry it's taken awhile to respond but running nautilus didn't change anything.  When I tried to change permissions it still instantly and automatically unchecked "allow executing file as program".

---

### Post by bodhi.zazen on 2011-09-02
Works here, perhaps a typo or wrong path ?

```
bodhi:~$ cat file.csh
#!/bin/csh

echo "It works"

bodhi:~$ ls -l file.csh
-rwxr-xr-x. 1 bodhi bodhi 28 Sep  2 13:09 file.csh

bodhi:~$ ./file.csh
It works
```

---

### Post by ppallett on 2011-09-02
The problem is specific to the files I'm running off of my LaCie external drive.  It works when I'm in my home directory too.  It's not a typo, if you see my earlier posts I say that I can take those same files, paste them into my home folder and run them using ./.  But if I'm running from the LaCie drive, I have to type csh filename rather than ./filename.  Unfortunately, I'm dealing with several hundered gigabytes of data that need to be portable, so I don't exactly want to copy it to the hard drive.  These same files work from the hard drive in lucid using ./, it's just in natty that it's become a problem.  So the only difference between when it worked and when it didn't is the version of Ubuntu I am running.  Although it isn't a big deal, it is starting to become a problem since there are certain new commands in my neuroimaging tool that rely on ./ to run other files.

---

### Post by bodhi.zazen on 2011-09-02
I believe your problem is that your external drive is mounted noexec as suggested above.

---

### Post by ppallett on 2011-09-03
I agree, but then noexec is not listed in the drive permissions: /dev/sdb1 on /media/LaCie type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_ permissions)  I'll openly admit that I haven't a clue what nosuid and nodev (no development?) refer to...  but otherwise at the level of the drive, the permissions look ok.  It's when I go into folders and files within the drive that the unchangeable (even via nautilus) restrictions appear.  Although using nautilus, I'm still trying to make changes through the GUI, perhaps if I tried it via command line it would work??  I know it shouldn't make a difference where I do it, but I know one of the early bugs with lucid made it so the shutdown button didn't work (on certain machines), but you could still shut down from the command line - which is why I am wondering if there may be a similar command line based work around.  Don't know how to do that though - I only know basic terminal commands, enough to move around in directories and run my files.

---

