---
title: "Need help with Konqueror"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by gshockxc on 2009-07-29
Why do sites display in Firefox but not in Konqueror?

[http://www.suzukiauto.com/](http://www.suzukiauto.com/) is just one example.  Jaunty.

Thanks.

---

### Post by zeroseven0183 on 2009-07-29
I had no problems accessing the site. Although I need to install Adobe Flash Player first to view other items.

---

### Post by gshockxc on 2009-07-29
> **zeroseven0183 said:**
> I had no problems accessing the site. Although I need to install Adobe Flash Player first to view other items.

I can get to it, but it's just a background.  There's nothing to see.  How do I install the Adobe Flash Player?

I'm not sure which package I need.  Once I download the right file, how do I install it?

I checked Synaptec and I already have the Adobe Flash plug-in, as well as the konqueror-nsplugins.

For some reason, Firefox doesn't display everything, and Konqueror won't even load the page, or loads a blank page.

---

### Post by gshockxc on 2009-07-29
I tried to install the Adobe Flash plugin, and I followed the instructions for Linux on their website.  I tried to double-click on the .deb file, but I get an error with the KPackageKit.  I get a pop-up dialog that says, "Sorry, an error occured."

Behind that pop-up is another dialog that says, "Unknown error, please report a bug.  More information is avail..."  The dialog is grayed out so I can't even click the details button to give you anymore information.  If I click 'OK' on the top dialog, all the pop-ups disappear.

Then I tried to install using the terminal window.  I can't get any of the methods to work.  The only one that appears to do anything is: 

```

sudo apt-get update

```

But it doesn't actually solve the problem, because the websites don't display any differently.  Please help.  I'm getting so frustrated because I can't seem to make any progress.

---

### Post by abn91c on 2009-07-29
go to the konqueror settings>plugins>plug in tab>scan for plugins, there should be something listed there like [COLOR="Blue"]**Netscape plugins **[/COLOR]

---

### Post by gshockxc on 2009-07-29
OK, I'm there, and I see the netscape plugins.  I have a 'Folders' window, and a 'Plugins' window.  I see the Netscape plugins listed, and the first one is x-shockwave-flash.  The description says it's an Adobe Flash Movie.

Everything else is mplayerplug, libtotem..., or libvlcplugin.

So what do I do from here?  In the 'Folders' window, do I move the Netscape plugins to the top of the list?  I have something called $HOME/.mozilla/plugins, and $HOME/.netscape/plugins, in that order.  What do I do from here?

---

### Post by abn91c on 2009-07-29
> **gshockxc said:**
> OK, I'm there, and I see the netscape plugins.  I have a 'Folders' window, and a 'Plugins' window.  I see the Netscape plugins listed, and the first one is x-shockwave-flash.  The description says it's an Adobe Flash Movie.

Everything else is mplayerplug, libtotem..., or libvlcplugin.

So what do I do from here?  In the 'Folders' window, do I move the Netscape plugins to the top of the list?  I have something called $HOME/.mozilla/plugins, and $HOME/.netscape/plugins, in that order.  What do I do from here?
click on the scan button then restart konqueror an try the website again, I'm attaching a pic of my list(i did not have problems with the car website)

---

### Post by gshockxc on 2009-07-29
Here's the website I'm trying to visit: [www.suzukiautos.com](www.suzukiautos.com)

Here's what I'm seeing in Konqueror.



[IMG]http://i33.photobucket.com/albums/d89/kristanxc/Suzukiautos.png[/IMG]

---

### Post by gshockxc on 2009-07-29
Here are the plugins that I have so far.


[IMG]http://i33.photobucket.com/albums/d89/kristanxc/Konqueror-Plugins.png[/IMG]

What do I need to do/change to make these pages display correctly?

Thanks.

---

### Post by gshockxc on 2009-07-30
> **abn91c said:**
> click on the scan button then restart konqueror an try the website again, I'm attaching a pic of my list(i did not have problems with the car website)

Yup, tried that.  but tried again just to make sure.  I think I found the reason why I'm having issues.  

I'm running x86-64-bit linux, and there aren't any adobe flash plugins yet for 64-bit browsers.  Lesson learned.

[http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

---

### Post by RomeReactor on 2009-07-30
Hi.
> **gshockxc said:**
> I'm running x86-64-bit linux, and there aren't any adobe flash plugins yet for 64-bit browsers.  Lesson learned.
There is a 64 bit plugin. You can get it [here]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz").

---

### Post by gshockxc on 2009-07-30
> **RomeReactor said:**
> Hi.

There is a 64 bit plugin. You can get it [here]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz").

Sweet.  Thanks.  I downloaded and extracted the file.  Next question, how do I install it.  I don't recall installing a .tar.gz file before.  Are there Terminal commands to do this, or do you just click the file to extract?

---

### Post by RomeReactor on 2009-07-30
You just extract it (you should get a file named **libflashplayer.so**), then you need to move it to wherever Konqueror looks for plugins; you could do that by pressing ALT+F2 and running:
```
kdesu dolphin
```
Then navigate to your home folder (opening Dolphin as root would most likely open Root's home folder), copy libflashplayer.so, and then navigating to the plugins folder where you'll paste the file. Note that you need to be particularly careful when opening the file manager as root since you can accidentally erase system files, but as long as you're careful there should be no problem.

However, it's been a few months since I last used KDE, so I don't remember where the plugins would be.

EDIT: From the screenshot of the plugins window in the first page, looks like Konqueror looks in **/usr/lib/mozilla/plugins**, which is where I install the plugin. You can paste the plugin there and restart Konqueror.

---

### Post by gshockxc on 2009-07-30
> **RomeReactor said:**
> You just extract it (you should get a file named **libflashplayer.so**), then you need to move it to wherever Konqueror looks for plugins; you could do that by pressing ALT+F2 and running:
```
kdesu dolphin
```
Then navigate to your home folder (opening Dolphin as root would most likely open Root's home folder), copy libflashplayer.so, and then navigating to the plugins folder where you'll paste the file. Note that you need to be particularly careful when opening the file manager as root since you can accidentally erase system files, but as long as you're careful there should be no problem.

However, it's been a few months since I last used KDE, so I don't remember where the plugins would be.

EDIT: From the screenshot of the plugins window in the first page, looks like Konqueror looks in **/usr/lib/mozilla/plugins**, which is where I install the plugin. You can paste the plugin there and restart Konqueror.


Fantastic.  That worked great.  I had to tweak some of the commands you gave me because they didn't work quite the same for me.  

```
kdesu dolphin
``` didn't give me root privilges.  It should have, but there was some kind of error.  "Could not start process Cannot talk to klauncher: The name org.kde.klauncher was not provided by any .service files"

No clue what that means.  So I did this instead in a terminal: 
```
gksudo cp libflashplayer.so /usr/lib/mozilla/plugins
```

I'm having trouble with Firefox doing the same thing, but I haven't figure out where Firefox looks for the plugins.  I think I came across it in the lib folder, but I'll go back and look.

Anyway, it's an improvement.  Thanks again.

---

### Post by RomeReactor on 2009-07-30
> **gshockxc said:**
> I'm having trouble with Firefox doing the same thing, but I haven't figure out where Firefox looks for the plugins.  I think I came across it in the lib folder, but I'll go back and look.

Make sure you only have *one* libflashplayer.so, otherwise you'll get conflicts:
```
sudo updatedb; locate libflashplayer.so
```
You should only let the one in **/usr/lib/mozilla/plugins**.
```
sudo aptitude purge flashplugin-nonfree flashplugin-installer nspluginwrapper gnash mozilla-plugin-gnash gnash-common
```

---

### Post by gshockxc on 2009-07-30
> **RomeReactor said:**
> Make sure you only have *one* libflashplayer.so, otherwise you'll get conflicts:
```
sudo updatedb; locate libflashplayer.so
```
You should only let the one in **/usr/lib/mozilla/plugins**.
```
sudo aptitude purge flashplugin-nonfree flashplugin-installer nspluginwrapper gnash mozilla-plugin-gnash gnash-common
```

OK, did that, and it appears to have worked.  I observed all the other libflashplayer.so files being removed from certain directories.  It showed up in several places, but there were only two places that I installed the updated version: /usr/lib/mozilla/plugins, and /usr/lib/firefox/plugins.  I guess at this, but I didn't notice any issues.  Still, I followed your suggestion and removed all the other files.

Now, Konqueror seems to be having issues.  Not sure if this has something to do with the files removed.

---

### Post by RomeReactor on 2009-07-30
Can you be more specific with the issues in Konqueror? Are they Flash related? Remember, you should leave only one libflashplayer.so in the system, preferrably in /usr/lib/mozilla/plugins. Also, it may be that Konqueror needs nspluginwrapper, so you could try installing it again:
```
sudo aptitude install nspluginwrapper
```

---

### Post by gshockxc on 2009-07-30
OK, here's something that's different between the two.  I'm going to [CNBC]("http://www.cnbc.com"), and clicking on the LIVE NOW video link in the middle of the page, at the top, right under "Top News and Analysis."  The video plays in Firefox, but not in Konqueror.  Any thoughts?

Here's a screenshot of Konqueror (left) vs. Firefox (right), and neither one of them is displaying the page correctly.


[IMG]http://i33.photobucket.com/albums/d89/kristanxc/KonquerorvsFirefox.png[/IMG]

---

### Post by RomeReactor on 2009-07-30
The video from CNBC is not Flash, so the problem is likely related to the gstreamer/totem/vlc video plugins. You could try installing kmplayer-konq-plugins:
```
sudo aptitude install kmplayer-konq-plugins
```
Does konqueror still report Flash as an available plugin? By the way, the suzukiauto page is really flash-heavy; it almost brought my Firefox to it's knees :/

---

### Post by gshockxc on 2009-07-31
> **RomeReactor said:**
> The video from CNBC is not Flash, so the problem is likely related to the gstreamer/totem/vlc video plugins. You could try installing kmplayer-konq-plugins:
```
sudo aptitude install kmplayer-konq-plugins
```
Does konqueror still report Flash as an available plugin? By the way, the suzukiauto page is really flash-heavy; it almost brought my Firefox to it's knees :/

Here's what it said in the terminal window.
```
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

I'm not sure if I understand what Konqueror is using for plugins, but if I'm reading this list right, Flash is available.

[IMG]http://i33.photobucket.com/albums/d89/kristanxc/KonquerorPlugins.png[/IMG]

The mozilla/plugins folders contain mplayer plugins, not Kmplayer.  Are they the same thing?

EDIT: in the screenshot I posted, you see a folder in the list: /us/lib/firefox/plugings.  there's a typo, it should be /usr/lib/... but I removed the list anyway.  I was just playing to see if I cold get it to work.

EDIT II: on the upside, Konqueror is running faster now that I removed that the /firefox/plugin folder.  Coincidence?

---

### Post by RomeReactor on 2009-07-31
I installed Konqueror to see if it would give me trouble with Flash, and it played YouTube videos properly--even when I only left /usr/lib/mozilla/plugins as the plugin location. However, the problems started as soon as I tried playing *any other kind of video*, such as most videos in apple.com/trailers. I even installed kmplayer-konq-plugins, and it refused to play anything except Flash, even after I restored the defaults for the plugins. I've been able to watch every video in Firefox, with only Flash and the Totem plugin installed, but that's neither here nor there.

So, don't know what else to suggest at the moment. Maybe someone more experienced with videos in Konqueror can chime in.

---

