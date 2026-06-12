---
title: "Really dumb question about terminal"
date: 2009-08-29
forum: New to Ubuntu
---

### Post by barnaclebill18 on 2009-08-29
Hello,

New to Ubuntu and have been trying to figure out how to use the terminal.

This is all pretty confusing to me as I am an old guy who only started using computers recently.

I have been copy and pasting short commands to see what happens, I saw an article about installing Start Up Manager and tried to follow the instructions.

Anyway, after trying to start it, the terminal said I must be root to run this program.

I kind of think I know what root is but I thought I was root since I am the only one using this computer and I thought I set it up so I would always have all rights.

Please don't get too technical, this stuff is hard for me to figure out.

Thanks for any help.

---

### Post by drs305 on 2009-08-29
Here is a good explanation:
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

As the first user, you have admin *rights* - you can gain temporary control of the system, but you don't have control all the time. 

To run commands as 'root', you preface the command with "sudo". To start graphical apps as 'root', use 'gksudo'.
```

sudo blkid
gksudo gedit

```
[http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

Welcome to Ubuntu and the Ubuntu forums, by the way!  :-)

---

### Post by NoaHall on 2009-08-29
In front of command, type "sudo"
So, for example, I would use
"sudo apt-get install start-up-manager"
It will then ask for my password, and i must fill it in, and press enter (notice, you won't be able to see your password as you type)
It will then install!

---

### Post by halitech on 2009-08-29
By default, the Root account is actually disabled in Ubuntu so instead of logging in as root, you use SUDO which gives the user temp rights to do administrative tasks. 

As the first user, you do but you don't have admin rights unless you invoke them with sudo.

ie. sudo apt-get update will work but apt-get update will fail.

---

### Post by Penguin Guy on 2009-08-29
You are *admin*, not root. To become root temporarily you have to type [COLOR="Green"]sudo[/COLOR] before a command and enter your password when prompted. This is so you can't delete your whole system by accident.

root - Can do anything.
admin - Can do anything after entering their password.
user - Can't do much.

---

### Post by philinux on 2009-08-29
> **barnaclebill18 said:**
> Hello,

New to Ubuntu and have been trying to figure out how to use the terminal.

This is all pretty confusing to me as I am an old guy who only started using computers recently.

I have been copy and pasting short commands to see what happens, I saw an article about installing Start Up Manager and tried to follow the instructions.

Anyway, after trying to start it, the terminal said I must be root to run this program.

I kind of think I know what root is but I thought I was root since I am the only one using this computer and I thought I set it up so I would always have all rights.

Please don't get too technical, this stuff is hard for me to figure out.

Thanks for any help.

To start startupmanager have a look under System>Admin you'll find it's put a menu item in there.

---

### Post by barnaclebill18 on 2009-08-29
Thank you for the quick replies.

I think I got it now, about this question, anyway.

I looked and now it is in the menu.

Thanks.

---

### Post by fitgene on 2009-08-29
hiii
just try this link[ http://www.ubuntupocketguide.com]("http://www.ubuntupocketguide.com/")/
its a pocket guide for ubuntu beginnners
it tells you from the scrap
i use it
a great stuff indeed

---

### Post by lyni on 2009-08-30
you may like to look at these links. keep them handy.
[https://help.ubuntu.com/](https://help.ubuntu.com/)
[http://www.linux.org/lessons/](http://www.linux.org/lessons/)
[http://linuxcommand.org/index.php](http://linuxcommand.org/index.php)
enjoy your ubuntu

---

### Post by MelDJ on 2009-08-30
i hope this is helpful :)

[http://fosswire.com/post/2007/08/unixlinux-command-cheat-sheet/](http://fosswire.com/post/2007/08/unixlinux-command-cheat-sheet/)

---

