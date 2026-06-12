---
title: "Videos wont play in youtube, or anywhere."
date: 2009-01-28
forum: New to Ubuntu
---

### Post by mr.big_gun on 2009-01-28
i am using firefox and i have adobe flash plugin installed and i also have shockwave player installed. about two months ago i had the same problem, and i fixed it by unistalling adobe flash in terminal and i could watch videos again. then i started to notice little flash things wouldn't show up, like the new player on my myspace profile (just an example). plz help

---

### Post by Crafty Kisses on 2009-01-28
I've sometimes noticed Flash doesn't seem to work when you have multiple Firefox windows running Flash applications, so for example if you're on YouTube watching a video in one window, then in another window you're on a Flash website, it doesn't seem to work. Have you tried opening Firefox and in the URL bar typing the following?
```
about:plugins
```
That should tell you if you have Flash enabled, and if you do what version you have. If you have the latest version, then make sure you clear your cookies, then try YouTube again, and see if it works and make sure that's the only Firefox you have open.

---

### Post by Temposs on 2009-01-28
First, go to Applications->Add/Remove... and check to see that you have the program called "Macromedia Flash plugin" installed. Please install it if it's not installed. If you install it, then restart firefox, and then try to play a video in youtube.

---

### Post by mr.big_gun on 2009-01-28
okay, i just did that and adobe dosen't even show up. i just installed it back on my system through the terminal and it sucessfully installed but it doesn't show in firefox and i cant watch videos anymore

---

### Post by mr.big_gun on 2009-01-28
okay, for codename,, i have it istalled already

---

### Post by RichardLinx on 2009-01-28
For some reason or other the Flash plugin doesn't want to work with Firefox. Try installing Opera and see If it runs through that.

You can get the latest Ubuntu build (.deb) from there site: [http://www.opera.com/download/](http://www.opera.com/download/)

If It doesn't work in Opera, then you should completely remove flashplugin-nonfree (or whatever It's called in Ubuntu).

After removing it run the commands:

```
sudo apt-get autoremove
```
```
sudo apt-get autoclean
```
Really handy commands, they will remove any junk packages. It could be that Firefox is trying to load up an older dependancy.

After that download the Flash 10 .deb from Adobes site:
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
It could be that It just didn't install correctly through the package manager.

---

### Post by Crafty Kisses on 2009-01-28
Run the following commands:
```
sudo apt-get remove --purge flashplugin-nonfree
```
Once you have ran that, try the following:
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by kansasnoob on 2009-01-29
You didn't mention which version of Ubuntu you're running.

If it's 8.10 I'd simply:

```
sudo apt-get install --reinstall ubuntu-restricted-extras
```

Then:

```
sudo apt-get remove flashblock
```

Then - in Firefox - go to Tools > Add-ons > Get Add-ons and search for and install Flashblock 1.5.7.1 or later!

If it's 8.04 still:

```
sudo apt-get install --reinstall ubuntu-restricted-extras
```

But then:

```
sudo apt-get remove flashplugin-nonfree
```

```
sudo apt-get install adobe-flashplugin
```

Then do the same thing as far as removing the repo version of Flashblock and installing Flashblock 1.5.7.1 or newer!

So, you want to know why the newer Flashblock improves flash performance?

I dunno! It just does!

---

### Post by mr.big_gun on 2009-01-29
okay thank you all  what i did was i uninstalled flash in terminal

sudo apt-get remove --purge flashplugin-nonfree

 and i ran what richardlinx said in terminal

sudo apt-get autoremove
then
sudo apt-get autoclean

then i installed it again and it worked perfect
thank you

---

### Post by Crafty Kisses on 2009-01-29
No problem, I'm glad I could help. :)

---

