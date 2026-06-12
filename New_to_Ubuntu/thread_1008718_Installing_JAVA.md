---
title: "Installing JAVA"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by BuntuFirstTimer on 2008-12-11
Every websites on installing JAVA I've been to are very confusing. Can somebody instruct me how to install JAVA written in very easy English?

Sorry for being too direct.

---

### Post by BuntuFirstTimer on 2008-12-11
Oh sorry, I still use Hardy Heron

---

### Post by albinootje on 2008-12-11
Assuming that you want java inside Firefox :

Open a terminal.
Type in : 

sudo apt-get install sun-java5-jre sun-java5-plugin

Restart Firefox

---

### Post by tuxxy on 2008-12-11
Java is included in ubuntu-restricted-extras which should be installed on any fresh installations, it includes Flash, Java, Codecs etc

Open temrinal and enter

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Joeb454 on 2008-12-11
Actually you'll probably want java6 ;)

Java 5 is pretty old :)

```
sudo apt-get install sun-java6-jre sun-java6-bin
```

---

### Post by jimmy the saint on 2008-12-11
What tuxxy said.  The restricted extras will also give you flash, mp3 support and a few other goodies to make the *buntu experience more enjoyable!

---

### Post by chrispy9 on 2008-12-12
Thanks for your simple instructions.  Took my computer a few minutes to complete the task, and, unfortunately, it did NOT seem to install a working copy of Java on my machine.

I still get the following message:

Java must be enabled for radar loops to display.

Any other ideas?...Chris.

---

### Post by albinootje on 2008-12-12
Can you show the content of /usr/lib/firefox/plugins/ ?

I'm using 8.10 and it looks like this :

lrwxrwxrwx 1 root root   39 2008-12-06 19:52 libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so

---

### Post by BuntuFirstTimer on 2008-12-14
Thank you people... but after I put

```
sudo apt-get install sun-java6-jre sun-java6-bin
```

into the terminal, it seems that Firefox doesn't recognize this.

Any ideas?

---

### Post by taurus on 2008-12-14
> **BuntuFirstTimer said:**
> Thank you people... but after I put

```
sudo apt-get install sun-java6-jre sun-java6-bin
```

into the terminal, it seems that Firefox doesn't recognize this.

Any ideas?

I have no idea what you meant here.  You can open a terminal by clicking Applications -> Accessories -> Terminal.  Then, type that command in to install Sun java 1.6.

---

### Post by starcannon on 2008-12-14
Java6 for linux is buggy with the Blackboard website, if one has college work that requires blackboard, then sunjava5 is what one will want to use. Sunjava6 will work with most of blackboard, but if you have a teacher that uses blackboard to administer tests... you may get 1/4 the way through the test, 1/2 the way through, maybe even 3/4 the way through, but you will not likely get all the way through before it crashes. For now, unless there is some compelling reason to use sunjava6, and especially for college students, stick with 5.

GL and have fun.

> **Joeb454 said:**
> Actually you'll probably want java6 ;)

Java 5 is pretty old :)

```
sudo apt-get install sun-java6-jre sun-java6-bin
```

---

### Post by BuntuFirstTimer on 2008-12-16
> **taurus said:**
> I have no idea what you meant here.  You can open a terminal by clicking Applications -> Accessories -> Terminal.  Then, type that command in to install Sun java 1.6.

I did type this command into the terminal and installed it completely. It's just that Firefox wouldn't recognize that I installed Java.

---

### Post by albinootje on 2008-12-16
> **BuntuFirstTimer said:**
> I did type this command into the terminal and installed it completely. It's just that Firefox wouldn't recognize that I installed Java.

Isn't also sun-java6-plugin needed if you want Java support in Firefox ?
Or did that get installed with it ?

---

### Post by jamesstansell on 2008-12-16
> **albinootje said:**
> Isn't also sun-java6-plugin needed if you want Java support in Firefox ?
Or did that get installed with it ?

