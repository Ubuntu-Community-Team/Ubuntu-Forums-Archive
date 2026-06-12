---
title: "Printer Prob."
date: 2011-08-26
forum: New to Ubuntu
---

### Post by lbenn1950 on 2011-08-26
I have a Canon pixma mg6120 printer that I haven't been able to get it to work in Ubuntu 11.04 I called Canon support and they have no driver for Ubuntu does anyone know where I can get one?

---

### Post by e79 on 2011-08-26
Have you looked at this post ?

[http://ubuntuforums.org/showthread.php?t=1656821](http://ubuntuforums.org/showthread.php?t=1656821)

---

### Post by lbenn1950 on 2011-08-26
Yes and it didn't do me any good at all. packages and common and filter WTF are they talking about? I have an amd64 3000 processor.  All I want is a driver that I can install to get my printer to work. You know put it in the cd and run and good. Otherwise Ubuntu what good is it?

---

### Post by e79 on 2011-08-26
First of all, let me tell you that **Ubuntu is NOT Windows**; and it is NOT Ubuntu's fault if the manufacturer did not released a simplier package to install as you would do in Windows. Though the process is quite simple , I will give you the command lines to install those drivers so you can learn a bit while configuring. As you are new to Linux, I can understand your frustration but believe me, a little command line is quite effective and you should at least learn the very basic of it

So, let say you downloaded the packages in your Downloads folder. Open up a terminal and type these commands :

For the first driver needed

Get into the Downloads folder:
```
cd Downloads
```Uncompress the .TAR archive:
```
tar -zxvf cnijfilter-mg6100series-3.40-1-deb.tar.gz
```Get into the newly uncompressed folder:
```
cd cnijfilter-mg6100series-3.40-1-deb/
```Launch the installation:
```
sudo ./install.sh
```I cannot proceed further on my computer since I do not have this printer and don't want to bloat my installation.

Now lets get back one folder (to the Downloads folder actually)
```
cd ..
```Uncompress the second .TAR archive:
```
tar -zxvf scangearmp-mg6100series-1.60-1-deb.tar.gz

```Get into the newly uncompressed folder:
```
cd scangearmp-mg6100series-1.60-1-deb/
```And again, launch the installation:
```
sudo ./install.sh
```Once done, you should be able to install/add your printer by going to the GUI Printing administration (see attached print screen):
If using Ubuntu 10.04-10.10: Administration --> Printing
If using Ubuntu 11.04+ with Unity: Simply type 'Printing' in the Search menu and click on the icon.

And BTW :
> I have an amd64 3000 processor.This as nothing to do with your present issue.

Hope this helps

---

### Post by PapaGary on 2011-08-26
As another option go to this page:

[http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html](http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html)

and follow the instructions at the top of the page.

---

### Post by sandyd on 2011-08-26
> **e79 said:**
> First of all, let me tell you that **Ubuntu is NOT Windows**; and it is NOT Ubuntu's fault if the manufacturer did not released a simplier package to install as you would do in Windows. Though the process is quite simple , I will give you the command lines to install those drivers so you can learn a bit while configuring. As you are new to Linux, I can understand your frustration but believe me, a little command line is quite effective and you should at least learn the very basic of it

So, let say you downloaded the packages in your Downloads folder. Open up a terminal and type these commands :

For the first driver needed

Get into the Downloads folder:
```
cd Downloads
```Uncompress the .TAR archive:
```
tar -zxvf cnijfilter-mg6100series-3.40-1-deb.tar.gz
```Get into the newly uncompressed folder:
```
cd cnijfilter-mg6100series-3.40-1-deb/
```Launch the installation:
```
sudo ./install.sh
```I cannot proceed further on my computer since I do not have this printer and don't want to bloat my installation.

Now lets get back one folder (to the Downloads folder actually)
```
cd ..
```Uncompress the second .TAR archive:
```
tar -zxvf scangearmp-mg6100series-1.60-1-deb.tar.gz

```Get into the newly uncompressed folder:
```
cd scangearmp-mg6100series-1.60-1-deb/
```And again, launch the installation:
```
sudo ./install.sh
```Once done, you should be able to install/add your printer by going to the GUI Printing administration (see attached print screen):
If using Ubuntu 10.04-10.10: Administration --> Printing
If using Ubuntu 11.04+ with Unity: Simply type 'Printing' in the Search menu and click on the icon.

And BTW :
This as nothing to do with your present issue.

Hope this helps
hmm. maybe I should pkg this....
might help some people....

but ill wait until Im sure this works, and my Ubuntu VM starts up...

---

### Post by e79 on 2011-08-26
> **PapaGary said:**
> As another option go to this page:

[http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html](http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html)

and follow the instructions at the top of the page.
+ 1

That's indeed even simplier lol  :tongue:

---

### Post by e79 on 2011-08-26
> **sandyd said:**
> hmm. maybe I should pkg this....
might help some people....

but ill wait until Im sure this works, and my Ubuntu VM starts up...

Kind of you but not sure its needed anymore after seeing **PapaGary**'s link ;)

---

