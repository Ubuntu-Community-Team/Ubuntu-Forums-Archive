---
title: "Yet another wireless internet question"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by Inferno falcon on 2009-08-27
Yes, it is true, I as well feel the need to post their own thread regarding ubuntu and wireless networks. After 4-5 hours of searching for threads, I decided I might have to post my own.

I am using a belkin f5d7231-4, if that matters.

It seems as though Ubuntu doesn't reconize my network at all, and I'm not sure what to do, seeing as I haven't a clue what I"m doing =P


Any help would be very much appreciated.

Thanks!

---

### Post by Darkwing-Duck on 2009-08-27
Have you tried [ndiswrapper]("http://http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Main_Page")? If not I would try that. 
 
You can install it from the terminal (Alt+F2)
 
```
sudo apt-get install ndiswrapper-common 
```
 
Once you have it installed you can "wrap" your windows driver for WiFi. If you want more information you can read the documentation on thier [SourceForge website]("http://http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Main_Page").
 
If you need more help just let us know!

---

### Post by cariboo on 2009-08-27
What wireless device are you using? If you are not sure, open an Applications-->Accessoreis-->Terminal and type:

```
lspci > lspci.txt
```

This will provide a list of your hardware and output it to a text file called lspci.txt

```
sudo lshw -C network > network.txt
```

This will list all your network devices and tell us if they are detected and the drivers are loaded, the text file will be called network.txt

Copy the text files to your Windows partition and paste the results in your next post.

---

### Post by bkratz on 2009-08-27
> **Inferno falcon said:**
> Yes, it is true, I as well feel the need to post their own thread regarding ubuntu and wireless networks. After 4-5 hours of searching for threads, I decided I might have to post my own.

I am using a belkin f5d7231-4, if that matters.



Thanks!


This is the router itself, what is the wireless card you are using? Is it PCI or USB?

much information can be gained through google or look at this site

[http://www.burnthesorbonne.com/?page_id=20](http://www.burnthesorbonne.com/?page_id=20)


WOT shows this site to be a bad thing---I'm sure it is not

---

### Post by Inferno falcon on 2009-08-27
The sourceforge link appears to be broken, but I do have ndiswrapper, I just don't know how to use it.
 
-

Replier 2 - Here's the log.

Usage: lspci [<switches>]
Basic display modes:
-mm  Produce machine-readable output (single -m for an obsolete format)
-t  Show bus tree
Display options:
-v  Be verbose (-vv for very verbose)
-k  Show kernel drivers handling each device
-x  Show hex-dump of the standard part of the config space
-xxx  Show hex-dump of the whole config space (dangerous; root only)
-xxxx  Show hex-dump of the 4096-byte extended config space (root only)
-b  Bus-centric view (addresses and IRQ's as seen by the bus)
-D  Always show domain numbers
Resolving of device ID's to names:
-n  Show numeric ID's
-nn  Show both textual and numeric ID's (names & numbers)
-q  Query the PCI ID database for unknown ID's via DNS
-qq  As above, but re-query locally cached entries
-Q  Query the PCI ID database for all ID's via DNS
Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]] Show only devices in selected slots
-d [<vendor>]:[<device>]   Show only devices with specified ID's
Other options:
-i <file> Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file> Look up kernel modules in a given file instead of default modules.pcimap
-M  Enable `bus mapping' mode (dangerous; root only)
PCI access options:
-A <method> Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val> Set PCI access parameter (see `-O help' for a list)
-G  Enable PCI access debugging
-H <mode> Use direct hardware access (<mode> = 1 or 2)
-F <file> Read PCI configuration dump from a given file

---

### Post by Liolikas on 2009-08-27
Replier 2 - Here's the log.

Usage: lspci [<switches>]
...
Means you made mistake try just copy paste, but if we know card it is not very important.

Basic info about NdisW here:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by bkratz on 2009-08-27
> **Inferno falcon said:**
> The sourceforge link appears to be broken, but I do have ndiswrapper, I just don't know how to use it.
 
-



This is even a better link it tells how to post a wireless ticket  (the info needed)

[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by Darkwing-Duck on 2009-08-27
Sorry for the link break. Here is the first link and another link that will help you with NDISwrapper.
 
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
 
And the SourceForge page again.
 
[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Main_Page)
 
Maybe this will be able to help you.

---

