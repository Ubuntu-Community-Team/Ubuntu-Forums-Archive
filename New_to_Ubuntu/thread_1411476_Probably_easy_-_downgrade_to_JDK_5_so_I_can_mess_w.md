---
title: "Probably easy - downgrade to JDK 5 so I can mess with android"
date: 2010-02-20
forum: New to Ubuntu
---

### Post by boredpcguy on 2010-02-20
Hey there, I am looking to basically use my Karmic install to play with Android source code.  
I have a lot of spare time and want to sharpen some skills I haven't used in years.  One of the requisites to build Android, due to an incompatibility, is to use JDK 1.5 update 12 or higher.  I have the JDK installed in /usr/java in a folder next to  /usr/java/jre1.6.0_17...  

When I try to "make" the source I downloaded, I get the error that I am using the wrong version of java (ie the latter vs the former). I know that I need to deselect/uninstall the JRE 1.6 but I guess my apprehension is that I will lose some functionality somewhere else...  Would the SDK fill the gaps lost by zapping the JRE 1.6 so I can use Java elsewhere?  Also, is there some sort of configuration file I would need to update to make the system "see" the install of the JDK from terminal?  I am so close to knowing what I am doing but it is all still fairly fresh to me after 4 months.  This phase of learning kills me, but open source really is worth every second of effort.

Thanks!

---

### Post by GregBrannon on 2010-02-20
Some IDEs (all?), Eclipse for sure, allow you to choose which version of Java is used in the compile process.  Would that help?

---

### Post by boredpcguy on 2010-02-20
Thanks for the hint...  I think you solved a future problem before it happened in Eclipse lol.
After I designated the JDK as the default for compiling in Eclipse, I ran make from the working directory of my source and still got the error 
```

You are attempting to build with the incorrect version
of java.
 
Your version is: java version "1.6.0_15".
The correct version is: 1.5.

```

I know I have to change some path somewhere to point to the JDK but I am not sure where my terminal commands are pulling this info from in the first place.  are there any pointers for a noob that might help me find out where that kind of configuration might be found, like some protocol in linux machines that is commonly followed?  thanks again!

---

### Post by GregBrannon on 2010-02-21
I installed the Java SDK, and it just works, so I can't talk you through terminal commands to fix your problem.

"It just works" means to me that when I start a project in Eclipse, I have the option on the first "Create Java Project" page, in the "JRE" section of the page, to choose the JRE environment.  There's also an option in that window to "Configure the JRE."  That may be where you need to go.

OR, you may need to check your Java SDK/JRE install.  As I said, mine just works.  Since your's doesn't, perhaps there's a problems with your install.

---

### Post by GregBrannon on 2010-02-21
Also, it's not clear from your original post if you installed the Android SDK.  If not, Google "install android sdk" and find a link with instructions on how to do that for your  environment.

---

