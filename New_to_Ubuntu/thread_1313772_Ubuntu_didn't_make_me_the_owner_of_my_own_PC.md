---
title: "Ubuntu didn't make me the owner of my own PC"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by ALF102 on 2009-11-04
Well, I started using Ubuntu for the first time ever like yesterday and started installing some themes, splash screen and etc....until I realised when I want to replace the splash screen for my GIMP, it gives out a message saying "Permission Are Denied" and when I open up the properties of the file, it says "You are not the owner, so you cannot change these permisions"

I am the only user there is, who else can be the owner!

---

### Post by ranch hand on 2009-11-04
Unlike systems that are security holes, Linux uses a file system that is pretty secure.  Your files in your home folder are free for you to do pretty much anything your want to.

System files are another thing.

Linux is a multi user setup.  I do not think that you would want your 6 year old to be able to mess with a lot of system files.  Therefore, you must have "super user" status to ess with those files.

You installed the system and therefore you are on the list of users that can have this status.  This is what the terminal and "sudo" are all about.

To answer your question, the other owner is "root" and you need to have "root" priveliges to mess with some files.  This is part of what makes it so hard for someone to plant malware on your system.  You have to give a password and do it for them.

I have never worried about the splash screen for gimp so I am not sure how you do it but if you tell me I can probably tell you how to do this.  It is not that hard.

---

### Post by 3rdalbum on 2009-11-04
Your ordinary user account can only modify files that are inside your home directory.

If you want to modify files outside your home directory, you can temporarily switch to "root". Root is the administrator of the machine, and the owner of most system files on your computer.

You can elevate to root using the "sudo" or "gksudo" commands when running a program. This is the basis of Ubuntu's security system.*

You can find out how to use sudo and gksudo via the following web page: [https://wiki.ubuntu.com/RootSudo#Usage](https://wiki.ubuntu.com/RootSudo#Usage)

The easiest option is to install the "nautilus-gksu" package from Synaptic. When you next log in, you can right-click a file or folder and choose "Open as Administrator".

*And it's one reason why viruses are so non-existent on Linux :-)  This differs from Windows XP, where the first user created is an all-powerful administrator, and viruses run rampant.

---

### Post by ALF102 on 2009-11-04
Soo, lets put the GIMP stuff aside as right now I wanna know how I can gain root privileges.

---

### Post by ranch hand on 2009-11-04
See the link that 3rdalbum gave you in his post.

---

### Post by 3rdalbum on 2009-11-04
> **ALF102 said:**
> Soo, lets put the GIMP stuff aside as right now I wanna know how I can gain root privileges.

No need to put it aside. Go to Synaptic Package Manager and install the "nautilus-gksu" package. Log out, and log back in again. Right-click on the directory icon that contains the file you want to edit, and choose "Open as Administrator". The directory will open, but this new file browser will have all root privileges. Now right-click the image file and choose "Open With..." and "GIMP Image Editor".

The Gimp will open as root and you can make whatever modifications are necessary.

---

### Post by ALF102 on 2009-11-04
Ah yes yes, thank you soo much, this really helps me a lot on understanding Ubuntu file systems. I have using windows for so long now, looks like using Linux really does took away some of my 'almighty' user power away.

---

### Post by ranch hand on 2009-11-04
Not really.  Using the tool you are using, you can go into any of your system files and change them.  Assuming that you have the source files for everything (you get them by default unless you change that), you can rewrite the kernel that runs your computer.

I do not care what kind of silly "powers" MS "gives" you, you sure can't get close to anything like that.

I just got done editing one of the scripts that runs my boot loader.

---

