---
title: "Wine doesn't open things."
date: 2009-08-19
forum: New to Ubuntu
---

### Post by metallicamike on 2009-08-19
Ok so for some reason I can't open anything with wine anymore. When I download a .exe file I have the option to open with wine. When I do that nothing happens. Then if I just download and try to open manually wine doesn't even show up on the list. And yes, of course I already have it installed. I don't know if this matters but I do have the wine repos as a source list.

---

### Post by lkraemer on 2009-08-20
Why would you assume that WINE will automatically execute any Windows
EXE file?  Typically, a Windows Software program in installed in
WINE or Crossover, then you click on the Icon created by the install
to execute the software (that you previously installed) which runs in
the WINE or Crossover environment.  If you have purchased Crossover,
and have a Bottle created (for example ... Quicken 2004) then you can use
RUN A WINDOWS COMMAND from the Menu and execute a EXE, COM, or BAT File
if you copy that Folder/Subdirectory into the Bottle that Crossover
created.  I've done this and it works good.

Example:
I have Purchased Crossover, and I installed Family Tree Maker which made
a Bottle FTM-8.  I copied the program PointBlank's folder inside the
Bottle created by Crossover.  Then I execute PointBlank from the
Crossover menu without installing PointBlank.  (PointBlank DOES NOT use
an Install/Setup program.) 

If you just want to run a DOS (EXE, COM, or BAT) file you most likely
need to install, and use Dosbox.  It is in the repos, and there are
tutorials, and Video's.  Use Google Search.

lkraemer

---

### Post by tarps87 on 2009-08-20
Try running it in a terminal
```
wine *pathToExe*
```

I would recommend looking for a alternative native program or if you insist on running programs compiled for window, install windows

---

### Post by alexlafreniere on 2009-08-20
I'm no Wine expert, but if worst comes to worst and you don't want to use it anymore, try running a complete Windows installation in VirtualBox.

---

### Post by Mark Phelps on 2009-08-20
> **metallicamike said:**
> Ok so for some reason I can't open anything with wine anymore. When I download a .exe file I have the option to open with wine. When I do that nothing happens. Then if I just download and try to open manually wine doesn't even show up on the list. And yes, of course I already have it installed. I don't know if this matters but I do have the wine repos as a source list.

It could also be that the particular apps you're trying to run simply don't work in Wine.  Would be good to check that by going to the CodeWeavers application compatibility site using the link below:

[http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true]("http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true")

---

