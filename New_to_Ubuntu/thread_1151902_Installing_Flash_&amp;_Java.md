---
title: "Installing Flash &amp; Java"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by GeordieJedi on 2009-05-07
Hi all. Hope your all doing well.

I have a (hopefully) quick question.

I a while back I installed Java and Flash on my PC.
However (I seem to rember doing this in one go, by copy and pasting
some commands from a how to guide, and if I remember clearly, it was
all in one go!).

Now I cant for the life of me, rember how to do this...Grr.

I've done quite a few searches on the formums and there is a guide
here  =

[http://ubuntuforums.org/showthread.php?t=766683&highlight=install+flash+java+32+bit](http://ubuntuforums.org/showthread.php?t=766683&highlight=install+flash+java+32+bit)

(But I think I've used this one before and when I enabled the
media-buntu repositorys I kept getting an error message stating that
the GPG key wasn't valid!!).

So does anyone remember, or know how to get the (in one go) install
working?

Thanks in advance for any help.  :D

---

### Post by DLG102282 on 2009-05-07
sudo apt-get install ubuntu-restricted-extras

---

### Post by Sef on 2009-05-07
There is also Add/Remove.   Applications > Add/Remove > Show: All Available Applications > Search: Sun Java 6, > check box next to Sun Java 6 > then Search: Macromedia Flash > check box next to Macromedia Flash > apply changes > apply > close.

---

### Post by m_2009 on 2009-05-07
Java Isnt included in the ubuntu-restricted-extras package in ubuntu jaunty.

The best way to get java and flash is to use synaptic to install the following packages.

ubuntu-restricted-extras
sun-java6-jre
sun-java6-plugin (This will give you java access in forefox, not sure about other browsers)

and hit "mark" when it asks you to mark additional requirements in the window the pops up.

or use a terminal window and execute the following

```
sudo apt-get install ubuntu-restricted-extras sun-java6-jre sun-java6-plugin
```EDIT: Just realised you are running ubuntu Intrepid, so you may not need to install all the packages seperately. Java may come bundled with the ubuntu-restricted-extras package.

If you want to install flash without the restrpicted extras package then just search for:

fplashplugin-nonfree


From when I used intrepid Im pretty sure that the java version included in the repository was a slightly outdated version of java.

If you want to install the latest java version (Update 13) manually then you can do it this way:

download the java bim file from the java website. Make sure you download the Linux (self-extracting file) not the Linux RPM (self-extracting file). Here is a direct link

[http://javadl.sun.com/webapps/download/AutoDL?BundleId=29210](http://javadl.sun.com/webapps/download/AutoDL?BundleId=29210)

WHen you have finished downloading, make sure the jre-6u13-linux-i586.bin is on your desktop. Then open up a terminal window an execute the following commands one by one. I will give a description of what each command does.

This will create the folder for which java will be installed to
```
cd /opt
sudo mkdir java
```This will move the installation file into the folder you created with the above command
```
sudo mv ~/Desktop/jre-6u13-linux-i586.bin /opt/java/
```This will set the permissions to allow the jre-6u13-linux-i586.bin to be executed
```
sudo chmod 755 /opt/java/jre-6u13-linux-i586.bin
```This will run the installer.
```
cd /opt/java/ 
sudo ./jre-6u13-linux-i586.bin
```You will see a lot of text appear in the terminal window, just keep hitting any key until it asks you a yes/no. Type y or yes, then hit enter, and the install will complete.

Next you need to set the newly installed java as the default, to do this run the following 2 commands in the terminal window.

```
sudo update-alternatives --install "/usr/bin/java" "java" "/opt/java/jre1.6.0_13/bin/java" 1 
sudo update-alternatives --set java /opt/java/jre1.6.0_13/bin/java
```If you want to add the plugin for firefox, run the following command from the terminal window.

```
sudo cp -s /opt/java/jre1.6.0_13/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla/plugins
```Java should now be fully installed and working.

If you want to check it has installed correctly and is set to the default then you can use these commands to verify.
```
java -version
```

The following command will check that java is set as the default.
```
sudo update-alternatives --config java
```

---

### Post by GeordieJedi on 2009-05-10
Wow, thank you very much indeed, DLG102282, Sef and m_2009.

Its much appreciated.
Cheers.

---

### Post by Mr_and_Mrs_D on 2009-05-25
Hallo - sorry I brought this up again, I think it's nice to have the info in one place
I am running Ubuntu 9.04 from a live cd   - are the instructions above valid for a live cd ? I mean the ones for  jre-6u13-linux-i586.bin.
I need to install java to perform an online scan...
I suspect at some point I will be asked for a pass : do you know it ?
EDIT : worked :)
No pass

Still the online scan won't run...
EDIT : Run (karpesky) - but crushed after a while - could be due to anything - Trend micro also run but didn't scan (remained on idle) - When it didn't run chances are I had also installed the openJDK java thing that comes with Ubuntu - and maybe there is conflict.

Fact is THE GUIDE ABOVE (jre-6u13-linux-i586.bin) IS VALID FOR THE LIVE CD v9.04

Thanks

D.

PS ubuntu rocks :)

---

