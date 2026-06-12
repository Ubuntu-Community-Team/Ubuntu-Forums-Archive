---
title: "[SOLVED] Removing ndiswrapper"
date: 2007-07-22
forum: Networking &amp; Wireless
---

### Post by Mark_in_Hollywood on 2007-07-22
I know nothing of wifi. A friend loaned my his Linksys WUSB 11v4 wireless usb adapter. With much trial and errror I was able to get it working on my desktop computer. I did this so as to help my pal, when I went to install the adapter on his (now Linux Ubuntu) laptop. It's working.

HOWEVER, I have ndiswrapper and whatever all it does to the kernel left behind and it's preventing me from operating a D-link (wda 2320) pci wireless adapter card. Their is a clash of drivers or packages.

HOW do I remove all of ndiswrapper and is that a good idea? I've seen any number of posts that talk about "blacklisting" ndiswrapper. Is that enough?  

Whatever Synaptic Pkg. Mgr. had in the way of MadWiFi, I've installed. Does it and ndiswrapper and the wusb drivers need removing? 

Anybody with experience with 2 networking cards on the same computer, please advise.

Thanks.

---

### Post by fredj on 2007-07-23
To remove ndiswrapper open a terminal and type 'sudo modprobe -r ndiswrapper'
You can also then go to the System->Administration->Synaptic Package Manager. Search for ndiswrapper
and mark all the installed packages for removal.

---

### Post by Mark_in_Hollywood on 2007-07-23
Thank you, but I think you are in great error. After following:

sudo modprobe -r ndiswrapper and making:

locate ndiswrapper

I see line after line of the module or package remaining in various locations such as:

/etc/ndiswrapper

/lib/modules/2.6.20-16-generic/kernel . . . many many sub and sub-sub directories here

/var/cache has a few

I used Synaptic Pkg. Mgr. to see what part of ndiswrapper is installed and it shows that no packages are installed.

MY question is: how do I get the OS to remove those packages?

---

### Post by Ayuthia on 2007-07-23
I am guessing that you installed ndiswrapper manually.  If that is the case, you still will need to remove the ndiswrapper entry out of /etc/modules.  You also take out the .inf that was installed also.  That could be done by:

sudo ndiswrapper -e <driver>

where <driver> is the name of the .inf file that you used.  You will need to enter it without the .inf extension (example: sudo ndiswrapper -e bcmwl5 -- if your driver is bcmwl5.inf).  

Then you will need to go to the directory where you installed ndiswrapper.  It could be something like /home/user/ndiswrapper-1.47.  You will need to go into that directory and type:
sudo make uninstall

That should remove the installation.

---

### Post by Mark_in_Hollywood on 2007-07-24
sudo ndiswrapper -e WUSB11v4 returned

bash: ndiswrapper: command not found

and

switching to /home/mark/ndiswrapper-147/WUSB11v4_08272004/Drivers

and sudo make uninstall returned

make: *** ANo rule to make target `uninstall'. Stop.

---

### Post by Ayuthia on 2007-07-24
> **Mark_in_Hollywood said:**
> sudo ndiswrapper -e WUSB11v4 returned

bash: ndiswrapper: command not found
It sounds like ndiswrapper is no longer there as a program.


> **Mark_in_Hollywood said:**
> switching to /home/mark/ndiswrapper-147/WUSB11v4_08272004/Drivers

and sudo make uninstall returned

make: *** ANo rule to make target `uninstall'. Stop.
You probably need to be in /home/mark/ndiswrapper-147.  I am guessing that is where the compile stuff is located.  The uninstall needs to be done in the same path where you did the 'make install'.

If there are files in /etc/ndiswrapper, you will need to go in there and remove them because that is what 'ndiswrapper -e' does.

---

### Post by Mark_in_Hollywood on 2007-07-24
> **Ayuthia said:**
> It sounds like ndiswrapper is no longer there as a program.

You probably need to be in /home/mark/ndiswrapper-147.  I am guessing that is where the compile stuff is located.  The uninstall needs to be done in the same path where you did the 'make install'.

If there are files in /etc/ndiswrapper, you will need to go in there and remove them because that is what 'ndiswrapper -e' does.

I was in /home/mark/ndiswrapper-147

I was in etc/ndiswrapper

---

### Post by kevdog on 2007-07-24
Sounds like ndiswrapper might be already gone.

Do this to confirm

```
sudo modprobe -r ndiswrapper 
sudo updatedb
locate ndiswrapper <---Delete any locations it specified
locate loadndisdriver <---Delete any locations specified
```

---

### Post by Mark_in_Hollywood on 2007-07-24
OK

all of ndis is GONE!

Now, how do I add the madwifi drivers, etc to /usr/src?

---

