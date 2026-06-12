---
title: "street view in google earth 5.0 doesnt load"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by thebestofall007 on 2009-04-26
is there anyone that is having a problem with the street view on google earth 5.0 not loading up completely? the yellow camera icons show up on the map when you enable it, but then flash on and off (with some street names, symbols, etc also flashing) and are not clickable. the checkbox where you enable the street view layer always has the loading symbol next to it after you enable it.

---

### Post by matbroadbent on 2009-04-27
Yeap, exactly the same here.  Installed "5.0.11337.1968-0medibuntu7" package the other day after upgrading to Jaunty and Google Earth's Street View feature does seem to be acting up.

I thought it was some kind of server error their side, as the data keeps refreshing itself/never quite finishes downloading.  But it's been like that for a day or two now.

---

### Post by brunogirin on 2009-04-27
It looks like the panoramio photos don't load either.

---

### Post by brunogirin on 2009-04-27
In fact, it looks like any type of embedded image fails to load.

---

### Post by matbroadbent on 2009-04-27
Are you getting those blue squares with question marks in them too?

---

### Post by brunogirin on 2009-04-27
Yes.

---

### Post by matbroadbent on 2009-04-27
Just done a reinstall from Synaptic, plus cleared my GE-cache, and that's not fixed it.

If you're quick enough, it is possible to grab one of the street view camera icons.  But all it does is take you down to zero elevation above street level.  The Street View globes just keep flicking on and off, without ever actually "unwrapping" and showing the image.

---

