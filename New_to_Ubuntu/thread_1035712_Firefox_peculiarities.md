---
title: "Firefox peculiarities"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by Bruv on 2009-01-10
I have recently installed Kubuntu, but have been using Firefox in windows for some time.
I have found some websites dont load the same when using it in Kubuntu, is this due to the site or my settings ?
I dont know of any settings changes that I could alter to rectify this, does anyone know why this is happening ?

---

### Post by albinootje on 2009-01-10
> **Bruv said:**
> I have recently installed Kubuntu, but have been using Firefox in windows for some time.
I have found some websites dont load the same when using it in Kubuntu, is this due to the site or my settings ?
I dont know of any settings changes that I could alter to rectify this, does anyone know why this is happening ?

Can you be more specific ?

Unfortunately there are some Firefox plugins which are available for Windows and not for Linux.

[http://plugindoc.mozdev.org/](http://plugindoc.mozdev.org/)

For the rest, playing webpage *embedded* audio and video can sometimes be a pain in Linux or simple impossible without finding out the real link to the embedded audio or video and using that.

You can give the Firefox add-on "mediaplayerconnectivity" a try.

For the BBC website, thanks to Canonical, there's now a new BBC-plugin for totem media player (available in 8.10), which works pretty well for BBC audio archives.

---

### Post by linux_tech on 2009-01-10
Make sure you have flash and java installed

```

sudo apt-get install adobe-flashplugin

sudo apt-get install sun-java6-jre sun-java6-plugin

```

---

### Post by Bruv on 2009-01-10
I am not talking about 'complicated' sites but sites with no super dooper affects such as the one for pc advisor (Is that allowed ? mentioning other sites)

How do I install flash and java ?
Is it as simple as opening a terminal and adding the script ?

---

### Post by albinootje on 2009-01-10
> **Bruv said:**
> I am not talking about 'complicated' sites but sites with no super dooper affects such as the one for pc advisor (Is that allowed ? mentioning other sites)

How do I install flash and java ?
Is it as simple as opening a terminal and adding the script ?

Can you provide the full link for that pc advisor website ?
And explain what the problem is within Firefox on Linux ?

If you've installed the 32-bit version of Ubuntu (The 64 bit version needs other instructions), run the following in a terminal :
```

sudo apt-get install flashplugin-nonfree flashplugin-nonfree-extrasound sun-java6-jre sun-java6-plugin

```
Make sure, at the point that the Java License agreement is shown, to press <tab> to get the focus on the [OK] button, and after that, press <enter>

Restart Firefox after that, type in the url field :
```

about:plugins 

```
to check whether the plugins are available.

---

### Post by Bruv on 2009-01-10
The full link is [http://www.pcadvisor.co.uk/](http://www.pcadvisor.co.uk/) and the problem is that it squashes into the centre of the monitor widthwise , making it unreadable.
To be honest I don't know what version of kubuntu I have installed, I am almost illiterate computors and all they entail.

---

### Post by albinootje on 2009-01-10
> **Bruv said:**
> The full link is [http://www.pcadvisor.co.uk/](http://www.pcadvisor.co.uk/) and the problem is that it squashes into the centre of the monitor, making it unreadable.
To be honest I don't know what version of kubuntu I have installed, I am almost illiterate computors and all they entail.

I just tried that website in Firefox, Galeon, and Konqueror, and I don't see any problems.

To check what you are running, please post the output of :
```

lsb_release -a
uname -a
dpkg -l firefox

```

---

### Post by Bruv on 2009-01-11
As requested the information you asked for, it is all gobbledegook to me....

bruv@bruv-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.04.1
Release:        8.04
Codename:       hardy

Linux bruv-desktop 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  firefox        <none>         (no description available)
bruv@bruv-desktop:~$


I am sure you will know what the problem is though.

---

### Post by albinootje on 2009-01-11
> **Bruv said:**
> 
||/ Name           Version        Description
+++-==============-==============-============================================
un  firefox        <none>         (no description available)


You wrote earlier that you're using Kubuntu.
By default Kubuntu doesn't install Firefox afaik.

Did you download Firefox from the mozilla webpage ?
If not, install it like this :
```

sudo apt-get install firefox

```

---

### Post by Bruv on 2009-01-11
I think I did download it, it is in the list of programs available which a ticked to install but then couldn't find if it installed or not.
Sorry for being vague, this a new system of install to me

---

### Post by albinootje on 2009-01-11
> **Bruv said:**
> I think I did download it, it is in the list of programs available which a ticked to install but then couldn't find if it installed or not.
Sorry for being vague, this a new system of install to me

OK. :)
Can you try this instead :
```

sudo apt-get update
sudo apt-get install --reinstall firefox 
sudo apt-get install flashplugin-nonfree flashplugin-nonfree-extrasound

```

---

### Post by Bruv on 2009-01-11
I think everything went OK until last part.....


flashplugin-nonfree is already the newest version.
Package flashplugin-nonfree-extrasound is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package flashplugin-nonfree-extrasound has no installation candidate

---

### Post by Bruv on 2009-01-11
Do I need to do anything such as uninstall the Forefox version I had already, because the site remains the same as before when using it.

---

### Post by albinootje on 2009-01-11
> **Bruv said:**
> Do I need to do anything such as uninstall the Forefox version I had already, because the site remains the same as before when using it.

You can do :
```

sudo apt-get remove --purge firefox firefox-*

```
Then see whether Firefox still starts... :)
After that :
```

sudo apt-get install firefox galeon midori

```

Please test the other browsers konqueror, galeon and midori too, and compare that with the results in firefox.

---

### Post by Bruv on 2009-01-11
I only have konqueror and firefox installed, but konqueror shows the site OK.
 I have just had a strange event from konqueror, while visiting a forum I happened across a thread with a youtube video embedded, the browser froze then went crazy with many vidoes opening across the monitor,even after attempting to close konquerer, I clicked on each one to close them then they disappeared, as if by magic.
I have watched other embedded videos without problem, although at other times I get a warning.
Could this be related to the other problem ?

---

### Post by Bruv on 2009-01-11
The site is OK in midori galleon and konqueror, but remains the same in firefox.

---

### Post by ajcham on 2009-01-11
Could you post a screenshot of the badly rendered page?

---

### Post by Bruv on 2009-01-11
> **ajcham said:**
> Could you post a screenshot of the badly rendered page?
I shall try.....I am finding my way around this new OS

---

### Post by albinootje on 2009-01-11
[Edited].. removed wrong suggestion, forgot it was about Kubuntu, not Ubuntu.

---

### Post by ajcham on 2009-01-11
> **Bruv said:**
> I shall try.....I am finding my way around this new OS

KSnapshot should be installed - check the Graphics menu.  (actually, in my experience PrtScr is usually mapped to launch this app, but I've not used KDE/Kubuntu for a while).

---

### Post by Bruv on 2009-01-11
I have taken the snapshot, and have located where it is (bear with me please) and gone to photobucket to upload it, but now I get the folder opening wide across my monitor so I have to drag it to see it all.

Here goes..[IMG][IMG]http://i2.photobucket.com/albums/y45/abbies/snapshot1.png[/IMG][/IMG]

You dont know the trouble that has taken.....

---

### Post by ajcham on 2009-01-11
What happens if you press ctrl+0 (zero) in Firefox?

> &#8230;gone to photobucket to upload it, but now I get the folder opening wide across my monitor so I have to drag it to see it all.
Yeah, I use Photobucket and their upload dialog screws up becuase of the huge list of possible file extensions.

---

### Post by Bruv on 2009-01-11
What happens ?
It solves the problem....that's all.

It cannot be that easy can it ?

The folder that was causing the problem in photobucket was the one that opens when you choose to upload from your PC.
In windows I can find my my around, but I am new to how Kubuntu works, but I am sure that is not the way it should happen.

---

### Post by ajcham on 2009-01-11
> **Bruv said:**
> What happens ?
It solves the problem....that's all.

It cannot be that easy can it ?
:p You were zoomed out is all, ctrl+0 restores the default zoom settings.

---

### Post by ajcham on 2009-01-11
> **Bruv said:**
> The folder that was causing the problem in photobucket was the one that opens when you choose to upload from your PC.
In windows I can find my my around, but I am new to how Kubuntu works, but I am sure that is not the way it should happen.

It's not the folder that causes the problem, it's the combo box that says *'Image and Video Files (*.gif, *.jpg … …)'*

---

### Post by Bruv on 2009-01-11
Well Ill be buggered, and it has retained that for that site alone even though the browser has been closed un-installed,and re-installed ?

Or at least that is what I thought the rest of this thread has been about.....I am not saying that in a bad way, just amazement.

---

### Post by albinootje on 2009-01-11
> **Bruv said:**
> Well Ill be buggered, and it has retained that for that site alone even though the browser has been closed un-installed,and re-installed ?

Or at least that is what I thought the rest of this thread has been about.....I am not saying that in a bad way, just amazement.

Was your Kubuntu installation completely new ? No restoring from backups at all ?
Try :
```

firefox -P

```
Create a new profile, and see whether that one has problems too.
Make sure to choose your Profile Name correctly when you want to get back to your default profile next time you start Firefox.

---

### Post by Bruv on 2009-01-11
> **ajcham said:**
> It's not the folder that causes the problem, it's the combo box that says *'Image and Video Files (*.gif, *.jpg … …)'*

I see what you are saying, I am on photobucket now, in konqueror and it just doesn't play the game some how, I tried to replicate the problem, but the 'choose files' button is not reacting.
I shall return to firefox,now its working I know what Im doing with that.

---

### Post by Bruv on 2009-01-11
> **albinootje said:**
> Was your Kubuntu installation completely new ? No restoring from backups at all ?
Try :
```

firefox -P

```
Create a new profile, and see whether that one has problems too.
Make sure to choose your Profile Name correctly when you want to get back to your default profile next time you start Firefox.

Sorry you are blinding me with science, if I was in windows I would copy and past that information and keep it for future reference in notepad, but as I keep saying, I am still finding my way around here.

---

### Post by ajcham on 2009-01-11
> **Bruv said:**
> Sorry you are blinding me with science, if I was in windows I would copy and past that information and keep it for future reference in notepad, but as I keep saying, I am still finding my way around here.

I wouldn't worry about it.  I don't think creating a new profile is necessary - the problem is sorted now so I think it can be left at that really.

> Well Ill be buggered, and it has retained that for that site alone even though the browser has been closed un-installed,and re-installed ?

Firefox stores the zoom preferences in your profile and this is left untouched when you uninstall/reinstall Firefox.

---

### Post by Bruv on 2009-01-11
I am impressed, most applications would forget preferences such as zoom when the session ended.

Thanks for your help I am learning lots as I go along, suspect I shall be back asking more simple questions.

---

### Post by minsf on 2009-01-11
> **Bruv said:**
> if I was in windows I would copy and past that information and keep it for future reference in notepad, but as I keep saying, I am still finding my way around here.
try runnung ```
kate
``` from the command line. this should open a text editor in kubuntu. i am sure there is a way to get it from the menu bar (maybe Applications>Accessories>Text Editor ?) but I am using gnome, so i am not sure how. 

this text editor should be able to do all notepad did (and probably more).

---

### Post by minsf on 2009-01-11
> **Bruv said:**
> Well Ill be buggered, and it has retained that for that site alone even though the browser has been closed un-installed,and re-installed ?

Or at least that is what I thought the rest of this thread has been about.....I am not saying that in a bad way, just amazement.

one little explanation might be that you removed the package, not purged it. that is you used a command like
```
sudo apt-get remove package_name
```
(and then "sudo apt-get install package_name"). or maybe you used 
```
sudo apt-get install --reinstall package_name
``` which is equivalent to first removing and then installing.

the point is, that removing a package does not delete the configuration files, only delete the binaries. if you really want to remove all the files INCLUDING the configuration files, you use
```
 sudo apt-get purge package_name
```
(and then install it again).

it is better not to purge, unless you are sure that you dont need the configuration files. i'm just posting this to explain the mystery.

of course, in the above, package_name was "firefox" (actually it's a meta-package that includes many small firefox packages together).

---

### Post by MickS on 2009-01-11
> **Bruv said:**
>  I was in windows I would copy and past that information and keep it for future reference in notepad, but as I keep saying, I am still finding my way around here.

As you are on Kubuntu try installing Knotes for storing stuff, that's what I use it has the advantage of being dead simple to use, no fancy stuff to learn, you might already have it.

Mick

---

### Post by Bruv on 2009-01-11
@ minsf
A bit like deleting the shortcut in windows ? But not the program ?
I don't know what method I used because I was following instructions from this thread.
It is a steep learning curve having only installed kubuntu in the last few days after being on windows since using a PC.
There is a lot to learn, I shall take it easy and ask before I leap into the unknown.

@ MickS

I actually found Knotes as I was talking about notepad earlier in this thread. Better than notepad because it remains saved until deleted, a very handy tool.

---

### Post by MickS on 2009-01-11
BTW I have just been uploading some photos to photobucket and have the same problem with the window being too wide but I have found that if you double click on the image you want it uploads it without having to move the window to find the button, also if you hold control and highlight several images and double click on the last one whilst still holding control it uploads all of them, hope that helps.

Mick

---

### Post by minsf on 2009-01-12
> **Bruv said:**
> @ minsf
A bit like deleting the shortcut in windows ? But not the program ?
yes sort of the same idea. a better analogue is uninstalling a program in windows without removing its registry keys. that is, say you install firefox in windows with the "install sheild" or whatever this is called (it is analogue to the "apt-get" tool, but the latter is more powerful- it has way more options for you to control it, rather than just pressing "next"...). say then firefox creates a registry key that specify some directory for your bookmarks. now let's say you uninstall firefox. the uninstaller sometimes leave the registry key. it may be good to leave this key (because, if you install firefox again, your bookmark directory will be the same as the first installation) and it may be bad (it may clutter your registry). 
but the point is that in windows you have no control- sometimes the registry keys are removed when you uninstall, and sometimes not and you have to manually edit your registry to remove them. with apt-get you have the control: use "remove" to leave the configuration files, and use "purge" to clean them too.

the shortcuts in windows are more like the launchers that you can create on the desktop, or like the symbolic links that you can create with the "ln" command in the terminal/konsole. they just point to a physical file, so when you remove them the file still exists. type "man symlink" in the terminal/konsole to learn more. (or point your firefox to "man:symlink")

> 
I don't know what method I used because I was following instructions from this thread.

My guess is you were probably following the commands in post #11 by albinoo that include "apt-get install --reinstall", and not his post #14 about purging. that's probably why the configuration files were left. but there can be other reasons.

if all of this is still overwhelming, dont worry- remember i'm a newbie too- only a month. 
here's a great link to explain installations:
[http://ubuntuforums.org/showthread.php?t=781352](http://ubuntuforums.org/showthread.php?t=781352)

---

### Post by minsf on 2009-01-12
since zooming solved your problem, let me post one more link about firefox shortcuts that you may find useful:
[http://support.mozilla.com/en-US/kb/Keyboard+Shortcuts](http://support.mozilla.com/en-US/kb/Keyboard+Shortcuts)
in particular, to zoom in you use ctrl and +, to zoom out ctrl and -, and to bring nack to the default zoom ctrl and 0. 
have fun :)

---

### Post by Bruv on 2009-01-12
Many thanks I have bookmarked all those links for later.

Bit more friendly in here than some forums I have visited.

---

