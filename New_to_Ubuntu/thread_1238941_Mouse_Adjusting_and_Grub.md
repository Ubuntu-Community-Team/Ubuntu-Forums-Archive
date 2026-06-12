---
title: "Mouse Adjusting and Grub"
date: 2009-08-13
forum: New to Ubuntu
---

### Post by Da-V-Man on 2009-08-13
I have a mouse, a Lasermouse 6000v2 to be exact. Now, it works fine, but I find that it scolls way too fast for my liking, and I'm not able to take advantage of the back/forward buttons, (or Mouse 4 and Mouse 5) in the file browser. Is there anything I can do to change this?

Also, I noticed that when the GRUB loader boots up, it shows the slightly older previous versions. Will these keep adding up without me manually changing it or will it eventually stop showing the older versions of Ubuntu?

---

### Post by raymondh on 2009-08-13
> **Da-V-Man said:**
> 

Also, I noticed that when the GRUB loader boots up, it shows the slightly older previous versions. Will these keep adding up without me manually changing it or will it eventually stop showing the older versions of Ubuntu?

Assuming this is a non-WUBI install ....

You can either edit the menu.lst to hash/comment the kernels you no longer wish to see in the Grub menu or, install startupmanager (see synaptic) and set defaults, etc. from there.  SUM is GUI-based and has the option to limit the number of kernels you wish to see, among others.  It also writes to the menu.lst.

---

### Post by rsiddharth on 2009-08-13
Hi Da-V-Man ,

As raymondhenson has said you can directly edit the **menu.lst** to hide the previous versions in the GRUB menu at boot or you can resort to other options specified in his reply . 

If you wish to edit the menu.lst to hide the previous versions in your your boot menu here is a brief how-to :

Open Terminal ( Applications-->Accessories -->Terminal ) .

Type this to change the Directory : 
```

cd /boot/grub/

```Type this to open menu.lst in nano ( Text editor ) 
```

sudo nano -S menu.lst 

```After the editor opens the file ( menu.lst )  . Hit Ctrl+V 2 times  ( to scroll down two pages of text ) . Now you will see something like :

```

## ## End Default Options ##

```Near the bottom of the editor . The text that follow after the above heading will the that showing up in the GRUB boot menu when you start the system . Comment those  that you want to hide in the boot menu options . 

Here is a small illustration : 

For instance I want to hide 

this 
```

  Ubuntu 9.04, kernel 2.6.28-13-generic

```from the boot menu , then I comment  "Ubuntu 9.04, kernel 2.6.28-13-generic " and others in that paragraph. 

--------
Before commenting : 

```

title           Ubuntu 9.04, kernel 2.6.28-13-generic
uuid            badef8ef-3d86-428f-920c-9dfd9d92f36c
kernel          /boot/vmlinuz-2.6.28-13-generic root=UUID=badef8ef-3d86-428f-920c-9dfd9d92f36c ro quiet splash
initrd          /boot/initrd.img-2.6.28-13-generic
quiet

```After commenting :

```

#title           Ubuntu 9.04, kernel 2.6.28-13-generic
#uuid            badef8ef-3d86-428f-920c-9dfd9d92f36c
#kernel          /boot/vmlinuz-2.6.28-13-generic root=UUID=badef8ef-3d86-428f-920c-9dfd9d92f36c ro quiet splash
#initrd          /boot/initrd.img-2.6.28-13-generic
#quiet

```After commenting the desired options , hit Ctrl+O to save the file and Ctrl+X to exit .
Exit terminal ( type : exit )  .
---------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------

Go to System --> Preferences --> Mouse and see if you can do anything to to tweak your Mouse setting .

---

### Post by Da-V-Man on 2009-08-16
Ah thanks. I also have some other questions.

First of all, is there a linux equivalent of .exe files? Also, how do you install programs or applications without using the package manager?

Secondly, I want to update Firefox to 3.5, but I don't see it in the package manager.

---

### Post by raymondh on 2009-08-16
> **Da-V-Man said:**
> Ah thanks. I also have some other questions.

First of all, is there a linux equivalent of .exe files? Also, how do you install programs or applications without using the package manager?

Secondly, I want to update Firefox to 3.5, but I don't see it in the package manager.

[http://www.linfo.org/filename_extension.html](http://www.linfo.org/filename_extension.html)
[http://en.wikipedia.org/wiki/Deb_(file_format](http://en.wikipedia.org/wiki/Deb_(file_format))
[https://help.ubuntu.com/8.04/add-applications/C/install-file.html](https://help.ubuntu.com/8.04/add-applications/C/install-file.html)

[http://www.ubuntusolutions.org/2009/07/ubuntu-firefox-3-5-install-use-ubuntu-mozilla-security.html](http://www.ubuntusolutions.org/2009/07/ubuntu-firefox-3-5-install-use-ubuntu-mozilla-security.html)

---

### Post by rsiddharth on 2009-08-17
If you have installed Firefox 3.5 through Synaptic or** apt **, then the updates for it are taken care by  Update Manager ( System-->Administration-->Update Manager ) . Open " Update Manager " ( you may be prompted for the password ) and click on " Check " to see whether your system needs an update . After checking and if there is anything that must be updated , it will present  you a list of packages/files that are to be updated and you will have the right to choose which are to be updated.  

The latest version of Firefox is v3.5.2 and I have this  ( I installed Firefox-3.5 through **apt** ) .

If you want to update your whole system through Terminal , Then you got to type this successively : 

```

sudo apt-get update 

```

```

sudo apt-get upgrade 

``` 

--------------------------------------
Check this out : [http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065)    
----------------------------------------

---

