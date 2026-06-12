---
title: "[SOLVED] Java chat applet not starting"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by greenleaves123 on 2008-12-29
I am using Firefox. I tried to open up this chat, but it's not working. What should I do?

---

### Post by taurus on 2008-12-29
Have you installed java and its plugin?

---

### Post by greenleaves123 on 2008-12-29
The chat was working before, but then Firefox crashed and I got help here and reinstalled Firefox.

Maybe I got rid of Java?

How to I get Java and it's plugins or whatever?

---

### Post by taurus on 2008-12-29
```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```
When you get to the java license screen, hit the Tab key to highlight the <OK> and then Return to accept it.

Remember, you have to restart firefox after installing a plugin.

---

### Post by igknighted on 2008-12-29
If using 32bit: "sudo apt-get install sun-java6-plugin"

If 64bit: Post back and seek further direction.

---

### Post by greenleaves123 on 2008-12-29
Before it asked me to put a folder for the cache or something. I didn't know what to do so I just selected the folder Public. I don't know if that has anything to do with it.

I got the updates, but it said Java was already the latest version. Chat is still not working. I don't know what 32bit and 64bit are.

---

### Post by taurus on 2008-12-29
```
uname -m
```

---

### Post by greenleaves123 on 2008-12-29
I got: i686

---

### Post by igknighted on 2008-12-29
In firefox, go to "tools"->"add ons"->"plugins" and see if Java is listed.

---

### Post by greenleaves123 on 2008-12-29
Nope, Java is not listed.

---

### Post by igknighted on 2008-12-29
Hmmm, go to synaptic and mark all the sun-java6 packages you have installed for complete removal and apply the changes.  Then go back and install them again, and restart firefox.

EDIT: Do you have the default ubuntu firefox installed?

---

### Post by greenleaves123 on 2008-12-29
I'm sorry, I don't understand what to do. What is synaptic? I went to this application, it asked for my password and there is a long list of stuff. Should I check everything with the word java?

---

### Post by igknighted on 2008-12-29
> **greenleaves123 said:**
> I'm sorry, I don't understand what to do. What is synaptic? I went to this application, it asked for my password and there is a long list of stuff. Should I check everything with the word java?

Synaptic is the default package manager... it is the GUI for installing or uninstalling software in Gnome/Ubuntu

[http://psychocats.net/ubuntu/installingsoftware#synaptic](http://psychocats.net/ubuntu/installingsoftware#synaptic)

---

### Post by greenleaves123 on 2008-12-29
I went to Synaptic and searched for sun java6 and marked all those that were not marked. I am waiting for it to install now, it is taking a long time.

---

### Post by greenleaves123 on 2008-12-29
I don't know if I have the default firefox.

---

### Post by igknighted on 2008-12-29
> **greenleaves123 said:**
> I went to Synaptic and searched for sun java6 and marked all those that were not marked. I am waiting for it to install now, it is taking a long time.

No, you wanted completely remove all of them (right click, mark for complete removal).  I think in fixing firefox, you erased something java needs.  Therefor we must reinstall java.  Once you have completely removed the sun-java6 packages, then you can reinstall the same ones you just removed.

---

### Post by greenleaves123 on 2008-12-29
Oops, I think I messed things up. It was taking forever so I thought maybe it was stuck so I restarted the netbook. Now synaptic has an error and won't start.

---

### Post by greenleaves123 on 2008-12-29
Here is the error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by igknighted on 2008-12-29
> **greenleaves123 said:**
> Oops, I think I messed things up. It was taking forever so I thought maybe it was stuck so I restarted the netbook. Now synaptic has an error and won't start.

Run this command from the CLI (you need to accept a license for java, that is likely what it is waiting for):

```
sudo dpkg --configure -a
```

Then run:

```
sudo apt-get -f install
```

Synaptic should now work fine.

---

### Post by SuperSonic4 on 2008-12-29
What is the error? Try ```
sudo dpkg --configure -a
``` It's the usual for broken packages IIRC

---

### Post by greenleaves123 on 2008-12-29
It didn't work, I don't know what to do. Do I go to the website?

[sudo] password for jenny: 
Setting up sun-java6-fonts (6-06-0ubuntu1) ...
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-lucida
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for UMingCN, defaulting to 0.

Setting up sun-java6-doc (6-06-0ubuntu1) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]

---

### Post by igknighted on 2008-12-29
<rant> Oh ****.  I hate the way Java is packaged </rant>

The only way to get rid of this is to go download the file it wants (it gives you the link), and then put it in the folder it asks you to.

---

### Post by SuperSonic4 on 2008-12-29
```
sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install sun-java6-fonts sun-java6-jre sun-java6-plugin
```

you don't need the documentation

---

### Post by igknighted on 2008-12-29
> **SuperSonic4 said:**
> you don't need the documentation

Indeed, but it won't let you use apt to install anything until you fix it.

---

### Post by greenleaves123 on 2008-12-30
It didn't work again. I went to the website, but I don't know what to do there.


