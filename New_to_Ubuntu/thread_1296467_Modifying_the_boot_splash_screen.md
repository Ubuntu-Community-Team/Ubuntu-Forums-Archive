---
title: "Modifying the boot splash screen"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by Living2007 on 2009-10-20
When I boot my Ubuntu, and the splash screens pops up, i notice that it is stretched. The boots screens res is at 1280x1024, and my monitors native res is 1680x1050. How do i get the boot screen to match my native res?

---

### Post by martrn on 2009-10-20
This would be a complicated answer for anyone to give.  I would leave it as it is.

When x11 starts it changes the screen resolution, so that x11 can handle the scree  but before that grub sets a screen resolution dependent on the frame buffer for storing graphical content for example items such as the screen.

See : [http://ubuntuforums.org/showthread.php?p=1541970]("http://ubuntuforums.org/showthread.php?p=1541970") in the tutorials section for a fuller explanation.

You have to follow the thred all the way through to work out the difficulties people have had with certain resolutions and the various outcomes.  The resolution '1280x1024' is a good well supported resolution hence the possible reason your computer boots up with that resolution.

---

### Post by ajgreeny on 2009-10-20
There are various codes for frame-buffer resolutions that may help.  I have absolutely no idea what that res would be, but the others would be as shown below.

Open your GRUB configuration file.  sudo gedit /boot/grub/menu.lst
To proceed, you'll need to know the framebuffer code for your desired resolution:    

Resolution
vga=785        640x480
vga=788        800x600
vga=791        1024x768
vga=794        1280x1024
vga=870        1280x800

Automatic (and update-proof) GRUB Configuration:  Find the line
# defoptions=quiet splash

and add your framebuffer resolution code, e.g. (for 1024x768)

# defoptions=quiet splash vga=791

Save the file, then execute  sudo update-grub

---

### Post by Unanimated on 2009-10-20
You can also search Synaptic for a program called Startup-Manager. It basically offers a GUI for editing the menu.lst file, and includes a function for saving the config file to a floppy, changing the splash screen and resolution of it, how many kernels show up in the list, etc. After installing, it shows up under **System** > **Administration**.

---

### Post by Living2007 on 2009-10-20
> **Unanimated said:**
> You can also search Synaptic for a program called Startup-Manager. It basically offers a GUI for editing the menu.lst file, and includes a function for saving the config file to a floppy, changing the splash screen and resolution of it, how many kernels show up in the list, etc. After installing, it shows up under **System** > **Administration**.
 is there a way to edit the boot splash screen directly?

---

