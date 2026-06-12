---
title: "JDownloader 4 Linux"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by Roger Allott on 2010-03-01
Yesterday, I downloaded and installed JDownloader for Windows and found it to be a damn useful tool for grabbing files from sharing sites such as Rapidshare.

There is also a linux version of the software, so now I've downloaded that too.

My problem comes in actually finding out how to install it and/or run it. Apparently, it is written completely in Java.

The file downloaded was a zip archive, which I've now extracted to create a folder in my home directory called 'JDownloader'. Unfortunately, there doesn't seem to be a nice deb file for me to open with GDebi.

What there are though are 2 .jar files - JDownloader.jar and jdupdate.jar.

Has anyone else here installed JDownloader onto Ubuntu, and if so, would you mind telling me how to install or run it?

---

### Post by Mighty_Joe on 2010-03-01
```
java -jar JDownloader.jar
```

---

### Post by Roger Allott on 2010-03-01
> **Mighty_Joe said:**
> ```
java -jar JDownloader.jar
```

Thanks for that. For others who might have the same question, the terminal code is actually:
```
java -jar JDownloader/JDownloader.jar
```
because the zip file extracts the .jar file to a new folder.

So, I've now got JDownloader installed, but it doesn't seem to have created an entry into my menu lists. How do I get it into Applications > Internet > ....., for example?

---

### Post by Mighty_Joe on 2010-03-01
> **Roger Allott said:**
> 
For others who might have the same question, the terminal code is actually:
I'd recommend running JDownloader from it's directory (hence my version of the command), rather than from your home. It does a lot of crazy dynamic updating and I'm not certain if it uses the working directory or if it's smart enough to figure out what directory you put it in.

> **Roger Allott said:**
> So, I've now got JDownloader installed, but it doesn't seem to have created an entry into my menu lists. How do I get it into Applications > Internet > ....., for example?

System->Preferences->Main Menu
or [create a launcher]("https://help.ubuntu.com/7.04/user-guide/C/launchers.html")

---

### Post by Roger Allott on 2010-03-01
> **Mighty_Joe said:**
> I'd recommend running JDownloader from it's directory (hence my version of the command), rather than from your home. It does a lot of crazy dynamic updating and I'm not certain if it uses the working directory or if it's smart enough to figure out what directory you put it in.
Ah. Good point. Oh well, I did it the other way. It seems to have installed OK, but your method is better I think.


> **Mighty_Joe said:**
> System->Preferences->Main Menu
or [create a launcher]("https://help.ubuntu.com/7.04/user-guide/C/launchers.html")
Both of these methods require me to know the command code to launch the application. Could you tell me what that is?

---

### Post by Mighty_Joe on 2010-03-01
> **Roger Allott said:**
> Ah. Good point. Oh well, I did it the other way. It seems to have installed OK, but your method is better I think.

It does the same thing.  If you start getting strange files in your home directory, you'll know how to fix it.

> **Roger Allott said:**
> 
Both of these methods require me to know the command code to launch the application. Could you tell me what that is?

```
java -jar JDownloader.jar
```
Are we playing "Who's On First"? ;)

---

