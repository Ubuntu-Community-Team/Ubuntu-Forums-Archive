---
title: "nvidia 9.04 install issues"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by conbon100101 on 2009-05-08
Hello.  I'm trying to set up 9.04.  I haven't updated in a long time, I'm still back before 7.04 >.< Most everything went smooth except for my nvidia driver.  When I try to install it, all seems to go well until I restart then I hit a black screen and can't really do anything.  I'd like to get it to work because I know it's a good graphics card and running at 800x600 is really irritating when I use to get far better.

I haven't used the terminal in a while (I won't lie) so if there is terminal work, please break this down for me.  It's really been a while since I did any of this.

Thank you!

---

### Post by presence1960 on 2009-05-08
> **conbon100101 said:**
> Hello.  I'm trying to set up 9.04.  I haven't updated in a long time, I'm still back before 7.04 >.< Most everything went smooth except for my nvidia driver.  When I try to install it, all seems to go well until I restart then I hit a black screen and can't really do anything.  I'd like to get it to work because I know it's a good graphics card and running at 800x600 is really irritating when I use to get far better.

I haven't used the terminal in a while (I won't lie) so if there is terminal work, please break this down for me.  It's really been a while since I did any of this.

Thank you!

Try booting into recovery mode. Once in scroll down and choose "Try to auto repair graphics problems". This should get you up again, at which point you can look into why your Nvidia driver is causing this problem.

---

### Post by Kareeser on 2009-05-08
How did you install the nvidia driver?

---

### Post by conbon100101 on 2009-05-08
> **Kareeser said:**
> How did you install the nvidia driver?


I tried installing it through the hardware drivers.

---

### Post by Kareeser on 2009-05-08
Try the instructions detailed here:
[http://ubuntu.kareeser.com/?p=44](http://ubuntu.kareeser.com/?p=44)

---

### Post by djuke04 on 2009-05-08
Hi,
  I'm also having this problem with the driver.  I followed the instructions linked below, and the terminal says first that it cannot find the address in the "wget" command, which I've checked is correct as well as verified that my network connection is fine.

  Anyways, I downloaded the file, stuck it on my desktop, then proceeded with your instructions, heading to terminal (Alt+Ctrl+F1) then sudo /etc....stop.

At this point I rtype the "sh NVIDIA-Linux......." command and it says "sh: Can't open NVIDIA-Linux...."

What am I doing wrong here?

---

### Post by Kareeser on 2009-05-08
When you run /etc/init.d/gdm stop, it shuts off the X windows system.

You then need to navigate to the folder where you downloaded the file, which is where you ran the "wget" command...

There is where you run "sudo sh"

---

### Post by djuke04 on 2009-05-08
Alright,
  So bearing in mind I'm new to this, if I move the file I downloaded to the Home folder, how do I navigate there with the terminal?

  And then once I'm in that directory I just type "sh FILE NAME (whatever it is)"??

---

### Post by Kareeser on 2009-05-08
You should already be there once you log in in the terminal. Are you sure it's in the Home folder? If you downloaded it through firefox, it sits in the Desktop by default.

You can go there by typing "cd ~/Desktop".

After that, yes, you can run "sudo sh NVIDIA...", make sure you append "sudo" to this command, as the script requires administrative privileges to run properly.

---

### Post by djuke04 on 2009-05-08
Alright!
  It's running! Thanks so much, you have been most helpful.  

Now for another question.  

  During the setup it asks "Install NVIDIA's 32-bit compativility OpenGL libraries?"

Is that going to interfere with my 64-bit system? Or is it just for "Compatibility?"

---

### Post by Kareeser on 2009-05-08
Correct, they're for compatibility. You can install them without issue.

---

### Post by djuke04 on 2009-05-08
Alright,
  More problems here...

  I installed everything and restarted the computer.  It says now:

Ubuntu is running in low-graphics mode

The following error was encountered.  You may need to update your configuration to solve this.

(EE) Failed to load module "type1" (module does not exist, 0)
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module!
Please ensure
(EE) NVIDIA(0): that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0): that the NVIDIA device files have been created properly.
(EE) NVIDIA(0): Please consult the NVIDIA README for details.
(EE) NVIDIA(0): ***Aborting***
(EE) Screen(s) found, but none have a usable configuration.


What the heck happened?

---

### Post by Kareeser on 2009-05-08
Odd. Have you checked to make sure that the driver you downloaded supports your graphics card model?

In the meantime, you can roll back the changes by running the same command, but appending --uninstall to the end.

