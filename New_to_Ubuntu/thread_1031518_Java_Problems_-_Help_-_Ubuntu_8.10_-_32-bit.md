---
title: "Java Problems - Help - Ubuntu 8.10 - 32-bit"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by crjackson on 2009-01-05
The company I work for uses a Java embeded page for placing PO's. I can access the first page but the Java buttons don't all show (the ones I need) and the ones that do show, don't work.

I went to [www.java.com](www.java.com) and tested my setup and it tells me I have an older version of java installed (6.10).

Then I may have done a bad thing. I downloaded the 6.11 bin file and installed it using root permissions. I tested again and the sun site reports version 6.10.

I installed it again using standard user permissions and tested again with the same result.

1) Did I screw up my system as far as java goes?
2) How do I remove the manually installed version?
3) How can I update my installed version (and hopefully get the website working)?

Any help is appreciated...

---

### Post by stchman on 2009-01-05
> **crjackson said:**
> The company I work for uses a Java embeded page for placing PO's. I can access the first page but the Java buttons don't all show (the ones I need) and the ones that do show, don't work.

I went to [www.java.com](www.java.com) and tested my setup and it tells me I have an older version of java installed (6.10).

Then I may have done a bad thing. I downloaded the 6.11 bin file and installed it using root permissions. I tested again and the sun site reports version 6.10.

I installed it again using standard user permissions and tested again with the same result.

1) Did I screw up my system as far as java goes?
2) How do I remove the manually installed version?
3) How can I update my installed version (and hopefully get the website working)?

Any help is appreciated...

SUN Java 1.6 is available in the repos for 32 bit and work perfectly.

```
sudo apt-get -y install sun-java6-bin sun-java6-fonts sun-java6-jdk sun-java6-jre sun-java6-plugin

```

This should do the trick.

As far as removing the old stuff try looking in your ~/.mozilla/plugins folder and see if there are any .so links.

---

### Post by crjackson on 2009-01-05
> **stchman said:**
> SUN Java 1.6 is available in the repos for 32 bit and work perfectly.

```
sudo apt-get -y install sun-java6-bin sun-java6-fonts sun-java6-jdk sun-java6-jre sun-java6-plugin

```

This should do the trick.

As far as removing the old stuff try looking in your ~/.mozilla/plugins folder and see if there are any .so links.

Okay, would that be the same version installed from ubuntu-restricted-extras? I already had that installed.

If I don't remove the one from the bin file I downloaded will in cause any conflicts or problems?

---

### Post by crjackson on 2009-01-05
I'm thinking you can have multiple versions of java installed without problems. I guess it's the plugin version I should be concerned with.

I just want to know if installing the above is different from installing ubuntu-restricted-extras.

---

