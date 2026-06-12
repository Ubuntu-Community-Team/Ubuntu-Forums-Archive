---
title: "Java plugin version - who do I believe?"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by litlfrog on 2009-03-11
If I go to the Java website and click "Do I have Java?", it says that I'm using version 6, update 10. If I run 
> sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin


then I get

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-bin is already the newest version.
sun-java6-jre is already the newest version.
sun-java6-plugin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


So which is it? Am I running the most current version or not? I especially need to know whether I'm running the most current version of the plugin for Firefox 3.0.7, because I'm trying to troubleshoot a problematic web app that uses Java, and I need to know whether my display problem would be fixed by a Java update.

---

### Post by kanikilu on 2009-03-11
Have you checked ```
about:plugins
``` in Firefox to see which version it's using? Put that in the address bar - I only put it in code tags so the forum wouldn't render a :p instead of : p (without the space).

---

### Post by gandaran on 2009-03-11
> **litlfrog said:**
> If I go to the Java website and click "Do I have Java?", it says that I'm using version 6, update 10. If I run 


then I get



So which is it? Am I running the most current version or not? I especially need to know whether I'm running the most current version of the plugin for Firefox 3.0.7, because I'm trying to troubleshoot a problematic web app that uses Java, and I need to know whether my display problem would be fixed by a Java update.
you are running the version available in synaptic (sun-java6 update 10) if you want the latest release (java6 update 14) get the sun-java  bin package from sunjava .com and install it.

---

### Post by litlfrog on 2009-03-11
There doesn't to appear to be a domain called sunjava.com. I downloaded the latest version from [www.java.com](www.java.com), which is update 12, and installed it from the command line. So why is Firefox still showing update 10?

---

### Post by gandaran on 2009-03-11
> **litlfrog said:**
> There doesn't to appear to be a domain called sunjava.com. I downloaded the latest version from [www.java.com](www.java.com), which is update 12, and installed it from the command line. So why is Firefox still showing update 10?
because you haven't removed the update 10 package, it's still there, look up sun-java6-plugin, jre and bin packages in synaptic and mark for complete removal, click the apply button.

---

### Post by gandaran on 2009-03-11
> **litlfrog said:**
> There doesn't to appear to be a domain called sunjava.com. I downloaded the latest version from [www.java.com](www.java.com), which is update 12, and installed it from the command line. So why is Firefox still showing update 10?
sorry, it's [http://java.sun.com/](http://java.sun.com/) not sunjava and you are right the latest is update 12

---

### Post by litlfrog on 2009-03-11
Whoa, if I mark sun-java6-bin for complete removal, it wants to uninstall Open Office. Is there a way around that?

---

### Post by litlfrog on 2009-03-12
All right, let me phrase the question another way. If I do a complete removal of sun-java6-bin but then want to *reinstall* OpenOffice, will that reinstallation overwrite the newer version of Java that I got off the Java website?

---

### Post by gandaran on 2009-03-12
> **litlfrog said:**
> All right, let me phrase the question another way. If I do a complete removal of sun-java6-bin but then want to *reinstall* OpenOffice, will that reinstallation overwrite the newer version of Java that I got off the Java website?
the answer is no, it won't overwrite anything, anyway you can always do a reinstall of java!  
now I don't know why it's asking to remove openoffice, this shouldn't be happening, java is not a dependency of open office, you must have done something. 
try removing by command line **sudo apt-get remove sun-java6-bin**

---

### Post by litlfrog on 2009-03-12
OK, I removed sun-java6-bin. When I was done, no Java plugins are showing up under about:plugins. Reinstalled the file I downloaded from java.com, still no plugins, and now my browser's acting up because half the pages on the damn web use Java. How do I fix this? Java support really is one of those areas where Windows has Linux beat--it's frustrating to not be able to click on a button and go.

Oh, and removing sun-java6-bin also got rid of some fonts that my browser uses.

---

### Post by philinux on 2009-03-12
See what you got installed then by using this.

```
sudo update-alternatives --config java

```
It will show you what is currently the default and what alternatives there are. This command can be run again to revert back.

---

### Post by zika on 2009-03-12
> **litlfrog said:**
> OK, I removed sun-java6-bin. When I was done, no Java plugins are showing up under about:plugins. Reinstalled the file I downloaded from java.com, still no plugins, and now my browser's acting up because half the pages on the damn web use Java. How do I fix this? Java support really is one of those areas where Windows has Linux beat--it's frustrating to not be able to click on a button and go.

