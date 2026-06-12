---
title: "what is the best flash / flv video player?"
date: 2010-07-25
forum: New to Ubuntu
---

### Post by 007casper on 2010-07-25
I just want to install flash video player... the quickest way from synaptic. 

what is the best media player that would handle this?  I have been looking at synaptic, and cant make up my mind, and I did search the forums without any luck.

thank you.

---

### Post by 007casper on 2010-07-25
I just went with totem.  If there are better players out there, please let me know.  Thank you.

[http://ubuntuforums.org/showthread.php?t=113251&highlight=play+flash+videos](http://ubuntuforums.org/showthread.php?t=113251&highlight=play+flash+videos)

---

### Post by 007casper on 2010-07-25
I get 

> The playback of this movie requires a application/x-shockwave-flash decoder plugin which is not installed.

any advice?

---

### Post by L2U2K2E on 2010-07-25
I prefer VLC media player for everything. It's not too pretty, but it will play anything without a fuss.

---

### Post by k3lt01 on 2010-07-25
I have had a little difficulty with flv in Totem so I went looking for an application that would play everything I throw at it (videos that is) and I installed VLC. I have never had an issue with it and have even removed Totem from my system.

---

### Post by k3lt01 on 2010-07-25
> **007casper said:**
> I get 



any advice?
Install restricted extras package.

---

### Post by munkyeetr on 2010-07-25
vlc +1

---

### Post by 007casper on 2010-07-25
vlc is giving me the same error
> The playback of this movie requires a application/x-shockwave-flash decoder plugin which is not installed.

I am sorry what do you mean by ~Install restricted extras package?
on the repo I have main, universe, restricted, multiverse already seleceted

---

### Post by nmaster on 2010-07-25
you need to install flash. do this at the terminal:
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by 007casper on 2010-07-25
yeah, did that... even shut down the computer, and restart

no luck. Now, it doesnt give any error and doesnt play either on vlc player.  On totem, it still gives the same error "The playback of this movie requires a application/x-shockwave-flash decoder plugin which is not installed."

The video does play on win with gom player

---

### Post by lovinglinux on 2010-07-25
Get [FLASH-AID](http://flash-aid-extension.blogspot.com), an extension to remove conflicting flash plugins and install the proper version according to your browser architecture.

Then see [Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683")

---

### Post by k3lt01 on 2010-07-25
Have you got the Medibuntu repo in your list?

Go to synaptic, do a search for flash and install. Check the screenshot.

---

### Post by 007casper on 2010-07-25
I do have medibuntu on the repo now.

when I type flash on synaptic, I dont get adobe-flashplugin at all.
I do have flashplugin-installer, and flashplugin-nonfree installed.

The problem still continues.  I uninstalled mplayer.  I got vlc player, and totem installed.

---

### Post by gandaran on 2010-07-25
> **007casper said:**
> I get 



any advice?
hi
I think you are trying to play shockwave directory files, if it is true you can forget it, you need the shockwave player and adobe din't make one for linux.
all the players you tried only play flash videos not flash shockwave files, if you want to play shockwave flash files try out swfdec player or gnash player from synaptic (just a warning! don't install the gnash or swfdec plugins, install only the stand alone player) or you can download the stand alone flashplayer for linux from adobe.com

---

### Post by masque7 on 2010-07-25
> **k3lt01 said:**
> and have even removed Totem from my system.
When I did that Nautilus spat loads of errors at me. Taking it you can't just apt-get remove totem?

---

### Post by k3lt01 on 2010-07-25
> **masque7 said:**
> When I did that Nautilus spat loads of errors at me. Taking it you can't just apt-get remove totem?It's 3am, I'm cold, feel off, can't sleep, and here I am taking screenshots to show I don't have Totem. Doesn't that just give you the warm fuzzies? ;)

Btw, when I removed Totem I didn't get any error messages. You may need to take a look at what it says and we can help you out.

---

### Post by gandaran on 2010-07-25
> **007casper said:**
> I do have medibuntu on the repo now.

when I type flash on synaptic, I dont get adobe-flashplugin at all.
I do have flashplugin-installer, and flashplugin-nonfree installed.

The problem still continues.  I uninstalled mplayer.  I got vlc player, and totem installed.
the adobe-flashplugin is in the canonical partner repo not medibuntu, you have to enable the repo in software sources, and just forget installing it because it's just exactly the same adobe flash plugin as the flashplugin-installer, theres no deference.

---

### Post by Excedio on 2010-07-25
Can you send us a link to the video you are trying to watch? We can test to see if it's the video or something else.

---

### Post by headbuster on 2010-07-25
vlc +1

---

### Post by 007casper on 2010-07-25
I think it is the shockwave player problem, and the 'puter is 64bit... I guess adobe is sleeping

boo@ha:~$ sudo apt-get install adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package adobe-flashplugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package adobe-flashplugin has no installation candidate

[http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)
We have temporarily closed the Labs program of Flash Player 10 for 64-bit Linux, as we are making significant architectural changes to the 64-bit Linux Flash Player and additional security enhancements. We are fully committed to bringing native 64-bit Flash Player for the desktop by providing native support for Windows, Macintosh, and Linux 64-bit platforms in an upcoming major release of Flash Player. We intend to provide more regular update information on our progress as we continue our work on 64-bit versions of Flash Player. Thank you for your continued help and support. Stay tuned to the Flash Player discussion forum for further announcements.


went through the whole list of updates, installations, trying everything under the sun
Comprehensive Multimedia & Video Howto
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

then I got on totem
GStreamer encountered a general supporting library error.

Gnome Mplayer said
Compressed SWF format not supported

installed gnash... no luck - removed
installed swfdec-gnome, libswfdec-0.8-0... no luck -removed

since I did all these installations, rebooting computer...

---

### Post by gandaran on 2010-07-25
> installed gnash... no luck - removed
installed swfdec-gnome, libswfdec-0.8-0... no luck -removed
okay, try the adobe stand alone flashplayer then, download [here]("http://download.macromedia.com/pub/flashplayer/updaters/10/flashplayer_10_sa.tar.gz") extract the package and double click the icon to start the player, this player only plays sockwave flash .swf files, this player doesn't play flash videos and wont play shockwave directory files too.

edit,
I not sure if it will work on your 64-bits system!

---

### Post by 007casper on 2010-07-25
gandaran - awesomeeeeee!  Thank you... thank you so much, that did it.  It plays.

how can I place this player under Applications > Sound & Video

thank you everyone for helping out...

---

### Post by nush on 2010-07-25
try
system them main menu.
on the left hand column select
sound and video
check the box next to your chose player
hope that helps
nush

---

### Post by 007casper on 2010-07-25
great.  It was hiding from me... thank you

---

### Post by DooM55 on 2010-10-25
> **gandaran said:**
> okay, try the adobe stand alone flashplayer then, download [here]("http://download.macromedia.com/pub/flashplayer/updaters/10/flashplayer_10_sa.tar.gz") extract the package and double click the icon to start the player, this player only plays sockwave flash .swf files, this player doesn't play flash videos and wont play shockwave directory files too.


[http://download.macromedia.com/pub/flashplayer/updaters/10/flashplayer_10_sa.tar.gz](http://download.macromedia.com/pub/flashplayer/updaters/10/flashplayer_10_sa.tar.gz)

the link dosen't work

---

### Post by beew on 2010-10-25
> **masque7 said:**
> When I did that Nautilus spat loads of errors at me. Taking it you can't just apt-get remove totem?

Like k3lt01 I also removed Totem (and Rhythmbox as well ) and use VLC. I never have any problem with the removal.

---

### Post by mahmoodkamal on 2010-10-26
try installing gnash from software center

---

