---
title: "flash plugin"
date: 2009-06-03
forum: New to Ubuntu
---

### Post by cpt.jack sparrow on 2009-06-03
Hi
I am on firefox 3 and am having problems installing adobe flash plugin
I tried the following
1.sudo apt-get install plugin-nonfree
2.followed the link for adobe flash plugin from you tube .deb ( with Gdebi....)
3..tar.gz for linux

But unfortunately nothing works...The package manager shows flashplugin as 'installed'
and I cant watch youtube videos...
expecting your learned replies
Thank you

---

### Post by Celauran on 2009-06-03
Sounds like you might have multiple copies of Flash installed, which is causing conflicts. I'd recommend removing what you've already installed and grabbing the .deb from the Adobe site.

---

### Post by stephanvaningen on 2009-06-03
Do you have Ubuntu-64bit installed?

---

### Post by cpt.jack sparrow on 2009-06-03
how to remove the already installed copies???

I think its 32bit...

---

### Post by Celauran on 2009-06-03
> **cpt.jack sparrow said:**
> how to remove the already installed copies???
Easiest way is to open Synaptic, search for flash, and uninstall them.

---

### Post by Lightsaber™ on 2009-06-03
Make sure you have 32 bit flash player if you're running 32 bit Ubuntu and 64 bit for 64 bit.

---

### Post by izizzle on 2009-06-03
Rn this: ```
wget http://queleimporta.com/downloads/flash10_en.sh
``` then this: ```
sudo bash ./flash10_en.sh
```

---

### Post by cpt.jack sparrow on 2009-06-03
Hi
 I tried both in the konsole and everything looked fine....( flash plugin installed..you may restart firefox ..etc) except that its not working...I still cant watch youtube videos....

---

### Post by Celauran on 2009-06-03
You may need to delete your ~/.mozilla and/or ~/.adobe directories

---

### Post by cpt.jack sparrow on 2009-06-03
shud i delete it now?
can u please post the commands 
thank you

---

### Post by Celauran on 2009-06-03
Backup your bookmarks before doing that, because they will be lost otherwise. Then open a console and type

EDIT: Actually, on second thought, probably better to move than delete

```
mv /home/yourusername/.mozilla /home/yourusername/.mozilla.bak
mv /home/yourusername/.adobe /home/yourusername/.adobe.bak
```

---

