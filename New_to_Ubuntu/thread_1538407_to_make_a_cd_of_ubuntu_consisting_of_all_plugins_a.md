---
title: "to make a cd of ubuntu consisting of all plugins and packages from our running ubuntu"
date: 2010-07-25
forum: New to Ubuntu
---

### Post by amityadav9314 on 2010-07-25
Hi there!

I am using ubuntu 10.04.

Well as we know after a fresh installation of ubuntu  we need to install plugins for MP3 and MPEG AND MANY VIDEO FORMATS  that is not supported by ubuntu 'cause those are patent.

After that we install many packages and dependencies for them either through terminal or Synaptic package manager. In addition we install many applications as well like..VLC, GOOGLE CHROME, OPERA,SKYPE, And many more.

And suppose we want to format our ubuntu, and install it again, then we have to go for all those package installation and application installation again. This is time consuming and very irritating as well.

So my question is here that :-
1:- Can we make a CD/DVD in an .iso format from our running ubuntu so that it includes all those things that we have got running on our present ubuntu.
2:-And when we install ubuntu later from our that CD/DVD, so are we gonna get all those application already installed on our system?

MY BOTTOMLINE HERE IS THAT CAN WE GET OR MAKE A CD/DVD THAT CONTAIN ALL THOSE PACKAGES/APPLICATIONS/PLUGINS/DEPENDENCIES etc. THAT OUR CURRENT UBUNTU RUNS.

Well I hope you have understand what I tried to say and want to achieve....

So please help me...
Thanks!

---

### Post by Res2216firestar on 2010-07-25
Assuming you have an internet connection, open a terminal (Applications>Accessories>Terminal), and run the command:

```
sudo dpkg --get-selections > installedsoftware
```

This generates a list of the software you have installed, which can be used by dpkg to download and install it on another install. Copy the generated file located in your home folder, installedsoftware, to a flash drive or something. After the clean install, put installedsoftware in that computer's home folder, open a terminal, and run:

```
sudo dpkg --set-selections < installedsoftware
```

Hope this helps :)

---

### Post by k3lt01 on 2010-07-25
Have a look at [Remastersys]("http://www.geekconnection.org/remastersys/") and/or [UCK (Ubuntu Customisation Kit)]("http://uck.sourceforge.net/"). There is another one but I can't remember its name atm.

---

### Post by mapes12 on 2010-07-25
Here are some utilities that I know of. They all achieve your objective but in a different way:-

[FSarchiver]("http://www.fsarchiver.org/Main_Page")

[Clonezilla]("http://clonezilla.org/")

[APTonCD]("http://aptoncd.sourceforge.net/")

---

### Post by rlp1938 on 2010-07-25
> **amityadav9314 said:**
> Hi there!

I am using ubuntu 10.04.


So my question is here that :-
1:- Can we make a CD/DVD in an .iso format from our running ubuntu so that it includes all those things that we have got running on our present ubuntu.
2:-And when we install ubuntu later from our that CD/DVD, so are we gonna get all those application already installed on our system?

MY BOTTOMLINE HERE IS THAT CAN WE GET OR MAKE A CD/DVD THAT CONTAIN ALL THOSE PACKAGES/APPLICATIONS/PLUGINS/DEPENDENCIES etc. THAT OUR CURRENT UBUNTU RUNS.


APTonCD can help here.
sudo apt-get install aptoncd
gets it for you.
Once installed you can invoke it from:
 System->Administration->APTonCD

There are 2 modes Create and Restore.
Create makes an iso which you can use to burn a CD or DVD. Personally I always burn to DVD regardless of size because that medium is so much more reliable. However after creation you can just copy the iso out to a USB memory stick if you want because the Restore function works off the iso image or optical medium at your option.

I have found that APTonCD is buggy on restore. You may optionally make a meta-package, named aptoncd-metapackage... which supposedly installs all of your software if you invoke it with Gdebi. My experience is that it fails to install all programs.
Consequently I opt to just restore all files during restoration.

That does not install anything! You have to follow that with:
sudo apt-get install -f
in order to actually install your newly restored cache.

That successfully installs everything but from then on every time you invoke apt-get you get nagged to use apt-get autoremove to clean out the auto installed packages. DON'T do that!

