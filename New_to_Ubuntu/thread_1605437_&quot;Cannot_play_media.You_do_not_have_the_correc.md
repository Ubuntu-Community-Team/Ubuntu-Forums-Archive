---
title: "&quot;Cannot play media.You do not have the correct version of the flash&quot;"
date: 2010-10-25
forum: New to Ubuntu
---

### Post by Roger Allott on 2010-10-25
Having just upgraded to lucid, I'm now getting this message on the BBC website whenever there's a video to watch.

```
Cannot play media.You do not have the correct version of the flash
```

There seem to be two variants of Flash that I can install. One is adobe-flashplugin and the other is flashplugin-installer, both of which conflict with each other. At the moment, I've got the latter one installed.

However, when I remove one and install the other, I still cannot play Flash content. Flash seems to not work whichever of these packages I have installed.

Anyone got any ideas on how I rectify this situation?

---

### Post by Verbeck on 2010-10-25
try downloading from adobe
[http://get.adobe.com/flashplayer/completion/?installer=Flash_Player_10.1_for_Linux_(.deb]("http://get.adobe.com/flashplayer/completion/?installer=Flash_Player_10.1_for_Linux_%28.deb"))

OR install adobe-flashplugin from canonical partners


also: is shockwave flash listed in firefox? [add-ons > plugins tab]

---

### Post by leeper69 on 2010-10-25
I had a simular problem. have you tried using Synaptic to download flashplugins? just start Synaptic and click on the search button at the top and type in flash then scroll down till you find the flashplugin-installer and flashplugin-nonfree and mark them both for installation then click on apply changes at the top of the screen.

---

### Post by philinux on 2010-10-25
For anyone with flash problems like this instal this addon.

[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

---

### Post by Roger Allott on 2010-10-25
> **Verbeck said:**
> try downloading from adobe
[http://get.adobe.com/flashplayer/completion/?installer=Flash_Player_10.1_for_Linux_(.deb]("http://get.adobe.com/flashplayer/completion/?installer=Flash_Player_10.1_for_Linux_%28.deb"))

Yes, that was one of the first things I tried, but GDebi refused to install it because of conflicts with the other Flash variant.

> **Verbeck said:**
> OR install adobe-flashplugin from canonical partners
Like who? And why would their version of adobe-flashplugin be any different to the one from the standard repositories?

> **Verbeck said:**
> also: is shockwave flash listed in firefox? [add-ons > plugins tab]
I've no idea. Firefox crashes every time I've tried to start it since 'upgrading' to lucid.

---

### Post by philinux on 2010-10-25
> **Roger Allott said:**
> Yes, that was one of the first things I tried, but GDebi refused to install it because of conflicts with the other Flash variant.


Like who? And why would their version of adobe-flashplugin be any different to the one from the standard repositories?


I've no idea. Firefox crashes every time I've tried to start it since 'upgrading' to lucid.

ok so remove all flash plugins and start from scratch.

---

### Post by bigsmitty64 on 2010-10-25
> **philinux said:**
> For anyone with flash problems like this instal this addon.

[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)
+1 Always works for me :)

---

### Post by Roger Allott on 2010-10-25
> **philinux said:**
> ok so remove all flash plugins and start from scratch.

Isn't that what I've been trying to do for the past day or so??

And when you say "start from scratch", which package should be installed? And which one(s) shouldn't?

And why is Firefox just crashing as soon as I try to start it?

---

### Post by Roger Allott on 2010-10-25
> **philinux said:**
> For anyone with flash problems like this instal this addon.

[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

Thanks, but it's not very helpful when Firefox is refusing to start.

---

### Post by bigsmitty64 on 2010-10-25
I would  "save/export" my bookmarks and reinstall firefox through synaptic, then start from scratch. Using the link provided by philinux

[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

---

### Post by Roger Allott on 2010-10-25
> **bigsmitty64 said:**
> I would  "save/export" my bookmarks and reinstall firefox through synaptic, then start from scratch. Using the link provided by philinux

[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

How does one "save/export" bookmarks, passwords, etc. when Firefox will not open?

---

### Post by Sir Jasper on 2010-10-25
Hi,

Two, possibly useless, thoughts:

1) Firefox has its own safe mode so that may start from your terminal.

2) If you back up your Firefox / .mozilla directory from Home and then rename it - you may not win, but you probably can't lose by then reinstalling Firefox.

My regards

PS if you do not already have a clone/backup of everything important that may be worthy of future consideration?

---

### Post by uRock on 2010-10-25
> **Roger Allott said:**
> How does one "save/export" bookmarks, passwords, etc. when Firefox will not open?
Back up the .mozilla folders in your /home folder.

---

### Post by ivarn on 2010-10-25
I can't see how deleting the .mozilla folder will help, since this is a flash problem and not a firefox, cache/history, nor a plugin problem (unless other plugins are effecting the way flash works on your browser).
Since you can't remove the flash plugins, I assume that your firefox is still running.
Try to force kill the process and remove all flash plugins you have installed.
Then, install adobe's flash plugin and their plugin for mozilla @ [https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)
The reason why you can't install the mozilla flash plugin is because you don't use adobe's plugin you'll find in synaptic. Use that flash plugin ONLY.
Don't use the gnash plugin.

---

### Post by philinux on 2010-10-25
> **Roger Allott said:**
> How does one "save/export" bookmarks, passwords, etc. when Firefox will not open?

Open a terminal.

```
firefox -safe-mode
```

See if an addon is causing a problem.

---

### Post by Roger Allott on 2010-10-25
I've backed up my .mozilla folder, removed Firefox using Synaptic (complete removal), and then installed Firefox from Synaptic.

The result of this is that I'm getting exactly the same crash behaviour that I was getting previously.

---

### Post by Roger Allott on 2010-10-25
> **philinux said:**
> Open a terminal.

```
firefox -safe-mode
```

See if an addon is causing a problem.

When trying to open in safe mode, I'm getting exactly the same crash behaviour as I was getting previously.

However, in Terminal I'm getting this message:
```
Attempting to load the system libmoon
```

I've no idea what relevance that might have.

---

### Post by ivarn on 2010-10-25
> **Roger Allott said:**
> I've backed up my .mozilla folder, removed Firefox using Synaptic (complete removal), and then installed Firefox from Synaptic.

The result of this is that I'm getting exactly the same crash behaviour that I was getting previously.

As I told you, this is not a firefox issue. I can tell cuz I use iPlayer.
Here's my setup, adobe flash plugin (Only - Not the Gnash plugin)
And the adobe flash plugin for mozilla that's been posted here 10 times already :)
Now, try this and go to [http://www.bbc.co.uk/radio/](http://www.bbc.co.uk/radio/) and see how it works.
Works like a charm here.

---

### Post by uRock on 2010-10-25
Can you run firefox in a terminal and post the error message here.

---

### Post by philinux on 2010-10-25
I would temporarily uninstall libmoon. It's a silverlight version for ubuntu.

```
sudo apt-get remove libmoon
```

---

### Post by Roger Allott on 2010-10-25
> **philinux said:**
> I would temporarily uninstall libmoon. It's a silverlight version for ubuntu.

```
sudo apt-get remove libmoon
```

Brilliant!

Getting rid of that enabled Firefox to start, and with Firefox started I could install the magic add-on that you recommended.

And that has done the trick. Flash files now viewable in Firefox as well as in Chromium.

Oddly enough though, Novell Moonlight is still showing as being an installed Add-On in Firefox.

Many thanks for your help on this.

---

### Post by philinux on 2010-10-25
> **Roger Allott said:**
> Brilliant!

Getting rid of that enabled Firefox to start, and with Firefox started I could install the magic add-on that you recommended.

And that has done the trick. Flash files now viewable in Firefox as well as in Chromium.

Oddly enough though, Novell Moonlight is still showing as being an installed Add-On in Firefox.

Many thanks for your help on this.

Excellent.

I used moonlight but I got it here. [http://go-mono.com/moonlight/prerelease.aspx](http://go-mono.com/moonlight/prerelease.aspx)

On sky player it crashes FF.

---

