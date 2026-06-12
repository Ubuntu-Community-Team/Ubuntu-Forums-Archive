---
title: "Installing quicktime for linux"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by Troll_the_Great on 2010-01-10
Hello folks!

I wonder, has anybody manage to install the program "quicktime for linux"? I found it here, but I didn't manage to install it. In the read me file I found this:
```
Building:
Quicktime for Linux requires a built copy of of libmpeg3 in a directory next to itself.
This is used for the mp3 interface.

Your directory structure should thus be:
/my_directory
/my_directory/libmpeg3-*.*.*
/my_directory/quicktime4linux-*.*.*


type "make" in the libmpeg3 directory.
type "make" in the quicktime directory.
type "make util" to get quicktime to build some utilities.


The makefiles automatically configure themselves.  The library is in
i686/libquicktime.a. You should manually set the CFLAGS environment
variable with the optimum optimization parameters for your i686
derivative.
```
I am very confused, I don't know what that means. Can somebody enlight this poor soul? :)
Thanks in advance!

---

### Post by 3rdalbum on 2010-01-10
What do you need it for? I don't think it is maintained. You can play Quicktime movies with Mplayer as long as you have the w32codecs from Medibuntu or Mplayer.hq

---

### Post by Troll_the_Great on 2010-01-10
> **3rdalbum said:**
> What do you need it for? I don't think it is maintained. You can play Quicktime movies with Mplayer as long as you have the w32codecs from Medibuntu or Mplayer.hq

I want to be able to play quicktime movies from the apple site, and I thought that if I install this package I could. Is there another way to see the trailers from apple movies in chromium?

---

### Post by 3rdalbum on 2010-01-10
The Quicktime file format is handled by all video players, and the codecs are handled by the w32codecs pack that you can get from Medibuntu. you additionally need a browser plugin for your chosen video player (for instance, VLC plugin).

If Chromium is not picking up your browser plugins, try updating to the Chrome beta.

---

### Post by Troll_the_Great on 2010-01-10
> **3rdalbum said:**
> The Quicktime file format is handled by all video players, and the codecs are handled by the w32codecs pack that you can get from Medibuntu. you additionally need a browser plugin for your chosen video player (for instance, VLC plugin).

If Chromium is not picking up your browser plugins, try updating to the Chrome beta.

I have both Chromium and Chrome, and if I try to watch trailers on apple site I get "QuickTime required". How can I fix that?

---

### Post by ibuclaw on 2010-01-10
Where did you get quicktime from?

Also - doesn't Helix Player do the same thing?

---

### Post by Troll_the_Great on 2010-01-10
> **tinivole said:**
> Where did you get quicktime from?

