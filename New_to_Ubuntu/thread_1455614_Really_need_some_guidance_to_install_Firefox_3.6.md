---
title: "Really need some guidance to install Firefox 3.6"
date: 2010-04-16
forum: New to Ubuntu
---

### Post by Peace_n_Pedals on 2010-04-16
I made the change over to Ubuntu 9.10 the other day and am really struggling to get to grips with it. I'm not use to using code and so find all the forums and advice on the internet a bit bewildering but will keep persevering for now! I've been trying to update firefox to 3.6 as I loved using it when I had windows. But I just can't do it. It keeps installing Namoroka...? A google search fills me in that this is some new build release thing of firefox but it just hangs everytime I try and open it. I've just installed some random other browser for now. But I want my good old (ok quite new) firefox 3.6 back with all my bookmarks (which I've backed up).

I'm still confused by how to install things in general so any "idiot proof" help would be an amazing.

Thank you :)

---

### Post by warfacegod on 2010-04-16
Try Swiftfox. It is Firefox with optimized code and as far as I know, all of the F.F. add-ons work with it as well.

[http://www.getswiftfox.com/deb.htm]("http://www.getswiftfox.com/deb.htm")

Skip reading the instructions and just scroll down and click on the proper link for your Processor. When it finishes downloading the file, go to that file and double click it.

---

### Post by Wobblybob on 2010-04-16
This may help you, [http://www.ubuntugeek.com/how-to-install-firefox-3-6-in-ubuntu-karmicjauntyintrepidhardy.html]("http://www.ubuntugeek.com/how-to-install-firefox-3-6-in-ubuntu-karmicjauntyintrepidhardy.html")

---

### Post by Peace_n_Pedals on 2010-04-16
Thanks for the replies so far.

Warfacegod - I don't know what my processor is to install the right version of Swiftfox. Maybe if I install it though I could use it to remove the add-ons from 3.5 (they might be making it hang maybe...?) and then try 3.6

Wobblybob - those were the instructions I initially followed yesterday. Nothing happened and then today it had the Namoroka thing on here instead but it wouldn't open.

Ahh it feels all so complicated! Although I managed to get the wireless card to work all by myself :)

---

### Post by wojox on 2010-04-16
You've got the daily builds installed. Purge all that and remove the ppa. Then follow this how to: [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by warfacegod on 2010-04-16
I don't think it's hanging because of your add-ons (although it is possible). If I remember correctly, Firefox 3.6.4 is supposed to be doing something new with Flash content and it's having serious problems because of it.

---

### Post by Peace_n_Pedals on 2010-04-16
I found out the way to start Firefox/Namoroka in safe mode and disabled Add-ons and it started up fine...progress...woohoo!

However, I'd rather have Firefox 3.6 rather than the pre-release Namoroka. How do I purge the daily builds? Everytime I've removed Namoroka and tried to install an older version of Firefox it just keeps installing Namoroka.

Thanks for the help. Am getting there!

---

### Post by sandyd on 2010-04-16
use ppa-purge or use synaptic to force the package version.

---

### Post by Peace_n_Pedals on 2010-04-16
Thanks Carlee. 

Would you or someone else be able to explain a bit more how I do that? I'm not clued up enough yet to know what ppa-purge is or how to force the package version in Synaptic.

---

### Post by mk1w86 on 2010-04-16
> **Peace_n_Pedals said:**
> Thanks Carlee. 

Would you or someone else be able to explain a bit more how I do that? I'm not clued up enough yet to know what ppa-purge is or how to force the package version in Synaptic.

First download and install the ppa-purge package for Karmic:

[http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/p/ppa-purge/ppa-purge_0.2.6~karmic_all.deb](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/p/ppa-purge/ppa-purge_0.2.6~karmic_all.deb)

Then run:

```
sudo ppa-purge ppa:ubuntu-mozilla-daily/ppa
```

This should remove the ppa and downgrade all the updated packages to the normal Ubuntu versions.

If that works, one way of running Firefox 3.6 is to get it from the Mozilla website:

[http://www.mozilla-europe.org/en/firefox/](http://www.mozilla-europe.org/en/firefox/)

Once you have downloaded the Linux version, extract it, and to run it double click the file called firefox (it's in the directory you have just extracted) and click Run.  If you want to access it system wide you can place the directory in /opt and add a menu entry for it by going to System >> Preferences >> Main Menu. 

Another option is to wait for Ubuntu 10.04 (Lucid Lynx) which will be released in just under two weeks and should have Firefox 3.6 already with it. ;)

---

### Post by lovinglinux on 2010-04-16
Remove the ppa as suggested above, then install Firefox 3.6.

If you are on 32bit, I would recommend the Ubuntuzilla method. If you are on 64bit, then download Firefox from Mozilla. See See the [[COLOR="Sienna"]**Installing Other Versions**[/COLOR]](http://lovinglinux.megabyet.net/?page_id=220#Installing-Other-Versions-1) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by Peace_n_Pedals on 2010-04-18
Thanks again for the help. Rather than wait for the next release I thought I'd have a go at sorting it out as it's good practice! I've now removed the daily builds and got FF 3.6 now. I've still got a couple of problems I'd like to tweak out there if anyone's able to help:

1. I don't seem to have an /opt folder.I'm just running FF from my download folder for now but how do I create this folder (it's not letting me add folders in the main directory)?

2. I've added FF to the main menu but when I go to chance the icon to the FF one I can't find it. 

3. FF isn't saving my passwords. I've checked under preferences and the save passwords box is ticked.

Thanks! Feel like I've learnt loads already in the past couple of days

---

### Post by lovinglinux on 2010-04-18
> **Peace_n_Pedals said:**
> 1. I don't seem to have an /opt folder.I'm just running FF from my download folder for now but how do I create this folder (it's not letting me add folders in the main directory)?

You need to use [sudo](http://en.wikipedia.org/wiki/Sudo)

```
sudo mkdir /opt
```

To move firefox to there you can use something like this:

```
sudo mv ~/Download/firefox /opt/firefox
```

The above command assumes firefox folder is under the Download folder in your home directory.

Nevertheless, running Firefox from your download folder is also fine.

> **Peace_n_Pedals said:**
> 2. I've added FF to the main menu but when I go to chance the icon to the FF one I can't find it. 

```
/usr/share/pixmaps/firefox.png
```

> **Peace_n_Pedals said:**
> 3. FF isn't saving my passwords. I've checked under preferences and the save passwords box is ticked.

Make sure you don't have "Saved Passwords" selected under "Edit >> Preferences >> Privacy >> Clear history when Firefox closes >> Settings"

---

### Post by Peace_n_Pedals on 2010-04-19
Success! Had a play in the Preferences of settings and under Privacy had to select "Use custom settings for history" for all the check boxes to show to allow me to select it not to clear passwords etc.

Have got firefox all sorted now which was a good intro into doing some basic stuff. Thanks again for all the help!

Now on to the next thing on my to do list... :)

---

### Post by rewyllys on 2010-04-19
> **Peace_n_Pedals said:**
> Thanks for the replies so far.

Warfacegod - I don't know what my processor is to install the right version of Swiftfox. . . . 

Click on System in the top taskbar, and from the menu choose Administration > System Monitor.  In the System Monitor pop-up, choose the System tab.  The Hardware section in the window will tell you what your processor is.  If you don't know whether you're running a 32-bit or a 64-bit processor, you're probably running 32-bit; but to be sure, you can always Google the specific processor.

I second Warfacegod's recommendation of Swiftfox.  It works nicely for me.

---

### Post by His on 2010-04-19
What I used was Ubunbuzilla. It's Mozilla builds of mozilla products for Ubuntu.

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page")

Thankfully 10.4 has the latest FF though.

---

