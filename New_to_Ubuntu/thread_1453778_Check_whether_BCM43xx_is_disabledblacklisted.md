---
title: "Check whether BCM43xx is disabled/blacklisted"
date: 2010-04-13
forum: New to Ubuntu
---

### Post by lepel on 2010-04-13
Hi,
i'm busy getting my wireless network working on my ubuntu laptop.
I've installed ndiswrapper, I found somewhere on the internet that you can check whether ndiswrapper is properly installed by typing the command: "whereis ndiswrapper"
The output shows "ndiswrapper:" plus the location of three directories, I assume that is correct.
So now I want to check whether BCM43xx is disabled (or blacklisted, is that the same?).
When I type: "whereis bcm43xx"
the output shows: "bcm43xx:"

Does this mean that it is disabled?

Lepel

---

### Post by WinterRain on 2010-04-13
You can check in 
```
gksudo gedit /etc/modprobe.d/blacklist.conf
```

---

### Post by lepel on 2010-04-13
Thanks very much!
Maybe you can help me out in another way,
I finally get a list of installed drivers by typing the command: "ndiswrapper -l", 
but I also get warnings. It says: "All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
Is this bad? What does it mean?
Lepel

---

### Post by lepel on 2010-04-13
Also, when I command "iwconfig" it says: 
lo          no wireless extensions
pan0     no wireless extensions

---

### Post by anewguy on 2010-04-13
When blacklisting the existing broadcom support, I think there may be up to 4 modules that need to be blacklisted.  I know one of them is b43, another is ssb, then your bcm43xx and I think there may also be another with a name something like b43-legacy.  You definitely need to add b43 and ssb to the blacklist.conf file.  Reboot.

After you've done that, do:

sudo ndiswrapper -l  -> if it doesn't show your device now, redo the sudo ndiswrapper -i xxxxxx.inf you did to install your driver the first time, but follow it with the following:

sudo depmod -a

sudo modprobe ndiswrapper

sudo ndiswrapper -m

sudo gedit /etc/modules

scroll to the end of the file and add the following line:

ndiswrapper

save the file, exit the editor and reboot again.

Now check to see if your wireless is working.

Dave ;)

---

### Post by lepel on 2010-04-14
> **anewguy said:**
> When blacklisting the existing broadcom support, I think there may be up to 4 modules that need to be blacklisted.  I know one of them is b43, another is ssb, then your bcm43xx and I think there may also be another with a name something like b43-legacy.  You definitely need to add b43 and ssb to the blacklist.conf file.  Reboot.

After you've done that, do:

sudo ndiswrapper -l  -> if it doesn't show your device now, redo the sudo ndiswrapper -i xxxxxx.inf you did to install your driver the first time, but follow it with the following:

sudo depmod -a

sudo modprobe ndiswrapper

sudo ndiswrapper -m

sudo gedit /etc/modules

scroll to the end of the file and add the following line:

ndiswrapper

save the file, exit the editor and reboot again.

Now check to see if your wireless is working.

Dave ;)

I'm sure all four modules are blacklisted. Still, it doesn't work. When I type the command "sudo modprobe ndiswrapper" it displays the same error as before;
"All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release."

And "ndiswrapper -m" results in about a thousand times the line: "module configuration already contains alias directive" .

---

### Post by lepel on 2010-04-14
Anybody a suggestion?

---

### Post by mcoleman44 on 2010-04-14
Have you tried checking under hardware drivers to see if the driver is listed there? system>admin>hardware drivers

---

### Post by lepel on 2010-04-14
I checked, it can't find anything.
So I guess I have to download a different driver and see if it will work?

---

### Post by achase79 on 2010-04-14
you are going to need to get a wired connection, update and then go to Hardware Manager.  I have a BCM43xx based wifi adapter and it should be able to use the b43 kernel module after you install b43-fwcutter (it requires the net to install successfully) to extract the device firmware.

---

### Post by anewguy on 2010-04-14
The "error" message from ndiswrapper you can ignore.  The messages from modprobe ndiswrapper are just telling you that ndiswrapper is already loaded, so you can ignore those as well.

If you've done everything properly with ndiswrapper and followed all the steps, check network manager and see if you need to enable wireless networking.  Also check to see if any connections are already showing, because if you did everything else correctly (and forget the modprobe ndiswrapper, as it is indicating the module is already loaded) it should work.

Also, if you follow the post above by achase79, remember do to somethings first:

- remove the items you added to blacklist.conf

- sudo ndiswrapper -l   -> for each item returned, do:

sudo ndiswrapper -e xxxxxx where xxxxxx is the driver returned

- via package manager, remove ndiswrapper

- sudo gedit /etc/modules

remove ndiswrapper from that file, save the file and exit

- reboot

THEN do the above post.  Otherwise you'll just have things stepping on each other and nothing will work.

Dave ;)

---

### Post by anewguy on 2010-04-14
By the way, if you need the firmware cutter and can't hard-wire a connection, it is located on the LiveCD you installed from in the /pool/main/b folder.

Dave ;)

---

