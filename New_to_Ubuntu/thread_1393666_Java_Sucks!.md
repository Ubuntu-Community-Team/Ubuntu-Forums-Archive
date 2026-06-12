---
title: "Java Sucks!"
date: 2010-01-29
forum: New to Ubuntu
---

### Post by LegendarySandwich on 2010-01-29
I use a java chat on [this site]("http://www.wiipals.net/Forum/chat.php"). I always have problems with it. First, it's very buggy in working. Sometimes it works, sometimes it doesn't, and sometimes it crashes my browser. And while it's working, the windows are sometimes erratic. Second, there's no sound, at all, even though there is sound in other programs.

How do I fix these problems?

---

### Post by Psumi on 2010-01-29
"You" do not. The developers / porters do. ;)

This is another sad tale of Flash-like adventures to be honest.

---

### Post by ratcheer on 2010-01-29
I dislike Java as much as the next guy, but it is really the greatest thing since sliced bread.

Tim

---

### Post by ovid9 on 2010-01-29
Out of curiousity, which java are you using?  The sun java for ubuntu or the umm, open source one?

From what I understand (and its very little) there are 2 java options for ubuntu currently but that ubuntu developers are leaving the sun version behind in favor of the open source one.
 
What i'm saying is this, have you tried the other java option in hopes it might be better?  I have no clue it if would or not, and I might be way off base in my understanding of java in ubuntu, but its worth a shot.

---

### Post by LegendarySandwich on 2010-01-29
> **ovid9 said:**
> Out of curiousity, which java are you using?  The sun java for ubuntu or the umm, open source one?

From what I understand (and its very little) there are 2 java options for ubuntu currently but that ubuntu developers are leaving the sun version behind in favor of the open source one.
 
What i'm saying is this, have you tried the other java option in hopes it might be better?  I have no clue it if would or not, and I might be way off base in my understanding of java in ubuntu, but its worth a shot.

I think I have both installed. But I think I was using the open-source version before, and just switched to the official version. No difference. Of course, I'm not sure if that was really what I did, and I'm open to suggestions.

> "You" do not. The developers / porters do. 

This is another sad tale of Flash-like adventures to be honest.
I've had problems with Flash too :p

---

### Post by Martin McFly on 2010-01-29
> **ratcheer said:**
> I dislike Java as much as the next guy, but it is really the greatest thing since sliced bread.

Tim

I eat loafs of bread in one piece (om nom nom).

But have to say that Java can get slow at times. However, it's one of means of multi-platformism, so it's helpful, isn't it ?

---

### Post by penguinv on 2010-01-29
> **ovid9 said:**
> Out of curiousity, which java are you using?  The sun java for ubuntu or the umm, open source one?

From what I understand (and its very little) there are 2 java options for ubuntu currently but that ubuntu developers are leaving the sun version behind in favor of the open source one.
 
What i'm saying is this, have you tried the other java option in hopes it might be better?  I have no clue it if would or not, and I might be way off base in my understanding of java in ubuntu, but its worth a shot.

link me please. OK I'll do it myself
Googleing it at first 
   [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)
which tells us " If it is not installed, JavaInstallation describes how to install some opensource flavors of Java. You may, however, have a need to run the Sun flavor of Java if something does not work correctly."
(My tongue is now experiencing the lining of my mouth, on the side, as they would have had they been you.)