### Post by cpt.jack sparrow on 2009-06-03
I ran the first command but with the second I got this mv: cannot stat `/home/sreejith/.adobe': No such file or directory

---

### Post by eMJayy on 2009-06-03
I had a similar problem recently after I had done a fresh installation of Jaunty. 

Basically, what's happening is that the adobe flash plug-in is installed but FF is also using another flash plug-in that is not from adobe. I don't remember the name of that extra flash plug-in but i found out which one it was by going to a website that uses flash ad banners (I went to [CNN.com]("http://www.cnn.com")) and right clicked a frame where  flash failed to render. That gave me the name of the plug-in that was causing interference with FF's use of the Adobe plug-in. Then I went into Synaptic, search for the plug-in and uninstalled it. After restarting FF, Adobe Flash 10 was working perfectly. 

In your Add-ons window in FF, you should only have *one* flash plug-in in the plug-ins section - Shockwave Flash 10.0r22. 

And in Synaptic, when you do a search for 'Flash', you should only have the following packages installed - 

[B]adobe-flashplugin (version 10.0.22.87-1)
flashplugin-installer (version 10.0.22.87ubuntu2)
flashplugin-nonfree (version 10.0.22.87ubuntu2)
libswfdec-0.8-0 (version 0.8.4-1)
ubuntu-restricted-extras (version 31)[/B]


You should have nothing else installed in the list of packages that comes up when you search for '*flash*' in Synaptic. I think the file I had to remove might have been *swfdec-mozilla*. I'm not absolutely sure it was the one, but it looks awfully familiar and it's **NOT** installed on my PC.

---

### Post by cpt.jack sparrow on 2009-06-03
this is what I get with adept..

---

### Post by cpt.jack sparrow on 2009-06-03
???!

---

### Post by eMJayy on 2009-06-03
> **cpt.jack sparrow said:**
> this is what I get with adept..

Here's what comes up when I search for 'flashplugin' in Synaptic

It does seem that you have the adobe flash 10 installed, but this search doesn't rule out that you don't also have other alternate plugins installed. You need to search for 'flash', not just 'flashplugin', as flashplugin will only bring up adobe's stuff. As long as you have more than one flash plugin installed, flash won't work.

---

### Post by cpt.jack sparrow on 2009-06-03
let me try that

---

### Post by cpt.jack sparrow on 2009-06-03
its a long list,but all of them are uninstalled..

---

### Post by eMJayy on 2009-06-03
> **cpt.jack sparrow said:**
> its a long list,but all of them are uninstalled..

If nothing in the list is installed then you don't have any flash plugins installed, at least not properly. You'll have to install adobe-flashplugin version 10 using Adept - that's the only way to ensure that the adobe-plugin has all the dependency files needed for it to work properly and to be upgraded automatically when new versions of the Adobe plugin are released.

---

### Post by Don1500 on 2009-06-03
Well, what video card do you have? Remember the older ATI cards are no longer supported by the latest ATI drivers. One of the problems I was having was the incompatability of Flash. I, too, coulden't view YouTube. I have since gone back to Intrepid on that machine. Actually, I can't tell the difference between Intrepid and Jaunty, except for the wallpaper, and the video works.

---

### Post by cpt.jack sparrow on 2009-06-04
hi
 I actually had flsh workin well but then I sort of 'uninstalled' wine and then its gone....Even though I uninstalled Wine the icon is still there..

---

### Post by Therion on 2009-06-04
Open Synaptic. 
Search on "SWF". 
In particular look for a package named **swf-mozilla-plugin**.  Something like that.  You'll know it when you see it.  
If it's installed, UN-install it.  
Try YouTube again.

---

### Post by cpt.jack sparrow on 2009-06-04
hi 
this is what I got for swf....

---

### Post by cpt.jack sparrow on 2009-06-04
this is what I get when I enter about:plugins.
Does this not mean that flash plugin is installed???

I am at my wits end to see that its near impossible to install a flash plugin in linux..I wonder why people use linux at all!!!

---

### Post by cpt.jack sparrow on 2009-06-04
hi

I tried the following
sudo apt-get install libdvdcss2
 "                    "     w32codec
 "                    "       ubuntu-restricted-areas  
 "                    "   flashplugin-nonfree

and for the last i got 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Could this problem be solved?I am having a tough time with linux.
Any help would be highly appreciated
Thank you

---

### Post by venator260 on 2009-06-04
Your last problem is caused by trying to use apt through the terminal and also having Synaptic open. You can't do that, it will return an error. 

As for your problem, what seems to be going on is that there is a conflict between the Adobe Flash plugin and the open source swfdec plugin. Both do the same thing, but the swfdec plugin doesn't work as well in some cases. 

What people are asking you to do is uninstall that plugin, because Firefox is trying to use it as opposed to Adobe's Flash plugin. 

To uninstall what the other posters in this thread are trying to get you to uninstall: 

```
sudo apt-get remove swfdec-mozilla
```

You may have multiple Flash packages installed. The only Flash package I have installed on my Jaunty system is flashplugin-installer. Uninstall everything Flash, and then just install flashplugin-installer 

See if that works


Edit: fixed incorrect terminal command.

---

### Post by ubername on 2009-06-04
Is it only youtube which doent't work (try [http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/))?
 I had a similar problem, which I think was caused by AdBlock. Try removing / disabling it if you are using it and see if that helps.

---

### Post by cpt.jack sparrow on 2009-06-04
hi

sreejith@zeroconf:~$ sudo apt-get uninstall swfdec-mozilla
E: Invalid operation uninstall
sreejith@zeroconf:~$

no the prob is not  restricted to youtube alone..

---

### Post by goldblattster on 2009-06-04
It isn't
```
sudo apt-get uninstall swfdec-mozilla
```
, it's
```
sudo apt-get remove swfdec-mozilla
```

---

### Post by cpt.jack sparrow on 2009-06-05
ok....shud I reinstall??

---

### Post by yamrjabhalla on 2009-06-05
bro if dnt get flash wrking even now thn let me now beacuse i am a begginer too bt i have solved this problem by a begginer way

---

### Post by baddnady23 on 2009-06-05
Hi,

I had the same problem and tried all sorts of things to mitigate it.  The one thing that worked like a charm was to just reinstall the whole distro and then install the ubuntu restricted extras package listed below.


```
sudo apt-get install kubuntu-restricted-extras

