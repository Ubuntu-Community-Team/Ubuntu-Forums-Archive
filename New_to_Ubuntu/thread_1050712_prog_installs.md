---
title: "prog installs"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by longisland on 2009-01-25
hey people. im absolute new in linux. i got ubuntu , wander if any can help me how to install programs.

---

### Post by Crafty Kisses on 2009-01-25
Depends on what you want to install, there is the Synaptic Package Manager, which can be easily accessed by going to **System->Administration->Synaptic Package Manager**, and from there you can search, and browse packages that you want/need. You can also compile programs from source, which isn't too hard to do, here is a great tutorial on that: [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo). There's also the Terminal way as well, which if you know the package name by heart, you can run the following:
```
sudo apt-get install package name
```
Then it will install the package and all it's proper dependencies.

---

### Post by SunnyRabbiera on 2009-01-25
For the basic user there is also add/remove, it has a smaller amouint of packages but it does the same job.

---

### Post by Hospadar on 2009-01-25
Here's a great guide:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

In short, almost everything you will ever install will be a package downloaded by a package manager (such as synaptic or aptitude) from an ubuntu package server.

Generally, if you are just looking for stuff to install, Applications -> Add/Remove, and if you are looking for stuff a little more in depth, go to System->Administration->Synaptic

If you see something on the internet somewheres for linux and you want to try it, take a look at the package manager first, they probably have a prepackaged version of it that will be a whole lot easier to install that something off the tubes.

---

### Post by longisland on 2009-01-25
i download .bin but how to start installation ? trying like in winds but he telling me that there is no application to open

---

### Post by longisland on 2009-01-25
this is google earths. plus got same problem with skype for linux, so i had to run it with wine.

---

### Post by longisland on 2009-01-25
actually i was thinking that there is somekinde installer?

---

### Post by Crafty Kisses on 2009-01-25
I'm not sure what you're trying to install, but let's just say your trying to install Java right, you're going to have to open the Terminal, which you can do that by doing the following, **Applications->Accessories->Terminal**. Once you're at the Terminal you can start installing the .bin file, so again let's just say your going to install the Java.bin file, follow these commands, assuming you saved the Java file to your desktop, and it's named "Java.bin", you would do the following:
```
cd ~/Desktop
chmod +x java.bin
sudo ./java.bin
```
So basically, what you need to do is move to the directory to where the .bin file is, make the .bin file executable, then once you've done that you can actually start running the .bin file, and once you're running it, it will obviously install what you needed, and you should be all set. If you have any problems please post your problem, and I or someone else can help you.

---

### Post by 3rdalbum on 2009-01-25
Have you checked to see if the program is available from Synaptic Package Manager? This is the easiest, most secure, and most flexible way of installing software, so use it if you can. You might also be able to find the program available in a third-party repository, so do a web search for an Ubuntu repository with that program available. For instance, if the program you downloaded is Google Earth, you can get it from the Medibuntu repository ([www.medibuntu.org](www.medibuntu.org))

The file that you have downloaded just sounds like a program. For security reasons, any executables that you download will not have "execute permission". If you right-click the file and choose "Properties", then go to the Permissions tab, you can click on the checkbox that allows the file to execute.

If double-clicking it now doesn't work, you might need to run it in a terminal. Open a terminal window and drag the file onto the terminal. Then press Enter inside the terminal window.

If the program you downloaded is an installer, it will likely need to be run as root (administrator) so it can put its files in system-wide locations. In the terminal window, type "sudo su", press enter and put in your password. Now you can drag the file onto the terminal window, etc.

EDIT: Google Earth is available from the Medibuntu repository at [www.medibuntu.com](www.medibuntu.com), as is Skype. Skype is also available from [www.skype.net](www.skype.net) as a Debian package, which is the native Ubuntu format. Download a "binary installer" or running the Windows version with Wine should be a **last resort** - use Synaptic Package Manager, a third-party repository or a native Debian package wherever possible.

---

### Post by SunnyRabbiera on 2009-01-25
Actually java is in the repositories, but first here is something for google earth:
[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

there was a installer for ubuntu that didnt need extra repos but it seems lost to time, though medibuntu has one that still works...

---

### Post by longisland on 2009-01-25
where can i find info about how to work with terminal (commands etc.)(especially sudo- what this means?)

---

### Post by Crafty Kisses on 2009-01-25
Try taking a look at this link: [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal).

---

### Post by longisland on 2009-01-25
normal password( the one for login to ubuntu) is not working, but i know that there should be a root password, but how to set it?

---

### Post by SunnyRabbiera on 2009-01-26
> **longisland said:**
> normal password( the one for login to ubuntu) is not working, but i know that there should be a root password, but how to set it?

Ubuntu has no root, for java just ignore the java download and use the repositories.

---

### Post by 3rdalbum on 2009-01-26
> **longisland said:**
> normal password( the one for login to ubuntu) is not working, but i know that there should be a root password, but how to set it?

There is no root password, you use your ordinary login password. Make sure you're typing it correctly. No bullets or asterisks will appear as you type it. Use sudo, not su.

---

