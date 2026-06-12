---
title: "How to install JDownloader 0.7 in Ubuntu 9.04 ?"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by SriLankanBoy on 2009-08-25
**_How to install JDownloader 0.7 in Ubuntu 9.04 ?_**

I followed the instructions on a site to make the folder, install and everything else. The installation and terminal processes things goes fine. When the application shows the loading screen ubuntu crashes and the windows is shown like broken pieces. I have to log out and in to get ubuntu working again. Can anyone help to solve this problem ?

* I am a total n00b. So it would be better if you can explain step by step process. :)

I am using the Mac4Lin package to make my ubuntu look like Mac OS.
```
http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac
```

My Java Version number is 1.6.0_14 .

---

### Post by Mighty_Joe on 2009-08-25
> **SriLankanBoy said:**
> 
I followed the instructions on a site to make the folder, install and everything else. 

It would be polite to let us know where you found these instructions, otherwise we don't know what you are talking about.  
I downloaded the Jdownloader zip file to my home directory, unzipped it, cd'd to the JDownloader directory and ran JDownloader. Open a terminal and type:
```

unzip JDownloader_0.7.zip
cd JDownloader\ 0.7
java -jar JDownloader.jar

```

---

### Post by SriLankanBoy on 2009-08-25
> **Mighty_Joe said:**
> It would be polite to let us know where you found these instructions, otherwise we don't know what you are talking about.  
I downloaded the Jdownloader zip file to my home directory, unzipped it, cd'd to the JDownloader directory and ran JDownloader. Open a terminal and type:
```

unzip JDownloader_0.7.zip
cd JDownloader\ 0.7
java -jar JDownloader.jar

```

I followed the instructions from here, and I changed the folder & file names according to the version I downloaded.

```
http://www.blackonsole.org/2009/03/install-jdownloader-on-linux-ubuntu-810.html
```

and

```
http://pagesofinterest.net/blog/2009/05/installing-jdownloader-in-ubuntu/
```

Which one should I follow to install correctly. If not, please put the steps to install. Also please mention how I can make a shortcut in my panel so that I can open it in future. (Not the setup, just the program) :)

---

### Post by brayden13 on 2009-08-25
Oh sorry mis read that. gimme a sec to think
are you able to run it as root? like with sudo jdownloader or something? as root doesn't use that mac4lin thing (i used to have mac4lin too)
to install it the "official" way as they have on the jdownloader site, use these commands
wget [http://212.117.163.148/jd.sh](http://212.117.163.148/jd.sh)
chmod +x jd.sh
./jd.sh
use those commands in terminal. one at a time too or they probably won't work
Thne it will install it the way you're meant to install it :)

---

### Post by Mighty_Joe on 2009-08-27
> **SriLankanBoy said:**
> If not, please put the steps to install. 

I gave you the instructions I used to install.  Unzip and run.  Simple.

> **SriLankanBoy said:**
> 
Also please mention how I can make a shortcut in my panel so that I can open it in future. (Not the setup, just the program) :)

I don't have Ubuntu handy right now, but it's probably something like right-clicking on the desktop and selecting "create launcher".

---

### Post by Vargas on 2010-03-04
Hi. Sorry for bringing this back but... is there a JDownloader 64-bit? I've been looking and can't find one. Thanks!!

---

### Post by Mighty_Joe on 2010-03-05
JDownloader is a Java application.  The Java API does not distinguish between 32 and 64-bit OS's so the same Java application will run on both platforms.
[Java HotSpot FAQ]("http://java.sun.com/docs/hotspot/HotSpotFAQ.html")

---

### Post by Vargas on 2010-03-08
> **Mighty_Joe said:**
> JDownloader is a Java application.  The Java API does not distinguish between 32 and 64-bit OS's so the same Java application will run on both platforms.
[Java HotSpot FAQ]("http://java.sun.com/docs/hotspot/HotSpotFAQ.html")

I thought so too but when I tried to install it, it gave me a wrong architecture message.

---

### Post by Mighty_Joe on 2010-03-08
> **Vargas said:**
> I thought so too but when I tried to install it, it gave me a wrong architecture message.

You'll have to share the command you used and the error message you got so we know what you are talking about.

---

### Post by mister_playboy on 2010-03-08
The instructions on the [JDownloader](http://jdownloader.org/download/index) page should work just fine.

   1.
      wget must be installed on system!
```
sudo apt-get install wget
```

   2.
      [Download](http://212.117.163.148/jd.sh) jd.sh
   3.
      chmod +x jd.sh
   4.
      start jd.sh

Note: Open jd.sh to read Manual or change Settings!

---

