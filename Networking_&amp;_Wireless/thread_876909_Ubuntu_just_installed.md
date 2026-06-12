---
title: "Ubuntu just installed"
date: 2008-08-01
forum: Networking &amp; Wireless
---

### Post by chopstiks on 2008-08-01
...and I cannot get any internet connections to work. it keeps asking me for the Ubuntu getty disk to install the ndiswrapper etc. 

Can anyone help? am i doing something wrong?
i dont have the administrator disk, i just want to be able to use wireless internet on it.. thanks i hope!:(

---

### Post by Kevbert on 2008-08-01
First thing is to find out what wireless card you re using.  Go to Applications-Accessories-Terminal and enter the following:
```
lshw -C network
```
To copy the text, highlight it with the mouse and copy it by going to Edit-Copy.  Post the output here with Ctrl+V.

---

### Post by chopstiks on 2008-08-01
the wirless card is a trendnet and the support said trendnet is not compatible. 

so i used a pc network connection to at least just try and get this laptop working but i get an error to install administrator disks every time i go to install a driver or go to system package manager

---

### Post by Kevbert on 2008-08-01
To get rid of the CD problem. Go to System-Administration-Software Sources. Under the Ubuntu Tab is seems you may have the CDROM ticked (click on that to remove the tick).  You want all the other boxes ticked on this tab.  Now go to the Update Tab and make sure Important, Recommended, Unsupported and Check for updates boxes are ticked all other should be unticked.  When you click on Close you may find you have a few software packages to download.

---

### Post by chopstiks on 2008-08-01
thankyou!! i will try this !

---

### Post by chopstiks on 2008-08-02
> **Kevbert said:**
> First thing is to find out what wireless card you re using.  Go to Applications-Accessories-Terminal and enter the following:
```
lshw -C network
```
To copy the text, highlight it with the mouse and copy it by going to Edit-Copy.  Post the output here with Ctrl+V.


ok, i really dont know what im doing, I was given this laptop with ubuntu installed and I have to get internet working, I dont know anything about computers!!! here is the output.

WARNING: YOU SHOULD RUN THIS PROGRAM AS SUPER-USER
*-network
description: Ethernet interface
product: 82801DB PRO/100 VE (MOB) Ethernet Controller
vendor: Intel Corporation
physical id: 8
bus info: pci@0000:02:08:0
logical name: eth0
version: 81
serial: 00:0d:60:13:38:9f
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=e100driverversion=3.5.17-k4-NAPI firmware=N/A ip=169.254.5.2 latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes

---

### Post by Kevbert on 2008-08-02
That didn't help much.  Please try the following commands in terminal (they may not help us though):
```
iwconfig
ifconfig
```
Do you know the trendnet model ?  There are a number of models listed on the [[COLOR="Red"]Ndiswrapper website[/COLOR]]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/") at the bottom of the page.  Is it one of these ?

---

### Post by chopstiks on 2008-08-02
> **Kevbert said:**
> That didn't help much.  Please try the following commands in terminal (they may not help us though):
```
iwconfig
ifconfig
```
Do you know the trendnet model ?  There are a number of models listed on the [[COLOR="Red"]Ndiswrapper website[/COLOR]]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/") at the bottom of the page.  Is it one of these ?

iwconfig output is:
lo    no wireless extensions
irda0  no wireless extensions
eth0  no wireless extensions

ifconfig returns some data for eth0 and lo  -  what do you need exactly as i cannot copy and paste.

the trendnet wireless card is called TEW-624

the guy that installed ubuntu on my laptop plugged his network connection in and internet worked great! he didnt install any drivers or do anything special, so when i come home to use my internet i have no idea where to start!

ipconfig is

---

### Post by Kevbert on 2008-08-02
For this you need the Windows wireless drivers for your wireless modem.
Your wireless is not mentioned on the NDISwrapper web site so it's possible that this won't work.  It's probably best for you to install the Ubuntu repository version which you can install via System-Administration-Synaptic Package Manager.  Enter your log-in password when prompted.  Click on Search and enter ndiswrapper.  Now you should see three packages mentioned.  Right-click on each of the boxes in turn and select mark for installation.  Now click on Apply to install them.  Close Synaptic.
Now go to System-Administration-Windows Wireless Drivers.  Click on Install New Driver and in the window that is displayed click on the folder icon and browse to where the Windows wireless drivers are.  The rest should be straightforward.

---

### Post by chopstiks on 2008-08-02
> **Kevbert said:**
> For this you need the Windows wireless drivers for your wireless modem.
Your wireless is not mentioned on the NDISwrapper web site so it's possible that this won't work.  It's probably best for you to install the Ubuntu repository version which you can install via System-Administration-Synaptic Package Manager.  Enter your log-in password when prompted.  Click on Search and enter ndiswrapper.  Now you should see three packages mentioned.  Right-click on each of the boxes in turn and select mark for installation.  Now click on Apply to install them.  Close Synaptic.
Now go to System-Administration-Windows Wireless Drivers.  Click on Install New Driver and in the window that is displayed click on the folder icon and browse to where the Windows wireless drivers are.  The rest should be straightforward.

i actually tried what you just mentioned from reading another post but when i try to install that i get an error :

W: failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/ndiswrapper](http://us.archive.ubuntu.com/ubuntu/pool/main/ndiswrapper)... etc etc

---

### Post by Kevbert on 2008-08-02
That's interesting.  As I was writing my last post earlier I installed ndiswrapper-common, ndiswrapper-utils-1.9, ndisgtk via Synaptic.  These are the three packages that you require.  I've just tried your link to the US server (and mine to the UK one) and both give a 404 (unreachable) error.  It may be that the Servers are down for maintenance.
In Synaptic you can try another server by selecting Settings-Repositories and changing the 'Downloading from:' to Main or anything else you want.  Give it a few hours and try again.  If you still have problems let me know.

---

### Post by chopstiks on 2008-08-03
> **Kevbert said:**
> That's interesting.  As I was writing my last post earlier I installed ndiswrapper-common, ndiswrapper-utils-1.9, ndisgtk via Synaptic.  These are the three packages that you require.  I've just tried your link to the US server (and mine to the UK one) and both give a 404 (unreachable) error.  It may be that the Servers are down for maintenance.
In Synaptic you can try another server by selecting Settings-Repositories and changing the 'Downloading from:' to Main or anything else you want.  Give it a few hours and try again.  If you still have problems let me know.

thanks!! I did that and am now getting the error:

Could not download all repository indexes

The repository might no longer be available or could not be contacted because of network problems.....

---

### Post by chopstiks on 2008-08-04
> **chopstiks said:**
> thanks!! I did that and am now getting the error:

Could not download all repository indexes

The repository might no longer be available or could not be contacted because of network problems.....

An error occurred

The following details are provided:

E: I wasn't able to locate file for the ndiswraper-common package. this might mean you need to manually fix the package

---

### Post by Kevbert on 2008-08-04
You need to run the following command in terminal
```
sudo apt-get install -f
```
to fix the damaged package.  It's possible that the package may be removed, so watch the messages.  You may want to do a
```
sudo apt-get update
```
afterwards.

---

### Post by chopstiks on 2008-08-04
> **Kevbert said:**
> You need to run the following command in terminal
```
sudo apt-get install -f
```
to fix the damaged package.  It's possible that the package may be removed, so watch the messages.  You may want to do a
```
sudo apt-get update
```
afterwards.

thanks - but im even more lost now than when i started. it seems that i just wanted to install a wireless driver for trendnet TEW-624 and now im running commands to manually fix and find ndiswrapper and I have no idea what im doing.

the error i am getting now when i type sudi get-apt update is a long error (i cant copy and paste as the laptop obviously has no network connection)

Failed to fetch [http://archive.ubuntu.com/](http://archive.ubuntu.com/).......

e: Unable to lock the administration directory (/var/lib/dpkg), is another process using it?

---

### Post by chopstiks on 2008-08-04
Hi again - have had enough of this... just want internet working. And dont have any more time past today to spend on it.

What wireless device can i go and buy, and when I simply put it in this laptop its going to work?

trendnet 624 which i currently own doesnt appear to be compatible?

I have looked at the list - i just want a wireless connection i can plug in and go.

HELP! thank you

---

### Post by Kevbert on 2008-08-04
Sorry I think I've gone off on a tangent.  What version of Ubuntu are you using ? Gutsy 7.10 or Hardy 8.04 ?  I'll see if I can get hold of the packages and then I'll try and attach them to my next post.

---

### Post by chopstiks on 2008-08-04
> **Kevbert said:**
> Sorry I think I've gone off on a tangent.  What version of Ubuntu are you using ? Gutsy 7.10 or Hardy 8.04 ?  I'll see if I can get hold of the packages and then I'll try and attach them to my next post.

hey kev - its Gutsy 7.10 by the looks of things

---

### Post by Kevbert on 2008-08-04
OK. ndiswrapper is on your Gutsy disk.  Put the disk in your CD drive and after a short while a window will appear (Nautilus File manager) showing some files.  If not click on the Ubuntu icon that is displayed (the CD) to display Nautilus.  Now click on the Pool folder, main, n, ndiswrapper and then double click on ndiswrapper-common_1.43-1ubuntu2_all.deb (the actual version may be different).  Package Installer will be displayed.  Click on Install Package.  If everything goes to plan you'll have installed your first 'deb' package (deb is short for Debian what Ubuntu is based on).
In the same folder there will be a ndiswrapper-utils deb.  Double click on that and install it.
I'm going to try to track down the graphical installer for the ndiswrapper program, so I'll need to reboot into 7.10.  It will be with my next post.

---

### Post by chopstiks on 2008-08-04
> **Kevbert said:**
> OK. ndiswrapper is on your Gutsy disk.  Put the disk in your CD drive and after a short while a window will appear (Nautilus File manager) showing some files.  If not click on the Ubuntu icon that is displayed (the CD) to display Nautilus.  Now click on the Pool folder, main, n, ndiswrapper and then double click on ndiswrapper-common_1.43-1ubuntu2_all.deb (the actual version may be different).  Package Installer will be displayed.  Click on Install Package.  If everything goes to plan you'll have installed your first 'deb' package (deb is short for Debian what Ubuntu is based on).
In the same folder there will be a ndiswrapper-utils deb.  Double click on that and install it.
I'm going to try to track down the graphical installer for the ndiswrapper program, so I'll need to reboot into 7.10.  It will be with my next post.


thank you so much... but i think i have to throw in the towel as i dont have the disk!! someone installed this for me a week ago to avoid all the viruses on my laptop so i could do some work for my job... but it just seems impossible to get internet functioning... UGH!!!

---

### Post by Kevbert on 2008-08-04
I forgot to ask whether your Ubuntu is 64 bit or 32 bit.  I've included both deb packages for ndisgtk (the graphical interface installer for your windows drivers).
You want to download the file for your system (amd64 - 64 bit, i386 - 32 bit) to the desktop by right-clicking on it and select save link as, and then double click on it to run the package installer and then install the file.
Now go to System-Administration-Windows Wireless Drivers. Click on Install New Driver and in the window that is displayed click on the folder icon and browse to where the Windows wireless drivers are.
Hopefully this will solve your problem........

---

### Post by chopstiks on 2008-08-04
> **Kevbert said:**
> I forgot to ask whether your Ubuntu is 64 bit or 32 bit.  I've included both deb packages for ndisgtk (the graphical interface installer for your windows drivers).
You want to download the file for your system (amd64 - 64 bit, i386 - 32 bit) to the desktop and then double click on it to run the package installer and then install the file.
Now go to System-Administration-Windows Wireless Drivers. Click on Install New Driver and in the window that is displayed click on the folder icon and browse to where the Windows wireless drivers are.
Hopefully this will solve your problem........

thanks but how do i install it when the laptop is not connected to the network?  do i just copy those fiules onot a memory card and put into the laptop?? thank you again!!

---

### Post by chopstiks on 2008-08-04
> **Kevbert said:**
> I forgot to ask whether your Ubuntu is 64 bit or 32 bit.  I've included both deb packages for ndisgtk (the graphical interface installer for your windows drivers).
You want to download the file for your system (amd64 - 64 bit, i386 - 32 bit) to the desktop and then double click on it to run the package installer and then install the file.
Now go to System-Administration-Windows Wireless Drivers. Click on Install New Driver and in the window that is displayed click on the folder icon and browse to where the Windows wireless drivers are.
Hopefully this will solve your problem........

oh my god - when i try to install yur files Kevc it says ERROR: DEPENDENCY IS NOT SATIDFIABLE: NDISWRAPPER-UTILS-1.9

and ERROR: WRONG ARCHITECTURE "amd64"

---

### Post by Kevbert on 2008-08-04
Here's the deb that you need to install. Copy it to your PC desktop and then double click on it (to run Package Installer).  Then do the same for the 32 bit file ndisgtk_0.7.2-1ubuntu1_i386.deb which I sent you in my last post.  You can ignore the other file sent in my last post as you have 32 bit Gutsy 7.10 on your PC.

---

### Post by chopstiks on 2008-08-04
> **Kevbert said:**
> Here's the deb that you need to install. Copy it to your PC desktop and then double click on it (to run Package Installer).  Then do the same for the 32 bit file ndisgtk_0.7.2-1ubuntu1_i386.deb which I sent you in my last post.  You can ignore the other file sent in my last post as you have 32 bit Gutsy 7.10 on your PC.

thanks again! latest error though is

Error: Dependency is not satisfiable 

when i try and double click on the new file you just sent me!@

---

### Post by Kevbert on 2008-08-04
We've gone full circle...
Put your Gutsy 7.10 CD in the drive. Go to System-Administration-Software Sources. Under the Ubuntu Tab tick the CDROM with Gutsy Gibbon box (click on that to add the tick). It may ask you to reload sources (do that, ignore any errors). Go to System-Administration-Synaptic Package Manager and search for ndiswrapper.  Right-click on the ndiswrapper-utils-1.9 box and select Install from the menu that appears.  All dependences should be looked after from there (as the files are on the CD).  Once this has been installed you can try re-installing the ndisgtk file I sent you.
If this works you can then go back to Software Sources and remove the tick from the CD box so that you don't have to keep on putting the CD in the drive.
Please post what happens.

---

### Post by ktrnka on 2008-08-04
Sorry, misread the post

---

