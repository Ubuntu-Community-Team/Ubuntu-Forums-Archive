---
title: "Strange DVD Playback Issues"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by MockY on 2009-11-12
In the past, I have been able to install all necessary codecs in order to play DVDs but this time it is simply not working.

Using VLC, it spits out the following error:
```
Playback failure:
VLC cannot set the DVD's title. It possibly cannot decrypt the entire disk.
Your input can't be opened:
VLC is unable to open the MRL 'dvd:///dev/sr0'. Check the log for details.
```
I have done the following
```

sudo apt-get install libdvdread4
sudo /usr/share/doc/libdvdread4/install-css.sh
sudo apt-get install ubuntu-restricted-extras 
sudo apt-get install w32codecs
sudo apt-get install libdvdcss2    // Added after edit

```
I have even used **regionset** and manually change it to Region 1, but I still get the same error. I have tried in both Jaunty and Karmic on different machines with the same result.
On Intrepid, extremely jerky sound comes out once all the errors are displayed, but in Karmic, nothing happens after the errors.

What else is there to do?

---

### Post by QIII on 2009-11-12
You may need to add the medibuntu repositories to your sources list and install libdvdcss2.

They've made a "here's the whole shot" C&P text for the command to get Medibuntu set up, and if you scroll down they have instructions on how to get libdvdcss2 installed.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by MockY on 2009-11-12
I forgot to add that to the list in my original post.
libdvdcss2 is already installed

---

### Post by QIII on 2009-11-12
Ouch.  Then this is an interesting problem.

As an aside, my performance with DVD playback got so much better with Karmic (and the new Catalyst 9.10 driver for the ATI card in that machine), that I watched movies I didn't like just for the thrill of it.

I'm running a test right now that is about to finish and I have to check results, so I'm going to have to sign off.  Hopefully someone else will come along shortly...

---

### Post by MockY on 2009-11-12
"interesting" is a relative term in this case  :)
The odd thing is that I have the same issue on two separate machines, one running Jaunty (not Intrepid as earlier stated) and the other one Karmic.
In the past, these packages that I already have installed was enough for getting it to work, but not now. Odd.

I can live without it since I don't watch DVDs on my computers, but the other machine is of an Ubuntu convert. But if I don't get this running, there is no way he is going to change from Windows. So I'll try anything in order to get this running.

---

### Post by soni1770 on 2009-11-12
yea, i've had that problem,

mediabutntu really is the answer,
 uninstall all that stuff from your list then follow the instructions on medibuntu
good luck

---

### Post by MockY on 2009-11-12
Still no go.

---

### Post by MockY on 2009-11-12
I tried it on my other laptop with Karmic installed and the same disc worked just fine there. So can the issue be with the actual DVD drive on the two machines (Jaunty and Karmic). I changed the region code for the Jaunty machine with no good results...so I'm very confused. What is going on here?

EDIT:
I tried what was suggested in this blog, but it still does not work. This is getting extremely frustrating.
[http://ctevisions.com/2009/10/31/play-dvds-with-ubuntu-9-10karmic/](http://ctevisions.com/2009/10/31/play-dvds-with-ubuntu-9-10karmic/)

---

### Post by jmszr on 2009-11-12
MockY,

Perhaps this will be of help: [http://www.ubuntugeek.com/fix-for-vlc-doesnt-play-video-after-ubuntu-9-10-karmic-upgrade.html](http://www.ubuntugeek.com/fix-for-vlc-doesnt-play-video-after-ubuntu-9-10-karmic-upgrade.html)

Some of the tips you've already done, but maybe one of the others will do it.

---

### Post by MockY on 2009-11-12
Thanks for the tip.

However, none of them worked.
VLC still spits out:
```
Playback failure:
VLC cannot set the DVD's title. It possibly cannot decrypt the entire disk.
Your input can't be opened:
VLC is unable to open the MRL 'dvd:///dev/sr0'. Check the log for details.
```
Also, when trying to play the DVD via Totem, it goes gray. This should not be hard, and this whole experience makes my hair go gray as well.

Can the problem be with Ubuntu not liking the DVD player? Or could it be some BIOS settings that Ubuntu does not like?

---

### Post by MockY on 2009-11-12
I ran **regionset** again and for some reason the changes I made before did not stick. The only thing that changed was the amount of resets. I changed it yet again to region 1 and restarted and now it works.

Thanks goodness. I will sure as heck double check what region the drive is set to next time I encounter a similar issue.

Thanks for all help.

---