I found this quicktime here:
[http://heroinewarrior.com/quicktime.php](http://heroinewarrior.com/quicktime.php)

---

### Post by 3rdalbum on 2010-01-10
> **Troll_the_Great said:**
> I have both Chromium and Chrome, and if I try to watch trailers on apple site I get "QuickTime required". How can I fix that?

That's probably caused by a little bit of Javascript in the page that checks the names of your plugins. I don't know how to get around this. You mentioned in your other thread that Firefox works with these videos - so try using some sort of User Agent Switcher extension for Chrome to make Chrome identify itself as Firefox.

Installing the package you were trying to compile will not solve this problem.

---

### Post by l-x-l on 2010-01-10
I just checked & have the same prob as the OP on apple's site using firefox-3.5.6. When attempting to play a preview clip, it prompts me to get quicktime. I personally detest quicktime (and i-tunes) so I don't mind but it does suck for someone who does want it.

---

### Post by Troll_the_Great on 2010-01-10
> **3rdalbum said:**
> That's probably caused by a little bit of Javascript in the page that checks the names of your plugins. I don't know how to get around this. You mentioned in your other thread that Firefox works with these videos - so try using some sort of User Agent Switcher extension for Chrome to make Chrome identify itself as Firefox.

Installing the package you were trying to compile will not solve this problem.

In order to work with firefox, I have the quicktime plugin installed (and some other tweaks). Where do I find plugins for Chromium? And how can I find out what plugins I have installed? I firefox the plugins are under Tools - Add-Ons, but I don't know where to find them in chromium.

---

### Post by tom.swartz07 on 2010-01-10
> **Troll_the_Great said:**
> In order to work with firefox, I have the quicktime plugin installed (and some other tweaks). Where do I find plugins for Chromium? And how can I find out what plugins I have installed? I firefox the plugins are under Tools - Add-Ons, but I don't know where to find them in chromium.

Okay. Heres the guide that I used, and it works GREAT! It covers everything that you could possibly want to know about media on Ubuntu.

[http://ubuntuforums.org/showthread.php?t=766683&highlight=dvd+flash+medibuntu](http://ubuntuforums.org/showthread.php?t=766683&highlight=dvd+flash+medibuntu)


The area of interest to you would be this:
```
GECKO MEDIA PLAYER/MPLAYERPLUG-IN


Note: If you're experiencing audio or video problems with ALL streams, please refer to the GNOME Mplayer/MPlayer section.

APPLE TRAILERS

For those of you recieving the message "Get the latest Quicktime", when you try to view some trailers (or other non-apple.com Quicktime videos), navigate to "Places > Home", then in the file browser menu, navigate to "View > Show Hidden Files", and tick that option. Within your home directory, navigate to ".mozilla > firefox > ??????.default" and find the file named "pluginreg.dat". Right-click on that file and then choose to open it with a text editor. Alternatively, you could open the terminal and enter a command like the following:

gedit ~/.mozilla/firefox/??????.default/plugingreg.dat

Note: Make sure you replace "??????.default" with the exact name of that folder.

Once you have opened that file with a text editor, search for "QuickTime Plug-in 6.0 / 7:$", then copy and paste "QuickTime Plug-in 7.0 / 7:$" directly above it, but without the quotation marks of course. Close and save, then restart your web browser.

```


You could check your plugins in Chrome by the address bar. Type about:plugins into the address bar, and itll show you everything you want to know about all of your plugins.

Good Luck!

---

### Post by Troll_the_Great on 2010-01-11
> **tom.swartz07 said:**
> Okay. Heres the guide that I used, and it works GREAT! It covers everything that you could possibly want to know about media on Ubuntu.

[http://ubuntuforums.org/showthread.php?t=766683&highlight=dvd+flash+medibuntu](http://ubuntuforums.org/showthread.php?t=766683&highlight=dvd+flash+medibuntu)


The area of interest to you would be this:
```
GECKO MEDIA PLAYER/MPLAYERPLUG-IN


Note: If you're experiencing audio or video problems with ALL streams, please refer to the GNOME Mplayer/MPlayer section.

APPLE TRAILERS

For those of you recieving the message "Get the latest Quicktime", when you try to view some trailers (or other non-apple.com Quicktime videos), navigate to "Places > Home", then in the file browser menu, navigate to "View > Show Hidden Files", and tick that option. Within your home directory, navigate to ".mozilla > firefox > ??????.default" and find the file named "pluginreg.dat". Right-click on that file and then choose to open it with a text editor. Alternatively, you could open the terminal and enter a command like the following:

gedit ~/.mozilla/firefox/??????.default/plugingreg.dat

Note: Make sure you replace "??????.default" with the exact name of that folder.

Once you have opened that file with a text editor, search for "QuickTime Plug-in 6.0 / 7:$", then copy and paste "QuickTime Plug-in 7.0 / 7:$" directly above it, but without the quotation marks of course. Close and save, then restart your web browser.

```


You could check your plugins in Chrome by the address bar. Type about:plugins into the address bar, and itll show you everything you want to know about all of your plugins.

Good Luck!

Thank you for the guide, but as you can see, this guide is for mozzila, not fot chromium. I don't know where to find "pluginreg.dat" in chromium.
I know this guide because that's what I used for seeing apple trailers in firefox.
Any other ideas?

---

### Post by tom.swartz07 on 2010-01-11
> **Troll_the_Great said:**
> Thank you for the guide, but as you can see, this guide is for mozzila, not fot chromium. I don't know where to find "pluginreg.dat" in chromium.
I know this guide because that's what I used for seeing apple trailers in firefox.
Any other ideas?

It should work the same. Chrome(ium) looks for the mozilla plugins and profile data as it operates, rather than creating another folder for cookies, search results, etc. 

If you change it, it should work. It did for me at least.

---

### Post by Troll_the_Great on 2010-01-11
> **tom.swartz07 said:**
> It should work the same. Chrome(ium) looks for the mozilla plugins and profile data as it operates, rather than creating another folder for cookies, search results, etc. 

If you change it, it should work. It did for me at least.

I don't understand. What should I change?

---

