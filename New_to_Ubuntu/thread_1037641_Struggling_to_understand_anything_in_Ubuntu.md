---
title: "Struggling to understand anything in Ubuntu"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by djk21108 on 2009-01-12
So I just installed about an hour ago.  I'm trying to use an OS without having to use terminal all the time.  Is this possible?  I'm having trouble installing things in .bin format, in tar format.  I just don't understand anything about Ubuntu.

Another concern I have.  I don't really know where the programs are when I install them.

In windows its c: program files. 

Ubuntu has a ton of folders in the file system I just don't know what any of them are.

If anyone has a really highly recommended  guide for explaining all this stuff for me, I'd be so ecstatic.


One more thing I thought of when I was writing this post.  In windows firefox when you make a spelling error, you right click on the word and possibilities come up for better spellings, this seems to be absent in the linux version.

---

### Post by lykwydchykyn on 2009-01-12
> **djk21108 said:**
> So I just installed about an hour ago.  I'm trying to use an OS without having to use terminal all the time.  Is this possible?  I'm having trouble installing things in .bin format, in tar format.  I just don't understand anything about Ubuntu.

What are you trying to install?  Unfortunately some people don't make nice install packages for Linux, so things have to be done that way.  But most stuff you need should be in the repositories, so it should be installable through add/remove programs or synaptic.  Check there *first*, rather than going to a website to download anything.

> 
Another concern I have.  I don't really know where the programs are when I install them.

In windows its c: program files. 

Ubuntu has a ton of folders in the file system I just don't know what any of them are.


Things are organized differently.  The good news is, you really don't need to know where anything is (usually).  If you want to run a program, just type the name in a terminal, or launch it from the menu.  

That said, the executables for most programs are in /usr/bin/

> 
If anyone has a really highly recommended  guide for explaining all this stuff for me, I'd be so ecstatic.

