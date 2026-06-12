---
title: "I want to listen to streaming radio."
date: 2009-01-22
forum: New to Ubuntu
---

### Post by Captain Legless on 2009-01-22
I enjoy listening to the radio online whilst I'm working on the computer.

I have just installed Ubuntu and am trying to get things running as they were in WinXP.

I've tried listening to the radio station at [http://www.fiveaa.com.au/dmgcustom/FiveaaNV.asx]("http://www.fiveaa.com.au/dmgcustom/FiveaaNV.asx") using *Firefox* but I get no sound, just the logo for the media player.

I've been given one suggestion of trying "*Medibuntu*" but having looked at the web site for it, it looks a bit scary. Having come from Windows I'm only used to double clicking on things rather than messing with codes and scripts.

Does anybody have a very simple basic, (like double click), solution for this problem? :???:

---

### Post by thomasyen on 2009-01-22
Your site appears to be using WMA for streaming audio. Because it's a proprietary format, I'm not sure if there are any non-Medibuntu media players that can play this format. You could try installing XMMS (not in the repository), Audacious, Amarok, etc. If all of them fail, then try using Medibuntu. It's actually fairly easy, because all that's needed is for you to copy and paste the code into a terminal.

---

### Post by Paqman on 2009-01-22
> **Captain Legless said:**
> 
I've been given one suggestion of trying "*Medibuntu*" but having looked at the web site for it, it looks a bit scary.

It's actually not too bad. If you're using Intrepid simply open a terminal (Applications > Accesories > Terminal) and copy/paste in this:
```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

then this:
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by nothingspecial on 2009-01-22
[[COLOR="Magenta"]This guide[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766683") will help you install all the codecs you need.

---

### Post by drs305 on 2009-01-22
Captain Legless,

I can listen to it with a combination of the MediaPlayerConnectivity plugin and vlc plugin. Works great.

I won't offer this as the best solution as I've used this 'workaround' combination for years and you can probably get it to play more directly. Just wanted you to know if you can't get it to work through the normal methods this option is available.

---

### Post by Captain Legless on 2009-01-22
Thanks guys for the prompt and informative replies. I'll report back if/when I master it!!:)

---

### Post by jfr1tz on 2009-01-22
That's quite an extensive guide, simply installing the ubuntu-restricted-extras package installed the missing codecs for me (intrepid)

---

### Post by philinux on 2009-01-22
Does not work with the Firefox totem plugin, but, I pasted the link into VLC and it works.

---

### Post by nothingspecial on 2009-01-22
> **jfr1tz said:**
> That's quite an extensive guide, simply installing the ubuntu-restricted-extras package installed the missing codecs for me (intrepid)

That guide is the first place I go after a clean install.

---

### Post by Ben Page on 2009-01-22
sudo apt-get install streamtunner

it will install streamtunner witch has access to shout cast and many others radio sites, and Audacious for listening to it all.

or maybe streamtuNer (only one N)

---

### Post by Captain Legless on 2009-01-22
Woa..........got it at last!!!

Thanks guys for all the ideas and help.:D

I'll get the hang of this lot eventually.

Now to start messing with WINE.:rolleyes:

I'll be back on the forums asking for more help I'm sure.

Thanks again!

---

