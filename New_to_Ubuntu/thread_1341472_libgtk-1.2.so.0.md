---
title: "libgtk-1.2.so.0"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by Exadrid on 2009-11-29
I'm trying to install epsxe but im getting:

> ./epsxe: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory


All i find online is for 64 bit but i am using 32bit karmic. I cant find the package anywhere.

Can someone help?

---

### Post by fooman on 2009-11-29
try opening a terminal and type or copy/paste the following:

```
 sudo apt-get install libgtk1.2
```

see if that installs the missing package.  if not,  then post any errors it produces.

hope that helps.

---

### Post by Exadrid on 2009-11-29
eric@eric-desktop:~$  sudo apt-get install libgtk1.2
[sudo] password for eric: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libgtk1.2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libgtk1.2 has no installation candidate

---

### Post by mc4man on 2009-11-29
If you must then you'll have to get the jaunty packages - 3 in total I think
 ( in this order for install

[http://packages.ubuntu.com/en/jaunty/libgtk1.2-common](http://packages.ubuntu.com/en/jaunty/libgtk1.2-common)

[http://packages.ubuntu.com/en/jaunty/libglib1.2ldbl](http://packages.ubuntu.com/en/jaunty/libglib1.2ldbl)

[http://packages.ubuntu.com/en/jaunty/libgtk1.2](http://packages.ubuntu.com/en/jaunty/libgtk1.2)

---

### Post by Exadrid on 2009-11-29
Thank you so much!

---

### Post by fairbird on 2010-04-03
> If you must then you'll have to get the jaunty packages - 3 in total I think
 ( in this order for install

[http://packages.ubuntu.com/en/jaunty/libgtk1.2-common](http://packages.ubuntu.com/en/jaunty/libgtk1.2-common)

[http://packages.ubuntu.com/en/jaunty/libglib1.2ldbl](http://packages.ubuntu.com/en/jaunty/libglib1.2ldbl)

[http://packages.ubuntu.com/en/jaunty/libgtk1.2](http://packages.ubuntu.com/en/jaunty/libgtk1.2)

i was try to do it but i don't now how ?

because i want to run Dreamup in ubuntu 9.10 

any one help my how to make that packages 

regards

---

### Post by Flos Headford on 2010-09-24
If you click on the links given, from the top down, you get to the page and look for the table: under Architecture, click on "all". You can then save the file.
For the next link, when you get to the page, look for the table under the heading "Download libglib1.2ldbl" and select (presumably) i386, and save the file.
For the third link, when you get to the page, look for the table under the heading "Download libgtk1.2" and click on i386, and save the file.
In the order downloaded, double-click on the saved files: this should start the Gdebi installer (make sure Synaptic isn't running).

My thanks to the contrbutors above - this has enabled me to install and run gsview - the best front-end for Ghostscript I've come across.
Best wishes to one and all,
Phil

---

### Post by Exp HP on 2010-12-01
I don't know if it's because I'm not used to the ubuntu packages site, or if those links are actually broken, but when I try to use those three links, I get a page with the following error:> two or more packages specified (libgtk1.2 jaunty)If you're getting this error message, too, then here's another way you can get the packages.

The packages are in the **jaunty universe** repository. Here's how you can add that repository to your sources in Lucid:

1. Open System >> Administration >> Synaptic Package Manager
2. Go to Settings >> Repositories
3. On the Other Software tab, click Add.
4. Enter the following:```
deb http://archive.ubuntu.com/ubuntu jaunty universe
```5. Close Synaptic

(if you don't have synaptic (i.e. you don't have the desktop), you can modify /etc/apt/sources.list manually in a text editor.  Just add the deb line to the bottom and save.)

Now it should be smooth sailing.
```
sudo apt-get update
sudo apt-get install libgtk1.2
```No more libgtk-1.2.so.0 errors for me!

---

### Post by crash123 on 2010-12-06
I added the jaunty repository and installed libgtk1.2, but I still get the same error message about libgtk-1.2.so.0. libgtk1.2 did install correctly, so I'm not sure what else to do here? I use 64-bit 10.10

---

### Post by muzikayise on 2010-12-07
> **Exp HP said:**
> I don't know if it's because I'm not used to the ubuntu packages site, or if those links are actually broken, but when I try to use those three links, I get a page with the following error:If you're getting this error message, too, then here's another way you can get the packages.

The packages are in the **jaunty universe** repository. Here's how you can add that repository to your sources in Lucid:

1. Open System >> Administration >> Synaptic Package Manager
2. Go to Settings >> Repositories
3. On the Other Software tab, click Add.
4. Enter the following:```
deb http://archive.ubuntu.com/ubuntu jaunty universe
```5. Close Synaptic

(if you don't have synaptic (i.e. you don't have the desktop), you can modify /etc/apt/sources.list manually in a text editor.  Just add the deb line to the bottom and save.)

Now it should be smooth sailing.
```
sudo apt-get update
sudo apt-get install libgtk1.2
```No more libgtk-1.2.so.0 errors for me!


thank you finally i got the right solution.

i am using ubuntu 10.10 and i had a problem with "epsxe
./epsxe: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory"

anyway after following these instructions above i was able to install libgtk1.2 now epsxe is working fine.

thanks again :D

---

### Post by joelstitch on 2011-03-30
> **Exp HP said:**
> I don't know if it's because I'm not used to the ubuntu packages site, or if those links are actually broken, but when I try to use those three links, I get a page with the following error:If you're getting this error message, too, then here's another way you can get the packages.

The packages are in the **jaunty universe** repository. Here's how you can add that repository to your sources in Lucid:

1. Open System >> Administration >> Synaptic Package Manager
2. Go to Settings >> Repositories
3. On the Other Software tab, click Add.
4. Enter the following:```
deb http://archive.ubuntu.com/ubuntu jaunty universe
```5. Close Synaptic

(if you don't have synaptic (i.e. you don't have the desktop), you can modify /etc/apt/sources.list manually in a text editor.  Just add the deb line to the bottom and save.)

Now it should be smooth sailing.
```
sudo apt-get update
sudo apt-get install libgtk1.2
```No more libgtk-1.2.so.0 errors for me!

I am also getting the "_**./epsxe: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory**_
"  error but when I do the last spet on your instructions this is what I get:

> pag@pag-laptop:~$ sudo apt-get install libgtk1.2
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


---

### Post by Rendsvig on 2011-04-12
Adding the Jaunty repository worked for me, too. I could not run LGP Uninstall or remove Shadowgrounds demo.

I got "lgp_uninstall: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory"

Thank you for the help!

**@ joelstitch**

Do you have Synaptic Package Manager running or doing updates or something like that? I think that causes it.

---

### Post by joelstitch on 2011-04-12
> **Rendsvig said:**
> Adding the Jaunty repository worked for me, too. I could not run LGP Uninstall or remove Shadowgrounds demo.

I got "lgp_uninstall: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory"

Thank you for the help!

**@ joelstitch**

Do you have Synaptic Package Manager running or doing updates or something like that? I think that causes it.

Not when Im trying to open the program

---

### Post by arskipaski on 2011-05-31
hmm, it appears that jaunty is gone from [http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/) 

any ideas for an alternative fix?

Thanks!

---

### Post by movin on 2011-06-17
> **arskipaski said:**
> hmm, it appears that jaunty is gone from [http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/) 

any ideas for an alternative fix?

Thanks!

Aye, I'm having the same problem right now. Trying to run equake_1.1.0_rc1-english.run which seems to require libgtk-1.2.so.0

---

### Post by araidian on 2011-07-20
hey guys,

i just wanted to add to this post that you only need debian packages so if you cant fine ubuntu ones any old debian file will work, i got mine from [http://packages.debian.org/search?keywords=libgtk1.2](http://packages.debian.org/search?keywords=libgtk1.2) and used dpkg -i to install them,

i hope this helps someone :)

---

### Post by t0p on 2011-07-21
**araidian:** If you look at my thread [here]("http://ubuntuforums.org/showthread.php?p=11069946#post11069946"), you'll see I also need libgtk-1.2.so.0 in order to get an old game to run on my 10.04 machine (Alien Arena 2006 Gold Edition). I tried to follow your instructions as best as I could understand them, but don't seem to be able to download it.  Any suggestions please?  Am I supposed to add a Debian repo to my sources? If so, which one?  If not, how *do* I get libgtk-1.2.so.0[B]?

Any help gratefully received...
[/B]

---

### Post by zack2006197 on 2011-07-21
Dear Sirs,
 
I installed ubuntu 10.04 LTS i386. I Have a lenovo laptop with broadcom802.11n.
when i use airmon-ng ...i do not find the interface even i am connected to the net ...
The problem that i'm connected to the net through the laptop wireless card and when i open the network connection i found that I have a wired connection ...but i am not using any ethernet cable.
Also i right-click the networkManager applet to display a menu that allows me to turn on/off  networking but i didn't find enable/disable wireless.
 
Please coud you help me.
 
Thanks and best regards
 
zack

---

### Post by Cascara on 2011-09-11
> **Exp HP said:**
> I don't know if it's because I'm not used to the ubuntu packages site, or if those links are actually broken, but when I try to use those three links, I get a page with the following error:If you're getting this error message, too, then here's another way you can get the packages.

The packages are in the **jaunty universe** repository. Here's how you can add that repository to your sources in Lucid:

1. Open System >> Administration >> Synaptic Package Manager
2. Go to Settings >> Repositories
3. On the Other Software tab, click Add.
4. Enter the following:```
deb http://archive.ubuntu.com/ubuntu jaunty universe
```5. Close Synaptic

(if you don't have synaptic (i.e. you don't have the desktop), you can modify /etc/apt/sources.list manually in a text editor.  Just add the deb line to the bottom and save.)

Now it should be smooth sailing.
```
sudo apt-get update
sudo apt-get install libgtk1.2
```No more libgtk-1.2.so.0 errors for me!

Ubuntu does not support Jaunty repos anymore, so to get the repos working you'll need hardy...

Add this sources instead of the jaunty ones:
```
deb http://archive.ubuntu.com/ubuntu hardy universe
```

---

