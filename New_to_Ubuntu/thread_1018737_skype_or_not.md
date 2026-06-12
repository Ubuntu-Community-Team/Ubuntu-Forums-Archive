---
title: "skype or not"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by alexinspain on 2008-12-22
First Hi to All !!

Well now i have had enough of Trojans etc on my windows xp laptop (compaq prisario r3200) !!
so now I have just installed ubuntu instead v7.4 and all seams OK as on my tower pc, However i have been trying to install SKYPE for linux Ubuntu but as soon as it finishes down loading I get an _Error : Dependency is not satisfiable : libqt 4-core  _
Anybody have an idea what this means and how to get skype on to my laptop ?
 
Also i down loaded Firefox v3 to the desktop and unpacked it but then what ?
cant get it into synaptic package manager , why ?

And any idea's how to make adjustments to the on board pointing device (pad) ?

All help really welcome Thanks   Alex ):P

---

### Post by Hospadar on 2008-12-22
You should try installing skype from the medibuntu repositories, you can find out how to do that here: [http://www.medibuntu.org/](http://www.medibuntu.org/)

Go to the repository how-to

Once you have that done you can install skype from System->Administration->Synaptic like any other kind of software.

As for firefox, it comes standard in the latest version of ubuntu, why did you install 7.4 instead of 8.10?

---

### Post by M4rotku on 2008-12-22
The first thing that I would recommend is to upgrade from 7.04 to 8.04.  This is the long term support version and it's repositories are probably more up to date.  I know that you can get Firefox 3 on 8.04 and I'm running Skype on it without any problems.

I realize that this might not be the answer that you are looking for, but upgrading will help a lot in the long run.

---

### Post by InfectedWithDrew on 2008-12-22
That dependency error means that the "libgt 4-core" package is out of date for the version of Skype you are trying to install.  You are of course using 7.04 which is a very old release (going to be two years old this upcoming April) compared to 8.04 which was the last LTS (Long Term Support) release or 8.10 which is the current release.  (Ubuntu releases work this way: <year>.<month>)

You could A) upgrade your Ubuntu release, B) fix that dependency error (perhaps sudo apt-get install libgt would work, not sure though, because you seem to have a quad-core processor and I don't know the package name for the quad-core library), C) try using a third-party repo (a guide here: [http://technical-itch.co.uk/2007/09/18/how-to-install-skype-on-ubuntu/](http://technical-itch.co.uk/2007/09/18/how-to-install-skype-on-ubuntu/)), or D) use an older version of Skype.

Now, about FF3, try to find a .deb installer - it will work in a similar way to Windows-style .exe installers and it's much simpler than compiling from source which is what you seem to be trying to do.

----------------
Now playing: [Honor Bright - I Gotta See A Thing About A Girl](http://www.foxytunes.com/artist/honor+bright/track/i+gotta+see+a+thing+about+a+girl)

---

### Post by alexinspain on 2008-12-23
Well thanks for the good advise all !!
So looks I'll be updating to the latest vision !!
                     Thanks Alex

---

