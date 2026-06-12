---
title: "has anyone got compiz 0.9.2 working?"
date: 2010-10-25
forum: New to Ubuntu
---

### Post by rockorequin on 2010-10-25
I downloaded compiz 0.9.2 ([http://releases.compiz-fusion.org/0.9.2/](http://releases.compiz-fusion.org/0.9.2/)) and built and installed it ([http://wiki.compiz.org/Installation/Development](http://wiki.compiz.org/Installation/Development)) on both a 32-bit Lucid installation and 64-bit Maverick installation, and although it runs without crashing or complaining of any errors, there are no window decorations (and yes, I am running the 0.9.2 gtk-window-decorator and have window decorations enabled in 0.9.2's ccsm). Also none of the plugins work (eg there is no compositing). Has anybody else had any success with it?

---

### Post by rburkartjo on 2010-10-25
rock uninstall the dev file and delete all compiz files and reinstall. problem seems to be with the dev program

---

### Post by rockorequin on 2010-10-25
By "uninstall the dev file", do you mean uninstall compiz 0.9.2 completely? I did do that, and I do have compiz 0.8.6 still working just fine, I just couldn't get 0.9.2 to work at all and yet the compiz devs say it is ready for general use.

---

### Post by trikster_x on 2010-10-25
It is not ready for general use.  It actually caused major problems for a lot of people.  Right now 0.8.6 is the version that is stable on Ubuntu.

---

### Post by rockorequin on 2010-10-26
I guess it's not ready for general consumption. I was hoping it might be because it's supposed to be much faster (when I tested it, glxgears ran faster with compiz 0.9.2 than in metacity!) and use less memory, and 0.9.2 only just came out ([http://www.phoronix.com/scan.php?page=news_item&px=ODcxMA](http://www.phoronix.com/scan.php?page=news_item&px=ODcxMA)). At least it doesn't crash all over the place any more like 0.9.0 did.

---

### Post by rockorequin on 2010-10-26
OK, I solved the problem. I needed to specify ccp on the command line (I was only specifying --replace):

compiz --replace ccp &disown

and manually start the window decorator (I must have had it misconfigured in ccsm):

gtk-window-decorator --replace &disown

and then everything works almost normally. Clicking on avant-window-navigator doesn't work, and resizing windows was a bit slow and jerky, and the glxgears animation was jerky and only about the same speed as 0.8.6. And then it crashed.

---

### Post by AbtZ on 2010-11-02
Just thought I'd add a post to thank you for going through the trouble for me, so I don't have to do it myself only to reach the conclusion that it wasn't worth it. :)

So, yeah. Thanks! :P

---

### Post by afrodeity on 2010-11-03
I think I accidently upgraded to 0.9. on maverick How to return to a working compiz?

---

### Post by rockorequin on 2010-11-04
> **afrodeity said:**
> I think I accidently upgraded to 0.9. on maverick How to return to a working compiz?

Does compiz --version show 0.9 and 'which compiz' show something like like /usr/local/bin/compiz? In that case, you have accidentally upgraded. Compiz 0.8.6 is probably still on your system, though, in /usr/bin.

If you upgraded by downloading the source tarballs and building/installing them, doing a "sudo make uninstall" from the various folders should do the trick. But be careful, you have to uninstall in the correct order, ie:

ccsm compizconfig-backend-gconf compizconfig-python libcompizconfig compiz-core

I used the attached script to build, install or uninstall from the tarballs, ie uninstall with "./build-compiz.sh uninstall" run from the parent source folder.

---

### Post by rockorequin on 2010-11-04
BTW, if you don't mind risking running the version from git, it's safer to build from the script at [http://forum.compiz.org/viewtopic.php?f=112&t=12565#p77557](http://forum.compiz.org/viewtopic.php?f=112&t=12565#p77557), ie where it says:

```
git clone git://anongit.compiz.org/users/soreau/scripts
./scripts/build_compiz++
```

It installs to /opt/compiz++ so you can run it manually for testing but the stable compiz remains the standard one.

The git version still has the same bugs that I found in 0.9.2, though, and it still crashes every so often.

---

### Post by rockorequin on 2010-11-17
The latest compiz 0.9 from git is working much better now. The window animations are pretty smooth and glxgears reports similar framerates to compiz 0.8.6 (although it still keeps stopping/starting in a jerky fashion). AVN still has that bug where if you click the icon to minimize the window and then click it again to restore it, nothing happens - if you click another icon then the minimized one again, it restores the window correctly, though.

The window previews for minimized windows in AVN are pretty cool!

---

