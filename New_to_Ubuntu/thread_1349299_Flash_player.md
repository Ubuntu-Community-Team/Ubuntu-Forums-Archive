---
title: "Flash player"
date: 2009-12-08
forum: New to Ubuntu
---

### Post by Drawstop on 2009-12-08
My PC tells me that I need to download and install the latest Flash Player.
 I can download it alright but I have no idea how to install it. Please can someone help?
Many thanks.

---

### Post by N00b-un-2 on 2009-12-08
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by candtalan on 2009-12-08
> **Drawstop said:**
> My PC tells me that I need to download and install the latest Flash Player.
 I can download it alright but I have no idea how to install it. Please can someone help?
Many thanks.

The usual and easiest approach is to install Ubuntu restricted extras from the add/remove (or software centre) in Applications menu. Choose 'All available' first.

However it is possible that the version held in the repositories is not actually the *very* latest. If you then find that it is truly critical to have the latest, not often needed though, you can download in other ways, but people here will help with that.

hth

---

### Post by fancypiper on 2009-12-08
To use the 64 bit version, you will have to download Get64bitFlash from the Adobe download site.

[Comprehensive Multimedia & Video Howto](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by MelDJ on 2009-12-08
see this too: [How to install ANYTHING in Ubuntu!]("http://amitech.50webs.com/installing/index.php.html#installing_a_package_manually")

---

### Post by Drawstop on 2009-12-26
> **N00b-un-2 said:**
> ```
sudo apt-get install flashplugin-nonfree
```
Thanks for reply. I have tried pasting this into terminal but cannot get anyjoy.What am I doing wrong?
Many thanks
Richard

---

### Post by Gone fishing on 2009-12-26
Goto synaptic (system > administration) Then goto settings > repositories and make sure you have all the repositories enabled reload and the you should be able to install either from synaptic or apt-get

---

### Post by Drawstop on 2010-01-05
> **Drawstop said:**
> Thanks for reply. I have tried pasting this into terminal but cannot get anyjoy.What am I doing wrong?
Many thanks
Richard
Have tried the above but synaptic just goes blank.  I am annoyed that Windows 7 works perfectly but I do not understand Ubuntu and am worried that I shall have to ditch it and stick to Windows.  I can download flashplayer but I do not know how to install it.
Any help (needs to be detailed for an elderly newbie) would be much appreciated.
Thanks
Drawstop.

---

### Post by Drawstop on 2010-01-05
> **N00b-un-2 said:**
> ```
sudo apt-get install flashplugin-nonfree
```
Have typed in the above and was asked for my password.  That worked but I was told that it could not find flashplugin - non free. So where do I go from here?
Many thanks.
Drawstop.

---

### Post by Methuselah on 2010-01-05
> **Drawstop said:**
> Have typed in the above and was asked for my password.  That worked but I was told that it could not find flashplugin - non free. So where do I go from here?
Many thanks.
Drawstop.

Go to software sources in the administration menu and make sure that the 'multiverse' repository is checked.
Basically, all of the first four should be checked.

---

### Post by 3rdalbum on 2010-01-05
You've got to help us to help you.

"I have tried pasting this into terminal but cannot get anyjoy.What am I doing wrong?" - doesn't help us. Did you get some sort of error message? If we know what response you got, then we know what is wrong.

Usually on Ubuntu you use Synaptic Package Manager or the "apt-get" command you used, to install software. For any software outside the package manager, you must follow the directions given with the software.

Adobe doesn't always provide instructions for Flash Player. Basically, you downloaded the Flash Player inside a .tar.gz archive. Extract it to a location you can get at easily.

Now you need to drag the contents into the "plugins" directory of the ".mozilla" folder, hidden in your home directory. Go to your home directory and press Control-H to view hidden files. Go to .mozilla and open it, and then create a new "plugins" directory here if one doesn't already exist. Drag the libflashplayer.so file into the plugins folder, and quit Firefox.

That's all there is to it.

---

### Post by Methuselah on 2010-01-05
He said flashpugin-nonfree not found.
I think he needs to enable the multiverse repository.

Go to the System->Administration->Software Sources menu then make sure the first four entires on the first tab are checked, especially the one that says (multiverse).
Close let, let it update then redo:

```

sudo apt-get install flashplugin-nonfree 

```

in a terminal.

---

### Post by Drawstop on 2010-01-06
Thanks everybody for your help.  Flashplayer is installed and working. ow I can watch all the videos of steam railways and church organs.  Thanks so much.  Have just chucked windows out of the window!

---

### Post by Evie~ on 2010-01-06
Thank you so much to 3rdalbum, you've made my YEAR! (Installed Ubuntu on New Year's day, been having trouble with an issue like this ever since :P)

First time I attempted to do this, I tried for four hours to find techniques, only to be bombarded with pages of commands to enter into the terminal.

THANK YOU!
:D

---

### Post by fancypiper on 2010-01-07
In Linux, the lowest common denominator is the command line. Bash is bash in all distros where as gui apps depend upon the window manager or desktop environment.

The command line is your friend.

---

