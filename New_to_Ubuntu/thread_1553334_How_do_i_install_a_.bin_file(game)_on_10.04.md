---
title: "How do i install a .bin file(game) on 10.04?"
date: 2010-08-14
forum: New to Ubuntu
---

### Post by Xelick on 2010-08-14
Title. :D

---

### Post by Reffner on 2010-08-14
Open up a terminal and navigate to where your download is.  Then run these commands...replacing "filename" with the name of your program.

```
sudo chmod +x filename.bin
./filename.bin
```

---

### Post by bodhi.zazen on 2010-08-14
Probably the other way around

```
chmod a+x foo.bin
sudo ./foo.bin
```

---

### Post by Xelick on 2010-08-14
It just says. "chmod: cannot access `Savage2Install-2.1.0-i686.bin': No such file or directory"

---

### Post by Bachstelze on 2010-08-14
> **Xelick said:**
> It just says. "chmod: cannot access `Savage2Install-2.1.0-i686.bin': No such file or directory"

The file is probably not where you're expecting it to be. If it's on your desktop, do [font=monospace]cd Desktop[/font] beforehand.

---

### Post by uRock on 2010-08-14
You have to direct the terminal to the folder containing the file first.

---

### Post by Reffner on 2010-08-14
> **bodhi.zazen said:**
> Probably the other way around

```
chmod a+x foo.bin
sudo ./foo.bin
```

lol thanks bodhi...I need SLEEP!!!

---

### Post by murderslastcrow on 2010-08-14
Your terminal starts in the home folder. For example, if the bin is your Downloads folder, you'd type the following.

cd Downloads
chmod +x file.bin
sudo ./file.bin

The only popular bins I know of are Java and Google Earth. What kind of application are you installing that needs a bin? There might be an alternative means of getting the software.

---

### Post by Rushyang on 2010-08-15
That **.bin** file is might be a disk image. You will have to create a virtual drive to mount it. Almost same as windows.

Follow the link.. It has always worked for me....

```
http://maketecheasier.com/mount-iso-bin-and-cue-files-from-nautilus/2009/05/23
```

---

### Post by lykeion on 2010-08-15
Xelick is obviously trying to install Savage 2

[http://naiux.wordpress.com/2009/03/29/savage-2-ubuntu-linux-installation-guide/](http://naiux.wordpress.com/2009/03/29/savage-2-ubuntu-linux-installation-guide/)

---

### Post by jzvbrt on 2010-08-15
> **murderslastcrow said:**
> Your terminal starts in the home folder. For example, if the bin is your Downloads folder, you'd type the following.

cd Downloads
chmod +x file.bin
sudo ./file.bin

The only popular bins I know of are Java and Google Earth. What kind of application are you installing that needs a bin? There might be an alternative means of getting the software.

I also have problems installing GoogleEarthLinux.bin. I get a message: Verifying archive integrity...Error in MD5 checksums: 23a82662ebe98d12f2bb0f9a9c9de3ac is different from c82b570db6dfc519d065b8b1a3b69511
Tried to download from diferent sites, always the same result. Anybody knows something about it?

---

### Post by uRock on 2010-08-15
> **jzvbrt said:**
> I also have problems installing GoogleEarthLinux.bin. I get a message: Verifying archive integrity...Error in MD5 checksums: 23a82662ebe98d12f2bb0f9a9c9de3ac is different from c82b570db6dfc519d065b8b1a3b69511
Tried to download from diferent sites, always the same result. Anybody knows something about it?
Why are you checking the MD5sum? 
Place the google eart file in the Home folder, the open a terminal and run ```
chmod +x Google*
``` then right click the Google file and then open with other application.. and then click enter custom command and then enter sh, then click Open.

---

### Post by jzvbrt on 2010-08-16
> **uRock said:**
> Why are you checking the MD5sum? 
Place the google eart file in the Home folder, the open a terminal and run ```
chmod +x Google*
``` then right click the Google file and then open with other application.. and then click enter custom command and then enter sh, then click Open.

URock, Thanks for your help. I did exactly like you sugested but it's not working. No messages are displayed and Google Earth is still not working.

---

### Post by lykeion on 2010-08-16
@jzvbrt
Really, how hard can it be?? :-)

[http://www.youtube.com/watch?v=15ngMiBRYZY](http://www.youtube.com/watch?v=15ngMiBRYZY)

---

### Post by jzvbrt on 2010-08-17
> **jzvbrt said:**
> URock, Thanks for your help. I did exactly like you sugested but it's not working. No messages are displayed and Google Earth is still not working.
I've downloaded the file again and repeated the procedure. It works fine. Thanks a lot!

---

### Post by uRock on 2010-08-17
> **jzvbrt said:**
> I've downloaded the file again and repeated the procedure. It works fine. Thanks a lot!
Awesome.

---

