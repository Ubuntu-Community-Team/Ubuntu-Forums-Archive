---
title: "How to install gnome 3 on ubuntu 10.10"
date: 2011-04-11
forum: New to Ubuntu
---

### Post by robro on 2011-04-11
Hello community,
I heard that gnome 3 just got released and figured to look at some screenshots of it and see how it looked... needless to say I loved it :lol: and I am wondering if there is a way to install it in ubuntu 10.10, preferably alongside gnome 2 if possible.

Thanks for the help :)

---

### Post by Kururu Souchou on 2011-04-11
Help me too! I'm very interested in this interface; I'll be also doing some research for my Science Fair Project.

---

### Post by Kururu Souchou on 2011-04-11
> **Kururu Souchou said:**
> Help me too! I'm very interested in this interface; I'll be also doing some research for my Science Fair Project.

I also heard about the Unity interface, what's about it?

---

### Post by robro on 2011-04-11
> **Kururu Souchou said:**
> I also heard about the Unity interface, what's about it?
Its the netbook version of ubuntu, I believe you can install it (using the terminal Applications>accessories>terminal) by using ```
sudo apt-get install unity
```but i'm not sure :)

---

### Post by wolfen69 on 2011-04-11
> **robro said:**
> **Its the netbook version of ubuntu**, I believe you can install it (using the terminal Applications>accessories>terminal) by using ```
sudo apt-get install unity
```but i'm not sure :)

Unity is NOT the netbook version of ubuntu. It will be the default desktop environment on ubuntu starting with the release of 11.04 in about 2 weeks.