---

### Post by djuke04 on 2009-05-08
Perhaps some new and pertinent information:

I started it in low graphics mode so I could get into System> Preferences> NVIDIA X Server Settings - I thought perhaps I could find more options in there.... or something.  But when it opened it says this:

"You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run 'nvidia-xconfig' as root), and restart the X server."

It says all of that, even the part in parentheses.

Also, NVIDIA's website says this is the right driver for my card, to be sure.

---

### Post by Kareeser on 2009-05-08
The part I don't understand is that the nvidia install script should have set up xorg automatically.

What happens when you run nvidia-xconfig like the error says?

You can just run this command in the terminal, in the Application -> Accessories menu

---

### Post by djuke04 on 2009-05-09
when I run "sudo nvidia-xconfig" in terminal, it says it made a new configuration, then I:

sudo /etc/init.d/gdm restart

to restart it

and it comes up with:

"There already appears to be an X server running on display :0. Should another display number by tried? Answering no will cause GDM to attempt starting the server on :0 again.  (You can change consoles by pressing Ctrl-Alt plus a function key, such as Crtl-Alt-F7 to go to console 7.  X servers usually run on consoles 7 and higher."

I've found this screen twice before, and if I pick Yes, it starts ubuntu in low graphics mode, with the same low graphics mode text boxes at startup.  If I choose No, it comes back to this same window.  

At this particular instance it's chosen to freeze.

---

### Post by djuke04 on 2009-05-09
I found this in the README on the NVIDIA download website:

> 
   My X server fails to start, and my X log file contains the error:
   
  (EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
   
  The X driver will abort with this error message if the NVIDIA kernel module fails to load. If you receive this error, you should check the output of dmesg for kernel error messages and/or attempt to load the kernel module explicitly with modprobe nvidia. If unresolved symbols are reported, then the kernel module was most likely built against a Linux kernel source tree (or kernel headers) for a kernel revision or configuration that doesn't match the running kernel.
   
  You can specify the location of the kernel source tree (or headers) when you install the NVIDIA driver using the --kernel-source-path command line option (see sh NVIDIA-Linux-x86_64-180.51-pkg1.run --advanced-options for details).
   
  Old versions of the module-init-tools include modprobe binaries that report an error when instructed to load a module that's already loaded into the kernel. Please upgrade your module-init-tools if you receive an error message to this effect.
   
  The X server reads /proc/sys/kernel/modprobe to determine the path to the modprobe utility and falls back to /sbin/modprobe if the file doesn't exist. Please make sure that this path is valid and refers to a modprobe binary compatible with the Linux kernel running on your system.
   
  [FONT=&quot]The "LoadKernelModule" X driver option can be used to change the default behavior and disable kernel module auto-loading.[/FONT]
Is this relevant to my situation?

---

### Post by Kareeser on 2009-05-09
With regard to the first post: Instead of restarting GDM, did you try rebooting instead?

Using modprobe is not my specialty, so I am not sure whether that error message pertains to you. Sorry.

---

### Post by CyDharttha on 2009-05-10
Thought I'd add my experience to this.. in 9.04, my friend had problems, fresh install, after turning on nvidia driver in hardware drivers dialog, restarting, he gets a black screen w/ a white box in the middle. After troubleshooting a while, I decided to try driver from nvidia.com. It was very important to uninstall ubuntu's nvidia package first (don't want old kernel module loading for version 180.44), and I uninstalled nvidia-common also for good measure, as well as cleaning out unneeded nvidia packages afterwards:

```

apt-get remove nvidia-glx-180 nvidia-common
apt-get autoremove

```

reboot after this.

The worse thing in 9.04, once I did this, go to install driver from nvidia.com, it can't find where to put the libraries. So I append some options:

```
sh NVIDIA-Linux-x86-180.51-pkg1.run --x-module-path=/usr/lib/xorg/modules --x-library-path=/usr/lib/xorg/modules
```

now /etc/init.d/gdm (re)start, all was good on this system again.

---

### Post by djuke04 on 2009-05-11
Thanks for your help and responses! 

I managed to get the driver from NVIDIA's website "working." the reason for the quotes is that it works, but...

I still have no sound.  Every application that makes a sound freezes.  Video won't even play.  Songs don't play, and the programs have to be force quitted.  

I went into System>Preferences>Sound, and try to change some options, but when I hit "Test," it says:

"audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Failed to connect stream: Invalid argument"

So where should I even start to troubleshoot this? And what might any of you make of that error?

---

