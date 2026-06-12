---
title: "install from cd"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by arunkmohan18 on 2009-12-13
i installed ubuntu from cd  can i install application and plugins from an iso file of ubuntu complete remix 9.1 anybody tell me how to do this

---

### Post by jvc26 on 2009-12-13
Yes, you can mount the iso (double click on the file and it should automount). Once mounted you can point aptitude to its location (System -> Administration -> Software Sources) and then install from it. Is there a reason you can't use the normal online repositories?

Il

---

### Post by arunkmohan18 on 2009-12-13
how to install it i used synaptic package manager and installed all files in that manager but i could not install application please tell me how to do it

---

### Post by mikewhatever on 2009-12-13
Why do you need the cd, if you can install files from Synaptic? Perhaps you'll be more comfortable with the Software Center under Applications. Don't install all packages, it's unnecessary, and will break your system.

---

### Post by Potters Son on 2009-12-13
As the previous posters said, it is much easier to install programs using the Ubuntu Software Center (formerly "Add/Remove Programs") under the Applications menu, which automatically downloads them off of the Internet. If you have slow Internet access, you can use the CD or USB drive you used to install Ubuntu as a source, without having to mount the ISO. However, if you have slow Internet access AND you don't have the original CD, your options are:

1) Burn the ISO image to a CD (easier)
      -- or --
2) Use a complicated workaround involving manually mounting the CD image and changing the repository list (harder).

If you really want to install packages from an ISO, I've created a workaround:

(In the process of trying to solve this problem, I realized that Software Sources does not recognize mounted iso files as CD-ROMs. This behavior is a bug and should be corrected. So, we have to manually mount it.)

1. Open a terminal window
Applications > Accessories > Terminal

2. Copy (Ctrl+C) and paste (Ctrl+**Shift**+V, not Ctrl+V) the following into the terminal. When it asks for your password, simply type it in and press enter; don't worry if it doesn't appear to respond to your keystrokes. It is.
```
sudo mkdir /media/ubuntucd
```

3. Now, I want you to copy the following into the terminal, but you need to change the path and filename ("~/Desktop/ubuntu-9.10-desktop-i386.iso") to match the iso on your system first, and then hit enter.
```
sudo mount -t iso9660 /home/karl/Desktop/ubuntu-9.10-desktop-i386.iso /media/ubuntucd -o loop
```

We've just mounted the ISO. Now, we'll manually change the repository information to include it in the package manager.

4. Open Software Sources
System -> Administration -> Software Sources

5. Click the "Other Software" tab

6. Click the (Add...) button, paste the following in the text box, and click the (Add Source) button. If it asks if you want to reload the package list, say yes.
"deb file:/media/ubuntucd/ karmic main restricted universe multiverse"

7. Click (Close).

8. Now, you can choose whether you want to use the Ubuntu Software Center, or Synaptic Package Manager. The Software Center makes it easier to install programs, but if you have specific packages you need to install, you can use Synaptic.

Now, the Software Center is quite user-friendly, but you asked about Synaptic, so I'll try to give you a rundown of how it works. In Ubuntu, software is represented by *packages*, a much saner version of Windows installer files. When you install a package, it downloads the appropriate files and installs them in the correct places, hassle-free. Often, some packages require other packages to be installed as well, but Ubuntu handles that for you as well.

Ubuntu hosts nearly 30,000 of these packages, but hardly anyone ever installs all of them. For one thing, doing so would likely require more disk space than the average desktop computer has room for; for another, people do not need all those programs. For instance, there's a package that lets you use an electronic keyboard with a computer, a package to configure proxy servers, and a package that lets you use spell-checking in Swahili. Nobody expects you to install everything.

To install a package in Synaptic, click on the square to the right of the package and select "Mark for installation." Do this for every package you want to install. Then, when you are finished, click the "Apply" button at the top, and Synaptic will begin to install software.

**Cleaning up**
If you followed by instructions for using the ISO file, you might want to unmount it and tell the repository not to use it anymore; I don't know what would happen if you left the ISO mounted and rebooted.

1. Go back into the "Other Software" tab in Software Sources and click the checkbox next to "file:/media/ubuntucd . . . " to disable using the cd.
2. In the terminal, run "sudo umount /media/ubuntucd"

You're done!

---

