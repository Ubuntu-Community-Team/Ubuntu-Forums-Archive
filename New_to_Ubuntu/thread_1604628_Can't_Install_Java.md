---
title: "Can't Install Java"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by ChannelZ28 on 2010-10-24
in windows i used to play yahoo backgammon and in ubuntu it says i need to download a plugin. so i downloaded it jre-6u22-linux-i586-rpm.bin. now how do i install it?

when i try, the terminal says "no such file or directory" its in the downloads folder since thats where firefox automatically downloads everything. i cant seem to use th cd command for downloads, it only says "no such file or directory". i can only use cd to get into a filesystem directory but i cant move the downloaded file into the filesystem.

---

### Post by waynefoutz on 2010-10-24
> **ChannelZ28 said:**
> in windows i used to play yahoo backgammon and in ubuntu it says i need to download a plugin. so i downloaded it jre-6u22-linux-i586-rpm.bin. now how do i install it?

when i try, the terminal says "no such file or directory" its in the downloads folder since thats where firefox automatically downloads everything. i cant seem to use th cd command for downloads, it only says "no such file or directory". i can only use cd to get into a filesystem directory but i cant move the downloaded file into the filesystem.

you need to install it through software center or synaptic package manager. Easiest way is to open up synaptic and search for "jre" and install all the related packages. 

My personal tip is to add the "SuperOS" repository, by installing the package linked at this site:

[http://hacktolive.org/wiki/Super_OS_repository#Adding_the_repository]("http://hacktolive.org/wiki/Super_OS_repository#Adding_the_repository")

then type these commands into the terminal:

```
sudo apt-get update
```

```
sudo apt-get install super-os
```


this will install java, dvd codecs, adobe flash, Google chrome, and a lot of other useful stuff in one easy fell swoop. It also adds a lot of great stuff to your Software Center like Google Earth. This is usually the first thing I do after an Ubuntu install. It pulls in all the extras that Ubuntu leaves out in one easy step.

---

### Post by hamstermoon on 2010-10-24
Hi! I am also having Java problems so may I add to this discussion?

I have just  thrown in the towel with Windows and installed 10.10 on my second laptop. 

It has OpenJDK and the IcedTea plugin intalled but its not working for a website I use regularily. On my notebook I had uninstall the OpenJDK and get Sun Java and a friend talked me through it. 

That friend isn't available so can anyone here talk me through what I need to do?

---

### Post by drpjkurian on 2010-10-24
> **ChannelZ28 said:**
> in windows i used to play yahoo backgammon and in ubuntu it says i need to download a plugin. so i downloaded it jre-6u22-linux-i586-rpm.bin. now how do i install it?

when i try, the terminal says "no such file or directory" its in the downloads folder since thats where firefox automatically downloads everything. i cant seem to use th cd command for downloads, it only says "no such file or directory". i can only use cd to get into a filesystem directory but i cant move the downloaded file into the filesystem.

Hi
Please note that you have downloaded .rpm package. The letter 'rpm' stands for redhat package manager. That means these packages are for linux OS like Redhat, fedora etc.
So in future please install the package which ends in .deb because ubuntu is debian based Linux OS

---

### Post by ArgusVision on 2010-10-24
While I haven't tinkered with super-OS, I would have to agree that installing **it** through on of the repos should work best for you right now.
If you're running 10.04 or 10.10 just go to the software center and type java in the search bar.

EDIT: By "it" (now in bold), I mean java, not super-os. I have nothing against super-os, I just haven't tried it.

---

### Post by waynefoutz on 2010-10-24
> **drpjkurian said:**
> Hi
Please note that you have downloaded .rpm package. The letter 'rpm' stands for redhat package manager. That means these packages are for linux OS like Redhat, fedora etc.
So in future please install the package which ends in .deb because ubuntu is debian based Linux OS

If they stick to packages in Software Center, or synaptic, they should be fine. One of the first thing you should explain to newbies us that downloading files off the web and trying to install them like you did in Windows is usually done as a last resort and rarely works.

---

### Post by drpjkurian on 2010-10-24
Hi
Super os.... this is a new piece of information for me

---

### Post by ArgusVision on 2010-10-24
Hamstermoon,
Same thing. You can use software center, or synaptic. ... or you can go to the java website and download the .deb.

I would go the built in software center first though

---

### Post by waynefoutz on 2010-10-24
> **ArgusVision said:**
> While I haven't tinkered with super-OS, I would have to agree that installing it through on of the repos should work best for you right now.
If you're running 10.04 or 10.10 just go to the software center and type java in the search bar.

SuperOS is just a repoisitory. The distro itself is just Ubuntu with all the codecs and Flash installed, plus a lot of useful stuff I would install anyway. The steps I listed above don't change Ubuntu in any way. Personally, this is what I do when I install Ubuntu on a computer, because it saves a lot of time rather than installing them all individually. It's a great time saver!

---

### Post by ChannelZ28 on 2010-10-24
hi, thanks. lots of replies in a short period of time.

waynefoutz: most of that software that you listed from the super OS repository is already listed in my version of synaptic. i installed chrome from synaptic and have installed java in the past...i dont know why i cant now.

drpjkurian: thank you for the file extension information. i didnt know that before. there was also a file with the .deb extension. i tried them both, not knowing the difference. but neither worked. still good info for future applications.

also, im not really all that new to linux, been using for about a year now. i just havent installed or tweaked anything lately and ive forgotten a lot of what i learned. i have successfully downloaded and installed software from websites many times, without using synaptic. i just seem to have forgotten something important.

i have sunjava installed from synaptic. i just doesnt seem to be working, or maybe isnt the right one.

---

### Post by ArgusVision on 2010-10-24
Well if the one from synaptic isn't working check the version against the .deb on the website. Go with the newer one usually.

---

### Post by howefield on 2010-10-24
> **ChannelZ28 said:**
> i have sunjava installed from synaptic. i just doesnt seem to be working, or maybe isnt the right one.

Which version of Ubuntu are you using ? If 10.04 or later, you may need to enable the Partner repository.

Try installing sun-java6-jre sun-java6-fonts and sun-java6-plugin.

---

### Post by waynefoutz on 2010-10-24
have you installed the plugin for the browser as well?

---

### Post by ChannelZ28 on 2010-10-24
howefield: those are what i was looking for. thats what i installed in the past to get it to work. for some reason they arent in my package manager. and they wont work this time. trying to install led to this message:

Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jre has no installation candidate

what does that mean?


waynefoutz: i dont know if i installed the browser plugin or not. i think thats what im trying to do right now. what would it be?

---

### Post by ChannelZ28 on 2010-10-24
also, im using 10.04 netbook remix.

---

### Post by howefield on 2010-10-24
Try reading here..

```
https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Sun Java moved to the Partner repository
```

---

### Post by waynefoutz on 2010-10-24
sun-java6-plugin

Also try installing ubuntu-restricted-extras-java

---

### Post by waynefoutz on 2010-10-24
> **howefield said:**
> Try reading here..

```
https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Sun Java moved to the Partner repository
```

I completely forgot about that..blame Oracle for that.

My "SuperOS" solution bypasses this problem.

---

### Post by ChannelZ28 on 2010-10-24
i installed sun-java6-jre from the partner repository and is STILL doesnt work. i dont get it, thats wat i installed in the past to get all yahoo java windows to work. 

i looked at the super-os and its about 600mb to install...i have an 8gb ssd on a netbook and thats just a bit too much. can i get what i need from the repository without having to download the whole thing?

---

### Post by howefield on 2010-10-24
Are you saying that you can't find sun-java6-plugin ?

---

### Post by cavh on 2010-10-24
Post the output of this command:

```
update-java-alternatives --list
```

---

### Post by perspectoff on 2010-10-24
Java is installed as part of ubuntu-restricted-extras (kubuntu-restricted-extras for Kubuntu)

Either install ubuntu-restricted-extras from a Package Manager or use a command-line interface Terminal (or Konsole):

 sudo apt-get install ubuntu-restricted-extras

---

### Post by ChannelZ28 on 2010-10-24
> **howefield said:**
> Are you saying that you can't find sun-java6-plugin ?

yup, couldnt find it. maybe im slightly retarted. but once i searched with the exact name, it was there. thank you. it works now.

---

### Post by howefield on 2010-10-24
> **ChannelZ28 said:**
> yup, couldnt find it. maybe im slightly retarted. but once i searched with the exact name, it was there. thank you. it works now.

Glad to hear it, after reading your post, I went over play some chess and backgammon there, a real blast from the past and doesn't seem to have changed much in the several (many) years since I used it last.

Good Luck.

---

### Post by beew on 2010-10-24
> **perspectoff said:**
> Java is installed as part of ubuntu-restricted-extras (kubuntu-restricted-extras for Kubuntu)

Either install ubuntu-restricted-extras from a Package Manager or use a command-line interface Terminal (or Konsole):

 sudo apt-get install ubuntu-restricted-extras

To get sun-java OP needs to add Canonical Partners to his sources list. In 10.10 you can only get open-jdk from the restricted repo.

You can find java-6-pluggin in the restricted repo (or one that is enabled by default), but not the .bin file so you can't install sun-java fully that way.

---

### Post by beew on 2010-10-24
In order to install sun-java in 10.10, you need to add Canonical Partners to your sources list. In Lucid you just need to check a box in Synaptic but in Maverick you apparently need to add the entry by hand.(Software center has Canonical Partners but the program listing there is apparently incomplete and for some reasons java is not listed, at least I couldn't see it)

So open up Synaptic, go to settings > repositories > other software and add the following line
> deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick partnerThen close the dialogue box and reload to update the listing. Open up Synaptic and then install sun-java6.bin, sun-java6-jre, sun-java6-jdk and sun-java6-plugin.

After that you still need to make sun-java the default as in Ubuntu, the default java the open version.

To change the default you can either remove all the packages associated with the open version, or in the terminal type
```

sudo update-java-alternatives -s java-6-sun
```

---

