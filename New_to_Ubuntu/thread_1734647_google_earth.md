---
title: "google earth"
date: 2011-04-20
forum: New to Ubuntu
---

### Post by DaveMcC on 2011-04-20
Why can I not get google earth to install on this computer, all I get is in screen shot

[IMG]http://i7.photobucket.com/albums/y282/dtmcc/earth00.jpg[/IMG]

This is on going, and as I have just downloaded, updated the up dates including some thing for google earth

How can I see where I am not going on holiday to this year, OH woo is me

Dave

---

### Post by Fraoch on 2011-04-20
Weird, I don't see this in Ubuntu Software Centre when I type Google Earth into the search box.  Instead I see, once I click on "Show 1 technical item" at the bottom:

"0.5.7 (googleearth-package)"

"This utility makes it possible to build your own personal Debian package of Google Earth. The packaging itself is Free Software, but the Google Earth program is governed by the copyright holder (Google), so you may be limited as to what you can do with the resulting package (i.e. no redistribution, etc). This package will simply help you create the package--it is your responsibility to use the resulting package responsibly."

This implies you can't get the Google Earth package directly.  You have to run googleearth-package first.

Did you get Software Centre to show the dialog you posted *after* running googleearth-package?  Where did you get the .deb file from?

If I build the file using the googleearth-package, then install using the .deb it builds, it installs and runs perfectly.  It's accessible in the Applications - Internet menu.

Try googleearth-package first.  To run it, type "make-googleearth-package --force" in a terminal.  I had to use "--force" because the first time it complained about an unrecognized version from Google.  No biggie, I believe they update Google Earth all the time so it's probably just a version beyond what the googleearth-package developers were expecting.

Let googleearth-package do its thing, it took a few minutes for me and although there were a series of warnings it did make a Google Earth .deb package in my home directory.  The one it made for me just now is "googleearth_6.0.2.2074+0.5.7-1_amd64.deb"  For you the last part of the file will probably read i386.  Then just double-click that.

---

### Post by Elfy on 2011-04-20
Would appear to be installed to me.

Are you sure it just isn't running?

Try running it from a terminal ```
googleearth
``` I think, if you get 

/usr/lib/googleearth/googleearth-bin: not found

Try installing lsb-core 

```
sudo apt-get install lsb-core
```

---

### Post by beew on 2011-04-20
Forget about the software center.

 Install lsb-core  and gdebi from Synaptic. Then download the latest stable .deb from googleearth
