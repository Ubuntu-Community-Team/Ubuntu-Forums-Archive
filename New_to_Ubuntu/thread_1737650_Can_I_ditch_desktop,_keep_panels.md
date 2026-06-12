---
title: "Can I ditch desktop, keep panels?"
date: 2011-04-23
forum: New to Ubuntu
---

### Post by LewRockwellFAN on 2011-04-23
Is there any good reason, other than tradition and fulfilling expectations, to treat the desktop directory differently from other directories? Although nautilus seems to have gotten a lot better recently, "killall nautilus" is still the first thing I try if I suspect a low memory problem. When I do that the "desktop" becomes just an inert picture but as far as I can tell I can still do anything I could with it just by going there in Thunar, and, in truth, I really like the detailed view better than the desktop-style display.  Am I missing something? What would I change to have Ubuntu boot up with a "desktop" that was just a background picture in between the top and bottom panels? Is there any good reason I shouldn't do this? Can I leave nautilus as an optional file browser that doesn't use any memory until invoked? And if I like that, is there a part of it used only to manage the desktop I could just uninstall and leave the file browser part? And if I find myself using thunar exclusively, can I unistall the whole thing? In either scenario, what specific packages would I uninstall or config files would I change? TIA for any thoughts on this.

---

### Post by dwasifar on 2011-04-23
I think you're asking for trouble if you remove Nautilus and expect the panels to still work properly.

If you don't want to use the desktop, just don't put anything on it.  The memory footprint is not that large; you wouldn't be saving much in the way of resources by trying to unbundle bits and pieces of Nautilus. 

If you're really tight on resources, and you don't care about using the desktop in the customary way, you should try LXDE instead of Gnome.  It's really light on resources.

---

### Post by LewRockwellFAN on 2011-04-23
Thanks, Dwasifar.
> **dwasifar said:**
> I think you're asking for trouble if you remove Nautilus and expect the panels to still work properly.You are probably right. But I often ask for trouble. That is what partition imaging is for. I like to tinker. I learn that way.


> **dwasifar said:**
> If you don't want to use the desktop, just don't put anything on it.  The memory footprint is not that large; you wouldn't be saving much in the way of resources by trying to unbundle bits and pieces of Nautilus. I'm sure you're right, but I'm playing around with custom livedisks that I can use anywhere. In the GVFS environment, it seems to me, every mB counts. Please correct me if you think I'm wrong. Also, there is something to be said for exploring configurations that differ minimally, both to understand exactly what behaviour resulted from what change and to reduce unexpected differences when using different environments.

> **dwasifar said:**
> If you're really tight on resources, and you don't care about using the desktop in the customary way, you should try LXDE instead of Gnome.  It's really light on resources.I'm interested. At one time, in Sabayon, the default installation included a menu at boot, I think just before or maybe just after logging in, that let you choose an environment, so you could start in gnome, kde, or fluxbox. Is there some way to do this in Ubuntu, so I can test drive desktops on a hd based installation without committing to exclusive use of one or the other?

---

### Post by Rubi1200 on 2011-04-23
Two options:

1. try one of the other *buntu versions such as Xubuntu (xfce) as a LiveCD to see if you like it

2. install the different desktop environments in your current install and choose which one to start at the login screen. Search Synaptic to find the packages.

I have already tried xfce, openbox, and fluxbox. For the most part, there are no conflicts with the default Gnome install (assuming that is what one is using in the first place)

Hope this helps.

---

### Post by Zimmer on 2011-04-23
I recall I installed a n other desktop with Gnome once and I was given the option at login to change the session to the other desktop, I think it was LXDE... but it cluttered up the gnome menus with all the alternative software it loaded.

I am currently writing from a test partition on a USB drive running Mint LXDE . 
I suggest an external USB HD for installing and testing various flavours of the desktop, keeping your working install working, as it were :)

---