```

---

### Post by eMJayy on 2009-06-05
> **cpt.jack sparrow said:**
> this is what I get when I enter about:plugins.
Does this not mean that flash plugin is installed???

I am at my wits end to see that its near impossible to install a flash plugin in linux..I wonder why people use linux at all!!!

Hey, don't give up yet. The problem with flash in Linux is that there are several options being provided by different open source codec providers and they get in the way of each other and of the proprietary flash plugin that you want (and need) to install. For instance, when you install ubuntu-restricted-extras, it installs among other things, its own flash plug-in. That's the one *I* had to remove, but it appears that since you are using Kubuntu, it's a little trickier for me to help. **What I'm realizing now is that, because you are using Kubuntu packages, you may have packages containing codecs that I can't see on my Ubuntu installation.** I'm going to install the Kubuntu GUI alongside my Ubuntu so that I can 'see what you see' by switching to KDE sessions. 

Your last screenshot showing about:plugins was helpful, because it's showing that your browser is using something called **flash movie player**, which, according to what I'm reading, can either be a standalone player or supply a browser plugin. 

I searched Synaptic for **flash movie player** and found that there are four flash packages related to it (there may be more or less search results on yours, as you are using KDE instead of Gnome) and one of them is specifically used by *KDE and Konqueror*. 

I think what is happening in your case is that your FF3 is borrowing a flash plugin from Konqueror (flash movie player plugin as seen in your about:plugins list). Do a search in Adept for **flash movie player**, as that's the one that your about:plugins list is reporting that FF is using. If any of the search results are installed, you should uninstall them using Adept. The bottom line is that if your Konqueror browser is using a preinstalled flash plugin provided by your KDE setup, you need to find it and remove it, then install the Adobe flash player version 10 using Adept. 

I see that you're installing other codecs as well. I have a link for you that you should bookmark - [http://ubuntutip.googlepages.com/home](http://ubuntutip.googlepages.com/home)

The site linked above is a *VERY EASY* step by step guide for everything from installing Ubuntu to getting multimedia working....it's what I use each time to install my multimedia codecs and it only takes 15 minutes or less to do everything. The reality is that you don't need to run commands from the command line to get multimedia up and running. There's only one thing that you actually need the command line during multimedia setup and that is to get the DVD codecs that are only available in medibuntu (these let you play encrypted DVDs)....all the details and explanations are provided by the website so you actually know what you're doing when you do it.

---

### Post by RyanVanDiemen on 2009-06-05
> **cpt.jack sparrow said:**
> 
I am at my wits end to see that its near impossible to install a flash plugin in linux..I wonder why people use linux at all!!!

First thing after fresh install I always install medibuntu repository and then install kubuntu-restricted-extras

It installs flashplugin, win32codecs for playing divx, and other multimedia plugins. It`s actually easier than after installing WinXP, where you had to install every plugin (except mp3) sepearately...

---