My workaround for that is to use this script:

<script>
#!/bin/bash
# restore.sh - restore all packages in cache
for i in \
packagexxx package....\
anotherpackage... \
lastpackage
do
  apt-get -y install $i
done
</script>

where you have to paste in the list of packages that apt wants to autoremove. NB you will have to paste in the '\' to escape the new line for every line of your list of packages except the last one. Apt-get will not install these packages as you have already done that but it will set the package status to 'manually installed' from the previous 'auto installed' status and stop the apt-get nagging.

This is a kludge and if anyone knows how to change these flags in some other way please tell me how.

Bob

---

### Post by mapes12 on 2010-07-25
> **Res2216firestar said:**
> Assuming you have an internet connection, open a terminal (Applications>Accessories>Terminal), and run the command:

```
sudo dpkg --get-selections > installedsoftware
```

This generates a list of the software you have installed, which can be used by dpkg to download and install it on another install. Copy the generated file located in your home folder, installedsoftware, to a flash drive or something. After the clean install, put installedsoftware in that computer's home folder, open a terminal, and run:

```
sudo dpkg --set-selections < installedsoftware
```

Hope this helps :)I like this!

Will this also install FF addons?

---

### Post by amityadav9314 on 2010-07-25
One more thing i would like to add to my Problem..
What is RECONSTRUCTION application...
Is this also related to my query?

---

### Post by CharlesA on 2010-07-25
Use remastersys, it creates a bootable livecd out of an existing debian environment.

Just boot off the cd/dvd you make and then install it.

---

### Post by beew on 2010-07-25
If your computer supports booting from usb you should make a live usb with persistence instead of a live CD, much more convenient to store and much faster to run and install too.

[URL="http://www.pendrivelinux.com/"]
http://www.pendrivelinux.com/
[/URL]

Opps, I am sorry, I think I misunderstood your question. :(

---

### Post by amityadav9314 on 2010-07-25
but i can not find remastersys any where, i am using  ubuntu 10.04

---

### Post by mikewhatever on 2010-07-25
> **amityadav9314 said:**
> but i can not find remastersys any where, i am using  ubuntu 10.04

Here you go.
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

---

### Post by amityadav9314 on 2010-07-25
oops!
I mean i could not add it to ubuntu softwares third party softwres.
After adding and relodin, it says some package can't be downloaded.

---

### Post by corncob on 2010-07-25
> **mapes12 said:**
> I like this!

Will this also install FF addons?

I don't know but what I do is to save .mozilla, a hidden folder in the home directory, to an external drive and then merge it back into the new installation.  I seem to get everything in Firefox back.

---

### Post by lovinglinux on 2010-07-25
> **Res2216firestar said:**
> Assuming you have an internet connection, open a terminal (Applications>Accessories>Terminal), and run the command:

```
sudo dpkg --get-selections > installedsoftware
```

This generates a list of the software you have installed, which can be used by dpkg to download and install it on another install. Copy the generated file located in your home folder, installedsoftware, to a flash drive or something. After the clean install, put installedsoftware in that computer's home folder, open a terminal, and run:

```
sudo dpkg --set-selections < installedsoftware
```

Hope this helps :)

That works like a charm.

> **mapes12 said:**
> I like this!