JavaInstallation is       
   [https://help.ubuntu.com/community/JavaInstallation](https://help.ubuntu.com/community/JavaInstallation)
which warns us of dungeons and dangers and things to do first.
eg To install OpenJDK, you must have the Universe repository enabled and be running Ubuntu 8.04 or later.
  And then it tells how to install Sun Java even though Google quotes the page as saying
OpenJDK is the open source Java, derived from sources which ...

I was thinking about installing it from this page>
[http://java.com/en/download/manual.jsp?host=java.com&locale=en-US#lin](http://java.com/en/download/manual.jsp?host=java.com&locale=en-US#lin)
edit: oops, that is Sun Java.

In the past, I've used terminal and never got Java to be installed. Alas.

Best of luck to me and you and all.

Edit: and the things about having repositories enabled is beyond me. Yes I looked at Synaptic and Synaptic Sources and searched... And Synaptic  [https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto) help shows synaptic with base system highlighted, and it does not show what mine does.
  I think I'll go do something else.

---

### Post by wojox on 2010-01-29
What's 

```
java -version
```

Say ?

---

### Post by Thelasko on 2010-01-29
It seems that by default Java tries to access your audio hardware directly.  This doesn't work well with ALSA and Pulseaudio.  Try [this applet]("http://www.jsresources.org/apps/JSInfoApplet.html") to review and change your audio settings.

---

### Post by Georgia boy on 2010-01-29
Hi. I've been following threads regarding Java. I went to one of the sites from my company here at home and it was telling me that I need to update my Java. 
I did a terminal and got the following:

thomas@Thriller:~$ java -version
java version "1.6.0_0"
OpenJDK  Runtime Environment (build 1.6.0_0-b11)
OpenJDK Client VM (build 1.6.0_0-b11, mixed mode, sharing)
thomas@Thriller:~$ 
This any good? I do show in my applications>Internet that there is an icon of Sun also, and when I went to the package manager it shows that I have the Sun Java but it don't look like the terminal shows I do. Looks like it only shows the OpenJDK?
What is actually better for us the OpenJDK or Sun Java? From what I've been reading through the threads here Ubuntu is getting away from Sun Java and going only OpenJDK? 

Thanks

Tom

---

### Post by wojox on 2010-01-29
> **Georgia boy said:**
> Hi. I've been following threads regarding Java. I went to one of the sites from my company here at home and it was telling me that I need to update my Java. 
I did a terminal and got the following:

thomas@Thriller:~$ java -version
java version "1.6.0_0"
OpenJDK  Runtime Environment (build 1.6.0_0-b11)
OpenJDK Client VM (build 1.6.0_0-b11, mixed mode, sharing)
thomas@Thriller:~$ 
This any good? I do show in my applications>Internet that there is an icon of Sun also, and when I went to the package manager it shows that I have the Sun Java but it don't look like the terminal shows I do. Looks like it only shows the OpenJDK?
What is actually better for us the OpenJDK or Sun Java? From what I've been reading through the threads here Ubuntu is getting away from Sun Java and going only OpenJDK? 

Thanks

Tom

Try this and see if it helps:

```
sudo apt-get install sun-java6-jre sun-java6-plugin
```

---

### Post by LegendarySandwich on 2010-01-29
So how would I use the open-source Java? I have it installed and the regular Java un-installed, but I don't think it's working...

---

### Post by LegendarySandwich on 2010-01-29
Okay, now I can't even install the original Java. When I go to the software center and try to install Java, it says it needs to get updated information. But when I click update, it says the software center crashed, even though it's still there.

This fricking sucks, what should I do?

---

### Post by LegendarySandwich on 2010-01-29
> **LegendarySandwich said:**
> Okay, now I can't even install the original Java. When I go to the software center and try to install Java, it says it needs to get updated information. But when I click update, it says the software center crashed, even though it's still there.

This fricking sucks, what should I do?

By the way, I'm using Lucid Lynx...

---

### Post by LegendarySandwich on 2010-01-29
Bump. I really need this answered now...

---

### Post by yazmonium on 2010-01-29
You should download the current version directly from java.com.  Use the self-extracting file.  The instructions for the 32-bit code is [here]("http://java.com/en/download/help/5000010500.xml#selfextracting").  You may have to create some directories.  Create the directories that are listed in the instructions, but may not be on your computer.  It was pretty easy.

---

### Post by LegendarySandwich on 2010-01-29
> **yazmonium said:**
> You should download the current version directly from java.com.  Use the self-extracting file.  The instructions for the 32-bit code is [here]("http://java.com/en/download/help/5000010500.xml#selfextracting").  You may have to create some directories.  Create the directories that are listed in the instructions, but may not be on your computer.  It was pretty easy.

But how would I get it to work with Chrome?

---

### Post by yazmonium on 2010-01-29
I didn't even bother installing chrome for that very reason.  It was just released for linux a few months ago.  They'll have the bugs worked out by the summer.

---

### Post by ratcheer on 2010-01-29
> **LegendarySandwich said:**
> But how would I get it to work with Chrome?

Chrome probably has a plugins directory. Doesn't it?

Tim

---

### Post by Georgia boy on 2010-01-30
Hi. I decided to leave everything alone since it's all working. Only thing I did do was to enable the plugin for FireFox on the Sun Java. I did email someone on one of the sites though asking why they were asking for employees to use Sun Java 1.4.2_06. Told them that in my opinion they should update their java instead of me downgrading mine. I'm not about to downgrade to use one of their links and I let them know what I thought of that. Can't believe that they would still be using an older version but I guess some companies uses what works for them until they're sure their systems are okay? Oh well. If I really need to use those links I'll just try to find a system at work to do so. Not downgrading my system even if it's Open Java I'm using.
Guess if I really need to use Sun for something that the Open Java won't work on then I'll do the Sudo install for it. Otherwise the Open works just fine. According to what I've been reading that's to be default anyway in the later versions of Ubuntu right? So might as well get used to it and if have problems then try to fix.

Well, hope everyone has a wonderful weekend!!!!

Thanks everyone for all advice I've been given in this forum. Know that I've asked dumb  questions in the past but that's how I learn. Just pop me on the head like Benny Hill used to do on that old man's head. I'll get the message. :lolflag:

Thanks to all.

Tom

---

### Post by *Raz0r* on 2010-01-30
There is nothing wrong with Java in my opinion. Its close to other languages such as C#. It all depends on how the program was written. If like you say it is buggy and crashes constantly then its not the actual Java fault, but a developers who programmed it.

---

### Post by LegendarySandwich on 2010-02-01
Okay, I upgraded to Firefox 3.6...but it says no Java plugins are installed, even when they are...

---

### Post by Georgia boy on 2010-02-01
I have a question on the Open Java we have in the repros. When I did the terminal version I got:
java version "1.6.0_0"
OpenJDK Runtime Environment (build 1.6.0_0-b11)
OpenJDK Client VM (build 1.6.0_0-b11, mixed mode, sharing)

Is this the latest version for the OpenJDK? Does it get updated automatically when there are updates? Just wondering when I see that there's later versions with Sun Java.

Thanks

Tom

---

