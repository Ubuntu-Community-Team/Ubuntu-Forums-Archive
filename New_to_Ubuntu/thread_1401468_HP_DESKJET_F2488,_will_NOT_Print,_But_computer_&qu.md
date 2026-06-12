---
title: "HP DESKJET F2488, will NOT Print, But computer &quot;Sees&quot; it,  Help What Next ?"
date: 2010-02-08
forum: New to Ubuntu
---

### Post by Ronok on 2010-02-08
Hi 
Printer will Not print ? Need help

**HP DESKJET F2488 (All-in-One Print & Scan)**
100% Ubuntu: 9.10 
Gnome: 2.28.1
Kernel: 2.6.31-19-generic
CPU: Pentium(R) Dual-Core E5300  @ 2.60GHz


**Tried:**
zhou@Zhou-Dian-Nao:~$ lsusb
Bus 001 Device 005: ID 03f0:7611 Hewlett-Packard
[B]
Then,
system> administration> "Printing"> [/B]
new, searching for printers, select device, 
(it shows up as)"HP Deskjet F2400 (CN9841N1T405BS)"
searching for available drivers, downloadable drivers,
Choose Driver, HP...
(it only offers) 
"HP Deskjet F2200 Series hpijs, 3.9.8 {en} (recogmended)"
Describe Printer, would you like to print a test page ? Yes
Test Page submitted as job 6, ok

**BUT NO PRINTING**

[URL="http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?lc=en&dlc=en&cc=lamerica_nsc_carib&product=3964429&lang=en&"]went to HP Web:[SIZE="1"]
-Select your operating system
-Which operating system is used with your product?
-Don't see your operating system?
-If your operating system is not listed above, HP does not have software or driver downloads available for this product in that operating system.
[/SIZE][/URL]


Everything else about this new 100% UBUNTU install
(my at least the 8th household brought over to UBUNTU)
Looks & works great 

**whole village watching... Need to Print**

I am very entry level with regard to code
what should I do Next ?
Thanks for your Help
Ronok

