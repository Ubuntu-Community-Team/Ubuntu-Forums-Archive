---
title: "Network problem"
date: 2009-08-07
forum: New to Ubuntu
---

### Post by serbforce on 2009-08-07
Hello
I was trying to setup my internet connection. It works only with mac adress that ISP registered when they installed internet. I had to change my network card and tried to change mac manualy and i messed up everything. It created new network connection eth2 and nothing worked after that. I read that solution may be reinstalling complete network tools which i did! i uninstalled it but now i cant install it with package menager becouse i dont have internet connection. 

Is there a way to manualy download that package and then transfer it to the PC in question? or any other solution?
Thanks in advance

Edit: command i used is : sudo apt-get remove purge network-manager net-tools

---

### Post by superprash2003 on 2009-08-07
is Auto eth0 still there? it usually cannot be removed , remove all other instances like eth1 eth2 etc..

---

### Post by Phobiac on 2009-08-07
You can download packages in their .deb file form from [here]("http://packages.ubuntu.com/"). All you should have to do is download the .deb, put it on some form of removable media like a flash drive, and then use that to transer the files. Double clicking on a .deb should bring up an installer, and you'll be good to go. However, you seem to have done a purge, so this process might be painful for you as it possibly removed dependencies as well. The command you said you used wasn't the purge command however
```
sudo apt-get purge packagename
```
is the proper one, the one you said you used would have removed the packages purge, network-manager, and net-tools but left behind configuration files and the like.
If you still have your install cd/dvd, I'd pop that in the drive and then do this command
```
sudo apt-get update && sudo apt-get install network-manager net-tools
```

If that works but your problem persists, try doing
```
sudo apt-get purge network-manger net-tools && sudo apt-get install network-manager net-tools
```
If it continues further after a reboot, we'll need more info to help you out.

---

### Post by cgb on 2009-08-07
Side note: typically you can force most ISP modems to rebind to new MAC address by completely powering down the modem for about 1 minute and then powering it back up connected to the new MAC address device.

---

### Post by Phobiac on 2009-08-07
> **trinidadflores said:**
> I'm having the same type of problem here but mine is with my wireless card.  I did have it working and it works fine in windows.  I did nothing to the setting but now my networking is totally disabled.  how do i get this back.  When it comes to networking with Ubuntu i am ignorent.  I need help.


Trinidad

That's not really a lot of information to go on to help get you up and running again, I'd suggest making another thread with this information:
1) To tell if your wireless card is even recognized and working, the output of ```
sudo ifconfig
```
2) If your wireless card is internal, the output of ```
lspci | grep Wireless
``` Or if your wireless card plugs into a USB port, the output of```
lsusb | grep Wireless
```
To tell the type of wireless card you have.

Those two pieces of information should at the very least give a good foundation for someone to help you out with your problem, but it'd be best to start a new thread to prevent confusion.

---

### Post by trinidadflores on 2009-08-07
1) To tell if your wireless card is even recognized and working, the output of ```
sudo ifconfig
```yes the card is working it is what I am using to connect to the network as we speak in windows. and it works fine when i run ubuntu off of the live disk.
2) If your wireless card is internal, the output of ```
lspci | grep Wireless
``` 02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AGN [Kedron] Network Connection (rev 61)

---

