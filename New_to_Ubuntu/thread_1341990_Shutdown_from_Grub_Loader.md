---
title: "Shutdown from Grub Loader"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by kakashi_12 on 2009-11-30
Does anyone know a command to shutdown FROM the Grub Loader?
 
Reason I'm asking is because I'm dual booted with Win and Linux and I restart a lot. Sometimes I restart mistakenly when I actually mean to shut down. So instead of booting up all the way, I could just go into the command line FROM the grub, by hitting "C" for command. And then typing commands. The reboot command works. But I haven't figured out yet a cmd for shutdown, powerdown, poweroff, or anything like that. Anyone?

---

### Post by neurostu on 2009-11-30
control+alt+delete usually works to restart, or you can just press the power button to turn off.

---

### Post by wirate on 2009-11-30
what about hitting the power button :)

---

### Post by ankspo71 on 2009-11-30
Hi,
when working from the terminal I use:

```
sudo shutdown -h now
```open your terminal and type this for more details:
```
shutdown --help
```James

---

### Post by fromthehill on 2009-11-30
found something
edit: tested, it works
add these entries to menu.lst (this does not work with karmic)
after the ### END AUTOMAGIC KERNEL LIST 

```
title Halt
halt

title Reboot
reboot 
```

I think these entries should work with karmic as well but I wouldn't know how to add them in grub2

---

### Post by ukripper on 2009-11-30
i use my toe to hit the power button on my machine placed under the desk before it even leaves grub screen.

---

### Post by oldfred on 2009-11-30
For old grub these were the entries for menu.lst as named, I have not found the equivalent for new grub2 yet. I like to put these at the end of menu.lst since I had several menus chainbooted.


title   Reboot
reboot

title   Halt
halt

---

### Post by kakashi_12 on 2009-11-30
power button is BAD. only used if a must!
 
I read on the forum hear, that halt does not mean shutdown. it only means halt... like sleeping.

---

### Post by kakashi_12 on 2009-11-30
Nevermind. I got it finally! :)
 
I tried the sudo shutdown -d now command
unrecognized command. That's the thing... a lot of the cmds that work in the OS, do not work in the grub. I wonder what the -d means. Then I tried without the -d, then without the now, etc.
 
Then for the heck of it, I did try the Halt command, with no variables/options. Just halt by itself. And it worked! So that's the answer to my question: halt
 
But I know I remember reading on this forum that someone said it only put it to sleep or something, but for me it shut it down. idk.
 
Thanks guys.

---

### Post by Gwasanaethau on 2009-11-30
> **kakashi_12 said:**
> power button is BAD. only used if a must!
 
I read on the forum hear, that halt does not mean shutdown. it only means halt... like sleeping.

I believe at this stage nothing from the hard disc has been loaded into RAM (at least not in a writable sense). The power button *should* be OK for turning off the computer from the GRUB menu.

Halt can mean different things depending on the hardware and OS. From Ubuntu, my desktop will suspend upon issuing **halt**, but my laptop will shut down. Both will shut down from Arch upon issuing **halt**.

---

### Post by b0b138 on 2009-11-30
In karmic you need to edit /etc/grub.d/40_custom and add ```
menuentry "Reboot" {
	reboot
}
```
then run sudo update-grub. This will work for reboot or halt

---

