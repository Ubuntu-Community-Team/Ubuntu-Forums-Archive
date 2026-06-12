---
title: "Destroyed Laptop / Ubuntu install"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by RichardCL on 2009-03-05
Hi there,

I've got an old Medion Laptop with AMD ML30 processor. The screen is half dead, the DVD is broken (literally) and the system hangs on bios not booting. The BIOS has no USB boot option.

I've demounted the hard disk and can read no problems using a USB-IDE connector on my desktop. Now I'd like to use what is left of the system as a media centre under Ubuntu.

How do I manually install or prepare the harddrive? Can I use uunetboot to install Ubuntu on the harddrive via the USB connection from my desktop? If so do I use the Live version? I guess I need to run install afterward but can I run install to the hard drive from the hard drive? Do I need to create and install partition first for the Uunetboot and if so, how do I change the bootable partition after the install?

Is there a way to easily remote control the system from my desktop?


Thanks in advance?


Richard

---

### Post by swoody on 2009-03-05
> **RichardCL said:**
> I've demounted the hard disk and can read no problems using a USB-IDE connector on my desktop. Now I'd like to use what is left of the system as a media centre under Ubuntu.

How do I manually install or prepare the harddrive? Can I use uunetboot to install Ubuntu on the harddrive via the USB connection from my desktop? If so do I use the Live version? I guess I need to run install afterward but can I run install to the hard drive from the hard drive? Do I need to create and install partition first for the Uunetboot and if so, how do I change the bootable partition after the install?

Is there a way to easily remote control the system from my deskop?

As long as your computer recognizes the laptop drive as an actual hard-disk, this should be pretty simple. You should be able to reboot your desktop to a livecd or Unetbootin. Then you install as normal, but make sure under 'Partitioning' that you select 'Manual' and make sure all the options for the harddrive you don't want to install to are unselected! If you accidentally select a partition on your Desktop HDD it will erase lots of info PERMANENTLY so make sure you're careful! To make things easier and stress-free, remove your Desktop HDD, completely from the computer before you install. Then install as usual to the new hard disk. This way, there's no doubt about keeping your Desktop HDD intact, and you install fully to the new drive.

Try this out, and let me know how it works out for you :)

---

### Post by RichardCL on 2009-03-07
Hi there,

Good point. I should have thought of that.

I first tried with my laptop, which didn't work because I got Kernel/hardware errors. I need to install x64 Ubuntu and I'm protected from doing that on my x32 laptop.

Then I tried with my x64 laptop. Everything went fine and the install worked. I just get too many options in Grub when booting (gives me the option to boot to sda1 (the hard disk of my desktop, which of course isn't there). I'll have to take a look into how to remove the false options later.

Just the problem now that my wireless isn't recognised. I wonder if that comes from it not being present during install (the desktop wireless adapter is a different one).

Thanks again.

---

### Post by mike555 on 2009-03-07
You could install "startup manager" on Ubuntu from the package manager , then use it to set boot options .......

---

