---
title: "Problem installing Scanner using Brother DCP375CW all in one printer"
date: 2010-04-01
forum: New to Ubuntu
---

### Post by bosun1000 on 2010-04-01
Help please. I am trying to install the scanner on the above printer (printing side works fine) in Ubuntu version 8.04 Hardy Heron I have installed XSane and the scanner driver brscan3.2.9-1.i386.deb also the Scan-key-tool brscan-skey-0.2.1-3.i386.deb but when I open Xsane to scan I get the message "failed to open device 'brother3:bus4;dev2':invalid argument" would somebody kindly tell me how to cure this problem if there is any code to write in the terminal would you kindly post it?
Thank you in advance.
Bosun

---

### Post by plucky on 2010-04-01
Is this USB connected or wireless?

---

### Post by bosun1000 on 2010-04-01
Plucky 
Thanks for your reply.
USB at the moment, eventually I hope to get it wireless also Lan Connected.

Bosun

---

### Post by plucky on 2010-04-01
Did you install **sane-utils** from the repositories?

Look [here](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#9) for instructions to get your scanner working in Hardy.

Good Luck

---

### Post by bosun1000 on 2010-04-01
> **plucky said:**
> Did you install **sane-utils** from the repositories?

Look [here](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#9) for instructions to get your scanner working in Hardy.

Good Luck

Yes sane-utils installed.
I've looked at" [here](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#9) for instructions to get your scanner working in Hardy." 
but do not understand what I need to enter into the terminal would you be kind enough to post the code required?
Thank you & sorry to be so dumb!
Bosun

---

### Post by Andavane on 2010-04-01
I have the Brother DCP-7010L and had identical problems to yours.
The page plucky pointed you to is the correct page: the key is there.
You need to locate that file and the place in that file and edit the file.
Chaning the "0664" to "0666" is the change in Hardy which gets the scanner working.

---

### Post by plucky on 2010-04-01
> **bosun1000 said:**
> Yes sane-utils installed.
I've looked at" [here](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#9) for instructions to get your scanner working in Hardy." 
but do not understand what I need to enter into the terminal would you be kind enough to post the code required?
Thank you & sorry to be so dumb!
Bosun

```
gksudo gedit /etc/udev/rules.d/40-basic-permissions.rules
```

And look for > # USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664"
SUBSYSTEM=="usb_device",                MODE="0664"


Change the value 0664 to 0666 on both lines.

Then reboot

Good Luck

---

### Post by bosun1000 on 2010-04-01
Deep Joy!!!
Thanks to everybody for helping me install my Scanner, particularly Plucky thank you for your patience & understanding.
Bosun

---

### Post by Andavane on 2010-04-02
> **bosun1000 said:**
> Deep Joy!!!
Thanks to everybody for helping me install my Scanner, particularly Plucky thank you for your patience & understanding.
Bosun

I second that :D

I'd just like to underline again, that the solution which Plucky gave for your scanner also works for my DCP-7010L, so I expect the same solution wil work for other scanners in the line.

Enjoy your Ubuntu-ing!

---

### Post by bosun1000 on 2010-04-02
> **Andavane said:**
> I second that :D

I'd just like to underline again, that the solution which Plucky gave for your scanner also works for my DCP-7010L, so I expect the same solution wil work for other scanners in the line.

Enjoy your Ubuntu-ing!

Yes thanks Andavane your remark is duly noted I have already saved this thread for future reference as I usually use Brother printers.
Thanks once again
Bosun

---

### Post by Andavane on 2010-04-02
Me too.
I also keep this thread tagged:

[http://ubuntuforums.org/showthread.php?t=934943]("http://ubuntuforums.org/showthread.php?t=934943")

as I went through a lot of grief with it, and didn't want anyone else tearing out their hair like I did.

Anyway, all's well now! :D

--andavane

---

