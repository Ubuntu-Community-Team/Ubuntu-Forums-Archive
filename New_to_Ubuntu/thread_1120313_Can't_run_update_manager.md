---
title: "Can't run update manager"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by Notrefervousa on 2009-04-08
I got this error message when trying to run update manager.....any ideas?
Before this i tried to get my sound card to work and after that nothing but errors.

> Failed to run /usr/sbin/synaptic '--hide-main-window' '--non-interactive' '--parent-window-id' '85983235' '-o' 'Synaptic::closeZvt=true' '--progress-str' 'Please wait, this can take some time.' '--finish-str' 'Update is complete' '--set-selections-file' '/tmp/tmpBtOygp' as user root.

---

### Post by fabricator4 on 2009-04-09
> **Notrefervousa said:**
> I got this error message when trying to run update manager.....any ideas?
Before this i tried to get my sound card to work and after that nothing but errors.

I don't have file in my /tmp directory called tmp*anything, Even when there _are_ packages to be installed.  You could try deleting that file, perhaps.  I think tmp is a virtual location that disappears when you reboot in any case, so if all else fails you could try that.

Chris.

---

### Post by Michael.Godawski on 2009-04-09
> **Notrefervousa said:**
> I got this error message when trying to run update manager.....any ideas?
Before this i tried to get my sound card to work and after that nothing but errors.

hi Notrefervousa, 

do you remember what commands you have used or what guide you have followed while tweaking your sound card?

Perhaps we can deduce from that what went awry.
If you do not remember no problem: all your commands are logged.

All your commmands started with sudo, executed with root privileges are stored in this log:
     /var/log/auth.log


     You can either access it by System - Administration - System Log - auth.log, or by typing into the terminal
 ```
gedit /var/log/auth.log
```     

There is also a log which stores every command you type into the terminal. It is located here:
     ~/.bash_history
     So open it with ```
gedit ~/.bash_history
``` and have a look at all your commands used so far.

---

### Post by Jakey_TheSnake on 2009-04-09
As a side note, that's Synaptic Package Manager, the Update Manager is run by using this command:

```
/usr/bin/update-manager
```

edit: try re-installing synaptic? 

```
sudo apt-get remove synaptic
sudo apt-get install synaptic
```

---

### Post by Notrefervousa on 2009-04-09
Michael.Godawski:

When i try to run gedit /var/log/auth.log in terminal it says that > Could not open /var/log/auth.log.  You do not have the permissions necessary to open the file.

i did run gedit ~/.bash_history in terminal, This is part of my history to where i think that i screwed it up
> sudo chmod 776 /etc/modprobe.d/blacklist
sudo cat /lib/linux-sound-base/noALSA.modprobe.conf >> /etc/modprobe.d/blacklist

sudo chmod 776 /etc/modprobe.d/blacklist
sudo cat /lib/linux-sound-bas/noALSA.modprobe.conf >> /etc/modprobe.d/blackilst
groups
sudo gedit /etc/group
usermod -g audio tommy
ls -la /dev/snd
dpkg -l linux-ubuntu-modules-2.6.22-14-386
dpkg -l linux-ubuntu-modules-*
sudo apt-get install linux-ubuntu-modules-2.6.22-14-386
ls -la /dev/snd
sudo usermod -g tommy -G audio tommy
sudo diff /etc/group /etc/group-
adduser [user] audio
adduser [tommy] audio

Any ideas?


Jakey_TheSnake:

I can open up update manager from System > Administration > Update Manager but when i try to install updates after I type in my Password it gives me that error.

I aswell tried to remove and install synaptic, but,
> Tommy is not in the sudoers file. This incident will be reported.

---

### Post by Dileeshvar on 2009-04-10
use the sudo command to
execute the file you are
trying to access /var/log/auth.log
it will give you permission only when you 
use sudo command 

cheers.

---

### Post by Notrefervousa on 2009-04-11
i used the sudo command but still nothing, still tells me > Tommy is not in the sudoers file.  This incident will be reported.

---

### Post by zvacet on 2009-04-12
Do you have just one account (one you created during install) or you have two accounts?If you have two one have admin privileges and other not.If that ic source of your problem then just switch users.If you just one account and you can not perform sudo then try to add user to admin group booting in recoveryy mode and type 

```
sudo adduser Tommy admin
```

---

### Post by Notrefervousa on 2009-04-13
Thanks so much zvacet it worked!

---

