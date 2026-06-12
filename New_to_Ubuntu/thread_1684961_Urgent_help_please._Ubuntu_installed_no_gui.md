---
title: "Urgent help please. Ubuntu installed no gui"
date: 2011-02-09
forum: New to Ubuntu
---

### Post by dont tch meh on 2011-02-09
I installed ubuntu on an hp pavillion with a 9.0.4 live disk or around that update i dont exactly remember i am a newbie have ubuntu on my every day computer and it runs amazing ive learned a litle about terminal n such but here is my problem:
       ```
GNU GRUB version 1.98+20100804-5ubuntu3
Ubuntu, with linux 2.6.35-24-generic
Ubuntu, with linux 2.6.35-24-generic (recovery mode)
Ubuntu, with linux 2.6.35-22-generis
Ubuntu, with linux 2.6.35-22-generic (recovery mode

Use the up and down arrow keys to slect which entry is highlighted. Press enter to boot the selected OS, 'e' to edit the commands before booting or 'c' for a command line.
```

If i choose any of these is just jump through alot of text and numbers down the screen and get to end...i enter help or commands and it says (inittrans) please help this is a computer i really need to get running

---

### Post by Ocxic on 2011-02-09
Choose:
Ubuntu, with linux 2.6.35-24-generic (recovery mode)

and when you get to a terminal type:
"apt-get update && apt-get dist-upgrade"  and if there are no errors type "reboot"

that should update your system and help fix anything that might not have installed properly

---

### Post by dont tch meh on 2011-02-09
/bin/sh: apt-get: not found


...yah that happened

---

### Post by dont tch meh on 2011-02-09
i made a usb 2.0 with ubuntu 10.10 and inserted it and booted from that. im at the screen where it gives option to either try or install. and when i hit install il just sits there twirling with the ubuntu thinking simbol. we have done this coutnless times and nothing happens

---

### Post by amsterdamharu on 2011-02-10
When you boot from the usb and highlight the "try ubuntu" option can you press tab to edit the menu entry?

Remove quiet splash from the boot options and boot, now you should see some output to the screen and maybe some messages that will help us fix the problem.

Pressing control + alt + F1,F2,F3... could show different outputs as well.

---

### Post by PunkLV on 2011-02-10
There might be, a slight chance though, that, assunimgly GDM, has trouble loading your locale or language for destop enviroment. 
I am probably wrong, however.

---

