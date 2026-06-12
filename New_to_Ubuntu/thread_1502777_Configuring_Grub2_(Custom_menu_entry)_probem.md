---
title: "Configuring Grub2 (Custom menu entry) probem"
date: 2010-06-06
forum: New to Ubuntu
---

### Post by okanagansage on 2010-06-06
I`m trying to create a custom menu entry in grub2 using the directions on the Grub2 help page: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)  . 

So I copy a menu entry from the /boot/grub/grub.cfg file and copy it into the 40_custom file located in /etc/grub.d  .  Then I change how the entry will be displayed by changing what is written after 'menuentry'. I also add a command in that menu entry after where it says 'quiet splash'. I am adding 'acpi=force' to fix a problem I'm having with the computer not fully shutting down (which is the reason I am doing this in the first place). 

When I try to save the changes, I get a message that says "Can't open file to write". 

Can someone please tell me what I'm doing wrong? I'm using Xubuntu 9.10 on a Compaq Presario that I have dual-booted with Windows 98.

---

### Post by mikewhatever on 2010-06-06
/etc/grub.d/40_custom is a system file and hence right protected. You can open it for editing with the following command:
```
gksudo gedit /etc/grub.d/40_custom
```

---

### Post by okanagansage on 2010-06-06
40_custom opens automatically after entering that command?

I've entered it into terminal and nothing happens.

---

### Post by geoffjay on 2010-06-06
If you're just trying to add an option to the kernel startup defaults you should run

$ sudo vim /etc/default/grub

(use nano if you don't know vim) and add them to the line GRUB_CMDLINE_LINUX_DEFAULT="..."

After you save and close run the command

$ sudo update-grub2

and reboot if there were no errors.

---

### Post by okanagansage on 2010-06-06
Thanks for the replies. 

Geoffjay, I tried what you said. Editing with nano seemed to work but updating grub2 gave me an error: /etc/default/grub: 9: acpi=force: not found . 

I'm accessing the forums on my hp desktop. The compaq (with xubuntu) is not currently online. Does this make a difference?

---

### Post by mikewhatever on 2010-06-06
> **okanagansage said:**
> 40_custom opens automatically after entering that command?

I've entered it into terminal and nothing happens.

That's odd. It should ask for your password and then open the file for editing in gedit. Perhaps there is a typo?

---

### Post by okanagansage on 2010-06-06
Mikewhatever, 

I checked it again. No typos. I was asked for a password for the sudo nano command.

---

### Post by mikewhatever on 2010-06-06
> **okanagansage said:**
> Mikewhatever, 

I checked it again. No typos. I was asked for a password for the sudo nano command.

Nano is fine too, and I might know what the problem is. Xubuntu, if that's what you are using, has Mousepad instead of Gedit. It should have been
```
gksudo mousepad /etc/grub.d/40_custom
```

---

### Post by geoffjay on 2010-06-06
Can you post the contents of the file /etc/default/grub from the PC that you're trying to fix?

I added acpi=force to mine as

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"

and was able to update without error.

---

### Post by okanagansage on 2010-06-06
Geoffjay, 

Thanks for the example. I had created separate quotation marks instead of just using the ones that were there. It updated now. Now I just have to try shutdown to see if it shuts down fully. 

Thanks to everyone for the help!

---

### Post by okanagansage on 2010-06-06
It shut down properly. Sweet. :)

---

