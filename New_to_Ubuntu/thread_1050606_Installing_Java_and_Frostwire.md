---
title: "Installing Java and Frostwire"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by Tmoney1309 on 2009-01-25
I downloaded Java and Frostwire onto my computer. I am using Ubuntu 8.04. How do I get these programs installed?

---

### Post by metallicamike on 2009-01-25
how did you download java? and also to install frostwire just double click if it is a .deb

---

### Post by Tmoney1309 on 2009-01-25
To download Java I just went to Java.com and downloaded it. I did click on Frostwire but it just kept directing me to package manager telling me to install and that is as far as it would go, it wouldn't open up at all after installing it.

---

### Post by syga on 2009-01-25
Forget Frostwire, install Deluge and GTK Gnutella instead. Both can be installed with Synaptic Package Manager easily with no fuss.

---

### Post by metallicamike on 2009-01-25
go to applications>add/remove and check "sun java 6 runtime" and hit apply. For frostwire try going to just [www.frostwire.com](www.frostwire.com) and download the one for ubuntu/debian and when it is done there should be a package named "frostwire-4.17.1.i586.deb" double click that. But first get rid of the first things you downloaded.

---

### Post by Crafty Kisses on 2009-01-25
Assuming you saved the Java file to your desktop, and it's named "Java.bin" do the following:
```
cd ~/Desktop
chmod +x java.bin
sudo mv java.bin /opt
cd /opt
sudo ./java.bin
```
Once you've done that it will start unzipping the files in the /opt directory, there should be a new directory, and not sure what it would be called, but navigate to it:
```
cd jre_directory/bin
sudo ln -s /opt/jre_directory/bin/java /usr/local/bin/java
```
That should get you going with Java. Java is also in the repositories if you don't feel like manually running the script, you can run the following command:
```
sudo apt-get install sun-java6-plugin ; sudo update-java-alternatives -s java-6-sun
```

---

### Post by Tmoney1309 on 2009-01-25
Thank you, I ran the second command and i believe i installed it...now it is on a configuring screen and there is nowhere to accept or anything to I just close the window...or how do I configure it?

---

### Post by Tmoney1309 on 2009-01-25
I tried to hit apply under add/remove programs and it said this...E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I tried to run 'dpkg --configure -a' then i was told i wasnt a superuser...any ideas??

---

### Post by Crafty Kisses on 2009-01-25
Try running the following:
```
sudo dpkg --configure -a
```
Then after that try reinstalling the Java package:
```
sudo apt-get install sun-java6-plugin ; sudo update-java-alternatives -s java-6-sun
```

---

### Post by metallicamike on 2009-01-26
whenever it says that you need super user privilages just run the same command with sudo in front of it. :)

---

### Post by minsf on 2009-01-26
you have another thread on the same topic:
[http://ubuntuforums.org/showthread.php?p=6620768#post6620768](http://ubuntuforums.org/showthread.php?p=6620768#post6620768)
please keep track of your threads, rather than starting new threads
cheers :)

---

