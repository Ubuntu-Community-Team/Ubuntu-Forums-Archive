---
title: "[F11] Installing NVIDIA"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by Couto on 2009-08-14
Hey, I just switched from Ubuntu to Fedora, but I'm so used to .deb files now I'm stuck on installing the NVIDIA package I downloaded.

Could you guys give me the commands to run the install?

The package is on my desktop and it's named "NVIDIA-Linux-x86_64-190.18-pkg2.run"

Thank you for the help!

---

### Post by Couto on 2009-08-14
Anybody?

---

### Post by bhaverkamp on 2009-08-15
sh *.run

Note you need to run this with your x server shutdown. so it needs to be run from a console.

---

### Post by Couto on 2009-08-15
> **bhaverkamp said:**
> sh *.run

Note you need to run this with your x server shutdown. so it needs to be run from a console.

How do I run in console mode? :/

---

### Post by Garyhans on 2009-08-15
Just download Envy out of synaptic. Envy will install your Nvidia drivers for you.

---

### Post by |Porsche on 2009-08-15
Hit Ctrl+Alt+F1 to go to console. 
Type:
"sudo /etc/init.d/gdm stop" to stop your X server.
"sh NVIDIA-*.run"
Go through the installer.
start Gnome by typing "/etc/init.d/gdm start"
You are done.

---

### Post by Crunchy the Headcrab on 2009-08-15
> **|Porsche said:**
> Hit Ctrl+Alt+F1 to go to console. 
Type:
"sudo /etc/init.d/gdm stop" to stop your X server.
"sh NVIDIA-*.run"
Go through the installer.
start Gnome by typing "/etc/init.d/gdm start"
You are done.
That doesn't work in Fedora 11.  For one the Desktop Environment uses TTY1 and for another gdm start/stop is non-existant

> **Couto said:**
> How do I run in console mode? :/
I'm using Fedora 11 too.  I think it's great.  Play by play:

1. logout or restart your pc
2. push ctrl-alt-f2
3. type: su (if you'd rather use sudo I can show you how to set up your sudoers file)
4. enter root password
5. type: init 3
6. At this point you may need to hit ctrl-alt-f2 again as it might have switched you to tty1 and you want to stay in tty2 so that you don't have to login again
7. type: cd Desktop
8. type: bash NVIDIA-Linux-x86_64-190.18-pkg2.run
9. type: reboot (easiest way to close out your superuser session and start gdm at the same time).

Sidenote:  The people at RPM fusion maintain packages of Nvidia drivers for Fedora.  If you'd prefer to download an RPM package from their repositories see this: [http://forums.fedoraforum.org/showthread.php?t=204752](http://forums.fedoraforum.org/showthread.php?t=204752)

---

### Post by |Porsche on 2009-08-15
> **Crunchy the Headcrab said:**
> That doesn't work in Fedora 11.  For one the Desktop Environment uses TTY1 and for another gdm start/stop is non-existant


I'm using Fedora 11 too.  I think it's great.  Play by play:

1. logout or restart your pc
2. push ctrl-alt-f2
3. su (if you'd rather use sudo I can show you how to set up your sudoers file)
4. enter root password
5. type: init 3
6. At this point you may need to hit ctrl-alt-f2 again as it might have switched you to tty1 and you want to stay in tty2 so that you don't have to login again
7. cd Desktop
8. bash NVIDIA-Linux-x86_64-190.18-pkg2.run
9. type: reboot (easiest way to close out your superuser session and start gdm at the same time).

Opps... I thought the change was from Fedora to Ubuntu. Good Catch.

---

### Post by Couto on 2009-08-15
> **Garyhans said:**
> Just download Envy out of synaptic. Envy will install your Nvidia drivers for you.

There is no Synaptic in Fedora.

---

### Post by Couto on 2009-08-15
> **Crunchy the Headcrab said:**
> That doesn't work in Fedora 11.  For one the Desktop Environment uses TTY1 and for another gdm start/stop is non-existant


I'm using Fedora 11 too.  I think it's great.  Play by play:

1. logout or restart your pc
2. push ctrl-alt-f2
3. type: su (if you'd rather use sudo I can show you how to set up your sudoers file)
4. enter root password
5. type: init 3
6. At this point you may need to hit ctrl-alt-f2 again as it might have switched you to tty1 and you want to stay in tty2 so that you don't have to login again
7. type: cd Desktop
8. type: bash NVIDIA-Linux-x86_64-190.18-pkg2.run
9. type: reboot (easiest way to close out your superuser session and start gdm at the same time).

Sidenote:  The people at RPM fusion maintain packages of Nvidia drivers for Fedora.  If you'd prefer to download an RPM package from their repositories see this: [http://forums.fedoraforum.org/showthread.php?t=204752](http://forums.fedoraforum.org/showthread.php?t=204752)

I'll try this.

---

### Post by Crunchy the Headcrab on 2009-08-15
If you like synaptic you could use Yummex.  It's a gui for Yum.  I like Yum so much that I just always use the terminal to do everything.  If you install presto you can save time on updates by only downloading the changes instead of the whole package every time you update something.

yum install presto

The preferred way to install nvidia drivers according to most fedora users is the repository in that link I gave you.  It automatically updates your driver when new ones come out or when your kernel is updated.  It usually is updated very quickly.  Or you could be like me and just do the method I posted earlier.

---

### Post by Crunchy the Headcrab on 2009-08-21
Sorry just thought of something else.  If you are going to compile your own driver you will need the gcc and kernel-devel packages.

> yum install kernel-devel gcc

You need to have them installed before you run that process I showed you earlier.

---

### Post by karth83 on 2009-08-21
Nvidia you can easily Install from synaptic by enabling proprietary software in the Software Sources List.

You need not download anything from Nvidia's Site. Synaptic will do.

ANother easy way. Go to System -> Hardware Drivers - Here you can easily enable the Nvidia Driver.

---