### Post by matbroadbent on 2009-04-27
Some fellow forum members were reporting this a couple of days ago over at [http://ubuntuforums.org/showthread.php?t=1132524&highlight=google+earth+5]("http://ubuntuforums.org/showthread.php?t=1132524&highlight=google+earth+5")

No one mentioned Street View though.

---

### Post by Linux Lurker on 2009-04-28
Ditto Here.
Version 4 worked fine for me on Intrepid. Upgraded to Jaunty and Google Earth v5.0.11337.1968 and now not able to use street view.

I played around with settings and was actually able to make it work BRIEFLY by unticking the "Compress" option under 3D View | Texture colors.  I "thought" that was the solution.  Unfortunately, upon restarting the application, it reverted back to exhibiting the same problems.
But... for a couple of minutes, it DID work the way it was supposed to.  So, my guess is that it must have something to do with that.
BTW, my relevant system info:
Kubuntu Jaunty
AMD Phenom 9950 Quad Core
EVGA 01G-P3-N959-TR GeForce 9500 GT 1GB
Nvidia driver version 180.44
4GB 1066 Memory

I have two systems configured nearly identically. Both experiencing the same problems with Google Earth.

Edit: Playing around with the layers by checking and unchecking different options like "Street View", "3D Buildings" & "Borders & Labels" will allow me to get street view to temporarily display.  But even then, once it refreshes, it kicks me back out so that I see the street view as only "bubbles" that I cannot re-enter.

---

### Post by Jack Harkness on 2009-04-29
I had the same problem.  Just installed Kubuntu Jaunty, then GE 5.0 from Medibuntu.  Street View never finishes loading, panoramio photos don't load, just question marks.

I finally gave up and removed 5.0, then downloaded 4.3 from Google and installed it.  It's slightly slower to start up, but everything works.  I'll just stick with it until someone figures out 5.0's issue.

---

### Post by matbroadbent on 2009-04-30
Suggested fix for the Panoramio fault over on Launchpad here: [https://bugs.launchpad.net/medibuntu/+bug/358749/comments/3]("https://bugs.launchpad.net/medibuntu/+bug/358749/comments/3")

YMMV

Will see what they want to do with the Street View problem in due course.

---

### Post by thebestofall007 on 2009-05-02
> **brunogirin said:**
> It looks like the panoramio photos don't load either.

for this remove the file in /usr/share/googleearth/qt.conf with this command:

sudo rm /usr/share/googleearth/qt.conf

and then restart Google Earth. cleared that panoramio issue right up!

---

### Post by nemarona on 2009-05-02
It didn't work for me. I deleted qt.conf but the Panoramio pictures still don't show up.

I'm using 64-bit Ubuntu Jaunty with all the latest updates. I installed GE from Medibuntu.

---

### Post by nemarona on 2009-05-02
I solved it following the instructions from [a previous comment]("https://bugs.launchpad.net/medibuntu/+bug/358749/comments/1") in the bug report. Just replace qt.conf with the following (for 64-bit Ubuntu):
```
[Paths]
Documentation=/usr/share/doc
Libraries=/usr/lib32
Plugins=/usr/lib32/qt4/plugins
Translations=/usr/share/qt4/translations
```

---

### Post by thebestofall007 on 2009-05-03
> **nemarona said:**
> I solved it following the instructions from [a previous comment]("https://bugs.launchpad.net/medibuntu/+bug/358749/comments/1") in the bug report. Just replace qt.conf with the following (for 64-bit Ubuntu):
```
[Paths]
Documentation=/usr/share/doc
Libraries=/usr/lib32
Plugins=/usr/lib32/qt4/plugins
Translations=/usr/share/qt4/translations
```

hmm, oddly enough, that didnt work for me, thats why i deleted the qt.conf file to see if that would work. my guess is that the 32 bit ubuntu's way of using the libraries concerning the qt.conf and google earth is different than the 64 bit version. i am using the 32 bit version.

---

### Post by fireoftroy on 2009-05-03
Make sure you have the ubuntu-restricted-extras from medibuntu installed, including qt4-qtconfig and the related libqt4* programs.

---

### Post by thebestofall007 on 2009-05-07
> **fireoftroy said:**
> Make sure you have the ubuntu-restricted-extras from medibuntu installed, including qt4-qtconfig and the related libqt4* programs.

i do, but i still have the problem with the street view not loading. if there is anyone with a solution, please dont hesitate to CHIME IN!

---

### Post by thebestofall007 on 2009-05-07
i just found out something: when i removed (DIDN'T PURGE IT) the google earth i installed from synaptic and installed the .bin file from google earth's website instead the street view problem goes away. this problem has something to do with the package that is installed from synaptic (i didnt purge the synaptic's google earth because it lets you still keep your configuration files (places, etc) and the problem was still fixed.:))

---

### Post by jespdj on 2009-05-07
> **thebestofall007 said:**
> hmm, oddly enough, that didnt work for me, thats why i deleted the qt.conf file to see if that would work. my guess is that the 32 bit ubuntu's way of using the libraries concerning the qt.conf and google earth is different than the 64 bit version. i am using the 32 bit version.
That's not strange, because you are using 32-bit Ubuntu, which does not have a /usr/lib32 directory. The fix works on 64-bit Ubuntu, where the 32-bit libraries are installed in /usr/lib32. (Google Earth is a 32-bit program).

---

### Post by thebestofall007 on 2009-05-07
> **jespdj said:**
> That's not strange, because you are using 32-bit Ubuntu, which does not have a /usr/lib32 directory. The fix works on 64-bit Ubuntu, where the 32-bit libraries are installed in /usr/lib32. (Google Earth is a 32-bit program).

in my case the fix didnt work because i have a 32-bit ubuntu version. in my case, deleting the qt.conf folder worked. my guess is that it forces google earth to use its own libraries.

---

### Post by james_xxx on 2009-05-09
In 32-bit Jaunty, I also removed the medibuntu googleearth, and installed the .bin from the Google website, and it seems to be working perfectly.

---

### Post by heldal on 2009-05-20
> **james_xxx said:**
> In 32-bit Jaunty, I also removed the medibuntu googleearth, and installed the .bin from the Google website, and it seems to be working perfectly.

Not so with jaunty32 here.

The latest deb from the medibuntu repo has qt.conf removed so panoramio, wikipedia and other pop-ups work. It looks like street-view tries to load images, but fails and that makes the icons flicker on the map and it's impossible to "enter" 3D view.

Results are slightly different when using the latest build from google. Street-view works in a standard install, but photos and some other elements fail to load (displays place-holder icons instead). Google's build includes its own version of a number of Qt libraries. I tried to remove those from /opt/google-earth to make the program use jaunty's version of those libs. Then street-view fails, but photos and other elements work and the GUI becomes consistent (fonts/colors) with the configured qt-preferences. 

This suggest that the problem is related to conflicts between the Qt4.4 libraries that google builds the application with and Qt4.5 included in jaunty.

----

Update: after purging everything related to google-earth and installing build 5.0.11733.9347 from Google I now have the application working when it is using the Qt libraries supplied by Google, although it looks butt ugly when fonts and theme doesn't match the desktop config. I've tried to move /opt/google-earth/libQt* aside which fixes desktop integration, but again breaks street-view. The problem will probably be fixed once Google starts building earth with Qt4.5

---

### Post by DJ_Peng on 2009-07-04
> **james_xxx said:**
> In 32-bit Jaunty, I also removed the medibuntu googleearth, and installed the .bin from the Google website, and it seems to be working perfectly.
Damn. That did the trick for me. Thanks. I needed to get into Street View to help me finish planning my trip to pick up a birthday present that was ordered for me. The MBTA (local mass transit system) uses Google Maps for their trip planner but doesn't use Street View, which will really help me see where I need to walk.

Now if only there were Street View images of more of my route it would really rock. :guitar:

---

### Post by thebestofall007 on 2009-07-23
the replies seem to state that removing the medibuntu google earth and installing the bin file worked. lets mark this as solved.

---

### Post by BigBananaMan on 2009-09-17
Now comes the problem of how on earth do you install the .bin from google?  I've tried but it always gives the same old 32 bit excuse.

---

### Post by texaswriter on 2010-08-16
chmod + x googleearth.bin
./googleearth.bin

---

### Post by dentaku65 on 2010-08-16
Mmmm,
Street View works here with GE of Medibuntu, but Panoramio not.
Launching from terminal:
```
sudo googleearth
```
it works!
...but I don't like to use sudo :-(

---

### Post by texaswriter on 2010-08-16
You mean Panaramio works with sudo?

---

### Post by dentaku65 on 2010-08-17
> **texaswriter said:**
> You mean Panaramio works with sudo?
Yes; I guess that the issue of Panoramio inside GE is regarding permissions somewhere...

---

### Post by texaswriter on 2010-08-18
I installed googleearth from a .bin downloaded from Google Earth website. Panoramio does not work, not with SUDO either. Guess I'll try to uninstall it and find out how to enable medibuntu repositories.

---

### Post by dentaku65 on 2010-08-20
> **texaswriter said:**
> I installed googleearth from a .bin downloaded from Google Earth website. Panoramio does not work, not with SUDO either. Guess I'll try to uninstall it and find out how to enable medibuntu repositories.

My version is the medibuntu one.

---

