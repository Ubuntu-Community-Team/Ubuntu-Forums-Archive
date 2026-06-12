---
title: "Help installing new Canon printer"
date: 2010-12-15
forum: New to Ubuntu
---

### Post by russcb on 2010-12-15
Hi everyone!
I really need a step by step dummies guide for installing my new Canon MX340 wireless printer.
I have downloaded the following files from the Canon site 
1. [COLOR="Blue"]MX340 series ScanGear MP Ver. 1.50 for Linux (rpm Packagearchive)[/COLOR] and 
2. [COLOR="Blue"]MX340 series IJ Printer Driver Ver. 3.30 for Linux (rpm Packagearchive)[/COLOR][COLOR="Black"][/COLOR] 
I have also download the respective debian packages.

The question now is how do I install the downloaded packages??

The printer has also been setup under WindowsXP and is working OK using the wifi connection.

Any help would be very much appreciated.

---

### Post by walt.smith1960 on 2010-12-15
RPM packages cannot be installed natively in Ubuntu, as far as I know.  You have to use a program called Alias to 'translate' them.  .deb packages should be easy, there are a couple GUI options.  One is Gdebi and the other is Ubuntu Software Center. It depends on which version of Ubuntu you have. Gdebi is available in Synaptic if you need it.   .deb files seem very much like Windows .exe installers, you just need an installation manager like Gdebi or Ubuntu Software Center.  They can be installed from the command line as well but GUIs are usually more familiar for newer users.  If the package installs correctly, restart and see what happens.  Hope this helps.  

Edit:  Here is a thread you may or may not be aware of:  [http://forums.linux-foundation.org/read.php?25,12125](http://forums.linux-foundation.org/read.php?25,12125)  This seems to indicate a pretty easy install.

---

### Post by russcb on 2010-12-16
Thanks walt.smith1960 for you reply!

I persisted and found the Gdebi and installed the .deb packages. I now have printer access, however no scanning yet. I will investigate further when time permits.
Thanks again.

---

