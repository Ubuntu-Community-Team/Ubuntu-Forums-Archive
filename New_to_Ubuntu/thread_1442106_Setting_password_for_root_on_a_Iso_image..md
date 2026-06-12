---
title: "Setting password for root on a Iso image."
date: 2010-03-29
forum: New to Ubuntu
---

### Post by ericeclifford on 2010-03-29
Hi I am trying to create a password for root for a customized Iso image that is booted from grub2( from a solid state disk).

I tried passwd root    and then typed my password that I wanted in, but I still could sudo stuff without a password and sudo -s stuff.

Maybe I should just erase sudo in a startup script as the last thing to do?

That way the users wont go messing up the grub2 Isodevice.

---

### Post by lisati on 2010-03-29
People who respond will need to be careful. Please have a look here:
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by sisco311 on 2010-03-29
> **ericeclifford said:**
> Hi I am trying to create a password for root for a customized Iso image that is booted from grub2( from a solid state disk).

I tried passwd root    and then typed my password that I wanted in, but I still could sudo stuff without a password and sudo -s stuff.

Maybe I should just erase sudo in a startup script as the last thing to do?

That way the users wont go messing up the grub2 Isodevice.

sudo needs your user password, so set one for the user:
```
passwd
```

and disable the root account password:
```
sudo usermod -p ! root
```

For more info, please read the links posted by lisati.

---

### Post by ericeclifford on 2010-03-29
> **sisco311 said:**
> sudo needs your user password, so set one for the user:
```
passwd
```

and disable the root account password:
```
sudo usermod -p ! root
```

For more info, please read the links posted by lisati.

well I tried this, I went to terminal and I still could type

```
sudo -s
```

and it still logged me on as root, I tested this by gedit /etc/fstab and entering something random and it still saved. I will look at those links nows :)

---

### Post by sisco311 on 2010-03-29
> **ericeclifford said:**
> well I tried this, I went to terminal and I still could type

```
sudo -s
```

and it still logged me on as root, I tested this by gedit /etc/fstab and entering something random and it still saved. I will look at those links nows :)

When using sudo, password is stored by default for 15 minutes. After that time, you will need to enter your password again.

Try to invalidate the user's timestamp:
```
sudo -k
```
then run sudo again. You should be prompted for the user's password.

---

### Post by ericeclifford on 2010-03-30
> **sisco311 said:**
> When using sudo, password is stored by default for 15 minutes. After that time, you will need to enter your password again.

Try to invalidate the user's timestamp:
```
sudo -k
```
then run sudo again. You should be prompted for the user's password.

well I tried to do the sudo -k in the customization process, and used chroot edit

and I typed in the passwd and usermod stuff, then tried sudo -k, and in the chroot environment it told me unable to resolve host for eric( which is the installed version, not the user for my customized iso image version)

---

### Post by sisco311 on 2010-03-30
before you chroot, bind the /etc/hostname & /etc/hosts files:
```
sudo mount --bind /etc/hostname **mount/point/etc/hostname**
sudo mount --bind /etc/hosts **mount/point/etc/hosts**

```

or in the chroot environment change temporarly the hostname:
```
hostname newhostname
```

Oh and please post the content of the sudoers file:
```
sudo cat /etc/sudoers
```

---

### Post by ericeclifford on 2010-03-30
```
ubuntu@ubuntu:~$ sudo -s
root@ubuntu:~# cat /etc/sudoers
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) NOPASSWD: ALL

```

I tried it again. But I think I didn't do the bind right I guess, because instead of your mounting, I just didnt rm the etc/hosts and stuff until after I typed this in the chroot environment. 
Thanks for helping though, this file seems to be weird(I need to study it more), anyways back to studying this subject, you would this changing the root pw for a live dvd iso wouldnt be this bad :).

---

### Post by sisco311 on 2010-03-30
> **ericeclifford said:**
> ```
ubuntu@ubuntu:~$ sudo -s
root@ubuntu:~# cat /etc/sudoers
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) NOPASSWD: ALL

```

