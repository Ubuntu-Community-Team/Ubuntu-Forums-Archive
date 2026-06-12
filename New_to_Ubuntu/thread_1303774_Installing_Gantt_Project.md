---
title: "Installing Gantt Project"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by djftl on 2009-10-28
Hi guys,

I just downloaded the gantt project software and the instructions are as follows:

'Make sure that Sun's Java Runtime is installed on your Linux box             and  that you can run java from the command line.              Unzip the file in your home directory ($HOME) and run              $HOME/ganttproject-2.0.10/ganttproject.sh script.
                          Please note that GanttProject will not run with gij/gcj Java Runtime which comes by default with             some Linux distributions. You do need either Sun's JRE or OpenJDK.'


I verified my java version and it came out to: djftl@ubuntu:~$ java -version
java version "1.6.0_0"
OpenJDK Runtime Environment (IcedTea6 1.4.1) (6b14-1.4.1-0ubuntu11)
OpenJDK Server VM (build 14.0-b08, mixed mode)


When I ran this command: /home/djftl/Documents/ganttproject-2.0.10/ganttproject.sh
bash: /home/djftl/Documents/ganttproject-2.0.10/ganttproject.sh: Permission denied

It said permission denied.


How can I install this program as I am not sure how to now.


Your help would be much appreciated.


Regards,


Tobela

---

### Post by anewguy on 2009-10-28
You probably just need to make the shell file executable:

in your terminal window, just type:

chmod ugo+x /home/djftl/Documents/ganttproject-2.0.10/ganttproject.sh


then try again.

Dave :)

---

### Post by djftl on 2009-10-28
Thanks Dave,

I ran the command as advised:

chmod ugo+x /home/djftl/Documents/ganttproject-2.0.10/ganttproject.sh
djftl@ubuntu:~$ /home/djftl/Documents/ganttproject-2.0.10/ganttproject.sh
28 Oct 2009 11:27:40 PM org.bardsoftware.impl.eclipsito.BootImpl run
INFO: Eclipsito platform is running.
[DescriptorParser] parse(): plugin descriptor url=file:/home/djftl/Documents/ganttproject-2.0.10/plugins/net.sourceforge.ganttproject_2.0.0/plugin.xml
[DescriptorParser] parse(): plugin descriptor url=file:/home/djftl/Documents/ganttproject-2.0.10/plugins/org.ganttproject.chart.pert_2.0.0/plugin.xml
[DescriptorParser] parse(): plugin descriptor url=file:/home/djftl/Documents/ganttproject-2.0.10/plugins/org.ganttproject.impex.htmlpdf_2.0.0/plugin.xml
[DescriptorParser] parse(): plugin descriptor url=file:/home/djftl/Documents/ganttproject-2.0.10/plugins/org.ganttproject.impex.msproject_2.0.0/plugin.xml
28 Oct 2009 11:27:40 PM org.bardsoftware.impl.eclipsito.BootImpl$1 uncaughtException
WARNING: [uncaughtException]java.lang.UnsatisfiedLinkError: Can't load library: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
java.lang.UnsatisfiedLinkError: Can't load library: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1666)
    at java.lang.Runtime.load0(Runtime.java:787)
    at java.lang.System.load(System.java:1022)
    at java.lang.ClassLoader$NativeLibrary.load(Native Method)
    at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1767)
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1684)
    at java.lang.Runtime.loadLibrary0(Runtime.java:840)
    at java.lang.System.loadLibrary(System.java:1047)
    at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:67)
    at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:47)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.awt.Toolkit.loadLibraries(Toolkit.java:1614)
    at java.awt.Toolkit.<clinit>(Toolkit.java:1636)
    at java.awt.Component.<clinit>(Component.java:568)
    at net.sourceforge.ganttproject.application.MainApplication.run(MainApplication.java:34)
    at org.bardsoftware.impl.eclipsito.ApplicationLauncher.launchApplication(Unknown Source)
    at org.bardsoftware.impl.eclipsito.BootImpl$2.run(Unknown Source);

I'm not so sure what is this advising.
Do I need to install Sun Java??

Regards,

---

### Post by anewguy on 2009-10-29
I wish I could advise you more on this, but I'm not familiar with this Gantt Project.  It would appear that it can't find a library.  If you do decide to go with Sun's Java, I think I remember reading somewhere that you have to uninstall openjava first.

Dave :)

---

### Post by djftl on 2009-10-29
Ok Thanks man,
I'll uninstall open java via synaptic and install sun's java and try it again.

Cheers

---

### Post by djftl on 2009-10-29
Dave Thanks,
I uninstalled open java and installed Sun's Java, and it worked :D!!!!
Thanks!

---

### Post by anewguy on 2009-10-29
You're welcome - glad everything worked out for you!  If you don' mind, could you go to the "Thread Tools" at the top of your first post and mark the thread as solved?  That helps others who may encounter the same problem know there is a solution.


Dave :)

---

### Post by bzsolt on 2009-12-12
Hi Guys!
I tried it too and I managed to start the program but it froze while loading. Ie it never started fully.
I checked the log and found:

INFO: registering font: cmsy10
Dec 12, 2009 11:27:11 PM net.sourceforge.ganttproject.GPLogger log
INFO: reading directory=/System/Library/Fonts
Dec 12, 2009 11:27:11 PM net.sourceforge.ganttproject.GPLogger log
INFO: directory /System/Library/Fonts is not readable
Dec 12, 2009 11:27:11 PM net.sourceforge.ganttproject.GPLogger log
INFO: reading directory=/home/bzs/ganttproject-2.0.10/plugins/org.ganttproject.impex.htmlpdf_2.0.0/resource/fonts

Any idea what to do?

TIA
z

---

### Post by sebeto on 2011-10-24
Hi everybody,

[I]I tried it too and I managed to start the program but it froze while loading. Ie it never started fully.
I checked the log and found (...)[/I]

Same problem for me:
[I]INFO: reading directory=/System/Library/Fonts
Oct 24, 2011 8:38:16 PM net.sourceforge.ganttproject.GPLogger log
INFO: directory /System/Library/Fonts is not readable
Oct 24, 2011 8:38:16 PM net.sourceforge.ganttproject.GPLogger log
INFO: reading directory=/home/sebeto/Software/ganttproject-2.0.10/plugins/org.ganttproject.impex.htmlpdf_2.0.0/resource/fonts[/I]

Would anyone have any idea to solve this problem? This log is the only useful output, nothing else appears.

---

### Post by sebeto on 2011-10-24
Okay, I found the solution to my problem (and probably yours bzsolt).

I had still one last OpenJDK thing installed: openjdk-6-jre-headless...

Removing this package solved the problem...

---

### Post by oldos2er on 2011-10-24
And with that we will close.

---

