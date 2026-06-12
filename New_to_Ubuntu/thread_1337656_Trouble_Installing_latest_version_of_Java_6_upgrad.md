---
title: "Trouble Installing latest version of Java 6 upgrade 17"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by Odin888 on 2009-11-25
Hi all.

I am a newbie to Ubuntu! I love my Linux machine and so do my computers. I have installed it on a friends notebook, and she loves it.

I am having a very difficult time trying to figure out how to install the latest update of Java 6, which is update 17.

I have entered

sudo apt-get install ubuntu-restricted-extras

and also

sudo apt-get install sun-java6-jre sun-java6-plugin

I thought this would upgrade to the 6 17 version. No luck.

I cannot access my account with the Government because of not having this.

Any help would be greatly appreciated.

Thank you,
Peter

---

### Post by Daveth on 2009-11-26
I guess the new build may have not hit the Ubuntu repositories yet. You can snag it from Sun here: 

[http://www.java.com/en/download/manual.jsp#lin](http://www.java.com/en/download/manual.jsp#lin)

where you should read the Linux self-extracting version, not the rpm one. You will need to "sudo" rather than "su", but apart from that it looks fairly straightforward. Remember to add to period "." in front of the / when running the bin file (./). I would uninstall any Java that you may have beforehand so it is a clean install with build 17.
David

---

### Post by XCan on 2009-11-26
Unfortunately, Canonical seems to have made the (very bad IMHO) decision to no longer update the sun-java, since they want people to use openjdk. However, there is a nice tutorial on how to install sun-java manually and integrate it nicely written by one of the forum members [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by Odin888 on 2009-11-26
Thanks will give it a shot tomorrow. :) Really appreciate the help!!!!

---

### Post by Odin888 on 2009-11-26
Yea it works!!!! Thanks again. Next task is the Nvidia update....Ooooo wish me luck. :)

---

### Post by XCan on 2009-11-27
Great that it worked out. :) Nvidia update, *shiver*, that can be a mess when it comes to kernel updates and stuff. :p

---

### Post by wirah on 2009-11-27
I hope Canonical realise that they've made an Ubuntu-damaging decision with Java.

Seriously. I work in a real company, one which makes money. I can't pretend that OpenJDK is so great that software I develop locally on it is going to work exactly the same, without risk, on a live system.

Canoncial, please start maintaining Java again. It's about choice, after all.

---

### Post by Norm24 on 2009-11-27
> **XCan said:**
> Unfortunately, Canonical seems to have made the (very bad IMHO) decision to no longer update the sun-java, since they want people to use openjdk. However, there is a nice tutorial on how to install sun-java manually and integrate it nicely written by one of the forum members [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

Worked great.Thanks for posting that link.

---

### Post by eyelessfade on 2009-12-13
> **XCan said:**
> Unfortunately, Canonical seems to have made the (very bad IMHO) decision to no longer update the sun-java[/url]

You don't have a link to this statement?

---

### Post by Norm24 on 2009-12-13
It worked for me.

---

### Post by spier on 2009-12-16
> **eyelessfade said:**
> You don't have a link to this statement?

maybe Synaptic's bottom line in sun-java6-jdk description's:

"Canonical does not provide updates for sun-java6-jdk. Some updates may be provided by the Ubuntu community."

---

### Post by philinux on 2009-12-16
The repo version 6-15 is pretty up to date. Just not bang up to date.
Java(TM) Plug-in 1.6.0_15

---

### Post by MadCatmkII on 2009-12-22
> **XCan said:**
> Unfortunately, Canonical seems to have made the (very bad IMHO) decision to no longer update the sun-java, since they want people to use openjdk. However, there is a nice tutorial on how to install sun-java manually and integrate it nicely written by one of the forum members [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

Thank you for that great link! I've been trying to install the java JDK for two days now. Does anyone know what else I have to do besides the steps needed for the JRE?

---

### Post by Mighty_Joe on 2009-12-22
> **spier said:**
> maybe Synaptic's bottom line in sun-java6-jdk description's:

"Canonical does not provide updates for sun-java6-jdk. Some updates may be provided by the Ubuntu community."

In [this bug]("https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/420426") there's some good discussion.  There's two reasons:
-there's a shortage of manpower and the Ubuntu devs don't want to be on the hook for 2 versions of Java
-OpenJDK's licensing is more in tune with Ubuntu's goals compared to Sun's.

---

### Post by Eladon on 2009-12-22
Had a couple of issues with the instructions from the link on post #3.

1) Strangely, it broke my Firefox.  Firefox would open, but no web pages would load.  I had to go into System > Administration > Synaptic Package Manager, and do a reinstall of Firefox.  But after that, everything worked fine.

2) The association for .jnlp files was broken.  When you click on a .jnlp file, choose "Open with", and browse to "/opt/java/32/jre1.6.0_17/bin/javaws", and if you like, check "Do this automatically...", then click "OK".

---

### Post by yoitslion on 2010-01-03
I followed all of the instructions on the link and i am still having trouble with Java. Firefox shows the plugin installed, I verfied on the Java website that I have the 6-17 update running, but for some reason I still have Java trouble on some sites. For instance, on the photo upload screen on Facebook, the uploader won't load. 

Just looks like this:

[IMG]http://img188.imageshack.us/img188/1807/screenshotlm.png[/IMG]


I looked at Synaptic and it shows no installed versions.  I'm confused. HELP!

---

### Post by 73ckn797 on 2010-01-03
I have just changed to the "openjdk" and it work just fine for my needs. No problems yet. I tried the latest Java ([http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)) but it was very slow to load an applet. Openjdk is working better than the "sun-java" in Synaptic or the link provided.

---

