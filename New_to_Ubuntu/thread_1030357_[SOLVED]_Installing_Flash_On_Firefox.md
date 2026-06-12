---
title: "[SOLVED] Installing Flash On Firefox"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by Monrizzy on 2009-01-04
I'm trying to install flash to Firefox.  After I download it the install files go to the package installer and it tells me "Only one software managment tool is allowed to run at the same time"

I'm brand new to Ubuntu and I'm not even sure how to determine what is running other than what I can see on the tool bar at the bottom of the screen.

If anyone has time please help!!!

---

### Post by mbzn on 2009-01-04
It should install when you access the page that needs it, you got a message that directed you to the adobe site. I guess this is how you got the file (.deb). The problem is you have annother installer open.
Close all the windows you see then try again, if that doesn't work reboot and try again.

Hope this helps

---

### Post by steveneddy on 2009-01-04
please close out all of your windows, open a terminal and copy/paste this in the terminal.

```
sudo apt-get install flashplugin-nonfree
```

It really is that easy.

Takes mere seconds and you will be done.

---

### Post by Monrizzy on 2009-01-04
When I pasted the above mentioned command in the terminal I got the following

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


---

### Post by Monrizzy on 2009-01-04
When I enter the command
  > dpkg --configure -a
It tells me 
> dpkg: requested operation requires superuser privilege

---

### Post by Monrizzy on 2009-01-04
Superuser Sounds kinda cool.... How do I become one?

---

### Post by zzHanks on 2009-01-04
Edit. Tom--d has the solution, I gave you the command to become root user.
-
You become a super user by typing ```
sudo -i 
```But be careful

---

### Post by Tom--d on 2009-01-04
When you want to do an administrative task, you want to put "sudo" infront of your command you want.

So, in your case, it would be:
```
sudo dpkg --configure -a 
```

More info: [http://en.wikipedia.org/wiki/Sudo](http://en.wikipedia.org/wiki/Sudo)

---

### Post by kansasnoob on 2009-01-04
> **Tom--d said:**
> When you want to do an administrative task, you want to put "sudo" infront of your command you want.

So, in your case, it would be:
```
sudo dpkg --configure -a 
```

More info: [http://en.wikipedia.org/wiki/Sudo](http://en.wikipedia.org/wiki/Sudo)

+1!

As far as flash goes I'd just install ubuntu-restricted-extras either from synaptic or run this command in terminal:

```
sudo apt-get install ubuntu-restricted-extras
```

NOTE: Of course change "ubuntu" to xubuntu or kubuntu if that is appropriate.

I've also found that Flashblock vastly improves my flash performance, but I recommend installing the newest version by going to (in Firefox) Tools > Add-ons > Get Add-ons. Then just search for and install Flashblock. (The repo version doessn't work well with FF 3.0.5).

---

### Post by Monrizzy on 2009-01-04
Thanks everyone....

With this kind of help I may actually learn something & that was the whole point for me. 

Thanks again!!!

---

### Post by Monrizzy on 2009-01-04
This problem is back...

Any attempt @ starting the install process gets stopped.

> **Only one software management tool is allowed to run at the same time**

> Please close the other application e.g. 'Update Manager','aptitude' or 'Synaptic' first.

I'm not sure how to get out of this jam.

---

### Post by Monrizzy on 2009-01-04
By-the-way

This message comes when I'm in the Package Installer

---

### Post by kansasnoob on 2009-01-04
> **Monrizzy said:**
> By-the-way

This message comes when I'm in the Package Installer

That usually shows up if you have a combination of the update manager, terminal, or synaptic open at the same time.

So, (the gui way), go to System > Administration > System Monitor and click on the Processes tab.

It's pretty easy to forget you have the terminal or something open using multiple desktops.

---

### Post by kansasnoob on 2009-01-04
Or just restart!

---

### Post by newbee70 on 2009-01-05
> **Monrizzy said:**
> This problem is back...

Any attempt @ starting the install process gets stopped.





I'm not sure how to get out of this jam.

use the gui: in 8.04.1

go into applications : add/remove; select all available applications/
do a search on ubuntu that will bring up ubuntu restricted put a check in it and the install flashplayer which is the right below it.

let it do the work for you.

---

### Post by Monrizzy on 2009-01-05
Thanks for the info newbee70,  but I've got flash working I'm just having a problem anytime I try to install anything else.  I was trying to install Deluge when it told me
> **Only one software management tool is allowed to run at the same time**

> Please close the other application e.g. 'Update Manager','aptitude' or 'Synaptic' first. 

---

### Post by Monrizzy on 2009-01-05
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

This is the message I get when I try to install Deluge from Add/Remove Programs...

When I open a terminal and enter command  sudo dpkg --configure -a  I get the following

> Setting up initramfs-tools (0.92bubuntu16) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
ln: cannot remove `/boot/initrd.img-2.6.27-9-generic.dpkg-bak': No such file or directory
cp: `/boot/initrd.img-2.6.27-9-generic' and `/boot/initrd.img-2.6.27-9-generic.dpkg-bak' are the same file
dpkg: subprocess post-installation script returned error exit status 1


---

### Post by Monrizzy on 2009-07-05
Unfortunately i'm still experiencing this problem.  Is there anyone out there who has any advice.  I've dragged this issue on for a number months.  I just kept using windows.  I think I'm ready to make the switch now.

---

