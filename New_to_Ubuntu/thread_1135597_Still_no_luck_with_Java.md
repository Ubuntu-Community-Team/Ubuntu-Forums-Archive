---
title: "Still no luck with Java"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by mystmaiden on 2009-04-24
I have tried pretty much everything to get Java going in Ubuntu 8.04 (everything but the right thing!). First I got jdk, but could not download icetea6-plugin. With add/remove, every time I searched for it, it would show up on the list and immediately disappear before I could check it.

Someone suggested I get sun java, so I removed jdk , installed sun java and still when I go to a page with java on it, I just get an empty box though under applications/internet I do show Sun Java webstart. I went to a Java test page, and it says Java Version 1.6.0_07 from Sun Microsystems Inc is enabled. 

Maybe it has something to do with Yahoo games, which is what I am trying to get working for my husband to use their daily crosswords and literati games. Do I need icedtea6-plugin 
to run Sun?

Trying not to pull my hair out here :)

Thanks,
mystmaiden

---

### Post by gandaran on 2009-04-24
> **mystmaiden said:**
> I have tried pretty much everything to get Java going in Ubuntu 8.04 (everything but the right thing!). First I got jdk, but could not download icetea6-plugin. With add/remove, every time I searched for it, it would show up on the list and immediately disappear before I could check it.

Someone suggested I get sun java, so I removed jdk , installed sun java and still when I go to a page with java on it, I just get an empty box though under applications/internet I do show Sun Java webstart. I went to a Java test page, and it says Java Version 1.6.0_07 from Sun Microsystems Inc is enabled. 

Maybe it has something to do with Yahoo games, which is what I am trying to get working for my husband to use their daily crosswords and literati games. Do I need icedtea6-plugin 
to run Sun?

Trying not to pull my hair out here :)

Thanks,
mystmaiden
did you also install the sun-java6-plugin?

---

### Post by ssdt on 2009-04-24
I think that the plugin in firefox would fix every problem. Ubuntu is so great with java that it even loads java that is not loaded in Windows where Windows freezes but here in Ubuntu it doesn't.

---

### Post by mystmaiden on 2009-04-24
I think I did load the sun java plugin. Is there a way I can check and make sure? 

Thanks to both of you.

---

### Post by gandaran on 2009-04-24
> **mystmaiden said:**
> I think I did load the sun java plugin. Is there a way I can check and make sure? 

Thanks to both of you.
yes, use synaptic to check if it's installed.
can you post the games link so we can try them?

---

### Post by mystmaiden on 2009-04-24
[http://games.yahoo.com/daily-games/dailycrosswords](http://games.yahoo.com/daily-games/dailycrosswords)

I found a thread at [https://answers.launchpad.net/ubuntu/+question/23218](https://answers.launchpad.net/ubuntu/+question/23218) that seems to indicate that having 2 java installed is the trouble. Though I thought I'd untinstalled the first one, when I checked I got - 
me@computer:~$  update-java-alternatives -l 
java-6-openjdk 1061 /usr/lib/jvm/java-6-openjdk
java-6-sun 63 /usr/lib/jvm/java-6-sun

Heh, unfortunately my brain is so scrambled now I can't remember how to remove the openjdk!

---

### Post by stchman on 2009-04-24
> **mystmaiden said:**
> I have tried pretty much everything to get Java going in Ubuntu 8.04 (everything but the right thing!). First I got jdk, but could not download icetea6-plugin. With add/remove, every time I searched for it, it would show up on the list and immediately disappear before I could check it.

Someone suggested I get sun java, so I removed jdk , installed sun java and still when I go to a page with java on it, I just get an empty box though under applications/internet I do show Sun Java webstart. I went to a Java test page, and it says Java Version 1.6.0_07 from Sun Microsystems Inc is enabled. 

Maybe it has something to do with Yahoo games, which is what I am trying to get working for my husband to use their daily crosswords and literati games. Do I need icedtea6-plugin 
to run Sun?

Trying not to pull my hair out here :)

Thanks,
mystmaiden

For 8.04 use the following:

32 bit
```
sudo apt-get -y install sun-java6-bin sun-java6-fonts sun-java6-jdk sun-java6-jre sun-java6-plugin

```


64 bit
```
sudo apt-get -y install icedtea-java7-jdk icedtea-java7-jre icedtea-java7-plugin

```

I have 8.04 in both 32 and 64 bit form running Java.  Mind you the 64 bit version the icedtea plugin works but not on 100% of all sites.  The SUN version works excellent.

---

### Post by gandaran on 2009-04-24
> **mystmaiden said:**
> [http://games.yahoo.com/daily-games/dailycrosswords](http://games.yahoo.com/daily-games/dailycrosswords)

I found a thread at [https://answers.launchpad.net/ubuntu/+question/23218](https://answers.launchpad.net/ubuntu/+question/23218) that seems to indicate that having 2 java installed is the trouble. Though I thought I'd untinstalled the first one, when I checked I got - 
me@computer:~$  update-java-alternatives -l 
java-6-openjdk 1061 /usr/lib/jvm/java-6-openjdk
java-6-sun 63 /usr/lib/jvm/java-6-sun

Heh, unfortunately my brain is so scrambled now I can't remember how to remove the openjdk!
I think some of those games won't work in linux, it's not java but I cont make out what plugin is needed, but most of those games uses flash, do you have adobe flash installed? 
use synaptic to remove the open java, it's easy, type java in search box, mark for complete removal all open java installed packages and click the apply button

---

### Post by mystmaiden on 2009-04-24
odd, because usually when played on Windows, it shows an applelet loading.. which I believed was java

---

### Post by Kirk M on 2009-04-24
> **gandaran said:**
> I think those games won't work in linux, it's not java but I cont make out what plugin is needed, mostly that site uses flash.
use synaptic to remove the open java, it's easy, type java in search box, mark for complete removal all open java installed packages and click the apply button

The games you're referring to are Flash based, not Java. The plugin you need is the Adobe Flash 10 plugin which can be installed via the Synaptic Package Manager.

Note: Make sure your browsser is closed before you do this.

Open the Package Manager and type *adobe-flashplugin* into the "Quick Search" field at the top and the correct plugin should then show at the top of the listed items (or somehwhere near the top). If the plugin doesn't show that it's already installed (it probably won't considering your problem) then mark it for installation, accept any extra packages that it might need to be installed as well and then hit "Apply" up in the tool bar. Once the installation is done you should be good to go.

HTH :)

---

### Post by mystmaiden on 2009-04-24
aha, I see what the confusion was on my part! Literati is java based, and it is working now, removing the openjdk and adding the fonts, etc.. Apologies for confusing the issue.

Now I'll download the flash and hopefully that will solve all of this. 

I am very grateful for all the help!!

Edited to add - It's working perfectly! You folks are true gems, thanks much!

---

