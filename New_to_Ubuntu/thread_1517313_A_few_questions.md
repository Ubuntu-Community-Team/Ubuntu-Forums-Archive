---
title: "A few questions"
date: 2010-06-24
forum: New to Ubuntu
---

### Post by one2fwee on 2010-06-24
So i'm hoping to start with ubuntu shortly, as i redo my computer.
First though, i have been backing up my documents and files and plan to do an xp / ubuntu dual boot.

Would it be best to install windows first and then ubuntu? Or the ubuntu first and then windows?

Also, i plan to make a backup image of the fresh xp root partition (probably with service pack 3) so that if i ever need to "redo" windows again, i can just copy that backup over the top rather than having to reinstall.
So i was wondering a good backup program - whether for windows, ubuntu or a seperate live disc or whatever - i had a bit of a look but it was all a bit confusing. It seems some are just for files whereas others can actually backup the operating system (which is what i guess i'd be needing).

However i never really thought of backing up my files before so it might be useful to get insight into general file backup too. I am all ears for any advice in this area as it is completely new to me.

------

Another thing i was thinking about is file organisation. Does anyone know of a good method to organising your files (or even web bookmarks). I never enjoy organising things but trying to sort through this mess of a computer to get all the stuff i need off of it has taught me that i never want to be in this position again so organisation is necessary. I just find it hard to think of good categories of things and don't like to have to duplicate folders in folders, ending up in some kind of horrid folder spaghetti. The thing is, it is very difficult when certain files or folders relate to more than one area - for example pictures could be related to the set (date) they are from or the type of thing they depict.
I am new to this area too, but in web bookmark terms i heard that multiple tags for things can be used as some kind of solution so that things can almost be in more than one "virtual folder".
I don't really know if there is an equivalent for files though, as everything has to be in an exact location. So, any ideas?
------------

Moving onto the next thing files between windows and ubuntu. Is it true now that ubuntu (or linux itself) can not only read ntfs but can actually write to it? As if this is the case i am thinking it would be best to have an ntfs partition for windows and its programs, an ext4 partition for ubuntu and its programs and an ntfs partition for my documents, music, video etc that can be opened and saved to by both operating systems?

Also another point here is what do i do about sharing a thunderbird install between windows and ubuntu - for example to share the same downloarded email archive / database / account so that it makes no difference whether i log on to windows or linux - i can still check my email with no problems and it won't adversely affect the other. Is it possible to do this (cleanly?).

I'm wondering the same also for firefox or anything too - for example with bookmarks.
------------------

The final thing is to do with drivers.
When trying the live usb version of ubuntu i found that although my keyboard and mouse worked well, the extra buttons on them did not work. For example, the volume, calculator etc buttons on my keyboard did not work, and the forward and back buttons on my mouse wouldn't work.
I have a microsoft internet keyboard and a intellimouse explorer.
In opensuse live usb, it picked these up properly and worked straight away, so i am assuming there are drivers for them somewhere. I guess that either they are not "free" and so are not distributed with ubuntu or are only in the dvd edition?

Also in terms of graphics drivers for my ati x1950 pro, i read that ati support for linux is not so good? But then i don't really understand what drivers come with ubuntu. Certainly the live usb performance was almost impossible to use unless visual effects were then disabled. Are there free versions of drivers for graphics cards and how do they compare to the propriety ones?

I guess the same question for creative xfi soundcards too.
---------------------

What are the differences between linux variations? I tried a lot of different live usbs, including puppy, fedora, ubuntu, mint, moonos and opensuse but in all honestly with some of them, like fedora, ubuntu and opensuse i couldn't really tell what the difference was (using gome versions of all).
Opensuse seemed to have better out of box support for some things but couldn't work with my aiptek tablet whereas ubuntu could.

It just seems like the differences are to do with what programs and drivers come with each linux, and the interface they use? But then what is the difference between each flavour of linux, that is what i didn't get even from trying (unless of course you are looking at the very slimmed down ones like puppy).

Sorry if these questions seem silly and foolish, but i am very new to all this and it is like another scary world.

I thank you if you read this far and i hope any answers might be of help to others too :)

---

### Post by CharlesA on 2010-06-24
It would help to break that wall of text up so it's easier to read. :)

Always install Ubuntu last unless you want to screw with grub.

---

### Post by Zzl1xndd on 2010-06-24
You Should Install Windows then Ubuntu. As Windows will write over Grub(the Bootloader). I would just back up the files and reinstall the OS if needed.

I can't really recommend a Organizing system as everyone likes to lay things out differently. 

Ubuntu Can Read and Write to NTFS. For my Bookmarks I just use the Sync Book marks option in Chrome.

You maybe able to configure the extra keys on your keyboard once Ubuntu is installed through System > Preferences > Keyboard.

I have never used your Graphics card and I mostly stick to Nvidia now, but most ATI cards work fine but you may not be able to use Compiz (desktop effects without extra configuration).

All Linux distros have some things in common, but I guess the short answer to your question is they will package different things as Default. Theres a lot more too it but for most people thats the important part.

---

### Post by amauk on 2010-06-24
> **one2fwee said:**
> Would it be best to install windows first and then ubuntu? Or the ubuntu first and then windows?Windows first, then Ubuntu
You can do a Linux distro before windows, but it's just easier installing Linux last