Yes, the sun-java6-plugin package is needed (or at least recommended) to enable the firefox java plugin.

---

### Post by jamesstansell on 2008-12-16
> **starcannon said:**
> Java6 for linux is buggy with the Blackboard website, if one has college work that requires blackboard, then sunjava5 is what one will want to use. Sunjava6 will work with most of blackboard, but if you have a teacher that uses blackboard to administer tests... you may get 1/4 the way through the test, 1/2 the way through, maybe even 3/4 the way through, but you will not likely get all the way through before it crashes. For now, unless there is some compelling reason to use sunjava6, and especially for college students, stick with 5.

GL and have fun.

Do you have a reference to any bug report(s)?

Do you know if the new plugin (libnpjp2.so - the plugin2) included with java 6u10 and 6u11 works any better with Blackboard?

---

### Post by starcannon on 2008-12-16
I have no bug reports, only anecdotal experience on 6 different computers. I'm not even sure that the problem resides with sun, it very well could be poorly written software with Blackboard. My last experience with this problem was this summer, and it was still present; the only way to take a test on Blackboard was to downgrade to Sun Java 5. 

I have spoken to the blackboard tech support regarding the issue, and of course was promptly told they do not support Linux, and only deal with Windows, I am not even sure if they deal with OSX.

I also use mathXL and had to actually Vbox xp in order to use that popular online college math program. My math professor was invited to some sort of advisory panel for mathXL and put in a good word for Linux and OSX students; she said the mathXL people seemed very open to the concept of inclusion and had hope that it would be available to us by 2009, I am a bit of a scalded dog and remain skeptical and reserve a wait and see attitude.

Anyway, I realize its not very good of me to not submit bug reports, and at this point it would be difficult to do as I don't have log files for it, and am not currently enrolled in any classes that require Blackboard.

Sun Java 5 works, and when one is going to school full time, well, its sometimes easy to just be lazy and just run with the work around.

---

### Post by lopoetve on 2008-12-16
is the sun-java6-plugin available on 64bit 8.10, or is that the new thing sun just came out with that I need to get?

---

### Post by starcannon on 2008-12-17
> **lopoetve said:**
> is the sun-java6-plugin available on 64bit 8.10, or is that the new thing sun just came out with that I need to get?
Its available(and has been for quite some time) in the synaptic package manager:
System>Administration>Synaptic Package Manager
Search: sun-java6
install the following:
sun-java6-bin
sun-java6-jre
sun-java6-plugin

I have little experience with 64bit, I ran it a month and went back to 32bit, so your experience is likely already greater than mine regarding how to proceed from here.

---

### Post by jamesstansell on 2008-12-17
> **lopoetve said:**
> is the sun-java6-plugin available on 64bit 8.10, or is that the new thing sun just came out with that I need to get?

It's the new thing. (java 6u12 early access, meaning beta at best)

The sticky java thread in the 64-bit forum has a pointer.

---

### Post by lopoetve on 2008-12-17
> **starcannon said:**
> Its available(and has been for quite some time) in the synaptic package manager:
System>Administration>Synaptic Package Manager
Search: sun-java6
install the following:
sun-java6-bin
sun-java6-jre
sun-java6-plugin

I have little experience with 64bit, I ran it a month and went back to 32bit, so your experience is likely already greater than mine regarding how to proceed from here.

Not listed anywhere I can see.  sudo apt-get install sun-java6-plugin doesn't list anything and says no package either.  >_<

Didn't think this would be that hard.

---

### Post by uniqueumang on 2008-12-17
How come noone is suggesting synaptic package manager for installation of java? :S

---

### Post by starcannon on 2008-12-17
> **uniqueumang said:**
> How come noone is suggesting synaptic package manager for installation of java? :S

I did in post #18
[http://ubuntuforums.org/showpost.php?p=6384446&postcount=18](http://ubuntuforums.org/showpost.php?p=6384446&postcount=18)
:)

---

