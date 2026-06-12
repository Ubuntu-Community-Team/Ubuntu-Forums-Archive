---
title: "install program but ubuntu says It cant find"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by twill2 on 2009-01-24
installed a tar.gz or tar ball or what ever the name is and down opened/loaded it into my home directories but when given the command in the terminal : GoWeather.sh I get bash: no such directories or command etc. or something to that effect. I read the read me text for instructions and they are very brief. it say every thing is in the tar zip file and all you have to do is open and load into your home directory then type GoWeather.sh in the terminal and all should work...not the case for me. After numerous attempts to do so and several days still no luck.  Please can someone HELP?  Thanks

---

### Post by ken22 on 2009-01-24
firstly make sure the file is executable

```
chmod u+x GoWeather.sh
```

then run it

```
./GoWeather.sh
```

---

### Post by gmjs on 2009-01-24
It sounds like you need to issue:

```
**./GoWeather.sh**
```

The terminal only searches for binaries in the PATH variable by default.  If the program you want to run is in the working directory, you must use **./** to specify 'in this folder' first.

Yes, they are called 'tarballs' and the terminal window error will have been:

```
bash: GoWeather.sh: command not found

```

---

### Post by Michael.Godawski on 2009-01-24
hi,

the posters above are correct.
If you want  to install new stuff in Ubuntu have a look at my page:

[http://ubunturesources.ub.ohost.de/howtoinstall.html](http://ubunturesources.ub.ohost.de/howtoinstall.html)

It explains briefly how to install different types of files.

To the others please feel free to suggest improvements to this site;
either suggesting a new file type or improving the existing descriptions.
But keep it simple.;)

---

### Post by twill2 on 2009-01-24
Thanks y'all for the info. I will try the ./ thing in front of the command. And Michael G.  thanks ,I  will check out the your page.

---

### Post by twill2 on 2009-01-24
> **ken22 said:**
> firstly make sure the file is executable

```
chmod u+x GoWeather.sh
```

then run it

```
./GoWeather.sh
```

ken22, did the test and got this: tim@tim-desktop:~$ chmod u+x GoWeather.sh
chmod: cannot access `GoWeather.sh': No such file or directory

---

### Post by handydan918 on 2009-01-24
Do ```
cd
```

then 
```
sudo updatedb
```

then ```
locate GoWeather
```

Let's see where that sucker is.

;)

---

### Post by ken22 on 2009-01-24
You must be in the correct directory. Use the ```
ls
``` command to make sure GoWeather.sh is in your current directory.

---

### Post by Michael.Godawski on 2009-01-24
Where is the GoWeather.sh located? On your Desktop?

You have to navigate into the right directory with the cd command in terminal.

---

### Post by Bölvaður on 2009-01-24
did you navigate to the correct directory?

that is

cd Desktop
cd myDirectory

or cd Desktop/myDirectory

you can see your options by entering "ls"

---

### Post by taurus on 2009-01-24
Are you even in the right directory?  If you saved something to your computer, changes are it would be saved to your desktop so you need to change to that directory first.

```
cd ~/Desktop
ls -la
```
Post the output of the second command here.

---

### Post by handydan918 on 2009-01-24
Right, taurus, that's why I told him to updatedb && locate....then we'll KNOW where the file(s) is/are.

---

### Post by twill2 on 2009-01-24
> **handydan918 said:**
> Do ```
cd
```

then 
```
sudo updatedb
```

then ```
locate GoWeather
```

Let's see where that sucker is.

;)
hey handydan918 guess what, It found Them!
Its all over the place! Yikes:redface: Guess that is where I have tried over and over but did not clean up after....at least I found it:p 
tim@tim-desktop:~$ cd
tim@tim-desktop:~$ sudo updatedb
[sudo] password for tim: 
tim@tim-desktop:~$ locate GoWeather
/home/tim/.kde/share/apps/RecentDocuments/GoWeather.sh.desktop
/home/tim/.kde/share/apps/RecentDocuments/GoWeather.sh[2].desktop
/home/tim/.kde/share/apps/RecentDocuments/GoWeather.sh[3].desktop
/home/tim/.local/share/Trash/files/GoWeather.2.sh
/home/tim/.local/share/Trash/files/GoWeather.sh
/home/tim/.local/share/Trash/files/wdisplay/GoWeather.sh
/home/tim/.local/share/Trash/files/wdisplay/wdisplay/GoWeather.sh
/home/tim/.local/share/Trash/files/wdisplay.2/GoWeather.sh
/home/tim/.local/share/Trash/info/GoWeather.2.sh.trashinfo
/home/tim/.local/share/Trash/info/GoWeather.sh.trashinfo
/home/tim/wdisplay/GoWeather.sh
 Now what do I do? throw it all in the trash and start over? Thanks

---

### Post by twill2 on 2009-01-24
tim@tim-desktop:~$ /home/tim/wdisplay/GoWeather.sh
/home/tim/wdisplay/WeatherD: error while loading shared libraries: libgdk_pixbuf.so.2: cannot open shared object file: No such file or directory
  

**After locating I put this commannd in the terminal but got the same results**

---

### Post by mc4man on 2009-01-24
wrong answer

---

### Post by taurus on 2009-01-24
> **twill2 said:**
> tim@tim-desktop:~$ /home/tim/wdisplay/GoWeather.sh
/home/tim/wdisplay/WeatherD: error while loading shared libraries: **libgdk_pixbuf.so.2**: cannot open shared object file: No such file or directory
  

**After locating I put this commannd in the terminal but got the same results**

Looks like you are missing a library for it.  You need to install libgdk-pixbuf2 either with synaptic or apt-get.

---

### Post by twill2 on 2009-01-24
s owner I get messages permission denied? in some cases. What would cause that?  I looked under authorizations and found my name listed twice in the directories but not in the root or as the ad-min but I am the only one with the code.  Do I have to format and start over? My password works to change things as a ad-min and to download etc.. boy this is getting me confused



/WeatherD: error while loading shared libraries: libgdk_pixbuf.so.2: cannot open shared object file: No such file or directory

---

### Post by mc4man on 2009-01-24
```
sudo apt-get install libgdk-pixbuf2
```

will take care of it

---

### Post by mikewhatever on 2009-01-24
> **Michael.Godawski said:**
> hi,

the posters above are correct.
If you want  to install new stuff in Ubuntu have a look at my page:

[http://ubunturesources.ub.ohost.de/howtoinstall.html](http://ubunturesources.ub.ohost.de/howtoinstall.html)

It explains briefly how to install different types of files.

To the others please feel free to suggest improvements to this site;
either suggesting a new file type or improving the existing descriptions.
But keep it simple.;)

Going after that link displays a BIG, really disgusting gambling related banner. Make sure to have javascript blocked before going to this guy's page. Configuring AdBlock doesn't seem to help because Mr. Godawski has the banner coming from various urls. Very resourceful.

---

### Post by twill2 on 2009-01-24
Got IT! WOO HOO !  thanks a million all of ya's

---

### Post by Michael.Godawski on 2009-01-24
> **mikewhatever said:**
> Going after that link displays a BIG, really disgusting gambling related banner. Make sure to have javascript blocked before going to this guy's page. Configuring AdBlock doesn't seem to help because Mr. Godawski has the banner coming from various urls. Very resourceful.

I have no influence on the banner ads sorry, they come from the ohost.de service.
There is no such thing as a perfect free hosting service. If you would read the page source code you would see.

I really not intend to harm someone or hinder the browsing experience. If I would have the monetary resources I would not play with free hosting services.

Once again sry.

By the way. It is not a virus or something. It is only a commercial dude.  It is not that bad and it is gone after a click. so....

---

### Post by mikewhatever on 2009-01-25
> **Michael.Godawski said:**
> I have no influence on the banner ads sorry, they come from the ohost.de service.
There is no such thing as a perfect free hosting service. If you would read the page source code you would see.

I really not intend to harm someone or hinder the browsing experience. If I would have the monetary resources I would not play with free hosting services.

Once again sry.

By the way. It is not a virus or something. It is only a commercial dude.  It is not that bad and it is gone after a click. so....

If that's the case, I have to apologize for the animosity expressed towards you. I have little patience for dumb advertisers, who think banners covering the screen bring anything but irritation. Anyway, since it's not your fault, sorry once again.

---

