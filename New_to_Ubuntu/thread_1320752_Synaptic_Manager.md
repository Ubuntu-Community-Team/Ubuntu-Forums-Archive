---
title: "Synaptic Manager"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by thadacto on 2009-11-09
As you can see, I am a complete diseaster when it comes to linux - especially as I have been in hospital for the last 2 months and forgotten the little I did learn. - I used to be able to install a program but have forgotten how to and any guides I have found haven't helped me.
I am trying to install the latest version of Kino (ver kin-1.3.4) of September 2009.
Unfortunately Synaptic Manager only as an old version 1.1.1.
Is there a way of getting the latest version through Synaptic? 
If not, how do I install Kino-1.3.4 from my desktop?
I thought that 
george@george-desktop:~$ 
was my desktop but it seems to be my home folder and I can't work out how to get to the desktop using 'cd'

---

### Post by JDShu on 2009-11-09
Looks like the version of Kino you want is too new to be included in the repositories, especially for Hardy. 

May you can  try either upgrading or compiling from source?

---

### Post by jmszr on 2009-11-09
thadacto,

Not exactly what you want, but you can get a Kino 1.3.2 .deb from here: [http://old.getdeb.net/search.php?keywords=kino](http://old.getdeb.net/search.php?keywords=kino)

---

### Post by mikechant on 2009-11-10
<i>I thought that 
george@george-desktop:~$ 
was my desktop but it seems to be my home folder and I can't work out how to get to the desktop using 'cd'
</i>

'george-desktop' is the 'computer name' and does not correspond to the Desktop where your icons etc are.

To get to your Desktop in the terminal just type ```
cd Desktop
```- note the upper case 'D'

---

### Post by SunnyRabbiera on 2009-11-10
> **jmszr said:**
> thadacto,

Not exactly what you want, but you can get a Kino 1.3.2 .deb from here: [http://old.getdeb.net/search.php?keywords=kino](http://old.getdeb.net/search.php?keywords=kino)

Good suggestion, it works.
Just keep in mind Ubuntu does have older versions of some apps, mainly for stability concerns.

---

### Post by tchoklat on 2009-11-10
> **SunnyRabbiera said:**
> Good suggestion, it works.
Just keep in mind Ubuntu does have older versions of some apps, mainly for stability concerns.
 
 
Open a terminal and type 
$ sudo apt-get update
then type 
$ sudo apt-get upgrade
 
this should do everything you want!

---

### Post by 3rdalbum on 2009-11-10
> **tchoklat said:**
> Open a terminal and type 
$ sudo apt-get update
then type 
$ sudo apt-get upgrade
 
this should do everything you want!

Firstly, no it won't. It doesn't magically make the repository version newer. Secondly, NEVER run sudo apt-get upgrade.

I'd say to try the Deb or upgrade to a newer Ubuntu - I imagine compiling software is probably beyond you right now (and if you tried compiling Kino, it might require later versions of libraries than what Hardy has; you'd be replacing large tracts of your system and compiling libraries too; too much hassle).

---

### Post by tchoklat on 2009-11-10
.... beg to differ, what I have suggested will update/upgrade the current version.
 
ref: " 3.4 Upgrading packages
Package upgrades are a great success of the APT system. They can be achieved with a single command: apt-get upgrade. You can use this command to upgrade packages within the same distribution, as well as to upgrade to a new distribution," ([http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html))

---

### Post by snowpine on 2009-11-10
> **3rdalbum said:**
> Secondly, NEVER run sudo apt-get upgrade.


Why not?

---

### Post by wojox on 2009-11-10
```
sudo apt-get -u upgrade
```

You shouldn't blindly run upgrades is why.

---

### Post by tchoklat on 2009-11-10
... if you feel like you want to I would suggest you install the latest version of Ubuntu either from an image or through the terminal with the command;
$ sudo apt-get -u dist-upgrade
 
 
tchoklat

---

### Post by tchoklat on 2009-11-10
It's useful to run this command with the -u option. This option causes APT to show the complete list of packages which will be upgraded. APT will download the latest versions of each package and will install them in the proper order.

---

### Post by tchoklat on 2009-11-10
**Update the Package Index**: The APT package index is essentially a database of available packages from the repositories defined in the /etc/apt/sources.list file. To update the local package index with the latest changes made in repositories, type the following: 
**sudo apt-get update**
**Upgrade Packages**: Over time, updated versions of packages currently installed on your computer may become available from the package repositories (for example security updates). To upgrade your system, first update your package index as outlined above, and then type: 
**sudo apt-get upgrade** **(taken from official ubuntu documentation at [https://help.ubuntu.com/8.04/serverguide/C/apt-get.html)**]("https://help.ubuntu.com/8.04/serverguide/C/apt-get.html)")

---

### Post by snowpine on 2009-11-10
-u is not necessary to display the packages that will be upgraded. (On my system ayway)

---

### Post by philinux on 2009-11-10
```
sudo apt-get update && sudo apt-get upgrade
```

I use this all the time. It's what update manager does anyway.

See

```
man apt-get
```

---

### Post by Paqman on 2009-11-10
Sudo apt-get upgrade is ok for small incremental updates, although it always pays to have a really good look at what packages it's going to change. The one you shouldn't run is sudo apt-get upgrade -y, since that's when you really are blindly upgrading.

---

### Post by snowpine on 2009-11-10
Using sidux for a while trained me to do this instead:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

Probably less of a big deal with Ubuntu, but I like to be thorough.

---

### Post by philinux on 2009-11-10
sudo apt-get update && sudo apt-get upgrade
There is absolutely no reason why you should not run this. This is what update manager does regularly. I just prefer to do it with the terminal. It's faster. And there's a Y/N question before it upgrades. On Karmic there is no reason not to upgrade. 

```
update
           update is used to resynchronize the package index files from their sources. The indexes of available packages are
           fetched from the location(s) specified in /etc/apt/sources.list. For example, when using a Debian archive, this
           command retrieves and scans the Packages.gz files, so that information about new and updated packages is available.
           An update should always be performed before an upgrade or dist-upgrade. Please be aware that the overall progress
           meter will be incorrect as the size of the package files cannot be known in advance.

       upgrade
           upgrade is used to install the newest versions of all packages currently installed on the system from the sources
           enumerated in /etc/apt/sources.list. Packages currently installed with new versions available are retrieved and
           upgraded; under no circumstances are currently installed packages removed, or packages not already installed
           retrieved and installed. New versions of currently installed packages that cannot be upgraded without changing the
           install status of another package will be left at their current version. An update must be performed first so that
           apt-get knows that new versions of packages are available
```

---

### Post by wojox on 2009-11-10
Maybe -u is just a Debian thing. That's just how I've done it after reading their docs. I did notice however 

```
sudo apt-get update && sudo apt-get upgrade
```

Will hold back without the -u until you confirm y/n.

Cool thanks for the for the heads up. I learned something new today. Two less characters to type. :p

---

### Post by tchoklat on 2009-11-10
the magic of the ubuntu comunity !

---

### Post by philinux on 2009-11-10
> **tchoklat said:**
> the magic of the ubuntu comunity !

Glad the misinformation was cleared up. :p

---