[Press RETURN to try again, 'no' + RETURN to abort] no
Abort installation of JDK documentation
dpkg: error processing sun-java6-doc (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 sun-java6-doc
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by igknighted on 2008-12-30
Can you run 'sudo apt-get remove --purge sun-java6-doc'?

---

### Post by greenleaves123 on 2008-12-30
I'm not sure what it did. I got this:

jenny@jenny:~$ sudo apt-get remove --purge sun-java6-doc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  apturl xulrunner-1.9-gnome-support
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  sun-java6-doc*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 197kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 100982 files and directories currently installed.)
Removing sun-java6-doc ...
Ignoring nonregistered document `sun-java6-jdk-doc'
jenny@jenny:~$

---

### Post by igknighted on 2008-12-30
> **greenleaves123 said:**
> I'm not sure what it did. I got this:

jenny@jenny:~$ sudo apt-get remove --purge sun-java6-doc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  apturl xulrunner-1.9-gnome-support
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  sun-java6-doc*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 197kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 100982 files and directories currently installed.)
Removing sun-java6-doc ...
Ignoring nonregistered document `sun-java6-jdk-doc'
jenny@jenny:~$

Hurray!  Now run 'sudo apt-get -f install', then try removing the packages discussed above in synaptic

---

### Post by greenleaves123 on 2008-12-30
I don't think it worked. I got this:

jenny@jenny:~$ sudo apt-get -f install
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
jenny@jenny:~$

---

### Post by igknighted on 2008-12-30
> **greenleaves123 said:**
> I don't think it worked. I got this:

jenny@jenny:~$ sudo apt-get -f install
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
jenny@jenny:~$

Do you have synaptic or the update manager open?

---

### Post by greenleaves123 on 2008-12-30
I closed synaptic manager and retyped the command. I got:

jenny@jenny:~$  sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  apturl xulrunner-1.9-gnome-support
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jenny@jenny:~$ 

What should I do now?

---

### Post by igknighted on 2008-12-30
try removing the packages discussed above in synaptic

---

### Post by greenleaves123 on 2008-12-30
Yay, I was able to remove them. Now I'm not sure which to install.

---

### Post by igknighted on 2008-12-30
'sudo apt-get install sun-java6-plugin'

---

### Post by greenleaves123 on 2008-12-30
I did that and it worked, but chat still does not work. :/

Thanks for all your help by the way! If I ever figure out everything about Ubuntu, I'll be sure to help others.

---

### Post by greenleaves123 on 2008-12-30
I looked under tools, add-ons then plugins and the java plugin was not listed.

---

### Post by igknighted on 2008-12-30
Did you restart firefox?

---

### Post by greenleaves123 on 2008-12-30
Yep, I restarted Firefox, still doesn't work.

---

### Post by igknighted on 2008-12-30
Can you run the command 'locate firefox > ~/Desktop/ffsearch', and then attach the file that appears?

Also, post the output of the command 'ls /usr/lib/mozilla/plugins'

---

### Post by greenleaves123 on 2008-12-30
I entered top into the terminal and it java isn't showing up at all. I guess it is not running.

---

### Post by igknighted on 2008-12-30
> **greenleaves123 said:**
> I entered top into the terminal and it java isn't showing up at all. I guess it is not running.

The top command shouldn't output anything, it should just put a file on your desktop.  You can attach that file to your post below the text field.

EDIT: Java doesn't run until it is called, so there wouldn't be a process in top to see.

---

### Post by greenleaves123 on 2008-12-30
jenny@jenny:~$ locate firefox > ~/Desktop/ffsearch
bash: locate: command not found
jenny@jenny:~$ ls /usr/lib/mozilla/plugins
flashplugin-alternative.so  nppdf.so
jenny@jenny:~$ 

The first didn't work.

---

### Post by igknighted on 2008-12-30
> **greenleaves123 said:**
> jenny@jenny:~$ locate firefox > ~/Desktop/ffsearch
bash: locate: command not found
jenny@jenny:~$ ls /usr/lib/mozilla/plugins
flashplugin-alternative.so  nppdf.so
jenny@jenny:~$ 

The first didn't work.

Hmm.  Ok... how about the command 'java -version'

---

### Post by greenleaves123 on 2008-12-30
jenny@jenny:~$ java -version
java version "1.6.0_0"
OpenJDK  Runtime Environment (build 1.6.0_0-b11)
OpenJDK Client VM (build 1.6.0_0-b11, mixed mode, sharing)
jenny@jenny:~$

---

### Post by igknighted on 2008-12-30
Ok, try 'sudo apt-get install sun-java6-plugin sun-java6-jre sun-java6-bin'

---

### Post by greenleaves123 on 2008-12-30
Not sure that did anything, I will try restarting firefox and trying chat.

jenny@jenny:~$ sudo apt-get install sun-java6-plugin sun-java6-jre sun-java6-bin
[sudo] password for jenny: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-plugin is already the newest version.
sun-java6-jre is already the newest version.
sun-java6-jre set to manually installed.
sun-java6-bin is already the newest version.
sun-java6-bin set to manually installed.
The following packages were automatically installed and are no longer required:
  apturl xulrunner-1.9-gnome-support
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jenny@jenny:~$

---

