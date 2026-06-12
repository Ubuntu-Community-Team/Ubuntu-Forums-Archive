---
title: "Problems Installing!"
date: 2011-03-27
forum: New to Ubuntu
---

### Post by iXD on 2011-03-27
Ok, im trying to install the latest version on my laptop (10.10 i think). Currently on my laptop is Windows 7 and i want to dual boot it. It installs right, but when i goto run it, all i get is like a black BIOS screen with text and no images. Shows me a load of code then says:

'Ubuntu Login:' 

so i login and it stays with the code.. anyone help?

My laptop is a Sony Vaio. Please help!

---

### Post by want-to-believe on 2011-03-27
Did you download the desktop version or the server? It sounds like you've got the server version. At the prompt type 

sudo apt-get install gdm

Approve what it asks you, and then when it is done type gdm at the prompt. You should get a desktop. We can help you from there if that works.

---

### Post by iXD on 2011-03-27
I downloaded the desktop version.

Ill try that now and see what happens.

---

### Post by iXD on 2011-03-27
Ok, i did the install thing and typed gdm in, and it says:

WARNING **: Failed to aquie org.gnome.DisplayManager: Connection "1.10" is not allowed to own the service "org.gnome.DisplayManager" due to security policied in the configuration file

Any ideas?

---

### Post by want-to-believe on 2011-03-27
What happens when you type this:

sudo apt-get update

and next type this:

sudo apt-get upgrade

Any error messages?

---

### Post by iXD on 2011-03-27
Just burnt to a new disk, trying to install again, ill get back to you in a second.

---

### Post by oldfred on 2011-03-27
If you got to the sign on & command line you had a working system but without the gui - gnome.

Many recent versions need a parameter on the boot line to get the video modes to work.

Depending on video card/chip all most need is nomodeset or xforcevesa.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

---