### Post by Vadi on 2009-01-05
You can have multiple java versions at once: [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

Try also GNU Java, icedtea, and openjdk. One of them might work.

---

### Post by Vadi on 2009-01-05
You can have multiple java versions at once: [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

Try also GNU Java, icedtea, and openjdk. One of them might work.

---

### Post by crjackson on 2009-01-05
> **Vadi said:**
> You can have multiple java versions at once: [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

Try also GNU Java, icedtea, and openjdk. One of them might work.


Thanks Vadi - I will give it a shot. BTW can you tell me if the version installed using ubuntu-restricted-extras somehow differs from the install method listed above?

---

### Post by Vadi on 2009-01-05
Don't think so. ubuntu-restricted-extras installs sun-java6-jre, which is part of the package set listed above.

---

### Post by crjackson on 2009-01-05
Okay, thanks for the information.

---

### Post by crjackson on 2009-01-05
Well so far nothing is working except booting into windows. The embedded Java frames just hang while loading, and it seems none of the Java's will solve the problem.

It works using MS Windows so I guess I'm stuck using that for work. It seems that Linux/Firefox just can't do the job in this particular case.

---

### Post by weegee101 on 2009-01-06
If GCJ is still installed (which I don't think it should be) it could be causing problems with the mozilla applet jvm since the Sun Java Applet JVM looks for "java" in the path.  Go ahead and install the sun-java6-jdk (I've had some situations where the jre has issues, both in Windows and Linux) using:
```
sudo apt-get install sun-java6-jdk
```

then type:
```
sudo update-alternatives --config java
```

and if it presents you with a list of options, chose the one that looks something like 
```
/usr/lib/jvm/java-6-sun/jre/bin/java
```

---

### Post by Vadi on 2009-01-06
It's very well plausible. Open source != working...

You can use Virtualbox or VMware to run windows inside it, then java will work (unless you're doing 3d work in it). Easier than rebooting whenever you need to work.

---

### Post by crjackson on 2009-01-06
> **weegee101 said:**
> If GCJ is still installed (which I don't think it should be) it could be causing problems with the mozilla applet jvm since the Sun Java Applet JVM looks for "java" in the path.  Go ahead and install the sun-java6-jdk (I've had some situations where the jre has issues, both in Windows and Linux) using:
```
sudo apt-get install sun-java6-jdk
```

then type:
```
sudo update-alternatives --config java
```

and if it presents you with a list of options, chose the one that looks something like 
```
/usr/lib/jvm/java-6-sun/jre/bin/java
```

Thanks, did all that and still no change.

---

### Post by crjackson on 2009-01-06
> **Vadi said:**
> It's very well plausible. Open source != working...

You can use Virtualbox or VMware to run windows inside it, then java will work (unless you're doing 3d work in it). Easier than rebooting whenever you need to work.

Thought about doing that but I'm told that every time there is a kernel upgrade it will break the install and I'll have to re-install everything again.

---

### Post by Vadi on 2009-01-06
Well, you were misinformed. The only thing that breaks is the addons which you have to reinstall inside the vm after *it* (not your host) gets upgraded.

Reinstalling addons is a 2 min thing, and since windows practically never gets kernel upgrades, that happens very rarely...

---

### Post by crjackson on 2009-01-06
> **Vadi said:**
> Well, you were misinformed. The only thing that breaks is the addons which you have to reinstall inside the vm after *it* (not your host) gets upgraded.

Reinstalling addons is a 2 min thing, and since windows practically never gets kernel upgrades, that happens very rarely...

Okay, it sounds like that might be my only solution then. I'll give that at shot this weekend.

---

### Post by crjackson on 2009-01-07
Just for information purposes, what would be your best guess for why Java won't work on this page using Ubuntu. Would you lean towards the Linux Java or the Firefox Browser?

I realize that the problem is most probably due to the site it's self, but one of the above factors is where the compatibility problem is. I'm just wondering which one.

---

### Post by crjackson on 2009-01-09
Has this thread died already?

---

### Post by Vadi on 2009-01-09
Nobody that knows that answer visited :P

---

### Post by crjackson on 2009-01-10
> **Vadi said:**
> Nobody that knows that answer visited :P

Yeah it's a bummer. I really wanted to find a way to make it work properly withing Ubuntu/Firefox without and MS solutions.

---

### Post by Vadi on 2009-01-10
It's most likely a Java problem I suspect. But Java is rapidly improving.

---

### Post by crjackson on 2009-01-10
> **Vadi said:**
> It's most likely a Java problem I suspect. But Java is rapidly improving.

Can't come soon enough for me.

---

### Post by PRC09 on 2009-02-21
Hi All,
   I am new at using Ubuntu and had a horrible time with java as well.Found this link and now everything is sorted out perfectly.Just follow all the steps including adding the plugin for Firefox (which was my problem) and now everything is working perfectly.Using Ubuntu 8.10

[http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/](http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/)

PS:I have used this on 64 bit as well.....

---

### Post by Vadi on 2009-02-21
Hey thanks for that. Needed an easy guide for the 64bit plugin.

---

### Post by txcrackers on 2009-02-21
99% of the time it's not Linux or Java that's the issue - it's the application itself. Typically, when "not running" problems arise, it's because the application is hard-coded to expect certain Operating System settings (like file-paths) instead of being written, as Java expects, to be OS-agnostic.

In this particular case, my contention is that the application was written on a Windows machine, works on a Windows machine, and was never tested on another browser or OS.

Don't blame Java or Linux. If you must blame someone, blame the idiot that wrote the application.

---

### Post by Vadi on 2009-02-21
Yet somehow the app manages to run if you use another java runtime or do some other magic to please it.

Sorry, but I don't believe the major cause is a hardcoded path. Most apps would be easily fixed now.

---

### Post by txcrackers on 2009-02-21
That's not what I said - I used file-paths as an example. What I did mean that the application developer (and their company) has to actually *ensure* that the application works correctly across JVMs and OSs. Most times, this does **not** occur, especially if there's a GUI involved. The fact that you have to "do magic" to get the application to run means the developers of said application have not done their job properly (from the user's point of view).

---

### Post by Vadi on 2009-02-21
Not really, not when this magic involves swapping several different versions of Java and hoping one of them works...

I do understand what do you mean by paths and etc. though. This is why actually Flash beats Java in cross-platformity - they abstract all of this for you, provide variables, so it "just works" even on the platform-specific things like temp paths and user's home folder and etc.

---

### Post by karlr42 on 2009-02-21
Um, Java abtracts that too, but you have to tell it to, it's flexible.
As an example, in a recent project I was working on to write a multicasting file tranfer client(and server), we needed a way to save a received file to disk. We started of with:
[PHP]outFile = new FileOutputStream(savePath + "\\" + fileName);//where to save the files[/PHP]
Which would have worked fine on our Windows machines, but not on my Hardy box. But then we discovered another way of doing it(we're students, not enterprise -level developers :P):
[PHP]outFile = new FileOutputStream(savePath + File.separator + fileName);//where to save the files[/PHP]
One of those is better, more portable than the other(we got awarded extra marks for cross-platform compatibility because of things like that). 
But Java is dependent on the programmer knowing what they're doing, knowing the language's abilities.

---

### Post by Vadi on 2009-02-21
@karlr42: cool, thanks for pointing that out.

---

### Post by crjackson on 2009-02-23
> **txcrackers said:**
> Don't blame Java or Linux. If you must blame someone, blame the idiot that wrote the application.

I'm not blaming anyone... I just need a solution.

---

### Post by fsando on 2009-03-05
I use FF 3.06 on Intrepid 8.10 32bit

I'm having very similar problems. 

I need to access my web bank with java. When I try to log in it usually goes like this. First try fails and FF locks up completely. Second or third time will succeed without lock up. Then the payments will lock up (each payment needs a confirmation in java). then I'll log in two, three sometimes up to 7 or 8 times before the process actually goes all the way through. And I'm never able to complete more than one payment in a row. Just spent two hours making three (3!!) payments.

I did not have any of those problems with FF2 (which is why I kept FF2 around just until it was EOL'ed)

I have installed (java6 stuff listed):

sun-java6-fonts
sun-java6-bin
sun-java6-jre
sun-java6-plugin
sun-java6-jdk

Following was tried
[LIST]
[*]Several attempts at login always ending in the java applet turning into a grey square and FF complete freeze, FF eats up one processor.
[*]Install jav6-fonts - after which I had first successful login and one payment. Attempt at another payment resulted in java applet turning into grey square and complete freeze and FF eats up one processor.
[*]Reinstall of jav6-plugin after which login and one payment was possible (may be an unrelated strike of luc&#7729;).
[*]Reinstall all of sun-jav6* - no change.
[*]Delete ~/.java - login and one payment succeeded didn't have more bills for this time ;) so didn't try more.
[/LIST]
It's as if java has trouble reading something that is already cached - hence the one-time successes.

---

### Post by theDaveTheRave on 2009-03-05
crjackson

the easy way to determine if it is a firefox or OS problem is to load firefox onto your windows platform.

If the system doesn't work then I would say you should be going to your boss and mentioning that the original devs have restricted you to only those people who use MS / internet explorer.

Proviso... if the devs were in house keep your mouth shut, or you may risk loosing your job when you point out how "stupid" a developer was, especially as that develper is now probably your boss or your bosses boss!
In this case just silently mention that it doesn't work from firefox, and see what happens...

Karl42

You mention about using the power of java to make it more platform independent, remember because we are using linux we have a tendancy to think along "platform independent" ideas. Allway keep an eye on the API as there are plenty of little tricks likethis one for getting things done in a more "elegant" manner.

David

---

### Post by Johandahl on 2009-03-24
I have had this problem too on another java applet

[http://www.proceedo.net/applet.htm](http://www.proceedo.net/applet.htm)

If firefox isn't running and I start firefox with
firefox [http://www.proceedo.net/applet.htm](http://www.proceedo.net/applet.htm)
will it almost always run otherwise it just hangs we browser.
This applet worked in 8.04 and it works on RHEL5. So something is flaky in 8.10.

/Johan Dahl

---

### Post by crjackson on 2009-04-01
> **theDaveTheRave said:**
> crjackson

the easy way to determine if it is a firefox or OS problem is to load firefox onto your windows platform.

David

The page works fine in Windows with Firefox/IE.

---

