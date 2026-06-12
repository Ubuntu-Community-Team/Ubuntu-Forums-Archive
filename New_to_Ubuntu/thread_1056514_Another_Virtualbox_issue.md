---
title: "Another Virtualbox issue"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by eilios on 2009-01-31
No drivers? I check my hardware drivers, but it says there are none and I have no way of installing them. =(


Edit: Solved, thanks for all help =D

---

### Post by jimmy the saint on 2009-01-31
open a terminal and type

```
sudo /etc/init.d/virtualbox setup 
```

This will rebuild the kernel module and you should be fine

---

### Post by niteshifter on 2009-01-31
Hi,

A little more info please. Drivers for the Host OS or the Guest OS? And what OSes are we talking about? What version of Vbox? What are you trying to do?

---

### Post by eilios on 2009-01-31
> **niteshifter said:**
> Hi,

A little more info please. Drivers for the Host OS or the Guest OS? And what OSes are we talking about? What version of Vbox? What are you trying to do?
Newest version of Vbox, Guest OS, and i'm trying to install graphics drivers so I can run some 3d programs.

Also: I am installing the guest OS packages as we speak, it should go on fine.

---

### Post by 3rdalbum on 2009-01-31
You need the guest editions (which I gather is what you are installing). Virtual machines don't get direct access to your graphics card, which is why no restricted drivers appear in the Hardware Drivers program.

---

### Post by albinootje on 2009-01-31
> **eilios said:**
> Newest version of Vbox, Guest OS, and i'm trying to install graphics drivers so I can run some 3d programs.

Also: I am installing the guest OS packages as we speak, it should go on fine.

VirtualBox uses a virtual video card, and only recently you can do 3D things in VirtualBox with some MS-Windows guest VMs, and nothing else so far.

---

### Post by eilios on 2009-01-31
Ok, found out part of my problem, there is a text file that says

```

Sun xVM VirtualBox Guest Additions 
 
Where have the Windows drivers gone? 
- The Windows Guest Additions drivers were removed from this directory to 
  save space on your hard drive. To get the files you have to extract them 
  from the Windows Guest Additions installers: 
 
  To extract the 32-bit drivers to "C:\Drivers", do the following: 
  VBoxWindowsAdditions-x86 /extract /D=C:\Drivers 
 
  For the 64-bit drivers: 
  VBoxWindowsAdditions-amd64 /extract /D=C:\Drivers 
 
  Note: The extraction routine will create an additional sub directory 
  with the selected architecture (x86 or amd64) to prevent mixing up 
  the drivers. 
 
  To get further help with the command line parameteres of the installer, 
  type: VBoxWindowsAdditions-<arch> /? 

```
But those doesn't work. Any idea on what to do?

---

### Post by albinootje on 2009-01-31
> **eilios said:**
> Ok, found out part of my problem, there is a text file that says
--- cut ---
But those doesn't work. Any idea on what to do?

In another thread you wrote that you've successfully installed the Guest Additions in an Ubuntu guest VM.
Is this, what you're referring to, in another (MS-Windows) guest VM ?

---

### Post by eilios on 2009-01-31
> **albinootje said:**
> In another thread you wrote that you've successfully installed the Guest Additions in an Ubuntu guest VM.
Is this, what you're referring to, in another (MS-Windows) guest VM ?
Well, not really. I was able to get into it sucessfully, I never said I installed it, I said it was working. The end part cut it off a bit. :(

---

### Post by eilios on 2009-01-31
Any help would be appreciated, i'm having a lot of trouble.

---

### Post by albinootje on 2009-01-31
> **eilios said:**
> Well, not really. I was able to get into it sucessfully, I never said I installed it, I said it was working. The end part cut it off a bit. :(

Not sure what you mean exactly, but did you restart the guest VM ?
And did you resize the window it's running in to get a higher resolution ?

---

### Post by eilios on 2009-01-31
Edit: Still nothing. :/

---

### Post by eilios on 2009-02-01
This topic may be a bit old, but all the drivers(and my full screen ability) is in a .run file, and I have tried using terminal commands to open it. I think I may have used the wrong command. :P

---

