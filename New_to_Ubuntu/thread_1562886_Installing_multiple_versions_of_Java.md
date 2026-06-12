---
title: "Installing multiple versions of Java"
date: 2010-08-28
forum: New to Ubuntu
---

### Post by aykayross on 2010-08-28
I need to get Sun Java jre1.5.0_13 installed on my Dell Vostro 1000 AMD64 Athlon X2  running Ubuntu 10.4 (lucid)
I already have Sun Java jre1.6.0.20 installed but when I connect to a specific installation of the Oracle eBusiness Suite I get an error message stating that jre1.5.0_13 is not installed.
Upgrading the Oracle eBusiness Suite Java to the latest version is not an option, so therefore I need to get the older Java version installed on my laptop along side the newer version.
Failing this I will have to regress and use Windows.

I have researched all the forums, but there is no clear instruction on how to install two versions of Java on Ubuntu or even Linux, an even more bizarre this is possible in Windows.

I have done the following but still cannot get the older Java version recognized.
downloaded version from Sun
***jdk-1_5_0_13-linux-amd64.bin***

run the following commands:
[B][I]sudo cp jdk-1_5_0_13-linux-amd64.bin /opt
cd /opt
sudo sh ./jdk-1_5_0_13-linux-amd64.bin[/I][/B]

accepted the license agreement
directory was created 
*jdk1.5.0_13*

then tried this command

***sudo update-alternatives --config java***

and got the following error message:
[I]There is only one alternative in link group java: /usr/lib/jvm/java-6-sun/jre/bin/java
Nothing to configure[/I].

the following command
***sudo update-java-alternatives -l ***
got this result:
*java-6-sun 63 /usr/lib/jvm/java-6-sun*

My existing version of Java is in the following directory:
*/user/lib/jvm*
I copied the *jdk1.5.0_13 directory into this directory, and made sure that the ownership was still root.*

Now how do I get this version as well as the newer version recognized by the system and most importantly by Firefox?

---

### Post by Zirts on 2010-08-28
You could try at first just getting rid of the latest version of java. 

Also as much as I know Firfox has it's own little java and flash plugin, so even if you removed all Javas from your computer, Firefox will still continue to play all videos and run all apps.

---

### Post by skatinjj on 2010-08-28
> **Zirts said:**
> You could try at first just getting rid of the latest version of java. 

Also as much as I know Firfox has it's own little java and flash plugin, so even if you removed all Javas from your computer, Firefox will still continue to play all videos and run all apps.

Can check [this]("http://ubuntuforums.org/showthread.php?t=1398360") out.

---

