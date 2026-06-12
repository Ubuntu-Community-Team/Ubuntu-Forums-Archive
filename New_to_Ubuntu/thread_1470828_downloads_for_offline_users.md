---
title: "downloads for offline users"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by Zelf on 2010-05-03
Hi..
First off... Eish!! u guys are flippen buzzy.. 5 pages of problems in 5 hours. and thats just the beginners posts. Shikes... now plus 1.
 
OK.. 
I got my copy of 10.04 from my friend, here's the thing...
I don't have Internet at home... South Africa is a bit behind with this.. We pay per Mb. So I can get downloads from friends. 
 
I used the glorious GIMP and noted that it is not on 10.04.. Got that now. Downloaded the Tar ball this morning...
 
Still need codecs for MP3 avi DVD and, and , and, 
Where can I get the codecs?????
 
I just got a link on how to get the nvidia drivers running.
 
Havent tested it though.
 
I think ubuntu should have site for people like me... Asite with all these needed stuff easy to download and easy to install.
 
Thanx:KS

---

### Post by 3rdalbum on 2010-05-03
[http://packages.ubuntu.com](http://packages.ubuntu.com)

You can download packages from there - you'll need quite a few of them for Gimp.

For the codecs, you'll need to download the packages that start with the word "gstreamer" and end in "bad" or "ugly".

DVD playback requires the "libdvdnav", "libdvdread" packages; you'll also need the "libdvdcss2" package from the Medibuntu.org website.

---

### Post by shuttleworthwannabe on 2010-05-03
hey, boeta--try the Ultimate release--it is about 2.xGB DVD download. Ask you friend to download that and you will be set.

---

### Post by brumman on 2010-06-17
I am in the same boat - that is no net connection for my machine using Ubuntu 9.10 and must download on Windows and install from flash stick. 
I'd like to be able to install those missing GIMP help files - are the packages/files available somewhere and how do I install them so that I can use GIMP help without being online?
Hope I am allowed to post this I think it is still on topic.

---

### Post by mapes12 on 2010-06-17
If your friend can get the packages then try aptoncd to manually pass them across to you: [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by XubuRoxMySox on 2010-06-17
Aptoncd is available in the repositories, too. Once installed, you can use a CD as a source for all the downloaded programs you want. It's nice for installing stuff on multiple machines, too.

Aptly,
Robin

---

### Post by mac9416 on 2010-06-17
> I don't have Internet at home... South Africa is a bit behind with this.. We pay per Mb. So I can get downloads from friends. 

I think ubuntu should have site for people like me... Asite with all these needed stuff easy to download and easy to install.Hi, Zelf, and welcome to UbuntuForums!

To understand what makes installing software on offline Linux computers so difficult, one should understand what makes it comparatively easy in Windows.

In Windows, each software installer (.exe) contains all files necessary for a program to run (with some rare exceptions, particularly in open source software). This makes installing a program as easy as one download and one double-click, but it also makes for large installers.

In Linux, software is broken into pieces called packages. Almost all packages depend on other packages to run properly. This makes for smaller installers and greater efficiency. Handy programs like Software Center and Synaptic find all the necessary dependencies, download, and install them for you. That's great... If you're online.

If you are not online, there are several things folks recommend. Here are some that have already been suggested, as well as my thoughts on each.

> [http://packages.ubuntu.com](http://packages.ubuntu.com)

You can download packages from there - you'll need quite a few of them for Gimp.packages.ubuntu.com provides a nice interface for finding packages, but it doesn't make finding all necessary dependencies much easier. You can click through lists of dependencies, painstakingly downloading each one. But this is very time-consuming, and mistakes are inevitable. 

> hey, boeta--try the Ultimate release--it is about 2.xGB DVD download. Ask you friend to download that and you will be set.[URL="http://ultimateedition.info/"]
Ubuntu Ultimate Edition[/URL] comes with some great software that doesn't come with the normal Ubuntu. However, it does not come with the media codecs that you are looking for. For that you might want to look at [Linux Mint]("http://linuxmint.com/").

> If your friend can get the packages then try aptoncd to manually pass them across to you: [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)APTOnCD allows you to create a CDROM containing packages from another Ubuntu computer to an offline computer. It has several disadvantages:


[LIST=1]
[*]  The online computer must be almost the same as the offline computer -- same Linux distro, flavor, and architecture. It must also have the same packages installed.
[*]You have to install the desired packages on the online computer to make them available to APTOnCD.
[/LIST]
 
If you're OK with both of those, APTOnCD may be the way to go.

But is there a better solution? 
[URL="http://keryxproject.org"]
Keryx[/URL] is a package manager that can take a snapshot of your offline computer and use that to download packages from an online computer. It handles getting the necessary dependencies. Another plus is that it will run on any Linux flavor and even on Windows.

Now, I must warn you that Keryx is not perfect. It is undergoing huge improvements, and in the meantime, you will probably run into problems. 

So, using Keryx, the answers to your questions are fairly simple.

> Still need codecs for MP3 avi DVD and, and , and,
Where can I get the codecs?????You will need to use Keryx to download ubuntu-restricted-extras. For DVD playback, you will need to enable [Medibuntu]("http://medibuntu.org/") on your computer and download (as 3rdalbum mentioned) libdvdread4, libdvdnav4, and libdvdcss2.

> I'd like to be able to install those missing GIMP help files - are the packages/files available somewhere and how do I install them so that I can use GIMP help without being online?Brumman, you should use Keryx to download gimp-help-en (replacing "en" with your language code if necessary).

---

