---
title: "How to Instlall Flash 7 if not on Synaptic"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by Barko1 on 2008-12-06
Hey all,

I'm pretty new to Linux but for the past 3 months or so I've been trying to re-invgorate a Toshiba PII 400mhz 192MB laptop.  
I've tried at least 8 distros, and thus far Fluxbuntu seems to be working best with this POS machine.

Problem is Flash.  I know this computer can run youtube on XP smoothly, but its choppy here.

I read around and it seems Flash 7 is way better for both Linux and the PII processor.  Flash 9 seems to hate both.  However, the Synaptic Package Manager only has 2 versions of Flash 9 I can install.

Somehow through reading around the internet I managed to download flashplugin-nonfree_7.0.63.3ubuntu3_i386.deb.

Not sure what to do with it though.  Even if I do get it installed how can I be sure the plugins for the browsers I use recognize it?  

THANKS MUCH ALL

---

### Post by Nano Geek on 2008-12-06
Make sure you uninstall Flash 9 first, then you should just be able to double-click the .deb you downloaded and the GUI will help you through the install.
That should be all you need to do.

---

### Post by binbash on 2008-12-06
if you have still troubles : 

[http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266&sliceId=2](http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266&sliceId=2)

download and install manually

---

### Post by Barko1 on 2008-12-06
Thanks for the quick responses guys.  It was quicker than the fluxbuntu boot.  

It says I need to set a "run action" either by dragging on an application or entering a shell command.
What should I enter?

And even when that does work, will this Flash automatically install itself on all the browsers?  Or do I need to find the specific browser plugin in the package manager?

---

### Post by pdtpatrick on 2008-12-06
So are you trying install flash for firefox?

---

### Post by Barko1 on 2008-12-06
> **pdtpatrick said:**
> So are you trying install flash for firefox?

Not particularly concerned with any browser.  I figure there are lighterweight browsers.  I have Konqueror,  the pre-installed Kazekhase and Icecape loaded.   Any recommendations?  Not sure what would be the best, and how to associate the flashplayer in the browser.  If there is no specific plugin, is it possible?

My goal is just to make a basic laptop with wireless, and be able to run mainstream sites like youtube, view pictures off and play videos from my camera.  

Also still not sure what command line to enter to run .deb files...

---

### Post by chrisod on 2008-12-07
Install the Ubuntu Restricted Plugins package via Add/Remove. Flash is included, along with MP3 and the other proprietary media stuff.

---

### Post by bwang on 2008-12-07
Download the file from adobe, and extract the appropriate file (there are some tar.gz files inside the zip, so extract the tar.gz's from the zip and then extract the tar.gz files)

Open a terminal, and cd to the directory where you extracted the files.

Type:
```

chmod +x flashplayer-installer
./flashplayer-installer

```

---

### Post by Nano Geek on 2008-12-08
I think, not sure, but I think that flash will automatically install itself when you install the .deb. 

And to install the .deb all you should need to do is to double-click it. A program should come up to help you finish installing it.

---

### Post by Barko1 on 2008-12-09
> **asjdfwejqrfjcvm msz34rq33 said:**
> I think, not sure, but I think that flash will automatically install itself when you install the .deb. 

And to install the .deb all you should need to do is to double-click it. A program should come up to help you finish installing it.

No thats my problem.  It is asking what program (or command line) I wish to run the .deb file.  I don't know what to put.

And as for the other suggestions, I already have a flash7.deb file sitting in my main directory.  I shouldn't need to tool with a general package or anything from Adobe right?

---

### Post by Joeb454 on 2008-12-09
If the .deb file is in your home directory, and you want to use the CLI to install, run ```
sudo dpkg -i ./flash_player_installer.deb
``` (that last part depends on the filename ;))

---

### Post by Barko1 on 2008-12-09
> **Joeb454 said:**
> If the .deb file is in your home directory, and you want to use the CLI to install, run ```
sudo dpkg -i ./flash_player_installer.deb
``` (that last part depends on the filename ;))

Yes that worked!

BUT (there is always a but)

