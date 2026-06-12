---
title: "is there a way to upgrade my filezilla?"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by mishkin on 2009-03-04
It has some bugs like when I first start xfering it won't show a progress bar until a file has finished while i have it on top. From then on it shows, also the in progress follow down as you scroll through making it hard to see files in que

anyways I have latest version according to synaptic package manger but it's a special ubuntu port??

there is a generic linux version which is much newer but it came in 2 formats

Already in a folder already installed (wasn't sure where i should put the folder if I wanna use it from that)

Or as source, problem was it wouldn't complile because the c++ thingy couldn't make executables (I looked for some solutions for this and some say it can't be compiled on ubuntu)

any help / insight appricated

---

### Post by SamNSane on 2009-03-05
> **mishkin said:**
> It has some bugs like when I first start xfering it won't show a progress bar until a file has finished while i have it on top. From then on it shows, also the in progress follow down as you scroll through making it hard to see files in que

anyways I have latest version according to synaptic package manger but it's a special ubuntu port??

there is a generic linux version which is much newer but it came in 2 formats

Already in a folder already installed (wasn't sure where i should put the folder if I wanna use it from that)

Or as source, problem was it wouldn't complile because the c++ thingy couldn't make executables (I looked for some solutions for this and some say it can't be compiled on ubuntu)

any help / insight appricated

May I suggest a somewhat easier way?

First of all, use Synaptic to "remove completely" the FileZilla version you have installed.

Now go to [http://www.getdeb.net/](http://www.getdeb.net/). If you are using NoScript or some other method of preventing Javascript from running in your browser, you'll have to allow getdeb.net to run Javascript.

Now click on the "version" link at getdeb and select the version of Ubuntu you are running. This will ensure that, when you search for software, getdeb will present packages that were compiled for your particular version of ubuntu.

Enter "FileZilla" in the search box on the getdeb page. You'll get a listing of recent FileZilla versions that have been compiled and set up as .deb packages for your OS.

You will need to download three packages:
1. filezilla
2. filezilla-common
3. filezilla-locales

Once you have them on your local system you install them in the following order: filezilla-common, filezilla, and filezilla-locales.

Don't be concerned if the package manager tells you that the filezilla-common installation couldn't be completed properly. The dialog that pops up tells you EXACTLY what to type in a gnome-terminal window. You execute that command, just as the package manager dialog told you to, and the installation of filezilla-common will be completed. You OK your way out of the dialogs. If you wish you can double-click on the filezilla-common package again, and it will be asking you if you want to reinstall the package. Just close out of the dialog. That was just so you'd know the installation succeeded.

Now continue by installing filezilla and filezilla-locales in turn by double-clicking on them.

The only disadvantage to installing FileZilla in this way is that you won't automatically get updates through Synaptic. So, when later versions of filezilla are available for your version of Ubuntu, you'll want to go back to getdeb to get them. And you'll have to go through the same process again to install them. (Only you won't really need to remove your old FileZilla first.)

I hope this is helpful. I've used this process on a couple of notebooks and 8 desktops -- some running 8.04 and some running 8.10 -- with no issues whatsoever.

---

### Post by tjustleft on 2009-06-03
> **SamNSane said:**
> The only disadvantage to installing FileZilla in this way is that you won't automatically get updates through Synaptic.

That doesn't seem much of a disadvantage to me. My Ubuntu 8.04 is up to date and Filezilla version is 3.0.7.1. Filezilla's updater says the new version to date is 3.2.4.1. 

I know Ubuntu wants to be sure packages are compatible but that seems like a fairly big gap in updates. I'm so tired of my version not staying connected. I may download the new version and see if it works better.

---

