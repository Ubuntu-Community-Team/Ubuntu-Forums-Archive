---
title: "Poor performance, Intel integrated graphics, Karmic"
date: 2009-12-23
forum: New to Ubuntu
---

### Post by crantok on 2009-12-23
I was running Xubuntu Jaunty and followed these steps

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

to vastly improve full screen video performance (especially flash video).

I've just done a fresh install of Ubuntu Karmic and am experiencing poor performance again. It looks like the same behaviour as before, but the posts at the end of the above thread say that Karmic should work fine out of the box in this respect.

```
lspci | grep Graphics
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

```Can anyone give me any pointers? Full screen flash video is unwatchable and AVIs played through VLC are not great.

---

### Post by FreezWay on 2009-12-23
i had the same issue. here are some experimental drivers (seem to work ok)

[http://linuxchronicles.wordpress.com/2009/11/14/xorg-edgers-repository/](http://linuxchronicles.wordpress.com/2009/11/14/xorg-edgers-repository/)

occasionally they will be weird, but i haven't had much trouble with them.

---

### Post by crantok on 2009-12-23
Thanks for the quick response FreezWay. Unfortunately, after adding those sources and running Update Manager, my system is so flaky it drops back to the login screen if I open Firefox. Is there any way to revert the changes made by Update Manager?

---

### Post by crantok on 2009-12-23
For anyone who tries adding the sources above and gets a similarly flaky result, I have managed to revert the changes on my machine and get things stable again by:

1) I deleted the new sources from Software Sources.

2) In Synaptic Package Manager I opened File -> History and found the update I performed after adding the new sources. The update listed the old and new versions of each package.

3) I downgraded each package to the original version using the command line ```
sudo apt-get install *package-name*=*old-version*
```Unfortunately I could not downgrade the packages in the same order that they appeared in the History because of dependencies (some of them threatened to remove ubuntu-desktop, xorg and other packages) so I experimented with order until they all downgraded without removing any other packages. Maybe it would have worked first time if I'd put all the downgrades in a single apt-get command?

---

### Post by crantok on 2009-12-23
Uh ... obviously I'm still looking for a solution to the poor full screen video performance. Would be very grateful for any help.

---

### Post by TBABill on 2009-12-23
I had the same thing happen with nVidia on my machine after doing a fresh install. Apparently when you install karmic the system then goes through a series of updates to get your system up to the latest configuration. Once that is done, however, you will need to disable your video driver (assuming you are using a proprietary driver like I am) and then simply install it again. Your system will race like it was after that...or at least mine did. 

I no longer have the glitchy scrolling after reinstalling the proprietary driver a second time (following the system updates).

---

### Post by FreezWay on 2009-12-23
if those drivers didn't work i dont know.

---

### Post by crantok on 2009-12-24
@TBABill : It's cool that your system is flying again. Unfortunately, I don't have any proprietary drivers on my machine so I guess this is a different issue?

@Freezway : Thanks anyway. It was worth a try.

Can anyone tell me if this is the kind of thing I should report as bug?

Or whether following the [**HOWTO: Jaunty Intel Graphics Performance Guide**]("http://ubuntuforums.org/showthread.php?t=1130582")
in Karmic would be counter-productive?

---

### Post by wojox on 2009-12-24
A B or C? Try B and change the ppa to karmic.

---

