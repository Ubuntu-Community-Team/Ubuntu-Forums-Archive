---
title: "Karmic &quot;messed up&quot;"
date: 2010-09-18
forum: New to Ubuntu
---

### Post by vecvan on 2010-09-18
Hi, i am new here to ask for help because i messed with visudo and cant sudo anymore.. 
I edit /etc/sudoers to relieve me from typing pws e.g. for every xsession. i added ```
<login_name> ALL= NOPASSWD /usr/sbin/hibernate
``` with 'sudo visudo' and [following this old thread,]("http://ubuntuforums.org/showthread.php?t=329902") cause i thought visudo would make sure i wouldnt mess up.
i didnt expect any errors, before i read this. maybe to forget the trailing '%' could cause such an error?
```
nomad@admon-desk:~$ sudo visudo
>>> /etc/sudoers: syntax error near line 25 <<<
sudo: parse error in /etc/sudoers near line 25
sudo: no valid sudoers sources found, quitting
nomad@admon-desk:~$ sudo gedit /etc/sudoers
>>> /etc/sudoers: syntax error near line 25 <<<
sudo: parse error in /etc/sudoers near line 25
sudo: no valid sudoers sources found, quitting
nomad@admon-desk:~$
```i wont shut off my computer until this is resolved, because atm i got my ntfs hdds mounted and after restart i could probly not access them anymore, except if i needed to run a livecd.

maybe i messed up saving the correct file while leaving nano. on saving it suggested 'sudoers.tmp' as filename, which i removed '.tmp' from and saved. was that wrong maybe?

could anymore specific infos help you?

edit: added the link and fixed grammar :)
edits: added a fev more descriptions, off to search the forum now

---

### Post by garvinrick4 on 2010-09-18
Seems you have to either return line 25 the way it was, get rid of it if you put it in or # (comment) it out.

---

### Post by garvinrick4 on 2010-09-18
##Here is a fresh one to copy and paste if needed: Only different is my default line is
##set to use just one password in terminal per session. But always have to use password when installing software.

#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults    env_reset,timestamp_timeout=-1

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Allow members of group sudo to execute any command after they have
# provided their password
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

---

### Post by juil on 2010-09-18
I ran into a similar problem not too long ago.

Here's what the Sudoers file should look like:

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults    env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Allow members of group sudo to execute any command after they have
# provided their password
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

What you need to do is restart the system in recovery mode in GRUB and when loaded select ROOT.
When a terminal appears (or it might be just a black screen with a prompt), type nano /etc/sudoers.
Repair any changes that are needed.
Exit nano.
Type exit in the terminal and select resume in the menu.

NOTE: If you were comparing your Sudoers with the one i posted and noticed a difference in the lines with the # sign, don't worry about that as this just means that it's a comment and won't affect the Sudoers file, just in case you didn't know that.

---

### Post by garvinrick4 on 2010-09-18
The only difference is mine has a timestamp not to ask me for my
password multiple times in same session (,timestamp_timeout=-1)
If I put 30 where -1 is it gives me a 30 minute timestamp instead of whole session.
or 20 or 40 whatever you want -1 is unlimited time

Defaults    env_reset,timestamp_timeout=-1

---

### Post by vecvan on 2010-09-19
can i edit sudoers from live-cd? i would think yes, but id like to confirm it.

---

### Post by garvinrick4 on 2010-09-19
> **vecvan said:**
> can i edit sudoers from live-cd? i would think yes, but id like to confirm it. Only if you mount drive and chroot into it.
Lets say you are trying to mount sda5
Use your own:
```
sudo mkdir /media/root
``````
sudo mount /dev/sda5 /media/root
``````
sudo chroot /media/root
```Now in root in sda5
Do what you want to install in Live Cd session:
Then hit ctrl/d
then:
```
sudo umount /media/root
```If you need to get internet connection before you do chroot command make sure you have connection in Live Cd and then;
```
sudo cp /etc/resolv.conf /media/root/etc/resolv.conf
```With internet connection after chroot you can update and upgrade
```
apt-get update && apt-get upgrade
```or you can fix broken dependencys
```
apt-get -f install
```Lots of fixes you can do while in chroot of a install.
Remember to run a to find your sdaX # to start. Use your own partition #
```
sudo fdisk -l
``` (lower case L)
It will tell you your sda number sda1, sda2, sda5 whatever the install is yours.

---

### Post by vecvan on 2010-09-23
thanks so much <3
it worked, i had to chmod sudoers after i edited it again

---

