---
title: "Virtualbox doesn't work anymore after ubuntu re-install?!"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by kramer65 on 2009-01-04
Hello,


I did a re-install of ubuntu while keeping my home partition. I wanted to use virtualbox again so I installed it again. When I start it now however it says: 

[HTML]Failed to create the virtualbox com object.
The application will now terminate.

Could not load the settings file '/home/ricam/.VirtualBox/VirtualBox.xml' (VERR_OPEN_FAILED).
FATAL ERROR: Attribute 'version' has a value, '1.3-linux', that does not match its #FIXED value, '1.2-linux'
Location: '/home/kram/.VirtualBox/VirtualBox.xml', line 5, column 83.


Result Code: 
0x80004005
Component: 
VirtualBox
Interface: 
IVirtualBox {76b25f3c-15d4-4785-a9d3-adc6a462beec}[/HTML]

Does anybody know what I can do to solve this?

---

### Post by kramer65 on 2009-01-04
Ok, I got a bit further. I deleted uninstalled virtualbox, deleted the ~/.Virtualbox folder, and re-installed virtualbox again. 

I could now make a new virtual hard disc and started up. It now gives me another error however;

```
Failed to start the virtual machine Windows XP

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).

Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}
```

I checked my kernel; 2.6.24-22-generic

I then opened synaptic and searched for virtualbox. It gives me this long list of modules that go up to "virtualbox-ose module for linux-image-2.6.24-22-generic". (It is just one missing). It also has the option of installing "virtualbox-ose module for linux-image-generic". If I choose that it says it also needs to install the following:
linux-image-2.6.24-21-generic
virtualbox-ose-modules-2.6.24-21-generic

But do I need to install a whole new kernel for this? I am scared to mess everything up with that.. any help..?

---

### Post by Robotman on 2009-02-08
I see that second error message every time I update the Linux kernel.  I wish VB would update the kernel modules itself, but there is a way to do it manually.
Open a terminal and enter:
```
sudo apt-get install virtualbox-ose-modules-2.6.24-23-generic
```
Note the version number of the kernel.  I've had to do this every time I've updated the kernel since 2.6.24-19.  Change the number to whatever version you're running.  You can check by running the System Monitor application.
After the new kernel modules are installed, which takes seconds, VB should be up and running just like before.
If that doesn't work, you can choose to boot your computer using the previous version of the Linux kernel, if you have one available from the Grub boot menu.  That's what I had to do before I found the above fix.
Someone also suggested that I install VirtualBox 2, but I just went back to the Open-Source Edition version because VB2 ran painfully slow on my computer.  It might run better for you though... and you can install it through Synaptic Package Manager.

---

### Post by HermanAB on 2009-02-08
Hmm, the moral of the story is: If you use a virtualizer (VMware, Virtualbox, whatever), then don't update your host system if you can help it - unless you wish to re-install the schtoopidttt thing again.

Cheers,

Herman

---

