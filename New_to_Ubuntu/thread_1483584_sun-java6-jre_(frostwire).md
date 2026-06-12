---
title: "sun-java6-jre (frostwire)"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by yoshiki2 on 2010-05-14
Cannot install frostwire in lubuntu.... it says dependency is not satisfiable.. any ideas??

---

### Post by scorp123 on 2010-05-14
> **yoshiki2 said:**
> Cannot install frostwire in lubuntu.... it says dependency is not satisfiable.. any ideas??

Sun's Java 6 is in the "partner" repositories .... So: Did you enable those? Please check what your "Software Sources" tool says about that:

***System > Administration > Software Sources***

---

### Post by zeroseven0183 on 2010-05-14
I had the same problem too while testing your issue. But after checking the [Lubuntu Release Notes page]("https://wiki.kubuntu.org/Lubuntu/ReleaseNotes/LucidLynx#Sun Java moved to the Partner repository") where it says > For lubuntu 10.04 LTS, the sun-java6 packages have been dropped from the Multiverse section of the lubuntu archive. It is recommended that you use openjdk-6 instead.

If you can not switch from the proprietary Sun JDK/JRE to OpenJDK, you can install sun-java6 packages from the Canonical Partner Repository. You can configure your system to use this repository via command-line:
add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner"

The reason why you're having that error is that it can't find the sun-java6 package.

So to make Frostwire work, add the repository mentioned above for openjdk-6: ```
sudo add-apt-repository "deb http://archive.canonical.com/ lucid partner"
```

then install Java6-JRE

```
sudo apt-get update && sudo apt-get install sun-java6-jre
```

Lastly, install Frostwire.

Hope that helps.

---

### Post by Soul-Sing on 2010-05-14
the newest frostwire noarch 4.20.3 runs fine via openjdk, you dont need sun java anymore.
unpack the rar in your /home and click runFrostwire.sh

---

### Post by SPARTAN-118 on 2010-06-13
> **leoquant said:**
> the newest frostwire noarch 4.20.3 runs fine via openjdk, you dont need sun java anymore.
unpack the rar in your /home and click runFrostwire.sh

I guess you must be talking about the tarball, then, because the .deb package for Ubuntu (which is now at 4.20.6, by the way) still says it needs sun-java6-jre.

---

### Post by HeartsRules on 2010-06-22
Hi All,

I'm a new user to Ubuntu, and i have the same Java Sun 6 problem with using frostwire! 

For the procedure that works can  I please get a step by step guide on how to resolve the issue for beginners like me please?

Thank you very much in advance.

HeartsRules

---

### Post by SPARTAN-118 on 2010-06-22
Hi HeartsRules, welcome to Ubuntu!

This is what I did (note: this is with the tarball package off Frostwire.com, not the .deb package):

1.Download the tarball

2.Extract the tarball in whatever directory you downloaded it to (I put mine in Home as not to accidentally delete it)

3.Click runFrostwire.sh to start the program.

Now, unless you followed some other site's directions, do not use the Frostwire.desktop if you want an icon on your desktop. 
Rather, go into your Desktop folder, right click, Create New-> Link to Application. 
Type in the details in the Application tab, for instance, here we would put Name: Frostwire, Description and Comment whatever you want, and for Command here we click Browse, find the folder you extracted Frostwire to, and click the "runFrostwire.sh" file. 
The Frostwire.desktop file looks for the files in /usr/bin. If you want you can look for better, more detailed instructions, but mine work just as well. 
Of course, if you want to keep hidden the fact that you have Frostwire on your computer at all, you can not bother with the .desktop thing at all. :)

---

### Post by jetbelbes on 2010-06-25
> **zeroseven0183 said:**
> I had the same problem too while testing your issue. But after checking the [Lubuntu Release Notes page]("https://wiki.kubuntu.org/Lubuntu/ReleaseNotes/LucidLynx#Sun Java moved to the Partner repository") where it says 

The reason why you're having that error is that it can't find the sun-java6 package.

So to make Frostwire work, add the repository mentioned above for openjdk-6: ```
sudo add-apt-repository "deb http://archive.canonical.com/ lucid partner"
```

then install Java6-JRE

```
sudo apt-get update && sudo apt-get install sun-java6-jre
```

Lastly, install Frostwire.

Hope that helps.
i was now able to install frostwire and make it successfully work!

thanks to this! :D

---

