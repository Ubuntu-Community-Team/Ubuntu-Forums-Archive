---
title: "Video and Radio"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by kyate on 2009-10-07
Hai-
I am new to Ubuntu but I am finding this venture of a Window's free life very rewarding.
However, I am running into a few issues, minor issues.
I enjoy listening to NPR in-between classes and I can't seem to get their online radio to play for me. I also troll around various sites that have video links or streaming video, etc. But I can't seem to watch either.
I am using Jaunty Jackalope on a Compaq Presario 2200 Laptop (awesome...I know *flex)
So I have two questions:

1) Is there an equivalent player I could install for Ubuntu that would work for streaming online radio?
2) Is there something I can install that will allow me to play streaming video/tv?

And I apologize if this has already been addressed...I am basically a noob in anything Ubuntu, including this forum.

~Thx

---

### Post by Sarmacid on 2009-10-07
1. Totem can stream radio for you, it already comes with Ubuntu.

2. I'm guessing you need flash, you can install it by trying to watch a video and following the install instructions or typing in a terminal ```
sudo apt-get install adobe-flashplugin
```

---

### Post by MegaJim on 2009-10-07
Are these flash video players, flash works fine for me :)

You should install the restricted extras package if you haven't done so already, that contains a lot of stuff like a/v codecs which could be the cause of the problem.

---

### Post by kyate on 2009-10-07
> **MegaJim said:**
> Are these flash video players, flash works fine for me :)

You should install the restricted extras package if you haven't done so already, that contains a lot of stuff like a/v codecs which could be the cause of the problem.

Yea, I believe most are Flash players. what is the name of this package?

Also, to Sarmacid:
this is what I got when I entered the code in the command line:

alex@alex-laptop:~$ sudo apt-get install adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package adobe-flashplugin is not available, but is referred to by another package.

---

### Post by MegaJim on 2009-10-07
open up add/remove programs (applications menu) and set the top filter dropdown to all available applications, then type "restricted" in the text filter box.

select the ubuntu restricted extras package and ubuntu should prompt you to enable third-party repositories.  Then hit the apply button and restart firefox

once this is done flash player should be installed next time you browse to a flash page in firefox.

have fun !

---

### Post by QIII on 2009-10-07
While you are at it, open up add/remove programs again and remove swfdec and gnash.  They conflict with Flash if they are installed.

Don't mark for complete removal, since that will likely blow your gnome away...

When you are done, open FireFox (if that is what you are using) and type about:plugins in the nav bar.

Scroll down a bit and find the entries for Flash.

Post what you find, and we'll let you know if you are actually using Flash.

---

### Post by OlsenCNC on 2009-10-07
This is a little strange, but if you go to real.com and download the free Real Player for Linux, the .deb package and install it, then click on the iTunes feed from the wpr site, not the Real Player Stream, it works. 

For some reason, the Real Player Stream would not work, but the iTunes Stream plays in Real Player ok. 

After you install Real Player, it should be the default option after you click "Listen Now" on the wpr's website. Just click OK and Real Player will load and play the station.

---

### Post by kyate on 2009-10-07
> **MegaJim said:**
> open up add/remove programs (applications menu) and set the top filter dropdown to all available applications, then type "restricted" in the text filter box
select the ubuntu restricted extras package and ubuntu should prompt you to enable third-party repositories.  Then hit the apply button and restart firefox
once this is done flash player should be installed next time you browse to a flash page in firefox.

                                                  [quote=QIII]While you are at it, open up add/remove programs again and remove swfdec and gnash. They conflict with Flash if they are installed.[/quote]

There was in fact a conflict when I tried installing via the program menu.
So I went to the command line and forced it...which was probably not wise, but it worked.
I removed swfdec-mozilla and gnash was not installed.

I went to Firefox and About:plugins
I have adobeshockwave and futuresplash installed

---

### Post by oldos2er on 2009-10-07
Vlc can play NPR streams just fine.

---

### Post by OlsenCNC on 2009-10-07
Have you tried Real Player or VLC. Both should play the stream. The page does not require Flash.

---

### Post by OlsenCNC on 2009-10-08
VLC won't Play the Real Player Stream, but it will Play the iTunes Stream. I think it might just be that the "[http://www.wpr.org/webcasting/live.cfm](http://www.wpr.org/webcasting/live.cfm)" Real Player Stream is a bad Link since Real Player won't play the Real Player Stream either. 

All you have to do is go into Add/Remove Applications, switch "Show" to "All Available Applications", and install VLC Media Player.

After it's installed, go to "[http://www.wpr.org/webcasting/live.cfm](http://www.wpr.org/webcasting/live.cfm)" and then click on the iTunes Stream, when "Opening wpr-music-96.m3u" windows pops up, select "Other" from the Open With Menu. Navigate to \usr\bin\ and select "vlc" then click "OK"

VLC will then start streaming the audio from "[http://www.wpr.org/webcasting/live.cfm](http://www.wpr.org/webcasting/live.cfm)"

Hope this works.

---

### Post by kyate on 2009-10-08
Awesome! It does. I can also watch streaming now. Thank you all.

~Kyate

---

