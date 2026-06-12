---
title: "Are outdated versions useless?"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by garyed on 2009-04-08
I know older versions are not supported but does that mean there's no way to get dependencies or other packages needed on a reinstall or new installation?
I ask this because I need to install csh on my Feisty computer.
Upgrading is out of the question because of hardware limitations.

---

### Post by matrixblue on 2009-04-08
Have you considered using Xubuntu?

---

### Post by LowSky on 2009-04-08
> **matrixblue said:**
> Have you considered using Xubuntu?

Any reason why you think you cannot use a newer version, the requirement have not changed, you never mentioned you actual hardware

Also why C-shell? couldnt you use Bash?

---

### Post by garyed on 2009-04-08
> **LowSky said:**
> Any reason why you think you cannot use a newer version, the requirement have not changed, you never mentioned you actual hardware

Also why C-shell? couldnt you use Bash?

The computer I'm running Feisty on has only got 256 meg ram which is the last Ubuntu OS to have that spec. Hardy requires more.  It boots up slow but it runs fine. Also csh is needed to install my printer. When installing the drivers it says it needs csh to dpkg the deb file.

---

### Post by Bölvaður on 2009-04-08
there are other distros for this type of specs. but ubuntu with tiling window manager will take less than 100mib if you are ready to give up gnome.

---

### Post by garyed on 2009-04-08
> **matrixblue said:**
> Have you considered using Xubuntu?

I've thought of it but I really want to stick with Feisty if I can.
It runs well on the computer & I'm already familiar with it.
I'm just surprised that there isn't an alternative to apt-get, aptitude or synaptic to install dependencies.

---

### Post by ibuclaw on 2009-04-08
All deprecated repositories have been moved to a different subnet of Ubuntu.

```

deb http://old-releases.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-security main restricted universe multiverse 

```

Be sure to update your sources.list accordingly.

Regards
Iain

---

### Post by kidux on 2009-04-08
> **garyed said:**
> I'm just surprised that there isn't an alternative to apt-get, aptitude or synaptic to install dependencies.

Why? This is a major selling point of Ubuntu, the ease of use in installing applications. Many other distros do not include such a package manager.

Also, you might look into packagekit. I haven't used it, but I've heard good things about it.

---

### Post by Temposs on 2009-04-08
> **garyed said:**
> The computer I'm running Feisty on has only got 256 meg ram which is the last Ubuntu OS to have that spec. Hardy requires more.  It boots up slow but it runs fine. Also csh is needed to install my printer. When installing the drivers it says it needs csh to dpkg the deb file.

Hardy's **recommended** requirements are 384MB, but the minimum requirements are only 64MB. You can certainly still run it on that machine:

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by benj1 on 2009-04-08
i agree with temposs.
i managed to install 8.04 on my old pc which has 256mb of ram, so i would try that, as long as youre happy without compiz.

---

### Post by LowSky on 2009-04-08
yeah my old dell inspiron 8100 is running 8.04 on 256MB of RAM and a P3 1Ghz processor, its works just fine using Gnome. Sure installing it was painfully slow but it works.

Also what printer? A newer version of Ubuntu may have better support

---

### Post by garyed on 2009-04-08
Thanks for all the ideas,
Sorry it took so long to get back but I had a hard day at work.
To answer some of the questions.
1 - I love the apt-get but it just wouldn't work on my older distro since its 
outdated. I am going to try updating my sources.list like tinivole suggested & see if that works.

2 - My printer is a Brother MFC-420CN 
The drivers loaded fine on my other Feisty laptop but that was when it was still supported in the repos.

---

### Post by juancarlospaco on 2009-04-09
*I have 6 LTS working and installing software perfectly...*

---

### Post by Sef on 2009-04-09
>  Also what printer? A newer version of Ubuntu may have better support

Almost all [HPs work out of the box]("http://hplipopensource.com/hplip-web/index.html").  

As for outdated versions, they do not receive any updates, so if there is still bad code written, it will not be fixed.

---

### Post by juancarlospaco on 2009-04-09
> **Sef said:**
> 
As for outdated versions, they do not receive any updates

No, 6 Series still with Updates, [check at USN for example.]("http://www.ubuntu.com/usn/usn-755-1")

---

### Post by overdrank on 2009-04-09
> **juancarlospaco said:**
> *I have 6 LTS working and installing software perfectly...*

> **juancarlospaco said:**
> No, 6 Series still with Updates, [check at USN for example.]("http://www.ubuntu.com/usn/usn-755-1")