> **one2fwee said:**
> Also, i plan to make a backup image of the fresh xp root partition (probably with service pack 3) so that if i ever need to "redo" windows again, i can just copy that backup over the top rather than having to reinstall.
So i was wondering a good backup program - whether for windows, ubuntu or a seperate live disc or whatever - i had a bit of a look but it was all a bit confusing. It seems some are just for files whereas others can actually backup the operating system (which is what i guess i'd be needing).

However i never really thought of backing up my files before so it might be useful to get insight into general file backup too. I am all ears for any advice in this area as it is completely new to me.Clonezilla
It's a linux liveCD that clones a complete hard-drive (or partition)
Depending on the size of your existing install, you'll need a fair bit of storage space
but it's the easiest thing in the world to clone a system to an image file, and then restore that image file to an identically working system

> **one2fwee said:**
> Another thing i was thinking about is file organisation. Does anyone know of a good method to organising your files (or even web bookmarks). I never enjoy organising things but trying to sort through this mess of a computer to get all the stuff i need off of it has taught me that i never want to be in this position again so organisation is necessary. I just find it hard to think of good categories of things and don't like to have to duplicate folders in folders, ending up in some kind of horrid folder spaghetti. The thing is, it is very difficult when certain files or folders relate to more than one area - for example pictures could be related to the set (date) they are from or the type of thing they depict.
I am new to this area too, but in web bookmark terms i heard that multiple tags for things can be used as some kind of solution so that things can almost be in more than one "virtual folder".
I don't really know if there is an equivalent for files though, as everything has to be in an exact location. So, any ideas?This is entirely personal preference
organise stuff in a way that best suits your needs

Ubuntu, by default, does come with ready made folders for things (downloads, pictures, videos, music, etc.) with key applications using those folders by default
but that's just the default. how you organise stuff is down to you

> **one2fwee said:**
> Moving onto the next thing files between windows and ubuntu. Is it true now that ubuntu (or linux itself) can not only read ntfs but can actually write to it? As if this is the case i am thinking it would be best to have an ntfs partition for windows and its programs, an ext4 partition for ubuntu and its programs and an ntfs partition for my documents, music, video etc that can be opened and saved to by both operating systems?Yes, full read/write support on NTFS
If you want to share stuff across OSs, then an NTFS partition would be a good solution

> **one2fwee said:**
> Also another point here is what do i do about sharing a thunderbird install between windows and ubuntu - for example to share the same downloarded email archive / database / account so that it makes no difference whether i log on to windows or linux - i can still check my email with no problems and it won't adversely affect the other. Is it possible to do this (cleanly?).

I'm wondering the same also for firefox or anything too - for example with bookmarks.No comment. Never tried it

> **one2fwee said:**
> The final thing is to do with drivers.
When trying the live usb version of ubuntu i found that although my keyboard and mouse worked well, the extra buttons on them did not work. For example, the volume, calculator etc buttons on my keyboard did not work, and the forward and back buttons on my mouse wouldn't work.
I have a microsoft internet keyboard and a intellimouse explorer.
In opensuse live usb, it picked these up properly and worked straight away, so i am assuming there are drivers for them somewhere. I guess that either they are not "free" and so are not distributed with ubuntu or are only in the dvd edition?All drivers are included 'within' linux
(with the exception of some proprietary drivers - nVidia, and some wireless drivers)

Things like mice & keyboards do not (usually) have device specific drivers
Most likely the buttons function, no problem
it's just that Linux does not realise they are there

Install easystroke
this is a nice app for configuring mutli-button mice

> **one2fwee said:**
> Also in terms of graphics drivers for my ati x1950 pro, i read that ati support for linux is not so good? But then i don't really understand what drivers come with ubuntu. Certainly the live usb performance was almost impossible to use unless visual effects were then disabled. Are there free versions of drivers for graphics cards and how do they compare to the propriety ones?

I guess the same question for creative xfi soundcards too.No comment. Never used either brand

> **one2fwee said:**
> What are the differences between linux variations? I tried a lot of different live usbs, including puppy, fedora, ubuntu, mint, moonos and opensuse but in all honestly with some of them, like fedora, ubuntu and opensuse i couldn't really tell what the difference was (using gome versions of all).
Opensuse seemed to have better out of box support for some things but couldn't work with my aiptek tablet whereas ubuntu could.

It just seems like the differences are to do with what programs and drivers come with each linux, and the interface they use? But then what is the difference between each flavour of linux, that is what i didn't get even from trying (unless of course you are looking at the very slimmed down ones like puppy).The differences between distros are far and wide.
Some are visually different
but some differences are largely under-the-skin, and not really user-visible
Just pick a distro you like.

---

### Post by one2fwee on 2010-06-26
Ok thanks for the answers, i guess the main thing is to get going rather than worrying about things :D

Thank you

edit
-----
Oh i just found [this]("http://pcsplace.com/firefox/share-firefox-between-windows-and-linux/") concerning sharing profiles of firefox and thunderbird between oses - so it seems like you can do it :)

---

### Post by fly-by-night on 2010-06-26
> **one2fwee said:**
> 
Also another point here is what do i do about sharing a thunderbird install between windows and ubuntu - for example to share the same downloarded email archive / database / account so that it makes no difference whether i log on to windows or linux - i can still check my email with no problems and it won't adversely affect the other. Is it possible to do this (cleanly?).

I'm wondering the same also for firefox or anything too - for example with bookmarks.
------------------


I used to share my Firefox profile between Ubuntu and Windows.  Now I use an addon called Xmark.   Also simply copying the profiles manually from one system to the next work too.

To share **one** profile:  Set up the profile on Windows, then with **firefox -profilemanager** add that profile to Firefox in Ubuntu. 

Always make sure that your Windows partition is mounted before starting Firefox.  I'm almost sure that the same will work in Thunderbird.

EDit: Nevermind.LOL

---

