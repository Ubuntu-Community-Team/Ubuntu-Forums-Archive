---
title: "Can't Download Any Packages"
date: 2011-07-05
forum: New to Ubuntu
---

### Post by seniorPantaloons on 2011-07-05
Hey there, Ubuntu Forums.

I used to have Ubuntu 11.04 Natty Narwhal as my sole operating system on my HP G60 US-117, but I couldn't turn on my wifi, so I formatted my hard drive and installed Ubuntu 10.04 Lucid Lynx as my sole operating system, and now I have wifi! :)

Problem is, however, that I can't download and install any packages. No matter what I try to install - Gimp, Docky, or even a Nvidia accelerated graphics driver - I get similar errors. Either I get an error stating "Package dependencies cannot be resolved" in the Ubuntu Software Center or "E: Broken packages" in the Terminal. I've searched around for solutions to all three errors, but have yet to solve the errors. 

I've tried
```
sudo apt-get update
```

I've tried
```
sudo apt-get -f install
```

I've tried
```
sudo dpkg --configure -a
```

I've tried the fix broken packages option in Synaptic.

I'm a Ubuntu noob, so I don't really know what to do in this situation. Help will be appreciated!

---

### Post by Rex Bouwense on 2011-07-05
Did you try to download any of them in Synaptic Package Manager or just try to repair a broken package?

---

### Post by seniorPantaloons on 2011-07-05
Thanks for responding. I just tried to install files through Synaptic Software Manager, and I keep getting lists of dependencies that can't be installed. I would try to fix a broken package, but I don't quite know how to find out which package(s) are broken.

---

### Post by wildmanne39 on 2011-07-05
> **seniorPantaloons said:**
> Hey there, Ubuntu Forums.

I used to have Ubuntu 11.04 Natty Narwhal as my sole operating system on my HP G60 US-117, but I couldn't turn on my wifi, so I formatted my hard drive and installed Ubuntu 10.04 Lucid Lynx as my sole operating system, and now I have wifi! :)

Problem is, however, that I can't download and install any packages. No matter what I try to install - Gimp, Docky, or even a Nvidia accelerated graphics driver - I get similar errors. Either I get an error stating "Package dependencies cannot be resolved" in the Ubuntu Software Center or "E: Broken packages" in the Terminal. I've searched around for solutions to all three errors, but have yet to solve the errors. 

I've tried
```
sudo apt-get update
```

I've tried
```
sudo apt-get -f install
```

I've tried
```
sudo dpkg --configure -a
```

I've tried the fix broken packages option in Synaptic.

I'm a Ubuntu noob, so I don't really know what to do in this situation. Help will be appreciated!
Hi, try these commands one right after the other has finished in the order that I list them.
```
sudo dpkg --configure -a
```
```
sudo apt-get clean
```
```
 sudo apt-get update
```
```
sudo apt-get upgrade
```

---

### Post by seniorPantaloons on 2011-07-05
Thanks for responding.

I'm still getting a "Package dependencies cannot be resolved" error from Ubuntu Software Center and an "E: Broken packages error" from the terminal.

---

### Post by hunterb108 on 2011-07-05
I think i may have the same problem... i have absolutely no idea what to do!!! there is a red circle on my top task bar with a white line going horizontally through it. when i right click it shows these options:
Show Updates
Install all Updates
Check for updates
Start package manager
Show notifications
Preferences

When I open the circle by double clicking i get this exact message:
______________________________________________________________________________________
An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, Eroblem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'
______________________________________________________________________________________

I am a total n00b with all of this so i do not know how to report bug against the 'update-manager' or whatever it is asking me to do. please help this problem is not allowing me to delete or install anything from the software center :(((((

---

### Post by wildmanne39 on 2011-07-05
> **hunterb108 said:**
> I think i may have the same problem... i have absolutely no idea what to do!!! there is a red circle on my top task bar with a white line going horizontally through it. when i right click it shows these options:
Show Updates
Install all Updates
Check for updates
Start package manager
Show notifications
Preferences

When I open the circle by double clicking i get this exact message:
______________________________________________________________________________________
An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, Eroblem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'
______________________________________________________________________________________

I am a total n00b with all of this so i do not know how to report bug against the 'update-manager' or whatever it is asking me to do. please help this problem is not allowing me to delete or install anything from the software center :(((((Hi, this should fix your problem.
```
sudo rm /var/lib/apt/lists/* -vf
```
Please use this command exactly as it is written, and do not use with other files or you could wipe out your system. It will remove the damaged list and when you run the second command it will replace it with a new list.
```
sudo apt-get update
```

---

### Post by wildmanne39 on 2011-07-05
> **seniorPantaloons said:**
> Thanks for responding.

I'm still getting a "Package dependencies cannot be resolved" error from Ubuntu Software Center and an "E: Broken packages error" from the terminal.Hi, type this in a terminal
```
cd /var/lib/apt/lists/
```
then
```
ls
```
and that will list your source list and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by seniorPantaloons on 2011-07-05
> **wildmanne39 said:**
> Hi, type this in a terminal
```
cd /var/lib/apt/lists/
```
then
```
ls
```
and that will list your source list and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

I saw your response to hunter, and I tried out ```
sudo rm /var/lib/apt/lists/* -vf
``` and it worked for me. I now have Gimp, Docky, the Nvidia driver, and more. Thanks a ton, you are a life saver!
:):):)

---

### Post by wildmanne39 on 2011-07-05
> **seniorPantaloons said:**
> I saw your response to hunter, and I tried out ```
sudo rm /var/lib/apt/lists/* -vf
``` and it worked for me. I now have Gimp, Docky, the Nvidia driver, and more. Thanks a ton, you are a life saver!
:):):)Hi, your welcome, I was not sure if it would work for you or not with your problem but I figured you would try when you saw it and I was hoping you would let me know,would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

