---
title: "Hi - I'm new and run a website."
date: 2009-03-06
forum: New to Ubuntu
---

### Post by Dazey on 2009-03-06
I need a few things that dont run in linux 8.10 and do got WINE.  I'm trying to run a prayer program under WINE but can't get it installed.

I also need the IETab for Firefox.  

Another thing, how come we can't upgrade the thunderbird we have?

Thanks, Linda

---

### Post by handy on 2009-03-06
You will find that posting Wine related question in the [*_Wine sub-forum_*]("http://ubuntuforums.org/forumdisplay.php?f=313") will usually get you quicker if not more in depth responses.

Your other questions may do best here, so I won't ask a mod to move your thread.

All the best.

---

### Post by anim on 2009-03-06
Hi Linda,
Some programs may not work with wine. Either tell us the name of the program so we can try to help, or [click here]("http://appdb.winehq.org/") to see if someone else has had any luck at getting it to work.

There are also quite a few free religious software packages that are availible for installation via the Applications->Add/Remove Programs menu. Use the search box to help you find what you're looking for.

And can you please elaborate on your Thunderbird question? Updates are automatic in Ubuntu, but sometimes newer versions of programs are not included until the next release of Ubuntu. At the very least, please let us know the version # of thunderbird that is installed right now, and the version # of the thunderbird you'd like to upgrade too.

Welcome to Ubuntu!

---

### Post by Lod on 2009-03-06
> **Dazey said:**
> 
Another thing, how come we can't upgrade the thunderbird we have?

I don't know, how come? The version in the repository is 2.0.0.19 which is the latest version of the program. What version do you have and how did you install it? Because if you did it the official ubuntu way then it should be upgraded automatically.

---

### Post by the8thstar on 2009-03-06
IE Tab for Firefox is not available in Linux. Perhaps you can try installing the Windows version of Firefox with Wine and add the IE Tab add on from there.

---

### Post by Temposs on 2009-03-06
hi Dazey,
   Welcome to the forums, since it's your first post :-)

A program that is designed to run under Windows isn't guaranteed to run under WINE. Sometimes a program will have been tested by someone and they may give instructions on how to set up a program under WINE. You can find such things here:

[http://appdb.winehq.org](http://appdb.winehq.org)

Just search for your program in the search bar in the top right. Your program may not be found since probably not many people use it, but you can try. Otherwise, you may be out of luck for this particular program. EDIT: If it doesn't work, try looking for a prayer program made for Linux. I bet there are a few :-)

Regarding IEtab: Internet Explorer is also a Windows program and will run under WINE, but you cannot IEtab with the Firefox that comes with Ubuntu. You would have to download the Firefox for Windows and install it with WINE, and then install Internet Explorer under WINE and then, install IEtab under WINE.

Regarding Thunderbird: You should usually use the version of Thunderbird that is included in the Ubuntu Add/Remove program. The version in there is the most stable and well-tested version for Ubuntu, and a newer version of Thunderbird isn't guaranteed to work well under Ubuntu. If you really really want a new version of Thunderbird, you should download the version for Linux, which looks to be a source package. If you've never done that before, you'll need to follow a tutorial like the ones here: [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
[http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html)

Hope this helps.

---

### Post by cptr13 on 2009-03-06
I don't know what your prayer program does, but there is a Ubuntu Christian edition and a Ubuntu Muslim edition, there are a lot of programs included.  There may be a linux version that suits your needs too.

---

### Post by card_ace on 2009-03-06
if its a windows program your trying to run, and wine isn't working for you, you can always install virtualbox and put a windows os inside of it to run all your old windows programs.  I'm not entirely sure why, but some windows programs don't work in Wine.  I'm assuming its something to do with how their programming is written.  maybe someone more experience can can give you a good reason for this.  Good luck!

---

### Post by cwsnyder on 2009-03-06
Another thing you may want to consider is using [IEs4linux]("http://www.tatanka.com.br/ies4linux/page/Installation") to get test versions of Internet Explorer to go to IE only websites.

---

### Post by Temposs on 2009-03-06
In order to run Windows programs, those who have made WINE have attempted to code in Linux form each little instruction that Windows programs send when they are run. Thousands of these little instructions run on each program. Since Windows is not open source, WINE programmers have to guess how each Windows instruction works, and try their best to code it themselves based on what they can tell from the behavior of Windows programs(reverse engineering). That means it's very unlikely and takes a lot of testing and mucking about to get each little instruction exactly correct for every single test case. Also, Microsoft is always adding more types of instructions and change how existing ones work. So, it's very unlikely for a program to work under WINE perfectly unless it's very simple or has been tested extensively by WINE contributors.

---

### Post by Paqman on 2009-03-06
> **Dazey said:**
> 
I also need the IETab for Firefox.


You can't use IETab, as Linux doesn't (normally) include IE. There is a package called IES4Lin that's designed for web designers/devs doing browser checks, but I can't vouch for how well it works.

> 
Another thing, how come we can't upgrade the thunderbird we have?


You'll always be brought up to what ever the latest version is in the repositories. This happens automatically, along with all the other upgrades on your system.

Sometimes the version in the normal repos will get quite old (especially on an LTS version of Ubuntu). You can try enabling the Backports repo to see if this has a more recent version, or else try the package's website

One trick that's handy for people who maintain wbesites: did you know that your file manager is also an FTP client? Go to places > Connect to server. You can even bookmark your server!

---

### Post by card_ace on 2009-03-06
> **Temposs said:**
> In order to run Windows programs, those who have made WINE have attempted to code in Linux form each little instruction that Windows programs send when they are run. Thousands of these little instructions run on each program. Since Windows is not open source, WINE programmers have to guess how each Windows instruction works, and try their best to code it themselves based on what they can tell from the behavior of Windows programs(reverse engineering). That means it's very unlikely and takes a lot of testing and mucking about to get each little instruction exactly correct for every single test case. Also, Microsoft is always adding more types of instructions and change how existing ones work. So, it's very unlikely for a program to work under WINE perfectly unless it's very simple or has been tested extensively by WINE contributors.

thanks for the explanation, now i understand it better too

---

