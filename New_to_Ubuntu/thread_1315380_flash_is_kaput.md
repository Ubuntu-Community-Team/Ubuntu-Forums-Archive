---
title: "flash is kaput"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by HomoGleek on 2009-11-05
I un-installed all flash plugins this morning as it became choppy, I then installed adobe flash. After shutting down my computer Firefox and other browsers startd saying there wasn't any flash installed. So I uninstalled and installed again.

Now Im getting nothing atall, and an error message

---

### Post by HomoGleek on 2009-11-05
And when I click on the error I get another error

---

### Post by ukripper on 2009-11-05
> **DarrenTod said:**
> And when I click on the error I get another error

try removing it completely from terminal:

```
sudo apt-get remove --purge flashplugin-nonfree adobe-flashplugin
```

and now install it by using command below:
```
sudo apt-get install adobe-flashplugin
```

---

### Post by HomoGleek on 2009-11-05
Hi

Tried that and I got 
```

darren@mango:~$ sudo apt-get remove --purge flashplugin-nonfree adobe-flashplugin
[sudo] password for darren: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
darren@mango:~$ 

```

I cannot use USC too install anything now either

---

### Post by ukripper on 2009-11-05
> **DarrenTod said:**
> Hi

Tried that and I got 
```

darren@mango:~$ sudo apt-get remove --purge flashplugin-nonfree adobe-flashplugin
[sudo] password for darren: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
darren@mango:~$ 

```

I cannot use USC too install anything now either
 Try this comand then:
```
sudo apt-get install --reinstall adobe-flashplugin
```

---

### Post by 3rdalbum on 2009-11-05
Try downloading the adobe-flashplugin package from [http://packages.ubuntu.com](http://packages.ubuntu.com) and placing it into /var/cache/apt/archives (you'll need to run a file browser as root to do this).

Also, removing and reinstalling software on Linux tends to do absolutely nothing toward solving problems. Reinstalling software will only solve the problem of a corrupted program, and it's extremely rare that programs get corrupted on Linux because they are owned by root.

A better first step would be to rename/remove the program's preferences file; in this case, the preferences can be found in ~/.macromedia/Flash_Player and ~/.adobe/Flash_Player. Rename them so Flash Player can't find them, and the preferences will be recreated from scratch. It's much more likely that your preferences file is corrupted than the program's file.

---

### Post by HomoGleek on 2009-11-05
Hi

Im not sure exactly what I need too download from there?

---

### Post by HomoGleek on 2009-11-05
> **ukripper said:**
> Try this comand then:
```
sudo apt-get install --reinstall adobe-flashplugin
```
No luck, thanks anyway

---

### Post by mac9416 on 2009-11-05
Hey, DarrenTod,

You can uninstall adobe-flashplugin, and install the flashplugin-nonfree with these commands:

> $ sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm  # Deletes a troublesome config file
$ sudo dpkg-reconfigure adobe-flashplugin --force  # Force-reconfigures adobe-flashplugin
$ sudo dpkg --purge --force-all adobe-flashplugin  # Force-removes adobe-flashplugin
$ sudo apt-get install flashplugin-nonfree  # Installs flashplayer the easy way

---

### Post by HomoGleek on 2009-11-06
> **mac9416 said:**
> Hey, DarrenTod,

You can uninstall adobe-flashplugin, and install the flashplugin-nonfree with these commands:
That worked, many many thanks :)

Also thanks for the comments besides the commands too explain what they are doing, very helpful :)

---

