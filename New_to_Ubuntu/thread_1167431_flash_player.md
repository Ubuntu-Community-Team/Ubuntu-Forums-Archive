---
title: "flash player"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by Ninfowarrior on 2009-05-22
So I am relatively new to ubuntu and I switched from Windows. I used to have ubuntu, but there was this one problem that made me want to switch back, every time I install flash player it does not show up or work. Yes, I am downloading the .deb version for 8.04 (which is the version I have) and I have tried the linux generics that play certain files but not mp3s. I was wondering what the problem could be, and if there was anything I could do about it. If this is a re-post, please direct me to the post so I can finally watch some videos and listen to music without the dreadful lag.

---

### Post by taurus on 2009-05-22
If you want to play mp3's, install the ubuntu-restricted-extras (for Gnome) package.

---

### Post by raymondh on 2009-05-22
You can use synaptic or the terminal to install flash.  Synaptic is a good package manager.  Just search for Flash and have a go. In terminal

```
sudo apt-get install flashplugin-nonfree
```

While you're there, also install the codecs to run those videos :)

```
sudo apt-get install ubuntu-restricted-extras
```

Regards,

---

### Post by raymondh on 2009-05-22
forgot the link for the restricted extras

[https://help.ubuntu.com/community/RestrictedFormats/](https://help.ubuntu.com/community/RestrictedFormats/)

and flash ...

[http://www.psychocats.net/ubuntu/flashubuntu](http://www.psychocats.net/ubuntu/flashubuntu)

Regards,

---

### Post by t0p on 2009-05-22
You won't need to install flash separately if you install the package **ubuntu-restricted-extras**.  If that's what you want.  Type into the terminal the command

```
sudo apt-get install ubuntu-restricted-extras
```

and the package manager will install the proprietary codecs to play mp3s and stuff, as well as the flash plugin.

---

### Post by Ninfowarrior on 2009-05-22
> **t0p said:**
> You won't need to install flash separately if you install the package **ubuntu-restricted-extras**.  If that's what you want.  Type into the terminal the command

```
sudo apt-get install ubuntu-restricted-extras
```and the package manager will install the proprietary codecs to play mp3s and stuff, as well as the flash plugin. 

So I entered that command in my terminal, and after a series of "y's" and "ok's" it said id something and it came up with my username thing that it does when you're first typing something in (i.e. john@ john-desktop:~$) then it lets you enter something in. I tried playing several videos and they all said i needed the flash update.

---

### Post by HuckleSmothered on 2009-05-23
Test your flash here:
[http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/)
Let us know the results.

Can you share one of the links you are trying to get to (youtube maybe)?

After you installed the ubuntu-restricted-extras did you close and reopen Firefox? If not, do so.

If that still doesn't work try the other suggestion above.
Close Firefox first, then open a Terminal and type the following;
sudo apt-get install flashplugin-nonfree
Then open Firefox and try again.

---

