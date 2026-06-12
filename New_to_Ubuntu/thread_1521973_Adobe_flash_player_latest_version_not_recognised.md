---
title: "Adobe flash player latest version not recognised"
date: 2010-07-01
forum: New to Ubuntu
---

### Post by Dermot Doyle on 2010-07-01
Hi All,
I've searched the threads, but can't find a solution to my problem. If I try to watch Grand Designs on youtube it tells me that I need the latest version of Adobe Flash Player. I have downloaded it, re-downloaded it, put a command in the terminal that tells me I already have it and looked in Synaptic Package Manager which tells me I have the latest version. None of these has made any difference and I am still told I need to download the latest version. Any ideas?

---

### Post by Kimm on 2010-07-01
Have you disabled javascript, or do you have NoScript (or similar) installed as an addon in firefox?

It might also just be that your browser doesn't realize that the plugin is there, have you tried rebooting? You could also try:

```

sudo ldconfig

```

in a terminal.

---

### Post by QIII on 2010-07-01
Are you using Firefox?

If so, type 

```
about:plugins
```

in the navigation bar and see it the version is Flash 10.1 r53.

If you also see swfdec or gnash in the plugins, uninstall them via Synaptic.  The conflict with Flash.

We'll go from there if you don't get a resolution.

Just for your reference, keep this in your bookmarks.  He posts here and has a great deal of info on Firefox.

[http://lovinglinuxblog.blogspot.com/](http://lovinglinuxblog.blogspot.com/)

---

### Post by Dermot Doyle on 2010-07-01
Hi, thanks for the quick responses. I ran about.plugins and sure enough it says I am running 9.0r124. I have downloaded the new version and Synaptic Package Manager says I have the newest version installed. I'm not particularly good with computers, but is there some simple step I have missed between Synaptic saying I've got version 10 and Firefox not recognising it?
Cheers

---

### Post by Dennis N on 2010-07-01
If your old flash plugin was the package 'flashplugin-nonfree' and the new one is 'adobe-flashplugin', that could be the source of the problem, as these two packages get installed into different directories (at least on my systems) and Firefox may not be looking at the directory with the newer version.

adobe-flashplugin installed in: /usr/lib/adobe-flashplugin
flashplugin-nonfree installed in: /usr/lib/flashplugin-nonfree

I would first use Synaptic to remove the old 9.0 r 124 version and see if that resolves the problem.

---

### Post by Dermot Doyle on 2010-07-02
Hi, I'm sure this is about as basic as it gets in terms of a question, but Synaptic has two listings for adobe flash player: 

Adobe Flash Player plugin version 10
This package will download the Flash Player from Adobe. It is a
Netscape/Mozilla type plugin. Any browser based on Netscape or Mozilla can use
the Flash plugin. This package officially supports the following browsers:

Firefox 2.x, Firefox 3.x, SeaMonkey 1.11

and,

Adobe Flash Player plugin installer
This package will download the Flash Player from Adobe.  It is a
Netscape/Mozilla type plugin.  Any browser based on Netscape or Mozilla can
use the Flash plugin.  This package currently supports the following browsers:
Mozilla, Mozilla-Firefox, Firefox, Iceweasel, and Iceape.  Also Galeon and
Epiphany can use the Flash plugin.  Konqueror can also use the Flash plugin if
konqueror-nsplugins is installed.

WARNING: Installing this Ubuntu package causes the Adobe flash plugin to be
downloaded from [www.adobe.com](www.adobe.com).  The distribution license of the Adobe flash
plugin is available at [www.adobe.com](www.adobe.com).  Installing this Ubuntu package implies
that you have accepted the terms of that license.

 Homepage: [http://wiki.ubuntu.com/FlashPlayer9](http://wiki.ubuntu.com/FlashPlayer9)

They both seem to be installation software so Synaptic seems to think I don't have the flash player at all. Is that right? Firefrox definitely has the older version installed. I must be missing something obvious. I have the install_flash_player_10_linux.deb folder on my desktop, but it doesn't seem to do anything. Advice aimed at the uncomputerate would be appreciated.

---

### Post by philinux on 2010-07-02
> **Dermot Doyle said:**
> Hi All,
I've searched the threads, but can't find a solution to my problem. If I try to watch Grand Designs on youtube it tells me that I need the latest version of Adobe Flash Player. I have downloaded it, re-downloaded it, put a command in the terminal that tells me I already have it and looked in Synaptic Package Manager which tells me I have the latest version. None of these has made any difference and I am still told I need to download the latest version. Any ideas?

Get hold of this addon.

[Flash Aid]("https://addons.mozilla.org/en-US/firefox/addon/161939/")

---

### Post by Dermot Doyle on 2010-07-02
Hi, I downloaded the addon, but nothing changed. My lack of understanding all things computerate may astound you, but I definitely have the old 9.0r124 version installed I just don't seem to be able to install the later version. I've been on the adobe website and downloaded the deb package for 8.04 which is now on my dektop and installed it (I assume) but nothing changes in firefox which lists the older version. What am I doing wrong? Cheers

---

### Post by Dennis N on 2010-07-02
You should check where Firefox is looking for the flash plugin. 

Here is how to find out:

1) Using Firefox, open a new tab and type ```
about:config
``` in the address bar.
2) look for "plugin.expose_full_path" in the left-hand column.
3) double click on this line to change value to 'true'
4) close the tab.