### Post by starcannon on 2008-12-17
> **lopoetve said:**
> Not listed anywhere I can see.  sudo apt-get install sun-java6-plugin doesn't list anything and says no package either.  >_<

Didn't think this would be that hard.

Make sure your software sources are all enabled:
[IMG]http://img384.imageshack.us/img384/6892/sources1eg2.png[/IMG]
[IMG]http://img384.imageshack.us/img384/469/sources2zc8.png[/IMG]

---

### Post by jamesstansell on 2008-12-17
> **starcannon said:**
> Make sure your software sources are all enabled:


The sun-java6-plugin package doesn't exist for 64-bit ubuntu.

(But check again in about 3 months.)

---

### Post by uniqueumang on 2008-12-17
ummm....I am lost!!! do u want help regarding installation of java , or do you want help installing java for firefox?

but before we continue ::
 lets check for java 

ccan you run following in your terminal :
```


 sudo update-alternatives --config java 
```

It should show list of java installed. If there is no java installed if no java installed then install one as mentioned above.

BTW : output of above code looks like following :
```


here are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*         1    /usr/lib/jvm/java-6-sun/jre/bin/java
          2    /usr/bin/gij-4.2
          3    /usr/bin/gij-4.3
 +        4    /usr/lib/jvm/java-gcj/jre/bin/java

Press enter to keep the default[*], or type selection number:

```

---

### Post by lopoetve on 2008-12-17
> **jamesstansell said:**
> The sun-java6-plugin package doesn't exist for 64-bit ubuntu.

(But check again in about 3 months.)

Sonofa!

/me goes to download 8.10 32bit.  :(

---

### Post by lopoetve on 2008-12-17
> **starcannon said:**
> Make sure your software sources are all enabled:
[IMdG]http://img384.imageshack.us/img384/6892/sources1eg2.png[/IMG]
[IMdG]http://img384.imageshack.us/img384/469/sources2zc8.png[/IMG]

Pretty sure they all are ;)  I don't think the plugin exists for 64bit.

---

### Post by Ascott on 2008-12-18
I am also a new user trying to install JAVA. I now have the following message, and need to know how to proceed from here:-   dpkg --configure -a
dpkg: requested operation requires superuser privilege

---

### Post by albinootje on 2008-12-18
> **Ascott said:**
> I am also a new user trying to install JAVA. I now have the following message, and need to know how to proceed from here:-   dpkg --configure -a
dpkg: requested operation requires superuser privilege

Try: sudo dpkg --configure -a

---

### Post by Ascott on 2008-12-18
> **albinootje said:**
> Try: sudo dpkg --configure -a

I now receive the following message:-


E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
WHAT NOW?.

---

### Post by albinootje on 2008-12-18
> **Ascott said:**
> I now receive the following message:-


E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
WHAT NOW?.
You probably have the add/remove application or synaptic package manager open. Close that first.

---

### Post by Ascott on 2008-12-18
In the terminal I now have a page with a blue background, and grey foreground page with the JAVA licence agreement.  This has a heading in red (Configuring sun-java6-jre),but I have no indication that anything is happening.  I need Java for the MONEYAM website, otherwise I would say forget it, and use Windows to view this site,

---

### Post by albinootje on 2008-12-18
> **Ascott said:**
> In the terminal I now have a page with a blue background, and grey foreground page with the JAVA licence agreement.  This has a heading in red (Configuring sun-java6-jre),but I have no indication that anything is happening.  I need Java for the MONEYAM website, otherwise I would say forget it, and use Windows to view this site,

You should press the tab-key, and then press the OK button to accept the Java license.
After that the installation should continue.

---

### Post by Ascott on 2008-12-18
Thank you , thar worked, but Firefox still does not see Java

---

### Post by albinootje on 2008-12-18
> **Ascott said:**
> Thank you , thar worked, but Firefox still does not see Java

