---
title: "Use Windows Drivers : help with  Installing ndisgtk package."
date: 2011-04-28
forum: New to Ubuntu
---

### Post by msg_ash on 2011-04-28
I installed ubuntu 10.10 on my acer travelmate 4740(i now dual boot wth windows 7)

I used this link [https://help.ubuntu.com/10.10/internet/C/troubleshooting-wireless.html](https://help.ubuntu.com/10.10/internet/C/troubleshooting-wireless.html)

to figure out why my wireless device isn't being recognised.

on typing : "sudo lshw -C network" , it said UNCLAIMED.
next i located my windows driver file ("bcmwl6.inf" in this case)

next i'm supposed to Install the ndisgtk package.
This is where i need help. I can't connect to the internet using ubuntu, so how do i install this package?? Can i download it with windows  save it on my desktop and open it using ubuntu? (something like the .exe executable files in windows)

Please help.

---

### Post by Leppie on 2011-04-28
you can download it from this page: [http://packages.ubuntu.com/maverick/ndisgtk](http://packages.ubuntu.com/maverick/ndisgtk)

then copy it onto a usb stick and install it on the destination machine by double clicking it, it should launch software-center which then will install the package. there might be some dependencies you will have to download as well.

---

### Post by msg_ash on 2011-04-28
if i try to install the i386 architecture, it says "dependency is not satisfiable" and doesn't allow me to install.

I even tried to install amd64 architecture(i'm guessing it's for amd processors), and it says wrong architecture.


What's happening?

---

### Post by RJ12 on 2011-04-28
There are a few dependencies that are required with ndisgtk, I think there are some python ones and a few ndiswrapper ones too. It would be a whole lot easier if you could temporarily plug in through ethernet

---

### Post by wep940 on 2011-04-28
Please be sure you have exhausted all other options for a native driver before you use ndiswrapper/ndisgtk.  It still works fine, but there are more and more restricted and open-source drivers becoming available you should use if you can.  
 
You can install both ndiswrapper and ndisgtk, with no dependency problems, right from your installation media.  If you used the LiveCD, or a USB flash drive "copy" of the LiveCD, just do the following:
 
[LIST]
[*]boot up ubuntu
[*]mount the installation media.  If a message comes up saying a software package source was found just cancel the message.
[*]look in the /pool/main/n folder on the installation media - there are 2 folders, one for ndisgtk and one for ndiswrapper.  You need to install these in the proper order:
[*]go to the ndiswrapper folder and click on the ndiswrapper common package to begin its installation.  Wait for it to finish.
[*]click on the ndiswrapper utilities package to begin its installation and wait for it to finish.
[*]go back to the /pool/main/n folder
[*]go to the ndisgtk folder and click on the ndisgtk package to begin its installation and wait for it to finish.
[/LIST]Now some other things you need to know:
[LIST]
[*]ndiswrapper (and the simpler GUI'd front end ndisgtk) works with Windows XP drivers *ONLY* - no Windows 7 drivers, for example.
[*]the Windows XP driver must be "unpacked" so that you have the .inf and .sys files available - copy these to your desktop.
[*]the Windows XP driver *MUST* match the architecture you chose for Ubuntu - 32 bit or 64 bit.
[/LIST]Now to install:
[LIST]
[*]Go to system/administration/windows wireless drivers - whenever it asks for a password in this process just use your normal Ubuntu password (it won't show on the screen).  This starts up the GUI'd front-end to ndiswrapper called ndisgtk.
[*]Click on new or add, whatever it is.
[*]Point it to the .inf file for the Windows XP driver that you placed on your desktop earlier (remember all the .inf and .sys files associated with your device must be there).
[*]Click on ok or whatever it is.
[*]It *should* show your device and as active.
[/LIST]

---

### Post by msg_ash on 2011-05-02
Here's the thing - I used a friend's CD to install Ubuntu, I don't have it with me anymore... :(

Could you please explain what you meant by: 
> Please be sure you have exhausted all other options for a native driver ???

---

