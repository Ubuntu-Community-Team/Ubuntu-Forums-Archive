---
title: "Resolution Issues."
date: 2008-12-27
forum: New to Ubuntu
---

### Post by leonhart83 on 2008-12-27
I am currently having issues with getting the bottom of applications to display on the screen. I am currently using xVM Virtual Box with the latest Ubuntu installation. I am running at the largest resolution possibel (800x600) and when I am trying to setup my email using evolution the forward button is below the bottom panel and I can't click it. I have removed the panel to see whether I can get to it but it is still below the screen. I can't put the application any higher up the screen either. Is there anyway to fix this with a scrollbar or something?

Thanks.

Micky.

---

### Post by billgoldberg on 2008-12-27
> **leonhart83 said:**
> I am currently having issues with getting the bottom of applications to display on the screen. I am currently using xVM Virtual Box with the latest Ubuntu installation. I am running at the largest resolution possibel (800x600) and when I am trying to setup my email using evolution the forward button is below the bottom panel and I can't click it. I have removed the panel to see whether I can get to it but it is still below the screen. I can't put the application any higher up the screen either. Is there anyway to fix this with a scrollbar or something?

Thanks.

Micky.

Well, resize the window to something smaller.

Or hold down alt and then drag the windows up.

That way you can move the application up.

---

### Post by RomeReactor on 2008-12-27
Hi. Also make sure you install the guest additions: run the virtual machine, wait until it boots all the way to the desktop, and (in the virtual machine) go to 'Devices->Install guest additions'. Then (still in the VM) log out and back in, or restart the virtual machine and see if you can now set a higher resolution.

---

### Post by leonhart83 on 2008-12-27
Thanks for the quick response.

I tried following this tutorial but I did not have any luck.

[http://ubuntu-tutorials.com/2007/10/13/installing-guest-additions-for-ubuntu-guests-in-virtualbox/](http://ubuntu-tutorials.com/2007/10/13/installing-guest-additions-for-ubuntu-guests-in-virtualbox/)

When running the command sudo bash ./VBoxLinux* it did not complete correctly. 

It come up with "Detected unsupported x86 environment".

I have a feeling that my setup is unsupported. :p

The alt idea suggested works as a band-aid solution. I can't resize the screen any smaller for some reason.

---

### Post by RomeReactor on 2008-12-27
> **leonhart83 said:**
> When running the command sudo bash ./VBoxLinux* it did not complete correctly. 

It come up with "Detected unsupported x86 environment".

You can check the name of the correct file by browsing the guest additions CD mounted in Ubuntu. Are you running Ubuntu 32 bit or 64 in VirtualBox?

---

### Post by leonhart83 on 2008-12-27
> **RomeReactor said:**
> You can check the name of the correct file by browsing the guest additions CD mounted in Ubuntu. Are you running Ubuntu 32 bit or 64 in VirtualBox?

I am running a 32bit virtual box.

Here is the output.
[COLOR="Red"]
****************************************************************
Verifying archive integrity... All Good.
Uncompressing VirtualBox 2.1.0 Guest Additons for Linux installation...................................................
VirtualBox 2.1.0 Guest Additions installation
Detected unsupported x86 environment
****************************************************************[/COLOR]

So from that output it seems like the file is on the cd. I am running a different command as we speak. Will let you know how it goes.

Micky.

---

### Post by leonhart83 on 2008-12-27
Solved. I must have been running the incorrect package. I could not read it properly because of the resolution issues.

Once I ran the correct package it is running smooth.

Thanks again guys.

---

