---
title: "problem with video driver"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by Artanis.ro on 2010-01-26
Hello,

I have a huge problem with my video card driver. I can't view libnotify notifications and openoffice doesn't work as well.

I have an old compaq laptop and the video card is ATI radeon M6 LY. I have used the tutorial I found here [http://http://swiss.ubuntuforums.org/showthread.php?t=899178]("http://http//swiss.ubuntuforums.org/showthread.php?t=899178")
Also, system monitor doesn't work. It shows a black window with small dots in it. Libnotify also is displayed the same. 

Can someone tell me how can I fix this? I am running ubuntu 9.

Thank you very much, your help is much appreciated.

---

### Post by blazemore on 2010-01-26
Can you install the driver from System -> Administration -> Hardware Drivers?

---

### Post by jd65pl on 2010-01-26
What do you get from

```
sudo glxinfo | grep -iE 'direct'
```

and

```
sudo fglrxinfo
```

---

### Post by Artanis.ro on 2010-01-27
> **jd65pl said:**
> What do you get from

```
sudo glxinfo | grep -iE 'direct'
```and

```
sudo fglrxinfo
```


X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  16
  Current serial number in output stream:  16


and on the second code

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  16
  Current serial number in output stream:  16

---

### Post by jd65pl on 2010-01-27
It would seem that you haven't completed or followed the instructions you provided a link to correctly. Either go back and have another go at the instructions or give blazemore's idea a go.

---

### Post by skymera on 2010-01-27
Not sure if it'll work but try EnvyNG.

I've used it to install my ATi and Nvidia driver for years on Ubuntu. I find it tends to have more success than Jockey

---

### Post by halitech on 2010-01-27
The instructions you followed were for 8.04, not for 9.04 or 9.10. I think with the vintage of the machine you are using, you will not be able to get the propritary drivers or the drivers from the ati website to work on this machine and you should look at either using the opensource radeon or ati drivers that Ubuntu ships with.

---

### Post by warfacegod on 2010-01-27
> **skymera said:**
> Not sure if it'll work but try EnvyNG.

I've used it to install my ATi and Nvidia driver for years on Ubuntu. I find it tends to have more success than Jockey

```
sudo apt-get install envyng-core
```

---

### Post by Artanis.ro on 2010-01-28
> **jd65pl said:**
> It would seem that you haven't completed or followed the instructions you provided a link to correctly. Either go back and have another go at the instructions or give blazemore's idea a go.


Yes, there is a problem during the install. I get an error in terminal when I do this:
```
sudo apt-get install compiz-fusion-* emerald-themes

```Here is the error:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting compiz-fusion-bcop for regex 'compiz-fusion-*'
Note, selecting compiz-fusion-plugins-unofficial for regex 'compiz-fusion-*'
Note, selecting compiz-fusion-plugins-extra for regex 'compiz-fusion-*'
Note, selecting compiz-fusion-plugins-unsupported for regex 'compiz-fusion-*'
Note, selecting compiz-fusion-plugins-main for regex 'compiz-fusion-*'
emerald-themes is already the newest version.
The following extra packages will be installed:
  compiz-fusion-plugins-unofficial compiz-fusion-plugins-unsupported
The following NEW packages will be installed:
  compiz-fusion-plugins-unofficial compiz-fusion-plugins-unsupported
0 upgraded, 2 newly installed, 0 to remove and 15 not upgraded.
Need to get 0B/791kB of archives.
After this operation, 2,216kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 140016 files and directories currently installed.)
Unpacking compiz-fusion-plugins-unofficial (from .../compiz-fusion-plugins-unofficial_0.0.2~git20070921+3v1ubuntu0_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/compiz-fusion-plugins-unofficial_0.0.2~git20070921+3v1ubuntu0_i386.deb (--unpack):
 trying to overwrite '/usr/lib/compiz/lib3d.so', which is also in package compiz-fusion-plugins-extra 0:0.8.4-0ubuntu2
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking compiz-fusion-plugins-unsupported (from .../compiz-fusion-plugins-unsupported_0.5.2~git20071006+3v1ubuntu0_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/compiz-fusion-plugins-unsupported_0.5.2~git20071006+3v1ubuntu0_i386.deb (--unpack):
 trying to overwrite '/usr/share/compiz/3d.xml', which is also in package compiz-fusion-plugins-extra 0:0.8.4-0ubuntu2
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-fusion-plugins-unofficial_0.0.2~git20070921+3v1ubuntu0_i386.deb
 /var/cache/apt/archives/compiz-fusion-plugins-unsupported_0.5.2~git20071006+3v1ubuntu0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```I have now stopped at step 11 of the tutorial I posted in my first thread's opening post.

I could really use a hand.

Also, here the answer I get now from the 2 code questions u asked me at your first post:

```
direct rendering: Yes
``` for the ```
sudo glxinfo | grep -iE 'direct'
```and for ```
sudo fglrxinfo
``` it tells me "command not found" but if I use "su" this is what I get:
```
The program 'fglrxinfo' is currently not installed.  You can install it by typing:
apt-get install xorg-driver-fglrx
``` But if I am right the tutorial actually tells me to uninstall fglrx (at step 6).





> **warfacegod said:**
> ```
sudo apt-get install envyng-core
```

Thank you. I have only one problem with this. I am a NOOB. I dont understand exactly the term "driver" on ubuntu. I know very well what means driver on any version of Windows and I want to switch to linux.

So, my question is: this envyng-core is the driver? or is some video utility or theme?

---

### Post by Artanis.ro on 2010-01-28
Sorry for the double post, but I have 2 new errors when I start ubuntu:

Sorry, the package "compiz-fusion-plugins-unsupported 0.5.2~git20071006 + 3v1ubuntu0" failed to install or upgrade

You can help the developers........


Sorry, the package "compiz-fusion-plugins-unofficial 0.0.2~git20070921 +3v1ubuntu0" failed to install or upgrade

You can help developers.........

---

### Post by jd65pl on 2010-01-28
> **Artanis.ro said:**
> 
Also, here the answer I get now from the 2 code questions u asked me at your first post:

```
direct rendering: Yes
``` for the ```
sudo glxinfo | grep -iE 'direct'
```and for ```
sudo fglrxinfo
``` it tells me "command not found" but if I use "su" this is what I get:
```
The program 'fglrxinfo' is currently not installed.  You can install it by typing:
apt-get install xorg-driver-fglrx
``` But if I am right the tutorial actually tells me to uninstall fglrx (at step 6).


These steps were just to confirm you weren't using fglrx. You can also check you are using the radeon drivers with the command below.

```
lspci -v | grep -iE 'radeon'
```

As you are having some issues with basic graphics rendering I would stay clear of the niceties of compiz etc for the time being, lets not put the graphics card under unnecessary stress at the moment. Remove it (compiz) and see if you have some better graphics performance with regard to the problems you were having.

```
sudo apt-get purge compiz-fusion-* emerald-themes
```

> Thank you. I have only one problem with this. I am a NOOB. I dont understand exactly the term "driver" on ubuntu. I know very well what means driver on any version of Windows and I want to switch to linux.
BTW the meaning of driver is the same for any OS.

---

### Post by Artanis.ro on 2010-01-28
ok, I have uninstalled compiz. Please tell me why do I have the emerald themes error? Or what does that error mean?

Regarding my missing notions about linux, I know that the driver is called driver on every OS. What I don;t understand is what is fglrx? (is this a driver?), what is compiz (driver?) and what is envyng-core? (which btw I've installed, though I don't understand if it needs configuration or not).


on the 
```
lspci -v | grep -iE 'radeon'
```

I get

```
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
    Kernel modules: radeon, radeonfb
```

---

### Post by jd65pl on 2010-01-28
fglrx is a proprietary ATI driver
Compiz and emerald are desktop enhancements i.e. effects
Envy is an application to auto configure the graphics driver.

google is always your friend in working out what things are.

You shouldn't need envy now as you already have an appropriate graphics driver in use

---

### Post by warfacegod on 2010-01-28
> **Artanis.ro said:**
> Yes, there is a problem during the install. I get an error in terminal when I do this:
```
sudo apt-get install compiz-fusion-* emerald-themes

```Here is the error:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting compiz-fusion-bcop for regex 'compiz-fusion-*'
Note, selecting compiz-fusion-plugins-unofficial for regex 'compiz-fusion-*'
Note, selecting compiz-fusion-plugins-extra for regex 'compiz-fusion-*'
Note, selecting compiz-fusion-plugins-unsupported for regex 'compiz-fusion-*'
Note, selecting compiz-fusion-plugins-main for regex 'compiz-fusion-*'
emerald-themes is already the newest version.
The following extra packages will be installed:
  compiz-fusion-plugins-unofficial compiz-fusion-plugins-unsupported
The following NEW packages will be installed:
  compiz-fusion-plugins-unofficial compiz-fusion-plugins-unsupported
0 upgraded, 2 newly installed, 0 to remove and 15 not upgraded.
Need to get 0B/791kB of archives.
After this operation, 2,216kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 140016 files and directories currently installed.)
Unpacking compiz-fusion-plugins-unofficial (from .../compiz-fusion-plugins-unofficial_0.0.2~git20070921+3v1ubuntu0_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/compiz-fusion-plugins-unofficial_0.0.2~git20070921+3v1ubuntu0_i386.deb (--unpack):
 trying to overwrite '/usr/lib/compiz/lib3d.so', which is also in package compiz-fusion-plugins-extra 0:0.8.4-0ubuntu2
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking compiz-fusion-plugins-unsupported (from .../compiz-fusion-plugins-unsupported_0.5.2~git20071006+3v1ubuntu0_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/compiz-fusion-plugins-unsupported_0.5.2~git20071006+3v1ubuntu0_i386.deb (--unpack):
 trying to overwrite '/usr/share/compiz/3d.xml', which is also in package compiz-fusion-plugins-extra 0:0.8.4-0ubuntu2
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-fusion-plugins-unofficial_0.0.2~git20070921+3v1ubuntu0_i386.deb
 /var/cache/apt/archives/compiz-fusion-plugins-unsupported_0.5.2~git20071006+3v1ubuntu0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```I have now stopped at step 11 of the tutorial I posted in my first thread's opening post.

I could really use a hand.

Also, here the answer I get now from the 2 code questions u asked me at your first post:

```
direct rendering: Yes
``` for the ```
sudo glxinfo | grep -iE 'direct'
```and for ```
sudo fglrxinfo
``` it tells me "command not found" but if I use "su" this is what I get:
```
The program 'fglrxinfo' is currently not installed.  You can install it by typing:
apt-get install xorg-driver-fglrx
``` But if I am right the tutorial actually tells me to uninstall fglrx (at step 6).







Thank you. I have only one problem with this. I am a NOOB. I dont understand exactly the term "driver" on ubuntu. I know very well what means driver on any version of Windows and I want to switch to linux.

So, my question is: this envyng-core is the driver? or is some video utility or theme?

envy will assist you in finding your proper video driver. Driver means the same thing in Linux as it does in Windows.

---

