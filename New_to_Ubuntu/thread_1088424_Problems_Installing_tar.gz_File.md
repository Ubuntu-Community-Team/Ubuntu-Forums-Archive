---
title: "Problems Installing tar.gz File"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by RedStarYellowSun on 2009-03-06
I am setting up my sister's computer so that she, too, can enjoy Ubuntu.
The problem is that I am having a problem installing an important program: OpenOffice 3.01.
I am told that you only need to download the file "OOo_3.0.1_LinuxIntel_install_en-US_deb.tar.gz" into Desktop and extract it. It should then become a folder entitled "OOO300_m15_native_packed-1_en-US.9379". Then, place the folder on Desktop, too. So far, so good.
Now comes the problem. Then I am to run: ```
sudo dpkg -i ~/Desktop/OOO300_m15_native_packed-1_en-US.9379/DEBS/*.deb
```
and then:
```
sudo dpkg -i ~/Desktop/OOO300_m15_native_packed-1_en-US.9379/DEBS/desktop-integration/openoffice.org3.0-debian-menus_3.0-9376_all.deb
```.

But, no matter what I do, it keeps telling me that the file or directory doesn't exist. When I type the first code, it always reports back: ```
ana-marie@ana-marie-desktop:~$ sudo dpkg -i ~/Desktop/OOO300_m15_native_packed-1_en-US.9379/DEBS/*.deb
[sudo] password for ana-marie: 
dpkg: error processing /home/ana-marie/Desktop/OOO300_m15_native_packed-1_en-US.9379/DEBS/*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /home/ana-marie/Desktop/OOO300_m15_native_packed-1_en-US.9379/DEBS/*.deb
```

The second instruction code gives the same results.

Unfortunately, due to my ignorance, I cannot see why on Earth this is. The instruction code already says "desktop" *2 times* and I can see the files in Desktop (both the tar.gz and the extracted folder). It *is* there, but it keeps saying that it does not exist.
In desperation, I tried the unfailing:
```
sudo apt-get install <name of deisred program>
```
but it failed:
```
ana-marie@ana-marie-desktop:~$ sudo apt-get install openoffice
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package openoffice
```
even though I already added it to the software source repository with the Authentication key.
I was tempted to install by Synaptic Package Manager, but (after web page after web page of searching) I found that it contains about 47 files and I am too ignorant to tell what files should be installed apart from the obvious ones.
I need help. Sorry for the number of ridiculous requests this past few days. Thank you for your time.

Take care,
RedStarYellowSun

PS: I am very sorry for the long read. _&#915;L°

---

### Post by Kareeser on 2009-03-06
Go to the DEBS folder in your desktop. What kind of files are in there?

There might not be a DEBS folder if you downloaded the wrong version of OpenOffice.

Did you download [this file]("http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=3.0.1")?

---

### Post by ClaytonOT on 2009-03-06
sudo apt-get install openoffice.org

---

### Post by rcayea on 2009-03-21
Hi,

I am completely brand new to Ubuntu. I fussed with other distros and anyway I love the support here...

I have the same problem as I am installing OpenOffice 3.1

I did what ClaytonOT said to do and that just reinstalled OO2.4. Is there something I can do to now target the 3.1 pack on my desktop?

Thanks in advance,
Randy

---

### Post by mocoloco on 2009-03-22
Not to take you guys off topic or discourage your efforts but just two things to consider here: 1) Ubuntu 9.04 comes out in a few weeks which will include OO.o 3, and I recommend most users get the latest release of the OS for the latest features and apps.  And 2) I've seen a lot of users who want to install OO.o 3.1 just 'cause, even though there are no features they need that aren't already in 2.4.

If you know you need 3.1 and you need it now, by all means proceed, and sorry I couldn't be of any actual help with that :p

---

### Post by rcayea on 2009-03-22
Mocoloco,

That makes a lot of sense to me. I am just baffled that this upgrade can't be done and I was hoping to upgrade. But, yes, I will definitely take your advice and just wait until the late April release. 

R.

---

### Post by James_Lochhead on 2009-03-22
Install Ubuntu Tweak:

[Click here to download the deb. Open it with GDebi to install.]("http://ubuntu-tweak.googlecode.com/files/ubuntu-tweak_0.4.6-1%7Eintrepid1_all.deb")

Ubuntu Teak is not in Applications > System Tools > Ubuntu Tweak

Go to Applications > Third Party Software and enable to Open Office 3 repository (remember to unlock the application first using the unlock button and your password).

Once the package list has reloaded go to the Update Manager > System Administration > Update Manager and update your system.

If you upgrade to Jaunty you might want to consider removing the package before the upgrade.

---

### Post by James_Lochhead on 2009-03-22
If a program asks you to download a gzipped tarball (.tar.gz file) like that it generally wants you to compile it (although there are plenty of exceptions to this rule).

Compiling is the process of converting a human readable programming language into something that the machine can understand.

This is quite an advanced topic and should not be undertaken by beginners.

To give you a rough idea of what it entails at the most basic level:

(Assuming you put the tarball in your home directory)

```
sudo apt-get install build-essential
```

You only need to do this once ever. Just installs the program you need.

```

tar xzvf <replace with name of tarball>

ls (look for them name of the directory that came out of the tarball - don't type anything after ls)

cd <replace with name of the directory that came out>

chmod + x configure

./configure

make

sudo make install

```

That is assuming that the package has no dependencies... if it does (which is probably likely) you will have to grab all the packages that are needed as well as their header files (end with devel - mostly not installed by default) or you will get an error.

---

### Post by rcayea on 2009-03-22
Just reading your post now. Thanks James_Lochhead I'll give that a try. 

R.

---

