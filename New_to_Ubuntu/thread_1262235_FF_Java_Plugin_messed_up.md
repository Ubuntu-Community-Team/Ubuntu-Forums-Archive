---
title: "FF Java Plugin messed up?"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by BobJam on 2009-09-09
Yesterday I went to a website ([http://www.rpnscc.com/](http://www.rpnscc.com/)) and immediately FF closed.  After some investigation, I discovered that the cause was an out of date Java.  (The site author told me that his newsfeeds were using Java applets, for one).

I checked my version with ```
sudo java -version
``` and it returned:

```
java version "1.6.0_0"
OpenJDK Runtime Environment (IcedTea6 1.4.1) (6b14-1.4.1-0ubuntu11)
OpenJDK Server VM (build 14.0-b08, mixed mode)

```Nearest I can tell, the latest version is 1.6.0.16.

I also ran ```
sudo update-java-alternatives -l
``` to check my version against the latest available.

The return was ```
java-6-openjdk 1061 /usr/lib/jvm/java-6-openjdk
```So then I ran ```
sudo update-alternatives --config java
``` to install the appropriate JVM. As I understand the command, there should have been a pseudo-Wizard to prompt me through the process.

But this was the return I got:

```
There is only 1 program which provides java
(/usr/lib/jvm/java-6-openjdk/jre/bin/java). Nothing to configure.

```I had thought I had my arms around Java, but after this I was confused.

So I opened my "clean" profile, and it **WOULD** go to that site.  The "IcedTea Java Web Browser Plugin" is **EXACTLY** the same in both profiles.  At first glance then, the difference causing the problem would be add ons.  But there are two things that still concern me.

First, even if that's the reason I can't keep FF open while visiting that site (and I haven't done a test by disabling add ons 'till it works), it really doesn't address the issue of getting an update at all.

Second, and this really has me baffled, when I go to the Java Sun test site at [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml) with my clean profile, the test image doesn't appear, indicating that Java is not working properly in my clean profile - yet with my clean profile I can go to that rpnscc site (listed above) . . . and my working profile of course closes immediately when I try to visit that site.

So the clean profile works to visit that site, but BOTH profiles fail the Java test.  Very confusing.

So I googled and found this reference to updating Java in Ubuntu:  [https://answers.launchpad.net/ubuntu/+question/6026](https://answers.launchpad.net/ubuntu/+question/6026)

I did those commands (substituting 16 everywhere there was a 2 or 02), and at the end I did get an indication in the terminal that the installed version was 1.6.0.16 ```
sudo java -version
``` returned 1.6.0_16.

But when I did a restart it apparently reverted back because ```
sudo java -version
``` returned 1.6.0_0 again.

But my usr/lib/jvm directory has a jre1.6.0_16 folder in it (and **NO** 1.6.0_0 folder)

And I can get the Java console with the "jcontrol" command, and it indicates both user and system are enabled with **jre1.6.0_16**.

This is all very confusing to me.  Does it have something to do with the FF IcedTea Java Web Browser Plugin not seeing the Java update?

What am I missing?

---

### Post by wobin77 on 2009-09-09
Well, maybe a dumb question.. (Using Ubuntu for 3 days now) But did you try to reinstall FF?

---

### Post by perce on 2009-09-09
Have you tried installing Sun's official plugin?

```
sudo apt-get install sun-java6-plugin
```

---

### Post by Excedio on 2009-09-09
Thanks for posting the website link...now I discovered that I need Java installed :-)

---

### Post by Codix121 on 2009-09-09
Totally irrelevant, but I clicked the link and my FF didn't close!
lol, nice to know my java's working fine :P Sorry! 
Good luck on the problem!

Try this:

go here:

[http://cards.lovingyou.com/index.php?step=sendcard&ec_id=3448](http://cards.lovingyou.com/index.php?step=sendcard&ec_id=3448)

It uses java, if you don't have a java, a link comes up that says
You need to download java, click here or something, not sure.

Uh just click it and firefox will automatically open up a "download plugins" (Java, etc) and they are all automatically done for you.
That's how I got my java to work anyway...

---

### Post by BobJam on 2009-09-09
> **wobin77 said:**
> Well, maybe a dumb question.. (Using Ubuntu for 3 days now) But did you try to reinstall FF?Considering that, but it's the last "drastic" alternative for me.  Want to try other stuff first . . . hoping I'll be able to solve it with suggestions made here.


> **perce said:**
> Have you tried installing Sun's official plugin?Tried that but no joy . . . terminal still shows 1.6.0_0.  Somehow I think I have to get rid of "OpenJDK" first.

> **Codix121 said:**
> Try this:
It uses java, if you don't have a java, a link comes up that says You need to download java, click here or something, not sure.A link **didn't** pop up . . . probably because I **DO** have Java, it's just an old version that apparently doesn't work on the rpnscc site.

Still trying to update my Java.  As I said, I probably have to figure out how to get rid of "OpenJDK" and then I might be able to install Sun's variant.  Or else I have to figure out how to update "OpenJDK" (which as I understand it is Ubuntu's open source variant of Java).

Learning more about Java than I bargained for.

Will post back here if I ever figure it out.

---

### Post by perce on 2009-09-09
> **BobJam said:**
> 
Tried that but no joy . . . terminal still shows 1.6.0_0.  Somehow I think I have to get rid of "OpenJDK" first.


Try something like this:

```
sudo apt-get remove --purge icedtea6-plugin 
```

It removes the openjdk plugin for Firefox (I think).

---

### Post by BobJam on 2009-09-10
> **perce said:**
> Try something like this:

```
sudo apt-get remove --purge icedtea6-plugin 
```It removes the openjdk plugin for Firefox (I think).Gotta get this down before I forget.

First of all, **IT WORKED**!!! Thanks **VERY MUCH** for the suggestions, perce. (And I will mark this thread "solved" when I'm finished making this post).

Here's what I did.

To begin with, I did this all with the FF browser closed. I have no idea if that's necessary, but just to be safe I wrote down the commands from perce here and closed FF.

And I don't know if the sequencing had anything to do with it, but I think it did.

One caveat . . . I had already installed 1.6.0.16 from that link I had posted before ( [https://answers.launchpad.net/ubuntu/+question/6026](https://answers.launchpad.net/ubuntu/+question/6026) ), so I don't know for sure if this should be the first thing done.

Step 1 (from here):

Remove OpenJDK with the command

```
sudo apt-get remove --purge icedtea6-plugin
```At this point I restarted (don't know if that was necessary either) just to be safe.

Then I opened FF and looked at my plugins just to see if IcedTea was gone. **IT WAS**!

And "**Java (TM) Plug-in 1.6.0_14**" was there.

Two things here.
[INDENT]     1. I don't know if this was from my previous attempt to install the Java update from that Launchpad link, but I suspect it was since I hadn't run perce's install command yet.

    2. Apparently the plug-in version, yes . . . it's "**14**" . . . is not the same as the jre version.
[/INDENT] Step 2.

Close FF again, just in case.

Run perce's install command

```
sudo apt-get install sun-java6-plugin
```Again, I may have been just reinstalling what I already installed with that Launchpad method (the link).  I think the terminal may have indicated that ("0 packages removed, 0 packages installed . . ." or something like that . . . can't remember, because I was so excited that it seemed to be working up to this point).

That's it for the steps.

But a coupla' comments need to be made.

    * The command "jcontrol" still worked, and the default is "automatic downloads" (and I left it that way), so I assume Sun Java will update itself.  But I'm not real sure if the plug-in will do that too.

    * The Sun test site **SHOWED JAVA WAS WORKING** and was updated to version 6 Update 16.

    * The "sudo java -version" command still showed "1.6.0_0".  Very confusing, but fine with me 'cause it works.

    * I was able to view the rpnscc site without FF closing.

Thanks again, perce, and HTH anyone else trying to update Java or having trouble with the IcedTea plugin.

---

