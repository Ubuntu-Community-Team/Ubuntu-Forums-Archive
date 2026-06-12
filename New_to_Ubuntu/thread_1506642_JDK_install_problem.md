---
title: "JDK install problem"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by Kirkland14 on 2010-06-10
So I'm trying to install jdk from java and after it downloads it says to choose an application to run it with.  I have no idea what that means.  Apparently I don't have the correct "viewer" to run the program.  I'm still learning all of this stuff and don't have any idea of where to begin.  Any Help?  Thanks

Kevin

---

### Post by nhasian on 2010-06-10
by default the java in 10.04 is not from sun, its the open source java which sometimes has problems on some sites.  make sure your using sun's java instead.

```
sudo apt-get install sun-java6-jre sun-java6-plugin
```


you can list the different javas on your computer with the command:

```
sudo update-java-alternatives -l
```

if necessary you can set it to sun's java with the command:

```
sudo update-java-alternatives -s java-6-sun
```

now run *java -version* to ensure that the correct version is being called.

---

### Post by tango_ninja on 2010-06-10
> **Kirkland14 said:**
> So I'm trying to install jdk from java and after it downloads it says to choose an application to run it with.  I have no idea what that means.  Apparently I don't have the correct "viewer" to run the program.  I'm still learning all of this stuff and don't have any idea of where to begin.  Any Help?  Thanks

Kevin

Hi Kevin, are you trying to install the JRE (java runtime environment) or the JDK (java development kit)?  JRE is for users who want to browse the java-enabled websites on the internet, while JDK is for Java programmers.

It sounds like you may be trying to download the java package(s) from the java website.  Don't do this.  Instead, open a terminal window (Applications > Accessories > Terminal) and enter

```
sudo apt-get install sun-java6-fonts sun-java6-jre sun-java6-plugin
```

It's kind of funny... i _just_ finished writing a quick tutorial on installing java.  You can [view it here]("http://justplainobvious.blogspot.com/2010/06/how-to-install-java-jre-in-ubuntu-linux.html").

---

### Post by Kirkland14 on 2010-06-10
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jre is already the newest version.
sun-java6-jre set to manually installed.
The following NEW packages will be installed:
  sun-java6-plugin
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,850B of archives.
After this operation, 61.4kB of additional disk space will be used.
Get:1 http://archive.canonical.com/ubuntu/ lucid/partner sun-java6-plugin 6.20dlj-1ubuntu3 [1,850B]
Fetched 1,850B in 0s (4,612B/s)           
Selecting previously deselected package sun-java6-plugin.
(Reading database ... 182313 files and directories currently installed.)
Unpacking sun-java6-plugin (from .../sun-java6-plugin_6.20dlj-1ubuntu3_amd64.deb) ...
Setting up sun-java6-plugin (6.20dlj-1ubuntu3) ..
```So this is what I got.  But for the life of me I still can't find development kit anywhere.  whenn i search for files it show this:

---

### Post by tom.swartz07 on 2010-06-10
> **nhasian said:**
> by default the java in 10.04 is not from sun, its the open source java which sometimes has problems on some sites.  make sure your using sun's java instead.

```
sudo apt-get install sun-java6-jre sun-java6-plugin
```


you can list the different javas on your computer with the command:

```
sudo update-java-alternatives -l
```

if necessary you can set it to sun's java with the command:

```
sudo update-java-alternatives -s java-6-sun
```

now run *java -version* to ensure that the correct version is being called.

Not to be nit-picky, but you forgot to add the partner repo. In 10.04, Java became an Ubuntu Parter, thus it must be enabled in the repos before you could get the official version, rather than the Open Source Edition.

```
sudo add-apt-repository &#8220;deb http://archive.canonical.com/ lucid partner&#8221;
```
```
sudo apt-get update
```
```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts sun-java6-jdk
```

The files could then be run from the terminal ```
java -jar FILENAME.jar
```
or you could right click on them and say "Open with Java" (or something to that effect)

---

### Post by tango_ninja on 2010-06-10
> **Kirkland14 said:**
> ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jre is already the newest version.
sun-java6-jre set to manually installed.
The following NEW packages will be installed:
  sun-java6-plugin
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,850B of archives.
After this operation, 61.4kB of additional disk space will be used.
Get:1 http://archive.canonical.com/ubuntu/ lucid/partner sun-java6-plugin 6.20dlj-1ubuntu3 [1,850B]
Fetched 1,850B in 0s (4,612B/s)           
Selecting previously deselected package sun-java6-plugin.
(Reading database ... 182313 files and directories currently installed.)
Unpacking sun-java6-plugin (from .../sun-java6-plugin_6.20dlj-1ubuntu3_amd64.deb) ...
Setting up sun-java6-plugin (6.20dlj-1ubuntu3) ..
```So this is what I got.  But for the life of me I still can't find development kit anywhere.  whenn i search for files it show this:

I think we assumed you were only looking for the JRE. If you want the JDK you must also run:

```
sudo apt-get install sun-java6-jdk
```

I'm not a java developer... but from what I understand you will also need to made some additional changes to code in java.  [See this link]("http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/").

---

### Post by Soul-Sing on 2010-06-10
> **tom.swartz07 said:**
> Not to be nit-picky, but you forgot to add the partner repo. In 10.04, Java became an Ubuntu Parter, thus it must be enabled in the repos before you could get the official version, rather than the Open Source Edition.

```
sudo add-apt-repository “deb http://archive.canonical.com/ lucid partner”
```
```
sudo apt-get update
```
```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts sun-java6-jdk
```

The files could then be run from the terminal ```
java -jar FILENAME.jar
```
or you could right click on them and say "Open with Java" (or something to that effect)

> Get:1 [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner sun-java6-plugin 6.20dlj-1ubuntu3 [1,850B]
Fetched 1,850B in 0s (4,612B/s)  

seems to be enabled...

---

### Post by Soul-Sing on 2010-06-10
but why [COLOR="Red"]sun[/COLOR] java?

---

### Post by jswitzer on 2010-06-10
I think that the .bin file you were trying to run is just a binary executable file. 
To run it, you would 
1) open up a terminal, 
2) cd to the directory that it's in, 
3) chmod a+x name_of_file.bin 
and then 
4) ./name_of_file.bin

(Item 3 adds executable privileges to the file)

That being said, you should just install from the repository and forget about the .bin.

---

### Post by QIII on 2010-06-10
> **leoquant said:**
> but why [COLOR=Red]sun[/COLOR] java?

My clients specify it and my bank website won't work with OpenJDK.

Still, it is to be hoped that at some point OpenJDK will be fully complete and compatible and that everyone who uses Sun Java on their websites or clients who want Java apps will be OK with that.

I'm all for open source!

---

### Post by Kirkland14 on 2010-06-10
> sudo add-apt-repository “deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner”
I get this message:

```
Error: need a repository as argument
```Am I doing something wrong somehow?  I know this pretty remedial stuff.  Still Learning.

thanks for the input

Kevin

---

### Post by tango_ninja on 2010-06-10
> **Kirkland14 said:**
> I get this message:

```
Error: need a repository as argument
```Am I doing something wrong somehow?  I know this pretty remedial stuff.  Still Learning.

thanks for the input

Kevin

Try again with single quotation marks:

```
sudo add-apt-repository 'deb http://archive.canonical.com/ubuntu lucid partner'
```

Alternatively, you can add the line **deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner** to your etc/apt/sources.list file  ([see here]("https://help.ubuntu.com/community/Repositories/CommandLine") for a lot more info)

```
sudo gedit /etc/apt/sources.list
```

---

### Post by tango_ninja on 2010-06-10
Kevin, from the output you provided in past posts it looks like that repo is already enabled.  Are you having trouble downloading the jdk package?

---

### Post by Kirkland14 on 2010-06-10
I downloaded it but could not get it to open after that. I was told to choose an application to open it with but I'm unsure of what application it would like me to use. I also can't seem to locate under anything in the accesories menu. Thanks

Kevin

---

### Post by Kirkland14 on 2010-06-10
So I went to look at the page about repositories.  When I typed:

```

/etc/apt/sources.list
```I got:

```
bash: /etc/apt/sources.list: Permission denied
```Why would I be denied access to my own system?

---

### Post by tom.swartz07 on 2010-06-10
> **Kirkland14 said:**
> So I went to look at the page about repositories.  When I typed:

```

/etc/apt/sources.list
```I got:

```
bash: /etc/apt/sources.list: Permission denied
```Why would I be denied access to my own system?

You as a user are denied permission to edit system specific files. Its just a security measure.

Use this instead from the terminal:```
gksudo gedit /etc/apt/sources.list
``` and you could save it.

---

### Post by Kirkland14 on 2010-06-10
> Hi Kevin, are you trying to install the JRE (java runtime environment)  or the JDK (java development kit)?  JRE is for users who want to browse  the java-enabled websites on the internet, while JDK is for Java  programmers.I want the JDK.  I already have the JRE.  I just wanted to play around with learning how to write code.  I thought it might be an easy way to learn but apparently I can't even figure how to open the program.

So I got into the source code and everything that should be unhashed seems to be except for these two:

```
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
```

Should these be unhashed?

---

### Post by QIII on 2010-06-11
Did you install the JRE through Synaptic?

Do you have the Lucid Partner repository checked in  System | Software Sources under the "Other Software" tab?

Use the GUI to activate the Lucid Partner repository if you have not.  When your sources are updated, close it.

Open Synaptic.

Search for and install the sun-java6 packages (one of them is the jdk).

Go to the terminal and type

```
sudo update-java-alternatives -s java-6-sun
```

That will make sure you are using Sun Java rather than OpenJDK.

To check to see that you have the latest Java installed, issue the following in the terminal:

```
java -version
```

You should be looking for Update 20.

---

### Post by Kirkland14 on 2010-06-11
> To check to see that you have the latest Java installed, issue the  following in the terminal:

     Code:
     java -version 
You should be looking for Update 20.I had already installed the JDK in the other sources box but just reinstalled it. I got this in the terminal so I know JDK has to be around here somewhere. 

```
java version "1.6.0_20"
Java(TM) SE Runtime Environment (build 1.6.0_20-b02)
Java HotSpot(TM) 64-Bit Server VM (build 16.3-b01, mixed mode)
```Thanks for everyones help on this.  It's always a blast being the noob.

Kevin

---

### Post by tango_ninja on 2010-06-11
> **Kirkland14 said:**
> I want the JDK.  I already have the JRE.  I just wanted to play around with learning how to write code.  I thought it might be an easy way to learn but apparently I can't even figure how to open the program.

So I got into the source code and everything that should be unhashed seems to be except for these two:

```
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
```

Should these be unhashed?


I'm going to make a bunch of assumptions in this post, so please don't take it the wrong way if I've interpreted your progress incorrectly....

I think that there may be some confusion about this whole process... from what I can understand, you're looking for a program in which you can type code, play around with programming and try to learn java.  You think that this program is the JDK and that you still need to install it.  That's incorrect, as far as I can see.

**_Question #1_: What happens when you run the following code in terminal?  Please post the output.**

```
sudo apt-get install sun-java6-jdk

```
I suspect you'll get something like this:

```
sun-java6-jdk is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

If your output resembles the text immediately above, JDK is already installed.

With JDK installed, you will be able to compile java text into a program and then run that program.  This can be done with the help of a text editor (**gedit** will do nicely).  Please review this short tutorial on beginning to program java in linux ([http://java.sun.com/docs/books/tutorial/getStarted/cupojava/unix.html](http://java.sun.com/docs/books/tutorial/getStarted/cupojava/unix.html)).  **Note: this tutorial uses pico as a text editor.  You should use gedit.  Just substitute "gedit" every time they refer to "pico."**

Lastly, it sounds like you're looking for a complete IDE (integrated development environment).  You might try **eclipse** ([see screenshot here]("http://www.yolinux.com/TUTORIALS/images/JavaIDE-Eclipse_FullSizeImage.gif")).  I've heard it's good.... I've never used it.  I recommend sticking with the gedit + terminal method above, but if you really want the IDE you can get it via:

```
sudo apt-get install eclipse

```
and launch via:

```
eclipse
```

Again, I made a bunch of assumptions based upon the thread progress thus far.  Hope I'm on the right track and apologies in case I've misinterpreted.

---

### Post by Kirkland14 on 2010-06-11
@Tango

You are absolutely correct in all of the above.  I see how the puzzle is pieced together now.  Thanks for all the help. And to everyone else who participated in my novice questions.

Kevin

---