### Post by crantok on 2009-12-24
Thanks you everyone for the info. I now understand what the PPA I added from [post #2]("http://ubuntuforums.org/showpost.php?p=8550378&postcount=2") was, i.e. the Bleeding Edge step in the [**HOWTO: Jaunty Intel Graphics Performance Guide.**]("http://ubuntuforums.org/showthread.php?t=1130582")

I tried installing the more stable updates from [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates") instead, which are part of the Safe/Optimal steps from the Jaunty guide, but that had no effect on performance. It just installed 4 OpenGL related updates which I guess are not concerned with 2D stuff like video playback?

When that didn't work, I tried each of the other Safe/Optimal steps in the Jaunty guide but none of them had any effect either.

One thing I wondered about. My xorg.conf file did not exist. I tried
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` but that did not create one. Is the same filename still used in Karmic? I only ask this because I don't seem to have a menu.lst in my grub directory any more and wondered if any other configuration files had changed.

---

### Post by bkratz on 2009-12-24
> **crantok said:**
> Thanks you everyone for the info. I now understand what the PPA I added from [post #2]("http://ubuntuforums.org/showpost.php?p=8550378&postcount=2") was, i.e. the Bleeding Edge step in the [**HOWTO: Jaunty Intel Graphics Performance Guide.**]("http://ubuntuforums.org/showthread.php?t=1130582")

I tried installing the more stable updates from [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates") instead, which are part of the Safe/Optimal steps from the Jaunty guide, but that had no effect on performance. It just installed 4 OpenGL related updates which I guess are not concerned with 2D stuff like video playback?

When that didn't work, I tried each of the other Safe/Optimal steps in the Jaunty guide but none of them had any effect either.

One thing I wondered about. My xorg.conf file did not exist. I tried
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` but that did not create one. Is the same filename still used in Karmic? I only ask this because I don't seem to have a menu.lst in my grub directory any more and wondered if any other configuration files had changed.



I have not found where I saw this ( I will keep looking) but somewhere I saw that this command no longer creates an xorg.conf since it has been deprecated in 9.10. This link (although hard to read because of colors) tells how to create one.

[http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html](http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html)


Here is another example.
[http://ubuntuforums.org/showthread.php?t=1325212](http://ubuntuforums.org/showthread.php?t=1325212)

---

### Post by schmolch on 2009-12-24
I dont understand why you mess around with all these PPAs and crap.
If you have a problem with the Intel-Driver (other than flash performance which sucks naturally) then you should get the latest code of the Intel-Driver from their cvs.
If you still have any problems with that you can directly talk to the developers on their mailing-list and they will listen to you because you used their latest code.
I have done that myself several times and they responded to me and i tested their changes until the problem was fixed.

---

### Post by crantok on 2009-12-27
@bkratz : Thanks for the xorg.conf info. Much appreciated. Unfortunately, adding those Jaunty changes didn't help.

@schmolch : You may well be right about going straight to the horse's mouth but...

I'm a bit fed up of this issue now. Not only is video playback worse for me than it was on Xubuntu 9.04, but Spotify (running through Wine) seems to have sound problems too. I've just found a spare hard drive so I'm going to install Xubuntu 9.04 on that in order to make direct comparisons. If anything interesting comes up then I'll post about it.

---

### Post by crantok on 2010-01-06
Well, I've installed Xubuntu 9.04 on that spare hard disc. I had to downgrade the xserver-xorg-video-intel package to 2.4 in order to get video to play.

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

I'd forgotten that I had to do that before.

However, I did **not** need to follow the previously mentioned [how to]("http://ubuntuforums.org/showthread.php?t=1130582") in order to get decent video playback so maybe that has been addressed in subsequent updates.

In addition, Spotify seems to be much more stable.

The end result of all this is that I have Ubuntu Karmic on my low performance laptop because it seems to handle my bluetooth headset better, but I am using Xubuntu Jaunty on my beefier desktop because it gives me better video performance. Go figure. Oh well, everything I want to use is working now so I'm happy :)

---

### Post by warjowuch on 2010-01-16
Hmm, that does not seem like a real solution...
I have also troubles on my mediacentre with intel i855 IGP. I now do jaunty based mint 7 on that machine. But it has some inconveniences, so I'd like to upgrade to mint 8.
But man, on Mint 8 my video sucks big time. If I take my currect xorg.conf from mint 7 install, it is better, but still not on par with my mint 7 performance, which is still not brilliant to my feelings.

So, would there be a sort of solution?
Hm, I have just seen a few bug-reports on launchpad. I have taken the liberty to assign these bugs to the intel graphics team. I hope they do something about it :).

---

### Post by rom85 on 2010-02-01
I have exactly the same toruble as crantok with my i865GLC board in fullscreen. Totem is impossible to use at all as it just shows some slides, with VLC or SMPlayer the situation is a bit better but the video isn't normal. It's like skipping frames, sometimes freezes and cpu load is constant 100%. My system is not powerful but I can comfortably watch those films I've tested under windows. This kill, having no ability to get rid of xp because of those troubles and issues.
Except that, when watching, there's an artefact in the movie when a camera moves. While that, it seems that the upper part of the picture is somewhat faster than the lower. I don't know what to do, I've tested different drivers and parameters in xorg.conf

---

