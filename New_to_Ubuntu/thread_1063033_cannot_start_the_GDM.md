---
title: "cannot start the GDM"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by benzodiaz on 2009-02-07
Hi,

There is an error that seems pretty common:

Cannot start the X server (your graphical environment)...

old interface appearing and the login option is accessible.

I think that this error is due to the resolution since everything was working fine, then I used my tv as a monitor for the first time, and ke blam.

I cannot use startx, it says that the directory is read only or locked. 

Also, I tried sudo apt-get remove xserver-xorg
which worked but i cannot now sudo apt-get update or install xserver-xorg

i am not sure how to access the graphics options

any help would be useful.

Thankyou

---

### Post by Mitch9654 on 2009-02-07
Try using Ubuntu's installation disk to repair...
(I think there is some good stuff in there...)

or there is some terminal code I have heard before
(great help, aren't I?)

Mitch9654

---

### Post by benzodiaz on 2009-02-07
I am not sure how to access the repair tool from the install disk.
I think that I should try to install, manually, and choose the sda5 where the kernel is installed on? Or should i choose swap?

cheers.

---

### Post by kansasnoob on 2009-02-07
I don't see how the Live CD would help you! So forget that for the moment.

After you restart the system (in your case you'll probably have to do a "hard" restart) wait until the system/BIOS screen has passed and you should have 3 seconds to access GRUB by pressing the "esc" key on the keyboard.

Then you should see a series of options (the length will depend on how many kernel updates have been made), but choose the newest kernels "recovery mode". After recovery mode is done running you'll be presented with several options.

One of the options will be something along the lines of reconfigure xserver or xorg (sorry I can't remember the exact wording), but that's what you want to do.

As far as Live CD recovery read here:

[https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery)

---

### Post by anand77 on 2009-02-07
For me, the system did not even boot into text mode. After selecting the kernel to boot, all I saw for about 5-10 mins was just black screen. I was waiting to see whether it comes back alive as there was access to the hard drive. Since I had a huge update last time, I thought some script is running to configure few things. But after some time the hard drive access also stopped. The machine was powered and it was sitting idle. I kept hitting the enter key few times and then I hit Ctrl+Alt+Del. Then I saw gdm could not be started. And few messages. I did a hard reset by pressing and holding the power button. The system then rebooted. This time, no problem. It booted as if there was no problem the previous time :confused:

When I looked into the system log viewer under deamon log there were these messages:

```

Feb  7 10:44:48 anand-desktop gdmgreeter[5182]: Gtk-CRITICAL: gtk_tree_view_get_selection: assertion `GTK_IS_TREE_VIEW (tree_view)' failed 
Feb  7 10:44:48 anand-desktop gdmgreeter[5182]: Gtk-CRITICAL: gtk_tree_selection_unselect_all: assertion `GTK_IS_TREE_SELECTION (selection)' failed 
Feb  7 10:44:48 anand-desktop gdmgreeter[5182]: Gtk-CRITICAL: gtk_tree_selection_select_iter: assertion `GTK_IS_TREE_SELECTION (selection)' failed 
Feb  7 10:44:48 anand-desktop gdmgreeter[5182]: Gtk-CRITICAL: gtk_tree_view_scroll_to_cell: assertion `GTK_IS_TREE_VIEW (tree_view)' failed 
Feb  7 10:44:49 anand-desktop avahi-daemon[4591]: Registering new address record for fe80::213:20ff:fe35:b09c on eth0.*.
Feb  7 10:45:08 anand-desktop gnome-session[5267]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager' 
Feb  7 10:45:18 anand-desktop gnome-session[5267]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout 
Feb  7 10:45:28 anand-desktop gnome-session[5267]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout 
```

I am running Ubuntu Intrepid Ibex on a Dell dimension 3000. Has anyone encountered anything similar to this??? Any help to diagnose the problem is greatly appreciated.

---

### Post by benzodiaz on 2009-02-07
when i boot from recovery mode it says that it has to run a file check or something then when it gets to about 70%

Duplicate or bad block in use!

---

