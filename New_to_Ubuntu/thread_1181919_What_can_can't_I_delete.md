---
title: "What can/ can't I delete?"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by TikiGoodrich on 2009-06-08
[COLOR=black][FONT=Verdana]My wife's Dell Mini is unable to perform updates because the hard drive is full. When I look in the file system I see a lot of file names that I do not know how to interpret. What can I remove? What must stay intact? Any help would be greatly appreciated.[/FONT][/COLOR]

---

### Post by Celauran on 2009-06-08
You could start by clearing out the apt cache.

```
sudo apt-get clean
```

You could also free up a little space by installing localepurge and getting rid of language files you don't need.

---

### Post by Hospadar on 2009-06-08
You might want to google around on linux filesystem tutorials and also cleaning up ubuntu type guides, the docs link in my sig might provide some helpful info on the latter.

Basically:
Anything in your home folder that you don't want you can probably safely delete.  If you show hidden files in your home folder, you'll see a ton of .config .this .that .etc looking files and folders.  These all have configuration data for programs in them. Generally you don't want to delete them for that reason (also they are very tiny so it wouldn't really help)

Probably what you do want to look into is cleaning up /temp (or /tmp) and /var
var tends to have a lot of logs and stuff in it that are often uneeded. 

In general, if you arn't sure as to whether or not something can be safely deleted, just rename it and see if things still work, and if so, then go on to actually deleting the file.

---

### Post by amingv on 2009-06-08
As a rule of thumb, anything you haven't copied yourself or that is owned by root should stay there.
In short, just stuff from your home folder (or you can uninstall appications you don't use).
It'd really be hard to tell you exactly what to or not to delete, since your configuration can be very different from anyone else's.

---

### Post by furialis on 2009-06-08
I would make a backup of anything I wanted to save and install a lighter version of Ubuntu. Check out [Xubuntu.]("http://www.xubuntu.org/news/9.04-release")

Just out of curiosity, how big is the HD?

---

### Post by _Purple_ on 2009-06-08
You can check this howto thread and see if your trash is using up the disk space
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

---

### Post by iponeverything on 2009-06-08
This will list all the installed packages sorted by size.


```
dpkg-query -W --showformat='${Installed-Size;10}\t${Package}\n' | sort -k1,1n
```

you can remove a package with:

dpkg -r <package name>

If you're not sure if you need the package you might post back for advice or google it.

---

### Post by TikiGoodrich on 2009-06-08
This is what the work order from my local dell dealer said after I took it in "The system isn't updating becuase the hard disk is 100% full.  The computer has a tiny hdd at only 4GB.  It is probabbly flash based and cannot upgrade without ordering a special drive.  The customer can go through and remove some files that aren't needed and then run some updates.  There is no dell recovery partion I can desize either."  The home folder only has about 11MB worth of files.  Every file in the File System is labeled as root. So now what?

---

### Post by CatKiller on 2009-06-08
> **TikiGoodrich said:**
> The computer has a tiny hdd at only 4GB. It is probabbly flash based and cannot upgrade without ordering a special drive.

4GB is pretty tiny these days. It might be worth getting a larger solid-state drive for it, either from Dell if you have a good relationship with them, or from somewhere else if you can find one cheaper. I'd imagine that there are detailed instructions for doing the replacement in one of the manuals for the machine.

Otherwise, it means being pretty brutal about what you install to keep the usage down, purging /var/log regularly, and cleaning out the apt cache of all the packages that you've installed.

---

### Post by H2SO_four on 2009-06-08
I couldn't imagine having that small of storage space. I would be limited to word processing and basic internet stuff.  A few music or .avi files and you are full to the brim!  

Another OS with a smaller "footprint" may be appropriate in this case.

---

### Post by Bucky Ball on 2009-06-08
Ubuntu Netbook Remix sounds like it might be just the thing.

---

### Post by snowpine on 2009-06-08
A lot of Dell Mini users seem to like installing Ubuntu 9.04 Netbook Remix. My understanding is that will leave you with about 1gb free. Good instructions on this site: [http://www.ubuntumini.com/2009/04/user-guides-for-ubuntu-904-juanty.html](http://www.ubuntumini.com/2009/04/user-guides-for-ubuntu-904-juanty.html) 

If you are open to a different user interface (other than Gnome), there are some "smaller" versions of Ubuntu: Xubuntu, Crunchbang, etc. Then there are hundreds of other, non-Ubuntu Linux distros, ranging in size all the way down to the 30mb SliTaz...

Some good advice in this thread too: [http://ubuntuforums.org/showthread.php?t=1178741](http://ubuntuforums.org/showthread.php?t=1178741)

And you will definitely want an SD card for storing personal files (leaving the internal SSD drive free for system files). The ultimate solution would be one of these: [http://www.mydigitaldiscount.com/CategoryProductList.jsp?cat=Browse+By+Brand:RunCore:RunCore+PCI+Express+Mini+PCI-e+SSDs:Dell+Inspiron+Mini+9+PCI-e+SSDs](http://www.mydigitaldiscount.com/CategoryProductList.jsp?cat=Browse+By+Brand:RunCore:RunCore+PCI+Express+Mini+PCI-e+SSDs:Dell+Inspiron+Mini+9+PCI-e+SSDs)

---

### Post by joyneo04 on 2009-06-08
Its really tough to say what to delete and what not to delete...one thing i would like to suggest is that before deleting please keep a back of of all the data....

---

### Post by CJ Master on 2009-06-08
With that small of space I would recommend you do a command-line install with Ubuntu alternate CD.

---

