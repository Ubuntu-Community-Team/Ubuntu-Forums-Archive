---
title: "Can't stop gdm"
date: 2010-01-29
forum: New to Ubuntu
---

### Post by klemperal on 2010-01-29
I'm going  little crazy here trying to stop gdm so I can install the Nvidia drivers from their website.  After dropping to the shell, I've tried the commands
```
sudo service gdm stop
```
```
sudo gdm stop
```
```
sudo stop gdm
```
```
sudo /etc/init.d/gdm stop
```
but none of them work for me.  Any suggestions?

---

### Post by mechro on 2010-01-29
Does logging out and changing session to Failsafe Terminal work?

---

### Post by drzoo2 on 2010-01-29
```
sudo /etc/init.d/gdm stop
```

This has always worked for me but I have not used anything past Jaunty.
What error(s) do you get one you run the command?

---

### Post by ratcheer on 2010-01-29
Are you in a system console terminal or just a regular shell terminal?

Tim

---

### Post by hemimaniac on 2010-01-29
anytime i have to do the nvidia dance i use

sudo telinit 3 from a terminal and then do the nvidia thing

---

### Post by birkopf on 2010-06-25
I have same problem. Sudo init.d gdm stop works on Jaunty and previous but not on Lucid. On Jaunty ma card gets recognised without problems, not on Lucid. Last on Jaunty I can install envy not on Lucid...

What about that GDM? 

Does ANYONE how to stop it from tty1 please?

---

### Post by birkopf on 2010-06-25
After 6h of google search that works for me:

To stop:

Sudo gdm-stop

To start:

Sudo service gdm start

---

### Post by afrodeity on 2010-07-13
bump

---

### Post by sisco311 on 2010-07-13
> **afrodeity said:**
> bump

If
```
sudo gdm-stop
```doesn't work, then reboot, hold down the Shift key until the grub menu shows up, highlight the *Recovery Mode* entry, press e for edit, replace **single** with **text** from the end of the *linux* line, then press Ctrl+x to boot.

---

### Post by afrodeity on 2010-07-13
> **sisco311 said:**
> If
```
sudo gdm-stop
```doesn't work, then reboot, hold down the Shift key until the grub menu shows up, highlight the *Recovery Mode* entry, press e for edit, replace **single** with **text** from the end of the *linux* line, then press Ctrl+x to boot.

Thought maybe this was the reason why I can't remove nvidia drivers, but starting up in text mode hasn't solved my problem:

```

sudo apt-get --purge remove nvidia*
[sudo] password for afrodeity: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting nvidia-glx-legacy-envy for regex 'nvidia*'
Note, selecting nvidia-180-libvdpau-dev for regex 'nvidia*'
Note, selecting nvidia-185-libvdpau-dev for regex 'nvidia*'
Note, selecting nvidia-glx-173-dev for regex 'nvidia*'
Note, selecting nvidia-current for regex 'nvidia*'
Note, selecting nvidia-libvdpau-ia32 for regex 'nvidia*'
Note, selecting nvidia-libvdpau1 for regex 'nvidia*'
Note, selecting nvidia-glx-dev for regex 'nvidia*'
Note, selecting nvidia-glx-185-dev for regex 'nvidia*'
Note, selecting nvidia-173 for regex 'nvidia*'
Note, selecting nvidia-settings for regex 'nvidia*'
Note, selecting nvidia-185-libvdpau for regex 'nvidia*'
Note, selecting nvidia-185-kernel-source for regex 'nvidia*'
Note, selecting nvidia-vdpau-driver for regex 'nvidia*'
Note, selecting nvidia-96-dev for regex 'nvidia*'
Note, selecting nvidia-cg-toolkit for regex 'nvidia*'
Note, selecting nvidia-96 for regex 'nvidia*'
Note, selecting nvidia-glx-new for regex 'nvidia*'
Note, selecting nvidia-glx-96-dev for regex 'nvidia*'
Note, selecting nvidia-glx-new-envy for regex 'nvidia*'
Note, selecting nvidia-glx-src for regex 'nvidia*'
Note, selecting nvidia-glx-173 for regex 'nvidia*'
Note, selecting nvidia-glx-180 for regex 'nvidia*'
Note, selecting nvidia-glx-177 for regex 'nvidia*'
Note, selecting nvidia-glx-185 for regex 'nvidia*'
Note, selecting nvidia-180-modaliases for regex 'nvidia*'
Note, selecting nvidia-kernel-common for regex 'nvidia*'
Note, selecting nvidia-libvdpau for regex 'nvidia*'
Note, selecting nvidia-current-dev for regex 'nvidia*'
Note, selecting nvidia-glx-71 for regex 'nvidia*'
Note, selecting nvidia-glx-96 for regex 'nvidia*'
Note, selecting nvidia-glx-180-dev for regex 'nvidia*'
Note, selecting nvidia-glx-envy for regex 'nvidia*'
Note, selecting nvidia-current-modaliases for regex 'nvidia*'
Note, selecting nvidia-173-modaliases for regex 'nvidia*'
Note, selecting nvidia-185-modaliases for regex 'nvidia*'
Note, selecting nvidia-glx-legacy for regex 'nvidia*'
Note, selecting nvidia-common for regex 'nvidia*'
Note, selecting nvidia-96-kernel-source for regex 'nvidia*'
Note, selecting nvidia-173-kernel-source for regex 'nvidia*'
Note, selecting nvidia-dev for regex 'nvidia*'
Note, selecting nvidia-current-dev instead of nvidia-dev
Note, selecting nvidia-180-kernel-source for regex 'nvidia*'
Note, selecting nvidia-libvdpau-dev for regex 'nvidia*'
Note, selecting nvidia-96-modaliases for regex 'nvidia*'
Note, selecting nvidia-glx for regex 'nvidia*'
Note, selecting nvidia-173-dev for regex 'nvidia*'
Note, selecting nvidia-180-libvdpau for regex 'nvidia*'
E: Couldn't find package nvidia*

```

sudo apt-get purge nvidia* also has same result. Has Lucid dumbed down all of a sudden and can't translate a wildcard vs regular expression?

---

### Post by afrodeity on 2010-07-13
Alright, here is the deal. If you do a manual install of NVIDIA drivers you have to purge only once. Thereafter, just leave out the step and manual installer will remove previous driver and install itself. Not exactly what one wants in terms of admin control, but it works for me.

---

### Post by brinktastee on 2011-01-08
> **sisco311 said:**
> If
```
sudo gdm-stop
```doesn't work, then reboot, hold down the Shift key until the grub menu shows up, highlight the *Recovery Mode* entry, press e for edit, replace **single** with **text** from the end of the *linux* line, then press Ctrl+x to boot.


Out of all the suggestions this is the only one that works with 10.10.
I needed to downgrade my NVidia driver to 256xx from 260xx because PrimeGrid fails on the new driver. Thanks Dude!:KS

sudo telinit 3 does not work.
sudo gdm-stop does not work.
sudo /etc/init.d/gdm stop does not work.
sudo service gdm stop does not work.
Something changed from 10.04 to 10.10 because all those used to work in 10.04 and prior.:confused:

---

