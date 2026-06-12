---
title: "New and Lost... plz help"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by angie4107 on 2009-04-26
I am really new at this... I 'd never used Linux or Ubuntu before  and just installed Ubuntu on my computer --loving it so far.. btw although I think there's a lot for me to learn now) and well I have a few questions.. 

1. I can't seem to get Java to work.. I installed the Java Runtime with Webstart and I went to the Java test page and it says I don't seem to have Java enabled (I then followed the instructions on their website and checked the "Enable Java" box.. but that didn't work.. and I've read about linking but honestly I don't understand at all what on earth it's talking about.. I really would appreciate help on this one.. oh and when I go to pogo.com for example it just says please wait while it loads and then nothing..  :(--

2. Secondly, I tried to put a downloaded wallpaper on my desktop and it's all blurry.. now what's odd is that it's the same file when I had windows on my computer and I could see it fine before  and the fact that all the images online and in the games seem fine... this is only happening when I put wallpapers up.. is there anyway to fix this?

3. I have an iphone and need to sync it.. is there anyway to use iTunes or another program to sync my phone  .. add music and videos, etc?

Any help you can offer is truly appreciated... thanks bunches :)

---

### Post by cariboo on 2009-04-26
How did you install java? the prefered way is to install it from the repositories, using Add/Remove Programs or Synaptic Package Manager.

I would suggest you install the ubuntu-restricted-extras meta package, this will install flash, java and most of the codecs needed to paly most types of audio/video media.

---

### Post by angie4107 on 2009-04-26
I installed java thru the add/remove programs... honestly I didn't know what I was doing and just clicked on a java program.. but it's not working.


ok.. I just followed a link from the help section for java and this is what came up:

angela@angela-desktop:~$ sudo update-java-alternatives -l
[sudo] password for angela: 
java-6-openjdk 1061 /usr/lib/jvm/java-6-openjdk
java-6-sun 63 /usr/lib/jvm/java-6-sun
angela@angela-desktop:~$ sudo update-java-alternatives -s java-6-sun
No alternatives for HtmlConverter.
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/appletviewer
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/apt
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/extcheck
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/HtmlConverter
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/idlj
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jarsigner
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jar
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javac
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javadoc
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javah
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javap
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jconsole
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jdb
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jhat
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jinfo
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jmap
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jps
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jrunscript
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jsadebugd
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstack
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstatd
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstat
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/native2ascii
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/rmic
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/schemagen
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/serialver
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/wsgen
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/wsimport
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/xjc
Using '/usr/lib/jvm/java-6-sun/jre/bin/ControlPanel' to provide 'ControlPanel'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/java' to provide 'java'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/java_vm' to provide 'java_vm'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/javaws' to provide 'javaws'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/jcontrol' to provide 'jcontrol'.
Using '/usr/lib/jvm/java-6-sun/jre/lib/jexec' to provide 'jexec'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/keytool' to provide 'keytool'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/orbd' to provide 'orbd'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/pack200' to provide 'pack200'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/policytool' to provide 'policytool'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/rmid' to provide 'rmid'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/rmiregistry' to provide 'rmiregistry'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/servertool' to provide 'servertool'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/tnameserv' to provide 'tnameserv'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/unpack200' to provide 'unpack200'.
Using '/usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so' to provide 'firefox-javaplugin.so'.
Using '/usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so' to provide 'iceape-javaplugin.so'.
Using '/usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so' to provide 'iceweasel-javaplugin.so'.
Using '/usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so' to provide 'midbrowser-javaplugin.so'.
Using '/usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so' to provide 'mozilla-javaplugin.so'.
Using '/usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so' to provide 'xulrunner-1.9-javaplugin.so'.
Using '/usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so' to provide 'xulrunner-javaplugin.so'.
angela@angela-desktop:~$ java - version
Unrecognized option: -
Could not create the Java virtual machine.
angela@angela-desktop:~$ sudo update-alternatives --config java

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*         1    /usr/lib/jvm/java-6-sun/jre/bin/java
 +        2    /usr/lib/jvm/java-6-openjdk/jre/bin/java

Press enter to keep the default
[*], or type selection number: 
angela@angela-desktop:~$ java - version
Unrecognized option: -
Could not create the Java virtual machine.
angela@angela-desktop:~$

---

### Post by angie4107 on 2009-04-26
> **cariboo907 said:**
> How did you install java? the prefered way is to install it from the repositories, using Add/Remove Programs or Synaptic Package Manager.

I would suggest you install the ubuntu-restricted-extras meta package, this will install flash, java and most of the codecs needed to paly most types of audio/video media.

I saw that one and tried to but it said: " it conflicted with some that I already had installed??"" <--- I'm assuming whatever java I already have.. but when I tried to unclick the java that I do have installed it says that it has "dependants" or something like that.. and that I'd have to use the package manager..

Thanks bunches for your help...

---

### Post by stwschool on 2009-04-26
Ok here's what I'd do.

1. Synaptic package manager. Find the java you installed, and click on the tickbox, choose "Mark For Complete Removal". Let's clean this sucker up.
2. Apply.
3. Look for ubuntu-restricted-extras and tick it. It'll sort out your java and everything else in one easy job.
4. Apply.

Wallpaper - Could you upload the picture here so we can check it out? My suspicion is that the picture is very small, and when you try using it as wallpaper it stretches, and becomes blurry.

Iphone - I don't have one myself (too poor) so can't really provide any info there sorry.

---

### Post by angie4107 on 2009-04-26
ok I completely removed the sun java 6 that I had installed ... and then installed the extras.. and still no luck with java pages working or the test thru java site to work... 

As for the wallpaper .. yes I had stretched it.. so all I need is an image that is larger? ... thanks bunches.. and ss that you couldn't help with the phone.. but I appreciate all the help so far..

---

### Post by shload on 2009-04-26
Not sure what to tell you to get java working, but if your new, it's good to have some kind of "tweaking guide".  One good place I usually start at is here...

[http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.10](http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.10)

By the end of that guide you should have all kinds of goodies such as flash, mp3, skype, etc. and though this guide is intended for 8.10 it should still work for 9.04.  of course you could wait a few more days, i'm sure howtoforge will have a new guide for 9.04 shortly.

now as far as the iphone goes...i'm in the same boat as you there.  The thing i find with it is that most people on the message boards tend to look down on the use of apple products. especially the iphone.  That said i haven't been able to find anything to sync with my phone.  

I tried getting itunes installed through wine whith no luck.  one option which did work for me was to use something like VMware or virtualbox (I prefer virtualbox).  these programs allow you to run windows within ubuntu like as though it were a native application.  install isn't overly complicated check out this guide...

[http://www.ubuntugeek.com/how-to-install-virtualbox-202-in-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/how-to-install-virtualbox-202-in-ubuntu-804-hardy-heron.html)

once you have virtualbox/windows installed you can install and use itunes.  You'll need to install the guest additions and tweak the USB but once this is done you'll have itunes and no need to dual boot.  there's a lot of good things you can use virtual box for. What I like most about it is it allows me to surf the web without a care. I can download whatever i want and test it out. and in the end if i end up with a virus i just delete my windows/virtualbox file and copy over a backup. no need for the long reinstall and ubuntu is not affected because your essentially working within a sandbox environment.  Only problem i have with it is that you can't really use it for games.

---

### Post by clive littlewood on 2009-04-26
Hi

Apple gives no help for Linux and as such both the iphone and touch will not sync with Linux/Ubuntu.

This is been worked on but currently the only way to sync is to "jailbreak" your device and then use SSH to sync.

I am waiting for 1 of the Ubuntu players (Amarok,Rythembox etc.) to crack the problem.

My next mp3 player will NOT be Apple!!!!!!!

Clive

---

### Post by alphacrucis2 on 2009-04-26
> **clive littlewood said:**
> Hi

Apple gives no help for Linux and as such both the iphone and touch will not sync with Linux/Ubuntu.

This is been worked on but currently the only way to sync is to "jailbreak" your device and then use SSH to sync.

I am waiting for 1 of the Ubuntu players (Amarok,Rythembox etc.) to crack the problem.

My next mp3 player will NOT be Apple!!!!!!!

Clive

Agreed. It's a bit ironic that Apple's OS is based on freeBSD, which is an open source version of Unix similar to Linux yet they thumb their noses at the open source community.

---

### Post by 3rdalbum on 2009-04-26
> **alphacrucis2 said:**
> Agreed. It's a bit ironic that Apple's OS is based on freeBSD, which is an open source version of Unix similar to Linux yet they thumb their noses at the open source community.

Well, Apple uses bits of FreeBSD rather than actually basing their operating system on it; but point taken. I too stay away from Apple MP3 players; they don't tend to work too well on Windows much less on Linux.

---

### Post by skompier on 2009-04-26
Another great site for new users is [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by angie4107 on 2009-04-26
Thank you all so much for the help with the iphone... I truly appreciate it.. and although I love my phone -- I agree, I'm going to look at alternatives for the next simply because I'm already loving Ubuntu much more than windows... :))

I'll take a look at the guide too.. thanks so much for all your help everyone !!!!

---

### Post by angie4107 on 2009-04-26
> **skompier said:**
> Another great site for new users is [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

[http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.10](http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.10)

Wow!! I sure wish I'd read these first... I actually did just "dive-in" though with no regrets so far.. thankfully ha ha --- I've had no major conflicts with hardware... only need to learn bunches and get used to not "synching" my phone... I'm going to see if I can use it as a "drive" ... which I actually couldn't do with iTunes and saw as a major bummer.. and never learned how to just manually choose what I like without having to build individual playlists for myself and my husband.. (just as time-consuming if not more than just drag n drop folders if you ask me) but anyhow.. I really loved both sites.. VERY educational for this newbie.. 

THANKS!!! 
Once you-buntu... there's no going back!!!

---

