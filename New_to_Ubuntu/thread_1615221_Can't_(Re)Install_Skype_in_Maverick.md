---
title: "Can't (Re)Install Skype in Maverick"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by mlnease on 2010-11-06
Hello,

I've been using Maverick since day one with nearly perfect results.  Recently, though, I started having some connection problems and completely uninstalled Skype as I was troubleshooting.  I seem to have worked out the connection problem, but now when I try to reinstall Skype I receive the following error message:

mn@mn-OptiPlex-GX270:~$ sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 skype : Depends: libqt4-network (>= 4:4.5.3) but it is not going to be installed
E: Broken packages

I don't seem to have any broken packages.  And when I try to install libqt4-network I just get more similar error messages.

I do have all the pertinent repos.  Anyone know what's going on?  

Thanks in advance.

mike

---

### Post by cariboo on 2010-11-08
Go to System-Administration->Synaptic Package Manager->Edit->Fix broken packages and make sure there isn't anything listed there.

---

### Post by mlnease on 2010-11-08
> **cariboo907 said:**
> Go to System-Administration->Synaptic Package Manager->Edit->Fix broken packages and make sure there isn't anything listed there.
Thanks for your response.  I know the error message indicates a broken package but Synaptic can't find it.

?!  Very odd.

mike

---

### Post by sikander3786 on 2010-11-08
What if you try,

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

---

### Post by mlnease on 2010-11-08
> **sikander3786 said:**
> What if you try,

```
sudo apt-get install -f
``````
sudo dpkg --configure -a
```
Thanks for your response.  I ran the code (also apt-get update) and still receive the same error messages.  Would it help if I post the output?  There's rather a lot of it--

---

### Post by sikander3786 on 2010-11-08
The error messages might reveal something informative. It would be better if you can post the output of both of the above mentioned commands.

One by one, select the output of both your commands after pasting them and use the code tags # from the post menu to format it accordingly.

---

### Post by gradinaruvasile on 2010-11-08
Just uninstall skype with aptitude first. Then download the Skype from the site and try to install it with the graphical installer (it pulls dependencies too).
Also there is an unpack-and-execute version of Skype on their site - that one does not need any preinstalled stuff i think (its the one with the bz2 extension).

---

### Post by mlnease on 2010-11-08
> **sikander3786 said:**
> The error messages might reveal something informative. It would be better if you can post the output of both of the above mentioned commands.

One by one, select the output of both your commands after pasting them and use the code tags # from the post menu to format it accordingly.
```
mn@mn-OptiPlex-GX270:~$ sudo apt-get install -f
[sudo] password for mn: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mn@mn-OptiPlex-GX270:~$
``````
mn@mn-OptiPlex-GX270:~$ sudo dpkg --configure -a
[sudo] password for mn: 
mn@mn-OptiPlex-GX270:~$
``````
mn@mn-OptiPlex-GX270:~$ sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 skype : Depends: libqt4-network (>= 4:4.5.3) but it is not installable
E: Broken packages
mn@mn-OptiPlex-GX270:~$
```

Thanks again.

---

### Post by sikander3786 on 2010-11-08
There are no error messages at all with those commands. Only the dependecy problem when installing skype.

Did you see **gradinaruvasile's** post. It is worth a try.

Side Note: aptitude is not present in maverick by default. You can install it by

```
sudo apt-get install aptitude
```

or just use apt-get. But I find aptitude better at dependencies when I run into problems like those so it is worth a try.

You can also try

```
sudo aptitude install skype
```

and see if it helps.

---

### Post by mlnease on 2010-11-08
> **sikander3786 said:**
> There are no error messages at all with those commands. Only the dependecy problem when installing skype.

Did you see **gradinaruvasile's** post. It is worth a try.

Yes, I'm downloading it now, thanks.

> **sikander3786 said:**
> Side Note: aptitude is not present in maverick by default. You can install it by

```
sudo apt-get install aptitude
```or just use apt-get. But I find aptitude better at dependencies when I run into problems like those so it is worth a try.

You can also try

```
sudo aptitude install skype
```and see if it helps.

I'll do that while I'm waiting for the download and let you know how it works out:
More errors:
```
mn@mn-OptiPlex-GX270:~$ sudo apt-get install aptitude
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package aptitude is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'aptitude' has no installation candidate
mn@mn-OptiPlex-GX270:~$
```

