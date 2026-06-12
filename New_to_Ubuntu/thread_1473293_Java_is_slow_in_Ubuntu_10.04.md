---
title: "Java is slow in Ubuntu 10.04"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by bsyapril88 on 2010-05-05
I tried installing both sun-java6-plugin and icedtea6-plugin.

Both plugins are slow to the point of being unusable for games on pogo.com.

Is there a more reliable implementation of java?

I attempted to follow the java.com instructions to install it but the browser failed to recognize it.

Thanks for the help.

---

### Post by madjr on 2010-05-05
example of a game so i can try it out?

but usually i prefer
 
[http://www.kongregate.com/](http://www.kongregate.com/)

or
[http://www.bubblebox.com/](http://www.bubblebox.com/)


not much of a need for java

---

### Post by bsyapril88 on 2010-05-05
I'm trying to play RISK on POGO.com.

For me, it hangs on the "now loading" screen.

---

### Post by Lilonius on 2010-06-01
I am developing a graph visualization application in Java using processing graphics library. It uses force directed algorythm to layout the graph. I use eclipse. The overall animation runs slower on Ubuntu 10.04 than in XP. And my XP is loaded, it takes 5 minutes to boot completely so it can be useful.

One detail is however that i use Wubi (not alowed to mess with partitions - work notebook). But, even if it is Wubi installation, the processing power of OS should not be slower, it is only read/write from HD that shouold suffer.

Any thoughts?

---

### Post by MIJ-VI on 2010-06-24
> **madjr said:**
> example of a game so i can try it out?

but usually i prefer
 
[http://www.***************/](http://www.***************/)

or
[http://www.bubblebox.com/](http://www.bubblebox.com/)


not much of a need for java

Hi madjr.

'Thing is that [http://www.pogo.com/](http://www.pogo.com/) appears to offer a popular form of social networking via its multiplayer Java-based games.

I recently gave my neighbour (a Windows user) a [Compaq Presario SR1520NX]("http://h10025.www1.hp.com/ewfrf/wc/product?lc=en&dlc=en&cc=us&lang=en&product=471644") running Edubuntu 10.04, and with some consternation he reported back to me that he couldn't get Pogo to play any games because Java (OpenJDK) wouldn't work.

From his perspective Edubuntu fell on its face the first time he tried to use it for something he cares about. :-\

And why did this happen? Because someone on Ubuntu 10.04's development team decided to replace sun-java6 with OpenJDK Java 6 **without thoroughly testing OpenJDK first**:

[http://www.java.com/en/java_in_action/](http://www.java.com/en/java_in_action/)

Here's what I did to get games on Pogo to work on my Acer Aspire 5517-5136 running 64 bit Edubuntu 10.04 LTS:

- quit Firefox

- go to System-->Administration-->Software Sources and make sure the Partner repository is checked under third-party software.

- in Terminal run sudo apt-get update (to update the lists of software available from the Ubuntu repositories)

- in Applications-->Ubuntu Software Center remove OpenJDK Java 6 Runtime (doing so will automatically remove its other two dependencies)

- in System-->Administration-->Synaptic Package Manager check mark and install sun-java6-plugin (doing so will automatically check mark and install its required dependencies)

- reboot

- now go to pogo and try a few games to confirm that this procedure worked.

I've e-mail these instructions to my neighbour but he hasn't responded.

--------

To Ubuntu's developers:

Please make sure that everything in Ubuntu 10.10 "just works".

Thank you

Gary

---

### Post by JohnnyC35 on 2010-07-01
[MIJ-VI]("http://ubuntuforums.org/member.php?u=955375") this has fixed my issue of slow or non working apps. I haven't found Vuze to be slow since limiting how many torrents I do at a time but some Java in webpages like Facebook and Bloom wouldn't work, and now they do. Many thanks :)

---

### Post by disastrophe on 2010-07-01
Just my two cents worth as a noob. But I just wanted to point out that this isn't an issue unique to Ubuntu or any OS. Having multiple JREs laying around in winders for example can cause very similar issues and it's actually much easier to fix in Ubuntu - you don't have to clean out a couple of hundred broken registry keys afterward!:D

---

### Post by QIII on 2010-07-02
> **MIJ-VI said:**
> 
To Ubuntu's developers:

Please make sure that everything in Ubuntu 10.10 "just works".

Thank you

Gary

At the risk of sounding gruff...

To Gary:

Install the development version of Ubuntu and report bugs through Launchpad so that the developers know what is wrong and by the next Release your concerns have a chance to be addressed.

;)

This isn't an Ubuntu problem.  This is a conflict problem with Sun Java and OpenJDK (the open source version of same, which is not quite there yet.)  Neither the Ubuntu developers nor the MOTUs control the development of Sun Java and OpenJDK.

---

### Post by MIJ-VI on 2010-08-17
> **QIII said:**
> At the risk of sounding gruff...

To Gary:

Install the development version of Ubuntu and report bugs through Launchpad so that the developers know what is wrong and by the next Release your concerns have a chance to be addressed.

;)

This isn't an Ubuntu problem.  This is a conflict problem with Sun Java and OpenJDK (the open source version of same, which is not quite there yet.)  Neither the Ubuntu developers nor the MOTUs control the development of Sun Java and OpenJDK.

Fair enough. And informative too.

Last night I downloaded, md5sum'd, and tried maverick-desktop-amd64 Alpha 3 via the current version of VirtualBox (the way I always vet a new OS). In repeated tries it froze early in the boot. (However, 32 bit Ubuntu Studio 10.10 Alpha 3 did boot in VirtualBox, but still doesn't have a real time kernel.)

I lack a proper grasp of software processes to file meaningful bug reports, thus I also lack the stature to suggest to the OpenJDK development team that they further vet their efforts at:

[http://www.pogo.com/misc/sun-java/plug-in-test.jsp](http://www.pogo.com/misc/sun-java/plug-in-test.jsp) *ducks for cover*

But IME there *is* one thing that I *do* know: Ubuntu 10.04 *beat the* *biscuits* out of Windows 7 Home Premium in a month-long, dual-boot shootout on a new notebook I bought a few months ago! :D

100% Ubuntu,
Gary

---

### Post by Zeppelin! on 2010-08-28
I'm having some trouble with this guys.

I can't find the sun-java6-plugin - neither with Synaptic or Aptitude.

I actually can't find anything named sun-java6 for that matter.

I've checked in software sources every 'verse, as well as in Other Sources unsupported updates and karmic partner (should this be lucid? I don't have lucid listed there :|)

I also have the RPM.bin from Sun java themselves, but I'm having extreme trouble executing it. Basically, every time I try to run it in terminal, I end up being told the directory does not exist. Very annoying.

---

### Post by MIJ-VI on 2010-08-28
> **Zeppelin! said:**
> I'm having some trouble with this guys.

I can't find the sun-java6-plugin - neither with Synaptic or Aptitude.

I actually can't find anything named sun-java6 for that matter.

I've checked in software sources every 'verse, as well as in Other Sources unsupported updates and karmic partner (should this be lucid? I don't have lucid listed there :|)

I also have the RPM.bin from Sun java themselves, but I'm having extreme trouble executing it. Basically, every time I try to run it in terminal, I end up being told the directory does not exist. Very annoying.

All I did was to enable System-->Administration-->Software Sources-->Other Software pane: check mark http....................................partner, and then run...

Applications-->Accessories-->Terminal: [FONT=Courier New]sudo apt-get update[/FONT] and then go to...

System-->Administration-->Synaptic Package Manager and type [FONT=Courier New]sun-java6-plugin[/FONT] into the search box.

I'm typing this from one of my Ubuntu installs which is still using OpenJDK Java 6 and just checked Synaptic. The [FONT=Courier New]sun-java6-plugin[/FONT] is indeed there.

---

