---
title: "Java upgrade"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by newbeeman on 2009-02-22
To use Pogo.com I need the latest upgrade of Java. The copies in Synaptic are older.
Went to the Java site, downloaded to my desktop the necessary file which is a .bin copy. There is an RPM but figured I didn't need that one.
The installation info on the Java site won't work on my machine.
Not terminal savvy, so would appreciate a 'hand-hold' to get the job done.
Thanks.

---

### Post by carml on 2009-02-22
Did you look for a .deb file?If there isn't one,you can always use that .rpm file,just lok for and install a program called Alien,if I'm not wrong.

---

### Post by newbeeman on 2009-02-22
> **carml said:**
> Did you look for a .deb file?If there isn't one,you can always use that .rpm file,just lok for and install a program called Alien,if I'm not wrong.

Sorry. There are conflicts using that program, not prepared to gamble with system files. No .deb file

---

### Post by carml on 2009-02-22
The latest version of Java avaible is 6,what is the version installe don your pc?

---

### Post by newbeeman on 2009-02-22
> **carml said:**
> The latest version of Java avaible is 6,what is the version installe don your pc?

I have version 6.0. would like to get V 6.12 which is the latest.

---

### Post by baizon on 2009-02-22
Download [http://packages.ubuntu.com/jaunty/sun-java6-jdk]("http://packages.ubuntu.com/jaunty/sun-java6-jdk") or [http://packages.ubuntu.com/jaunty/sun-java6-jre]("http://packages.ubuntu.com/jaunty/sun-java6-jre")
and install it (Package: sun-java6-jre (6-12-0ubuntu1)) :-)

---

### Post by newbeeman on 2009-02-22
> **baizon said:**
> Download [http://packages.ubuntu.com/jaunty/sun-java6-jdk]("http://packages.ubuntu.com/jaunty/sun-java6-jdk") or [http://packages.ubuntu.com/jaunty/sun-java6-jre]("http://packages.ubuntu.com/jaunty/sun-java6-jre")
and install it (Package: sun-java6-jre (6-12-0ubuntu1)) :-)

I did say at the beginning that I needed a 'hand hold' this lot is confusing. Any other suggestions, please?

---

### Post by carml on 2009-02-22
Look for sun-java-bin on System->Administration->Synaptic package manager and you'll get the latest version avaible.

---

### Post by newbeeman on 2009-02-22
> **carml said:**
> Look for sun-java-bin on System->Administration->Synaptic package manager and you'll get the latest version avaible.

Did all that before I troubled you all. Synaptic loads version 6.0 I want to get V6.12. 
I have downloaded the file on my desktop but cannot load the file into my system.
Please can you re-read the first post?

---

### Post by baizon on 2009-02-22
Download the files form my link above. Then open a terminal, go to the Desktop then... ```
sudo dpkg -i sun-java6-jre_6-12-0ubuntu1_all.deb
sudo dpkg -i sun-java6-jdk_6-12-0ubuntu1_i386.deb
```
Then you will have the lastest version of Java.

---

### Post by Miljet on 2009-02-22
Pogo will run fine using the version in the repositories. (Java(TM) Plug-in 1.6.0_10)

That said, I could never get Pogo to run on Ubuntu 8.04. Tried everything I could find for months. I finally created another partition and reinstalled Gutsy just to use Pogo. Last week, I installed 8.10 (Intrepid) and Pogo now runs better than it ever did.

BTW, I too have tried installing the .bin package from the Sun site and never did have any luck with it. You always get lost at the point of creating a link to the plugin. The file system for Ubuntu doesn't match the instructions on the Sun site.

---

### Post by newbeeman on 2009-02-22
> **baizon said:**
> Download the files form my link above. Then open a terminal, go to the Desktop then... ```
sudo dpkg -i sun-java6-jre_6-12-0ubuntu1_all.deb
sudo dpkg -i sun-java6-jdk_6-12-0ubuntu1_i386.deb
```
Then you will have the lastest version of Java.

Tried that. Your way I got an error "no such file"
With the .deb installer I got "Error Dependency not satisfiable"
Any suggestions?

---

### Post by newbeeman on 2009-02-22
> **Miljet said:**
> Pogo will run fine using the version in the repositories. (Java(TM) Plug-in 1.6.0_10)


Not on my machine. Contacted Pogo, they tell me it's a java failure, so just trying all the bases before I give it up as a lost cause.

---

### Post by Hastings101 on 2009-02-22
Java is kind of tricky on Linux, and sometimes the plugins don't work well with Firefox.  I'd either wait until the next Java update and hope for the best, or try using an open-source version if that's possible.

---

### Post by Miljet on 2009-02-22
Which version of Ubuntu are you using?

I kept up a running dialogue with the Pogo folks for about a week. They finally admitted that they knew absolutely nothing about Linux or Unix systems.

I tried different versions of Sun java, open source java, different browsers, different versions of Firefox, and about everything else you can name. Pogo simply refused to run with Hardy. It ran under Gusty, and runs fine under Intrepid.

---

### Post by PRC09 on 2009-02-22
Hi,
  Found this guide that works for 32bit and 64bit.Using Ubuntu 8.10 on both 32 and 64 and I am also new to this...

[http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/](http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/)

---

### Post by peggyarmstrong on 2009-02-27
> **baizon said:**
> Download [http://packages.ubuntu.com/jaunty/sun-java6-jdk]("http://packages.ubuntu.com/jaunty/sun-java6-jdk") or [http://packages.ubuntu.com/jaunty/sun-java6-jre]("http://packages.ubuntu.com/jaunty/sun-java6-jre")
and install it (Package: sun-java6-jre (6-12-0ubuntu1)) :-)

I tried this and got message [COLOR="Red"]Error: Dependency is not satisfiable: sun-java6-binjia32-su-java6.bin[/COLOR]

---

### Post by Shazaam on 2009-02-27
> **newbeeman said:**
> Sorry. There are conflicts using that program, not prepared to gamble with system files. No .deb file

Conflicts? How so?
Alien is safe to use. Works great for installing rpm's.

---

### Post by hobo on 2009-03-13
I too have had problems running POGO games in 8.04 after upgrading from 6.06. What I found was TWO JAVA plugins resident in a Firefox subdirectory. Anyways, what I did was remove all JAVA from the system and downloaded the newest JAVA from SUN and installed. Then I deleted the OLD plugin and now POGO works just fine in 8.04 for me.

---

