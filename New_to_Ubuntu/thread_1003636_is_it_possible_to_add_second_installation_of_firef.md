---
title: "is it possible to add second installation of firefox to 8.10?"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by thane1 on 2008-12-06
Want to add a second installation of Firefox, which can be stripped down and hardened for useage with Tor.  Don't want all of my normal settings, etc from my default Firefox instl'n to be available.  8.10 won't seem to allow me to add a second copy of Firefox either through Synaptic or using sudo apt-get install.  Is there a way of doing this?  I installed the Mozilla Seamonkey-Browser prog, but there doesn't seem to be a Firefox-like plugin for Seamonkey to allow it to work with Tor (I installed Tor via Synaptic.)  Just need a stripped down second copy of Firefox.  TIA   cheers.

---

### Post by PierreDeKat on 2008-12-06
In terminal, type:

```
firefox -profilemanager
```

Create additional profiles.

Set up launchers on your desktop, etc., for:

```
firefox -p [profilename1]
```

```
firefox -p [profilename2]
```

etc.

---

### Post by taurus on 2008-12-06
The easiest way is to download the binary version and unpack it in your $HOME.  Then, create a link to that version on your desktop so when you want to use it, just click on the icon.

---

### Post by thane1 on 2008-12-06
Thank you so much gents. Tried the second suggestion first and it worked first time.  Thanks to you both.  I unpacked the Mozilla Firefox site's .tar.bz2 firefox to my /home/thane/ directory and it showed up in a /firefox subdirectory.Next I rt-clicked the Desktop to start the CreateLauncher program.  Gave launcher a Name and used Command of /home/thane/firefox/firefox .  Works great!  Off to the races again.  Cheers

---

### Post by Paqman on 2008-12-06
A good way to do it would be to grab the beta of Firefox 3.1, since it's a lot faster than 3.0 anyway.

It's available from this repo:
```
deb http://ppa.launchpad.net/fta/ubuntu intrepid main
```

---

### Post by mkvnmtr on 2008-12-06
I have to thank you for posting this question. I quit often need more than one browser open and I really like both the solutions.

---

### Post by thane1 on 2008-12-06
Minor glitch here.  I think after all, that I am going to be using a combination of both of the first two responses to my question.  I got the second installation of Firefox working fine, but I'm finding that its accessing not all but a fair number of the original installation's settings, menus, plugins, bookmarks, etc and that if I change any of these specific settings in the new Firefox instl'n, it also changes them in the main instl'n.  Did some googling and realized, that I probably need to use Pierre's ideas as well to complete my Firefox requirements.  I'll report back, when I've either solved my case or come to another dead end.  Thanks to all.  Cheers.

---

### Post by rotwang888 on 2008-12-06
I don't know all that much about it, but you could also try installing "abrowser".  It's an "unbranded" version of Firefox for Ubuntu similar to Seamonkey.

---

### Post by thane1 on 2008-12-06
Update to current situation:  Got both working with so far seemingly separate settings.  Used Pierre's suggestion to get separate profiles concurrently as follows.  (With any and all firefox sessions closed) from terminal as listed in first post response, enter [COLOR="DarkRed"]firefox -profilemanager[/COLOR] and then create your individual profiles with different names.  Then on Desktop rt-click and start the launcher program to create a launcher for the first default firefox program using the opening command of [COLOR="DarkRed"]firefox -p [your first profilename][/COLOR].  Repeat process to make another launcher for the second firefox profile instance using [COLOR="DarkRed"]firefox -p [your second profilename][/COLOR].  Each launcher will then open a separate session with individual custom settings, bookmarks, etc possible.  I then experimented with deleting the second copy of firefox, which I had installed and found everything still worked from the one original firefox installation.  Was able to use the .png firefox icon from [COLOR="DarkRed"]/usr/share/pixmaps/firefox-3.0.png[/COLOR] for a replacement icon for my main firefox Desktop launcher icon.  Used a downloaded free web icon to replace the icon for my second Desktop launcher.  Only remaining problem seems to be that after I dragged a copy of the Desktop launchers up to the TopMenu bar, they would not accept the .png icons.  Only seem to want  .svg icons.  A bit of googling directed my to a program, which is in Synaptic, called inkscape, which should convert .png files to .svg files with a bit of experimentation.  However this might be a bit on the illegal side if I reproduce the firefox icon as a .svg file.  Does anyone know of an official firefox .svg icon source?  Otherwise all seems fine here so far.  Cheers.
[COLOR="DarkRed"][/COLOR]

---