You might also like my [Umarks](http://umarks-extension.blogspot.com) extension, that does and also re-install ppa repositories. It also allows to export the list of packages, with the packages included, so you don't need to download them again.

> **mapes12 said:**
> Will this also install FF addons?

Depends. Some extensions can be installed from the repositories, so they would be covered too, but most extensions don't. For instance I have more then 60 extensions and I get all of them from Mozilla site.

Anyway, you can simply copy the ~/.mozilla folder, but I would also consider having a [separate partition for /home]("https://help.ubuntu.com/community/Partitioning/Home/Moving"), so you can re-install Ubuntu without losing your settings and personal files. With a separate partition and Umarks I can re-install Ubuntu and get everything working as before in no time.

I also recommend [FEBE](https://addons.mozilla.org/en-US/firefox/addon/2109/) extension for regular Firefox backups. It also has a feature, called Quick Backup, that allows to create a single xpi file with all your FF extensions, so you can install all at once.

---

### Post by mapes12 on 2010-07-25
> but i can not find remastersys any where, i am using ubuntu 10.04

You need to add the repo to your software sources. Here's a full tutorial (mostly GUI):-

[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)

---

### Post by anand_30 on 2010-07-25
Good question my friend was also in search of this,but he has another condition that one should be able to install this on a system with NO INTERNET connection.

But,will following procedure require internet on destination system??or you can download packages previously,put them in usb and install them on another system???
> **Res2216firestar said:**
> Assuming you have an internet connection, open a terminal (Applications>Accessories>Terminal), and run the command:

```
sudo dpkg --get-selections > installedsoftware
```This generates a list of the software you have installed, which can be used by dpkg to download and install it on another install. Copy the generated file located in your home folder, installedsoftware, to a flash drive or something. After the clean install, put installedsoftware in that computer's home folder, open a terminal, and run:

```
sudo dpkg --set-selections < installedsoftware
```Hope this helps 

I really liked remastersys and will suggest to my friend.

---

### Post by rlp1938 on 2010-07-25
> **Res2216firestar said:**
> Assuming you have an internet connection, open a terminal (Applications>Accessories>Terminal), and run the command:

```
sudo dpkg --get-selections > installedsoftware
```

This generates a list of the software you have installed, which can be used by dpkg to download and install it on another install. Copy the generated file located in your home folder, installedsoftware, to a flash drive or something. After the clean install, put installedsoftware in that computer's home folder, open a terminal, and run:

```
sudo dpkg --set-selections < installedsoftware
```

Hope this helps :)

And then it downloads it all again does it not?

Bob

---

### Post by Res2216firestar on 2010-07-25
> **rlp1938 said:**
> And then it downloads it all again does it not?

Bob

Not sure what exactly you mean. It creates a list of software installed on one computer and installs it on another. a list of software onto a different install. It doesn't redownload anything the second computer already has, but it does have to download packages it doesn't have.

---

### Post by mapes12 on 2010-07-25
On the [Remastersys geek site]("http://www.geekconnection.org/remastersys/ubuntu.html") under the dist option it says > Clean up history and cache and copy over the contents to /etc/skel 
1. How do I clean up history and cache?
2. Where do I copy over the contents of /etc/skel to, and why?

---

### Post by oldfred on 2010-07-25
If installing to another computer with the same version of Ubuntu then the Remastersys, clonezilla and/or aptonCD may make more sense.

But if upgrading to a new version the dpkg --get-selections makes better sense as it is just a list of applications, not versions so it installs the latest version. But it does have to download them.
In my case I had upgraded in place for about 3 years and not housecleaned. It had many obsolete and older software in the list that I did not really want to reinstall, so houseclean before using the dpkg procedure. I regularly run the dpkg & include that list in my backup of /home so I can more easily recover if I ever have a total crash.

---

### Post by philinux on 2010-07-25
> **mapes12 said:**
> On the [Remastersys geek site]("http://www.geekconnection.org/remastersys/ubuntu.html") under the dist option it says 
1. How do I clean up history and cache?
2. Where do I copy over the contents of /etc/skel to, and why?

Although it's not clear I think he means Firefox>tools>clear recent history and cache. Then copy the .mozilla folder to /etc/skel. But only if you want you existing bookmarks and other stuff available on the livecd.

---

### Post by k3lt01 on 2010-07-25
It could also be Places > Recent Documents > Clear Recent Documents.

---

### Post by jerrykenny on 2010-07-25
Being old fashioned i'd tackle this at the installation stage by having a separate partition for /local

After all, isnt this one of the reasons we have partitions !!!?

---

### Post by mapes12 on 2010-07-26
> Although it's not clear I think he means Firefox>tools>clear recent history and cache. Then copy the .mozilla folder to /etc/skel. But only if you want you existing bookmarks and other stuff available on the livecd.> It could also be Places > Recent Documents > Clear Recent Documents.Thanks guys. Although I still don't understand why anything has to be copied into /etc/skel. I'll give this a go on my test rig later this week to see what results I get with the various config options.:?

---

