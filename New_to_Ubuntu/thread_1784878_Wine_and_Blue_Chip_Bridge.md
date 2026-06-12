---
title: "Wine and Blue Chip Bridge"
date: 2011-06-17
forum: New to Ubuntu
---

### Post by jud1929 on 2011-06-17
Hello,
I'm having trouble installing Blue Chip Bridge Demo under Wine in Ubuntu 11.04.
It did run under 9.04, however, I don't recall how I did it. I have searched on the internet and tried multiple methods. 
The software site offers a choice of downloads, one a zip file, the other executable. I have received an error message saying that the executable bit is not set.

The site is 
[http://www.bluechipbridge.co.uk/demo.htm](http://www.bluechipbridge.co.uk/demo.htm)


Thank you for your help.

I don't know if it matters but I changed  to the Gnome desktop. Also the computer is an Asus 900a. I used Synaptic to install Wine. Thanks again.

---

### Post by e79 on 2011-06-17
I do not play bridge but could try this trial without problems. _Are you using the latest wine version (1.3.20) ?_ Try this :
 
**1.** Add the PPA for Ubuntu Wine repositories at [https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa) for your specific distribution (Natty, Maverick or Lucid)
 
**2. **```
**sudo apt-get update && sudo apt-get dist-upgrade**
```
 
**3. **```
**sudo apt-get install wine**
```
 
**4. **Download the .ZIP version found at [http://www.bluechipbridge.co.uk/downloads/Blue_Chip_Bridge_Demo_Zip.zip](http://www.bluechipbridge.co.uk/downloads/Blue_Chip_Bridge_Demo_Zip.zip)
 
**5. **Put it in your home folder, extract everything, get into the extracted folder, right-click the **'Blue_Chip_Bridge_Demo.exe'** and choose **'Open with Wine Windows Program Loader'.**
 
The result is show on the attached picture.
 
Hope this helps **:D**

---

### Post by jud1929 on 2011-06-19
Thank you for your help.

My eventual solution was to learn about file permissions and set the file to executable.

I made some error somewhere in attempting to follow your advice. I tried to uninstall my old version of wine and replace it with 1.3.2 . I didn't realize it at first but somewhere I went wrong and had the same old version and the same difficulty receiving the error message regarding the executable bit.

At that point I used      chmod u+x filename       command to make the file executable.


The file then opened with wine program loader. An entry was not placed in the wine programs menu so I moved the program to the  desktop and surprising it works just by clicking.
  
Again, thank you.

---

### Post by e79 on 2011-06-20
The pleasure is all mine :)

---

