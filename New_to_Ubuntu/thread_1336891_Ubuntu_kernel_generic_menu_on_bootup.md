---
title: "Ubuntu kernel generic menu on bootup"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by G-Com on 2009-11-25
Is there any way to disable it? :???:

Thank you. :)

---

### Post by Sealbhach on 2009-11-25
Are you using Ubuntu 9.10 or an earlier version?

.

---

### Post by G-Com on 2009-11-25
9.10.

Thank you for the quick response. :)

---

### Post by Sealbhach on 2009-11-25
Ok, you need to edit a config file to hide the menu. You can bring up that file by opening a terminal and running the command:
[B]
gksudo gedit /etc/default/grub[/B]

The file looks like this (see below). Simply delete the # before the GRUB_HIDDEN_TIMEOUT line.

Save and close, then run 

[B]sudo update-grub
[/B]
If for some reason later, you need to see the menu hold down the Shift key after booting and it will display the menu as normal.


```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
[COLOR=Red]#[/COLOR]GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="[COLOR=Black]3[/COLOR]"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys 			 		
```

.

---

### Post by G-Com on 2009-11-25
Thank you so much. :)  I will try this.

---

### Post by G-Com on 2009-11-25
Problem: all the **gksudo gedit /etc/default/grub **command does is open a blank gedit window. :(

---

### Post by Sealbhach on 2009-11-25
Well, that's strange, that's the location of the file given in the Ubuntu documentation:

[https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202")

Did you copy and paste the command? I'm thinking maybe you did a typo.

EDIT: you can also install Startup Manager, which will allow you to easily change the timeout:

**sudo apt-get install startupmanager**

.

---

### Post by G-Com on 2009-11-25
> **Sealbhach said:**
> Well, that's strange, that's the location of the file given in the Ubuntu documentation:

[https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202](https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202)

Did you copy and paste the command? I'm thinking maybe you did a typo.

EDIT: you can also install Startup Manager, which will allow you to easily change the timeout:

**sudo apt-get install startupmanager**

.
I copied and pasted it.  I tried it several times.

I'll try the Startup Manager app.

---

### Post by G-Com on 2009-11-25
I got rid of it. However, it's rather slow to book and a lot of text appears.

---

### Post by liquider on 2009-11-25
You can also edit
> 
/boot/grub/menu.lst

to resemble
```

...
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		0
...

```
You would have to edit this after each kernel upgrade, though.

---

### Post by G-Com on 2009-11-25
Thanks, Liquider.

I did a restart to see if it was quicker.  It was.  I just need to reduce the delay.

The assistance is appreciated.  :)

---

### Post by Sealbhach on 2009-11-25
> **liquider said:**
> You can also edit

to resemble
```

...
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        0
...

```You would have to edit this after each kernel upgrade, though.


He's using 9.10 so I assume he's got Grub2 so there wouldn't be a menu.lst.

.

---

### Post by lotharmat on 2009-11-25
Unless he upgraded...

---

### Post by Paqman on 2009-11-25
Check the version of Grub you've got. If it says "Grub 1.97 beta4" at the top then you've got Grub 2. Otherwise you've got Grub 1 in which case you should edit /boot/grub/menu.lst (or just use startupmanager)

---

### Post by G-Com on 2009-11-26
> **Paqman said:**
> Check the version of Grub you've got. If it says "Grub 1.97 beta4" at the top then you've got Grub 2. Otherwise you've got Grub 1 in which case you should edit /boot/grub/menu.lst (or just use startupmanager)
I'm using StartupManager.

Thanks again everyone. :)

---

