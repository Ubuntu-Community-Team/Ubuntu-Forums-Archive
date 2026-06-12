---
title: "Java help needed please"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by Alex82 on 2009-03-02
hello
I cant get java to work on my machine at all.
Its an AMD turion 64X2 running Ubuntu 8.04 64 bit version
I have downloaded and installed allsorts and messed around but not having any joy with java6 or plugin for firefox 

any help would be fantastic thanks

---

### Post by konqueror7 on 2009-03-02
what do you mean by "downloaded all sorts"? there is are java packages in the repository, you can install it via synaptic or apt-get...

```
sudo apt-get install sun-java6-jre sun-java6-jdk sun-java6-plugin
```

---

### Post by Alex82 on 2009-03-02
Done that one:

alex@alex-laptop:~$ sudo apt-get install sun-java6-jre sun-java6-jdk sun-java6-plugin
[sudo] password for alex: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jre is already the newest version.
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate
alex@alex-laptop:~$

---

### Post by Alex82 on 2009-03-03
sorry,
any ideas as this is driving me nuts

---

### Post by konqueror7 on 2009-03-03
your 64bit? because i'm on 32bit, maybe that's the problem, have you tried using the IcedTea java plugin instead? 

let's wait for someone who has a similar problem...

---

### Post by Alex82 on 2009-03-03
I will give it a go now but have seen alot of people who have no success

---

### Post by pspsampsp on 2009-03-03
try clicking the refresh button in synaptic before running sudo apt-get install sun-java6-jre sun-java6-jdk sun-java6-plugin

---

### Post by konqueror7 on 2009-03-03
you might want to check [this]("https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins#Java"),

---

### Post by gandaran on 2009-03-03
theres no sun-java plugin for 64-bits systems in synaptic but you can get and download the 64-bits sun-java **bin** package from sun java.com, get the install and firefox plugin instructions there too.

---

