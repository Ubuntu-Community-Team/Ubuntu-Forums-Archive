---
title: "firefox closes unexpectedly"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by Matt26 on 2010-05-07
i just upgraded to Ubuntu 10.04 and now firefox has started crashing without notice.

i tried running it from a terminal windows and got the following message when it crashed:

"Segmentation fault"

anyone know what could be causing this?

---

### Post by phillw on 2010-05-07
Hi,

This is not a 'cop out', but a real good area for trouble shooting Ffox is [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

It is a well supported thread, with plenty of information to help and where you can ask for help.

Regards,

Phill.

---

### Post by dwasifar on 2010-05-07
Did you have Moonlight installed before the upgrade?  If so, try ```
sudo apt-get remove libmoon
``` and see if that fixes it.

---

### Post by lovinglinux on 2010-05-07
> **dwasifar said:**
> Did you have Moonlight installed before the upgrade?  If so, try ```
sudo apt-get remove libmoon
``` and see if that fixes it.

+1

Also would be interesting if you could provide information about your flash plugins version and also if it crashes on any page or particular ones, with flash content.

> **phillw said:**
> Hi,

This is not a 'cop out', but a real good area for trouble shooting Ffox is [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

It is a well supported thread, with plenty of information to help and where you can ask for help.

Regards,

Phill.

+1, but I'm suspicious, since I'm the dude who wrote it :)

Thanks Phill for recommending it.

---

### Post by Matt26 on 2010-05-08
thanks for the responses.. oddly, the plugins section doesn't list anything flash related, so does that mean it isn't installed?  i'm almost certain i had it installed before the upgrade.

i'm not sure how to check for libmoon, can someone point me in the right direction?

---

### Post by lovinglinux on 2010-05-08
> **Matt26 said:**
> thanks for the responses.. oddly, the plugins section doesn't list anything flash related, so does that mean it isn't installed?  i'm almost certain i had it installed before the upgrade.

It is listed as Shockwave Flash. 

> **Matt26 said:**
> i'm not sure how to check for libmoon, can someone point me in the right direction?

Run this on a terminal to remove it...

```
sudo apt-get remove libmoon
```

...or open "System >> Administration >> Synaptic Package Manager" then search for libmoon, mark it for removal and apply.

---

### Post by Matt26 on 2010-05-08
i have Shockwave Flash v10.0 r45.

libmoon is not installed.

---

### Post by Matt26 on 2010-05-12
i've kept firefox open to only the ubuntu forums and the browser is still crashing.

what else can i try here?  the last time this happened i believe it was a flash-related issue.

---

### Post by wojox on 2010-05-12
Open a terminal and launch firefox. Then do what you do until it crashes then look at the terminal screen for anything good.

---

### Post by ubunterooster on 2010-05-12
> **wojox said:**
> Open a terminal and launch firefox. Then do what you do until it crashes then look at the terminal screen for anything good.
He did that
> **Matt26 said:**
> i tried running it from a terminal and got the following message when it crashed:"Segmentation fault"

---

### Post by wojox on 2010-05-12
> **ubunterooster said:**
> He did that

Yes your right. Didn't see that. hmmmmm

---

### Post by wojox on 2010-05-12
Try Alt-F2

Then type in 

```
firefox -safe-mode
```

---

### Post by byStanderone on 2010-05-12
...a 'segmentation fault' is saying that certain dependencies are not satisfied, am wondering what version of firefox it is that you are running in 10,04 at the moment?

---

### Post by Matt26 on 2010-05-12
> **bystanderone said:**
> ...a 'segmentation fault' is saying that certain dependencies are not satisfied, am wondering what version of firefox it is that you are running in 10,04 at the moment?

3.6.3

---

### Post by byStanderone on 2010-05-13
...if you have installed some addons to firefox, you can check on them also to isolate the problem.

---

### Post by wojox on 2010-05-13
And what about safe mode. Does it make a difference?

---

### Post by Matt26 on 2010-05-25
i've had the browser running in safe mode for almost 2 days now with no crashes, running the same websites that i had opened the last time it crashed.

the terminal window has the following message appearing numerous times after the command to run firefox in safe mode:

> (firefox-bin:12851): Gdk-WARNING **: XID collision, trouble ahead

anyone have any idea what this means?

---

### Post by Matt26 on 2010-05-29
still having issues with the browser closing down.. can anyone help me out on this one?

---

### Post by acrazyplayer on 2010-05-29
My answer would be to purge Firefox and reinstall it all again along with the very newest adobe flash player. 
Make a backup of your bookmarks first and write down your add ons someplace so you remember what you had.  

When your ready enter into a terminal 
"sudo apt-get purge firefox*" notice what it says will be uninstalled and make double sure it is what you want gone. Maybe write the uninstall options down so you can check later if they all have been installed again.
after purging everything then simply type 
"sudo apt-get install firefox"

That's is for that. To get the newest flash player type in "adobe flash 10.1" into your fav search engine and download the Linux version of the release candidate 6 or whatever it is now then extract it and copy the extracted file into the directory "/home/your user name here/.mozilla/plugins" if plugins folder does not exist then simply create it. You can do all this without a terminal by simply pressing "control" + "H" together in your home folder and looking for the ".mozilla" folder. 

if your problem still persists then give another browser a shot.

---

### Post by lovinglinux on 2010-05-29
> **acrazyplayer said:**
> My answer would be to purge Firefox and reinstall it all again along with the very newest adobe flash player. 
Make a backup of your bookmarks first and write down your add ons someplace so you remember what you had.

Purging Firefox won't remove your bookmarks or add-ons. 

> **acrazyplayer said:**
> When your ready enter into a terminal 
"sudo apt-get purge firefox*" notice what it says will be uninstalled and make double sure it is what you want gone. Maybe write the uninstall options down so you can check later if they all have been installed again.
after purging everything then simply type 
"sudo apt-get install firefox"

You can do this instead:

```
sudo apt-get install --reinstall firefox
```


> **acrazyplayer said:**
> That's is for that. To get the newest flash player type in "adobe flash 10.1" into your fav search engine and download the Linux version of the release candidate 6 or whatever it is now then extract it and copy the extracted file into the directory "/home/your user name here/.mozilla/plugins" if plugins folder does not exist then simply create it. You can do all this without a terminal by simply pressing "control" + "H" together in your home folder and looking for the ".mozilla" folder. 

[FLASH-AID](http://flash-aid-extension.blogspot.com/) can do that for you.

---

### Post by lovinglinux on 2010-05-29
> **Matt26 said:**
> still having issues with the browser closing down.. can anyone help me out on this one?

Get Firefox 3.6.4 or 3.6.5pre and test it.

See [FoxTester](http://foxtester-extension.blogspot.com/) or if you don't want to test them first, see the [[COLOR="Sienna"]**Installing Other Versions**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/installing-other-versions.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

