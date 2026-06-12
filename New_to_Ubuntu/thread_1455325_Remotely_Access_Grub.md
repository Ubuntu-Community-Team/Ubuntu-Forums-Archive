---
title: "Remotely Access Grub"
date: 2010-04-15
forum: New to Ubuntu
---

### Post by imthemark on 2010-04-15
Hey there,
I'm quite new to Linux and have come into a bit of a problem here.
I have a multiboot Grub with W7 and Karmic.
I normally do Wake On Lan and since W7 ist def. I use TeamViewer to access my PC.
But sometimes I need Linux.
Is there any possibility to connect to Grub (Timeout to zero so he'll prolly wait) and choose the OS which should boot?
Thanks!

---

### Post by falconindy on 2010-04-15
The only way to get direct remote access to Grub is to use a serial console. The only thing running on the system when Grub loads is Grub, so you're at its mercy.

---

### Post by cuberts on 2010-04-15
> **imthemark said:**
> Hey there,
I'm quite new to Linux and have come into a bit of a problem here.
I have a multiboot Grub with W7 and Karmic.
I normally do Wake On Lan and since W7 ist def. I use TeamViewer to access my PC.
But sometimes I need Linux.
Is there any possibility to connect to Grub (Timeout to zero so he'll prolly wait) and choose the OS which should boot?
Thanks!Well you will have to have the actual file installed before you can Open Grub itself. So do that, or burn it on a CD that helps
Well I hoped this helped!

---

### Post by imthemark on 2010-04-15
> **cuberts said:**
> Well you will have to have the actual file installed before you can Open Grub itself. So do that, or burn it on a CD that helps
Well I hoped this helped!

What file do you mean? Can't say I can follow you :)
Do I need to boot from USB or Smthg first?

---

### Post by btindie on 2010-12-27
For other coming across this thread looking for a solution to this, here's what I did.
 
As mentioned previously, when Grub starts the only access you have to it is either via the console or serial port. If you've got a server with a BMC port then that's not so bad as you can access the serial port via Serial-Over-LAN but desktop systems don't have this.
 
The best option would be to have the system always boot into Linux, from there you can set which entry you'd like it to boot into on the next reboot by using the grub-reboot command. Then just reboot as normal. If you're running a full desktop system this could be quite a slow process if you just want to get into windows..
 
So you could add a minimal rescue image as the default entry where it's only purpose is to allow you remote SSH access and to run the command grub-reboot to set the entry for the next reboot. That way the process shouldn't take that long. You could probably get away with creating a custom entry in Grub that uses the existing Ubuntu install and create an entry that boots into text mode by appending 'text' to the kernel options. 'single' user mode / recovery mode wouldn't be an option as that doesn't start networking / openssh. Just remember to install the openssh-server package!
 
[https://help.ubuntu.com/community/Grub2#Configuring GRUB 2](https://help.ubuntu.com/community/Grub2#Configuring GRUB 2)

---

