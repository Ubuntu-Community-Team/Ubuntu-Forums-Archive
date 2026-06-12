---
title: "n00b needs help with Thingamablog program"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by arnold_ziffle on 2009-12-04
Hi,

I am brand new with ubuntu, moving from Win XP.  One thing I use all the time on Win XP is a blogging program called Thingamablog. On the Thingamablog web site [http://www.thingamablog.com](http://www.thingamablog.com), it says it will work with linux, and even has an ubuntu.deb file to download. 

I was able to install the program from the .deb file, but when I click on the icon or try to run from the cmd line, it says something about JAVA.  Does Ubuntu have java installed? If not how do I install it? I am a complete n00b and really don't know what I am doing.

Would love to get Thingamblog running on ubuntu! Thanks.

---

### Post by bodhi.zazen on 2009-12-04
How did you install it ?

Try  running ```
sudo apt-get -f
``` In a terminal.

---

### Post by arnold_ziffle on 2009-12-04
Hi, I installed it by downloading the deb file on the thingamablog web site. Then I just doubled clicked on it, and it installed it under "Internet" in the Ubuntu menu.

I ran that command and it showed the most frequently used commands. Install looks like the command i should use, but what do I do to install java? 

On the thingamablog web site it says it needs java 1.6 or better.

---

### Post by avtolle on 2009-12-04
You may need to install Sun Java. An easy way to do this would be to use Synaptic (System->Administration->Synaptic Package Manager), search for Sun Java.

---

### Post by MooPi on 2009-12-04
Well arnold_ziffle, sounds as if you need to have java installed on your machine. To check and see if it is already installed try this command in a terminal.
> dpkg --get-selections > installed-softwareThis will dump a text file of everything that is installed on your computer. Check to see if you have java installed. Look for java jre , java commaon, java bin, java plugin.

---

### Post by wojox on 2009-12-04
Just run from your terminal:

```
 sudo apt-get install sun-java6-jre sun-java6-jdk sun-java6-plugin
```

---

### Post by arnold_ziffle on 2009-12-04
> 
 sudo apt-get install sun-java6-jre sun-java6-jdk sun-java6-plugin
Thanks for all the replies! Bingo, this was the command I needed. Thingamablog is running perfectly under Ubuntu now :)

I searched the forum here for installing java. The command I used only had 
sun-java6-jre sun-java6-plugin 
What is the jdk, I did not install that? Will  I need it? Thingamablog appears to run ok without sun-jdk.

Thanks!

---

### Post by thiebaude on 2009-12-04
Now if you want to latest java follow this guide exactly, [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by arnold_ziffle on 2009-12-04
> 
Now if you want to latest java follow this guide exactly, [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)


Thanks, I think I will save that for another day :) Thingamablog is running just great with the version of java I installed, so as long as I am able to get it running in Ubuntu I am happy enough for now.

Still wonder if I should have installed the java-sun-jdk? Anyone know? Seems to make no difference without it.

---

### Post by avtolle on 2009-12-04
No, you don't need java-sun-jdk for your purposes. That is for use, I believe, for development. The jre is sufficient to provide the environment to run apps such as yours. Someone with more knowledge, please correct any misstatements hereinabove made.

---

### Post by bodhi.zazen on 2009-12-04
oops, me bad :redface:

should have been :```
sudo apt-ger **install** -f
```

The -f flag == "fix" and it would have automatically pulled and installed the dependencies.

Hopefully this will help you the next time you install a .deb ;)

---

