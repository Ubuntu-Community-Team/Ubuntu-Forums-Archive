---
title: "choosing which os to boot"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by launchy on 2010-05-07
[SIZE=2]hi i installed lucyd lynx via wubi inside my c drive where vista is currently running as well. Whenever i turn on the computer, i am presented with 2 choices to boot: vista and ubuntu. when i select ubuntu, another "choose what os" is showing. is this normal or is there some way to get rid of the second choosing option screen?[/SIZE]

---

### Post by emoguitarist06 on 2010-05-07
> **launchy said:**
> [SIZE=1]hi i installed lucyd lynx via wubi inside my c drive where vista is currently running as well. Whenever i turn on the computer, i am presented with 2 choices to boot: vista and ubuntu. when i select ubuntu, another "choose what os" is showing. is this normal or is there some way to get rid of the second choosing option screen?[/SIZE]

I've never ran wubi (mainly because it's within windows which means viruses can attack it) however that Does not sound normal

What does it show after you choose Ubuntu?
Does it give you like a couple of kernels and a recovery and memtest?
if so then I guess that may be a wubi thing

---

### Post by launchy on 2010-05-07
[SIZE=2]it gives me another list something like this:
1. ubuntu linux generic kernel (latest)
2. [/SIZE][SIZE=2]ubuntu linux generic kernel (older one)
3. ubuntu mem test
4. windows vista on /sda2

as far as i remember from my latest boot


[/SIZE]

---

### Post by mikewhatever on 2010-05-07
Let's look at the output of **cat /etc/default/grub**, which is the grub's configuration file.

---

### Post by launchy on 2010-05-07
> **mikewhatever said:**
> Let's look at the output of **cat //etc/default/grub**, which is the grub's configuration file.
[SIZE=2]
where cn i access it?
[/SIZE]

---

### Post by launchy on 2010-05-08
[SIZE=2]i believe this is the one u are looking for

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
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

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
[/SIZE]

---

### Post by mikewhatever on 2010-05-08
Yes, that's the right output. It's somewhat puzzling why you get the second boot menu screen, perhaps it is because Windows is detected as the other OS. ([More here]("https://help.ubuntu.com/community/Grub2#/etc/default/grub%20%28file%29")) You could try disabling the other OS probber:

```
echo "GRUB_DISABLE_OS_PROBER=true" | sudo tee -a /etc/default/grub && sudo update-grub
```

---

### Post by uRock on 2010-05-08
I agree, it looks like grub recognized windows when running its configuration.

---

### Post by launchy on 2010-05-08
[SIZE=2]btw i also experienced this problem when i finished installing ubuntu and running the updates through update manager:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576622](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576622)
i dont know if its related but i wanted to point it out as well.
[/SIZE]

---

### Post by oldfred on 2010-05-08
Wubi is in the windows partition and as such has to use the windows boot loader to boot. Once in Ubuntu then you get the standard grub boot menu. So having two menus is normal, the first is from windows and the second is grub.

You can adjust the timeouts in the grub file posted above so you do not normally see it. Use shift key to show it once hidden. If you make timeout too short it may be difficult to get menu.

General info:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by launchy on 2010-05-08
[SIZE=2]> **oldfred said:**
> Wubi is in the windows partition and as such has to use the windows boot loader to boot. Once in Ubuntu then you get the standard grub boot menu. So having two menus is normal, the first is from windows and the second is grub.

You can adjust the timeouts in the grub file posted above so you do not normally see it. Use shift key to show it once hidden. If you make timeout too short it may be difficult to get menu.[/SIZE]> **oldfred said:**
>  [SIZE=2]

General info:[/SIZE] [SIZE=2]
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)[/SIZE] [SIZE=2]
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)[/SIZE] [SIZE=2]

thank u for clearing this out for me! now it makes sense that vista and ubuntu has their own separate boot loaders. i was actually looking at the same links that u posted while waiting for answers. again i appreciate it! menu is gone now! 
[/SIZE]

---

### Post by mikewhatever on 2010-05-08
> **launchy said:**
> [SIZE=2][/SIZE][SIZE=2]

thank u for clearing this out for me! now it makes sense that vista and ubuntu has their own separate boot loaders. i was actually looking at the same links that u posted while waiting for answers. again i appreciate it! menu is gone now! 
[/SIZE]

Well, I am confused. Aren't you gonna tell us what you did to make the menu gone?

---

### Post by uRock on 2010-05-08
> **mikewhatever said:**
> Well, I am confused. Aren't you gonna tell us what you did to make the menu gone?
I am thinking he/she is just clicking the kernel when the list come up and goes with it.

---

### Post by launchy on 2010-05-08
[SIZE=2]> **mikewhatever said:**
> Well, I am confused. Aren't you gonna tell us what you did to make the menu gone?

i did this code:

[/SIZE][SIZE=2]cat /etc/default/grub | grep 'GRUB_TIMEOUT='   # Checks current TIMEOUT value.
sudo sed 's/GRUB_TIMEOUT=5/GRUB_TIMEOUT=**T**/g' -i /etc/default/grub  # Change TIMEOUT value. Replace **T** with new value.[/SIZE][SIZE=2]

replaced the timeout to 0.

from [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[/SIZE]

---

### Post by uRock on 2010-05-08
Awesome!

---

### Post by frillybob on 2010-05-08
press f6 and run eithor acpi or acpi=off it just controls the fans

---

