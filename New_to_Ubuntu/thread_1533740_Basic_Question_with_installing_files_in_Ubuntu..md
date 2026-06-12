---
title: "Basic Question with installing files in Ubuntu."
date: 2010-07-18
forum: New to Ubuntu
---

### Post by djk21108 on 2010-07-18
I understand the idea of the Ubunutu Application Center which should enable me to find all the programs I need to make my system work. I just don't understand how to install files easily that I download from websites on Ubunutu.

As many of you know in windows when you download a .exe file to the desktop you double click it and it installs. Right now I have a graphics driver file on my desktop "ati-driver-installer-10-6-x86.x86_64.run"

How do I install this driver?

How do I install anything with .run or .deb at the end...easily? 

Thanks in advance!

---

### Post by Bapun007 on 2010-07-18
You install deb files just by double clicking then .

---

### Post by drpjkurian on 2010-07-18
Hi
There are three ways of installing programmes
1. Easiest way is to install the programme is by Ubuntu software centre. Browse through the programme and click to install

2. Download the .deb package of the programme from the website if available For es Chrome, skype or picassa. Just download it and double click it to inatall

3. Download the .targz file and install it manually by commands through the terminal. It is difficult for beginners.

---

### Post by djk21108 on 2010-07-18
Well thanks for your help so far, how about a .run file?

---

### Post by crichard on 2010-07-18
> **djk21108 said:**
> Well thanks for your help so far, how about a .run file?

move .run file to your home directory,

and try this,

```
sudo sh /home/yourname/filename.run
```

---

### Post by drpjkurian on 2010-07-18
Hi 
Meanwhile you can try my blog for basic instruction to install .targz file
it is [ubuntucrack.blogspot.com]("http://ubuntucrack.blogspot.com/")

---

### Post by Jazzy_Jeff on 2010-07-18
The easy way to execute the .run file is by right clicking on it and goto properties. Click on permissions tab and check the box that says allow to execute as a program. Just remember if you download a program outside of the software center you are putting yourself at risk. Make sure you can trust the site you are getting the program from.

---

### Post by KdotJ on 2010-07-18
Change directory to your desktop

```
cd Desktop
```

make the file executable

```
sudo chmod a+x ati-driver-installer-10-6-x86.x86_64.run
```

enter password for the above command
then run it

```
./ati-driver-installer-10-6-x86.x86_64.run
```


As noted by people, this is not recommended way to install files. You should use the Ubuntu Software Centre, or a package management program such as Synaptic. Files from the web cannot always be trusted

---

### Post by emoguitarist06 on 2010-07-18
> **KdotJ said:**
> Change directory to your desktop

```
cd Desktop
```
[COLOR="Red"]Only do this if you saved the .run file on your desktop otherwise you want to cd (change directory) to the folder you have it in[/COLOR]
> **KdotJ said:**
> Change directory to your desktop

make the file executable

```
sudo chmod a+x ati-driver-installer-10-6-x86.x86_64.run
```
[COLOR="red"]This is the same thing as[/COLOR] > **Jazzy_Jeff said:**
> The easy way to execute the .run file is by right clicking on it and goto properties. Click on permissions tab and check the box that says allow to execute as a program.
> **KdotJ said:**
> 
enter password for the above command
then run it

```
./ati-driver-installer-10-6-x86.x86_64.run
```


[COLOR="red"]Hope this helps, and yes only .deb files can you double click and install on Ubuntu.[/COLOR]

---

