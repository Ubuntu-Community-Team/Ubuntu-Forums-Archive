---
title: "ATI Driver Problem"
date: 2010-04-12
forum: New to Ubuntu
---

### Post by lanetherif on 2010-04-12
Hello,

whenever I try to open Catalyst Control Center, I get a initialization error that tells me that either no ATI graphics display is installed or it is not functioning properly and that either I have to install the correct ATI driver or configure it using aticonfig. 

Under Hardware Drivers, I am able to see the driver, yet it is reported that although the driver is activated it not currently in use. My installed fglrx version is 2:8.723.1-0ubuntu1 .

I tried to remove and install it again, yesterday. I got impatient and hit reset button before the restart process was completed and had few problems and thanks to forum I was able to solve. After solution, I tried once again and this time waited about 20 minutes which I guess enough for whatever driver was installed, still it didn't restart properly and I once again hit reset button, this time without encountering any problem.

Any clues for where to start?

---

### Post by clhsharky on 2010-04-12
HI

Info please

What release and which ATI card?

Sharky

---

### Post by lanetherif on 2010-04-12
> **clhsharky said:**
> HI

Info please

What release and which ATI card?

Sharky

I'm using an ATI Radeon HD 4850 on 10.04 Lucid Lynx.

---

### Post by e4uforums on 2010-04-12
I just battled with getting the 10.3 catalyst drivers working on Lucid with a 4870x2.  I was not able to get them working correctly.  I installed Karmic (Ubuntu 9.10) and the drivers installed flawlessly with all desktop effects and 3d acceleration working properly.

I read through the testing forums and there are many people having problems with Lucid and ATI cards.  Hopefully a driver update from ATI will fix the issue.

---

### Post by shebaw on 2010-04-12
Install Envy and let it manage your graphics card driver, it may work. I had problems with the graphics card when I updated my wireless modules and Envy fixed it for me. Its worth a try.

---

### Post by lanetherif on 2010-04-12
> **shebaw said:**
> Install Envy and let it manage your graphics card driver, it may work. I had problems with the graphics card when I updated my wireless modules and Envy fixed it for me. Its worth a try.

I've made a little search and I guess it is not available for 10.04. I have to wait either for a driver upgrade or Envy upgrade.

---

### Post by e4uforums on 2010-04-12
> **lanetherif said:**
> I've made a little search and I guess it is not available for 10.04. I have to wait either for a driver upgrade or Envy upgrade.


According to this [http://albertomilone.com/wordpress/?p=477](http://albertomilone.com/wordpress/?p=477) Envy will no longer be updated.  The main developer is going to focus on the default driver manager instead.

---

### Post by lanetherif on 2010-04-12
> **e4uforums said:**
> According to this [http://albertomilone.com/wordpress/?p=477](http://albertomilone.com/wordpress/?p=477) Envy will no longer be updated.  The main developer is going to focus on the default driver manager instead.

Then I have to wait for a driver upgrade... :)

---

### Post by e4uforums on 2010-04-12
> **lanetherif said:**
> Then I have to wait for a driver upgrade... :)

Believe me, I'm in line waiting too!

---

### Post by quadproc on 2010-04-12
> **lanetherif said:**
> Hello,

whenever I try to open Catalyst Control Center, I get a initialization error that tells me that either no ATI graphics display is installed or it is not functioning properly and that either I have to install the correct ATI driver or configure it using aticonfig. If you did not remove the driver before you upgraded the OS then you probably have a corrupted driver.  Usually, the fix for this is to uninstall completely the driver and then reinstall it.

> Under Hardware Drivers, I am able to see the driver, yet it is reported that although the driver is activated it not currently in use. My installed fglrx version is 2:8.723.1-0ubuntu1 .There is a problem in jockey-gtk (the Hardware Drivers utility) which causes it to report that fglrx is not in use when it _is_ actually in use.  the utility does seem to understand that the driver is there but it doesn't know that it is in use.

I am running HD4870x2 and ended up with a corrupt driver when I upgraded from Ubuntu 9.04 to 9.10; I forgot to uninstall the driver first.  Removing and reinstalling the driver fixed the problem that I had.

I suspect that Ubuntu 10.04 has some serious compatibility issues with the fglrx driver so I am waiting a few months to see what shakes out before I take the plunge to 10.04.

I suggest that you do not use Hardware Drivers to get and install your driver; that utility does not give you any insight into what it is doing, nor does it give you any choice regarding the driver.  Instead, copy the version that you want from the ATI web site into some directory of your own.  Then use sudo sh <the_ati_file_name> --keep --install.  This will leave behind the files and directories that the .run file used; you can study these to see how it was done.  You can remove the directory any time after the install succeeds.

> I tried to remove and install it again, yesterday. I got impatient and hit reset button before the restart process was completed and had few problems and thanks to forum I was able to solve. After solution, I tried once again and this time waited about 20 minutes which I guess enough for whatever driver was installed, still it didn't restart properly and I once again hit reset button, this time without encountering any problem.

Any clues for where to start?I am not sure where you were in the process while you were waiting.  It might have been during the driver download time; that can be lengthy because the file is over 80 MB long.  When you start the .run file it won't take long for the ATI install screen to pop up on your screen.  If you wait minutes and nothing happens then I would suspect damaged files.  In that case you probably need to completely remove them and start with a fresh set.

Good luck!

quadproc

---