That is the point, 6.06 Dapper is not outdated. It is long term support. But its support will end soon. :)

---

### Post by fabricator4 on 2009-04-09
> **garyed said:**
> The computer I'm running Feisty on has only got 256 meg ram which is the last Ubuntu OS to have that spec. Hardy requires more.  It boots up slow but it runs fine. Also csh is needed to install my printer. When installing the drivers it says it needs csh to dpkg the deb file.

Firstly, dpkg works fine under bash so the instructions you're using are either badly written, or out of date.  Regardless, you could run csh under Hardy if you wanted to.

Secondly, the memory is only a suggestion, and then I think it's mainly for Gnome.  The _requirement_ is only 64Mb.  You can save close to 100Mb by using something like fluxbox instead of Gnome, however going this light on the GUI isn't for everyone.  Kubuntu seems to have the same "suggested" RAM level but it would be worth trying and see if it results in a smaller swap file.

Chris.

---

### Post by garyed on 2009-04-09
> **tinivole said:**
> All deprecated repositories have been moved to a different subnet of Ubuntu.

```

deb http://old-releases.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-security main restricted universe multiverse 

```

Be sure to update your sources.list accordingly.

Regards
Iain

Well I tried it & edited my sources.list but still got the same error about not being able to find package & it may be obsolete.
Thanks anyways.

---

### Post by Temposs on 2009-04-09
Did you remove the old lines in sources.lst or did you just add the lines that tinviole recommended? You have to delete the old lines as well or, yes, you'll still get the error.

---

### Post by chriskin on 2009-04-09
> **kidux said:**
> Why? This is a major selling point of Ubuntu, the ease of use in installing applications. Many other distros do not include such a package manager.

Also, you might look into packagekit. I haven't used it, but I've heard good things about it.


nah, packagekit feels like it came from another century. i've tried more than 30 distros, ubuntu's default way of installation is definitely the easier and faster

---

### Post by MysticGold04 on 2009-04-09
I *JUST* installed Hardy last night on one of my machines.  I think I'll be keeping it for awhile.  Is it possible for you to upgrade your RAM? It will do wonders in how your computer operates.

---

### Post by kanikilu on 2009-04-09
> **juancarlospaco said:**
> No, 6 Series still with Updates, [check at USN for example.]("http://www.ubuntu.com/usn/usn-755-1") Notice that 7.04 is conspicuously missing as it reached end of life last year. [7.10 is next](http://www.ubuntu.com/news/ubuntu-7.10-eol)...

Also, I'd like to reiterate 2 things already suggested. First, if you haven't tried it, XFCE/Xubuntu would be a bit lighter on your hardware, and you might be pleasantly surprised.

I've used Gnome off and on for 10 years, and keep coming back to it, but I recently installed Xubuntu 9.10 beta on my netbook, and am liking it so far, it's really not drastically different. It actually has a feature in particular that I'd love to see in Gnome, which is to hide icons in the notification area...

Secondly, what kind of computer is this? You may be able to find RAM pretty cheaply and a small investment would keep the old hardware alive without resorted to running an obsolete OS.

---

### Post by ranch hand on 2009-04-09
We recently got an old HP Pavilion xt993.  Gal gave it to us.  5Gb HDD was bad.

I had a 10Gb HDD.

The bugger only had 128Mb ram.  I got 2x256Mb sticks (new) for about 10 bucks with shipping.

It is now running Intrepid as fast as this box (see sig) ran under Vista.

---

### Post by garyed on 2009-04-09
> **Temposs said:**
> Did you remove the old lines in sources.lst or did you just add the lines that tinviole recommended? You have to delete the old lines as well or, yes, you'll still get the error.

Yes, I deleted all the deb lines & only used the ones tinivole recommended & it didn't work. Then I tried putting my original sources.list back & just changed the beginning directories of all the debs to the old-release ones & still the same error about package not available; either missing or obsolete. 
```
 sudo apt-get install csh 
```

---

### Post by pbotros1234 on 2009-04-09
Make sure to run a ```
sudo apt-get update
``` after you change your sources.list, this will refresh your list of packages.

---

### Post by garyed on 2009-04-09
> **pbotros1234 said:**
> Make sure to run a ```
sudo apt-get update
``` after you change your sources.list, this will refresh your list of packages.
That did it !!
Thanks to all for all the help.
I'm in the process of downloading Xubuntu to give it a try also but that's for another thread.

---

