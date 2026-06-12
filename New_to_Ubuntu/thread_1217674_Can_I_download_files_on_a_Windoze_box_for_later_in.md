---
title: "Can I download files on a Windoze box for later installation on an Ubuntu box?"
date: 2009-07-19
forum: New to Ubuntu
---

### Post by zer010 on 2009-07-19
I was wondering if there is a way to get Linux programs while on a Windoze computer.  I have a winxp laptop,and I see a Linux program I want. My linux box doesnt have internet access. I want to get the file(s) and put them on a usb stick.  Then when I get home, install the program on my Linux comp.  What file types can I do this with?  How do I do this?  Will it have to be a bunch of compiling? 
Thanks for any help.:)
P.S.
This is a theoretical setup. Linux box is assumed to be updated via occasional net access.

---

### Post by Jimleko211 on 2009-07-19
If they offer a .deb, you can download that and it'll work on your linux box.

---

### Post by robert shearer on 2009-07-19
This should be ideal...
[http://keryxproject.org/](http://keryxproject.org/)
[http://crashsystems.net/2009/01/keryx-tutorial/](http://crashsystems.net/2009/01/keryx-tutorial/)

---

### Post by mjpatey on 2009-07-19
I was contemplating Jimleko211's response above, and it occurred to me... I think .deb files will work unless you happen to be missing some dependencies.  If I'm not mistaken, a .deb file doesn't come packaged with its dependencies, but will download them during installation.  If I'm right about that, you may not be able to install your package without an Internet connection.

-Mark

---

### Post by EXCiD3 on 2009-07-20
> **mjpatey said:**
> I was contemplating Jimleko211's response above, and it occurred to me... I think .deb files will work unless you happen to be missing some dependencies.  If I'm not mistaken, a .deb file doesn't come packaged with its dependencies, but will download them during installation.  If I'm right about that, you may not be able to install your package without an Internet connection.

-Mark
You can if you use [Keryx]("http://keryxproject.org").

---

### Post by zer010 on 2009-07-20
Firstly, thanks for the responses!  They are quite insightful, but sounds like a lot of "legwork".  "Que sera, sera!" Sounds like fun! As for a friend o' mine, well...
But anyhow, the theoretical setup has been appended....

Download/Install an Ubuntu program on net accessable, Ubuntu box, then transfer the program onto another Ubuntu box to be Installed and Used.

Please keep the ideas comming. Even if it involves compiling, point me on a great How-To on compiling.

Thanks very much!:P

---

### Post by llamabr on 2009-07-20
What's wrong with the network on the linux side?

---

### Post by Garrovick on 2009-07-20
I download generic files on either computer for either computer, using Windozer. I've not had any significant problems. WinRar files are the exception.  Although there is a command line WinRar program for Linux.

---

### Post by robert shearer on 2009-07-20
> Download/Install an Ubuntu program on net accessable, Ubuntu box, then transfer the program onto another Ubuntu box to be Installed and Used.

Now that is easier.
Look in the repos for 'aptoncd'. Then install it on the online compy.

If the two compys are using the same version then aptoncd can be used to make a cd of apps and updates from the online machine.

Take the cd to the offline compy and when you load it you will be asked if you want to add the cd as a software source.

Answer yes and the cd is added to apt.

Then open synaptic and search for the apps you want, apply to install them and they will be installed from the cd.

At some point you will be prompted to run the updates, again from the cd.

All very simple. Use cdrw's and run it weekly to keep up to date.(If left **too** long between updates there can be dependency problems.) 

If you install aptoncd from the cd to the 2nd compy you can even use the option to add the whole of the cd contents to your apt cache.

User manual here...[http://aptoncd.sourceforge.net/doc-manual.html](http://aptoncd.sourceforge.net/doc-manual.html)

You can also make an iso  and use a flash drive to transfer it then restore from it.

---

### Post by zer010 on 2009-07-21
Thanks for the great info y'all!!  This is VERY helpfull!  :D Its nice to know you can still get updates and software if you ever lose net connection.

---

### Post by zer010 on 2009-08-03
SOLVED: Won't fit in the title. Thanks again!

---