5) Again open a new tab, type ```
about:plugins
``` in the address bar.
6) Look for **Shockwave Flash**.
7) The first line under the name should show now you the full path to the location of the plugin currently in use.

You should see something like this: 

```
File: /usr/lib/adobe-flashplugin/libflashplayer.so
```

(libflashplayer.so is the actual plugin file.)

If you don't see this, that is why the downloaded plugin isn't working. Report back.

---

### Post by Dermot Doyle on 2010-07-02
This is what came up:

File: /usr/lib/flashplugin-nonfree/libflashplayer.so

---

### Post by Dennis N on 2010-07-02
> **Dermot Doyle said:**
> This is what came up:

File: /usr/lib/flashplugin-nonfree/libflashplayer.so

That is what I suspected. You have two different flash player packages installed, and Firefox is ignoring the new one. Use Synaptic Package Manager and see if it shows these two packages both marked as installed:

1) adobe-flashplugin
2) flashplugin-nonfree

(#1 is the new one you downloaded from adobe, #2 is probably from the Ubuntu repository)

Check if this is so, and report back.

---

### Post by Dermot Doyle on 2010-07-02
You're absolutely right. Do I just need to get Synaptic to uninstall the older, nonfree version?

---

### Post by Dennis N on 2010-07-02
You need to:

1) Use Synaptic Package Manager, mark for complete removal 'flashplugin-nonfree' and apply.

2) Close and Restart Firefox. Use ```
about:plugins
``` again to see if it detects the newer plugin. If no flash plugin is listed at all, there is a work around.

Report back.

---

### Post by Dermot Doyle on 2010-07-02
Yes, halfway there, there is no flash plugin detected now. Rebooted just in case, but no change.

---

### Post by Dennis N on 2010-07-02
Here is a workaround:

You need to copy the new flashplugin from '/usr/lib/adobe-flashplugin/' to '/usr/lib/flashplugin-nonfree/'.

[INDENT]Check first to see if the destination folder still exists. It could have been deleted by the uninstall. If it does not exist, recreate it with the terminal:

```
cd /usr/lib/
sudo mkdir flashplugin-nonfree
```

(If is gives an error that the directory cannot be created, with the reason "File exists", then it is still there, so just move to the next step)[/INDENT]

To copy the flash plugin file to its new location, use the Terminal:

```
cd /usr/lib/adobe-flashplugin/
sudo cp libflashplayer.so /usr/lib/flashplugin-nonfree/
```

I think that should fix this problem.

---

### Post by Dermot Doyle on 2010-07-02
You're a genius, thanks a lot

---

### Post by Dennis N on 2010-07-02
Glad to hear that the new flash plugin is finally working.

---

### Post by limestone on 2010-07-02
Flash should be banned :P

---

