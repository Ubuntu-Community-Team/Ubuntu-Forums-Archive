---
title: "How to install flash"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by Bat-es on 2009-06-04
Hello all,

I'm still very new to Ubuntu, and I'm trying to install flash, with no success.

I've downloaded the .deb file from [http://www.adobe.com/products/flashplayer/productinfo/instructions/](http://www.adobe.com/products/flashplayer/productinfo/instructions/) 

When I run the .deb file I get the error message:

[I]Only one management too is allowed to run at the same time

Please close the other application e.g. 'Update Manager', 'aptitude' or 'Synaptic' first.[/I]

But as far as I know I don't have any of these open, and can't see anything I can close.

Any ideas?

Thanks

---

### Post by aysiu on 2009-06-04
Do you have Add/Remove open?

---

### Post by Bat-es on 2009-06-04
No add/remove isn't open.

I've tried restarting so I'm sure nothing is running and clicking the .deb file st thing - still says the same error message!

---

### Post by freakyruft on 2009-06-04
why not
```

sudo apt-get install flashplugin-nonfree

```
?

---

### Post by Bat-es on 2009-06-04
> **freakyruft said:**
> why not
```

sudo apt-get install flashplugin-nonfree

```
?

When I enter this into terminal, it asks for my password. After entering my password I get the message

*E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. *

Any ideas??

---

### Post by aysiu on 2009-06-04
I would wait until a more knowledgeable forum member confirms this is safe to do, but I would think (if you really know you have no package management apps open) you could paste this command in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo rm /var/lib/apt/lists/lock
``` and that may do the trick.

---

### Post by aysiu on 2009-06-04
[quote=Bat-es]When I enter this into terminal, it asks for my password. After entering my password I get the message

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

Any ideas??[/quote] Oh, then you just paste this command into the terminal to fix it: ```
sudo dpkg --configure -a
```

---

### Post by Bat-es on 2009-06-04
Ok, thanks very much for that. I've now managed to run the .deb file, and it installed successfully.

But... when I go to any site using firefox that uses flash it still says I need to download flash.

Is there something else I need to do?

---

### Post by aysiu on 2009-06-04
> **Bat-es said:**
> Ok, thanks very much for that. I've now managed to run the .deb file, and it installed successfully.

But... when I go to any site using firefox that uses flash it still says I need to download flash.

Is there something else I need to do?
That's weird. Do you have the NoScript extension perhaps?

---

### Post by freakyruft on 2009-06-04
Just because I'm new to the forum doesn't mean I'm new to linux...
I have also tried to install the adobe flashplayer (downloaded) some time ago and discovered that the flashplugin-nonfree works just the same, but managed by apt, so all is configured correctly.
Have you restarted firefox yet?
If so, I think you have to add the firefox plugin manually - There is a way to do this, but I can't remember clearly how (too long ago). Have you read [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash) ?

---

### Post by Bat-es on 2009-06-04
Ah, (feels sheepish), turns out it was actually Java I was wanting to install, not flash. But flash will be very useful too, so thanks for that!

So... I've been following the instructions to get java here [http://www.java.com/en/download/help/5000010500.xml#selfextracting](http://www.java.com/en/download/help/5000010500.xml#selfextracting)

but not doing so well.

What's the easiest way to et java, if you can spare a bit more advice!?

---

### Post by Tholley on 2009-06-04
You should be able to install Java from your Add/Remove or Synaptic Package Manager, I believe.

---

### Post by Tholley on 2009-06-04
You might check out this link too.
 
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by oldos2er on 2009-06-04
> **Bat-es said:**
> So... I've been following the instructions to get java here [http://www.java.com/en/download/help/5000010500.xml#selfextracting](http://www.java.com/en/download/help/5000010500.xml#selfextracting)

but not doing so well.

What's the easiest way to et java, if you can spare a bit more advice!?

 You might want to read [https://help.ubuntu.com/9.04/add-applications/C/index.html](https://help.ubuntu.com/9.04/add-applications/C/index.html) and [http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)

---

### Post by Miljet on 2009-06-04
```
sudo apt-get install sun-java6-jre sun-java6-fonts sun-java6-plugin
```

---

### Post by Bat-es on 2009-06-05
> **Miljet said:**
> ```
sudo apt-get install sun-java6-jre sun-java6-fonts sun-java6-plugin
```

Thanks for the help.

When I type the above in the terminal I get the following:

[I]alex@alex-desktop:~$ sudo apt-get install sun-java6-jre sun-java6-fonts sun-java6-plugin
[sudo] password for alex: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jre is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic libseda-java mbr
  libdvdread3
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed
  sun-java6-fonts sun-java6-plugin
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 3784B of archives.
After this operation, 217kB of additional disk space will be used.
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse sun-java6-fonts 6-13-1 [1832B]
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse sun-java6-plugin 6-13-1 [1952B]
Fetched 3784B in 0s (24.5kB/s)         
Selecting previously deselected package sun-java6-fonts.
(Reading database ... 174094 files and directories currently installed.)
Unpacking sun-java6-fonts (from .../sun-java6-fonts_6-13-1_all.deb) ...
Selecting previously deselected package sun-java6-plugin.
Unpacking sun-java6-plugin (from .../sun-java6-plugin_6-13-1_i386.deb) ...
Setting up sun-java6-doc (6-13-1) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6u10-docs.zip jdk-6u10-docs-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort[/I]]

I get the same message when I try and upgrade package updates as well. Here's a screenshot from trying to uupgrade ubuntu:

[IMG]http://i715.photobucket.com/albums/ww152/Bat-es/Screenshot-1.png[/IMG]

Any ideas??

---