I tried it again. But I think I didn't do the bind right I guess, because instead of your mounting, I just didnt rm the etc/hosts and stuff until after I typed this in the chroot environment. 
Thanks for helping though, this file seems to be weird(I need to study it more), anyways back to studying this subject, you would this changing the root pw for a live dvd iso wouldnt be this bad :).

edit the file:
```
sudo visudo
```
and change the last line to:
```
%admin ALL=(ALL) ALL
```
save it & exit (Ctrl+x, y, Enter).

now when you use sudo you will be prompted for your password.

---

### Post by ericeclifford on 2010-03-30
> **sisco311 said:**
> edit the file:
```
sudo visudo
```
and change the last line to:
```
%admin ALL=(ALL) ALL
```
save it & exit (Ctrl+x, y, Enter).

now when you use sudo you will be prompted for your password.

Ok cool, well I tried to save the file in both VI and gedit, and it wont let me save it for some reason.

Edit: I might of made a mistake, by not doing the : to exit insert mode, sorry thought I could do it in gedit, because I forgot VI manual :).

Anyways I changed the permissions, so now I am just going to restart it and try.

---

### Post by sisco311 on 2010-03-30
> **ericeclifford said:**
> Ok cool, well I tried to save the file in both VI and gedit, and it wont let me save it for some reason.

Edit: I might of made a mistake, by not doing the : to exit insert mode, sorry thought I could do it in gedit, because I forgot VI manual :).

Anyways I changed the permissions, so now I am just going to restart it and try.

You should always use visudo to edit the file. If you want to use a different editor than the default, then run:
```
sudo EDITOR=gedit visudo
```

The file has 0440 permissions, if you don't use visudo to edit it, the editor may change the permissions of the file, run:
```
chmod 0440 /etc/sudoers
```to set the correct permissions on the file.

---

### Post by ericeclifford on 2010-03-31
I am not sure why, but when I do visudo in chroot mode, I dont even see that last line there to change.

Is it only unpacked when the ISO boots up? maybe I need to have a startup script change the /etc/sudoers file to what I need it be.

Since visudo changes I am guessing with the ISO image unpacking.

Unless I am missing something totally :).

---

### Post by sisco311 on 2010-03-31
> **ericeclifford said:**
> I am not sure why, but when I do visudo in chroot mode, I dont even see that last line there to change.

Is it only unpacked when the ISO boots up? maybe I need to have a startup script change the /etc/sudoers file to what I need it be.

Since it visudo changes I am guessing with the ISO image unpacking.

Unless I am missing something totally :).

EDIT: 

Then edit the sudoers file from your host OS with gedit. 

Assuming that the ISO is mounted under /media/iso:
```
sudo EDITOR=gedit /media/iso/etc/sudoers
```

---

### Post by ericeclifford on 2010-03-31
I forgot when I mount the file, It is not uncompressed.

So maybe I will hide a sudoers txt file in the customized iso somewhere, and have my startup script cp to the /etc folder and overwrite it, that should do what you are asking right?

---

### Post by ericeclifford on 2010-03-31
Well here is a update,

Well I did the steps you told me,

and I cp'ed the edited sudoers file to the /etc dir.

But when I do sudo "something" or sudo -s  I get a password required line, but the password changes from my password to Blank( No space/characters just a blank password, all it takes is me to press Enter and it logs on)

I wonder if I can just erase the ubuntu user, and make my own user.

ubuntu seems to have admin permissions, but still that doesnt really help too much due to the password I create being deleted and replaced with a blank password. Maybe I can create a user and erase Ubuntu, and just cp and paste edited text files for that said user including the password, and just cp/rm the files as needed?

I am going to read more into it, everything should be controlled by text files right? so if I played around with it enough and have a startup script with lots of cp's to overwrite the original live cd user/pass text config files, it should be possible right :)

EDIT: btw, if there is a way to disable root being accessed and sudo not being allowed at all, that would be fine, well i did some more searching, and found out how to lock root, and then I am going to comment some stuff out of the sudoers config file, and see what happens, you only learn by doing and failing :)

---

### Post by ericeclifford on 2010-04-01
Well here is a little update, at the end of my script I added a rm /etc/sudoers and I also did a passwd -l root during customization.

