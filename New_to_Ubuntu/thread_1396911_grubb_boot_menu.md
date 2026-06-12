---
title: "grubb boot menu"
date: 2010-02-02
forum: New to Ubuntu
---

### Post by vnpifhf on 2010-02-02
when i start my machine up, i get the choice of windows vista, linux ubuntu and linux ubuntu recovery mode on this gnu grub thing

how do i make it autoboot without doing anything like windows used to do without that stupid annoying menu :P

and maybe if i wanted to dual boot to vista i could press a button (say f11) but it would autoboot anyway without the menu?
all help thanks!

---

### Post by drs305 on 2010-02-02
Take a look at this guide and come back if it doesn't answer your questions:
[Grub 2 -  5 Common Tasks]("http://ubuntuforums.org/showthread.php?t=1302743")

Look at the TIMEOUT and DEFAULT sections.

---

### Post by vnpifhf on 2010-02-02
sorry i dont get it where does the code go or something?

---

### Post by drs305 on 2010-02-02
The file you edit is /etc/default/grub.  It is a system file so you have to edit it as root.

Tell us what you want to do and provide the results of meierfra's [boot info script]("http://bootinfoscript.sourceforge.net/") (follow the instructions there) and we will tell you how to edit the file.

---

### Post by vnpifhf on 2010-02-02
i dont get it at ALL lol 

what do i do with the code

what is it!!

sorry i just dont do command prompt 
please just need a step by step guide

Thanks!

---

### Post by drs305 on 2010-02-02
Let's try this a different way. For basic tasks, Startup-Manager can still do the job in Grub legacy or Grub 2.

From Synaptic, find and install the package "startup-manager". (System, Administration, Synaptic Package Manager). I'm hoping you know how to install packages!

Once you have installed it, open it via "System, Administration, Startup-Manager".
It will spend some time reading your system. Wait until it finishes and shows it's interface.

In the "Boot" tab, set the timeout to 0 and select the OS you want to boot, then press "Close".

Let it complete the change and then reboot.

---

### Post by vnpifhf on 2010-02-02
i installed it /download but after it finished it said not all updates can be installed and nothing came up :(

---

### Post by drs305 on 2010-02-03
If you open a terminal as previously described and enter:
```
gksu startupmanager
```
Does it run? If not:
```

sudo apt-get install startupmanager

```
And try again.

If it doesn't work, please give us the error messages. You can copy the messages in the terminal by highlighting them and then pressing the middle mouse button into a post. You only have to highlight the message for it to be copied into memory. If you want to use the keyboard to copy/paste the data, highlight it and use CTRL-SHIFT-C to copy and then CTRL-V to paste the contents outside the terminal

---