Oh, and removing sun-java6-bin also got rid of some fonts that my browser uses.
You might find some answers to Your questions in:[http://ubuntuforums.org/showpost.php?p=6791349&postcount=59](http://ubuntuforums.org/showpost.php?p=6791349&postcount=59)

---

### Post by litlfrog on 2009-03-12
> **philinux said:**
> See what you got installed then by using this.

```
sudo update-alternatives --config java

```
It will show you what is currently the default and what alternatives there are. This command can be run again to revert back.

I get "No alternatives for Java."

---

### Post by philinux on 2009-03-12
> **litlfrog said:**
> I get "No alternatives for Java."

Thats ok then i would reinstall sun-java6-bin and hopefully java is working again.

---

### Post by litlfrog on 2009-03-12
> **zika said:**
> You might find some answers to Your questions in:[http://ubuntuforums.org/showpost.php?p=6791349&postcount=59](http://ubuntuforums.org/showpost.php?p=6791349&postcount=59)

I'm sorry, but a) those commands are for 64-bit systems and b) I seriously don't understand what they're doing. I saw a java plugin install as part of the package I downloaded; why is Firefox not using, or even SEEING, that plugin after I restart the computer? And is there a way to get OpenOffice installed without the older version of Java? I need to run OpenOffice on this system. I've tried AbiWord, but it's very slow and highlighting text makes it unreadable.

---

### Post by gandaran on 2009-03-12
> **litlfrog said:**
> OK, I removed sun-java6-bin. When I was done, no Java plugins are showing up under about:plugins. Reinstalled the file I downloaded from java.com, still no plugins, and now my browser's acting up because half the pages on the damn web use Java. How do I fix this? Java support really is one of those areas where Windows has Linux beat--it's frustrating to not be able to click on a button and go.

Oh, and removing sun-java6-bin also got rid of some fonts that my browser uses.
the sun-java package you installed does not include a firefox plugin, you have to make a system link to java to work in firefox, go back to java.com, look up the installing instructions for firefox.

---

### Post by litlfrog on 2009-03-12
> **philinux said:**
> Thats ok then i would reinstall sun-java6-bin and hopefully java is working again.

:( But that's my whole problem! It was installed successfully before, but the installed package apparently doesn't include the latest version of the plugin. That's what I'm trying to accomplish here: to have a working version of Java, the latest version of the plugin to test a web app, and Open Office all installed and working properly.

---

### Post by gandaran on 2009-03-12
> **litlfrog said:**
> :( But that's my whole problem! It was installed successfully before, but the installed package apparently doesn't include the latest version of the plugin. That's what I'm trying to accomplish here: to have a working version of Java, the latest version of the plugin to test a web app, and Open Office all installed and working properly.
you can still have the sun-java6-bin and jre installed but don't install the sun-java6-plugin, for firefox make that system link to the other java package, now you'll have the latest update 12 working in firefox!

---

### Post by philinux on 2009-03-12
> **litlfrog said:**
> :( But that's my whole problem! It was installed successfully before, but the installed package apparently doesn't include the latest version of the plugin. That's what I'm trying to accomplish here: to have a working version of Java, the latest version of the plugin to test a web app, and Open Office all installed and working properly.

Ok , is this 64 or 32 bit ubuntu you running?

---

### Post by litlfrog on 2009-03-12
It's 32-bit. I've reinstalled sun-java6-bin, -jre, and -fonts. I presume that the newer version of the java plugin is on my system somewhere since I haven't uninstalled it, but Firefox has no clue that it's there. There's no mention of Java in about : plugins.

---

### Post by philinux on 2009-03-12
You'll have to close FF and restart it for it to pick it up.

---

### Post by gandaran on 2009-03-12
> **litlfrog said:**
> It's 32-bit. I've reinstalled sun-java6-bin, -jre, and -fonts. I presume that the newer version of the java plugin is on my system somewhere since I haven't uninstalled it, but Firefox has no clue that it's there. There's no mention of Java in about : plugins.
what *newer version of the java plugin*? the package from java.com does not include a plugin, you have to make the system link for firefox!
[http://java.sun.com/javase/6/webnotes/install/jre/manual-plugin-install-linux.html](http://java.sun.com/javase/6/webnotes/install/jre/manual-plugin-install-linux.html)

---

### Post by litlfrog on 2009-03-12
*deep breath* OK, maybe I'm using the wrong terminology here. I installed sun-java6-bin from the command line. When I go to the Java webpage, it says that I don't have the most current version installed--I've got Java 6, update 10. I download a package directly from Java's website. I install THAT package from the command line--it supposedly contains Java 6, update 12. When I return to the Java webpage, it still says that I've got update 10. Maybe the java plugin versions are the same, I don't know.

---

### Post by philinux on 2009-03-12
> **litlfrog said:**
> *deep breath* OK, maybe I'm using the wrong terminology here. I installed sun-java6-bin from the command line. When I go to the Java webpage, it says that I don't have the most current version installed--I've got Java 6, update 10. I download a package directly from Java's website. I install THAT package from the command line--it supposedly contains Java 6, update 12. When I return to the Java webpage, it still says that I've got update 10. Maybe the java plugin versions are the same, I don't know.

Can you post your installation method?

---

### Post by gandaran on 2009-03-12
> Maybe the java plugin versions are the same, I don't know
no they are not, if the update 10 is showing up in firefox it's because you have the sun-java6-plugin from synaptic installed.
did you try this for the other package [http://java.sun.com/javase/6/webnotes/install/jre/manual-plugin-install-linux.html](http://java.sun.com/javase/6/webnotes/install/jre/manual-plugin-install-linux.html)

---

### Post by litlfrog on 2009-03-12
First, I did

> sudo apt-get remove sun-java6-bin

Then I navigated to the directory where I downloaded the file from the Java website and ran 

> sudo ./jre-6u12-linux-i586.bin

I didn't see any error messages, but something must have gone wrong. When I installed that version, it didn't install any plugins and I was missing fonts. I went back to a terminal window and ran

> sudo apt-get install sun-java6-fonts

and

[QUOTE]sudo apt-get install sun-java6-plugin/QUOTE]

When I went to about:plugins, it still didn't list any plugins installed. When I went to Java's webpage, it prompted me to install a plugin through a pop-up window. I did so, but about:plugins *again* lists the version as update 10.

---

### Post by litlfrog on 2009-03-12
> **gandaran said:**
> no they are not, if the update 10 is showing up in firefox it's because you have the sun-java6-plugin from synaptic installed.
did you try this for the other package [http://java.sun.com/javase/6/webnotes/install/jre/manual-plugin-install-linux.html](http://java.sun.com/javase/6/webnotes/install/jre/manual-plugin-install-linux.html)

No gandaran, I did not try that method yet. I don't know where to find the old version of the Java plugin in the filesystem. What's more, the instructions for Firefox make no sense to me: what's a "symbolic link" to the plugin? How the heck do I know which version to choose between ns7 and ns7-gcc29 if it depends on "whether Firefox was compiled with gcc2.9"?

---

### Post by philinux on 2009-03-12
If you have to have the latest version then you need to remove any synaptic versions and then follow these instructions.

[http://www.java.com/en/download/help/5000010500.xml](http://www.java.com/en/download/help/5000010500.xml)

Make sure you follow the 32 bit version.

---

### Post by detroit/zero on 2009-03-12
I followed the instruction at the Java website to the letter, and I can't make the plugin work either.

When I check about: plugins, nothing at all is listed for Java. When I try the "verify your install" button (or visit any page with Java content) I get the "Install missing plugins" dialog which, of course, dead-ends with me downloading the outdated version from the repos, or going back and trying to follow the instructions again with the same result.

I'd say me & OP are in the same boat on this one.

There's an .rpm available... hasn't anybody bothered to slap together a .deb? I've been fighting Java since Gutsy... there has to be a better/more-ubuntu-specific way to get java working and keep it up-to-date. The version I had was the hardy-repo 1.6-u7

What good is that?

---

### Post by philinux on 2009-03-12
I'm on 64 bit so things is a bit different. but you both need to find out where the plugin got installed to. Maybe it's a symlink problem.

```
sudo updatedb

```
then

```
locate libjavaplugin_oji.so

```
Hope I got the right file name for 32 bit.

---

### Post by fooman on 2009-03-12
> **zika said:**
> You might find some answers to Your questions in:[http://ubuntuforums.org/showpost.php?p=6791349&postcount=59](http://ubuntuforums.org/showpost.php?p=6791349&postcount=59)

hey zika,  that works great on my intrepid 64bit! ...loads much faster then whatever i had on there previously.  :)

thanks

---

### Post by litlfrog on 2009-03-12
Problem fixed! Thanks folks. I followed the instructions on the Java page linked and everything works now. When I initially downloaded the file, that page had not included the configuration info I needed for Firefox. Whew, that was pretty involved. Thanks again all.

---

### Post by philinux on 2009-03-12
Job done then :P.

---

### Post by detroit/zero on 2009-03-12
> **philinux said:**
> I'm on 64 bit so things is a bit different. but you both need to find out where the plugin got installed to. Maybe it's a symlink problem.

```
sudo updatedb

```then

```
locate libjavaplugin_oji.so

```Hope I got the right file name for 32 bit.I can't speak for OP, but for me, the plugin installs right where the instructions say it installs. The commands you recommend confirm it.

This is a little long, and I'll edit out the worst of it, but here's my whole install process step-by-step```
root@zero-laptop:/home/zero# mkdir /usr/java
root@zero-laptop:/home/zero# cp Incoming*/jre* /usr/java
root@zero-laptop:/home/zero# cd /usr/java
root@zero-laptop:/usr/java# ls
jre-6u12-linux-i586.bin
root@zero-laptop:/usr/java# chmod a+x jre*
root@zero-laptop:/usr/java# ./jre*

[REMOVED SUN-JAVA EULA]

Do you agree to the above license terms? [yes or no]
y
Unpacking...
Checksumming...
Extracting...
UnZipSFX 5.50 of 17 February 2002, by Info-ZIP (Zip-Bugs@lists.wku.edu).

[REMOVED 20 PAGES OF TERMINAL OUTPUT]
 
Done.
root@zero-laptop:/usr/java/jre1.6.0_12/plugin/i386# cd /usr/lib/firefox/plugins
root@zero-laptop:/usr/lib/firefox/plugins# ls
flashplugin-alternative.so  mplayerplug-in-qt.xpt  mplayerplug-in-wmp.so
mplayerplug-in-dvx.so       mplayerplug-in-rm.so   mplayerplug-in-wmp.xpt
mplayerplug-in-dvx.xpt      mplayerplug-in-rm.xpt  mplayerplug-in.xpt
mplayerplug-in-qt.so        mplayerplug-in.so
root@zero-laptop:/usr/lib/firefox/plugins# ls /usr/java/jre1.6.0_12/plugin/i386/ns7
libjavaplugin_oji.so
root@zero-laptop:/usr/lib/firefox/plugins# updatedb
root@zero-laptop:/usr/lib/firefox/plugins# locate libjavaplugin_oji.so
/usr/java/jre1.6.0_12/plugin/i386/ns7/libjavaplugin_oji.so
/usr/java/jre1.6.0_12/plugin/i386/ns7-gcc29/libjavaplugin_oji.so
root@zero-laptop:/usr/lib/firefox/plugins# ln -s /usr/java/jre1.6.0_12/plugin/i386/ns7/libjavaplugin_oji.so
root@zero-laptop:/usr/lib/firefox/plugins# cd ../extensions
root@zero-laptop:/usr/lib/firefox/extensions# unzip /usr/java/jre*/lib/deploy/ffjcext.zip
Archive:  /usr/java/jre1.6.0_12/lib/deploy/ffjcext.zip
```Everything looks like it worked, and yet when I load Firefox and check about: plugins, I get nothing to do with Java.

> **litlfrog said:**
> Problem fixed! Thanks folks. I followed the instructions on the Java page linked and everything works now. When I initially downloaded the file, that page had not included the configuration info I needed for Firefox. Whew, that was pretty involved. Thanks again all.
Care to enlighten me? I've been following those same instructions and I'm hung up where you were.

Which part did I miss?

---

### Post by zika on 2009-03-12
> **litlfrog said:**
> I'm sorry, but a) those commands are for 64-bit systems and b) I seriously don't understand what they're doing. I saw a java plugin install as part of the package I downloaded; why is Firefox not using, or even SEEING, that plugin after I restart the computer? And is there a way to get OpenOffice installed without the older version of Java? I need to run OpenOffice on this system. I've tried AbiWord, but it's very slow and highlighting text makes it unreadable.
sorry, but a)You did not mention that You have 32-bit and I assumed (my mistake) and b)I can explain but I think is is irrelevant now ... ;) glad to see that You resolved Your problem.

---

### Post by zika on 2009-03-12
> **fooman said:**
> hey zika,  that works great on my intrepid 64bit! ...loads much faster then whatever i had on there previously.  :)

thanks
I'm telling You ... ;)

---

### Post by litlfrog on 2009-03-12
Do you have a directory for usr/lib/firefox-3.0.7? I created the shortcut in the plugins directory there and in firefox, because I wasn't sure which one was correct.

---

### Post by detroit/zero on 2009-03-12
> **litlfrog said:**
> Do you have a directory for usr/lib/firefox-3.0.7? I created the shortcut in the plugins directory there and in firefox, because I wasn't sure which one was correct.
Well, don't I feel stupid. That went right by me!

Once I changed into the 3.0.7 dir and re-linked from that plugins folder, everything works.

Thanks for the pointer.. That's two solved in one thread:popcorn:

---

### Post by josefski on 2009-04-12
BAM! Been fiddling with this one for weeks now. So, if you wish to manually install the latest Java, do this: 

Remove previous version of java, and then: 

1.Download file from java.com
2.extract it into your usr/lib/jvm directory (that's where I put it)
3.for a 32 bit machine, create a link to usr/lib/jvm/jre<version>/plugin/i386/ns7/libjavaplugin_oji.so in  usr/lib/firefox/plugins AND put *another* link in usr/lib/firefox-addons/plugins

That's what worked for me. 

Thanks for all the clues folks!

---