Did you restart Firefox and cleared the cache ?
Can you post the output of
```

ls -la /usr/lib/mozilla/plugins/
ls -la /usr/lib/firefox/plugins/
ls -la /etc/alternatives/java*

```

---

### Post by jamesstansell on 2008-12-18
> **Ascott said:**
> Thank you , thar worked, but Firefox still does not see Java

Do you have the sun-java6-plugin package installed?

---

### Post by Ascott on 2008-12-19
I entered check you suggeste and received the followin:-
tom@tom-laptop:~$ sudo ls -la /usr/lib/mozilla/plugins/
[sudo] password for tom: 
total 8
drwxr-xr-x 2 root root 4096 2008-12-12 16:38 .
drwxr-xr-x 4 root root 4096 2008-10-30 00:50 ..
lrwxrwxrwx 1 root root   37 2008-12-12 16:38 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
lrwxrwxrwx 1 root root   44 2008-12-11 17:14 libtotem-basic-plugin.so -> ../../totem/default/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root   42 2008-12-11 17:14 libtotem-gmp-plugin.so -> ../../totem/default/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root   44 2008-12-11 17:14 libtotem-mully-plugin.so -> ../../totem/default/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root   50 2008-12-11 17:14 libtotem-narrowspace-plugin.so -> ../../totem/default/libtotem-narrowspace-plugin.so
tom@tom-laptop:~$  sudo ls -la /usr/lib/firefox/plugins/
total 8
drwxr-xr-x 2 root root 4096 2008-12-12 16:38 .
drwxr-xr-x 4 root root 4096 2008-12-12 16:36 ..
lrwxrwxrwx 1 root root   37 2008-12-12 16:38 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin
tom@tom-laptop:~$  sudo ls -la /etc/alternatives/java*
lrwxrwxrwx 1 root root 40 2008-12-18 19:11 /etc/alternatives/java -> /usr/lib/jvm/java-6-openjdk/jre/bin/java
lrwxrwxrwx 1 root root 50 2008-12-18 19:11 /etc/alternatives/java.1.gz -> /usr/lib/jvm/java-6-openjdk/jre/man/man1/java.1.gz
lrwxrwxrwx 1 root root 12 2008-12-14 14:53 /etc/alternatives/javac -> /usr/bin/ecj
lrwxrwxrwx 1 root root 28 2008-12-14 14:53 /etc/alternatives/javac.1.gz -> /usr/share/man/man1/ecj.1.gz
lrwxrwxrwx 1 root root 14 2008-12-14 14:53 /etc/alternatives/javadoc -> /usr/bin/gjdoc
lrwxrwxrwx 1 root root 30 2008-12-14 14:53 /etc/alternatives/javadoc.1.gz -> /usr/share/man/man1/gjdoc.1.gz
lrwxrwxrwx 1 root root 39 2008-12-18 19:22 /etc/alternatives/java_vm -> /usr/lib/jvm/java-6-sun/jre/bin/java_vm
lrwxrwxrwx 1 root root 42 2008-12-18 19:22 /etc/alternatives/javaws -> /usr/lib/jvm/java-6-openjdk/jre/bin/javaws
lrwxrwxrwx 1 root root 52 2008-12-18 19:22 /etc/alternatives/javaws.1.gz -> /usr/lib/jvm/java-6-openjdk/jre/man/man1/javaws.1.gz
tom@tom-laptop:~$ 
But I still get the following JAVA message:-Java Runtime Environment is not working on your computer.

---

### Post by albinootje on 2008-12-19
> **Ascott said:**
> I entered check you suggeste and received the followin:-
tom@tom-laptop:~$ sudo ls -la /usr/lib/mozilla/plugins/
--cut info --
tom@tom-laptop:~$  sudo ls -la /usr/lib/firefox/plugins/
--cut info --

Thanks for that info.
You're missing a symlink to the java plugin in your firefox plugins directory, that must be why it's not working.

---

### Post by Ascott on 2008-12-19
Thank you to all who answered. I got the final solution from the Firefox online help.
All is now working.