I cant get in root at all for my LIVE cd, which is exactly what I want, but before I remove the Sudoers file, my startup script runs the command and programs that need to be run with root. I got a lot of stuff for firefox installed, so no need in downloading anything outside of the home directory.

Thanks for your help.

---

### Post by ericeclifford on 2010-04-02
Well I am close, but not there yet, my startup script is not doing what it is expose to.

I am trying to make my program run, and then sleep for 5 second and then remove sudoers( it takes sudo for my program to run).

It is like this

./path/to/program

sleep 5 &
rm /etc/sudoers



This is a startup script, but it is not removing the /etc/sudoers file, anyone know why?

---

### Post by JKyleOKC on 2010-04-02
> **ericeclifford said:**
> 
./path/to/program

sleep 5 &
rm /etc/sudoers

This is a startup script, but it is not removing the /etc/sudoers file, anyone know why?I see two possible problems here. First is that startup scripts run as the root user, so you need an absolute path for "./path/to/program" to get it to execute since "." may not refer to the directory you think it does at that time. The other is that by putting the "sleep 5" in the background with the "&" at the end of the line, it will return immediately instead of waiting as you intend.

Neither of these, though, would explain why sudoers does not get removed. Incidentally, if your program includes calls to sudo, that could keep it from working at startup time since it would already be running as root. I would try removing all the calls to sudo, and adding the "rm /etc/sudoers" as the very last command in your script...

---

### Post by ericeclifford on 2010-04-02
> **JKyleOKC said:**
> I see two possible problems here. First is that startup scripts run as the root user, so you need an absolute path for "./path/to/program" to get it to execute since "." may not refer to the directory you think it does at that time. The other is that by putting the "sleep 5" in the background with the "&" at the end of the line, it will return immediately instead of waiting as you intend.

Neither of these, though, would explain why sudoers does not get removed. Incidentally, if your program includes calls to sudo, that could keep it from working at startup time since it would already be running as root. I would try removing all the calls to sudo, and adding the "rm /etc/sudoers" as the very last command in your script...

Well, I have the pathing right, 

and when I had my program with the & sign after it, and then the rm /etc/sudoers, it would remove sudoers, but my program wouldnt run( and my program ran before I had the & /etc/sudoers in, so I thought it was a timing issue, so I added the sleep 5, but you say sleep 5 and & dont go well together? because my program is running, but sudoers is not getting removed, so maybe do it like this.


./path/to/program

sleep 5

rm /etc/sudoers &

?

Anyways, I am recreating the iso image right now, so will test that out soon.

---

### Post by ericeclifford on 2010-04-02
Well this is very difficult( lol it looks so easy too)

I can get the pat_update.exe to work, but I need to include a ampersand after it to rm /etc/sudoers because my program stays open.

But when I ran the program and had a ampersand with rm /etc/sudoers right after it, The program didnt work.

---

### Post by JKyleOKC on 2010-04-02
> **ericeclifford said:**
> Well this is very difficult( lol it looks so easy too)

I can get the pat_update.exe to work, but I need to include a ampersand after it to rm /etc/sudoers because my program stays open.

But when I ran the program and had a ampersand with rm /etc/sudoers right after it, The program didnt work.Can you include the "rm /etc/sudoers" as the last command in your script? At start-up time, the script will run as "root" so it will never need "sudo" itself. You could then add the "&" to the line that calls your program, and it ought to work...

If you want to be able to test the program from a terminal without wiping out your own sudoers file, you could do this at the end:
```
if [ "`id -u`" -eq 0 ]; then
  rm /etc/sudoers
fi

```
That will only remove sudoers when the program runs as root -- but then the other commands would need the "sudo" prefix while testing...

---

### Post by ericeclifford on 2010-04-05
Well I did what you said, I  put the program at the top, with a ampersand after it, and it looks like I never got passed that program, like it just stalls at the program, the program will run forever, it is a C program with a LOOP so. I guess it is considered a process, anyways I put the program at the top with a & and it ran but the rest of the script never ran due to it.

---

