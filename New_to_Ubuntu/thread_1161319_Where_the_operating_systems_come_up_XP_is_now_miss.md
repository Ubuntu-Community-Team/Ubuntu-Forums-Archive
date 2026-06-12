---
title: "Where the operating systems come up XP is now missing"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by danielseyfried on 2009-05-16
When I turn on the Computer and the operating systems pop onto the screen
XP no longer is there and I can't get on with it.When I try other operating systems I get error 11. What can I do to fix this?

---

### Post by Didius Falco on 2009-05-16
Hi, welcome to the Ubuntu forums.

If you would, please, boot into your Live CD with the "make no changes to my computer" option. Once you are at the desktop, download the Boot Info Script in my signature to your desktop - you can do it from the CD.

After the script is on your desktop, open a Terminal shell, found at **Applications/Accessories/Terminal**
and type in the following:

```
sudo bash ~/Desktop/boot_info_script*.sh
```Running that script will generate a file to the desktop named **RESULTS.txt**. open that file, select all and copy it, then paste it in this thread. Highlight what you just posted and put code tags around it by clicking the hash (#) on the menu tool bar.

The contents of that file will help us to determine the problem, and more importantly, help us to find a solution to it.

Regards,

Didius

---

### Post by mikewhatever on 2009-05-16
It depends on how you got to that state. Can you tell what happened.

---

### Post by danielseyfried on 2009-05-16
The last thing I did that may have caused the problem was when I tryed to install Thunderbird

---

### Post by danielseyfried on 2009-05-16
I don't seem to be able to locate my signature, could please tell me where it is?   thanks

---

### Post by Dr.Vista on 2009-05-16
> **danielseyfried said:**
> I don't seem to be able to locate my signature, could please tell me where it is?   thanks
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by danielseyfried on 2009-05-16
This is want came up when I ran the sudo bashUsage:	bash [GNU long option] [option] ...
	bash [GNU long option] [option] script-file ...
GNU long options:
	--debug
	--debugger
	--dump-po-strings
	--dump-strings
	--help
	--init-file
	--login
	--noediting
	--noprofile
	--norc
	--posix
	--protected
	--rcfile
	--restricted
	--verbose
	--version
	--wordexp
Shell options:
	-irsD or -c command or -O shopt_option		(invocation only)
	-abefhkmnptuvxBCHP or -o option
danielseyfried@Seyfried-Family:~$ 

it doesn't look correct

---

### Post by Didius Falco on 2009-05-16
Nope, that isn't correct. <G> Assuming you have the boot info script downloaded to your desktop, open a Terminal shell, found at **Applications/Accessories/Terminal**
and type in the following:

        ```
sudo bash ~/Desktop/boot_info_script*.sh
```
 
Running that script will generate a file to the desktop named **RESULTS.txt**. open that file, select all and copy it, then paste it in this thread. Highlight what you just posted and put code tags around it by clicking the hash (#) on the menu tool bar.

If you haven't got the script, look at the bottom of this post and you'll find a link to it - it's the link that says - > Thanks, meierfra right behind it.

Sorry it took so long to get back to you - I have a lot going on right now.

Regards,

Didius

---

