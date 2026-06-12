---
title: "have wine, whats next"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by johnycage on 2009-05-18
I've donwloaded wine 1.0.1 tar.bz2 file. what to do next? where to extract & how its interface is like?

I wanted wine for some Windows based applications. I have an old CD of FrontPage 2003. will it work on Ubuntu using wine?

---

### Post by Redache on 2009-05-18
Why not just install it from the Ubuntu repository?

```
sudo apt-get install wine
```It's a lot easier than trying to compile it from source.

if you look at [http://www.winehq.org]("http://www.winehq.org/") it lists applications and reports on if an application works or not.

But if you want to know how to do a source install: (I Heavily recommend avoiding it if at all possible)

you'll need to:

```

./configure
make
make install
```AFTER making sure that all dependencies are met (it won't finish configure if they aren't). Usually the Readme File for the Application lists all dependencies.

---

### Post by SunnyRabbiera on 2009-05-18
Right, no need to compile unless its needed, and compiling in Ubuntu is at a alltime low.

---

### Post by Game Over on 2009-05-18
> **SunnyRabbiera said:**
> Right, no need to compile unless its needed, and compiling in Ubuntu is at a alltime low.

Any links on this, Sunny?? I have yet to compile yet, but will be soon.

---

### Post by SunnyRabbiera on 2009-05-18
> **Game Over said:**
> Any links on this, Sunny?? I have yet to compile yet, but will be soon.

No real stats, but the size of the Ubuntu repository shows good signs of not needing to compile all the time.
Maybe its down to 3 out of 10 times

---

### Post by cariboo on 2009-05-18
I haven't needed to compile a package since I started using Ubuntu v 6.06. All of the software I use everyday is available from the repositories.

---

### Post by mikurej95 on 2009-05-18
Or, you can use .deb

---

### Post by Mark Phelps on 2009-05-18
If you click the link below to the CodeWeavers site, you'll see their compatibility page for FrontPage, and will note that they have not tested it.  So, it may or may not work.

[=ASC;curPos=200"]http://www.codeweavers.com/compatibility/browse/name/?letter=f;showall=1;sort[app_name]=ASC;curPos=200]("http://www.codeweavers.com/compatibility/browse/name/?letter=f;showall=1;sort[app_name)

---

### Post by Cresho on 2009-05-18
The one that comes with ubuntu from repos usually run better than the built ones.  I suggest you use the #sudo apt-get install wine command.

---

### Post by NightwishFan on 2009-05-18
You can download the latest version of Wine if you desire. I have tested it and found no major drawbacks. Here is a tutorial:

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by WitchCraft on 2009-05-18
> **johnycage said:**
> I've donwloaded wine 1.0.1 tar.bz2 file. what to do next? where to extract & how its interface is like?

I wanted wine for some Windows based applications. I have an old CD of FrontPage 2003. will it work on Ubuntu using wine?

FrontPage 2003 works very well

apt-get install wine

wine ./setup.exe

---

### Post by UBTRook on 2009-05-18
I ran the sudo apt-get install wine command and have wine installed.  Any advice on how to install itunes through wine.  I attempted following another posts but I think I messed something up renaming the richedit20.dll to richedit20.bak

---

### Post by NightwishFan on 2009-05-18
Before I installed itunes without modifications just fine, though I do not know if it was a modern one. It did not have the 'cover flow' stuff.

Try the wine app database for information.

---

### Post by Paddy Landau on 2009-05-18
May I suggest that before installing anything under wine, you first install [PlayOnLinux]("http://www.playonlinux.com/"). Instructions for Ubuntu are on the download page.

Install your Windows programs through PlayOnLinux, because it makes it easier, and also keeps your Windows programs separate from each other.

---

### Post by NightwishFan on 2009-05-18
Is play on linux really needed?

---

### Post by Paddy Landau on 2009-05-18
> **NightwishFan said:**
> Is play on linux really needed?
No, it's not needed. But I've found it makes it so much easier. And if you want to "uninstall" a Windows program, it's quick and painless.

---

### Post by WitchCraft on 2009-05-23
> **NightwishFan said:**
> Is play on linux really needed?

Certainly not, but you can if you want to.

You can also use CrossOver Office/Crossover Games, which is the commercial version of wine.
That makes less work to get everything running.

Actually, sometimes it doesn't work in wine, but works in crossover - and sometimes, if something doesn't work in crossover, it works in wine...

And if it doesn't work in both, download the latest version from svn and, if necessary, search for a patch via google. If there is none, search the problem and patch it yourselfs.

---

