---
title: "Pendrive has files with lock symbols and I can't delete them"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by brawd on 2009-06-26
Hi,

I had this great idea - copy the Ubuntu files to my pendrive so I could boot from that on any machine.

So I did.

It didn't work, (nothing unusual there).

Now I have a load of file symbols whth padlocks taking a lot of room on my pendrive.

Can anyone tell me how to get rid of them please?

Can anyone tell me how to set up my pendrive to be bootable?

regards to all,

brawd

---

### Post by t0p on 2009-06-26
To delete the padlocked files, you need to have admin privileges.  Hit Alt+F2, and in the box that appears type

```
gksudo nautilus
```

Use the file manager window that appears to navigate to the usb stick in question.  You should now be able to delete them pesky files!

Be careful while using Nautilus with admin privs, and exit from the program as soon as you've done what you wanted to do.  It's possible to screw up your entire system if you inadverdently deleted the wrong files.

If you want to delete *everything* from the stick, you could use **gparted**. (This is a bit like using a pile driver to crack a walnut, and you must be careful when using the utility.  The devs have called gparted "a weapon of mass destruction"!  But you may as well get used to using gparted, as you'll likely want it to format and partition a drive that you want to put a bootable operating system on.) Hit Alt+F2 and type in the box that appears:

```
gksudo gparted
```

Now select the usb stick from the drop-down menu of drives, right-click and select to Unmount.  Click Apply.  Then select to format.  Choose a format type (eg ext3, fat16, etc... choose ext3 if you're going to put Ubuntu on the stick) and again click Apply.  Hey presto - an empty stick, formatted and ready for you to put Ubuntu on it.

If it turns out that you don't have gparted installed, type in a terminal

```
sudo apt-get install gparted
```

To make the stick bootable, you can also use gparted.  When you've opened the stick in gparted, look for the tab that says something like "Manage Flags" and then select the option called "boot".

A simple way to make a live usb stick is to use Ubuntu's **Create Startup USB**.  It's in **System > Administration** I think (I'm currently using Xubuntu Hardy, which doesn't have the utility).

---

### Post by starcraft.man on 2009-06-26
> **brawd said:**
> Hi,

I had this great idea - copy the Ubuntu files to my pendrive so I could boot from that on any machine.

So I did.

It didn't work, (nothing unusual there).

Now I have a load of file symbols whth padlocks taking a lot of room on my pendrive.

Can anyone tell me how to get rid of them please?


regards to all,

brawd
Quick and dirty way to get rid of them is to just start the file manager with root power. Push alt+F2 and type in and then return:
```
gksudo nautilus
```

Then navigate to pen drive and delete the files.

What happened is the files that were put on the drive are owned by the root user, with only your user power you can't remove them. Make sure to close this browser when done, it's ill advised to give root power to a file browser permanently.


> Can anyone tell me how to set up my pendrive to be bootable?

Ask and ye shall [receive.]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent") Explains everything needed to know, remember that there are limitations.

---

### Post by brawd on 2009-06-26
Thank you everybody, it is all fixed.

Now I must find out apbout these new (for me) commands.

brawd

---

### Post by ajgreeny on 2009-06-26
Be aware that if you just hit the delete button when you were using nautilus as user or root, the files will just have been put into that trash.  You will still be wasting that file space unless you empty the trash, which for root is not so obvious, but is in /root/.local/share/Trash/files directory, I think.

If you did just send the files to trash and want to get rid of them completely, use ```
gksudo nautilus
``` to open the file manager with root privileges, or just install **gksu-nautilus** plugin, which is incredibly useful. letting you open folders with root privileges from a user's nautilus, from the context right-click menu.

BE CAREFUL using nautilus as root!!!

---

