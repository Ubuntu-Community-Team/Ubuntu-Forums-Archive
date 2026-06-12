---
title: "New netbook"
date: 2009-06-06
forum: New to Ubuntu
---

### Post by indiana_crook on 2009-06-06
Hello... here's my issue, I just got a netbook from a friend.  The netbook already has ubuntu 9.04.  I want to reset the passwords and users and everything, is there any other way to do this besides reinstalling ubuntu?  The netbook is hp and has no cd-rom so it would have to be done with a flash drive.  I've tried that but I'm totally lost.  Anyone who can help?

---

### Post by arochester on 2009-06-06
Have a look at "How to reset your password in Ubuntu" on [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by ayenack on 2009-06-06
Copy any files you want to keep to a usb drive or something.

If you know the administrator password you can just add a new administrator user in your name and then delete the other users. to do this the easy way do this.

Go to.

System/Administration/Users and Groups

When in Users Settings:

Unlock

Add User

Then Under Account enter the name and password for the new user and in Profile make it Administrator. Now click on User Privileges tab and click on the options you need/want [COLOR="Red"][COLOR="Red"](make sure that Administer the System is ticked)[/COLOR][/COLOR] and click OK. Once you've done this log out and log in as the new user. Once logged in you can go to Users and Groups again and delete the users you don't want [COLOR="Red"](DO NOT DELETE THE ROOT USER)[/COLOR] once done reboot your computer and login as the new user. 

After this there will still be the home directories of the other users you can delete these by going to:

Places/Computer and clicking on the Filesystem icon then home here you will see your home folder and those of the other users and a lost+found folder. you can delete all these except lost+found, root, and your own home folder.

All this could be done from the command line also. You may need to use the command line to remove the previous admin users home folder. To do this follow these commands very carefully.

**sudo rm -r /home/ayenack** "where ayenack is the name of the previous admin account"  This is a dangerous command so be careful. You could just leave the other home folders alone.

---

### Post by nothingspecial on 2009-06-06
Or you could do a brand new install using unetbootin.

Assuming you are using 9.04 ```
sudo apt-get install unetbootin
```

Download the 9.04 ubuntu iso from [[COLOR="Magenta"]here[/COLOR]]("http://www.ubuntulinux.org/getubuntu/download")

Launch unetbootin from applications > system tools (I think)

Unmount and unplug any usb storage device except for the one you want to use to install from.

Check the disk image spot halfway down and browse to your newly downloaded iso. 

Just to be utterly sure type ```
sudo fdisk -l
``` and check that the imformation in the output matches what is in the Drive box in the unetbootin gui (second from left at the bottom).

Click ok and wait for the magic.

Reboot and enter your bios (usually by pressing escape or one of the F buttons). Have a mess about in the menus till you find something about boot and change it to boot from usb.

Away you go.

---

### Post by mikechant on 2009-06-08
> Or you could do a brand new install using unetbootin.

9.04 should have the 'imagewriter' application installed already, that's what I used to make a USB install. I think it's on the system/admin menu (not at Ubuntu PC currently so I can't check).

---