### Post by zika on 2009-03-03
this works on 8.10 so You might make some changes: [http://ubuntuforums.org/showpost.php?p=6791349&postcount=59](http://ubuntuforums.org/showpost.php?p=6791349&postcount=59)

---

### Post by Alex82 on 2009-03-03
> **pspsampsp said:**
> try clicking the refresh button in synaptic before running sudo apt-get install sun-java6-jre sun-java6-jdk sun-java6-plugin


alex@alex-laptop:~$ sudo apt-get install sun-java6-jre sun-java6-jdk sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jre is already the newest version.
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate
alex@alex-laptop:~$

---

### Post by Alex82 on 2009-03-03
> **zika said:**
> this works on 8.10 so You might make some changes: [http://ubuntuforums.org/showpost.php?p=6791349&postcount=59](http://ubuntuforums.org/showpost.php?p=6791349&postcount=59)

followed this through and now the java plugin required has gone and the aplet starts but a blank box with no data in it loads?

---

### Post by Alex82 on 2009-03-03
Java website test returns:

Verifying Java Version
Oops! You don't have the recommended Java installed.
Your Java version is 1.6.0_0. Please click the button below to get the recommended Java for your computer.

NOTE: If you recently completed your Java software installation, you may need to restart your browser (close all browser windows and re-open) before verifying your installation.

---

### Post by Alex82 on 2009-03-04
still having no joy here I have removed icedtea and am now seeing GCJ Web Browser Plugin 0.96-pre in about:plugins

but still only get a blank applet.

Im trying to view [www.ADVFN.com](www.ADVFN.com) and look at the monitor.

my java version is
alex@alex-laptop:~$  java -version
java version "1.6.0_14-ea"
Java(TM) SE Runtime Environment (build 1.6.0_14-ea-b01)
OpenJDK 64-Bit Server VM (build 14.0-b10, mixed mode)

---

### Post by zika on 2009-03-04
did You enable Java and Java script and checked all entries in advanced (Edit->Preferences->Content)?

---

### Post by Alex82 on 2009-03-04
Yes I have all those enabled.
I have changed back to the iced tea plugin but am still loading a blank aplet on the ADVFN site.

I have changed where firefox looks for plugin in about: config and matched it to the plugin in about: plugin for both icedtea as i thought that may work but still get blank aplet
Please help as im going mad!

---

### Post by zika on 2009-03-04
what do You get if You type in terminal:```
sudo update-alternatives --display java
```

---

### Post by Alex82 on 2009-03-04
sudo update-alternatives --display java
java - status is manual.
 link currently points to /opt/jre1.6.0_14/bin/java
/usr/bin/cacao - priority 10
 slave java.1.gz: /usr/share/man/man1/cacao.1.gz
/usr/bin/gij-4.2 - priority 42
 slave java.1.gz: /usr/share/man/man1/gij-4.2.1.gz
/usr/lib/jvm/java-gcj/jre/bin/java - priority 1042
/usr/lib/jvm/java-6-sun/jre/bin/java - priority 63
 slave java.1.gz: /usr/lib/jvm/java-6-sun/jre/man/man1/java.1.gz
/opt/jre1.6.0_14/bin/java - priority 1
/usr/lib/jvm/java-1.5.0-sun/jre/bin/java - priority 53
 slave java.1.gz: /usr/lib/jvm/java-1.5.0-sun/jre/man/man1/java.1.gz
/usr/lib/jvm/java-6-openjdk/jre/bin/java - priority 1061
 slave java.1.gz: /usr/lib/jvm/java-6-openjdk/jre/man/man1/java.1.gz
Current `best' version is /usr/lib/jvm/java-6-openjdk/jre/bin/java.
alex@alex-laptop:~$

---

### Post by zika on 2009-03-04
what happens if You visit [URL="http://www.java.com/en/download/help/testvm.xml"]http://www.java.com/en/download/help/testvm.xml
[/URL]

---

### Post by Alex82 on 2009-03-04
It tells me I am using an older version of the JRE
I can see the dancing duke but he has a bar across his head for more information
Java 6 update
sun microsystems
1.6.0_0

---

### Post by zika on 2009-03-04
> **Alex82 said:**
> It tells me I am using an older version of the JRE
I can see the dancing duke but he has a bar across his head for more information
Java 6 update
sun microsystems
1.6.0_0
put the libnpjp2.so and its respective path back in FF preferences, ... You're having something else now and Your update alternatives java points to this jre. lot of stuff happened and i can not keep the track. go back to my post and try again to the letter.

---

### Post by Alex82 on 2009-03-04
ok give me ten minutes to get it all changed

---

### Post by Alex82 on 2009-03-04
Right done all that and the final message from terminal was:
Using '/opt/jre1.6.0_14/bin/java' to provide 'java'.

---

### Post by zika on 2009-03-04
does [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml) works ?

---

### Post by Alex82 on 2009-03-04
same result.

However ADVFN monitor now just continues to load aplet and never finishes

---

### Post by Alex82 on 2009-03-04
Restarted firefox and went to [www.ADVFN.com](www.ADVFN.com) then to monitor and the aplet starts and the adverts at the bottom load up but not the main part which I need?

---

### Post by presence1960 on 2009-03-04
> **Alex82 said:**
> hello
I cant get java to work on my machine at all.
Its an AMD turion 64X2 running Ubuntu 8.04 64 bit version
I have downloaded and installed allsorts and messed around but not having any joy with java6 or plugin for firefox 

any help would be fantastic thanks

Go to this link in the x86-64 bit users section of the forum : [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

click on the Sun Java 64bit beta link and download the file. Then right click the file and choose extract here. You should find a Get64bit java file. Double click it and then choose run in terminal. You will then have Java working.

Note: a lot of people post in Absolute Beginners forum about 64 bit Flash and Java problems. The proper forum is the x86-64 bit users section of the forums. If we would go there we would see there is a whole HOW TO posted in the stickys that will get Flash and Java working on 64bit platforms.

---

### Post by zika on 2009-03-04
that script is a bit outdated, there is a new version of 64-bit Java Alpha and that script uses alternative directories to store plugin. that arrangement did not work in my case and in case of numerous others. I write posts only according to arrangement that worked in my case and I emphasize that fact. I do not like when somebody do a copy and paste from a thread without even trying that recipe for himself.  for example, I like to put alternatives that doesn't come with Ubuntu official install in /opt director so i have the record of what is installed from Ubuntu repositories and what is from elsewhere. also, it is empirically proven that   ~/.mozilla/plugins and /usr/lib/mozilla/plugins are better place to put links to plugins that You want to be seen both with Epiphany, Swiftweasel and Firefox and others from that family. in my case, I use(d) this for FF2.*, FF3.0.*, FF3.1*, FF 3.2*, SwiftWeasel, Epiphany and Opera. finally post that I referred here to is in the section You propose. I do not give an advice on how to set up Java Alpha for Opera since I did not manage to make it work for myself yet ... ;)
not to get me wrong, I'm not defending anything, I'm merely explaining myself ... ;)
one thing more, the script You mention does not provide uninstall option so, once You try it and if You are not at least merely experienced You are stuck ... ;)
update: there is a remove script, sorry.

---

### Post by Alex82 on 2009-03-04
Trying this now 
here is what terminal says:
 This script is used to setup the Sun Java 64bit beta  
 and plugin b03. By entering yes below you acknowlage that
 you are installing development software and you 
 will file bug reports with Sun for every 
 problem you incounter.

 Do you agree? yes or no : 
(please type the whole word in lower case letters)yes
Java installing.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package icedtea6-plugin
--11:03:08--  [http://www.java.net/download/jdk6/6u12/promoted/b03/binaries/jre-6u12-ea-bin-b03-linux-amd64-22_dec_2008.bin](http://www.java.net/download/jdk6/6u12/promoted/b03/binaries/jre-6u12-ea-bin-b03-linux-amd64-22_dec_2008.bin)
           => `jre-6u12-ea-bin-b03-linux-amd64-22_dec_2008.bin'
Resolving [www.java.net](www.java.net)... 64.125.132.39, 64.125.132.37
Connecting to [www.java.net|64.125.132.39|:80](www.java.net|64.125.132.39|:80)... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://download.java.net/jdk6/6u12/promoted/b03/binaries/jre-6u12-ea-bin-b03-linux-amd64-22_dec_2008.bin](http://download.java.net/jdk6/6u12/promoted/b03/binaries/jre-6u12-ea-bin-b03-linux-amd64-22_dec_2008.bin) [following]
--11:03:11--  [http://download.java.net/jdk6/6u12/promoted/b03/binaries/jre-6u12-ea-bin-b03-linux-amd64-22_dec_2008.bin](http://download.java.net/jdk6/6u12/promoted/b03/binaries/jre-6u12-ea-bin-b03-linux-amd64-22_dec_2008.bin)
           => `jre-6u12-ea-bin-b03-linux-amd64-22_dec_2008.bin'
Resolving download.java.net... 72.5.124.114
Connecting to download.java.net|72.5.124.114|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 19,579,490 (19M) [application/octet-stream]

---

### Post by Alex82 on 2009-03-04
Ok A MASSIVE thanks to all who helped me here. It is finally working using the libnpjp2.so plugin had to change also in about: config.
icedtea plugin is also present but hopefully that wont have any negative effects.

Again thanks and sorry about posting in the wrong forum Im very new to this and there were so many posts I just tried to much too soon. Next task is to get a media player working!
Hopefully Ill soon be able to help others and Thanks to all again

---

### Post by presence1960 on 2009-03-04
> **zika said:**
> that script is a bit outdated, there is a new version of 64-bit Java Alpha and that script uses alternative directories to store plugin. that arrangement did not work in my case and in case of numerous others. I write posts only according to arrangement that worked in my case and I emphasize that fact. I do not like when somebody do a copy and paste from a thread without even trying that recipe for himself.  for example, I like to put alternatives that doesn't come with Ubuntu official install in /opt director so i have the record of what is installed from Ubuntu repositories and what is from elsewhere. also, it is empirically proven that   ~/.mozilla/plugins and /usr/lib/mozilla/plugins are better place to put links to plugins that You want to be seen both with Epiphany, Swiftweasel and Firefox and others from that family. in my case, I use(d) this for FF2.*, FF3.0.*, FF3.1*, FF 3.2*, SwiftWeasel, Epiphany and Opera. finally post that I referred here to is in the section You propose. I do not give an advice on how to set up Java Alpha for Opera since I did not manage to make it work for myself yet ... ;)
not to get me wrong, I'm not defending anything, I'm merely explaining myself ... ;)
one thing more, the script You mention does not provide uninstall option so, once You try it and if You are not at least merely experienced You are stuck ... ;)
update: there is a remove script, sorry.
z

---

### Post by Alex82 on 2009-03-04
hello again
after the sucess I closed firefox and went away.
now Im back and unfortunatly only have grey aplets again!
what could have hapened?

---

### Post by Therion on 2009-03-04
I only skimmed all four pages of this thread, but I didn't see any mention of simply installing the ubuntu-restricted-extras package.  Did I miss it?  

```
sudo apt-get install ubuntu-restricted-extras
```
Try that.

---

### Post by Alex82 on 2009-03-04
done that one.
after presence1960 help the java aplets worked but since shuting down and now reopening they no longer work?

---

### Post by Alex82 on 2009-03-05
ok so I have gone through all the steps again and still having no joy after only one sucessful load of aplet Im back to square 1.
what should I do now?

---

### Post by Alex82 on 2009-03-05
Right I think I know what I need to do but dont know how to do it.
every time that I install the plugin that works it appears a the top of the plugins list in firefox about: plugins and aplets load.
after a restart of the browser however it appears near the middle or bottom of list and icedtea is at the top and aplets dont work?
how do I get the correct plugin to stay at the top?
cheers

---

### Post by novafluxx on 2009-03-05
Do you want OpenJDK or Sun Java?

If you want Sun Java, check out the x64 forum, we've got a lot of good information on how to get the latest Sun Java release working!

I myself on 2 seperate systems had touble getting the Java plugin working in Firefox (every time an applet would load in FF, FF would crash), I ended up having to just REDO everything exactly the same way...no idea why, but I got it working, and I got Java added to my path, so applications like Frostwire work now!

If you need help feel free to PM me but please check out the x64 forums!

---

### Post by zika on 2009-03-05
@presence1960:
z: command not found

---

### Post by zika on 2009-03-05
> **Alex82 said:**
> Right I think I know what I need to do but dont know how to do it.
every time that I install the plugin that works it appears a the top of the plugins list in firefox about: plugins and aplets load.
after a restart of the browser however it appears near the middle or bottom of list and icedtea is at the top and aplets dont work?
how do I get the correct plugin to stay at the top?
cheers
uninstall icedtea from synaptic (complete removal). I thought that was the first thing You've done ... ;)

disclamer: that is just my opinion, it is not opinion of an expert ... ;)

---

### Post by presence1960 on 2009-03-05
> **zika said:**
> @presence1960:
z: command not found

that is because it is not a command

---

### Post by presence1960 on 2009-03-05
> **Alex82 said:**
> done that one.
after presence1960 help the java aplets worked but since shuting down and now reopening they no longer work?

Uninstall iced tea from your package manager (synaptic or adept) The instructions I gave you the link to may not be as exquisite, as new or exotic as what zika proposes- BUT you will have a working java on your rig. I look for results rather than methods.

---

### Post by presence1960 on 2009-03-05
> **novafluxx said:**
> do you want openjdk or sun java?

If you want sun java, check out the x64 forum, we've got a lot of good information on how to get the latest sun java release working!

I myself on 2 seperate systems had touble getting the java plugin working in firefox (every time an applet would load in ff, ff would crash), i ended up having to just redo everything exactly the same way...no idea why, but i got it working, and i got java added to my path, so applications like frostwire work now!

If you need help feel free to pm me but please check out the x64 forums!

[size="7"]+1[/size]

---

### Post by zika on 2009-03-05
> **presence1960 said:**
> that is because it is not a command
should I install it or is it just haiky ... ?

---

### Post by zika on 2009-03-05
> **presence1960 said:**
> Uninstall iced tea from your package manager (synaptic or adept) The instructions I gave you the link to may not be as exquisite, as new or exotic as what zika proposes- BUT you will have a working java on your rig. I look for results rather than methods.
it seems that I offended You since You have an urge to offend me. I will not get involved in such a communication so ... results were lacking so I changed methods.
**update:** I've just checked and I do not seem to find any kind of communication I had with You in this whole forum. so, I really do not see what happened. I just checked to see if I should apologize or what ... so, again, enjoy Your sarcasm alone ...

---

### Post by Alex82 on 2009-03-05
right so icedtea is compleatly removed and libgcjwebplugin.so is at the top of my about: plugin list. I change this to match in about: config. The java aplet loads briefly and then reverts back to grey.
libnpjp2.so is at the bottom of the list so I try this to....same result?

---

### Post by presence1960 on 2009-03-05
> **zika said:**
> it seems that I offended You since You have an urge to offend me. I will not get involved in such a communication so ... results were lacking so I changed methods.
**update:** I've just checked and I do not seem to find any kind of communication I had with You in this whole forum. so, I really do not see what happened. I just checked to see if I should apologize or what ... so, again, enjoy Your sarcasm alone ...

no offense, not offended You are the one who went on the rant about the script being outdated, not installed to /opt etc. etc. etc. 

The z post if you look at reason for edit : I removed my comments because restraint is a smart thing.

I know for a fact that the Alpha Java on the x86-64 bit users works just fine. I have it installed on My machine (Kubuntu 8.10 & Linux Mint5) on my daughters HP (Linux Mint 6) and on a few friends rigs with Ubuntu 8.04 and Ubuntu 8.10.

The statement I look for results rather than methods is not an insult or provocation to you. Just stating facts. Alex has had no success with the other methods suggested so I suggested what works for me. At least he got it running temporarily. I suspect that because of all the scripts and installations he ran prior he needs to remove all those other things before it will work for good.

Linux is about choice so we can both co-exist peacefully. you install Java your way, I use the method on the x86-64 bit users forum. We are both happy right?

So if I offended you I am sorry. Let's get back to the business here of helping and being helped.

---

### Post by zika on 2009-03-05
> **presence1960 said:**
> no offense, not offended You are the one who went on the rant about the script being outdated, not installed to /opt etc. etc. etc. 

by no means I dod not mean to make anything near a "rant". I'm matematician and I just always say what I think and I did not think anything bad about Your method, just, I thought, constructive suggestions that I gave my arguments (reasons) for ...

> The z post if you look at reason for edit : I removed my comments because restraint is a smart thing.sorry, I understood that completely different ... my mistake. I could not agree more about restraint. 

> I know for a fact that the Alpha Java on the x86-64 bit users works just fine. I have it installed on My machine (Kubuntu 8.10 & Linux Mint5) on my daughters HP (Linux Mint 6) and on a few friends rigs with Ubuntu 8.04 and Ubuntu 8.10.just because I had a spotless experience with it I was brave enough to give advices on about how to implement it ... 

> The statement I look for results rather than methods is not an insult or provocation to you. Just stating facts. Alex has had no success with the other methods suggested so I suggested what works for me. At least he got it running temporarily. I suspect that because of all the scripts and installations he ran prior he needs to remove all those other things before it will work for good.problem is that we do not have control of all the stuff that is happening on the machine of the guy that we are helping to. I think that he has nspluginwrapper on his disk and that fact and maybe some other stuff is making things heavier than they should have been. just because I was having great time with (both) flash and java plugin in 64 I was trying to help.

> Linux is about choice so we can both co-exist peacefully. you install Java your way, I use the method on the x86-64 bit users forum. We are both happy right?You will never see me in a discussion on Windows or such just because I live by the "live and let other live". so we are, I believe OK. 

> So if I offended you I am sorry. Let's get back to the business here of helping and being helped.peace ... :)

---

### Post by presence1960 on 2009-03-05
Alex, I have attached a file with my about:plugins from FF. I do have icedtea installed. my flash & java work fine. take a look and compare to yours.

I may be incorrect, but I suspect after running all those scripts and installations prior to trying the link I provided is the reason why it won't work permanently. You may have to remove or uninstall all those. Good Luck!

---

### Post by presence1960 on 2009-03-05
Sounds good to me zika. hoping to see you around in the forum.

---

### Post by Alex82 on 2009-03-05
IcedTeaPlugin.so      This is the plugin that works for you, I have never had this plugin, my icedtea plugin had a different name (icedtea-gcjwebplugin)

where can I get this one and how do I remove the other two cheers

libgcjwebplugin.so
libnpjp2.so           These are the two plugins I currently have for Java

---

### Post by mixtri on 2009-03-05
Alex I think you should try un-installing everything u have done including deleting all created folders in opt and wherever else.

After this, I suggest you follow Zika's instructions and it should work for you.

It successfully installed on my AMD64 bit laptop and boy! I've never seen firefox at full throttle as it is now. It flies man!

I would follow everything in his instructions barring the stuff about the _about:config_ in FF which completely threw me.

Zika you care to elaborate on what that is, as its not entirely clear to me.
-----------------------------------------------
[B]open about:config in FF
Code:[/B]

java.default_java_location_others -> /opt/jre1.6.0_14
java.java_plugin_library_name -> libnpjpj2.so
--------------------------------------------------------
Anyway As I said i did everything in the instructions apart from the bit about about:config and it seemed to work well.

After the installation i relaunched firefox and typed:
**About:plugins** in a firefox address bar it displays details of the **libnpjp2.so** file with a list of associated files underneath. This is verification that the install was successfully configured. Hope this helps.

I'd also like to use this opportunity to Thank Zika as you saved me from pulling my hairs out. :D

---

### Post by presence1960 on 2009-03-05
Alex I believe FF prompted me to install it immediately after I installed kubuntu and prior to running the other java script from the link I provided. Immediately after the OS install I go to a web page that has some commands I run. The page requires java and flash. Thats when FF prompted me to install it. I know icedtea-gcjplugin is in the repositories but I didn't use that one. As far as removing them I really don't have that answer.

---

### Post by presence1960 on 2009-03-05
> **mixtri said:**
> Alex I think you should try un-installing everything u have done including deleting all created folders in opt and wherever else.

After this, I suggest you follow Zika's instructions and it should work for you.

It successfully installed on my AMD64 bit laptop and boy! I've never seen firefox at full throttle as it is now. It flies man!

I would follow everything in his instructions barring the stuff about the _about:config_ in FF which completely threw me.

Zika you care to elaborate on what that is, as its not entirely clear to me.
-----------------------------------------------
[B]open about:config in FF
Code:[/B]

java.default_java_location_others -> /opt/jre1.6.0_14
java.java_plugin_library_name -> libnpjpj2.so
--------------------------------------------------------
Anyway As I said i did everything in the instructions apart from the bit about about:config and it seemed to work well.

After the installation i relaunched firefox and typed:
**About:plugins** in a firefox address bar it displays details of the **libnpjp2.so** file with a list of associated files underneath. This is verification that the install was successfully configured. Hope this helps.

I'd also like to use this opportunity to Thank Zika as you saved me from pulling my hairs out. :D

Alex, out of curiosity I did a clean install of my Kubuntu 8.10 64bit and tried the method zika posted here: [http://ubuntuforums.org/showpost.php?p=6791349&postcount=59](http://ubuntuforums.org/showpost.php?p=6791349&postcount=59)

It did work even the about:config instruction worked. In the about:config you just need to double click on the line for those strings and an edit box will come up. Just copy and paste the proper lines in there.

I then went to a bunch of websites and didn't really notice any visible increase in speed. But it wasn't any slower either. So the bottom line is both methods work and give a nice java experience. Maybe yours is so bogged down right now from all those scripts and installs.

P.S. I did a clean install to test it out since this is what you may need to do unless someone can tell you how to remove all those installs you tried. My daughter was mad because I hijacked her rig to make my last post while the install was running. That's the benefit of being the parent-LOL

---

### Post by Alex82 on 2009-03-05
If I do a clean install do I loose everything? or can I choose to keep some things like the package which makes my wireless work etc?

---

### Post by presence1960 on 2009-03-06
> **Alex82 said:**
> If I do a clean install do I loose everything? or can I choose to keep some things like the package which makes my wireless work etc?

A clean install is just that - "clean"! it will wipe everything. If you have a separate /home partition that won't get wiped, **_but remember to edit that partition on the partitioner and set it to the same filesystem it is now and set the mount point to /home- DO NOT CHECK the box marked format._** you do this when installing from the Live CD

---

### Post by Alex82 on 2009-03-06
hopefully I can find a way to do it without a clean install, as I have probably gone way over my download limit his month!

---

### Post by zika on 2009-03-06
> **mixtri said:**
> Zika you care to elaborate on what that is, as its not entirely clear to me.
-----------------------------------------------
[B]open about:config in FF
Code:[/B]

java.default_java_location_others -> /opt/jre1.6.0_14
java.java_plugin_library_name -> libnpjpj2.so
--------------------------------------------------------

in FF type about:config in address bar and answer "yes" when cautioned. find these two entries and change them as stated above. click on it (twice, I think) and then You will be able to change its value. as I said that is not necessary in most cases but is good to know in cases when there are problems. in Your case I think it is not necessary. 

> I'd also like to use this opportunity to Thank Zika as you saved me from pulling my hairs out. :Dglad I could be of any help.

---

### Post by zika on 2009-03-06
> **presence1960 said:**
> Alex, out of curiosity I did a clean install of my Kubuntu 8.10 64bit and tried the method zika posted here: [http://ubuntuforums.org/showpost.php?p=6791349&postcount=59](http://ubuntuforums.org/showpost.php?p=6791349&postcount=59)

It did work even the about:config instruction worked. In the about:config you just need to double click on the line for those strings and an edit box will come up. Just copy and paste the proper lines in there.

I then went to a bunch of websites and didn't really notice any visible increase in speed. But it wasn't any slower either. So the bottom line is both methods work and give a nice java experience. Maybe yours is so bogged down right now from all those scripts and installs.

P.S. I did a clean install to test it out since this is what you may need to do unless someone can tell you how to remove all those installs you tried. My daughter was mad because I hijacked her rig to make my last post while the install was running. That's the benefit of being the parent-LOL

thank You for all the trouble and effort You made. the only difference between our two methods are the places where file is stored and linked. as You said earlier, that is the beauty of Ubuntu ... :) give my best to Your daughter and my apologies for her inconvenience ... ;)

---

### Post by Alex82 on 2009-03-06
Clutching at straws now, but any ideas how to fix this without a clean install?

---

### Post by Alex82 on 2009-03-06
When I try to load the aplet Im after this is the screen that I see....
I can find the whitelist file anywhere on my computer?

---

### Post by presence1960 on 2009-03-06
> **Alex82 said:**
> When I try to load the aplet Im after this is the screen that I see....
I can find the whitelist file anywhere on my computer?

try changing the value of take the screenshot after a delay of - to 3 seconds so you can shut that window and we can then see what you are talking about. You have it set for 0 that is why the screenshot window is on top of what you want us to see. Do this and repost. I am off to work now.

---

### Post by zika on 2009-03-06
> **Alex82 said:**
> When I try to load the aplet Im after this is the screen that I see....
I can find the whitelist file anywhere on my computer?
click on Trust if you trust that site. if You are going to use that site often, click on Trust and add to whitelist. that is not the problem with java but is the security problem, You have to decide whom You trust. You can not find the whitelist on Your computer since this is the first site that should have been added to Your list ... ;)

---

### Post by zika on 2009-03-06
> Clutching at straws now, but any ideas how to fix this without a clean install?go to mozillazine site and test Your Java plugin. if it works, then You do not have java problem anymore. [http://kb.mozillazine.org/Testing_plugins](http://kb.mozillazine.org/Testing_plugins)

if problem is still there, do what is advised, uninstall icedtea, clean up the stuff You've installed beside what presence1960 and me advised and choose either one or both methods of ours and ... ;)

---

### Post by Alex82 on 2009-03-06
right I had it working for a brief time lastnight but then accidentally deleted the libnpjpj2.so plugin. Where can I get this back?

On the Java test page it said I was using a newer version of java than they had available (build 1.6.0_12) but in terminal java -version it siad i was using 
java version "1.6.0_14-ea"
Java(TM) SE Runtime Environment (build 1.6.0_14-ea-b01)
OpenJDK 64-Bit Server VM (build 14.0-b10, mixed mode)

---

### Post by zika on 2009-03-07
> **Alex82 said:**
> right I had it working for a brief time lastnight but then accidentally deleted the libnpjpj2.so plugin. Where can I get this back?

one option is to follow advice given by presence1960 [http://ubuntuforums.org/showpost.php?p=4822974&postcount=1](http://ubuntuforums.org/showpost.php?p=4822974&postcount=1)

the other option is to follow instructions I gave and follow [http://ubuntuforums.org/showpost.php?p=6791349&postcount=59](http://ubuntuforums.org/showpost.php?p=6791349&postcount=59)

it seems we are at the very beginning again.

> **Alex82 said:**
> On the Java test page it said I was using a newer version of java than they had available (build 1.6.0_12) but in terminal java -version it siad i was using 
java version "1.6.0_14-ea"
Java(TM) SE Runtime Environment (build 1.6.0_14-ea-b01)
OpenJDK 64-Bit Server VM (build 14.0-b10, mixed mode) "1.6.0_12-ea" You would get following, for example, script from [http://ubuntuforums.org/showpost.php?p=4822974&postcount=1](http://ubuntuforums.org/showpost.php?p=4822974&postcount=1).
"1.6.0_14-ea" is the one You would get following [http://ubuntuforums.org/showpost.php?p=6791349&postcount=59](http://ubuntuforums.org/showpost.php?p=6791349&postcount=59).
it still seems that You have a bunch of files from all different sources. as I said before, pick one and stick to it. in order to help us please post what gives ```
sudo updatedb
locate libnpjp2.so
```thanks to presence1960 we know that both our methods work but together, since we use different directories You get different versions of the same java plugin and its jre colliding with each other. not to mention other, like icedtea, jdk, ... according to the output of ```
java -version
sudo update-alternatives --display java
``` You gave earlier if I recall it right.

---

### Post by Alex82 on 2009-03-08
Hello sorry for the late reply had to go and work!
Firstly I now seem to have a full working Java! (1.6.0_14-ea) hopefully it will stay that way this time!
The way I got it fixed was very unorthodox and would not recomend it to anyone, I did however learn alot aong the way and become much more confident as a ubuntu user so it wasnt all bad.
Basically I had to delete as much java stuff as I had downloaded and just keep the new release, then I had to move the correct plugin manually into the right directory and reference it all in about: config and finally delete something called cacco? from synaptic.

For anyone who is interested in deleting anything that is protected you have to press alt + f2 and then type gksu nautilus into the box and run.
you can then delete and move whatever you like so I suspect this is a very dangerous method so be careful.

Finally thanks to all of you here for all of your help as I would be lost without you all and will definatly be back here if and when I get stuck in the future

---

### Post by zika on 2009-03-08
> **Alex82 said:**
> Hello sorry for the late reply had to go and work!
Firstly I now seem to have a full working Java! (1.6.0_14-ea) hopefully it will stay that way this time!
The way I got it fixed was very unorthodox and would not recomend it to anyone, I did however learn alot aong the way and become much more confident as a ubuntu user so it wasnt all bad.
Basically I had to delete as much java stuff as I had downloaded and just keep the new release, then I had to move the correct plugin manually into the right directory and reference it all in about: config and finally delete something called cacco? from synaptic.

For anyone who is interested in deleting anything that is protected you have to press alt + f2 and then type gksu nautilus into the box and run.
you can then delete and move whatever you like so I suspect this is a very dangerous method so be careful.

Finally thanks to all of you here for all of your help as I would be lost without you all and will definatly be back here if and when I get stuck in the future
I'm glad You did it. enjoy!

---

### Post by presence1960 on 2009-03-08
> **Alex82 said:**
> Hello sorry for the late reply had to go and work!
Firstly I now seem to have a full working Java! (1.6.0_14-ea) hopefully it will stay that way this time!
The way I got it fixed was very unorthodox and would not recomend it to anyone, I did however learn alot aong the way and become much more confident as a ubuntu user so it wasnt all bad.
Basically I had to delete as much java stuff as I had downloaded and just keep the new release, then I had to move the correct plugin manually into the right directory and reference it all in about: config and finally delete something called cacco? from synaptic.

For anyone who is interested in deleting anything that is protected you have to press alt + f2 and then type gksu nautilus into the box and run.
you can then delete and move whatever you like so I suspect this is a very dangerous method so be careful.

Finally thanks to all of you here for all of your help as I would be lost without you all and will definatly be back here if and when I get stuck in the future

I am glad you got it working, especially after all that work! I think it is safe to say we all learned something trying to help you, so that is a good thing. I want to thank zika, for now I know another way to install java on 64bit. It is always good to know alternate methods especially when you work on someone else's machine and run into a problem.

---

### Post by KROwen1959 on 2010-08-08
I was having Trouble with Java and Adobe, This is a fantastic site. I am new to linux and learning all over again. You all helped wonderfully. Thanks

---