This is a good place to start: [https://help.ubuntu.com/community](https://help.ubuntu.com/community)

> 
One more thing I thought of when I was writing this post.  In windows firefox when you make a spelling error, you right click on the word and possibilities come up for better spellings, this seems to be absent in the linux version.

It works here, maybe check your preferences?  Not sure why that's not working for you.

---

### Post by jrusso2 on 2009-01-12
The most common places for programs to install to are /usr/bin, usr/share/program name,/usr/lib and /opt

---

### Post by aesis05401 on 2009-01-12
After you have checked out the above poster's link check out this one: [Basic Terminal Tutorial]("https://help.ubuntu.com/community/UsingTheTerminal").

Many people have an aversion to the terminal.  After a few weeks, though, most people that I know have changed their tune.  If you are coming from an MS environment you will be amazed at how many issues can be instantly fixed with a terminal command or two.

---

### Post by iaculallad on 2009-01-12
Here's a link on [Linux Directory Structures]("http://www.debianadmin.com/linux-directory-structure-overview.html").

For your other queries, try googling for the information since those topic are too broad to be explained on a single posting.

---

### Post by djk21108 on 2009-01-12
I still don't understand installing stuff.  I got a .bin to install java.  I double click it and Linux says no.  Any advice there?

---

### Post by Fass on 2009-01-12
> **djk21108 said:**
> One more thing I thought of when I was writing this post.  In windows firefox when you make a spelling error, you right click on the word and possibilities come up for better spellings, this seems to be absent in the linux version.

Have you installed [the proper dictionaries](https://addons.mozilla.org/en-US/firefox/browse/type:3) and chosen to have Firefox check spelling by right-clicking in a text entry field?

---

### Post by jrusso2 on 2009-01-12
> **djk21108 said:**
> I still don't understand installing stuff.  I got a .bin to install java.  I double click it and Linux says no.  Any advice there?

Why are you downloading a .bin file to install Java when its in the repository and all you need is to use add/remove or synaptic to install or apt.

---

### Post by newbee70 on 2009-01-12
> **djk21108 said:**
> I still don't understand installing stuff.  I got a .bin to install java.  I double click it and Linux says no.  Any advice there?

Hi, Welcome to the forums.

Have you added the ubuntu-restricted modules?

go to applications / add-remove software.

click on the all at the top and in the search bar type ubuntu
the first response should be ubuntu-restricted add it.

browse the apps for what you want to add or remove.

---

### Post by djk21108 on 2009-01-12
I'm getting a basic grasp of Add/Remove programs.  I know how to search, but when i tried to get VLC player and Java I get this.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by iaculallad on 2009-01-12
> **djk21108 said:**
> I still don't understand installing stuff.  I got a .bin to install java.  I double click it and Linux says no.  Any advice there?

Installing a BIN file using the terminal would be:

You can make it executable by:

```
sudo chmod a+x ./<bin_package_name>
```

then

```
sudo ./<bin_package_name>
```

---

### Post by Fass on 2009-01-12
> **djk21108 said:**
> I still don't understand installing stuff.  I got a .bin to install java.  I double click it and Linux says no.  Any advice there?

Bin-files don't work that way. First you'd need to set its permissions to be executable and then execute it from the terminal, but that's all unnecessary as you can install Sun Java from the repositories.

[First enable all the repos (main, universe, restricted, multiverse) as outlined here](https://help.ubuntu.com/community/Repositories/Ubuntu). Then install the following packages through Synaptic: sun-java6-jre sun-java6-jdk sun-java6-plugin

---

### Post by iaculallad on 2009-01-12
> **djk21108 said:**
> I'm getting a basic grasp of Add/Remove programs.  I know how to search, but when i tried to get VLC player and Java I get this.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

On your terminal, As the error message says, try the command below:

```
sudo dpkg --configure -a
```

---

### Post by djk21108 on 2009-01-12
Thank you I really appreciate all of your help.  I have a few more questions though.

On windows you can connect to your default wireless network automatically.  How do you do this in Linux?

Is there a way where I don't have to type in my username to get in, just type my password.

Print screen works for me on the desktop, when i print screen in firefox, I'm not sure how that whole process works, is there a "paint" program I can paste it into?

Also, in windows when you control alt delete you can see everything thats running including processes.  Does Ubuntu have this application.

When I installed something it says I have a broken package...WTF?

---

### Post by Ender41 on 2009-01-12
> **djk21108 said:**
> I still don't understand installing stuff.  I got a .bin to install java.  I double click it and Linux says no.  Any advice there?

If you downloaded from sun there is instructions there about how to install it however as others have already told you. First check out what is available in the repositories before resorting to getting tars and bins etc.
Installing ubuntu-restricted-extras for instance will install java and a lot of other codecs you may need. In other words don't jump into the deep end of the pool take it slowly and your new experience with linux will be more fun and less stressful.

---

### Post by blackened on 2009-01-12
> **djk21108 said:**
> When I installed something it says I have a broken package...WTF?

Sometimes, if a program is interrupted during installation it will leave you with a broken package. To fix it, do as the terminal suggested earlier:
```
sudo dpkg --configure -a
```

After that you should be able to install things normally again.

> Also, in windows when you control alt delete you can see everything thats running including processes.  Does Ubuntu have this application.

In the main menu:
System -> Administration -> System Monitor

> Is there a way where I don't have to type in my username to get in, just type my password.

Use a login theme that includes a user picker, or just hibernate or sleep your machine and it should only ask you for your password. 

> On windows you can connect to your default wireless network automatically.  How do you do this in Linux?

Right click on the network manager icon in the system tray and select "Edit Connections". Select the Wireless tab in the subsequent dialog. Find your SSID in the list and press the "Edit" button on the right. Another dialog will open, check the "Connect automatically" checkbox at the top then close the dialogs.


In parting the following link is a good place to familiarize yourself with what you've gotten into: [http://linux.oneandoneis2.org/LNW.htm]("http://linux.oneandoneis2.org/LNW.htm")

---

### Post by cybergrunt on 2009-01-12
In regards to your task manager question. Open a shell and have a look at 'ps' and 'top'. ps-aux should give you most of the info you'll ever need. Use the MAN pages for more info.

---

### Post by djk21108 on 2009-01-12
Great thanks a bunch blackened.

One more problem I've noticed is I copy and paste in firefox, close it, and try to copy and paste in something else.  The selected stuff is gone.  Any way to remedy this?

---

### Post by pastalavista on 2009-01-12
After you have installed the restricted-modules, open a terminal (Applications->Accessories->Terminal) and type```
sudo dpkg --configure -a
```enter your password (nothing will show but it is being read) and then try installing VLS again.

(I should have read all the comments... never mind)

---

### Post by ajcham on 2009-01-12
> **djk21108 said:**
> Print screen works for me on the desktop, when i print screen in firefox, I'm not sure how that whole process works, is there a "paint" program I can paste it into?

Print Screen should open a screenshot dialog - you can use this to save the screenshot as a .png file which you can open in any image editor, or you can copy to the clipboard for pasting.

If it doesn't open the dialog you can get by using Applications » Accessories » Take Screenshot. You can set up the PrtScr shortcut using System » Preferences » Keyboard Shortcut, and looking for Take Screenshot in the Desktop Actions.

Try gpaint from Add/Remove Programs if you want a basic paint program.

---

### Post by MickAld on 2009-01-12
If anyone has a really highly recommended  guide for explaining all this stuff for me, I'd be so ecstatic.


If you are interested in purchasing a book I have used one called Ubuntu for non Geeks by Rickford Grant. I find reading and locating internet instructions can be a bit hit and miss and sometimes what you find is a bit geeky. 

This book explains in easy stages the workings of Ubuntu without frightening the pants off you. Well worth the money I think.

---

### Post by djk21108 on 2009-01-12
Allright, thanks for the recommendation.  Firefox still seems to underline words I got wrong, but doesn't tell me how to fix it.  I'm perplexed.  

And I guess as you close firefox, you lose anything stored in its clipboard?

---

### Post by iaculallad on 2009-01-12
> **djk21108 said:**
> And I guess as you close firefox, you lose anything stored in its clipboard?

Yes, and that applies to any application you use with Ubuntu.

---

### Post by djk21108 on 2009-01-12
> **iaculallad said:**
> Yes, and that applies to any application you use with Ubuntu.

well aint that a kick in the groin.

---

### Post by ajcham on 2009-01-12
> **iaculallad said:**
> Yes, and that applies to any application you use with Ubuntu.
Are you sure?  I'm able to copy and paste between different apps just fine, even if I've closed the app that I copied from - including Firefox.  I don't recall installing anything in particular that would have added this capability, so I assume it is the default, but I may be mistaken.

---

### Post by djk21108 on 2009-01-12
well if you find whatever gave you these strange and wonderful powers...tell me.

---

### Post by iaculallad on 2009-01-12
> **ajcham said:**
> Are you sure?  I'm able to copy and paste between different apps just fine, even if I've closed the app that I copied from - including Firefox.  I don't recall installing anything in particular that would have added this capability, so I assume it is the default, but I may be mistaken.

Not unless you had [glipper]("http://glipper.sourceforge.net/") installed that data's copied on clipboard will remain even if the source application(s) is/are closed.

---

### Post by ajcham on 2009-01-12
> **iaculallad said:**
> Not unless you had [glipper]("http://glipper.sourceforge.net/") installed that data's copied on clipboard will remain even if the source application(s) is/are closed.

Nope, glipper is not installed - I do have klipper installed (KDE clipboard tool) but I'm in Gnome and klipper is not active.

---

### Post by mick222 on 2009-01-12
just copy and paste.
```
  dpkg --configure -a 
```
into terminal should sort that out.
Go to systam->admin->synaptic package manager 
Click on settings repositories make sure everything except for source is ticked.Then search for Ubuntu restricted extras and apply.
hope this helped ,you seldom really need to use terminal it's just easier for people to give commands rather than detailed instructions.
Check out the sticky in multi media it installs a lot of stuff that you probably want. i.e. codecs for dvd playback mozilla plugins and vlc.

---

### Post by Sprut1 on 2009-01-12
If you need quick help about something in the terminal you can use the "man" command, I guess it comes from "manual". Need help with tar? "man tar", need to know how folders are organized? "man hier". Remember that command in the future and you can save yourself a lot of pain, at least I did.

---

### Post by Geemonster on 2009-01-12
I must be honest,im struggling myself with ubuntu,i have had a problem with Skype audio,and as for the command line,well i guess i've been using Windows for too long.
   All i want to do is chat thru my mic rather than typing all the time.
I thought over the last year and a half i'd learnt quite a lot.
It seems to me ubuntu's made for geeks.
   Any suggestions please peeps?

---

### Post by ajcham on 2009-01-12
> **djk21108 said:**
> well if you find whatever gave you these strange and wonderful powers...tell me.

Now that I think about it, I remember that I didn't install from a vanilla Ubuntu CD - I used a 'Special Edition' that came with LXF magazine.  I can't find what must have been included to allow this capability.

I have however discovered this: [GNOME Clipboard Daemon]("http://members.chello.nl/~h.lai/gnome-clipboard-daemon/"), while searching online.  It doesn't appear to be installed on my system, but the author does make reference to a (rejected) patch for gnome-settings-daemon - maybe the guys that put together the Special Edition I installed integrated this patch?

---

### Post by djk21108 on 2009-01-12
Another weird quirk just popped up.  I was messing with my screen resolution and suddenly everything changes.  Icons are different and firefox looks strange.  And to top it all off I can't change my resolution anymore.

---

### Post by babloo75 on 2009-01-12
So u r where i was few weeks back.. its good to see one more member of ubuntu community.. and u must appreciate so many people have come here and stopped to help you.. one day u will become an expert too... there are so many of ur new frenz here... isn't it... thats the best thing i love about ubuntu.. i have tried most of the versions of linux viz. fedora, suse, mandriva, kubuntu... but above all of 'em is UBUNTU... its a love, a beautiful love... (no i m not joking)
ya.. and u will learn ubuntu only after u make mistakes.. check regularly on forums what other people face problems and how to solve 'em.. thats the way u will learn (and thats how i m here.. i read ur thread and now m writing this)
may be u r not reading it but still i will give my advice... see these threads regularly so that u don't commit mistakes which other new users have already made..
sincerely speaking i always do experiments with my ubuntu.. and have faced very surprising mistakes which usually other people don't encounter..
and i will continue to do so till i get support from this community..
there are few websites too which will help u.. most of them are mentioned above and here are few:

[http://ubuntuguide.org/wiki/Ubuntu:Intrepid](http://ubuntuguide.org/wiki/Ubuntu:Intrepid)
[http://www.ubuntugeek.com/top-posts](http://www.ubuntugeek.com/top-posts)
[http://ubuntu-tutorials.com/](http://ubuntu-tutorials.com/)

happy experimenting..........!

---