---

### Post by mlnease on 2010-11-08
Thanks for this--

> **gradinaruvasile said:**
> Just uninstall skype with aptitude first. Then download the Skype from the site and try to install it with the graphical installer (it pulls dependencies too).
Also there is an unpack-and-execute version of Skype on their site - that one does not need any preinstalled stuff i think (its the one with the bz2 extension).

I only found a .deb file for Ubuntu 8.10, downloaded it and tried installing it with gdebi.  Got the attached error.

Thanks again for your help.

---

### Post by jtarin on 2010-11-08
Make sure you have the correct sources entered and uncomented in your /etc/apt/sources.list.....I don't know all for Skype but I would at least make sure of ```
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner
```

---

### Post by HarrisonNapper on 2010-11-08
post the output of
```
uname -a
```

---

### Post by pWnpDl on 2010-11-08
Hi

I have a similar problem. I am a new convert to ubuntu and loving the experience, but I could not get skype to install. I have a 64 bit intel i3 processor. When i run the .deb file to install skype, it says "wrong architecture amd 64". I had no problem installing and running skype with my older 32 bit machine. Will appreciate  any help in this regards. 

Thanks

---

### Post by mlnease on 2010-11-08
> **jtarin said:**
> Make sure you have the correct sources entered and uncomented in your /etc/apt/sources.list.....I don't know all for Skype but I would at least make sure of ```
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner
```
Thanks, jtarin--yes, both are in 
```
 /etc/apt/sources.list
