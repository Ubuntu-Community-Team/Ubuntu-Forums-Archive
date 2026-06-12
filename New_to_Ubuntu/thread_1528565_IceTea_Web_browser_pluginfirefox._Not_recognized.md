---
title: "IceTea Web browser plugin/firefox. Not recognized?"
date: 2010-07-10
forum: New to Ubuntu
---

### Post by UbuNoob001 on 2010-07-10
So a question.... 

A site I go to has a chat portion of the site, Java, which I have used in the past. I have done a fresh install of Firefox recently (from repository)since visiting the site, however...


when I go to the site, it says "additional plugins required"...I then install. After, I try and view the site and it gives the same error. At which point I view my list of plugins and it is NOT listed. However, when I try to -again- install the plugin, it says this plugin is already installed. 


 any suggestions? I am linux newbie.

---

### Post by QIII on 2010-07-10
Unfortunately, much of the world at large does not recognize OpenJDK and  IcedTea as Java.  So you get messages like that.  My bank website will  not recognize the open source Java.  I'm going to ask you to do a couple of things in the terminal, but fear not.  They are simple and not terribly dangerous.  But be sure you type carefully!

There is some debate about whether Sun Java and OpenJDK/IcedTea can  coexist happily on the same machine.  But, since OpenJDK and IcedTea can  be easily reinstalled, try uninstalling them from Synaptic.  

Edit:  Ah!  Dung.  I just looked at your info.  If you are using Karmic, the following doesn't apply, but I'll leave what I gave you here in case.

The Java available in the repositories prior to Lucid is old and has security holes.  Your website may not accept it.  You need the newest version.  This may be a bit of a chore and you'll have to use the terminal, but follow the fine instructions at the URL below.  The guy really has a good method.

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)







Alternatively, if you already have Sun Java installed, you may try to just toggle between Sun Java and OpenJDK by issuing the following in the termnal (Applications | Accessories | Terminal):

```
sudo update-java-alternatives -s java-6-sun
```You will be asked for your password.  That's the one you log in to your machine with.  Type your password, but be aware that you will not see anything, not even asterisks.  That is normal.

If you go the route of getting rid of OpenJDK and don't have Sun Java installed, read on.

You get to the Synaptic Package Manager by going to System |  Administration | Synaptic Package Manager.

Use the search feature to find OpenJDK and IcedTea and mark them for  removal.  Then click Apply.

When the changes have been made, close Synaptic.

But that may leave you with no Java at all.

Go to System | Administration | Sofware Sources.  On the "Other  Software" tab, make sure that Lucid Partner is checked (don't bother  with the one that says "Source Code" if you don't plan to do any  modifications to the source code...).

Close the form.

Since you are relatively new, I won't send you to the terminal to  install Java, which is what I would do.

Instead, go back to Synaptic.

Search for "sun-java6" (without quotes)

Select the following to install:

sun-java6-fonts, sun-java6-bin, sun-java6-jre, sun-jav6-plugin

Click apply.  When the changes are complete, close Synaptic.

It is probably still worth making sure your machine knows to use Sun Java, so go back to the terminal and issue

```
sudo update-java-alternatives -s java-6-sun
```If you use Firefox, start it.  In the navigation bar, type

```
about:plugins
```Make sure you have "Java(TM) Plug-in 1.6.0_20"

That will make everyone happy about Java no matter where you go on the  web.

If you still have trouble, we'll take a look at Flash.  But give this a  shot first.

---

### Post by UbuNoob001 on 2010-07-11
> **QIII said:**
> Unfortunately, much of the world at large does not recognize OpenJDK and  IcedTea as Java.  So you get messages like that.  My bank website will  not recognize the open source Java.  I'm going to ask you to do a couple of things in the terminal, but fear not.  They are simple and not terribly dangerous.  But be sure you type carefully! (...)
[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)(...)

That will make everyone happy about Java no matter where you go on the  web.

If you still have trouble, we'll take a look at Flash.  But give this a  shot first.

Wow QIII, thanks SO much for your help. I will report back.

---

### Post by UbuNoob001 on 2010-07-12
Hi,
  Okay so I have gone the command-line route (note that the synaptic method did not work for me as even the "lucid partner" repository didn't include anything starting with sun-java6).  So I was able to get java: 


however following the link above 
[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

Starting about half way down...
```
:~$ sudo update-alternatives --install "/usr/bin/java" "java" "/opt/java/64/jre1.6.0_20/bin/java" 1
[sudo] password for administrator: 
:~$ sudo update-alternatives --set java /opt/java/64/jre1.6.0_20/bin/java
:~$ rm ~/.mozilla/plugins/libnpjp2.so
:~$ ln -s /opt/java/64/jre1.6.0_20/lib/amd64/libnpjp2.so ~/.mozilla/plugins/
:~$ 

```

however, in firefox "about:plugins" doesnt show anything for java. 

note that ```
[SIZE=3][COLOR=#000000][COLOR=#0000FF][/COLOR][/COLOR][/SIZE]ln -s /opt/java/64/jre1.6.0_20/lib/amd64/libnpjp2.so ~/.mozilla/plugins/

``` exists and has been linked 

thanks for the help in advance!

---

### Post by gandaran on 2010-07-12
> Okay so I have gone the command-line route (note that the synaptic method did not work for me as even the "lucid partner" repository didn't include anything starting with sun-java6)
what! are you very sure there no sun-java in synaptic? did you enable the right repository? archive-canonical (lucid partner) and reloaded synaptic or run the synaptic/apt-get update command after enabling the repo.
> sudo apt-get update
if you have done it right then type sun-java in search box.
report back if still no sun-java.

---

### Post by UbuNoob001 on 2010-07-12
> **gandaran said:**
> what! are you very sure there no sun-java in synaptic? did you enable the right repository? archive-canonical (lucid partner) and reloaded synaptic or run the synaptic/apt-get update command after enabling the repo.

if you have done it right then type sun-java in search box.
report back if still no sun-java.

I must have made a mistake with Synaptic. Probably not updating it post archive addition. This method worked. Thanks!

I will mark this thread as solved as my underlying problem is solved. If you have a moment: do you notice anything wrong with my command line entries? In previous post? Thanks, just trying to learn more CLI stuff.

---