---

### Post by BuntuFirstTimer on 2008-12-20
> **albinootje said:**
> Isn't also sun-java6-plugin needed if you want Java support in Firefox ?
Or did that get installed with it ?

somehow I typed ```
sudo apt-get install sun-java6-plugin
```

into the terminal and it didn't work.

Is there another way of doing it?

---

### Post by Sef on 2008-12-20
> Thank you to all who answered. I got the final solution from the Firefox online help.
All is now working.

Could you provide a link to the solution or post it in this thread.  Thank you.

---

### Post by igknighted on 2008-12-20
Wow... this thread has been hijacked three times in 3 days... is that some sort of record?

@ the OP:
> **BuntuFirstTimer said:**
> somehow I typed ```
sudo apt-get install sun-java6-plugin
```

into the terminal and it didn't work.

Is there another way of doing it?

What is the output of the command 'uname -a'?  Or, if you know, did you install the 32bit (i386) or 64bit (amd64) version?

There is no 64bit java plugin in the repo's right now.  Sun has one available on their website, or you can go to the 64bit section of the forum and read the how-to in the stickies there.

---

### Post by albinootje on 2008-12-20
> **Ascott said:**
> Thank you to all who answered. I got the final solution from the Firefox online help.
All is now working.

Can you share the solution with us ?
E.g. give a link to "the Firefox online help" you've used.

---

### Post by MTGap on 2008-12-20
> E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

I got this too because at the time when the Java Configuration thing came up and said <Ok> I didn't know to press TAB so I just exited out, now I can't do anything. The Syanpatic Package Manager isn't working anymore because of it... 


Anyone way I can get back to that configuration and press TAB?

---

### Post by albinootje on 2008-12-20
> **MTGap said:**
> I got this too because at the time when the Java Configuration thing came up and said <Ok> I didn't know to press TAB so I just exited out, now I can't do anything. The Syanpatic Package Manager isn't working anymore because of it... 


Anyone way I can get back to that configuration and press TAB?

Can you perform the following in a terminal, and post any errors ?
```

sudo killall synaptic
sudo apt-get update
sudo apt-get -f install

```

---

### Post by MTGap on 2008-12-20
> E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


The first sudo killall said no process killed, the update one started working then gave a similar error like the first one. The third gave the error instantly. 

I still can't install anything use Synaptic Package Manager or the Add/Remove Programs.

---

### Post by albinootje on 2008-12-20
> **MTGap said:**
> The first sudo killall said no process killed, the update one started working then gave a similar error like the first one. The third gave the error instantly. 

I still can't install anything use Synaptic Package Manager or the Add/Remove Programs.

You need to make sure that all programs like synaptic and apt-get and dpkg are not running anymore, and then try installing again.
Since you're not providing the output (for whatever reason) the easiest solution for you might be a reboot, and try again.

---

### Post by MTGap on 2008-12-20
Yeah I restarted and was able to fix everything and install Java... I'm happy now Thx. :)

---

### Post by jamesstansell on 2008-12-20
> **BuntuFirstTimer said:**
> somehow I typed ```
sudo apt-get install sun-java6-plugin
```

into the terminal and it didn't work.

Is there another way of doing it?

Can you be more specific about how it didn't work?

Also, what is the output of that apt-get command?

---

### Post by BuntuFirstTimer on 2008-12-20
> **jamesstansell said:**
> Can you be more specific about how it didn't work?

Also, what is the output of that apt-get command?

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate

```

---

### Post by jamesstansell on 2008-12-20
> **BuntuFirstTimer said:**
> ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate

```

If you're running a 64-bit ubuntu version then that is the curently expected output.  Right now there isn't a 64-bit version of sun-java6-plugin available (it will hopefully come out in about 3 months time.)

If you're running a 32-bit ubuntu version then you need to enable the multiverse repository.  Here is a long writeup about how to do that:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