Gnome 3 is a whole other matter, and it is advised that you install 11.04 first, add the gnome3 ppa, then upgrade to it. [http://unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1625-how-to-install-gnome3-in-ubuntu-1104-natty-via-ppa](http://unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1625-how-to-install-gnome3-in-ubuntu-1104-natty-via-ppa)

I've heard of problems going from unity to gnome 3, so I went from xubuntu 11.04 and then added gnome 3. Do this only if you are comfortable with possible breakage, as 11.04 is not even released yet, and gnome 3 is in it's infancy.

---

### Post by jhargis1012 on 2011-04-11
^^ Question: will the above solution work in Ubuntu 10.04?

---

### Post by robro on 2011-04-11
> **wolfen69 said:**
> Unity is NOT the netbook version of ubuntu. It will be the default desktop environment on ubuntu starting with the release of 11.04 in about 2 weeks. 

I forgot that unity is going to come preinstalled with 11.04 :lol:


> **wolfen69 said:**
>  Gnome 3 is a whole other matter, and it is advised that you install 11.04 first, add the gnome3 ppa, then upgrade to it. [http://unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1625-how-to-install-gnome3-in-ubuntu-1104-natty-via-ppa](http://unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1625-how-to-install-gnome3-in-ubuntu-1104-natty-via-ppa)

I've heard of problems going from unity to gnome 3, so I went from  xubuntu 11.04 and then added gnome 3. Do this only if you are  comfortable with possible breakage, as 11.04 is not even released yet,  and gnome 3 is in it's infancy.

but I dont want 11.04 as I dont have the mb's to download it nether do I have a spare partition I can use, so I hope theres another another way other than having 11.04 installed. (and I don't care about breakage as I'm fixing to have my whole computer backed up)

---

### Post by wolfen69 on 2011-04-12
> **jhargis1012 said:**
> ^^ Question: will the above solution work in Ubuntu 10.04?

No.

---

### Post by wolfen69 on 2011-04-12
> **robro said:**
> I forgot that unity is going to come preinstalled with 11.04 :lol:




but I dont want 11.04 as I dont have the mb's to download it nether do I have a spare partition I can use, so I hope theres another another way other than having 11.04 installed. (and I don't care about breakage as I'm fixing to have my whole computer backed up)

You could always order a cd when 11.04 is released. [http://www.linuxcd.org/?ref=distrowatch](http://www.linuxcd.org/?ref=distrowatch)
ubuntu is only $1.75 U.S.

---

### Post by oklokl on 2011-04-12
$ sudo add-apt-repository ppa:gnome3-team/gnome3
$ sudo apt-get update
$ sudo apt-get dist-upgrade
$ sudo apt-get install gnome-shell

[http://deviantcj.tistory.com/158](http://deviantcj.tistory.com/158)

---

### Post by Dragonfly_X on 2011-04-12
The instructions by @oklokl will do the trick but not sure about 10.10 as I have it running on 11.04.

Be warned though that this is bleeding edge stuff so there are bound to be bugs

---

### Post by oklokl on 2011-04-12
From 10.10. Bug does not occur
insall Normal. 

11.04 beta bug part occurrences. 

Question person 10.10 referring

---

### Post by Kururu Souchou on 2011-04-12
> **wolfen69 said:**
> Unity is NOT the netbook version of ubuntu. It will be the default desktop environment on ubuntu starting with the release of 11.04 in about 2 weeks.

Gnome 3 is a whole other matter, and it is advised that you install 11.04 first, add the gnome3 ppa, then upgrade to it. [http://unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1625-how-to-install-gnome3-in-ubuntu-1104-natty-via-ppa](http://unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1625-how-to-install-gnome3-in-ubuntu-1104-natty-via-ppa)
.
Can you install it separetely, like installing kde sepeartely?

---

### Post by Kururu Souchou on 2011-04-12
> **wolfen69 said:**
> Unity is NOT the netbook version of ubuntu. It will be the default desktop environment on ubuntu starting with the release of 11.04 in about 2 weeks.

Gnome 3 is a whole other matter, and it is advised that you install 11.04 first, add the gnome3 ppa, then upgrade to it. [http://unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1625-how-to-install-gnome3-in-ubuntu-1104-natty-via-ppa](http://unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1625-how-to-install-gnome3-in-ubuntu-1104-natty-via-ppa)

I've heard of problems going from unity to gnome 3, so I went from xubuntu 11.04 and then added gnome 3. Do this only if you are comfortable with possible breakage, as 11.04 is not even released yet, and gnome 3 is in it's infancy.
As I see on the tutorial posted, it looks like gnome3 is using the old-fashioned windows window borders. Is this the full version of gnome3?

---

### Post by Kururu Souchou on 2011-04-13
Never Mind, go to this site, it works!!!
[http://www.wiredrevolution.com/ubuntu/install-gnome-shell-in-ubuntu-10-10-maverick](http://www.wiredrevolution.com/ubuntu/install-gnome-shell-in-ubuntu-10-10-maverick)
using the compile method

---

### Post by robro on 2011-04-13
> **Kururu Souchou said:**
> Never Mind, go to this site, it works!!!
[http://www.wiredrevolution.com/ubuntu/install-gnome-shell-in-ubuntu-10-10-maverick](http://www.wiredrevolution.com/ubuntu/install-gnome-shell-in-ubuntu-10-10-maverick)
using the compile method
 
Thanks now I know how to actually **enable** gnome 3 :D

---

### Post by bmbaker on 2011-04-14
if you just want you to try it out without breaking your machine, or if you don't want to upgrade to 11.04 then this is the best way i have found so far;

[http://www.webupd8.org/2010/10/install-gnome-shell-from-git-in-ubuntu.html](http://www.webupd8.org/2010/10/install-gnome-shell-from-git-in-ubuntu.html)

---

### Post by pressko on 2011-04-15
Hi guys ,

So ... is it fine to install gnome 3 (aka. shell) on my ubuntu 10.10 ? Will it break my theme, programs or settings ? And  finally is it worth it ?

Gratz, 

Pressko :popcorn:

---

### Post by Paqman on 2011-04-15
> **pressko said:**
> Will it break my theme, programs or settings ?

If you're worried, create a new account and try it using that.

---

### Post by __Ryan__ on 2011-04-15
> **pressko said:**
> Hi guys ,

So ... is it fine to install gnome 3 (aka. shell) on my ubuntu 10.10 ? Will it break my theme, programs or settings ? And  finally is it worth it ?

Gratz, 

Pressko :popcorn:

You will be fine installing it in 10.10, it will not break your current GNOME 2 installation. You will simply be installing the new packages for GNOME 3 along side the older ones.

I have been testing the latest GNOME 3 in 10.10 for weeks with these steps. I am able to go back and forth between GNOME 2/3 without any issue.
[http://www.wiredrevolution.com/ubuntu/install-gnome-shell-in-ubuntu-10-10-maverick]("http://www.wiredrevolution.com/ubuntu/install-gnome-shell-in-ubuntu-10-10-maverick")

Good Luck!

---

### Post by pressko on 2011-04-15
10x a lot man :)) 

I'm gonna try this right now .. for further questions stay alert :P


This process is taking over an hour and a half .... Oo 
The slowest installation i have ever seen :O

---

### Post by velt on 2011-04-16
What I have read is that gnome 3 is supposed to work on ubuntu 11, is that right?
So why installing it on ubuntu 10x?

They also say that gnome 3 is in its infancy and prone to bugs. So maybe we should wait for ubuntu 11 just to be safe?

---

### Post by pressko on 2011-04-16
> **velt said:**
> What I have read is that gnome 3 is supposed to work on ubuntu 11, is that right?
So why installing it on ubuntu 10x?

They also say that gnome 3 is in its infancy and prone to bugs. So maybe we should wait for ubuntu 11 just to be safe?



Yeah , I got that on the hard way :(

---

### Post by velt on 2011-04-16
> **pressko said:**
> Yeah , I got that on the hard way :(

have problems with ubuntu 11 or gnome 3? or maybe both...

when is ubuntu 11 going to be ready?

---

### Post by dniMretsaM on 2011-04-16
I think the release date is April 28.

---

### Post by oklokl on 2011-04-16
Unstable
It is true

(GUI) and ubuntu 11.04 1~2 beta

**ubuntu 10.10 -> windows xp.. **
It is similar to
Feel

gnome 3
 No problem
Is trustworthy

---

### Post by Rushyang on 2011-04-16
There is a difference between gnome-shell (which is being discussed here) and gnome3... Yes, they are little similar, but I'm saying this because guy here asked how to install GNOME3.

---

### Post by velt on 2011-04-16
> **oklokl said:**
> Unstable
It is true

(GUI) and ubuntu 11.04 1~2 beta

**ubuntu 10.10 -> windows xp.. **
It is similar to
Feel

gnome 3
 No problem
Is trustworthy


Thats a shame, looks so nice. Also I kind of dont like the look an feel of unity on ubuntu 10. I mean, on firefox the up menu and lower menu takes up a lot of space.

---

### Post by richlyn9 on 2011-06-06
hey people!!
I intend to install Gnome 3 on My Ubuntu 10.04 LTS and have found these instructions by googling around a bit.

need to verify if this is fine and will not break anything.

[B]1) Install Dependencies
Run this command to install the GNOME Shell dependencies.
$ sudo apt-get install curl libtiff4-dev libgstreamer0.10-dev libcroco3-dev xulrunner-dev mesa-utils mesa-common-dev libreadline5-dev libgl1-mesa-dev libwnck-dev librsvg2-dev libgnome-desktop-dev libgnome-menu-dev libffi-dev libgtk2.0-dev libgconf2-dev libdbus-glib-1-dev gtk-doc-tools gnome-common git-core flex bison automake build-essential icon-naming-utils autopoint libvorbis-dev libpam-dev libgcrypt-dev libtasn1-dev libtasn1-3-bin libgnome-keyring-dev libupower-glib-dev libxklavier16 libxklavier-dev xserver-xephyr python-dev libpulse-dev libjasper-dev jhbuild libgtop2-dev libsqlite3-dev libproxy-dev libdb-dev libproxy-dev libcups2-dev libusb-1.0-0-dev
2) Download the Source
Get the script to setup your jhbuild environment.
$ wget [http://git.gnome.org/browse/gnome-shell/plain/tools/build/gnome-shell-build-setup.sh](http://git.gnome.org/browse/gnome-shell/plain/tools/build/gnome-shell-build-setup.sh)
Make the script executable.
$ chmod +x gnome-shell-build-setup.sh
Execute the script. This will install jhbuild.
$ ./gnome-shell-build-setup.sh
3) Build GNOME 3
This command will download the latest source code and build GNOME 3. GNOME Shell includes 40+ packages that need to be downloaded and built. This can take a significant amount of time to complete so be patient.
$ jhbuild build
4) Keep GNOME 3 Up to Date
You are running the bleeding edge version of GNOME 3 and because of this the code in the git repositories will be constantly changing. To test the latest changes after your initial insallation simply run the following command. This automatically update your local copy of the source code and rebuild if there are any changes to GNOME 3 package or its dependencies.
$ jhbuild build
Starting GNOME Shell
Alt+F2 and enter:
$ ~/gnome-shell/install/bin/gnome-shell –-replace
Stopping GNOME Shell
To exit and return to your default Gnome 2 hit Alt+F2 and enter:
debugexit
[/B]

Thanks for your assistance!

---

