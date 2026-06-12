---
title: "ubuntu boots to blank screen"
date: 2010-02-16
forum: New to Ubuntu
---

### Post by guerilla on 2010-02-16
hello, ive just installed 9.10 on my pc everything went fine and when i boot it goes to grub and i can select my windows install or ubuntu. when i click ubuntu though it boots into a blank screen

what has gone wrong?

---

### Post by Satoru-san on 2010-02-16
> **guerilla said:**
> hello, ive just installed 9.10 on my pc everything went fine and when i boot it goes to grub and i can select my windows install or ubuntu. when i click ubuntu though it boots into a blank screen

what has gone wrong?
Did you happen to do an update before you shut down your computer last?

Also try hitting escape when it goes to a black screen, this may have debug information that will help us help you.

---

### Post by guerilla on 2010-02-16
it happened on first install

the error is something like 

piix4simbus conflicts with acpi region sor1

---

### Post by Satoru-san on 2010-02-16
is that a laptop?

---

### Post by guerilla on 2010-02-16
no a desktop, its the first time installing on this one, ive used ubuntu on others before

---

### Post by Satoru-san on 2010-02-16
Looks like you are not alone. I will do some more research, but this should give you something to google for.

[http://ubuntuforums.org/showthread.php?t=1317602](http://ubuntuforums.org/showthread.php?t=1317602)

---

### Post by guerilla on 2010-02-18
i found this bug which relates at
[https://bugs.launchpad.net/ubuntu/+s...ux/+bug/444235](https://bugs.launchpad.net/ubuntu/+s...ux/+bug/444235)

from what ive read it seems like it solved but i dont know how, can anyone help?

---

### Post by guerilla on 2010-02-20
anybody?

---

### Post by Paddy Landau on 2010-02-20
Did it work when you tested from the Live CD?

I don't know the answer, guerilla, but here are three suggestions.

[LIST]
[*]Ensure that your Live CD is valid by running the option to test the CD.
[*] Search the forums for how to turn off acpi in the grub2. It may work, but I can't guarantee it.
[*] Wait until 10.04 comes out in about three months.
[/LIST]

---

### Post by _khAttAm_ on 2010-02-20
Did you try the recovery mode? What happens when you do?


Anyways, here's what I can think of:
-try updating BIOS
-try changing ACPI settings from BIOS.

---

### Post by guerilla on 2010-02-21
Thanks for helping.

ive verified that the cd is okay and i also tried installing from usb stick just in case.

ive also disabled acpi in my bios and then used the no acpi kernal, but i still had the same problem.

dont know what revcovery mode, how do i try it?

---

### Post by Paddy Landau on 2010-02-21
> **guerilla said:**
> dont know what revcovery mode, how do i try it?
When you turn on the computer, you get a  prompt asking you what to boot into: Windows or Ubuntu.

The top option is the Ubuntu 9.10. The final option is Windows.

The second option from the top is Ubuntu 9.10, but in recovery mode. When you boot, it will not start the X Windows (i.e. the GUI), but instead take you to the terminal prompt.

I don't know what you'd do from there; someone else with more knowledge than I would have to help you.

---

