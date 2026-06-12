---
title: "install java"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by 0864045 on 2010-01-02
**Hi..**
 
 
[SIZE=2]Dear brothers:[/SIZE]
 
 
**how to install java on ubuntu>>?**
 
 
 
 
**Thank you very much..**
 
 
 
 
[B] 

[/B]

---

### Post by s.fox on 2010-01-02
Hello.

[This]("https://help.ubuntu.com/community/Java") community wiki page should be of help to you.

-Silver Fox

---

### Post by Cheesemill on 2010-01-02
Go to System > Administration > Software Sources and make sure the partner repos are checked. Then open a terminal and type:
```
sudo apt-get update && sudo apt-get install sun-java6-jre
```

When the licence screen appears hit TAB then ENTER to accept it.

---

### Post by 0864045 on 2010-01-02
> **Cheesemill said:**
> Go to System > Administration > Software Sources and make sure the partner repos are checked. Then open a terminal and type:
```
sudo apt-get update && sudo apt-get install sun-java6-jre
```
 
When the licence screen appears hit TAB then ENTER to accept it.
 
 
[B][SIZE=3][COLOR=#800000][SIZE=3][COLOR=#800000][LEFT][SIZE=2][COLOR=black]"[/COLOR][/SIZE][/COLOR][/SIZE][/COLOR][/SIZE][FONT=Segoe UI][FONT=Segoe UI][FONT=Segoe UI][SIZE=2][COLOR=black]PLZ " Can you explain to me pictures or some other way[/COLOR][/SIZE][/FONT][/FONT][/FONT][SIZE=2][COLOR=black] "..[/COLOR][/SIZE][/LEFT]
[FONT=Segoe UI][SIZE=3][COLOR=#800000][FONT=Segoe UI][SIZE=3][COLOR=#800000][FONT=Segoe UI][SIZE=3][COLOR=#800000][LEFT][SIZE=2][COLOR=black]Because I did not understand your goa[/COLOR][/SIZE][SIZE=2][COLOR=black]l[/COLOR][/SIZE][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Times New Roman][SIZE=2][COLOR=black] ...[/COLOR][/SIZE][/FONT][/LEFT]
[/B]

---

### Post by The Cog on 2010-01-02
Open a terminal (Programs / Accessories / Terminal) and enter these commands:
> sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-plugin
Or you could start System / Administration / Synaptic, and search for and install sun-java6-jre  and sun-java6-plugin from there.

---

### Post by QIII on 2010-01-02
Before you do anything else, STOP.

Canonical has decided to use OpenJDK from this point forward in place of Java  (I would have preferred that both OpenJDK and Sun's Java had been maintained). Last time I checked, the latest Java you can install from the repositories is Update 15, which had some severe security problems.  Sun's latest version is Update 17.

Follow the tutorial here (but you will have to use the terminal):

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

Edit:  Sef has rightly pointed out that my original post used hasty language.

---

### Post by Sef on 2010-01-02
Easy way to install Java/OpenJDK:

Applications > Ubuntu Software Center > Edit > Software Sources > Password > Tic both Community Maintained and Software Restricted boxes > Search > Two Choices:

a) OpenJDK - an open source version of Sun Java

b) Sun Java

>  Type one in search > Click on the one that you chose > Click on install > Go back to search > java plugin > install either Sun java plugin or iced tea plugin (for OpenJDK.) > close

Note: If you want to install most of the restricted extras at once (java, flash, avi, mp3, etc.) repeat the steps up to search > Type in Ubuntu > Click on Ubuntu Restricted Extras > Click on install > close.

---

### Post by Sef on 2010-01-02
**QIII**: > Canonical has decided to use OpenJDK from this point forward in place of Java  (terribly unwise IMHO)

I disagree.   I have used it since Jaunty and have found it to work just fine.

If you or anyone else would like to continue this discussion, then please start a thread in the Community Cafe.

---

### Post by 0864045 on 2010-01-09
[SIZE=2]I thank all who helped me in the topic[/SIZE]

---

