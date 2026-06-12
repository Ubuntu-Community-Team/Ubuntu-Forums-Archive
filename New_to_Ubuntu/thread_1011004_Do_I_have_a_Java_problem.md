---
title: "Do I have a Java problem??"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by n4lbl on 2008-12-14
The symptom that I am confronted with is an error message from a video, specifically: [http://radar.weather.gov/radar.php?rid=PUX&product=N0R&overlay=11101111&loop=yes](http://radar.weather.gov/radar.php?rid=PUX&product=N0R&overlay=11101111&loop=yes) and click on e.g. Base Loop.  The error message is : "Java is necessary for radar looping and is best optimized using Java version 1.4.2 or higher".  The video is not displayed.

Background:  I am running 8.10 off of a USB startup disk.  Other videos work.  If I look at Synaptic and search All for "java" I find 102 packages listed and many have the Ubuntu symbol which I think means it is installed.  I jump to the conclusion that I have java installed.  I'd guess that it must be recent enough for the error message to be misleading since I am running 8.10.  Where do I start to solve this??  How do I check what java I am running??

thanx,,,

---

### Post by taurus on 2008-12-14
Ubuntu symbol doesn't mean it is installed.  If the square box is solid, then it is installed; otherwise, you need to install it yourself.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
java -version
```

---

### Post by n4lbl on 2008-12-14
At the end of line 2 I was presented with what I think is the first page of the java license.  I don't know how to reply to continue.

---

### Post by taurus on 2008-12-14
Hit the Tab key to highlight the <OK> and then press Enter to accept it.

---

### Post by n4lbl on 2008-12-14
I restarted Firefox and all is wonderful!!  I did receive an error (below).
I presume that since the problem is solved that the error can be ignored.  Do you need more for that assessment??

again,,, thanx,,,


Errors were encountered while processing:
 linux-image-2.6.27-7-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
ubuntu@ubuntu:~$ java -version
java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) Client VM (build 11.0-b15, mixed mode, sharing)

---

### Post by kostkon on 2008-12-14
Open a terminal and give
```
sudo update-java-alternatives -s java-6-sun
```
to set the Sun Java as the default Java in your system.

---

### Post by n4lbl on 2008-12-14
Thanks very much for your help.  I've done that and everything still works!!
I tried to understand what that update did but could not.  My system did not have a man page for update.  The Update manager Manual was unable to load the correct page "The requested URI "file:///usr/share/omf/update-manager/update-manager-C.omf#" is invalid"  

My problem is solved and I really appreciate 1) the help, and 2) the very rapid help!!  I don't want to drag this out forever but do want to become a better user.  How do I lookup commands like this update command??

thanx,,,

---

### Post by albinootje on 2008-12-14
> **n4lbl said:**
> 
How do I lookup commands like this update command??


Read the manual page :
man update-alternatives

And with this :
ls -la /etc/alternatives/ | less

you can browse through those "alternatives" a bit to get an idea what's going on there.
:)

---

### Post by karlr42 on 2008-12-14
man update-java-alternatives. Basically, if you program in java, when you go to compile your code, you type javac nameOfFile, then java nameOfFile to run it. The command posted tells Ubuntu which java to use when you type javac or java- either the free version that came included, or Sun's liscensed java which you just installed.

---

### Post by n4lbl on 2008-12-14
Thanks guys for both the syntax help (I'd never have guessed ...alternatives) and for the explanation.  

Many thanks to all of you for your help.

---

