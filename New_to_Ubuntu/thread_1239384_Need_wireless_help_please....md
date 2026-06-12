---
title: "Need wireless help please..."
date: 2009-08-13
forum: New to Ubuntu
---

### Post by DarkSaga70 on 2009-08-13
I Just put a Trendnet TEW-643PI Wireless N PCI Adapter in my friends cpu and I have Verizon FIOS the router is not 20 feet from her cpu and I can not figure out how to connect her to the router> There is no indication that there is even a wireless network to connect to? Help please.

---

### Post by Revolutionary101 on 2009-08-13
This thread may be of some help to you.
[http://ubuntuforums.org/showthread.php?t=1031999](http://ubuntuforums.org/showthread.php?t=1031999)

Hope it helps.

---

### Post by DarkSaga70 on 2009-08-13
I see he used ndiswrapper to get it to work but how can I install that if I can not get it online? I mean is there a way to burn it install then go or am I gonna have to just move the entire tower to a wired spot?

---

### Post by ugriffin on 2009-08-13
Simply download a frontend for ndiswrapper from here:

[http://packages.ubuntu.com/jaunty/ndisgtk](http://packages.ubuntu.com/jaunty/ndisgtk)

Download all the "Related" packages and "ndisgtk" and then pass those packages on a usb or something to the PC you're trying to hook to the internet.


EDIT: I've been seeing the entire package structure for ndiswapper, and, yep, it's easier to just move the tower to somewhere with cabled internet. Or, download all the dependencies for "ndisgtk" one by one.

---

### Post by Revolutionary101 on 2009-08-13
You could use a Ubuntu computer which is already connected to the internet to put the .deb file on a flash drive or something like that. To do that open the Synaptic Package Manager on the Ubuntu computer connected to the internet. Then search for ndiswrapper and mark it for installation. When you have done that go to File>Generate package download script then put the script on whatever you are going to use to transfer the .deb files over to the other computer. Then open that folder and double click the .sh file and it will download the .deb files so you can install them on the computer with no internet connection.

Edit: or you could use the post before this one for help. I have looked at it and that seems simpler.

---

### Post by ugriffin on 2009-08-13
^ Lol, didn't know that trick. Thanks for that, really helps in updating those computers with only ethernet.

---

### Post by Revolutionary101 on 2009-08-13
> **ugriffin said:**
> ^ Lol, didn't know that trick. Thanks for that, really helps in updating those computers with only ethernet.

No problem glad I could help.

---

### Post by bkratz on 2009-08-13
> **ugriffin said:**
> Simply download a frontend for ndiswrapper from here:



EDIT: I've been seeing the entire package structure for ndiswapper, and, yep, it's easier to just move the tower to somewhere with cabled internet. Or, download all the dependencies for "ndisgtk" one by one.


Isn't ndisgtk (and all the dependancies)  on the installation disk, which the OP could go to system administration synaptic package manager settings repositories and put a check in the position for cd rom?  I could be wrong, I did it on a wired connection!

---

### Post by DarkSaga70 on 2009-08-13
Ok I installed ndiswrapper and rebooted and it still does not try to connect to my network. Suggestions?

---

### Post by bkratz on 2009-08-13
> **DarkSaga70 said:**
> Ok I installed ndiswrapper and rebooted and it still does not try to connect to my network. Suggestions?


Did you run the program ndiskgtk and install the windows drivers (inf file/s ?) previously obtained?

---

### Post by DarkSaga70 on 2009-08-13
> **bkratz said:**
> Did you run the program ndiskgtk and install the windows drivers (inf file/s ?) previously obtained?

Yes i installed the pkgs and rebooted and no prompt to join any networks or nothing.

---

### Post by bkratz on 2009-08-13
> **DarkSaga70 said:**
> Yes i installed the pkgs and rebooted and no prompt to join any networks or nothing.

Go to system-preferences-Network Connections and select the wireless tab and enter in the require information for the new connection.

---

