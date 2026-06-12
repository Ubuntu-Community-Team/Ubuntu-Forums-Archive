---
title: "Some questions re the Remix please"
date: 2010-12-29
forum: New to Ubuntu
---

### Post by mikeody on 2010-12-29
Am not an absolute beginner but today I rather think I am !
Have been using Ubuntu desktop for a while and have been impressed. I thought I would instal the Netbook Remix on a fairly new Netbook.
After mastering a series of traumatic installation problems, I am now 'exploring' the Remix. Isnt it slow to boot !

I have 3 immediate problems.

1. Firefox wont open certain web pages [it did on my desktop]. I am told it is something to do with Flash player, Can any one advise on the fix please?

2. I transferrd a number of .deb files from my desktop with a view to installing them on the Netbook. A double-click on the .deb on the desktop usually gave fairly trouble free install. On the remix I seem to go around and around accepting this and that but still dont get an install. Would it be best to use the terminal and forget all the bells and whistles ?

3. And finally, for now anyway, has anyone anywhere written an 'idiots guide' to using that awful new desktop ? If not, is there a simple way to dump it in favour of the traditional desktop used on the desktop versions ?

thanks.

---

### Post by trinitydan on 2010-12-29
You can solve all three of those problems by selecting "Desktop Session" (or it's something close to that anyway) from the pull down menu at the log in window and it will log you in to the normal gnome desktop environment.  Then you can just customize that to look like something that actually belongs on a netbook!  All three problems solved.  ;)

(Sorry, I was kind of kidding about the first two problems.  Someone will probably offer a better answer for those.)

---

### Post by mcduck on 2010-12-29
1. Install the flash plugin. ;)

The simplest way is to install the ubuntu-restricted-extras-package, which would give you Flash plugin, bunch of non-free audio/video codecs and some other stuff that can't be included in the default install. Of ocurse you can just use your packge amnager of choice and install only the flash plugin package.

2. Yep, a terminal would be a good option if you are having troubles. If nothing else,a t least it will give you an error message that you can post here so people can help you to figure out what's the problem...

3. No idea about such guide. :D

..but getting the default desktop is as easy as installing the "ubuntu-desktop" package, and then selecting "Ubuntu Desktop Edition" as your session in the login screen. (It might not be such a great setup for a low-resolution netbook screen, but with a well selected GTK theme, some gconf tweaks, and arranging the panels to better fit the small vertical resolution it should be usable. Although I'd probably go for a minimalistic Openbox setup if I had a netbook...)

---

### Post by audiomick on 2010-12-29
For point one, as has been said, install ubuntu-restricted-extras.

Can't help with the .deb packages, although I seem to recall something about gdebi not being installed by default in some version or other. Might be related, might not...


As far as the UNR desktop goes, yes, I found it odd to start with. Here are the main insights which helped me get to rather like using it.

A right click on the cross in the upper title bar of the open window will give you a menu offering "minimise" and such like, allowing you to get the window away from it's anchored and maximised position.

A click on the menu symbol in the top left will fold up the open window and bring you back to the "front page", from where you can open a new program.

When you have several windows open, you can go from one to the other by clicking on the icons in the bar at the top left.


Hope that helps you.

---

### Post by trinitydan on 2010-12-29
> **mcduck said:**
> 
3. No idea about such guide. :D

..but getting the default desktop is as easy as installing the "ubuntu-desktop" package, and then selecting "Ubuntu Desktop Edition" as your session in the login screen. (It might not be such a great setup for a low-resolution netbook screen, but with a well selected GTK theme, some gconf tweaks, and arranging the panels to better fit the small vertical resolution it should be usable. Although I'd probably go for a minimalistic Openbox setup if I had a netbook...)

I thought you could just select it from the menu?  That's what I did when I went through the same the as the OP where I installed UNR and really didn't like it.  I came on here asking how to get it back to what I wanted and found out all I had to do was select desktop session from the pull down.  Has something changed?

I think Ubuntu 10.10 desktop works fine on a netbook.  I don't change it from the default resolution or anything.  I just set both the panels to autohide to maximise screen space and it works fine for me.  That said, I am on my netbook right now running a minimal openbox environment (#!) so I guess I have to say you are right.  :D

---

### Post by mcduck on 2010-12-29
> **trinitydan said:**
> I thought you could just select it from the menu?  That's what I did when I went through the same the as the OP where I installed UNR and really didn't like it.  I came on here asking how to get it back to what I wanted and found out all I had to do was select desktop session from the pull down.  Has something changed?

I think Ubuntu 10.10 desktop works fine on a netbook.  I don't change it from the default resolution or anything.  I just set both the panels to autohide to maximise screen space and it works fine for me.  That said, I am on my netbook right now running a minimal openbox environment (#!) so I guess I have to say you are right.  :D

I'm not sure if it's installed by default or not. If it is, then you can of course just select it from the login screen without having to install it separately. :)

But true, even the default Gnome setup is quite usable on a netbook. Much better than WinXP/7 thos things tend to ship with anyway. :D 

Of course some program windows are too large to even fit on the screen, and everything else requires a lot of scrolling. But those things are pretty much something you have to live with if you use a netbook, and whatever you tweak can only make things a bit better. I supose it's just that I have the habit of making things better if I can, even if the improvement is just something small. ;)

I'd actually like to try a command-line only setup on a netbook. Might work surprisingly well, plus I'd never have to touch the horrible small touchpad those things usually have... :D Of course Openbox with well set keyboard shortcuts is pretty good for avoiding the touchpad as well.

---

### Post by mikeody on 2010-12-30
Thanks everyone for the huge response.
Since posting the questions I have installed desktop 10.04 on the netbook and it runs perfectly - apart from an interminable boot time - literally 6 minutes !!
The firefox issue is still the same but I will hunt down that 'ubuntu restricted extras package'.
Thanks again.

---

### Post by trinitydan on 2010-12-30
> **mcduck said:**
>  Although I'd probably go for a minimalistic Openbox setup if I had a netbook...)

> **trinitydan said:**
> I am on my netbook right now running a minimal openbox environment (#!) so I guess I have to say you are right.  :D

> **mikeody said:**
>  I have installed desktop 10.04 on the netbook and it runs perfectly - apart from an interminable boot time - literally 6 minutes !!


You might want to consider a minimal openbox environment.  6 minutes is unacceptable.  My netbook boots CrunchBang "Statler" in 25 seconds.  Granted it is a pretty fast netbook, all solid state, but still, I think you could expect boot time well under a minute (even Ubuntu 10.04 I would expect to boot in about 1 minute).  Performance is also snappy using distros like CrunchBang that are super easy on the resources.  I don't know how you get a verbose boot out of 10.04, but at the very least I would try to see what it is hanging up on for so long during boot up.

---

### Post by mikeody on 2010-12-30
Hey Trinitydan,
Have just spent a while researching crunchbang and am minded to try it.
My frustration is that I have  a fairly new netbook [Toshiba NB300, Atom CPU, 200GB SSHD, 1 Gb RAM] yet I have been plagued by problems with the Ubuntu Netbook Remix.
So much so that I have now put Lucid on the netbook [have been running Lucid on my desktop for a fair while]. It runs really well on the netbook but it is taking 6 mins plus to boot yet it boots in less than a minute on the fairly low powered desktop. No one seems able to figure it - I expected it to be slower but not by that much.
Anyway re Crunchbang.
All I am chasing is a simple, reasonably easy to use OS for the netbook that can easily access internet wirelessly, run Open Office, email etc and allow me to tinker with software such as NMap and Metasploit. No networking.
Any thoughts on all that before I download the ISO ?
Thanks again.

---

