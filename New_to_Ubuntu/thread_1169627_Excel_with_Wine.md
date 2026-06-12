---
title: "Excel with Wine ?"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by CoCoKnots on 2009-05-25
OpenOffice does not do some of the routines I need for my study program. Is there a way to load & run Excel using Wine?

---

### Post by shifty_powers on 2009-05-25
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=11](http://appdb.winehq.org/objectManager.php?sClass=application&iId=11)

---

### Post by CoCoKnots on 2009-05-25
> **shifty_powers said:**
> [http://appdb.winehq.org/objectManager.php?sClass=application&iId=11](http://appdb.winehq.org/objectManager.php?sClass=application&iId=11)


This is interesting... However, it looks like a case where the operation may be a success but the patient is going to die anyway. I notice this side effect from the link for 'Wine' in getting this to work.

"VBA and macro recording actually WORKS when DCOM98 is installed and ole32, oleaut32 and rpcrt4 overrides are used. However these overrides cause Excel to crash in file open/save."

Also, I believe I need to install Excel using the entire set of disc including the 'Installer'. I'm a Nube and not sure how that works using wine.

---

### Post by ulfj on 2009-05-25
Sorry don't want to hijack the thread,but what routines won't work?Just wondering.

---

### Post by CoCoKnots on 2009-05-25
> **ulfj said:**
> Sorry don't want to hijack the thread,but what routines won't work?Just wondering.

Originally I setup a spreadsheet in Open Office. One of the sheets was to import data from the web daily and work as a data base for reference in other areas. The macros I was using failed when I tried to automate the process. Individually each step worked fine. I broke down & purchased the 'M-' Excel and setup the spreadsheet again. I am running Excel on a desktop with windows xp. It works fine now on that machine, but the notebook computer I have Ubuntu on is developing issues and about to die.

 This is the only program I need Windows to run... Everything else is great & I really like the Linux environment. When I replace the notebook I would rather do something other than Microsoft... If I can't get Excel to work in Wine or on an Apple MacBook, I may have to go back to a notebook using M/S Windows OS... Not by choice.

---

### Post by Steelmourne on 2009-05-25
You could try to rewrite macros for openoffice spreadsheet. Also make sure you are using openoffice 3.1 which may fix the issue. This guide explains how to install it and also sets up automatic updates for openoffice: 

news.**softpedia**.com/news/How-to-**Install**-**OpenOffice**-org-3-1-on-**Ubuntu**-9-04-111105.shtml

---

### Post by sandyd on 2009-05-25
ill give you what you need

Applications -> Accessories -> Terminal

Copy and paste
```

sudo apt-get install -y cabextract
wget http://wine.budgetdedicated.com/archive/ubuntu/intrepid/wine_1.1.16~winehq0~ubuntu~8.10-0ubuntu1_i386.deb
sudo dpkg -i wine_1.1.16~winehq0~ubuntu~8.10-0ubuntu1_i386.deb
 wget http://winezeug.googlecode.com/svn/trunk/winetricks
sudo mv winetricks /usr/bin/winetricks
sudo chmod 777 /usr/bin/winetricks

```[B]Office 2003 (includes excel)
[/B]just pop the cdrom in, open the cdrom in ubuntu, and run setup.exe
afterwords...
```

winecfg

```go over to Libraries tab, add new override for riched20.dll. click on the item that just appeared on the list, click "edit" and select "native"
 you might also wanna go over to the "About" tab and slap your name in. 

[B]
Office 2007 (also includes excel)
[/B]```

winetricks msxml3 vcrun2005 vcrun2005sp1 wsh56

```Then just double click on "Setup.exe" (inside the cd)
afterwords...
```

winecfg

```go over to Libraries tab, add new override for riched20.dll. click on the item that just appeared on the list, click "edit" and select "native"
then also add usp10 as an override
you might also wanna go over to the "About" tab and slap your name in.

---

### Post by CoCoKnots on 2009-05-25
I have tried using the macros in OpenOffice 3.0 without any luck. The issue has been experienced by others & the 'bug' reported. Perhaps v3.1 might correct the problem. I will try that first.

Carlee I am using Hardy. Will your suggestions work 8.04 ?

---

### Post by sandyd on 2009-05-25
change the lines 
```

wget http://wine.budgetdedicated.com/archive/ubuntu/intrepid/wine_1.1.16~winehq0~ubuntu~8.10-0ubuntu1_i386.deb
sudo dpkg -i wine_1.1.16~winehq0~ubuntu~8.10-0ubuntu1_i386.deb

```to

```

wget http://wine.budgetdedicated.com/archive/ubuntu/hardy/wine_1.1.16~winehq0~ubuntu~8.04-0ubuntu1_i386.deb
sudo dpkg -i  wine_1.1.16~winehq0~ubuntu~8.04-0ubuntu1_i386.deb

```

p.s. Don't use the latest version of wine, all versions of wine past 1.1.16 have a bug that seems to be inhibiting the installation of office.

---

### Post by CoCoKnots on 2009-05-25
> **carlee said:**
> change the lines 
```

wget http://wine.budgetdedicated.com/archive/ubuntu/intrepid/wine_1.1.16~winehq0~ubuntu~8.10-0ubuntu1_i386.deb
sudo dpkg -i wine_1.1.16~winehq0~ubuntu~8.10-0ubuntu1_i386.deb

```
to

```

wget http://wine.budgetdedicated.com/archive/ubuntu/hardy/wine_1.1.16~winehq0~ubuntu~8.04-0ubuntu1_i386.deb
sudo dpkg -i  wine_1.1.16~winehq0~ubuntu~8.04-0ubuntu1_i386.deb

```

Great... Thanks.

---

### Post by albinootje on 2009-05-25
> **CoCoKnots said:**
> OpenOffice does not do some of the routines I need for my study program. Is there a way to load & run Excel using Wine?

Which MS-Office version are you referring to ?
MS-Office 2007 gets a bronze medal in the CrossOverLinux database, and is apparently fairly usable, and older MS-Office versions like MS-Office-XP get a silver medal, MS-Office-97 a gold one.

There's several howto's about how to make MS-Office 2007 run with Wine in Ubuntu.

---

### Post by sandyd on 2009-05-26
> **albinootje said:**
> Which MS-Office version are you referring to ?
MS-Office 2007 gets a bronze medal in the CrossOverLinux database, and is apparently fairly usable, and older MS-Office versions like MS-Office-XP get a silver medal, MS-Office-97 a gold one.

There's several howto's about how to make MS-Office 2007 run with Wine in Ubuntu.
crossover linux database tests are based on WINE 1.01, i believe. The latest (in development version) of wine would offer him the best stuff... but im afraid you can't install it on the latest. All versions past 1.1.16 have a regression that fries the isntaller

---

