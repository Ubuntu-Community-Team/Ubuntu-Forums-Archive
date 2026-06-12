---
title: "Installing Java Runtime Environment"
date: 2010-04-07
forum: New to Ubuntu
---

### Post by Vistz on 2010-04-07
I'm having some trouble installing java. I went to Application>>>Add/Remove and I found the OpenJDK Java 6 Runtime along with the Webstart. After choosing them and clicking "Install All" and "Apply Changes", I got an error message saying 

[HTML]You have 1 broken package on your system!

Use the "Broken" filter to locate it.[/HTML]Any thoughts? Oh, and I'm an absolute beginner at this. Please assume I know close to nothing about Ubuntu when responding.

---

### Post by n0dix on 2010-04-07
[http://ubuntuforums.org/showpost.php?p=8490797&postcount=2]("http://ubuntuforums.org/showpost.php?p=8490797&postcount=2")

---

### Post by Vistz on 2010-04-07
Ok. I went into the "Synaptic Package Manger" and I clicked Edit>>Fix Broken Packages. Then I pressed "Apply". But then I got this error message:

[HTML]E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory[/HTML]

---

### Post by n0dix on 2010-04-07
It usually means you have a package manager running. Either you still have add/remove open, or you have synaptic open, or you are manually running the apt-get command. If you're sure you don't have any of those running, then log out and log back in - hopefully it will kill whatever process is using the lock file.

---

### Post by Vistz on 2010-04-07
I restarted and installed the JRE. When I go into the terminal and type java-version, I get
```
java version "1.6.0_14"
Java(TM) SE Runtime Environment (build 1.6.0_14-b08)
Java HotSpot(TM) Server VM (build 14.0-b16, mixed mode)

```However, when I go to [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml), the applet does not show up.

---

### Post by n0dix on 2010-04-07
Reboot the system.

---

### Post by Vistz on 2010-04-07
> **n0dix said:**
> Reboot the system.

It still doesn't work.

---

### Post by n0dix on 2010-04-07
Are you using 64bit ubuntu?

---

### Post by tom.swartz07 on 2010-04-07
> **Vistz said:**
> It still doesn't work.

It might be easier to install the official package. Follow the link in my signature. 

Its a bit of stuff to copy and paste in a terminal, but it definitely solves all of the major problems.

---

### Post by dominiquec on 2010-04-07
I think it might be because the sun-java6-plugin isn't installed.

On the command line, run 

```
sudo aptitude install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

---

### Post by Vistz on 2010-04-08
Yea. I ran this yesterday and it worked. 
```
sudo apt-get ins sun-java6-jre sun-java6-plugin sun-java6-fonts

```

Thanks guys.

---

