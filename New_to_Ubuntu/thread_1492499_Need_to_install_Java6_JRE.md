---
title: "Need to install Java6 JRE"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by leebaldwin on 2010-05-24
So I am trying to install Frostwire and I get a dependency message stating::
 
Error: Dependency is not satisfiable: sun-java6-jre

Then I run:
sudo apt-get install sun-java6-jre

and I get

Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jre has no installation candidate

What am I doing wrong here? This is on Ubuntu 10.04.

---

### Post by MBG1987 on 2010-05-24
first open the terminal and write:

[PHP]
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update[/PHP] 

then write:

[PHP]sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts[/PHP]

hope this helps

---

### Post by leebaldwin on 2010-05-26
```

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jre has no installation candidate

```

As you can see still no go. Please help.

---

### Post by Windows Nerd on 2010-05-26
From [http://www.jaxmag.com/itr/news/psecom,id,35104,nodeid,146.html](http://www.jaxmag.com/itr/news/psecom,id,35104,nodeid,146.html) 

It took a minute to find this. Please try Google first next time
> 

**How To Install Java 6 on Ubuntu**

   Misunderstandings of how to install Sun Java  seem rampant on the Ubuntu forums, and trying to clear the fog is [this]("http://www.ossgeeks.co.uk/?page_id=4")  post at the [Open Source Software Geeks]("http://www.ossgeeks.co.uk/?page_id=4"). As per the post,  installing Java on Ubuntu is a "breeze". This is how:

 Before you begin, you need to ensure that your repositories are up to  date by issuing the following:
 sudo apt-get update

      If you are developing Java applications, you will require Java  Development Kit (JDK), on the other hand if you just require Java to run  Java applications, then you need just Java Runtime Environment (JRE).  For the former, the command is as follows:
 sudo apt-get install sun-java6-jdk sun-java6-plugin

For JRE:
 sudo apt-get install sun-java6-jre sun-java6-plugin

Once either one is done, run the sudo update-java-alternatives  -s java-6-sun command and finally add the line  &#8220;/usr/lib/jvm/java-6-sun&#8221; to the top of the /etc/jvm file (gksudo  gedit /etc/jvm). Save and exit. To test your Java(TM) setup in  the terminal type:-

java -version

If you get an output like below, then you are done!

java version &#8220;1.6.0&#8243; Java(TM) SE Runtime Environment (build 1.6.0-b105) Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)

---

### Post by 2hot6ft2 on 2010-05-26
That's all fine but I don't see anything about the partner repo. that it's in now or the missing libstdc++5 file that sun java 6 needs but was replaced by libstdc++6 in 10.04.

Welcome to the forum, just keep in mind commands are run in the terminal and your password will not be displayed when you enter it just type it in and hit enter when needed.
Applications > Accessories > Terminal
And Synaptic is
System > Administration > Synaptic Package Manager

There are 2 ways to go. The first is removing openjdk and the other is to have both sun and openjdk installed and setting it to use the sun version. Since I've already covered both ways I'll just link to them. Don't let the thread titles throw you off they are what I said.

[First removing openjdk and installing suns version]("http://ultimateeditionoz.com/forum/viewtopic.php?f=73&t=1080&p=3878")

[Having both installed and setting it to use the sun version]("http://forumubuntusoftware.info/viewtopic.php?f=68&t=4594&start=10#p51578")

Each has their reason for doing it that way, for one removing openjdk would remove other things that it shouldn't have so having both installed was the way to go in that case.
:popcorn:

---

### Post by PRC09 on 2010-05-26
I think this is a better explanation as Java has been moved to the Partner Repository now....


[http://www.ubuntugeek.com/how-install-sun-java-runtime-environment-jre-in-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/how-install-sun-java-runtime-environment-jre-in-ubuntu-10-04-lucid-lynx.html)

---

