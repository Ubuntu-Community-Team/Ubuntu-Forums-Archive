---
title: "The system does not let me install flash plugin for Chromium"
date: 2011-03-08
forum: New to Ubuntu
---

### Post by mrtn474 on 2011-03-08
Hello,

I don't seem to be able to download plugins for chromium. When I click the link to download, the ubuntu software installer opens. A note says that I need a third party source. I click the button "Use this source." I authenticate, but the authentication dialog window never closes after I type in my password. 

Also, when I visit a site that requires java, I never get the option to download that plugin.

Details: I'm new to Ubuntu, and this is actually the first time I try it after fully installing it in my machine using wubi.

Thanks in advance for all the replies.

---

### Post by mrtn474 on 2011-03-08
I initially installed the netbook remix edition, but i really didn't like it. It was so simple and it seemed to be a bit slow so I switched to the desktop version(?) with the settings from Login Screen. 

I noticed that I have mutter and metacity installed, which is what makes the netbook edition look the way it does, right? What if I uninstall them? Will I regret it?

I've searched this forum for answers, but I've found none :\

---

### Post by mikewhatever on 2011-03-08
Search for the **ubuntu-restricted-extras** in the Software Center. That package will pull in flash, java and other useful multimedia goodies.

---

### Post by wojox on 2011-03-08
Open a terminal and run:

```
sudo apt-get update; sudo apt-get install ubuntu-restricted-extras
```

This will install codecs and plugins and lots of great stuff.

As far as removing mutter and metacity, I would leave them. Metacity is your window manager so you need that to fall back on if mutter or compiz flake out.

---

### Post by mrtn474 on 2011-03-08
awesome! thank you so much, it worked :)

---

### Post by mrtn474 on 2011-03-08
Actually, it kinda worked. Youtube worked perfectly okay, but when i went on minecraft or runescape to test out java, the games would load, but then the screen would turn black once they finished loading.

---

### Post by gandaran on 2011-03-08
> **mrtn474 said:**
> Actually, it kinda worked. Youtube worked perfectly okay, but when i went on minecraft or runescape to test out java, the games would load, but then the screen would turn black once they finished loading.
you need sun-java for minecraft or runescape, remove the openjdk-java that the ubuntu-restricted-extras package installed then enable the archive.canonical partner repository in software sources and update software package list next then you will find the sun-java6-plugin in the package manager ready for install.

---

### Post by mrtn474 on 2011-03-08
> **gandaran said:**
> you need sun-java for minecraft or runescape, remove the openjdk-java that the ubuntu-restricted-extras package installed then enable the archive.canonical partner repository in software sources and update software package list next then you will find the sun-java6-plugin in the package manager ready for install.
Okay, I'm a total noob at this. could you explain that either more detailed, or more simple?

---

### Post by mikewhatever on 2011-03-08
OK, open Application->Accessories->Terminal.

First, remove openjdk java:
```
sudo apt-get purge openjdk-6-jre openjdk-6-jre-lib icedtea6-plugin icedtea-6-jre-cacao
```

Clean up any residual packages:
```
sudo apt-get --purge autoremove
```


Add the partner repository for Maverick:
```
sudo add-apt-repository &#8220;deb http://archive.canonical.com/ maverick partner&#8221;
```

Install Sun's java:
```
sudo apt-get install sun-java6-jre sun-java6-plugin
```

---

### Post by mrtn474 on 2011-03-08
I think there was an error when I tried to run the first command: 

> mrtn@ubuntu:~$ sudo apt-get purge openjdk-6-jre openjdk-6-jre-lib icedtea6-plugin icedtea-6-jre-cacao
[sudo] password for mrtn: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 openjdk-6-jre : Depends: openjdk-6-jre-headless (>= 6b20-1.9.7-0ubuntu1) but it is not going to be installed
E: Broken packages


---

### Post by mikewhatever on 2011-03-08
That error means openjdk java wasn't installed correctly in the first place. For now, disregard my previous post and let's try fixing openjdk. 

That should fix the broken packages:
```
sudo apt-get install -f
```

---

### Post by mrtn474 on 2011-03-08
> mrtn@ubuntu:~$ sudo apt-get install -f
[sudo] password for mrtn: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Seems like the fix was successful. I tried out minecraft once more but it still gave me the same result, which was expected, right? Now do I follow the instructions on your previous post?

---

### Post by mikewhatever on 2011-03-08
Yea, but before you do, make sure the browser plugin is installed:

```
sudo apt-get install icedtea6-plugin
```

I don't use java myself, so not quite sure what works with minecraft.

---

### Post by mrtn474 on 2011-03-08
> mrtn@ubuntu:~$ sudo apt-get install icedtea6-plugin
[sudo] password for mrtn: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
icedtea6-plugin is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


I'm assuming that says it is already installed? So now, should I follow your previous instructions?

---

### Post by mikewhatever on 2011-03-08
> **mrtn474 said:**
> I'm assuming that says it is already installed? So now, should I follow your previous instructions?

Yep. Try the games in other browsers as well.

---

### Post by mrtn474 on 2011-03-09
ugh.. it's still not working. it gave me the same message. it seems to work on firefox, though. 

If I want to play anything that runs on java i'll just use firefox. thank you so much for all the replies :)

---

