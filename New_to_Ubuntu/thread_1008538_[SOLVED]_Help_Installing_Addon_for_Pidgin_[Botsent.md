---
title: "[SOLVED] Help Installing Addon for Pidgin [Botsentry]"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by Valtiel on 2008-12-11
I have searched for Botsentry on the Add/Remove interface, as well as, in the Sypnatic repositories without any luck. 

I searched and found the sourceforge.com page for the Botsentry project, but I don't know how to install the file.

[http://sourceforge.net/project/showfiles.php?group_id=156021&package_id=235862](http://sourceforge.net/project/showfiles.php?group_id=156021&package_id=235862) 

They have **bot-sentry-1.3.0.tar.bz2** and **bot-sentry-1.3.0.tar.bz2.asc** and when I try to download one of them the system ask me to open it with "Very Sign" or something

I  even downloaded the file to my desktop to try to drop it in pidgin without any luck. 

How can I install this addon for Pidgin?

---

### Post by Michael.Godawski on 2008-12-11
Hi Valtiel, 

here we go:


[LIST=1]
[*]run the terminal
[*]```
sudo apt-get install pidgin-dev
```
[*]download the **bot-sentry-1.3.0.tar.bz2**
[*]extract it to your desktop
[*]navigate in terminal with cd into the extracted folder
[*]run in terminal
[*]```
./configure
```
[*]```
make 
```
[*]```
sudo make install
```
[/LIST]

---

### Post by Valtiel on 2008-12-11
> **Michael.Godawski said:**
> Hi Valtiel, 

here we go:


[LIST=1]
[*]run the terminal
[*]```
sudo apt-get install pidgin-dev
```
[*]download the **bot-sentry-1.3.0.tar.bz2**
[*]extract it to your desktop
[*]navigate in terminal with cd into the extracted folder
[*]run in terminal
[*]```
./configure
```
[*]```
make 
```
[*]```
sudo make install
```
[/LIST]

I'm having a problem

In step 5, I'm told to navigate to the botsentry folder after extracting it to the Desktop so I did this

```
cd Desktop/bot-sentry-1.3.0
```

that went fine.  Now I'm 

```
~/Desktop/bot-sentry-1.3.0$
```

Then I ran ./configure but I get the following message

**configure: error: Your intltool is too old.  You need intltool 0.40.0 or later.**


Can anybody help me with this? I'm in the middle of the installation.

---

### Post by Valtiel on 2008-12-11
Any help?

---

### Post by cdmike2k8 on 2008-12-11
type ```
sudo apt-get install intltool
``` into a terminal and that should install it for you.  If you have any questions or error messages, please post them here

---

### Post by Valtiel on 2008-12-11
> **cdmike2k8 said:**
> type ```
sudo apt-get install intltool
``` into a terminal and that should install it for you.  If you have any questions or error messages, please post them here

Thank you, after that everything went just fantastic.

Now here is my current concern when ran
```

sudo apt-get install pidgin-dev
```

Many files got installed and some got removed. I was told that some files wont be needed anymore and I was told to remove it after I was done with the installation. If I remember correctly, these were some, if not, all of the pidgin.dev files. [for some reason this part of the text in terminal wont show up. I guess you can only have some any characters per window]

How do I remove them?
**EDIT:***I came to find out you can add/remove the pidgin-dev package straight from Synaptic. Just search/find "pidgin-dev"*

Moreover, the files that got removed, are they important for the overall stable operation of Ubuntu? If so, how do I get them back?

Here are the files that got removed

[B]Removing gnash ...
Removing gnash-common ...
Removing libboost-date-time1.34.1 ...
Removing libboost-thread1.34.1 ...
Removing linux-headers-2.6.27-7-generic ...
Removing linux-headers-2.6.27-7 ...[/B]

---

### Post by Michael.Godawski on 2008-12-12
I am getting concerned. 

Why in the name of all linux gods, the installation of the dev files for pidgin is linked with the removing of the core system internals like the linux-headers? Can somebody enlighten me. I know there are metapackages, but isn't this example here a little of a overkill.?

Is your system still working Valtiel?

---

### Post by meson2439 on 2008-12-12
The last time I tried removing packages, mysql got corrupt. The lesson here is never to remove packages, even when the terminal suggested it. The system is clever enough to take care of itself. If it was me I will open up synaptic and make sure those packages are still there. You should pray it is still there...[-o<

---

### Post by Valtiel on 2008-12-12
> **Michael.Godawski said:**
> I am getting concerned. 

Why in the name of all linux gods, the installation of the dev files for pidgin is linked with the removing of the core system internals like the linux-headers? Can somebody enlighten me. I know there are metapackages, but isn't this example here a little of a overkill.?

Is your system still working Valtiel?

To be honest, I have no idea. I'm very new to all of this. I realized those packages were being removed after I had agreed to how much space these new files were going to take in my HD. When I saw that those packages got removed I thought my system was done for and that I had to start from zero all over again. 

Now all I know is that next time around, I will be more careful and take the time to read all that is being told to me on the terminal. 

On the good side, my system started well today [wipes sweat off forehead]

---

### Post by Valtiel on 2008-12-12
> **meson2439 said:**
> The last time I tried removing packages, mysql got corrupt. The lesson here is never to remove packages, even when the terminal suggested it. The system is clever enough to take care of itself. If it was me I will open up synaptic and make sure those packages are still there. You should pray it is still there...[-o<

As obvious as checking for the packages in Synaptic, that was the last thing in my head last night. 

Anyways, after your scary suggestion to check in Synaptic, I came to find out that the Linux gods are by this mere Linux mortal. I searched, found and installed all the packages that got removed during the pidgin-dev blah blah packages installation.

Now I feel more safe :p

---

### Post by LordPenguin on 2008-12-13
> **Michael.Godawski said:**
> Hi Valtiel, 

here we go:


[LIST=1]
[*]run the terminal
[*]```
sudo apt-get install pidgin-dev
```
[*]download the **bot-sentry-1.3.0.tar.bz2**
[*]extract it to your desktop
[*]navigate in terminal with cd into the extracted folder
[*]run in terminal
[*]```
./configure
```
[*]```
make 
```
[*]```
sudo make install
```
[/LIST]

Definitely one of the most clearly written guides to compiling from source code. Seriously, after weeks of frustration I finally know how to do this.

---

### Post by fxu on 2008-12-26
nvm, I forgot the first step. pidgin-dev.

---

### Post by JDuc on 2008-12-26
> **cdmike2k8 said:**
> type ```
sudo apt-get install intltool
``` into a terminal and that should install it for you.  If you have any questions or error messages, please post them here

I'm having this same problem.  I tried this code, and got the following:

```
$ sudo apt-get install intltool
[sudo] password for jan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
intltool is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic linux-headers-2.6.24-19
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Before this, I also manually installed intltool 0.40.1 from this web page: [https://launchpad.net/ubuntu/+source/intltool/0.40.1-1](https://launchpad.net/ubuntu/+source/intltool/0.40.1-1)

I manually installed it by just changing to that directory and running the ./configure command.

Yet I'm still getting the notice that my intltool is still too old.  

When I go to the Synaptic package manager, I'm only presented with version 0.37.1.  If I uninstall this, then manually install 0.40.1, then go back into the package manager, I don't show anything as being installed....but version 0.37.1 shows up (again, just not installed).

I cannot get past this aspect of the install!

I'm relatively new to Linux, so any instructions need to be pretty straight forward...lol

Thanks for any help.

---

### Post by JDuc on 2008-12-27
figured it out after talking with a friend who is familiar with Linux in general.

He directed me to these instructions: [http://www.linuxfromscratch.org/blfs/view/stable/general/intltool.html](http://www.linuxfromscratch.org/blfs/view/stable/general/intltool.html)

After that, I ran into an issue where I didn't have the gettext library, or some such, so I searched for it in Synaptic and installed it, then all went well.

---

### Post by jubalj on 2009-01-04
Hi guys,

Just a quick tip if you are trying to install bot-sentry in ubuntu intrepid but dont want to do all the compiling stuff.. (I have limited space and couldnt afford to install the 65MB required for the build environment).

The jaunty binary seems to work fine for me (on intrepid); as a added bonus the whole process is pretty user-friendly through gdebi.. (no commandline)
 
click below if you are using i386;
[http://launchpadlibrarian.net/19770706/pidgin-bot-sentry_1.3.0-0ubuntu1_i386.deb](http://launchpadlibrarian.net/19770706/pidgin-bot-sentry_1.3.0-0ubuntu1_i386.deb)

builds for other platfoms can be found from this page;
[https://launchpad.net/ubuntu/+source/bot-sentry/1.3.0-0ubuntu1](https://launchpad.net/ubuntu/+source/bot-sentry/1.3.0-0ubuntu1)

hope this helps, hopefully this wont break anything - effect should be pretty similar to installing manually..

cheers
Jubal

---

