---
title: "When will we see openoffice 3.1 in ubuntu 9.04 repository?"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by legolas_w on 2009-05-21
Hi
thank you for reading my post.
Can someone please let me know whether OpenOffice 3.1 will find its way into ubuntu 9.04 repository or I should install if from source?

Thanks

---

### Post by kpkeerthi on 2009-05-21
Possibly. But until someone [backports]("https://wiki.ubuntu.com/UbuntuBackports") it, you can install it from here:
[https://edge.launchpad.net/~openoffice-pkgs/+archive/ppa]("https://edge.launchpad.net/~openoffice-pkgs/+archive/ppa")

---

### Post by Aearenda on 2009-05-21
Best not to install it until the build failures are fixed...

---

### Post by ad_267 on 2009-05-21
Never. Only security updates are included in release versions.

You'll have to use the PPA. It doesn't appear to be building all the packages successfully yet though so probably best to wait.

---

### Post by meborc on 2009-05-21
openoffice packages usually take a long time to end up in either backports or usable PPA packages... if no major bug is discovered in the version that is shipped with jaunty, there is no motivation for the maintainers to backport it...

to install it in jaunty, i used this guide that worked well - [http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml](http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml)

---

### Post by kpkeerthi on 2009-05-21
I upgraded to Ooo3.1 using the PPA successfully. No problems whatsoever.

---

### Post by Orion2000za on 2009-05-21
> **kpkeerthi said:**
> I upgraded to Ooo3.1 using the PPA successfully. No problems whatsoever.

i also did this but have no helpfiles... are you more lucky than me on that one?

---

### Post by ad_267 on 2009-05-21
> **kpkeerthi said:**
> I upgraded to Ooo3.1 using the PPA successfully. No problems whatsoever.

I get errors about half the packages being held back, maybe that's because my language is set to British English rather than American.

---

### Post by kpkeerthi on 2009-05-21
> **Orion2000za said:**
> i also did this but have no helpfiles... are you more lucky than me on that one?

Helpfiles? Well, I haven't checked. Never did that since I started using linux since 2006 :) I can check that for you when I get back home today and report back.

---

### Post by kpkeerthi on 2009-05-21
> **ad_267 said:**
> I get errors about half the packages being held back, maybe that's because my language is set to British English rather than American.

Not sure. I have en_US.

---

### Post by meborc on 2009-05-21
i would still use the HOWTO i linked in my earlier post ;)

---

### Post by kpkeerthi on 2009-05-21
> **kpkeerthi said:**
> Possibly. But until someone [backports]("https://wiki.ubuntu.com/UbuntuBackports") it, you can install it from here:
[https://edge.launchpad.net/~openoffice-pkgs/+archive/ppa]("https://edge.launchpad.net/~openoffice-pkgs/+archive/ppa")
If anyone is interested in installing Ooo 3.1 by commanline (much easier & quicker than the graphical solution posted at softpedia)

1. Open the sources.list (terminal command)
```

gksudo gedit /etc/apt/source.list

```
2. Add the repository. Copy these lines:
```

deb http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu jaunty main

``` Save and exit gedit.

3. Add the repository OpenPGP key (terminal command)
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 247D1CFF 

```

4. Upgrade (terminal command)
```
sudo apt-get update && sudo apt-get dist-upgrade
```

* The dist-upgrade will automatically resolve new packages to be installed, packages to be upgraded and/or removed, as necessary, during the upgrade process. See **man apt-get** for more info on dist-upgrade. It does not do a "distribution upgrade (one ubuntu release to the next)" as many would think.

---

### Post by kpkeerthi on 2009-05-21
> **kpkeerthi said:**
> Helpfiles? Well, I haven't checked. Never did that since I started using linux since 2006 :) I can check that for you when I get back home today and report back.

OK. The help files are not installed by default and it tells what package you need to install to fix it. There is nothing wrong with the PPA.

---

### Post by asandler on 2009-05-23
It tells you what package to install of course, but the package itself isn't available. The only help for OOo available is from version 3.0.

---

### Post by kpkeerthi on 2009-05-23
[http://packages.ubuntu.com/search?keywords=openoffice.org-help&searchon=names&suite=jaunty&section=all]("http://packages.ubuntu.com/search?keywords=openoffice.org-help&searchon=names&suite=jaunty&section=all")

---

### Post by TunaCanTommy on 2009-05-23
I did the "command-line" method suggested by kpkeerthi and got the following at the end of the upgrade . . . any idea what this means ? ? any problems here  ? ?

```
The following packages have been kept back:
  openoffice.org-base-core openoffice.org-core openoffice.org-gnome openoffice.org-gtk python-uno
0 upgraded, 0 newly installed, 0 to remove and 5 not upgrade
```d.

---

### Post by kpkeerthi on 2009-05-23
What command did you type? Post that as well.

---

### Post by growled on 2009-05-23
> **TunaCanTommy said:**
> I did the "command-line" method suggested by kpkeerthi and got the following at the end of the upgrade . . . any idea what this means ? ? any problems here  ? ?

```
The following packages have been kept back:
  openoffice.org-base-core openoffice.org-core openoffice.org-gnome openoffice.org-gtk python-uno
0 upgraded, 0 newly installed, 0 to remove and 5 not upgrade
```d.
That's because you have language files and other dependencies from OO 3.01 still on your system. If you go to this link posted on the first page:

[http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml](http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml)

You need to do this before OO 3.1 will install:

> sudo apt-get remove language-support-en language-support-translations-en openoffice.org-help-en-gb openoffice.org-l10n-en-gb openoffice.org-l10n-en-za thunderbird-locale-en-gb

I followed this guide and OO 3.1 installed perfectly for me.

---

### Post by TunaCanTommy on 2009-05-23
Got it . . . super !  Everything's working OK now.
Thanks for the assistance.

---

### Post by alphacrucis2 on 2009-05-23
> **TunaCanTommy said:**
> Got it . . . super !  Everything's working OK now.
Thanks for the assistance.

The PPA atcually looks to be in a bad state if you have a look you will see that the localisation packages have failed to build for either hardy, intrepid or jaunty. This would mean that while OO will work you will have no help files or support for any languages other than English.

---

### Post by TunaCanTommy on 2009-05-23
I have noticed that . . . English is fine with me.
Guess I'll have to wait a while for things to get sorted out with regard to the help files, etc.

---

### Post by legolas_w on 2009-05-24
finally I installed version 3.1. but it is very funny to see that splash screen still shows that OpenOffice version 3.0 is loadig instead of showing ubuntu 3.1

In the same way the about page shows version 3.0 in the graphical part and 3.1 in the text part. I attached the about window screenshot.[IMG]http://www.ubuntu-pics.de/bild/14943/figure07_1CfSIe.jpg[/IMG]

---

### Post by kayvee on 2009-11-07
Hi
I was wondering how I can install Openoffice 3.1 on Ubuntu Jaunty? I checked the Openoffice Scribblers PPA that was mentioned in this post but it is empty now... Is there any way to upgrade my Openoffice to 3.1 without upgrading to Karmic?

---

### Post by Hagar Delest on 2009-11-08
Yes you can: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by kayvee on 2009-11-08
> **Hagar de l'Est said:**
> Yes you can: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

Thank you very much. It worked perfectly.

---

