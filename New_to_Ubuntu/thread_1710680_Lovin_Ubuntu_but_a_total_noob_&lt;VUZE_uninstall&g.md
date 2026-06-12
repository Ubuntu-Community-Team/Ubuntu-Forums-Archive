---
title: "Lovin Ubuntu but a total noob &lt;VUZE uninstall&gt;"
date: 2011-03-20
forum: New to Ubuntu
---

### Post by dannodan2008 on 2011-03-20
Hi people, 3 days ago i cut my hard drive in half and have and installed Ubuntu. WOW ! everything is so much better and i am learning alot more about computers now everyday. 
Remember im a total noob to commands, terminal etc. For me it was always control panel.uninstall program and its gone. But with vuze on ubuntu. im having trouble. i uninstall it from the package manager but its not actually uninstalled at all. So i have a look on your forums and have tried various commands i have seen in the "terminal". but to be honest cant make head or tail of it. 

danno@danno-laptop:~$ apt-get vuze remove
E: Invalid operation vuze
danno@danno-laptop:~$ apt-get azureus remove
E: Invalid operation azureus
danno@danno-laptop:~$ apt-get remove
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
danno@danno-laptop:~$ sudo apt-get vuze remove
E: Invalid operation vuze
danno@danno-laptop:~$ sudo apt-get remove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  ttf-dejavu-extra libswt-cairo-gtk-3.5-jni azureus libswt-gtk-3.5-jni
  java-common liblog4j1.2-java libswt-mozilla-gtk-3.5-jni
  libaccess-bridge-java-jni libaccess-bridge-java icedtea-6-jre-cacao
  libcommons-cli-java sdparm openjdk-6-jre-headless tzdata-java openjdk-6-jre
  openjdk-6-jre-lib libcommons-lang-java libswt-gnome-gtk-3.5-jni
  libswt-gtk-3.5-java ca-certificates-java java-wrappers
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
danno@danno-laptop:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
danno@danno-laptop:~$ ^C
danno@danno-laptop:~$ ^C
danno@danno-laptop:~$ 


Any detailed advice would be greatly appreciated,
And thank you for Ubuntu !!:KS
Regards
Danno

---

### Post by roger_1960 on 2011-03-20
Hi

In all your attempts you missed the right one

> sudo apt-get remove vuze

In terminal you can type  > man apt-get to get a "manual" on the command.  This works for almost all terminal commands.  Type the letter q (for quit) to exit the manual.

---

### Post by TeoBigusGeekus on 2011-03-20
First of all, you can only have one of the following running
[LIST]
[*]apt-get
[*]software-center
[*]synaptic
[/LIST]
Secondly, you have to use apt-get with sudo, ie.
```
sudo apt-get
```
Apt-get makes changes to your system, so you have to give it administrator privileges.

Finally, the correct syntax for removing a program with apt-get is
```
sudo apt-get remove nameofprogram
```
In your case
```
sudo apt-get remove vuze
```

If you want the program gone as well as its configuration files, you can use purge (it's equivalent to the Completely Remove option in synaptic):
```
sudo apt-get purge vuze
```

You should also use autoremove with sudo in order for it to function properly:
```
sudo apt-get autoremove
```
The command above will uninstall any packages that were installed as dependacies for other packages and are no longer needed.

---

### Post by dannodan2008 on 2011-03-20
> **TeoBigusGeekus said:**
> First of all, you can only have one of the following running
[LIST]
[*]apt-get
[*]software-center
[*]synaptic
[/LIST]
Secondly, you have to use apt-get with sudo, ie.
```
sudo apt-get
```Apt-get makes changes to your system, so you have to give it administrator privileges.

Finally, the correct syntax for removing a program with apt-get is
```
sudo apt-get remove nameofprogram
```In your case
```
sudo apt-get remove vuze
```If you want the program gone as well as its configuration files, you can use purge (it's equivalent to the Completely Remove option in synaptic):
```
sudo apt-get purge vuze
```You should also use autoremove with sudo in order for it to function properly:
```
sudo apt-get autoremove
```The command above will uninstall any packages that were installed as dependacies for other packages and are no longer needed.


Hi guys, sorry im asking yet another question, but thanks for the fast response, i used the 2nd command  the purge vuze one, this is what i got
danno@danno-laptop:~$ sudo apt-get purge vuze
[sudo] password for danno: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package vuze is not installed, so not removed
The following packages were automatically installed and are no longer required:
  ttf-dejavu-extra libswt-cairo-gtk-3.5-jni azureus libswt-gtk-3.5-jni
  java-common liblog4j1.2-java libswt-mozilla-gtk-3.5-jni
  libaccess-bridge-java-jni libaccess-bridge-java icedtea-6-jre-cacao
  libcommons-cli-java sdparm openjdk-6-jre-headless tzdata-java openjdk-6-jre
  openjdk-6-jre-lib libcommons-lang-java libswt-gnome-gtk-3.5-jni
  libswt-gtk-3.5-java ca-certificates-java java-wrappers
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
danno@danno-laptop:~$ 

As you can see it says that vuze is not installed ? but it is, i can open it and use it ?
If i am just missing something obvious i appologise for wasting your time

---

### Post by dannodan2008 on 2011-03-20
one of the other commands worked. sudo apt-get autoremove ..... after ... sudo apt-get remove vuze.
 even though it said wasnt installed ??
Well thanks guys ! It wouldnt of got sorted that quick in a microsoft forum :guitar:

---

### Post by _0R10N on 2011-03-20
If it's not listed as an installed package, then I suppose you have installed the program from an installer you downloaded from Internet, or by decompressing a non-installation folder downloaded from Vuze's site. This second option is less possible since it seems that you have it listed under Internet Applications menu.

Since I installed Vuze using the aptitude tool, I'm not familiarized with alternative Vuze installation methods.

It would be helpful if you'd describe how you've installed Vuze, in the first place.

Kind regards!

---

### Post by _0R10N on 2011-03-20
> **_0R10N said:**
> If it's not listed as an installed package, then I suppose you have installed the program from an installer you downloaded from Internet, or by decompressing a non-installation folder downloaded from Vuze's site. This second option is less possible since it seems that you have it listed under Internet Applications menu.

Since I installed Vuze using the aptitude tool, I'm not familiarized with alternative Vuze installation methods.

It would be helpful if you'd describe how you've installed Vuze, in the first place.

Kind regards!


lol I was writing my previous comment at the same time you were posting yours! Glad you've managed to get rid of the problem!

Kind regards!

---

