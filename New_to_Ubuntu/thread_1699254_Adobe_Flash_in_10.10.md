---
title: "Adobe Flash in 10.10"
date: 2011-03-03
forum: New to Ubuntu
---

### Post by bob brazie on 2011-03-03
Fresh install of 10.10.

What is the easiest way to install Adobe Flash?

I see the installer is already installed in the software center.

Thanks in advance. Bob.

---

### Post by maqtanim on 2011-03-03
1. Install it from the software center.

or

2. Download the .deb version of flash player from the following link and double click the file to install it:
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

---

### Post by verymadpip on 2011-03-03
Hey Bob.

I think it should 'install itself' if you had install 3rd party stuff checked during the actual installation of 10.10.

Just give something from you tube a go to see if it's there & working.

Otherwise I would say software centre is the easiest way to do it.

Good luck

Pip

---

### Post by beew on 2011-03-03
The best way would be to install using the firefox plugin "flashaid" developed by Ubuntu forum member LovingLinux. It checks for updates, removes cobflicting flash versions and automatically configures flash for optimization in Ubuntu boxes. It works better than installing from the repository or Adobe.

---

### Post by verymadpip on 2011-03-03
Actually flashaid is very good...............

good point beew

---

### Post by kn0w-b1nary on 2011-03-03
I always add the flash repository by using Ubuntu Tweak.

---

### Post by bob brazie on 2011-03-03
Not sure what the file it is looking for.

Is there a comand line install command?

---

### Post by gandaran on 2011-03-03
> **bob brazie said:**
> Not sure what the file it is looking for.

Is there a comand line install command?
```
sudo apt-get install flashplugin-installer
```
installing this package is all you need for flash ( only recommend for 32-bits system), if your system is messed up by installing some other flash packages then I recommend installing the firefox [flash-aid]("https://addons.mozilla.org/en/firefox/addon/flash-aid/") addon for helping removing conflicting plugins and installing the correct one.

---

### Post by bob brazie on 2011-03-03
The installer is already shown as installed in the software center. (?)

Using 32 bit system here.

---

### Post by gandaran on 2011-03-03
> **bob brazie said:**
> The installer is already shown as installed in the software center. (?)

Using 32 bit system here.
lets see if it's installed correctly
type these commands and post the output of the last one
```
sudo updatedb
```
```
locate libflash
```

---

### Post by bob brazie on 2011-03-03
bob@bob-HP-Pavilion-dv7-Notebook-PC:~$ bob@bob-HP-Pavilion-dv7-Notebook-PC:~$ sudo updatedb
bob@bob-HP-Pavilion-dv7-Notebook-PC:~$: command not found
bob@bob-HP-Pavilion-dv7-Notebook-PC:~$ locate libflash
/usr/lib/openoffice/basis3.2/program/libflashli.so
bob@bob-HP-Pavilion-dv7-Notebook-PC:~$

---

### Post by gandaran on 2011-03-03
> **bob brazie said:**
> bob@bob-HP-Pavilion-dv7-Notebook-PC:~$ bob@bob-HP-Pavilion-dv7-Notebook-PC:~$ sudo updatedb
bob@bob-HP-Pavilion-dv7-Notebook-PC:~$: command not found
bob@bob-HP-Pavilion-dv7-Notebook-PC:~$ locate libflash
/usr/lib/openoffice/basis3.2/program/libflashli.so
bob@bob-HP-Pavilion-dv7-Notebook-PC:~$
no flash was found installed but the update data-base command didn't work so try again updating the data first.

---

### Post by bob brazie on 2011-03-03
Do you mean issusing the command: sudo apt-get install flashplugin-installer?

because I did not do that as I thought it was already installed.

---

### Post by gandaran on 2011-03-03
> **bob brazie said:**
> Do you mean issusing the command: sudo apt-get install flashplugin-installer?

because I did not do that as I thought it was already installed.
no I mean updating data 
```
sudo updatedb
```
but run the install command too just to see what it spits out

---

### Post by bob brazie on 2011-03-03
bob@bob-HP-Pavilion-dv7-Notebook-PC:~$ sudo apt-get install flashplugin-installer
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
bob@bob-HP-Pavilion-dv7-Notebook-PC:~$ sudo apt-get install flashplugin-installer
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
bob@bob-HP-Pavilion-dv7-Notebook-PC:~$

---

### Post by gandaran on 2011-03-03
> **bob brazie said:**
> bob@bob-HP-Pavilion-dv7-Notebook-PC:~$ sudo apt-get install flashplugin-installer
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
bob@bob-HP-Pavilion-dv7-Notebook-PC:~$ sudo apt-get install flashplugin-installer
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
bob@bob-HP-Pavilion-dv7-Notebook-PC:~$
run in terminal to fix broken packages
```
sudo dpkg --configure -a
```
then the install command again

---

### Post by bob brazie on 2011-03-03
Thanks for the help. The two command seem to have done the trick!

Bob.

---

