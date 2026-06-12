---
title: "printing with hp products"
date: 2011-08-18
forum: New to Ubuntu
---

### Post by ToniTonelli on 2011-08-18
Ubuntu 9.10
Cups 1.41
HPLIP 3.7.11
Printer = HP Deskjet 2050 J510 series
Computer HP Desktop with AMD 64 bit dual core

I am having difficulty getting this particular printer to work, but it seems like many are having problems with other HP printers, so maybe there is a generic way to solve many problems.

I have been trying for several days to stumble on the correct way to get this printer to work.

I have tried to make with 'disable foomatic-rip, enable foomatic-rip-hplip.
Deleting all printers and turning on again
I have tried so many things I don't understand, just cut and pasted lines of commands for Tar-gz, make things with options that I don't understand.

However, every time I get the same result:System Administration, Printing, Right Click printer, properties, ink/toner levels, Status Messages = Printer 'Deskjet 2050 j510 Series' 'cups missing filter'

How do i look for and activate this missing filter, in very simple terms.

Frustrated in Cleveland

Additional note, I have another computer running Ubuntu 10,04 LTS. Identical problem.
I was using a HP psc 1315 all in one for years, the paper mechanism gave out and I bouth this printer as a replacement.

---

### Post by Daveth on 2011-08-18
seems to be a bit patchy even when you do get it running
[HTML]http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_2050_j510_series.html[/HTML]

that said, this seems to suggest a solution, though it is Ubuntu version-specific

[HTML]https://answers.launchpad.net/ubuntu/+source/hplip/+question/140685[/HTML]

---

### Post by robdls on 2011-08-18
i am also having printer problems with acer aspire one and hp officejet 6500

---

### Post by LowSky on 2011-08-19
use hplip from hp's site

[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

---

### Post by ToniTonelli on 2011-08-19
Thanks Daveth and LowSky. I have been to HPLIP and downloaded version 3.7.11
I have used the Wizard and installed automatically, I have downloaded the tarball and installed with make "foomatic-rip, enable foomatic-rip-hplip.
Nothing works, The maddening status message of 'cups-missing-filter' is always present.  Do I need to tell cups to look at hplip or something.

So far I have been to foomatic, HPLIP, and Cups website but getting nowhere.

---

### Post by nomko on 2011-08-19
First go to synaptic and search for hplip packages. Mark all those files for removal and deinstall them. Then open a terminal and type (copy/paste) this command: **sudo apt-get purge hplip***. 
 
The download the hplip driver from [http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html). Unzip the tarball (rightclick and select unzip here). In a terminal go to the directory where the tarball is unzipped. Then install the hplip driver again. 
 
I've noticed that 9.10 is not mentioned on the download page of HPLIP. Using the driver for 10.04 should work because the driver doesn't differ. You just download the same driver for the various Ubuntu versions.

---