### Post by LewRockwellFAN on 2011-04-23
Thanks, Rubi.
> **Rubi1200 said:**
>  . . .  install the different desktop environments in your current install and choose which one to start at the login screen. Search Synaptic to find the packages.
I take that to mean the menu to choose environment comes automatically when an alternate environment is installed and installing one doesn't wipe out what I have. If nobody contradicts that assumption here before I get to it sometime today, I'll try that. Thanks.

 I appreciate these responses and will probably act on parts at least of both. But I'm still curious about my original question re nautilus and doing without a special desktop display mode altogether  but just looking at it like any other directory, either with no nautilus or with just some part of it needed to use it as a file browser. Dwasifir implies he suspects the gnome panels may depend on part or all of nautilus without quite saying they do and I do appreciate that insight. But I'm not terribly afraid of breaking things. That's what partition imaging is for and I keep my data on a separate data partition. But I would love to have some more explicit comments on the subject if anyone has any to offer afore I pull out my pocket knife and start carving chunks out of this system. Do the gnome panels depend on part of nautilus and if so, is it a part I can separate from the part that draws the desktop icons and manages clicks on the desktop? The fact I can "killall nautilus" and they still seem to work fine even though the desktop becomes an inert image that doesn't respond to clicks and has no icons would seem to indicate they don't depend on it. If anybody believes they may see a hole in that logic or a misstatement of fact I'd be interested. I'm not ***just*** trying to set up installations in ways I'd like to use them. I'm also trying to understand them better. So I'm not desperate and I don't want to impose on anyone's time but if you feel like commenting on any of this, I'd be interested to read it. TIA.

---

### Post by LewRockwellFAN on 2011-04-23
> **Zimmer said:**
> I recall I installed a n other desktop with Gnome once and I was given the option at login to change the session to the other desktop, I think it was LXDE... but it cluttered up the gnome menus with all the alternative software it loaded.

I am currently writing from a test partition on a USB drive running Mint LXDE . 
I suggest an external USB HD for installing and testing various flavours of the desktop, keeping your working install working, as it were :)Thanks, Zimmer. I do that some. But boy, that mother is slooooow. Slower than my CD drive with a live disk. Probably the usb port is usb1 and that's the bottleneck. It also has some strange issue with rebooting. Can only cold boot. Hot reboot and it hangs. I also have a total of 5 bootable partitions on internal hard drives so I can use one of them as a testbed. Maybe it's time to give up a Sabayon or W2k.

---

### Post by JKyleOKC on 2011-04-23
Thunar is a lighter replacement for nautilus, that's the standard file manager in XFCE. It doesn't have all the features of nautilus, particularly the ability to scan your LAN if you have one, but is quite capable in most areas and does fit your request to just have a picture between the panels. Its panels are different from those of Gnome, so you might have to reconfigure all of your launchers for it though...

---

### Post by d3v1150m471c on 2011-04-23
you could use blackbox with perlpanel.

[URL="http://s892.photobucket.com/albums/ac121/d3v1150m471c/Desktop/?action=view&current=2011-04-14-234409_1280x800_scrot-1.png#%21oZZ1QQcurrentZZhttp%3A%2F%2Fs892.photobucket.com%2Falbums%2Fac121%2Fd3v1150m471c%2FDesktop%2F%3Faction%3Dview%26current%3D2011-04-23-141023_1280x800_scrot.png"]see my desktop album here
[/URL]

---

### Post by Krytarik on 2011-04-24
The panels themselves don't depend at all on Nautilus, as you already experienced.

You can disable Nautilus' handling of the desktop by unticking the key "/apps/nautilus/preferences/show_desktop" in "gconf-editor".

