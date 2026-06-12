---
title: "root password?"
date: 2011-05-25
forum: New to Ubuntu
---

### Post by mkornig on 2011-05-25
Hi,

I've just installed Ubuntu 10.04 32bit on my computer. I want to use it with a Lexmark X2670 printer.

I've found a suitable driver for this printer on Lexmark's website. I've downloaded the driver successfully to my harddisk. When executing the installer wizzard asks EXPLICITLY for the the root password.

MY user password (I'm the ONLY user of the system so far) won't work.

**Questions**: 

[LIST=1]
[*]What's the root password? I've never set it.
[*]Is there some kind of default root password?
[*]Is there another way to install the driver?
[/LIST]
Any help appreciated.

---

### Post by soylentcola on 2011-05-25
As far as my research goes, there doesn't seem to be a default root password, on Ubuntu root is just kind of a catch all for administrative tasks, so you don't do something on accident and screw up your system, try leaving it blank? (If you haven't tried so already?)

Otherwise (and I don't think this is a good idea) you can open a terminal and set the root password yourself by typing:

```
sudo passwd
```

It'll ask you to enter your password (since you used sudo) then you can enter the new root password.  Though again, I don't recommend it due to system safety issues.

As for the driver thing...I generally just connect to the printer (since mine is on a network) and Ubuntu does it's best to find a suitable driver for me.  If you don't feel comfortable editing the root password, you can try that and see how it goes.

---

### Post by terrykiwi83 on 2011-05-25
How are you installing it, are you using 'sudo'? etc

If your installing via terminal you must put sudo before the text.

Sudo password is the same as your ubuntu login password

hope that helps

---

### Post by mkornig on 2011-05-25
Here are two screen dumps before and after entering some root password (which I don't know).

---

### Post by terrykiwi83 on 2011-05-25
have you tried entering your ubuntu login password?

---

### Post by sisco311 on 2011-05-25
> **mkornig said:**
> Here are two screen dumps before and after entering some root password (which I don't know).

Yep, the Lexmark `driver' is not Ubuntu friendly. It prompts for the root password, which is locked, by default in Ubuntu. Ubuntu uses sudo (Check out: [uhelp]community/RootSudo[/uhelp])

But the `driver' should work in Ubuntu too.

Just open a terminal (Applications -> Accessories -> Terminal) and type:
```
sudo
```
then press a space, drag and drop the lexmark-*.zip file in the terminal window and press enter. You will be prompted for your password. Type it in (NOTE: sudo will not provide any visual feedback, that's normal) and press enter again. Then follow the  instructions...

---

### Post by zealibib slaughter on 2011-05-25
> Just open a terminal (Applications -> Accessories -> Terminal) and type:
```
sudo
```
then press a space, drag and drop the lexmark-*.zip file in the terminal window and press enter. You will be prompted for your password. Type it in (NOTE: sudo will not provide any visual feedback, that's normal) and press enter again. Then follow the instructions...
 
 
not to get off topic but thats cool, never knew you could drag and drop in terminal.

---

### Post by mkornig on 2011-05-25
Thanks for your help and coments, everybody!

I've actually installed the printer by doing the following:

[LIST=1]
[*]connect as a user with root/admin privileges
[*]open a terminal
[*]go the directory in which the driver installation file *sh is located
[*]submit the command: *sudo ./*sh*
[/LIST]
*...*and then, big surprise, the driver wizzard didn't ask for the root password any more.

Lexmark printer prints fine now.

---

