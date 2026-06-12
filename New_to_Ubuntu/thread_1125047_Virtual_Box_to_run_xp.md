---
title: "Virtual Box to run xp"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by thraxsa on 2009-04-14
Here is my situation.

- I have 2 hardrives in my pc, one for ubuntu and the other for xp.

Everything works fine in terms of grub, dual boot etc 

What I want to do is use Virtual Box to run XP from it's own hard drive.

Sound really simple I know and probably is, but how do I set it up ???  

Even is someone can give me a link to go to that would be most welcomed.

---

### Post by ninjapirate89 on 2009-04-14
This looks like what you want but its really complex.[http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html]("http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html")

---

### Post by Cresho on 2009-04-14
man, I love this setup!  I have virtualbox running vegas video 8 with xp.  IT boots in 5 seconds with a click of my icon.  I backup the vdi file and if xp dies, all i do is delete the file and use the backup file.  It is just too funny!

Listen.  DO this.  I'm going to post all my notes here so bare with me.
-------------------------------------------------------------------------
go to this website and download the deb file and install it.  It's like an executable.

[http://dlc.sun.com/virtualbox/vboxdownload.html](http://dlc.sun.com/virtualbox/vboxdownload.html)

thats to get you started.

install this one
fixes kernel changes in ubuntu (specific virtualbox and maybee wifi) sudo apt-get install dkms

virtualbox is under...applications->system tools.

fixes
--------------------------------------------------
install guest addon

First we’ll need to install the VirtualBox Guest Additions. I haven’t yet blogged about how to do this on Windows guests, but you might refer to my previous post on Installing Guest Additions for Ubuntu Guests. Hopefully this’ll be enough until I write a proper article on the topic.

configure video memory to 24mb

Activating Seamless Integration

With the release of VirtualBox 1.5.0 (the version you just installed via the Ubuntu repositories) Innotek added the seamless integration feature. This is similar to what is available on Parallels on Mac, allowing you to run individual applications from a virtual environment seamlessly on your native desktop.

Once your guest machine is running and logged in you can activate seamless mode via a shortcut key. Now I want to note that you might double-check to see what your “Host Key” is set to before you dive into this. This proved problematic for me on my MacBook as the default key is right-ctrl, but there is no right-ctrl on the MacBook.

Navigate to (File > Preferences) inside the main VirtualBox window, select the “Input” option and verify or set your “Host” Key” before you go forward.

You’ll also need to install Guest Additions on the Windows guest for this to be available.  See the mention in the next section on how to do that.

Once you’re sure what your “Host Key” is, go back into your running Windows guest and activate seamless mode by hitting:

    "Host Key"+L

This should make everything but the Start menu disappear, allowing you to launch individual applications as you normally would. You may want to move your bottom gnome panel to the top for better integration.

Configuring Shared Folder Integration

One additional thing you might want to setup is shared folder integration. What I mean by this is having the files from your Ubuntu desktop appear on your Windows desktop as well. This might be useful, for instance, if you launched Internet Exploder via your integrated Start menu and downloaded a file. The saved file would then appear on your native Ubuntu desktop, via the shared folder system.

First we’ll need to install the VirtualBox Guest Additions. I haven’t yet blogged about how to do this on Windows guests, but you might refer to my previous post on Installing Guest Additions for Ubuntu Guests. Hopefully this’ll be enough until I write a proper article on the topic.

Next activate virtual shared folder support in your guest OS (Windows). Do this via the main VirtualBox window, selecting (Machine > Settings > “Shared Folders”). Click the button to add a shared folder (the top right icon), and define the path to your share. You’ll likely want to share your current Desktop, so you might select:

    /home/username/Desktop

Now, toggling back to your Windows guest, you’ll want to mount this shared folder. You’ll need to open a shell using (Start > Run > “cmd“). Then use the following command to “mount” this shared folder between your Ubuntu host and your Windows guest.

    net use x: \\vboxsvr\Desktop

You should now have access to your shared folder, but we also want to tell Windows to use this as its primary folder.

Start up regedit via (Start > Run > “regedit“) and navigate to the following location:

    (HKEY_CURRENT_USER > Software > Microsoft > Windows > CurrentVersion > Explorer > User Shell Folders)

Look for the key “Desktop” and change the value to:

    x:                   originaly was %USERPROFILE%\Desktop

Save your changes, reboot your Windows guest and you should be done.

-------------------------------------------------------------------------
now this is important!  if you need to install drivers, it's called the virtualbox guest additions.  you will need to unmount the cd drive windows xp cd installer and the unmount icon is located on the virtualbox window of the cd on the lower right hand corner.  Now you click on top on devices, guest addons and install that.  reboot the virtual win and you have graphics and etc.

USB does not work but only in sudo mode.

---

### Post by Paqman on 2009-04-14
> **thraxsa said:**
> 
Sound really simple I know and probably is, but how do I set it up ???  


Really not simple at all.

However, there's nothing to stop you from installing a second copy of Windows into Virtualbox and using that.

---

### Post by thraxsa on 2009-04-14
thanks for the help, certainly appears more difficult than I imagined...

If only I could run a Virtual Machine for my Xbox 360 : )

---

### Post by Mister.Vash on 2009-04-14
The stickies at the top of the Virtualization forum have all the details your need, [http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

---