[http://www.google.com/earth/download/ge/agree.html](http://www.google.com/earth/download/ge/agree.html)

The latest is ge6

Right click to install and that's it. 

(gdebi is basically for the right click-install function for .deb packages, otherwise the software center would install it with right click, but I hate the SC. Of course you can also use the dpkg -i command to install .debs)

---

### Post by DaveMcC on 2011-04-20
> **beew said:**
> Forget about the software center.

 Install lsb-core  and gdebi from Synaptic. Then download the latest stable .deb from googleearth
[http://www.google.com/earth/download/ge/agree.html](http://www.google.com/earth/download/ge/agree.html)

The latest is ge6

Right click to install and that's it. 

(gdebi is basically for the right click-install function for .deb packages, otherwise the software center would install it with right click, but I hate the SC. Of course you can also use the dpkg -i command to install .debs)

And you see the screen shot of what I get

Dave

> **Fraoch said:**
> 

  "googleearth_6.0.2.2074+0.5.7-1_amd64.deb"  For you the last part of the file will probably read i386.  Then just double-click that.

The rest I don't under stand,,, but! for this bit googleearth_6.0.2.2074+0.5.7-1_amd64.deb,,, amd64 thats the version of ubuntu I am running so why should I change googleearth_6.0.2.2074+0.5.7-1_amd64.deb to i386

Dave

After running 
sudo apt-get install lsb-core
I get this 

[IMG]http://i7.photobucket.com/albums/y282/dtmcc/earth01.jpg[/IMG]

if its running it well hidden

Dave

---

### Post by Fraoch on 2011-04-20
> **DaveMcC said:**
> The rest I don't under stand,,, but! for this bit googleearth_6.0.2.2074+0.5.7-1_amd64.deb,,, amd64 thats the version of ubuntu I am running so why should I change googleearth_6.0.2.2074+0.5.7-1_amd64.deb to i386

Dave

I just assumed you weren't running 64-bit as it's not that common.  You don't have to change it, googleearth-package makes the package for you based on the architecture it finds.  So yes, in your case, it would read "googleearth_6.0.2.2074+0.5.7-1_amd64.deb".  I was just saying what you *might* find instead.

But try googleearth-package, it's pretty simple and it made a package for me that worked fine.  I used Google Earth in Ubuntu several versions ago - it worked well for a bit but I had problems with it for a few versions of Ubuntu.  However this version works just fine in 10.10 for me.

---

### Post by alphacrucis2 on 2011-04-20
> **DaveMcC said:**
> Why can I not get google earth to install on this computer, all I get is in screen shot



This is on going, and as I have just downloaded, updated the up dates including some thing for google earth

How can I see where I am not going on holiday to this year, OH woo is me

Dave

Your screen shot says that the package is installed so what's the problem. Have you actually tried to run it?

---

### Post by DaveMcC on 2011-04-21
Fraoch
It runs well on this computer which is running ver 9 of ubuntu

alphacrucis2
In my second it says its running, I just can't find it, On MY computer which is running ubuntu ver 10.10 amd 64bit
And it is my computer that I need it to run on, "or would like it to be working on"

I have tried to install ver 5 but it keeps reverting back to ver 6 of google earth, even after I have deleted what I can find of it

Dave

---

### Post by alphacrucis2 on 2011-04-21
> **DaveMcC said:**
> Fraoch
It runs well on this computer which is running ver 9 of ubuntu

alphacrucis2
In my second it says its running, I just can't find it, On MY computer which is running ubuntu ver 10.10 amd 64bit
And it is my computer that I need it to run on, "or would like it to be working on"

I have tried to install ver 5 but it keeps reverting back to ver 6 of google earth, even after I have deleted what I can find of it

Dave


Try opening a terminal and typing as below and hit enter

```
googleearth
```

Does it display any error messages?

---

### Post by DaveMcC on 2011-04-21
This is what happen

boss@boss-desktop:~$ googleearth
googleearth: command not found
boss@boss-desktop:~$ 

Its conflicting itself

Dave

---

### Post by Fraoch on 2011-04-21
> **DaveMcC said:**
> This is what happen

boss@boss-desktop:~$ googleearth
googleearth: command not found
boss@boss-desktop:~$ 

Its conflicting itself

Dave

Go into Synaptic and search for "googleearth", is it there and is the box green (indicating that it's installed)?

That command should have done something if it is installed.  If you see it in Synaptic, right-click on it, select "Properties" and the "Installed Files" tab.  It should be listed in /usr/bin/googleearth , which is where that command would call.

If it's not there, it's not installed but there may be traces of it left.  Try looking for it in Synaptic by clicking on the "Status" button on the lower right and looking for it in the "Not installed (residual config)" section.  If it's there, highlight it, right-click and select "Mark for complete removal", then click the "Apply" button up top.  Now you can reinstall it.  Again, try the googleearth-package program rather than a download on Google's site.  googleearth-package worked perfectly for me with 10.10 64-bit.

---

### Post by DaveMcC on 2011-04-21
Fraoch
Went into Synaptic and search for "googleearth",
Found this  "maverick" 0.5.7
(Package) googleearth package (installed version) 0.5.7  (Latest Package) 0.5.7 (Desripton) utility to automatically build a Debian package of google earth

So then I done see it in Synaptic, right-click on it, select "Properties" and the "Installed Files" tab.
as seen below

```
/.
/usr
/usr/bin
/usr/bin/make-googleearth-package
/usr/share
/usr/share/doc
/usr/share/doc/googleearth-package
/usr/share/doc/googleearth-package/README.Debian
/usr/share/doc/googleearth-package/changelog.gz
/usr/share/doc/googleearth-package/copyright
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/make-googleearth-package.1.gz
```


I then done the rest of what you have said "I think" but am back to start again, see first post
On the remove of file it was 69kb in size not the 22.5mb download

Dave

No, still back at first post,,??

Fraoch, how do you, or explain more, cuz I,m only an old fool trying to get to grips with ubuntu

Quote
 "Again, try the googleearth-package program rather than a download on  Google's site.  googleearth-package worked perfectly for me with 10.10  64-bit."
Unquote

Dave

---

### Post by Fraoch on 2011-04-22
> **DaveMcC said:**
> No, still back at first post,,??

Fraoch, how do you, or explain more, cuz I,m only an old fool trying to get to grips with ubuntu

Nah, we've all been there!  It was really difficult for me at first and it's still pretty challenging.  I'm still a rank amateur.  However I'm learning more and more.

> 
Quote
 "Again, try the googleearth-package program rather than a download on  Google's site.  googleearth-package worked perfectly for me with 10.10  64-bit."
Unquote

Dave

Did you run the googleearth-package by typing its name into the terminal?

Did it create a .deb for you?  It will be in the same directory you invoked googleearth-package from - if you did this just after opening a terminal then it will be your home directory.  (/home/[your user name])  What's the name of this package?  If it's much different than what it created for me just a day ago, there's likely something wrong.

Now if Synaptic only found googleearth-package, then you do not have any remnant of Google Earth left from an earlier install.  Double-check in Synaptic - Status - Not installed (residual config) to be sure.  Once you are sure you have no trace of Google Earth left, you can install from the .deb googleearth-package just made for you.

I prefer installing using GDebi.  It will examine the .deb, determine if there's anything wrong with it and if you have all the required dependencies.  To install GDebi, in terminal type:

```
sudo apt-get install gdebi
```

Of course you can do this through Synaptic or Software Center if you like.

Once you've installed GDebi, locate the file and double-click on it.  It should check the file, check for dependencies and you should be able to install it.

Then Google Earth is available through Applications - Internet.

---

### Post by PhillyPhil on 2011-04-22
> **Fraoch said:**
> I just assumed you weren't running 64-bit as it's not that common.

I think you'll find it is pretty common...if it's not the majority yet it's not far off. 

OP, try running google earth with sudo or gksudo.

---

### Post by alphacrucis2 on 2011-04-22
> **DaveMcC said:**
> This is what happen

boss@boss-desktop:~$ googleearth
googleearth: command not found
boss@boss-desktop:~$ 

Its conflicting itself

Dave

Try this, which is what the launcher has on my setup.

```
google-earth
```

---

### Post by DaveMcC on 2011-04-22
Fraoch
I have found google earth in my downloads place with a .deb 
Did you run the googleearth-package by typing its name into the terminal? command not found
Did it create a .deb for you?  It will be in the same dir  at this point I am getting lost and losing the will to go on
I prefer installing using GDebi.  It will examine the .deb,  don't know what that is or means
Of course you can do this through Synaptic or Software Center if you like.
,,, software centre does not work see screen shot 1

PhillyPhil
OP, try running google earth with sudo or gksudo. 	,,, sorry don't know what they are

alphacrucis2
google-earth
it works, but do I have to do that every time I want to run google earth?

Dave

I am too old for all this cr---ap

---

### Post by beew on 2011-04-22
> **DaveMcC said:**
> Fraoch
I have found google earth in my downloads place with a .deb 
Did you run the googleearth-package by typing its name into the terminal? command not found
Did it create a .deb for you?  It will be in the same dir  at this point I am getting lost and losing the will to go on
I prefer installing using GDebi.  It will examine the .deb,  don't know what that is or means
Of course you can do this through Synaptic or Software Center if you like.
,,, software centre does not work see screen shot 1

The googleearth-package is used to create the .deb (which is the ge installer basically). Since you already have it there is no need for running googleearth package. That's why I told you in my first post to forget about google-package if it gives you problems and just downmload the .deb from the google earth web site.

But from below it looks like you already have it installed so no need to run the .deb either.

> PhillyPhil
OP, try running google earth with sudo or gksudo.     ,,, sorry don't know what they are
That means running ge as root, normally you shouldn't have to unless you fouled something up during install.


> alphacrucis2
google-earth
it works, but do I have to do that every time I want to run google earth?

DaveYou can create a launcher either on the desktop or in  the menu.

For a desktop launcher right click anywhere and choose create launcher (something like that) and when the dialogue box opens type "google-earth" in the box that says 'command' and you can make it look nice by clicking the box in the upper left hand corner and choose the googleearth icon (the blue earth), it is probably in /usr/share/icons. It should be a png file. if you are not sure open  up Synaptic and  choose googleearth and right click choose properties and then installed files and you should be able to locate the icon and then you can choose it in the create launcher dialog box. (You can basically type anything in the box that asks for the package name, but of course you want to name it google earth, so type "google earth" in that one, it is the command that would actually launch the application so you have to make sure that one is entered correctly)

For a menu icon you go to system > preference > main menu on the top bar and then choose "internet" on the left panel. Choose create new launcher (or something like that) on the right panel, a dialog box will open and you go through the same steps as above and you will have a launcher created in  internet > googleearth

I have installed googleearth in 3 ways(ppa, download .deb from ge and google-package) and never did I have to create my own launcher, I am not sure what happened  :)

---

### Post by DaveMcC on 2011-04-22
Beew have a beer on me
finnally got it the way I want it

Dave

---

