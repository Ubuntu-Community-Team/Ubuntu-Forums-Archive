---
title: "Automatically resolve dependencies with dpkg"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by mo0nykit on 2009-09-16
Hello everyone!

Say, I got a **.deb** file from the web through **wget** or **Firefox**. Then I install it with ```
dpkg -i <package name>
``` Then the installation complains that the **.deb** has some dependencies which I don't have yet. Last time I tried, I just did this ```
sudo apt-get install <dependency_01> <dependency_02> <dependency_n>
``` It's all right if there are only a few dependencies, but what do I do if there are tens or hundreds of dependencies to be resolved?

Thanks in advance!
Kit

---

### Post by Paqman on 2009-09-16
This is what's know as "dependency hell" and there's only one easy solution: use the package manager and the repos. Stray outside of those and you're likely to run into this problem.

---

### Post by mo0nykit on 2009-09-16
:(
I use Blender, and if I stay with the repositories, I get Blender 2.48a, but the latest version is Blender 2.49b. I had to download a **.deb** file from their site.

On the other hand, when I was trying to install the **Firefox Flash plugin**, I ran into a dependency oven (since it was only a few dependencies :))

Let's wait and see when someone might have a workaround for dependency hell with **dpkg**

---

### Post by Paqman on 2009-09-16
By all means, use .debs! Using a .deb will mean that your dependencies are automatically satisfied (assuming those dependencies are available). It doesn't matter whether you use dpkg, Synaptic, apt-get, or just click on the package and use Gdebi (since they all just use dpkg anyway).

That's why PPAs are great. The PPA owner can put all the dependencies into the PPA, and the package manager takes care of everything.

You can get Flash from the repos, btw. Although for 64-bit the one from Adobe works a lot better in my experience.

---

### Post by scorp123 on 2009-09-16
> **mo0nykit said:**
>  ```
sudo apt-get install <dependency_01> <dependency_02> <dependency_n>
``` It's all right if there are only a few dependencies, but what do I do if there are tens or hundreds of dependencies to be resolved? ```
sudo apt-get -f install
``` Voila, done.

---

### Post by scorp123 on 2009-09-16
> **Paqman said:**
> This is what's know as "dependency hell"  Only if you don't bother to read the manual of "apt". The manual is your friend. So is Google. And if you bother to search for the correct answer you'd see that with *.deb packages something like "dependency hell" should not really be possible for as long as you stick to your distribution.

Where you definitely might run into a dependency hell is if you e.g. try to install obscure Debian packages that were not meant to be installed on a modern Ubuntu system (e.g. they were created with an old Debian release in mind). Such packages may insist on depending on other packages that do not exist on Ubuntu under that name ... So yes, you might run into dependency hell there if you mix packages from other distros.

Another candidate would be converted packages that someone (poorly) converted using "alien". Sometimes people forget to adjust the dependencies and the resulting package may all of a sudden insist on depending on something that doesn't even exist on Debian or Ubuntu (but may have existed for Fedora, Red Hat or SUSE ...).

But again: for as long as you use packages that were really intended for your Ubuntu release you should not run into dependency problems, let alone "dependency hell".

---

### Post by mo0nykit on 2009-09-16
**@Paqman**
All this time I was wondering what a PPA was, and I couldn't google the acronym expansion for that (Personal Package Archive, in case someone else is also wondering:)). I see, so PPAs are related to dependency hell. Now I know :)
> Using a .deb will mean that your dependencies are automatically satisfied (assuming those dependencies are available). Yes, I still have to make sure I have the dependencies, and the process of "making sure" constitutes dependency hell.. hehe.. scorp123 has suggested a solution...

**@scorp123**
So, for example, I type
```
sudo dpkg -i <flash plugin package>
``` It doesn't finish up with the configuration, and writes a **notice** to the package manager that it needs this and that package.
Then I issue
```
sudo apt-get -f install
``` Then the **-f** flag reads the broken dependency **notice** and installs the needed packages? (I have just read the **apt-get -h**)

---

### Post by scorp123 on 2009-09-16
> **mo0nykit said:**
> I have just read the [B]apt-get -h Why not the full manual? ;)

```
man apt-get
```

---

### Post by 3rdalbum on 2009-09-16
> **mo0nykit said:**
> Hello everyone!

Say, I got a **.deb** file from the web through **wget** or **Firefox**. Then I install it with ```
dpkg -i <package name>
``` Then the installation complains that the **.deb** has some dependencies which I don't have yet. Last time I tried, I just did this ```
sudo apt-get install <dependency_01> <dependency_02> <dependency_n>
``` It's all right if there are only a few dependencies, but what do I do if there are tens or hundreds of dependencies to be resolved?

Thanks in advance!
Kit

The easiest solution is to install the Debian packages by double-clicking them, which opens them in Gdebi.

Gdebi will resolve dependencies for you.

---

### Post by mo0nykit on 2009-09-16
**@scorp123**
thanks! I just wanted a quick glance at what **-f** does :)

**@3rdalbum**
thanks! I'm trying to stay away from GUI solutions, though, so I could learn what makes Linux tick under the hood :) but your tip sure is helpful for someone who might want a quick fix :D

---

### Post by dawynn on 2009-09-16
Just some thoughts.

Not every package is available from the repositories.  And not every package made available on the web comes through an Ubuntu-based PPA.  And perchance you have to convert an rpm to deb through alien?? ....

That being said, here's my experience...

Gdebi -- great GUI tool that will try to resolve dependencies as much as possible.  But you may be stuck if your package depends on libraries not available in the repositories you use.

aptitude -- as a command-line tool, it is interchangeable with apt-get.  These have a problem in that, if you have a system where packages are marked as automatically installed but no longer have any dependent packages installed, or an install failed with several packages still marked for update, any attempt to install any new pacakges will attempt to work also on all the other marked packages.  So, trying to install a single package with aptitude or apt-get may do more than you want it to.

dpkg -- will work on the packages specifically mentioned in the command line call.  Does not try to overwork.  Does not try to install all dependencies when asked to install one package.  Does not try to purge auto-installed packages when asked to purge just one package.

In order of my personal preference when installing for a single package:

1) Check your repositories first.  Use synaptic or aptitude or whatever package manager you typically use.  Aptitude if you want a little more control over what optional packages also get installed.

2) If downloading a separate package from the web -- gdebi rules all because it tries to auto-resolve dependencies.

3) If gdebi cannot resolve all the dependencies, find the dependencies on the web, and use one of the command line tools to install (dpkg, aptitude, apt-get).

If you're having trouble finding an archaic dependency, try checking these resources:

Ubuntu repository search: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
Debian repository search: [http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages)

In these search tools, open up the search to distribution "any", section "any", and give it a whirl.  But be advised that mixing releases, and mixing libraries from Ubuntu and Debian can make for an unstable system.

---

### Post by scorp123 on 2009-09-16
> **dawynn said:**
>  If you're having trouble finding an archaic dependency, try checking these resources:

Ubuntu repository search: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
Debian repository search: [http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages)

In these search tools, open up the search to distribution "any", section "any", and give it a whirl.  But be advised that mixing releases, and mixing libraries from Ubuntu and Debian can make for an unstable system.

Excellent posting!

Last but not least: Don't forget Google. Should you really ever run into dependency problems (e.g. because you tried to manually install a package that you got from a web site and not from a repo) try Googling the error message that you receive. Chances are that someone has already run into the problem before and hopefully managed to solve it. Or maybe Google will find a blog posting or some other web page that explains how to get around the problem ...

---

### Post by scorp123 on 2009-09-16
> **mo0nykit said:**
> **@scorp123**
thanks! I just wanted a quick glance at what **-f** does :) As you probably have seen by now the "-f" parameter tries to **f**ind missing dependencies.

The explanation is this: When you install package with unsatisfied dependencies that package will be marked as "broken" and "not completely installed". "apt" and "dpkg" will complain about it whenever they get a chance. You will see this e.g. when you try and do a "sudo apt-get update && sudo apt-get dist-upgrade" then "apt" might complain about *"10 packages not updated, 1 held back, 1 not completely installed ... "*

So "**sudo apt-get -f install**" is the right remedy for that ... usually. It will work for as long as the dependencies can be found somewhere in the repos that you configured (*/etc/apt/sources.list* and all lists underneath */etc/apt/sources.list.d/** ...)

If those dependencies can't be found in any repository then you will have to try your luck with the two search engines mentioned above ... Or with Google.

Another useful search engine I'd like to mention is this one here:

"LaunchPad PPA Search"
[http://ppa-search.appspot.com/](http://ppa-search.appspot.com/)

This is especially useful if you use lots of stuff from PPA repos. Sometimes one PPA application might depend on stuff that can be found in another PPA repo ... But which one? Voila. This search engine can find any PPA out there.

---

### Post by mo0nykit on 2009-09-16
Thanks guys!

That was a lot more help than I could swallow :popcorn: hehe... I hope this thread turns out to be very helpful for everyone else. Thanks thanks! :)

---

