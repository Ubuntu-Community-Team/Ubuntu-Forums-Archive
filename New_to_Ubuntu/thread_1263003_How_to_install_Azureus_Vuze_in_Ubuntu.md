---
title: "How to install Azureus Vuze in Ubuntu ?"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by SriLankanBoy on 2009-09-10
I recently came upon a bittorrent software called [Vuze]("http://www.vuze.com/app").

The interface looked nice and the review upon the software was pretty much positive. Therefore I thought of giving it a try. Luckily there is a Linux version available.

I downloaded a .deb version from [This Site]("http://www.detector-pro.com/2009/05/how-to-install-vuze-4202-on-ubuntu-904.html"). However when I start the application it shows this error message :

```
The location "usr/share/vuze" is not writable. This will prevent future updates from being applied"
```

Can anyone provide a step by step guide on how to install Vuze and run it properly ?

---

### Post by Ichtyandr on 2009-09-10
try "sudo apt-get install vuze" it is in the repos

---

### Post by diplomat.x on 2009-09-10
Go to Add/Remove and search for "torrent". Do enable all softwares while searching. That will get u the vuze.

---

### Post by mustard greens on 2009-10-03
you need to change owner of the usr/share/vuze file.  type this into the terminal

sudo chown "yourusername":"yourusername" /usr/share/vuze

hit enter

of course, where it says "yourusername" enter your user name, but without the quotes.

restart vuze and it should be able to update successfully.

---

### Post by motorhead_1 on 2009-10-21
> **Ichtyandr said:**
> try "sudo apt-get install vuze" it is in the repos

I've typed  "sudo apt-get install vuze" in the terminal in order to install Vuze, it seems like the process had been  successfully completed, I've now a Vuze icon under my Internet programs. However if I click on it nothig happens. what what can the problem be?  
I'm running ubuntu 9.04

---

### Post by marshmallow1304 on 2009-10-21
Run it from the terminal:
Open Applications -> Accessories -> Terminal.
Type
```
vuze
```
and hit enter.
Post back any error messages.

---

### Post by motorhead_1 on 2009-10-21
exec: 11: /usr/lib/jvm/java-6-openjdk/jre/bin/java: not found

---

### Post by motorhead_1 on 2009-10-21
I can't install openjdk-6-jre package since it depends on openjdk-6-jre-headless, openjdk-6-jre-headless in turn depends on:
Depends: openjdk-6-jre-lib but it is not going to be installed
 Depends: ca-certificates-java but it is not going to be installed
 Depends: tzdata-java but it is not going to be installed     Depends:        tzdata (=2009n-0ubuntu0.9.04.1) but 2009n-1
 Recommends: icedtea-6-jre-cacao but it is not going to be installed

icedtea-6-jre-cacao for example depends on:
 Depends: openjdk-6-jre-headless but it is not going to be installed

tzdata-java Depends:        tzdata (=2009n-0ubuntu0.9.04.1) but 2009n-1  but it is not going to be installed

it's like a recursion....

---

### Post by motorhead_1 on 2009-10-22
any idea?

---

### Post by ohzopants on 2009-10-22
Try Sun's java.  It's called sun-javaXXXX.

---

### Post by motorhead_1 on 2009-10-22
i've Sun Java 6

---

### Post by marshmallow1304 on 2009-10-22
[http://ubuntuforums.org/showpost.php?p=7954282](http://ubuntuforums.org/showpost.php?p=7954282)

---

### Post by motorhead_1 on 2009-10-22
> **marshmallow1304 said:**
> [http://ubuntuforums.org/showpost.php?p=7954282](http://ubuntuforums.org/showpost.php?p=7954282)
Solved, thanks! 

I find ktorrent excellent by the way, but I couldn't find an option which allows me to select to download only certain files from the torrent and not necessarily everything, that's why I was going back to Vuze. Do you happen to know if this option does exist in ktorrent? thanks.

---

### Post by marshmallow1304 on 2009-10-22
> **motorhead_1 said:**
> I find ktorrent excellent by the way, but I couldn't find an option which allows me to select to download only certain files from the torrent and not necessarily everything, that's why I was going back to Vuze. Do you happen to know if this option does exist in ktorrent? thanks.

When you add a torrent, there should be check boxes next to the files.  Also, if you go to the Files section at the bottom, you can check/uncheck files from there.

Deluge is also nice if you want to try different clients.  I use both Deluge and ktorrent.

---

### Post by motorhead_1 on 2009-10-22
Thanks a lot!

---

