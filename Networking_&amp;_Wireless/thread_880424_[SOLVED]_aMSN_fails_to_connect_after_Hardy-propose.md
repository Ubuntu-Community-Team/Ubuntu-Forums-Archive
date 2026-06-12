---
title: "[SOLVED] aMSN fails to connect after Hardy-proposed updates"
date: 2008-08-05
forum: Networking &amp; Wireless
---

### Post by scradock on 2008-08-05
As of a few hours ago aMSN fails to connect to the MS servers. 

At first I thought this might be due to Hardy-proposed updates to two ns libraries (libnspr4-0d and libnss3-1d) but the same failure occurs on a Ubuntu Studio install that has had no updates, and on an Intrepid install.

aMSN starts up at start-up, but hangs at "Logging in..." instead of connecting.

Starting aMSN from a terminal gives no error messages.

Connecting to the same MS Live account using Pigeon as a chat client or Firefox to access Hotmail succeeds - the username/password info is correct.

Has anyone else noticed this?

---

### Post by peakshysteria on 2008-08-05
Same here actually. Not sure why. We prefer Amsn before Pidgin. Anyone have a solution for this?

[[img]http://bildr.no/thumb/235708.jpeg[/img]](http://bildr.no/view/235708)

Checking automatically for a new version via amsn tells us there is a newer bersion (0.97.2) available for download. Checking the [changelog]("http://amsn.sourceforge.net/wiki/tiki-index.php?page=ChangeLog") tells us nothing about the differences from the one we have installed and the new version. It only tells Changes from 0.96 to 0.97!

---

### Post by Merderan on 2008-08-05
I solved this problem with amsn 0.97.2 
I didn't find any .deb package for it but finally i learnt how can i make one for myself :)

---

### Post by mandos on 2008-08-05
same here too. I've tried with autopackage version but he tcl/tk error appeared

---

### Post by Merderan on 2008-08-05
Here is the .deb package : [http://rapidshare.com/files/134979364/amsn_0.97.2-1.deb](http://rapidshare.com/files/134979364/amsn_0.97.2-1.deb)

It's working well :)

---

### Post by mandos on 2008-08-05
thanks. Everything is working now

---

### Post by jonbonjovi on 2008-08-05
i've had the same problem since yesterday! now trying to solve woth this new version you linked....

EDIT: now everything works well! but the anti-aliasing doesn't work!

---

### Post by peakshysteria on 2008-08-05
No solution for us 64 bit users?

---

### Post by mcondecontreras on 2008-08-05
> **Merderan said:**
> I solved this problem with amsn 0.97.2 
I didn't find any .deb package for it but finally i learnt how can i make one for myself :)


Can you explain us how to create a deb package?? or where do you read the info to make it, there are someone that use a 64 bits ditro and the package that you make was in 32 bits.

I appreciate your answer. Tanks.

---

### Post by Merderan on 2008-08-05
I made it with

```
./configure

make deb
```

commands... But i get many errors , and i searched those errors on google and found solutions... I installed a few package with Synaptic...

Actually i forgot which apps i've installed. So i just say , follow the errors and search on google :)

---

### Post by pedrogfrancisco on 2008-08-05
Related bugs:

[scradock's bug report](https://bugs.launchpad.net/ubuntu/+source/amsn/+bug/254847) which has been marked as a duplicate of [bug #243722](https://bugs.launchpad.net/ubuntu/+source/amsn/+bug/243722)

scradock: even marked as duplicate, I've updated your description, since the related library issue is a coincidence.

I've talked to the guy who marked it as a duplicate, he said he was sure it was the same issue. Though I don't agree, he has been following #amsn and as such I'll respect his decision to mark scradock's bug as a duplicate.

---

### Post by scradock on 2008-08-05
> **pedrogfrancisco said:**
> Related bugs:

[scradock's bug report](https://bugs.launchpad.net/ubuntu/+source/amsn/+bug/254847) which has been marked as a duplicate of [bug #243722](https://bugs.launchpad.net/ubuntu/+source/amsn/+bug/243722)

scradock: even marked as duplicate, I've updated your description, since the related library issue is a coincidence.

I've talked to the guy who marked it as a duplicate, he said he was sure it was the same issue. Though I don't agree, he has been following #amsn and as such I'll respect his decision to mark scradock's bug as a duplicate.


Thanks, Pedro - I was inclined to challenge the duplicate status myself, given the timeline! But if it all gets worked out in the end it's OK

Does anyone know if there is a 64-bit deb available?

---

### Post by pedrogfrancisco on 2008-08-05
> Nop, 32 bits here.

--"--"--

Anyway, workaround for aMSN not connecting (only 32 bits I guess, if you find an autopackage with 64 bits, tell me here):

First, an intro:
As some of you might know, there are three versions of Tk, the graphical toolkit of Tcl (you usually know them both by Tcl/Tk): the ugly version, the good version and the beautiful version.

I've only seen in the wild the ugly version and the good version. The beautiful version I've only seen in a screenshot of a guy trying to prove Tk could be beautiful.

Anyway, considering you've {K,X}Ubuntu Hardy Heron 8.04 and you want to update to latest aMSN release:

----UGLY VERSION---- __And also the easiest solution___

* Go [here]("http://www.amsn-project.net/linux-downloads.php")

* Download *aMSN Installer for Tcl/Tk **8.4*** (your home directory might be a good download folder)

* Remove previous aMSN version and be sure tcl is kept:
> sudo apt-get install tcl8.4
sudo aptitude purge amsn

(yes, it's an ugly solution but I still don't know how to tell aptitude that it should mark a package as manually installed -- have to read the man page someday)

* Go to your download folder, do
> chmod +x amsn-0.97.2-1.tcl84.x86.package
(**if** you want, you can do it with point and click, see [here]("http://www.autopackage.org/docs/howto-install/"))

* Do
> ./amsn-0.97.2-1.tcl84.x86.package

It should require your root password, download an AutoPackage base files and GTK frontend and then install aMSN.

Don't forget to watch the installation, the installer tells you new commands to manage programs installed with AutoPackage.



----GOOD VERSION----
Well you only can't use the good version right away because in Ubuntu, the default Tcl/Tk installation is 8.4 . How do I know that? Do:
> ls /etc/alternatives/wish* -l
lrwxrwxrwx 1 root root 16 2008-08-05 16:19 /etc/alternatives/wish -> /usr/bin/wish8.5
lrwxrwxrwx 1 root root 32 2008-08-05 16:20 /etc/alternatives/wish.1 -> /usr/share/man/man1/wish8.5.1.gz



In your case it should be pointing to wish8.4; on mine I've updated it already.

Do > man update-alternatives if you want to know what the hell is /etc/alternatives. The man page also tells you a pretty way that didn't work for me thanks to not reading the man page properly to change the default Tcl/Tk interpreter, which is > sudo update-alternatives --config wish

You should see something like this (once again, mine is already changed to use Tcl/Tk 8.5) :
> $ LC_ALL=C sudo update-alternatives --config 

There are 2 alternatives which provide `wish'.

  Selection    Alternative
-----------------------------------------------
*         1    /usr/bin/wish8.5
 +        2    /usr/bin/wish8.4

Press enter to keep the default[*], or type selection number: 


Press 1 to select Tcl/Tk 8.5 (P.S.: In cause you're wondering, the "LC_ALL=C" before "sudo update-alternatives --config" is to get the messages in English, since I suppose none of you speaks Portuguese, my default OS language ;) ).

Now, the "hard work" is done (I though it was harder because when I did it I edited the symlinks by hand :D):

* Go [here]("http://www.amsn-project.net/linux-downloads.php")

* Download *aMSN Installer for Tcl/Tk **8.5*** (your home directory might be a good download folder)

* Remove previous aMSN version and be sure tcl is kept:
> sudo apt-get install tcl8.5
sudo aptitude purge amsn

(yes, it's an ugly solution but I still don't know how to tell aptitude that it should mark a package as manually installed -- have to read the man page someday)

* Go to your download folder, do
> chmod +x amsn-0.97.2-1.tcl85.x86.package
(**if** you want, you can do it with point and click, see [here]("http://www.autopackage.org/docs/howto-install/"))

* Do
> ./amsn-0.97.2-1.tcl85.x86.package

It should require your root password, download an AutoPackage base files and GTK frontend and then install aMSN.

Don't forget to watch the installation, the installer tells you new commands to manage programs installed with AutoPackage.



Hope you liked it :)

BTW, no I don't know where to get the beautiful version :)

---

### Post by smergs on 2008-08-05
So I just installed ubuntu yesterday and just attempted to install aMSN this morning for the first time.  I'm also having the issue of not being able to connect.  

My question is, if I am patient, will the autoupdate probably be available in the next few days or so?  I appreciate the detailed instructions above on a way to install the latest version, but as an Ubuntu noob (used a year - year and a half ago but now I've forgotten how to do anything through terminal and what not) I'd rather just take the easy road and wait for it to update the easy way.

---

### Post by pedrogfrancisco on 2008-08-05
Glad you liked it ^^

Well the updates will appear. Keep checking Launchpad. We'll keep you posted.

P.S.: if they don't appear, I'll bug someone at #ubuntu at FreeNode :D

**P.S. number 2: Pidgin & Kopete work fine, you can always install those.**

---

### Post by pedrogfrancisco on 2008-08-05
Package is in Intrepid Ibex and its pending approval for Hardy Heron :D

---

### Post by Ben Carlin on 2008-08-05
Argh stupid thing wont connect.. exaclty same problem used to work fine untill last night when I tried it. Stuck on connecting screen. I used 64bit Hardy heron .. hopefully there will be updates to solve this soon as I love this program and have it looking just like the real msn ..in my opinion slightly better!

---

### Post by peakshysteria on 2008-08-05
```
sudo apt-get install amsn
```
gives me:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
amsn is already the newest version.
The following packages were automatically installed and are no longer required:
  lib32ncurses5 lib32gcc1 lib32z1 lib32stdc++6
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Has anyone tried to apt-get autoremove lib32ncurses5 lib32gcc1 lib32z1 lib32stdc++6? Not to familiar with the temrinal so I don't feel to comfortable experimenting with it.

---

### Post by Dalston on 2008-08-05
> **Merderan said:**
> Here is the .deb package : [http://rapidshare.com/files/134979364/amsn_0.97.2-1.deb](http://rapidshare.com/files/134979364/amsn_0.97.2-1.deb)

It's working well :)

Thanks for this, it now works fine.  Whoever started the thread should mark it as solved because theres quite a few threads with the same problem.

---

### Post by scradock on 2008-08-05
> **Dalston said:**
> Thanks for this, it now works fine.  Whoever started the thread should mark it as solved because theres quite a few threads with the same problem.

That's great, but it isn't solved for those of us using 64-bit, so I propose to wait until a 64-bit deb hits the repos....

---

### Post by Dalston on 2008-08-05
Oh sorry didnt realise,  hope you get a 64bit solution soon.

---

### Post by peakshysteria on 2008-08-05
> **scradock said:**
> That's great, but it isn't solved for those of us using 64-bit, so I propose to wait until a 64-bit deb hits the repos....
Agreed. It's not solved for all of us. And this was really one of the two first threads about it. People don't seem to search the forums at all now. That's why we have so many threads on the same issue.


_________________

Tried to install aMSN Installer for Tcl/Tk 8.5
    Distribution independent installer for those who already have Tcl/Tk 8.5 final version from the [[COLOR="Red"]Amsn pages[/COLOR]]("http://www.amsn-project.net/linux-downloads.php"). This is an Autopackage. But I couldn't make it work. Running the autopackage gave me:
> autopackage for "AMSN MSN client"


The installation of this software requires some additional support
code to be installed.

A] If the support code is found in a local directory, it will be used.
   The file containing the support code will be called:

      "autopackage.tar.bz2"

 or

B] If there is an active Internet connection, the support code will be
   downloaded from:

      "http://autopackage.org/downloads/latest/autopackage.tar.bz2"

   Proxy users should ensure the http_proxy environment variable is
   set, otherwise the download may fail.


Selection B --> OK to download and install support code now? (Y/n): y

Attempting download of [http://autopackage.org/downloads/latest/x86_64/autopackage.tar.bz2](http://autopackage.org/downloads/latest/x86_64/autopackage.tar.bz2) ... 

--23:22:02--  [http://autopackage.org/downloads/latest/x86_64/autopackage.tar.bz2](http://autopackage.org/downloads/latest/x86_64/autopackage.tar.bz2)
           => `autopackage.tar.bz2'
Resolving autopackage.org... 130.225.247.90
Connecting to autopackage.org|130.225.247.90|:80... connected.
HTTP request sent, awaiting response... Read error (Connection timed out) in headers.
Retrying.

--23:22:16--  [http://autopackage.org/downloads/latest/x86_64/autopackage.tar.bz2](http://autopackage.org/downloads/latest/x86_64/autopackage.tar.bz2)
  (try: 2) => `autopackage.tar.bz2'
Connecting to autopackage.org|130.225.247.90|:80... connected.
HTTP request sent, awaiting response... Read error (Connection timed out) in headers.
Giving up.

Download failed.


Attempting download of [http://www.wildgardenseed.com/autopackage/latest/x86_64/autopackage.tar.bz2](http://www.wildgardenseed.com/autopackage/latest/x86_64/autopackage.tar.bz2) ... 

--23:22:28--  [http://www.wildgardenseed.com/autopackage/latest/x86_64/autopackage.tar.bz2](http://www.wildgardenseed.com/autopackage/latest/x86_64/autopackage.tar.bz2)
           => `autopackage.tar.bz2'
Resolving [www.wildgardenseed.com](www.wildgardenseed.com)... 209.25.170.201
Connecting to [www.wildgardenseed.com|209.25.170.201|:80](www.wildgardenseed.com|209.25.170.201|:80)... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://www.wildgardenseed.com/autopackage/1.2.5/x86/autopackage.tar.bz2](http://www.wildgardenseed.com/autopackage/1.2.5/x86/autopackage.tar.bz2) [following]
--23:22:29--  [http://www.wildgardenseed.com/autopackage/1.2.5/x86/autopackage.tar.bz2](http://www.wildgardenseed.com/autopackage/1.2.5/x86/autopackage.tar.bz2)
           => `autopackage.tar.bz2'
Reusing existing connection to [www.wildgardenseed.com:80](www.wildgardenseed.com:80).
HTTP request sent, awaiting response... 200 OK
Length: 896,905 (876K) [application/x-tar]

100%[====================================>] 896,905      239.13K/s    ETA 00:00

23:22:33 (238.52 KB/s) - `autopackage.tar.bz2' saved [896905/896905]

Download completed.


.............................................................................................
autopackage/libexec/autosu-tui: error while loading shared libraries: libglib-2.0.so.0: cannot open shared object file: No such file or directory

Press Enter to close this window.

Which of course left me with nothing.

Tried:```
bash amsn-0.97.2-1.tcl85.x86.package
```
Which gave me:
> The installation of this software requires some additional support
code to be installed.

A] If the support code is found in a local directory, it will be used.
   The file containing the support code will be called:

      "autopackage.tar.bz2"

 or

B] If there is an active Internet connection, the support code will be
   downloaded from:

      "http://autopackage.org/downloads/latest/autopackage.tar.bz2"

   Proxy users should ensure the http_proxy environment variable is
   set, otherwise the download may fail.


Selection B --> OK to download and install support code now? (Y/n): y

Attempting download of [http://autopackage.org/downloads/latest/x86_64/autopackage.tar.bz2](http://autopackage.org/downloads/latest/x86_64/autopackage.tar.bz2) ... 

--23:26:50--  [http://autopackage.org/downloads/latest/x86_64/autopackage.tar.bz2](http://autopackage.org/downloads/latest/x86_64/autopackage.tar.bz2)
           => `autopackage.tar.bz2'
Resolving autopackage.org... 130.225.247.90
Connecting to autopackage.org|130.225.247.90|:80... connected.
HTTP request sent, awaiting response... 
Read error (Connection timed out) in headers.
Retrying.

--23:27:03--  [http://autopackage.org/downloads/latest/x86_64/autopackage.tar.bz2](http://autopackage.org/downloads/latest/x86_64/autopackage.tar.bz2)
  (try: 2) => `autopackage.tar.bz2'
Connecting to autopackage.org|130.225.247.90|:80... connected.
HTTP request sent, awaiting response... Read error (Connection timed out) in headers.
Giving up.

Download failed.


Attempting download of [http://www.wildgardenseed.com/autopackage/latest/x86_64/autopackage.tar.bz2](http://www.wildgardenseed.com/autopackage/latest/x86_64/autopackage.tar.bz2) ... 

--23:27:15--  [http://www.wildgardenseed.com/autopackage/latest/x86_64/autopackage.tar.bz2](http://www.wildgardenseed.com/autopackage/latest/x86_64/autopackage.tar.bz2)
           => `autopackage.tar.bz2'
Resolving [www.wildgardenseed.com](www.wildgardenseed.com)... 209.25.170.201
Connecting to [www.wildgardenseed.com|209.25.170.201|:80](www.wildgardenseed.com|209.25.170.201|:80)... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://www.wildgardenseed.com/autopackage/1.2.5/x86/autopackage.tar.bz2](http://www.wildgardenseed.com/autopackage/1.2.5/x86/autopackage.tar.bz2) [following]
--23:27:16--  [http://www.wildgardenseed.com/autopackage/1.2.5/x86/autopackage.tar.bz2](http://www.wildgardenseed.com/autopackage/1.2.5/x86/autopackage.tar.bz2)
           => `autopackage.tar.bz2'
Reusing existing connection to [www.wildgardenseed.com:80](www.wildgardenseed.com:80).
HTTP request sent, awaiting response... 200 OK
Length: 896,905 (876K) [application/x-tar]

100%[====================================>] 896,905      208.76K/s    ETA 00:00

23:27:20 (193.16 KB/s) - `autopackage.tar.bz2' saved [896905/896905]

Download completed.


.............................................................................................
The version of glib needs to be upgraded to version 2.0 or higher.
The autopackage support code could not be installed.

It can be manually downloaded and installed by running the
installation script located in the downloaded archive.


root@peaks-desktop:/home/peaks/Desktop# 
root@peaks-desktop:/home/peaks/Desktop# 

And once again left me with nothing.
I followed [How to install Linux autopackages in 4 easy steps]("http://www.autopackage.org/docs/howto-install/") but still nogo. Anyone made it yet?

---

### Post by pedrogfrancisco on 2008-08-05
Works for me, so I must have that file.

Let's see which package provides it:

```
$ dpkg -S libglib-2.0.so
libglib2.0-0: /usr/lib/libglib-2.0.so.0.1600.4
libglib2.0-0: /usr/lib/libglib-2.0.so.0
libglib2.0-dev: /usr/lib/libglib-2.0.so
```

So a
```
sudo apt-get install libglib2.0-0
```
should fix your problem.

P.S.: [apt-file allows you to know to which package belongs a file *even if it isn't installed on your system* (which dpkg -S can't tell)]("http://wiki.linuxquestions.org/wiki/Apt-file")

---

### Post by peakshysteria on 2008-08-05
Thanks man. But not working for me:
```
sudo apt-get install libglib2.0-0
```
Gives me:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
libglib2.0-0 is already the newest version.
The following packages were automatically installed and are no longer required:
  lib32ncurses5 libsnack2 lib32gcc1 tcltls tcl lib32z1 lib32stdc++6
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
 

---

### Post by pedrogfrancisco on 2008-08-05
> **peakshysteria said:**
> ```
sudo apt-get install amsn
```
You meant apt-get remove right?

> **peakshysteria said:**
> 
gives me:

Has anyone tried to apt-get autoremove lib32ncurses5 lib32gcc1 lib32z1 lib32stdc++6? Not to familiar with the temrinal so I don't feel to comfortable experimenting with it.

Doing:
```
sudo apt-get autoremove
``` is enough

Those packages are dependencies of another package, probably, since aMSN dependencies are these:

```
$ apt-cache showpkg amsn
Dependencies: 
0.97+final-0ubuntu5 - libc6 (2 2.4) libgcc1 (2 1:4.1.1-21) libjpeg62 (0 (null)) libpng12-0 (2 1.2.13-4) libsnack2 (0 (null)) libstdc++6 (2 4.1.1-21) libx11-6 (0 (null)) python (0 (null)) tcl8.5 (0 (null)) tcltls (0 (null)) tk8.5 (0 (null)) xdg-utils (0 (null)) zlib1g (2 1:1.2.3.3.dfsg-1) docker (0 (null)) firefox (16 (null)) iceape (16 (null)) galeon (16 (null)) konqueror (0 (null)) sox (0 (null)) tclsh (0 (null)) wish (0 (null))
```


Do ```
sudo apt-get autoremove
``` and you're ready to go.

---

### Post by peakshysteria on 2008-08-05
I'm not to good with the terminal man. Thanks for guiding me so far. But still no luck.
 ```
sudo apt-get autoremove
```
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  lib32ncurses5 libsnack2 lib32gcc1 tcltls tcl lib32z1 lib32stdc++6
The following packages will be REMOVED:
  lib32gcc1 lib32ncurses5 lib32stdc++6 lib32z1 libsnack2 tcl tcltls
0 upgraded, 0 newly installed, 7 to remove and 0 not upgraded.
After this operation, 3232kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 189370 files and directories currently installed.)
Removing lib32stdc++6 ...
Removing lib32gcc1 ...
Removing lib32ncurses5 ...
Removing lib32z1 ...
Removing libsnack2 ...
Removing tcl ...
Removing tcltls ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place

And:
```
bash amsn-0.97.2-1.tcl85.x86.package
```

> The installation of this software requires some additional support
code to be installed.

A] If the support code is found in a local directory, it will be used.
   The file containing the support code will be called:

      "autopackage.tar.bz2"

 or

B] If there is an active Internet connection, the support code will be
   downloaded from:

      "http://autopackage.org/downloads/latest/autopackage.tar.bz2"

   Proxy users should ensure the http_proxy environment variable is
   set, otherwise the download may fail.


Selection B --> OK to download and install support code now? (Y/n): y

Attempting download of [http://autopackage.org/downloads/latest/x86_64/autopackage.tar.bz2](http://autopackage.org/downloads/latest/x86_64/autopackage.tar.bz2) ... 

--00:16:52--  [http://autopackage.org/downloads/latest/x86_64/autopackage.tar.bz2](http://autopackage.org/downloads/latest/x86_64/autopackage.tar.bz2)
           => `autopackage.tar.bz2'
Resolving autopackage.org... 130.225.247.90
Connecting to autopackage.org|130.225.247.90|:80... connected.
HTTP request sent, awaiting response... Read error (Connection timed out) in headers.
Retrying.

--00:17:05--  [http://autopackage.org/downloads/latest/x86_64/autopackage.tar.bz2](http://autopackage.org/downloads/latest/x86_64/autopackage.tar.bz2)
  (try: 2) => `autopackage.tar.bz2'
Connecting to autopackage.org|130.225.247.90|:80... connected.
HTTP request sent, awaiting response... Read error (Connection timed out) in headers.
Giving up.

Download failed.


Attempting download of [http://www.wildgardenseed.com/autopackage/latest/x86_64/autopackage.tar.bz2](http://www.wildgardenseed.com/autopackage/latest/x86_64/autopackage.tar.bz2) ... 

--00:17:17--  [http://www.wildgardenseed.com/autopackage/latest/x86_64/autopackage.tar.bz2](http://www.wildgardenseed.com/autopackage/latest/x86_64/autopackage.tar.bz2)
           => `autopackage.tar.bz2'
Resolving [www.wildgardenseed.com](www.wildgardenseed.com)... 209.25.170.201
Connecting to [www.wildgardenseed.com|209.25.170.201|:80](www.wildgardenseed.com|209.25.170.201|:80)... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://www.wildgardenseed.com/autopackage/1.2.5/x86/autopackage.tar.bz2](http://www.wildgardenseed.com/autopackage/1.2.5/x86/autopackage.tar.bz2) [following]
--00:17:21--  [http://www.wildgardenseed.com/autopackage/1.2.5/x86/autopackage.tar.bz2](http://www.wildgardenseed.com/autopackage/1.2.5/x86/autopackage.tar.bz2)
           => `autopackage.tar.bz2'
Reusing existing connection to [www.wildgardenseed.com:80](www.wildgardenseed.com:80).
HTTP request sent, awaiting response... 200 OK
Length: 896,905 (876K) [application/x-tar]

100%[====================================>] 896,905      375.53K/s             

00:17:23 (374.37 KB/s) - `autopackage.tar.bz2' saved [896905/896905]

Download completed.


.............................................................................................
The version of glib needs to be upgraded to version 2.0 or higher.
The autopackage support code could not be installed.

It can be manually downloaded and installed by running the
installation script located in the downloaded archive.

Still nothing :confused:

---

### Post by scradock on 2008-08-05
The updated amsn package for 64-bit is now in the Hardy-proposed repo. I have downloaded it and installed without problems. aMSN now connects!!!!

pH: I tried the autopackage route myself - it failed, with nasty-looking stuff being downloaded from god-knows-where. Looked just like a rampant Trojan in Windows - that stuff scares me. Take the ubuntu route, and get the package from the repo.

Marking this thread [Solved].

---

### Post by peakshysteria on 2008-08-05
Hm, nothing hear yet (even though proposed is checked). I'll wait till it turns up. Thanks for telling man.

---

### Post by pedrogfrancisco on 2008-08-05
WTH?

Try
```
sudo apt-get install libglib2.0-dev
```
Though it shouldn't be needed...

---

### Post by pedrogfrancisco on 2008-08-05
```

```> **scradock said:**
> pH: I tried the autopackage route myself - it failed, with nasty-looking stuff being downloaded from god-knows-where. Looked just like a rampant Trojan in Windows - that stuff scares me. Take the ubuntu route, and get the package from the repo.

ROFL fair enough. If you want to clean your system:

```
$ sudo package list
amsn: AMSN MSN client
autopackage-gtk: Relação De Usuário Gráfica De Autopackage GTK+

```

and remove all installed, e.g.
> sudo package remove amsn
sudo package remove autopackage-gtk

and finally remove autopackage itself:
```
sudo package remove autopackage
```

---

### Post by tuxxy on 2008-08-05
I just had to compile from source also, after installing tcl/tk 8.5 it seems I could not simply ./configure as normal, I had to state the path also see below

```
./configure --with-tcl=/usr/lib/tcl8.5 --with-tk=/usr/lib/tk8.5
```

---

### Post by kahram.yoon on 2008-08-05
> **scradock said:**
> The updated amsn package for 64-bit is now in the Hardy-proposed repo. I have downloaded it and installed without problems. aMSN now connects!!!!

pH: I tried the autopackage route myself - it failed, with nasty-looking stuff being downloaded from god-knows-where. Looked just like a rampant Trojan in Windows - that stuff scares me. Take the ubuntu route, and get the package from the repo.

Marking this thread [Solved].

What is hardy-proposed repo?  Where can i get it?  Sorry cuz I am an extreme noob to ubuntu and need help.  Need the 64 bit aMSN package.

---

### Post by peakshysteria on 2008-08-05
> **pedrogfrancisco said:**
> WTH?

Try
```
sudo apt-get install libglib2.0-dev
```
Though it shouldn't be needed...
```
sudo apt-get install libglib2.0-dev
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libglib2.0-dev is already the newest version.
libglib2.0-dev set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
:confused:

---

### Post by peakshysteria on 2008-08-05
> **kahram.yoon said:**
> What is hardy-proposed repo?  Where can i get it?  Sorry cuz I am an extreme noob to ubuntu and need help.  Need the 64 bit aMSN package.

System --> Aministration --> Software sources --> Updates --> Check hardy-proposed

---

### Post by zero_tolerance on 2008-08-05
managed to install 0.97.2 on a 64-bit by compiling from source (cause hardy-proposed still doesnt have it)

but i lost anti-aliasing!!!!

any help?

---

### Post by peakshysteria on 2008-08-06
Got an hardy-proposed update prompt just now. It's back. Yay... :popcorn:

---

### Post by Adri2000 on 2008-08-06
Hi,

As mentioned in a previous post, this issue is tracked in [https://bugs.launchpad.net/ubuntu/+source/amsn/+bug/243722](https://bugs.launchpad.net/ubuntu/+source/amsn/+bug/243722) and a fix is already available in hardy-proposed.
Please test the hardy-proposed package and provide feedback in this bug report so that it can then go to hardy-updates.

Also, is anyone experiencing this bug using gutsy, feisty or dapper?

Thanks.

---

### Post by Zeckman on 2008-08-06
thanks for the info.. was wondering why I couldn't connect since yesterday

cheers :)

---

### Post by claschxtreme on 2008-08-06
Installed the package in the link and i can connect now, but the fonts are too small and unreadable, i tried the autopackage but and the installation went fine but it didn't work. I tried to compile the source myself but i'm getting a lot of errors, it's not working for me yet.

---

### Post by Adri2000 on 2008-08-06
> **claschxtreme said:**
> Installed the package in the link and i can connect now, but the fonts are too small and unreadable, i tried the autopackage but and the installation went fine but it didn't work. I tried to compile the source myself but i'm getting a lot of errors, it's not working for me yet.

Try the package from the hardy-proposed repository, as I said two posts above.

---

### Post by pedrogfrancisco on 2008-08-06
> **peakshysteria said:**
> ```
sudo apt-get install libglib2.0-dev
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libglib2.0-dev is already the newest version.
libglib2.0-dev set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
:confused:

LOL ok forget autopackage then, it really doesn't seem to work on your system, weird.

Follow last line's instructions.



[QUOTE=zero_tolerance]
managed to install 0.97.2 on a 64-bit by compiling from source (cause hardy-proposed still doesnt have it)

but i lost anti-aliasing!!!!

any help?[/QUOTE]

Most certainly you compiled against Tcl/Tk 8.4 which, at least on Ubuntu, doesn't have anti-aliasing (I'm not aware if it's a compilation option or if it truly doesn't support anti-aliasing).

Enable hardy-proposed **but** remove any manually installed version **first**.

Then, follow last line's instructions.







_***EVERYONE:***_
[Here is how to enable {Ubuntu version}-proposed, aka hardy-proposed for most of you.]("https://wiki.ubuntu.com/Testing/EnableProposed")

Don't forget to add/edit the file **/etc/apt/preferences** as mentioned in the wiki, otherwise you'll end up testing ALL hardy-proposed packages instead of just the one you want, which is aMSN.

Finally, do:

```

sudo aptitude -t hardy-proposed install amsn

```
(as you might have guessed, the *-t hardy-proposed* indicates that that particular package is to be downloaded from that category, hardy-proposed).

---

### Post by pedrogfrancisco on 2008-08-06
BTW, aMSN from hardy-proposed working fine here, Adri2000 :)

---

### Post by jordilin on 2008-08-06
64 bit not solved yet. I have the same problem

---

### Post by pedrogfrancisco on 2008-08-06
> **jordilin said:**
> 64 bit not solved yet. I have the same problem

Please, check installed version. MUST be similar to this one:

```
$ LC_ALL=C aptitude show amsn
Package: amsn
New: yes
State: installed
Automatically installed: yes
Version: 0.97+final-0ubuntu5**.1**

```

Do note the final **.1**

---

### Post by scradock on 2008-08-06
The update for Intrepid is now available in the Intrepid repo; you will need to REMOVE amsn first, because the new version has some routines in another package, amsn-data, that conflict with the routines in the earlier amsn package. If you try to install that with the old version of amsn installed it will fail.

so, using your front-end of choice:

1) remove amsn;
2) install amsn-data;
3) re-install amsn.

For me, it works using 64-bit Intrepid; also the Hardy-proposed version works in 8.04.

Thanks, everyone for the updates!

---

### Post by slumbergod on 2008-08-06
I used the script provided on this website:
[http://nstasino-ubuntulog.blogspot.com/2008/08/fix-ugly-fonts-in-amsn-0972.html](http://nstasino-ubuntulog.blogspot.com/2008/08/fix-ugly-fonts-in-amsn-0972.html)

It worked perfectly for me...aMSN 0.97.2 with aliased fonts and it connects correctly! 

Xubuntu (32bit Inel)

---

### Post by Mirak PT on 2008-08-06
> **Merderan said:**
> Here is the .deb package : [http://rapidshare.com/files/134979364/amsn_0.97.2-1.deb](http://rapidshare.com/files/134979364/amsn_0.97.2-1.deb)

It's working well :)

Merderan,

Thank you. It worked pretty well. 5:KS

Mirak Pt


[I]
Want to earn some extra money? Check out this[/I]: [bux.to]("http://bux.to/?r=Mirak_PT")

---

### Post by Cool2 on 2008-08-06
Hardy-proposed worked for me too. 64-bit user. Didn't uninstall the previous version. Just updated.

---

### Post by peakshysteria on 2008-08-06
Second that. All is good now :popcorn:

---

### Post by Adri2000 on 2008-08-06
> **scradock said:**
> The update for Intrepid is now available in the Intrepid repo; you will need to REMOVE amsn first, because the new version has some routines in another package, amsn-data, that conflict with the routines in the earlier amsn package. If you try to install that with the old version of amsn installed it will fail.

so, using your front-end of choice:

1) remove amsn;
2) install amsn-data;
3) re-install amsn.

For me, it works using 64-bit Intrepid; also the Hardy-proposed version works in 8.04.

Thanks, everyone for the updates!

The conflict when upgrading is reported: [https://bugs.launchpad.net/ubuntu/+source/amsn/+bug/255437](https://bugs.launchpad.net/ubuntu/+source/amsn/+bug/255437)

---

### Post by Raval on 2008-08-09
Same problem here :(

---

### Post by Adri2000 on 2008-08-09
> **Raval said:**
> Same problem here :(

What problem?

The login issue is (should be) fixed in intrepid, hardy-proposed, gutsy-proposed, feisty-proposed and dapper-proposed. (Please report your -proposed testing results in the bug report [0].)
The conflicting files problem when upgrading intrepid is also fixed now.

[0] [https://bugs.launchpad.net/ubuntu/+source/amsn/+bug/243722](https://bugs.launchpad.net/ubuntu/+source/amsn/+bug/243722)

---

### Post by TechnoTech on 2008-08-11
amsn 0.97.2 is working now after many many installs and compiles on x64.

compiled amsn from source.
compiled tls from source.
compiled openssl from source.

after all that i was still getting the pop-up for TLS install.

issue corrected after editing "~.amsn/plugins/tls1.50/pkgIndex.tcl"

changed "ifneeded tls 1.50"  to "ifneeded tls 1.5"

amsn now connects.

---

### Post by scradock on 2008-08-11
Is anyone getting successful retrieval of hotmail through aMSN? Before the recent protocol changes my hotlog would go straight through to logged-in status; now it dumps me at "incorrect password login" and I have to re-enter my password to get into hotmail.

I've tried deleting hotlog.htm, but that didn't fix the problem.

Any ideas, anyone?

---

### Post by mbocciab on 2008-08-13
Hardy-proposed version works also for me on amd64.
Thanks

---

### Post by amac777 on 2008-08-14
> **pedrogfrancisco said:**
> Most certainly you compiled against Tcl/Tk 8.4 which, at least on Ubuntu, doesn't have anti-aliasing (I'm not aware if it's a compilation option or if it truly doesn't support anti-aliasing).

Enable hardy-proposed **but** remove any manually installed version **first**.

Then, follow last line's instructions.

I am still not able to get my anti aliased fonts back. I have two computers: one running feisty, one runny gutsy.

For both, I first enabled the proposed (either feisty-proposed or gutsy-proposed), then I made the etc/apt/preferences file as described above, then I did a 'sudo apt-get update', then I did a 'sudo apt-get remove --purge amsn'. Then I did 'sudo aptitude -t gutsy-proposed install amsn' (or the same command with gutsy changed to fiesty for the other computer).

The result is aMSN now works on both computers, however, the fonts are ugly.

Can somebody tell me what I did wrong? (or what step I missed?)

Thanks!

---

### Post by Adri2000 on 2008-08-14
amac777: as far as I know, the packages from the official repositories have never had anti-aliased fonts.

--

The hardy and feisty fixed packages are now available through -updates (now, modulo the mirror you're using). However, the gutsy and dapper ones still need testing feedback in the bug report I mentioned above. Thanks in advance to anyone who will add a comment to this bug.

---

### Post by peakshysteria on 2008-08-14
Running nicely on Hardy 64 bit and Gutsy 32 bit in my end. Both came as proposed updates.

---

### Post by RandomXcore on 2008-09-07
> **Merderan said:**
> Here is the .deb package : [http://rapidshare.com/files/134979364/amsn_0.97.2-1.deb](http://rapidshare.com/files/134979364/amsn_0.97.2-1.deb)

It's working well :)

yeh it sure is, thanks so much! i havent been able to log on amsn for ages and had to resort to windows live messenger which ****** up my windows lol so yeh im just glad that i can talk again.
sweet <3

---

### Post by SheNux on 2008-10-24
I downloaded the .deb file, and tried to run it with gdebi package installer. It said the the following dependencies weren't satisfiable: zlib1g

I ran terminal and typed sudo apt-get install zlib1g, and it said it was already in the newest version.

Synaptic package manager won't force-update my version (0.96) of aMSN. I'm getting pretty ticked off, because gaim and pidgin are EATING my contact lists. Yes, eating, they're spontaneously deleting my contacts. I don't want to be dependent on meebo, and aMSN worked fine the last time I used it, presumably before the updates.

If it matters, I'm running Feisty Fawn.

---