[[SIZE="1"]http://www.gongkuo.com/china16shanxi1.htm[/SIZE]]("http://www.gongkuo.com/china16shanxi1.htm")

---

### Post by blazemore on 2010-02-08
```
wget http://prdownloads.sourceforge.net/hplip/hplip-3.9.12.run
```
```
./hplip-3.9.12.run
```
Follow the instructions

---

### Post by Ronok on 2010-02-08
Thanks & sorry **seems I need help with:**
"**Permissions**"


100%[====================>] 21,379,309  59.1K/s   in 3m 41s  

2010-02-08 19:28:43 (94.4 KB/s) - `hplip-3.9.12.run' saved [21379309/21379309]

zhou@Zhou-Dian-Nao:~$ ./hplip-3.9.12.run
bash: ./hplip-3.9.12.run: **Permission** denied
zhou@Zhou-Dian-Nao:~$ sudo ./hplip-3.9.12.run
[sudo] password for zhou: 
sudo: ./hplip-3.9.12.run: command not found
zhou@Zhou-Dian-Nao:~$ 

(now in the time of writing this...
2 neighbours want ubuntu also ...)

thanks
R

---

### Post by warfacegod on 2010-02-08
Just for kicks go to: System> Admin.> Printing> right click you printers icon> make sure it's enabled.

---

### Post by Ronok on 2010-02-08
warfacegod:

"System> Admin.> Printing> right click you printers icon> 
make sure it's enabled. "

Yes it is enabled (checked)

thanks for the tip

also tried to print from a variety of places:
Gimp, plain text document, Open office, etc.

**Still Not Printing**

Thanks [blazemore & warfacegod] for getting back to me
I tryed via sudo & nautilus to change the "**Permissions**"
to no avail, I know there must be a way though, some how
what to try next?
Thanks Again
R

---

### Post by halitech on 2010-02-08
why not open a terminal and install it from the repos?
```
sudo apt-get install hplip
```

---

### Post by blazemore on 2010-02-08
wget [http://prdownloads.sourceforge.net/hplip/hplip-3.9.12.run](http://prdownloads.sourceforge.net/hplip/hplip-3.9.12.run)
chmod +x hplip-3.9.12.run
./hplip-3.9.12.run

---

### Post by Ronok on 2010-02-11
[blazemore] 
Thanks that did it
and thanks others for tips and input

**Success**

---

### Post by Ronok on 2010-02-11
. . .
Report of Succcess: **HP DESKJET F2488**, will NOW Print

an addition to the last post,
yes had to follow all steps, 

then it would print from **Gimp** immediately
_but_ in **open Office** it would _not at first_,

Check this
after following [blazemore] # 7 post
I had to go back to

System> Admin.> Printing> 
and see that there might be 2 or 3 
printers or 2 or 3 of the same printer in my case
- unassigned and delete the wrong ones
- maybe assign the correct one as Default
- it put a green [check] mark 
_then Open Office would Print Just fine_

**Looks Good**
if [blazemore] or anyone could add after the fact
add why # 2 post did not work and # 7 did the trick
maybe we can learn a little better about 
attaining "Hardware Drivers" 

**Thanks Again**
Ronok

[SIZE="1"][http://www.gongkuo.com/zhongwen1.htm ]("http://www.gongkuo.com/zhongwen1.htm")[/SIZE]

---

### Post by blazemore on 2010-02-11
Post 2 didn't work, that was my fault.
When you download a binary file from the Internet, for security reasons it does not have permissions for anyone to execute the code contained within it.
In post 7, I added the "chmod +x" command which means "modify the permissions so this file can be executed"

Hope this helps :-)

PS you can also do it from a graphical user interface. Right-click the file, go to Properties->permissions and click the Execute checkbox.
Then you can doubl-click the file.

---

### Post by fixxxer50 on 2010-04-21
> **Ronok said:**
> . . .
Report of Succcess: **HP DESKJET F2488**, will NOW Print

an addition to the last post,
yes had to follow all steps, 

then it would print from **Gimp** immediately
_but_ in **open Office** it would _not at first_,

Check this
after following [blazemore] # 7 post
I had to go back to

System> Admin.> Printing> 
and see that there might be 2 or 3 
printers or 2 or 3 of the same printer in my case
- unassigned and delete the wrong ones
- maybe assign the correct one as Default
- it put a green [check] mark 
_then Open Office would Print Just fine_

**Looks Good**
if [blazemore] or anyone could add after the fact
add why # 2 post did not work and # 7 did the trick
maybe we can learn a little better about 
attaining "Hardware Drivers" 

**Thanks Again**
Ronok

[SIZE="1"][http://www.gongkuo.com/zhongwen1.htm ]("http://www.gongkuo.com/zhongwen1.htm")[/SIZE]


Thanks for sharing the information, it helped me too install my Hp F2488. 
I love Ubuntu community :popcorn:

---

### Post by Ronok on 2010-10-26
There seems to be a New Version of: "**hplip**"
(HP Linux Imaging and Printing)
From: **[_SourceForge.net_]("http://sourceforge.net/projects/hplip/files/hplip/")**
 
making this recent update caused a number of things to work better on this machine. 

There are 2 main ways to do this

Applications > Accessories > Terminal:
```

wget http://sourceforge.net/projects/hplip/files/hplip/3.10.9/

chmod +x hplip-3.10.9.run

./hplip-3.10.9.run
```
Another Way:
1) go online with firefox to **[_SourceForge.net_]("http://sourceforge.net/projects/hplip/files/hplip/")**
2) Left click the Green "Download Now" Button
3) Save file, OK, then Save some place like: /usr/share/
4) navigate to that folder
5) Right Click the file: "hplip-3.10.9.run"
6) go to "Properties" then go to "Permissions"
7) check the "executable" box
8) now double Left click the file, chose Run
9) follow the prompts (from here the same as starting from the Terminal)
(Note: if your thinking of trying to Copy something your seeing going by, 
normally "Ctrl+Shift+C" would copy highlighted text, but here it seems to kill this window)
Just let it Run
answer about 3 questions, what OS etc
maybe restart or unplug & re-plug the Printer at their last prompt

and that's it !
Print and Scan

Ronok
[URL="http://www.gongkuo.com/linuxcli.htm"]--> My Linux / Ubuntu web Page
_http://www.gongkuo.com/linuxcli.htm_[/URL]

---

