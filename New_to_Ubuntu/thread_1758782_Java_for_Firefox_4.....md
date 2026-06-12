---
title: "Java for Firefox 4....?"
date: 2011-05-15
forum: New to Ubuntu
---

### Post by jrozo17 on 2011-05-15
Okay guys I really need help. I have searched and searched how to install Sun Java, not OpenJDK, since not everything works with that. I've tried looking it up in Synaptic Package Manager, installing .deb files, running the terminal, etc but apparently I'm doing something wrong.

Can someone help me out? How do you firstly install Java, and secondly install the plugin? And why is this so complicated to do?(compared to installing Adobe flash player)

I have Ubuntu 10.04 and Firefox 4.

:confused:

---

### Post by manishraj2011 on 2011-05-15
Do you want to install Sun Java JRE or JDK ......????

---

### Post by jrozo17 on 2011-05-15
> **manishraj2011 said:**
> Do you want to install Sun Java JRE or JDK ......????

What is the difference??

---

### Post by manishraj2011 on 2011-05-15
> **jrozo17 said:**
> What is the difference??
JDK is Java Development Kit .... It is required if u want to do some coding work in Java ....

If u just need that just as a surfing plugin for firefox then go for JRE.....

What's your choice???

---

### Post by jrozo17 on 2011-05-15
> **manishraj2011 said:**
> JDK is Java Development Kit .... It is required if u want to do some coding work in Java ....

If u just need that just as a surfing plugin for firefox then go for JRE.....

What's your choice???

Ohh for sure JRE then.. How do i get it? :confused:

---

### Post by wildmanne39 on 2011-05-15
> **jrozo17 said:**
> What is the difference??

Hi, if you go into the thread marked Multimedia & Video then click on Comprehensive Multimedia & Video Howto it will tell you what you need to know to get all your media working.:)

---

### Post by manishraj2011 on 2011-05-15
> **jrozo17 said:**
> Ohh for sure JRE then.. How do i get it? :confused:
Check this link ( directly from Sun Java website )...

