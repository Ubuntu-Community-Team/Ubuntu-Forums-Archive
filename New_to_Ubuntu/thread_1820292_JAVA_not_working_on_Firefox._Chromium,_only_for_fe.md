---
title: "JAVA not working on Firefox. Chromium, only for few seconds on Opera"
date: 2011-08-07
forum: New to Ubuntu
---

### Post by Zerberus on 2011-08-07
Well I am unable to use JAVA in firefox and chromium! If I go on the website ukchatterbox, the website is empty in firefox and chromium, however in opera it works for a few seconds, I am able to write a couple of lines, but then absolutely nothing, and I cant use the backspace button as well!

Can anyone help?

Thanks

---

### Post by x-D on 2011-08-07
> **Zerberus said:**
> Well I am unable to use JAVA in firefox and chromium! If I go on the website ukchatterbox, the website is empty in firefox and chromium, however in opera it works for a few seconds, I am able to write a couple of lines, but then absolutely nothing, and I cant use the backspace button as well!

Can anyone help?

Thanks

Which Java Plugin are you running currently?
Have you tried other Java sites?

---

### Post by Zerberus on 2011-08-07
I have tried both javas the opensdk and the sun java, I have tried icedtea and javaplugin, and it only works in opera. but the backspace button doesnt work in opera. And after a small amount of time for java chat the panel where to enter text just doesn't enable any more text to be entered. i can read in opera but then can't write anymore

---

### Post by x-D on 2011-08-07
> **Zerberus said:**
> I have tried both javas the opensdk and the sun java, I have tried icedtea and javaplugin, and it only works in opera. but the backspace button doesnt work in opera. And after a small amount of time for java chat the panel where to enter text just doesn't enable any more text to be entered. i can read in opera but then can't write anymore

Hey, I need to know, have you tried using any other websites that require Java?

---

### Post by Zerberus on 2011-08-07
give me a website

---

### Post by x-D on 2011-08-07
> **Zerberus said:**
> give me a website

I don't know one off of the top of my head, but just try and find one, please? Actually don't worry I'll try to help you fix it anyway!

I need you to type in Java in the Package Manager and print screen that then upload the Image here, so I can see what Java packages you have installed.

---

### Post by Zerberus on 2011-08-07
I tried this website. Yes it shows 

Java Version 1.6.0_26 from Sun Microsystems Inc.


[http://javatester.org/version.html](http://javatester.org/version.html)

so its either my browsers or the website?

---

### Post by x-D on 2011-08-07
> **Zerberus said:**
> I tried this website. Yes it shows 

Java Version 1.6.0_26 from Sun Microsystems Inc.


[http://javatester.org/version.html](http://javatester.org/version.html)

so its either my browsers or the website?

Well, if that's all well and good, at least we know you have Java, and it is recognised by the Browser. Hmmmh, try and open a Website that actually properly uses Java, instead of just tests that you have it (ie a game etc)

and print screen the image of you in the ubuntu software centre, search for Java, so I can see exactly what you've gotten installed, it could be a case of conflicting plugins!

---

### Post by Zerberus on 2011-08-07
added a png

---

### Post by x-D on 2011-08-07
> **Zerberus said:**
> added a png

I'm not too familiar with Synaptic, could you go into "Ubuntu Software Centre" and do the same?

---

### Post by x-D on 2011-08-07
Something like this, would do:

>Open "Ubuntu Software Centre
>Search for "Java"
>Print-Screen this
>Upload it here

---

### Post by x-D on 2011-08-07
This is an example screenshot I just did!

---

### Post by Zerberus on 2011-08-07
yeah i dont use it cause it takes ages, just got the picture ready

---

### Post by x-D on 2011-08-07
> **Zerberus said:**
> yeah i dont use it cause it takes ages, just got the picture ready

Hey, can you do it on all installed software, because I need to know all of what you have, not just canonical's partners. Go to the Tab: Installed Software.

If you have multiple Plugins, you will need to remove some, as this is the reason, and I will tell you which to do so.

---

### Post by Zerberus on 2011-08-07
on installed overall none of the java shows up....

---

### Post by x-D on 2011-08-07
> **Zerberus said:**
> on installed overall none of the java shows up....

Try it on get software, (I should be able to see most of them), if this fails, I would really recommend doing a format and installing the newest version of Ubuntu, seeing as yours is heavily outdated anyway.

Tell me, what Java Plugins do you have installed, I mean PLUGINS, ie Firefox, Chrome, Opera Plugins, such as: Iced Tea Browser PLUGIN. I need you to tell me, and I will tell you which ones to uninstall

---

### Post by Zerberus on 2011-08-07
how so? I am using natty? and update daily.

---

### Post by x-D on 2011-08-07
> **Zerberus said:**
> how so? I am using natty? and update daily.

Haha, Sorry to my eyes that theme made it look slightly older.

Use the search for software tab and screenshot that.

The problem is either... a) too many Java Plugins, or b) the fact that you've installed Gnome 3 Shell, before it is supported in Ubuntu, you should not have done this, wait for 11.10 to do so. Uninstall Gnome 3 Shell, and then we will talk about which plugins you need to get rid of.

---

### Post by Zerberus on 2011-08-07
ok downloading a ubuntu iso just now...

---

### Post by SalHelder on 2011-08-07
For a Java test site, here's one: [http://dan-ball.jp/en/javagame/dust/](http://dan-ball.jp/en/javagame/dust/)

---

### Post by x-D on 2011-08-07
> **Zerberus said:**
> ok downloading a ubuntu iso just now...

Are you going to do a clean install. Right, once you have burned the ISO to disk and reinstalled Ubuntu 11.04, I will tell you what to do to get the right flash and Java plugins. Once I've got these setup, DO NOT INSTALL ANY MORE JAVA/FLASH PLUGINS. This will RUIN THE SYSTEM.

Do NOT install GNOME 3 SHELL. This is NOT SUPPORTED and is likely to mess the system up. If you REALLY need GNOME 3 SHELL, wait for Ubuntu 11.10 and it will be supported, which will stop all the bugs caused by it. Then upgrade to 11.10 and install GNOME 3 SHELL.

---

### Post by Zerberus on 2011-08-10
reinstalled and everything is working fine

---

