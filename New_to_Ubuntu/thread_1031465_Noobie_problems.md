---
title: "Noobie problems"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by Scott_MacAdam on 2009-01-05
I'm new to Linux and ubuntu but it has all been going well until I recently broke my hard drive and someone else re-installed ubuntu after getting me a new hard drive and putting it in my computer. none of these problems were present before, only now after the re-installation.

first off, when I log in, i get an error message, now i can't quite remember exactaly (i'll copy and paste if needed) but it says something along the lines of the home directory not being associated with the user ($home).... not quite sure what is going on here..
I went in under administration/users and groups and made sure that I have the root set to /root and my user log in set to /home/scott
but still the same message


secondly, I am having some root privileges problems in the terminal... when i am using commands that require root privileges, do i just use sudo?

third, I'm trying to get a driver for my comstar320GB externalHD for linux because I can't get access to it until i do and i haven't the slightest clue where to start.  can anyone help me there?

thanks for reading!

---

### Post by namdung on 2009-01-05
Pls post the exact error message.

Pls post output of ```

ls /home
sudo cat /etc/sudoers

```

Is ur external HDD connected via USB? Is it being recognized now? Was it being recognized earlier? Pls post the output of the following after connecting the HDD.
```
lsusb
```

Which Ubuntu version?

Pls paste specific details of the issues to help u better.

---

### Post by Scott_MacAdam on 2009-01-05
> **namdung said:**
> Pls post the exact error message.

Pls post output of ```

ls /home
sudo cat /etc/sudoers

```

Is ur external HDD connected via USB? Is it being recognized now? Was it being recognized earlier? Pls post the output of the following after connecting the HDD.
```
lsusb
```

Which Ubuntu version?

Pls paste specific details of the issues to help u better.


I'm pretty sure it's the newest version of ubuntu... 8.10?

I'll get that error message now and post it after this.

root@scott-laptop:~# ls /home
scott
root@scott-laptop:~# sudo cat /etc/sudoers
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL



I am connecting through USB, and when I do it appears as "new volume" but is unable to mount. 

this is what I get with it connected:

root@scott-laptop:~# lsusb
Bus 005 Device 002: ID 046d:08f0 Logitech, Inc. QuickCam Messenger
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 12c8:1f03  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

thanks for the help here.

---

### Post by donkyhotay on 2009-01-05
> **Scott_MacAdam said:**
> secondly, I am having some root privileges problems in the terminal... when i am using commands that require root privileges, do i just use sudo?

Yes, ubuntu by default uses root exclusively and while there are ways of logging in as root it is strongly discouraged. Most of us just use sudo since it is much more secure/safe. Here's a link for the information on ubuntu's usage of root/sudo. 
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Scott_MacAdam on 2009-01-05
well apparently I can't copy from that error box, but it said the users $home .dmrc file is being ignored. there was some more after that, but i think it was just explaining it...tell me if you need the rest

---

### Post by namdung on 2009-01-05
> **Scott_MacAdam said:**
> $home .dmrc file is being ignored

This is usually due to the fact that either that file or your home directory no longer belongs to you and is in the hands of root. U need to assign the ownership of ur home directory to urself.

In terminal
```
sudo chown -R $USERNAME: $HOME
chmod 755 $HOME
chmod 644 $HOME/.dmrc
```

Several posts on this in this forum
[http://ubuntuforums.org/showthread.php?t=971110](http://ubuntuforums.org/showthread.php?t=971110)
[http://ubuntuforums.org/showthread.php?t=371052](http://ubuntuforums.org/showthread.php?t=371052)

---

### Post by Scott_MacAdam on 2009-01-05
this is what I get

scott@scott-laptop:~$ sudo chown -R $Scott: $home
chown: missing operand after `:'

did I type it wrong?

---

### Post by namdung on 2009-01-05
Copy paste the code provided earlier in the terminal.

$home and $HOME are not the same.

---

### Post by Scott_MacAdam on 2009-01-05
another problem....
scott@scott-laptop:~$ sudo chown -R $SCOTT: $HOME
chown: cannot access `/home/scott/.gvfs': Permission denied

---

### Post by Scott_MacAdam on 2009-01-05
double post....

---

### Post by jerome1232 on 2009-01-05
You need to literally type "$USERNAME" not "$SCOTT".

$USERNAME is a variable that means the current user that's logged in.

Type echo $USERNAME to see what I mean. 

Permission denied will be normal for .gvfs it's a "special" folder I wouldn't worry about it.

---

### Post by cariboo on 2009-01-05
That's normal nothing to worry about.

Jim

---

### Post by namdung on 2009-01-05
Try this in terminal
```
sudo chmod 644 /home/scott/.dmrc
sudo chown scott /home/scott/.dmrc
sudo chmod -R 700 /home/scott
sudo chown -R scott /home/scott
```

Pls go through the above mentioned links carefully and u should be fine.

---

### Post by albinootje on 2009-01-05
> **Scott_MacAdam said:**
> 
third, I'm trying to get a driver for my comstar320GB externalHD for linux because I can't get access to it until i do and i haven't the slightest clue where to start.
Can you plug in that drive and then post the output of the following :
```

sudo update-usbids
lsusb
mount
dmesg

```

---

### Post by beattyml1 on 2009-01-05
I have the exact same problem I fixed it once upon a time and now it's back and i've just been ignoring it I will try to  fix it again and if it works post the code to do it.

---

### Post by beattyml1 on 2009-01-05
the following code resolved the problem for me
```
sudo chown username .dmrc
```
```
sudo chmod 644 .dmrc
```
```
sudo chmod 755 ~
```

that is the code I used, another way that means the same thing but assumes less would be:

```
sudo chown username /home/username/.dmrc
```
```
sudo chmod 644 /home/username/.dmrc
```
```
sudo chmod 755 /home/username/
```

hope that helps

---