[http://www.java.com/en/download/help/linux_install.xml](http://www.java.com/en/download/help/linux_install.xml)

If u have any problem following the steps mentioned in there, please feel free to post back ( with error you encountered ).

---

### Post by jrozo17 on 2011-05-15
> **manishraj2011 said:**
> Check this link ( directly from Sun Java website )...

[http://www.java.com/en/download/help/linux_install.xml](http://www.java.com/en/download/help/linux_install.xml)

If u have any problem following the steps mentioned in there, please feel free to post back ( with error you encountered ).

Thanks but quick question.. The downloads say Linux, or Linux RPM. Which is it?

EDIT: Nevermind, it says right under it. Duh lol sorry.

---

### Post by manishraj2011 on 2011-05-15
> **jrozo17 said:**
> Thanks but quick question.. The downloads say Linux, or Linux RPM. Which is it?

EDIT: Nevermind, it says right under it. Duh lol sorry.
Download the binary and follow the instruction for the same.

---

### Post by jrozo17 on 2011-05-15
Okay, I got to step 4 and there's no license agreement that pops up... All it says is 'Done'?

---

### Post by manishraj2011 on 2011-05-15
> **jrozo17 said:**
> Okay, I got to step 4 and there's no license agreement that pops up... All it says is 'Done'?
Yes.... I think its** fine **because when I have installed the same then at that time also no pop-up for agreement acceptance was shown.....

---

### Post by jrozo17 on 2011-05-15
> **manishraj2011 said:**
> Check this link ( directly from Sun Java website )...

[http://www.java.com/en/download/help/linux_install.xml](http://www.java.com/en/download/help/linux_install.xml)

If u have any problem following the steps mentioned in there, please feel free to post back ( with error you encountered ).

Ok this is the part I get stuck on.. in the Enable and Configure section I type everything it tells me to.. and it says this. :confused:

james@james-desktop:~$  cd /usr/lib/firefox/plugins
james@james-desktop:/usr/lib/firefox/plugins$ ln -s /home/james/jre1.6.0_25/lib/i386/libnpjp2.so
ln: creating symbolic link `./libnpjp2.so': Permission denied
james@james-desktop:/usr/lib/firefox/plugins$ 

Can you make any sense of that? I'm prettyy sure I'm running as root.

---

### Post by wildmanne39 on 2011-05-15
> **jrozo17 said:**
> Ok this is the part I get stuck on.. in the Enable and Configure section I type everything it tells me to.. and it says this. :confused:

james@james-desktop:~$  cd /usr/lib/firefox/plugins
james@james-desktop:/usr/lib/firefox/plugins$ ln -s /home/james/jre1.6.0_25/lib/i386/libnpjp2.so
ln: creating symbolic link `./libnpjp2.so': Permission denied
james@james-desktop:/usr/lib/firefox/plugins$ 

Can you make any sense of that? I'm prettyy sure I'm running as root.

Hi, that is the reason I suggested using the media how to guide it does it all for you.

---

### Post by wildmanne39 on 2011-05-15
> **jrozo17 said:**
> Ok this is the part I get stuck on.. in the Enable and Configure section I type everything it tells me to.. and it says this. :confused:

james@james-desktop:~$  cd /usr/lib/firefox/plugins
james@james-desktop:/usr/lib/firefox/plugins$ ln -s /home/james/jre1.6.0_25/lib/i386/libnpjp2.so
ln: creating symbolic link `./libnpjp2.so': Permission denied
james@james-desktop:/usr/lib/firefox/plugins$ 

Can you make any sense of that? I'm prettyy sure I'm running as root.
Did you put sudo before the command and then enter your password?

---

### Post by jrozo17 on 2011-05-15
> **wildmanne39 said:**
> Did you put sudo before the command and then enter your password?

You mean for the command it shows an error on?

---

### Post by manishraj2011 on 2011-05-15
> **jrozo17 said:**
> Ok this is the part I get stuck on.. in the Enable and Configure section I type everything it tells me to.. and it says this. :confused:

james@james-desktop:~$  cd /usr/lib/firefox/plugins
james@james-desktop:/usr/lib/firefox/plugins$ ln -s /home/james/jre1.6.0_25/lib/i386/libnpjp2.so
ln: creating symbolic link `./libnpjp2.so': Permission denied
james@james-desktop:/usr/lib/firefox/plugins$ 

Can you make any sense of that? I'm prettyy sure I'm running as root.
U are still not having root privilege because

u wrote : james@james-desktop

Type :

sudo -s

It will ask for your password and then your prompt should become like :

root@james-desktop

Then you can proceed with the other steps...

---

### Post by jrozo17 on 2011-05-15
When I ran sudo before I got this:


james@james-desktop:/usr/lib/firefox/plugins$ **sudo** ln -s /home/james/jre1.6.0_25/lib/i386/libnpjp2.so
[sudo] password for james: 


then after I typed my password, this showed up..


james@james-desktop:/usr/lib/firefox/plugins$ sudo cd /usr/lib/firefox/plugins


The directions dont mention anything like this showing. :confused:

---

### Post by jrozo17 on 2011-05-15
> **manishraj2011 said:**
> U are still not having root privilege because

u wrote : james@james-desktop

Type :

sudo -s

It will ask for your password and then your prompt should become like :

root@james-desktop

Then you can proceed with the other steps...

Took your advice and got this..
james@james-desktop:/usr/lib/firefox/plugins$ sudo -s
root@james-desktop:/usr/lib/firefox/plugins# ln -s /home/james/jre1.6.0_25/lib/i386/libnpjp2.so
ln: creating symbolic link `./libnpjp2.so': File exists
root@james-desktop:/usr/lib/firefox/plugins#

---

### Post by jrozo17 on 2011-05-15
I'll be back after a few hours after I sleep and hopefully we can do this..

manishraj2011 and wildmanne39 thanks for all the help, I appreciate it. Hopefully you guys will be on tomorrow :)

---

### Post by manishraj2011 on 2011-05-15
> **jrozo17 said:**
> Took your advice and got this..
james@james-desktop:/usr/lib/firefox/plugins$ sudo -s
root@james-desktop:/usr/lib/firefox/plugins# ln -s /home/james/jre1.6.0_25/lib/i386/libnpjp2.so
ln: creating symbolic link `./libnpjp2.so': File exists
root@james-desktop:/usr/lib/firefox/plugins#
delete the link file and try the steps again....

( You can use :  rm -i libnpjp2.so )

.....

---

### Post by mikewhatever on 2011-05-15
Here is a very nice howto on installing JRE manually.
[http://sites.google.com/site/easylinuxtipsproject/java#TOC-Manual-for-JRE](http://sites.google.com/site/easylinuxtipsproject/java#TOC-Manual-for-JRE)

---

### Post by manishraj2011 on 2011-05-15
I think u have installed the jre in your home folder.....

( u wrote :

 ln -s** /home/james/**jre1.6.0_25/lib/i386/libnpjp2.so )

So after deleting the link file u have to also delete the jre folder.

( U can do that by following steps :

1) Go to home folder :

cd

2) take root privilege :

sudo -s

3) Delete the folder :

rm -Rf ./jre1.6.0_25/ 

)

Then follow the following steps carefully ( specially compiled by me ) :

 [SIZE=2]# _Steps to install Sun jre :_[/SIZE]

1) Download the bin file ( I think you already did that )

2) make the file executable :

**chmod u+x <file>**

3) **sudo -s** # To gain root access #

4) **cd /usr**

5) **mkdir java **

6) **cd java**

7) **/<download path>/<downloaded bin file>**

  e.g. /home/james/Downloads/jre-6u25-linux-i586.bin
[SIZE=2]
# _To install firefox-4.0 plugin_[/SIZE]

8 ) **cd /usr/lib/firefox-4.0/plugins/**

9) [B]ln -s /usr/java/jre1.6.0_25/lib/i386/libnpjp2.so
[/B]
10) For confirming the installation of plugin, close all firefox windows and re-open it .
     
    Type in :
     
     about: plugins     ( without spaces )

    in the awesome bar ( as firefox calls it )  and pressing enter key .

11) You can also confirm the installation of java plugin by the following link :

     [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)

---

### Post by jrozo17 on 2011-05-15
> **manishraj2011 said:**
> I think u have installed the jre in your home folder.....

( u wrote :

 ln -s** /home/james/**jre1.6.0_25/lib/i386/libnpjp2.so )

So after deleting the link file u have to also delete the jre folder.

( U can do that by following steps :

1) Go to home folder :

cd

2) take root privilege :

sudo -s

3) Delete the folder :

rm -Rf ./jre1.6.0_25/ 

)

Then follow the following steps carefully ( specially compiled by me ) :

 [SIZE=2]# _Steps to install Sun jre :_[/SIZE]

1) Download the bin file ( I think you already did that )

2) make the file executable :

**chmod u+x <file>**

3) **sudo -s** # To gain root access #

4) **cd /usr**

5) **mkdir java **

6) **cd java**

7) **/<download path>/<downloaded bin file>**

  e.g. /home/james/Downloads/jre-6u25-linux-i586.bin
[SIZE=2]
# _To install firefox-4.0 plugin_[/SIZE]

8 ) **cd /usr/lib/firefox-4.0/plugins/**

9) [B]ln -s /usr/java/jre1.6.0_25/lib/i386/libnpjp2.so
[/B]
10) For confirming the installation of plugin, close all firefox windows and re-open it .
     
    Type in :
     
     about: plugins     ( without spaces )

    in the awesome bar ( as firefox calls it )  and pressing enter key .

11) You can also confirm the installation of java plugin by the following link :

     [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)

Wow, that did the trick! You are awesome man. Thanks for taking your time typing that out, and thank you to everyone else as well. :)

Hopefully this thread will help anyone else dealing with the same problem with java. ;-)

Peace :guitar:

---

