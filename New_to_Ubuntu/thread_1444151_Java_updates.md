---
title: "Java updates"
date: 2010-03-31
forum: New to Ubuntu
---

### Post by flyfishingphil on 2010-03-31
It's been addressed before but I'm not sure that something from '05 or '06 is really that applicable today.

Hit a couple of sites that required Java RunTime Vers.19 so went to Ubuntu store, entered Java and installed it. Went back to sites and was told I did not have the current version needed.

Found it but figured I'd get direction first. Could somebody give me a step by step on how to install the Ver 19 of Java? I can do the download but after that I'm lost.

Thanks for the assist.

---

### Post by mikewhatever on 2010-03-31
Sun's java in the repositories is rarely, if at all, updated. Try the link below for a manual.
[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by flyfishingphil on 2010-04-01
That one didn't want to work right even though I followed the instructions and did the copy/paste process. I did notice though that it recommended against the use of the JRE but did recommend the OpenJDK Java 6 Runtime instead. Went to the http it recommended and followed the instructions there. Will see if everything works right. 

If anybody is looking for the info on how to get the OpenJDK Java 6 Runtime here is the page with full instructions: [easylinuxtipsproject]("http://sites.google.com/site/easylinuxtipsproject/multimedia")

Hopes this works right.

Thanks for pointing me in the right direction.

---

### Post by mikewhatever on 2010-04-01
The copy-pasting may not have worked because the commands deal with java6u18, while you have u19. I wonder if openJDK gets updated.

---

### Post by flyfishingphil on 2010-04-01
Just checked around the net and found several games sites where you can't play the games. Went back in and checked at Firefox and it states that JRE is needed, not JDK. Great, now I have to figure out how to install the JRE to get it to work right. That may prove to be real interesting since I went thru the steps before and have no idea how much garbage I left behind.

(Since this is a "public" location, I won't say what I'm thniking right now but it's usually expressed something like this "%^%$$@$%&*((&^%#$#&*(&$#@@#$%^&%$#%$##!)

---

### Post by mikewhatever on 2010-04-01
To be sure, there is a removal section.
[http://sites.google.com/site/easylinuxtipsproject/java#TOC-Removal](http://sites.google.com/site/easylinuxtipsproject/java#TOC-Removal)

---

### Post by flyfishingphil on 2010-04-01
Trying to follow the instructions at the Easy Linux tips. Here's what happens:

flyfishingphil@flyfishingphil-laptop:~$ cd /opt
flyfishingphil@flyfishingphil-laptop:/opt$ sudo mkdir 32
[sudo] password for flyfishingphil: 
mkdir: cannot create directory `32': File exists
flyfishingphil@flyfishingphil-laptop:/opt$ sudo mv ~/jre-6u19-linux-i586.bin /opt/java/32
flyfishingphil@flyfishingphil-laptop:/opt$ sudo chmod 755 /opt/java/32/jre-6u19-linux-i586.bin
chmod: cannot access `/opt/java/32/jre-6u19-linux-i586.bin': Not a directory
flyfishingphil@flyfishingphil-laptop:/opt$ sudo chmod 755 /opt/java/32/jre-6u19-linux-i586.bin
chmod: cannot access `/opt/java/32/jre-6u19-linux-i586.bin': Not a directory
flyfishingphil@flyfishingphil-laptop:/opt$
When I tried it earlier this is where I ran into the roadblock and could get no further.

I looked in the Home Directory and see a folder marked Java with a lock on it but didn't see the JRE 6 Ver 19 that I downloaded in there anymore.

Any ideas on how else it might be installed?

Another question: Trying to use the install directions from Sun Java and it calls for a change to the directory in which to install using cd <directory path name>. WHat directory do I need to direct this to? (Example in the directions show "cd /usr/java")

---