I can't get flash in any other browser to use it but firefox 2.  And I don't even think that worked correctly, as soon as I went to youtube it downloaded some package.  I thought it would be for Flash 7, but it appears I've been updated to Flash 10.  I don't want Flash 10!

Oddly enough, the Synaptic Package Manger still claims I am running Flash 7?

Either way, how would I get the Flash 7 install to be recongized on the other browsers?  There is no plugin installer for flash on any other browser.  

Thanks so much everyone for staying with my thread!

---

### Post by Nano Geek on 2008-12-11
Is there a specific browser that you want Flash in. It might help to know which one you were trying for.

---

### Post by Sef on 2008-12-11
Flash 7 may not work with a lot of sites.   The current Flash is 10.   That may work better for you than Flash 9.   You did try Flash 9, correct?

---

### Post by Barko1 on 2008-12-12
> **asjdfwejqrfjcvm msz34rq33 said:**
> Is there a specific browser that you want Flash in. It might help to know which one you were trying for.

I'd be happy with any browser but right now I figure it would be easiest to get started with firefox.

> **Sef said:**
> Flash 7 may not work with a lot of sites.   The current Flash is 10.   That may work better for you than Flash 9.   You did try Flash 9, correct?

Yes, I did try Flash 9, it and Flash 10 didn't work so hot.  I may have to accept the fact that Flash may never work well with this combo of hardware + Linux.   But I'd at least like to attempt see how Flash 7 runs. 

I managed to completely remove Flash 10 and re-installed Firefox 2, Flash 7.  And through synaptic, Libflash0c2 and libflash-mozplugin.

I went to a flash test version page and said I did not have flash installed at all.  
What am I doing wrong?  THanks all

---

### Post by Barko1 on 2008-12-16
don't mean to bump if its against the rules, but I'm still adrift.  Perhaps I have to copy files to various browser directories?

---

### Post by Nano Geek on 2008-12-23
I'm sorry I've been away so long, but does this help you any?

[https://answers.launchpad.net/ubuntu/+source/firefox/+question/1822](https://answers.launchpad.net/ubuntu/+source/firefox/+question/1822)

---

### Post by igknighted on 2008-12-23
There's a deb for flash 7 here: [http://packages.ubuntu.com/dapper/flashplugin-nonfree](http://packages.ubuntu.com/dapper/flashplugin-nonfree)

---

### Post by LowSky on 2008-12-23
> **Barko1 said:**
> Hey all,

I'm pretty new to Linux but for the past 3 months or so I've been trying to re-invgorate a Toshiba PII 400mhz 192MB laptop.  
I've tried at least 8 distros, and thus far Fluxbuntu seems to be working best with this POS machine.


Just so you know, many website are running newer version of Flash, so using an outdated version like 7 may not work on all websites.

Have you tried, Puppy or DSL or even staight vanilla debian? All  run on lower end machine alot better than Ubuntu.

---

### Post by Barko1 on 2008-12-26
> **asjdfwejqrfjcvm msz34rq33 said:**
> I'm sorry I've been away so long, but does this help you any?

[https://answers.launchpad.net/ubuntu/+source/firefox/+question/1822](https://answers.launchpad.net/ubuntu/+source/firefox/+question/1822)

This thread well never die!
Yes, that link really did help here.   From reading it, I downloaded a different package.
"install_flash_player_7_linux.tar.gz" instead of nonfree-flashplugin-ubuntu 
This package actually asked for my firefox directory during the installation process.  

welp anyway, flash 7 wasn't any less choppy than flash 9 or 10 for this old system.  At least I learned quite a bit from this venture.  Thanks all again for the attention.



> **LowSky said:**
> Just so you know, many website are running newer version of Flash, so using an outdated version like 7 may not work on all websites.

Have you tried, Puppy or DSL or even staight vanilla debian? All  run on lower end machine alot better than Ubuntu.
Yeah I tried flash 9 and 10, and they all were choppy.  As 7 wasn't any better, I may just have to accept the hardware limitations of this computer.

Puppy has quite a many issues with Toshiba laptops, specifically in the video driver portion.  DSL doesn't even seem to boot.  Haven't tried straight vanilla debian though.

---