```and uncommented.

---

### Post by mlnease on 2010-11-08
> **HarrisonNapper said:**
> post the output of
```
uname -a
```
```
mn@mn-OptiPlex-GX270:~$ uname -a
Linux mn-OptiPlex-GX270 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 i686 GNU/Linux
mn@mn-OptiPlex-GX270:~$
```

---

### Post by jtarin on 2010-11-08
[Check "Backports" then.]("https://help.ubuntu.com/community/UbuntuBackports")

---

### Post by mlnease on 2010-11-08
> **jtarin said:**
> [Check "Backports" then.]("https://help.ubuntu.com/community/UbuntuBackports")
Here are the backports at [I]/etc/apt/sources.list:
[/I]```
deb http://fi.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
deb-src http://fi.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
deb http://archive.canonical.com/ubuntu maverick-backports partner
deb-src http://archive.canonical.com/ubuntu maverick-backports partner
```Is this what you had in mind?
Thanks again.

---

### Post by beew on 2010-11-08
What error message did you get if you try to install libqt4-network? It probably depends on something else in an older version than the newest version of that something in your repo.

---

### Post by jtarin on 2010-11-08
> **beew said:**
> What error message did you get if you try to install libqt4-network? It probably depends on something else in an older version than the newest version of that something in your repo.
Good possibility!

---

### Post by mlnease on 2010-11-08
> **beew said:**
> What error message did you get if you try to install libqt4-network? It probably depends on something else in an older version than the newest version of that something in your repo.
Sorry, thought I had already posted this:
```
mn@mn-OptiPlex-GX270:~$ sudo apt-get install libqt4-network
[sudo] password for mn: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libqt4-network is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libqt4-network' has no installation candidate
mn@mn-OptiPlex-GX270:~$
```

---

### Post by beew on 2010-11-08
libqt-network should be in the main repository. Do you see it in Synaptic? If you do, what version is that? 

[URL="http://packages.ubuntu.com/maverick/i386/libqt4-network/download"]http://packages.ubuntu.com/maverick/i386/libqt4-network/download
 [/URL]

---

### Post by mlnease on 2010-11-08
> **beew said:**
> libqt-network should be in the main repository. Do you see it in Synaptic? If you do, what version is that? 

[URL="http://packages.ubuntu.com/maverick/i386/libqt4-network/download"]http://packages.ubuntu.com/maverick/i386/libqt4-network/download
 [/URL]
Nada.

---

### Post by mlnease on 2010-11-08
> **beew said:**
> libqt-network should be in the main repository. Do you see it in Synaptic? If you do, what version is that? 

[URL="http://packages.ubuntu.com/maverick/i386/libqt4-network/download"]http://packages.ubuntu.com/maverick/i386/libqt4-network/download
 [/URL]
The Ubuntu download page advises, "If you are running Ubuntu, it is strongly suggested to use a package manager like [aptitude]("http://packages.ubuntu.com/maverick/aptitude") or [synaptic]("http://packages.ubuntu.com/maverick/synaptic") to download and install packages, instead of doing so manually via this website."
Should I try downloading and installing it anyway?

---

### Post by mlnease on 2010-11-08
> **beew said:**
> libqt-network should be in the main repository. Do you see it in Synaptic? If you do, what version is that? 

[URL="http://packages.ubuntu.com/maverick/i386/libqt4-network/download"]http://packages.ubuntu.com/maverick/i386/libqt4-network/download
 [/URL]
OK--went to [http://packages.ubuntu.com/maverick/i386/libqt4-network/download](http://packages.ubuntu.com/maverick/i386/libqt4-network/download), downloaded the .deb, opened it with gdebi and received this error message.
Thanks again, all.

---

### Post by beew on 2010-11-08
That's weird. I just installed (I mean right now) Skype in  10.10  as easy as a piece of  cake.  It may sound dumb, but did you enable the main  repository? I notice you can't install aptitude either. 

BTW. I am running Maverick 32-bit and I am not sure if that is relevant.

---

### Post by mlnease on 2010-11-08
Hi beew,

> **beew said:**
> That's weird. I just installed (I mean right now) Skype in  10.10  as easy as a piece of  cake.  It may sound dumb, but did you enable the main  repository? I notice you can't install aptitude either. 

BTW. I am running Maverick 32-bit and I am not sure if that is relevant.
Here are my (Other Software) repos.  See anything missing?

Also, I installed skype on day one in 32bit Maverick too.  I completely uninstalled it while troubleshooting some (still persistent) connection problems and haven't been able to REinstall it.

Thanks again for your time.

---

### Post by beew on 2010-11-08
Hi,

Your screenshot shows the tab "other software", but did you check all the boxes on the tab 'Ubuntu software"? Also you have a few Lucid ppas, you may want to disable (uncheck) those and reload, they may cause weird dependency problems.

---

### Post by mlnease on 2010-11-08
> **beew said:**
> Hi,

Your screenshot shows the tab "other software", but did you check all the boxes on the tab 'Ubuntu software"? Also you have a few Lucid ppas, you may want to disable (uncheck) those and reload, they may cause weird dependency problems.
OK, here are the Ubuntu repos.  The Lucids are, I think, for things that aren't in the Maverick repos yet but I'll try unchecking them and see what happens.

I'll be away for the rest of the evening (GMT-eight) but thanks a million (everyone) for all the help and I'll check in again first thing tomorrow.

---

### Post by mlnease on 2010-11-09
> **mlnease said:**
> OK, here are the Ubuntu repos.  The Lucids are, I think, for things that aren't in the Maverick repos yet but I'll try unchecking them and see what happens.

I'll be away for the rest of the evening (GMT-eight) but thanks a million (everyone) for all the help and I'll check in again first thing tomorrow.

I've finally solved all the above problems.  I think I know how but I AM  A COMPLETE BEGINNER so if you find this thread and seem to have a  similar problem, *try this **at your own risk _[COLOR=black]only[/COLOR]_***.

At some point in trying to resolve the various unmet dependencies, the terminal suggested
```
The following actions will resolve these dependencies:

     Downgrade the following packages:                                     
1)     libqt4-xml [4:4.7.0-0ubuntu4.1 (now) -> 4:4.7.0-0ubuntu4 (maverick)]
2)     libqtcore4 [4:4.7.0-0ubuntu4.1 (now) -> 4:4.7.0-0ubuntu4 (maverick)]
```I accepted and after first installing aptitude then running
```
sudo aptitude update && sudo aptitude full-upgrade
```I was able to install Skype from the repos and all is well.

Thanks again all for your assistance.

mike

---

### Post by matus71 on 2010-11-14
I had the same problem with installing SKYPE.

I found "strange" solution... [http://ubuntuforums.org/archive/index.php/t-1538605.html](http://ubuntuforums.org/archive/index.php/t-1538605.html)

[I]sudo dpkg -P --force-all libqt4-dbus libqt4-network libqt4-script  libqt4-sql libqt4-sql-mysql libqt4-svg libqt4-xml libqtcore4 libqtgui4

sudo apt-get -f install[/I] [I]

sudo apt-get install skype[/I]

---