You can try to replace Nautilus completely by, for example, Thunar by following this guide:
[https://help.ubuntu.com/community/DefaultFileManager](https://help.ubuntu.com/community/DefaultFileManager)

As for file managers, I just very recently noticed that PCManFM is, too, really great and fast as hell, even faster than Thunar, and it even includes toolbar buttons (of reasonable size) and a search feature, as opposed to Thunar.

Greetings.

---

### Post by yetiman64 on 2011-04-24
> What would I change to have Ubuntu boot up with a "desktop" that was  just a background picture in between the top and bottom panels?Open a terminal and put in ,
```
gconf-editor
```navigate to Apps > Nautilus > Preferences, and de-tick the entry show_desktop. With this setting de-ticked the files in ~/Desktop don't show on the desktop between the panels. I think that is what you want at least from my reading of your first post.

You can also as has been mentioned try different desktop envirnoments.

Edit: just noted [Krytarik]("http://ubuntuforums.org/member.php?u=1187548") covered this in the last post. Apologies for the doubling up of this info.

---

### Post by LewRockwellFAN on 2011-04-24
> **JKyleOKC said:**
> Thunar is a lighter replacement for nautilus, that's the standard file manager in XFCE. It doesn't have all the features of nautilus, particularly the ability to scan your LAN if you have one, but is quite capable in most areas and does fit your request to just have a picture between the panels. Its panels are different from those of Gnome, so you might have to reconfigure all of your launchers for it though...
Thanks, JKyleOKC. Yeah, Thunar is GREAT. I didn't realize the same project had panels. I'll check them out. Right now I use thunar pretty regularly. Seems faster at everything except cut and pasteing of large files within the same partition. I guess it must copy and delete whereas Nautilus must just rewrite directories. Didn't know about Nautilus scanning the LAN. I'll check that out too.

> **d3v1150m471c said:**
> you could use blackbox with perlpanel.
[URL="http://s892.photobucket.com/albums/ac121/d3v1150m471c/Desktop/?action=view&current=2011-04-14-234409_1280x800_scrot-1.png#%21oZZ1QQcurrentZZhttp%3A%2F%2Fs892.photobucket.com%2Falbums%2Fac121%2Fd3v1150m471c%2FDesktop%2F%3Faction%3Dview%26current%3D2011-04-23-141023_1280x800_scrot.png"]see my desktop album here
[/URL]
Thanks.devil. I've read a little about blackbox and it's forks. Perlpanel is new to me. I'll check it out. [SIZE=1]** N07h1n6 i5 7ru3**[/SIZE] ? So Vacuum is Veracious?

> **Krytarik said:**
> The panels themselves don't depend at all on Nautilus, as you already experienced.

You can disable Nautilus' handling of the desktop by unticking the key  "/apps/nautilus/preferences/show_desktop" in "gconf-editor".

You can try to replace Nautilus completely by, for example, Thunar by following this guide:
[https://help.ubuntu.com/community/DefaultFileManager](https://help.ubuntu.com/community/DefaultFileManager)

As for file managers, I just very recently noticed that PCManFM is, too,  really great and fast as hell, even faster than Thunar, and it even  includes toolbar buttons (of reasonable size) and a search feature, as  opposed to Thunar.

Greetings.

Thanks, Krytarik. That is exactly what I needed to know. I've already  switched my places menu to Thunar. On my hd based systems I like having  Nautilus available as a file manager as long as it can be made to lie  quietly on the hard drive until I need it and go away when closed. I'll  study that doc and I'll take a second and longer look at PCManFM (I  don't remember the "FM" so maybe it isn't the same I looked at earlier  anyway) with particular attention to those features.

Thanks, [yetiman64]("http://ubuntuforums.org/member.php?u=1043255"). Redundant confirmation is always great. Great minds run in like channels.  lol, I try to pay a little forward by answering simple ones in Absolute Beginners whenever I can, and half the time by the time I finish my slooowly typed response to a 0 reply question it has a 3 answers.

-------------------------
Thanks a lot, guys. I really appreciate all your responses. This is a great forum. If I come with interesting things in doing this, I'll report back. Marking this solved for now.

---

### Post by Krytarik on 2011-04-24
> **LewRockwellFAN said:**
> I'll  study that doc and I'll take a second and longer look at PCManFM (I  don't remember the "FM" so maybe it isn't the same I looked at earlier  anyway) with particular attention to those features.
I guess it's the same thing, "FM" just stands for "File Manager", and "PCManFM" is the official name/abbreviation.

---

