---
title: "Ubuntu boots to Command Prompt"
date: 2010-09-13
forum: New to Ubuntu
---

### Post by thenetminder33 on 2010-09-13
Hi, I am brand new to linux and ubuntu. I just installed ubuntu into a dual boot setup with Windows today. However, when i select ubuntu on the dual boot menu, it displays the pink ubuntu screen with loading dots then switches to a command prompt screen with a login prompt.

After reading previous posts. I used the command: ```
startx
```

It works, however i am looking for a way to bypass this by possibly adding a command to the boot code or something of that sort.

Also, when I try to shut down, restart, etc. in ubuntu, it wont let my click the power button in the upper right of desktop. When i use ctrl+alt+del the shut down and restart commands are faded and do not respond.

Many thanks for any help

---

### Post by wojox on 2010-09-13
Sounds like something got borked up. Try:

```
sudo apt-get install -f
```

Is this Ubuntu 10.04 Lucid Lynx you installed?

---

### Post by thenetminder33 on 2010-09-13
not sure about exact version, but i just downloaded the ISO file from official ubuntu site about a week or two ago and burned it onto a CD-R which i used to install

---

### Post by thenetminder33 on 2010-09-13
I tried the command you supplied me with, and, unfortunately, it did not help. The command executed and returned a line about o found, 0 updates etc.

---

### Post by wojox on 2010-09-13
What does this return:

```
lsb_release -a
```


Also try:

```
sudo apt-get install ubuntu-desktop
```

---

### Post by thenetminder33 on 2010-09-13
The first command returns:
```

No LSB modules are available.
Ditributor ID: Ubuntu
Description  : Ubuntu 10.04.1 LTS
Release      : 10.04
Codename     : lucid

```

The second command returned something along the lines of
```
ubuntu-desktop is already the newest
```

---

### Post by wojox on 2010-09-13
The only other thing I could think to do is 

Open Startup Applications and +Add

Fill it in like this, +Add it and restart.

---

### Post by wojox on 2010-09-13
> Also, when I try to shut down, restart, etc. in ubuntu, it wont let my click the power button in the upper right of desktop. When i use ctrl+alt+del the shut down and restart commands are faded and do not respond.

So I'm afraid to ask, how do you shutdown?  :)

---

### Post by thenetminder33 on 2010-09-14
I was unable to find the startup applications folders, where is it?


Also, unfortunately i have had to use the power and reset buttons on my case when in linux. I used  ctrl alt del in command prompt

---

### Post by thenetminder33 on 2010-09-14
anyone else have ideas on how to bypass this??

---

### Post by wojox on 2010-09-15
> **thenetminder33 said:**
> I was unable to find the startup applications folders, where is it?

Not the folder. Go to System &#8211;> Preferences &#8211;> Startup Applications.



Try shutting it down by opening a terminal and

```
sudo shutdown -h now
```

Or reboot

```
sudo shutdown -r now
```

---

### Post by thenetminder33 on 2010-09-15
The startup application fix did not work, however the terminal shutdowns do

---

### Post by thenetminder33 on 2010-09-18
I reinstalled with brand new Live CD and all problems were installed

---

