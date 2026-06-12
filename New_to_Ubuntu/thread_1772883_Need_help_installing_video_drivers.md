---
title: "Need help installing video drivers"
date: 2011-06-01
forum: New to Ubuntu
---

### Post by wizardduder on 2011-06-01
So im fairly new to linux and what my main goal is to play games like morrowind and WoW. so after installing these programs they crash and what i needed was to install the ati graphic card drivers directly from their site so i downloaded them and they would not run. So looking into the guide on the site it says i needed these:
XFree86-Mesa-libGL
&#8226; libstdc++
&#8226; libgcc
&#8226; Free86-libs
&#8226; fontconfig
&#8226; freetype
&#8226; zlib
&#8226; gcc

After looking around i see you get these from repositories. so my question is how do i install these and make them work properly?


Oh and the error message when i try to use the .run i got from the website says this:
gedit has not been able to detect the character encoding.
Please check that you are not trying to open a binary file.
Select a character encoding from the menu and try again.

---

### Post by Locke_99GS on 2011-06-01
You need to install the *build-essential* package first, as the driver will get compiled as a module against your kernel. Then, don't open the .run file, but execute it in a terminal.

---

### Post by Mark Phelps on 2011-06-01
What's your ATI card make and model?  Only the newer HD cards are supported with Linux drivers.  If you don't know, open a terminal, enter "lspci" and look for the line containing "VGA" -- and post the results back here.

---

### Post by seawolf167 on 2011-06-01
Welcome to the forums!

As posted above, please install

```
sudo apt-get install build-essential
```Then download the file, change the working directory to the download location

```
cd /path/to/downloaded file
```this is by default

```
cd ~/Downloads
```make it executable

```
sudo chmod +x *nameoffile*
```then run the file

```
./*nameoffile*
```

If you post the output of 

```
sudo lspci
```in CODE tags, we can make sure you are downloading the correct proprietary drivers

---

### Post by wizardduder on 2011-06-01
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
i saw how to look up the graphics card in a different post but now i get 

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.38-8-generic-pae; make sure that the version is being
correctly set by --iscurrentdistro

now lemme check if i can play my games.

Edit: i checked my games arnt working

---

### Post by seawolf167 on 2011-06-01
Here is your driver [download page ]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English")for your device (Radeon X1200), and the [download link]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-3-x86.x86_64.run") as well as [installation instructions]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat92-inst.pdf").

---

### Post by seawolf167 on 2011-06-01
I should also add the WineHQ links for the installation instructions and notes for the two games you mentioned in your first post:

[The Elder Scrolls III: Morrowind]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=3383")
[World of Warcraft ]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1922")

Of course you'll need Wine to setup the games

```
sudo apt-get install wine
```

---

### Post by wizardduder on 2011-06-01
i mean i have the correct download but as reading the guide it says: ATI recommends you uninstall the ATI Proprietary Linux
Driver before installing a newer version.
so how would i uninstall my current driver?

of course i have wine that was the first thing i looked up when i was on my quest to play wow with linux

---

### Post by marios88 on 2011-06-01
I dont think you have to uninstall them

---

### Post by seawolf167 on 2011-06-01
Take a look here for [un-installation ]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver")instructions.

---

### Post by wizardduder on 2011-06-01
Thanks alot i got em all in good and things are running better. Thanks for you help all.

---

### Post by seawolf167 on 2011-06-01
Glad you got it working!

---