### Post by greenleaves123 on 2008-12-30
Nope, chat doesn't work.

---

### Post by igknighted on 2008-12-30
> **greenleaves123 said:**
> Not sure that did anything, I will try restarting firefox and trying chat.

jenny@jenny:~$ sudo apt-get install sun-java6-plugin sun-java6-jre sun-java6-bin
[sudo] password for jenny: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-plugin is already the newest version.
sun-java6-jre is already the newest version.
sun-java6-jre set to manually installed.
sun-java6-bin is already the newest version.
sun-java6-bin set to manually installed.
The following packages were automatically installed and are no longer required:
  apturl xulrunner-1.9-gnome-support
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jenny@jenny:~$

Aha! Try 'sudo dpkg --configure -a' again.

---

### Post by greenleaves123 on 2008-12-30
I did that, nothing happened? Or at least no words appeared. I quit and restarted firefox, chat still doesn't work.

---

### Post by igknighted on 2008-12-30
> **greenleaves123 said:**
> I did that, nothing happened? Or at least no words appeared. I quit and restarted firefox, chat still doesn't work.

Open synaptic again and try to install (or re-install if they are already marked as installed) those three java packages there.

---

### Post by greenleaves123 on 2008-12-30
I reinstalled the sun java6 plugin, jre and bin. I restarted firefox. Chat still doesn't work.

I'll brb, going to shower. Thanks again for all the help.

---

### Post by greenleaves123 on 2008-12-30
I'm back. I don't know if this helps, but my Dell netbook came with this special Dell version of Ubuntu I think....I read about it in the dell forum here.

I had also had problems with that chat before. Sometimes it wouldn't load and I'd have to restart firefox to get it working again.

I'm going to try rebooting, see if that works.

---

### Post by linux_tech on 2008-12-30
after you installed Java, did you select which to use  as the default. If not type;
```

sudo update-alternatives --config java


```

post output, selections

---

### Post by greenleaves123 on 2008-12-30
jenny@jenny:~$ sudo update-alternatives --config java
[sudo] password for jenny: 

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*+        1    /usr/lib/jvm/java-6-openjdk/jre/bin/java
          2    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 2
Using '/usr/lib/jvm/java-6-sun/jre/bin/java' to provide 'java'.

---

### Post by greenleaves123 on 2008-12-30
I selected 2 to see if it would make chat work, it didn't. I switched it back to 1.

When I try to open chat it says the applet is starting, but it doesn't come up. Also the java logo doesn't appear.

On the site with the chat they say to make sure to have the latest version of Java. I don't know if that is important. Again chat was working fine at first. I don't know if maybe fixing firefox messed up java.

---

### Post by greenleaves123 on 2008-12-30
I selected 2 to see if it would make chat work, it didn't. I switched it back to 1.

When I try to open chat it says the applet is starting, but it doesn't come up. Also the java logo doesn't appear.

On the site with the chat they say to make sure to have the latest version of Java. I don't know if that is important. Again chat was working fine at first. I don't know if maybe fixing firefox messed up java.

---

### Post by waspbr on 2008-12-30
for some odd reason I am also having similar problems with intrepid 8.10

I happened to spot this little disclaimer from the sun website

> Provide Information, then Continue to Download

There are no 64-bit versions of the Java Plugin, Java Web Start or Java Control Panel; however the 32-bit versions of the JRE can be installed on 64-bit systems in order to obtain this functionality. Note that only 32-bit browsers are supported at this time. 

---

### Post by linux_tech on 2008-12-30
make sure that "Enable Java" is selected in your Firefox Options Preferences:
 At the top of the Firefox windowOn the menu bar, click on the ToolsFirefoxEdit menu, and select Options->Preferences->
Select the Content panel and make sure that Enable Java is selected

---

### Post by linux_tech on 2008-12-30
Test your Java to make sure its working correctly by going here-
[http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)
also here
[http://javatester.org/index.htm](http://javatester.org/index.htm)
It will also tell you if you are running the latest version or not.

---

### Post by greenleaves123 on 2008-12-30
I tested Java and it didn't work. I got the version number though, it's 1.6.0_0.

Any other ideas?

---

### Post by greenleaves123 on 2008-12-30
Enable java is selected.

---

### Post by greenleaves123 on 2008-12-31
I am thinking of paying for java technical support. Do you guys think I need that? 

What kind of information should I provide to make this go as quickly as possible? I would be paying for the minute.

---

### Post by greenleaves123 on 2008-12-31
I am getting frustrated. I just put $50 into a live expert account only to have the expert tell me he can't help me. He told me it was a problem with Firefox and to go search the Internet for the answer.

I don't even know where to start searching, I am really in the dark with this technical stuff.

---

### Post by greenleaves123 on 2008-12-31
I got chat to work!!!!

Woohoo!

I found this:

[http://maketecheasier.com/java-not-working-on-your-firefox-3-try-this-simple-fix/2008/07/10](http://maketecheasier.com/java-not-working-on-your-firefox-3-try-this-simple-fix/2008/07/10)

I used this:

> sudo apt-get autoremove icedtea-gcjwebplugin

---

