---
title: "fluxbox transparency not working at all"
date: 2010-07-09
forum: New to Ubuntu
---

### Post by lolzwut on 2010-07-09
I am trying to set my fluxbox transparency but it is not working as far as I can see. I put it down to under 150 too. I also read the Q&A/FAQ from fluxbox and everything they said checked out:




[LIST=1]
[*] You must be running a Fluxbox version 0.9.2 or newer. 0.1.x does not contain transparency support.
[*] Fluxbox must be restarted for changes in the alpha value to take effect (just choose restart in the menu).
[*] You need to have the XRender extension enabled in X, and compiled into fluxbox. Running **fluxbox -i** and **xdpyinfo | grep RENDER** should both say "RENDER".
[*] You must have set the background with an XRender-compatible tool. [fbsetbg]("http://www.xs4all.nl/%7Ehanb/software/fluxbox/fbsetbg.html") comes with fluxbox and tries to make this easy for you, try it (the web page also has list of transparency supporting background tools). Run fbsetbg -i to see if it can find a suitable tool.
[/LIST]

the only one I'm not sure of is the last one. I set it with fbsetbg -f /home/user/.fluxbox/backgrounds/examplepicture.jpg

does anyone has any idea whats wrong?

---

### Post by ov3rcl0ck on 2010-07-09
If you want composition, like transparency on terminal windows and all to work in Fluxbox, Openbox, Blackbox, and some others you'll need xcompmgr, make sure you have it with this command.
```

sudo apt-get install xcompmgr

```
Then for basic composition just use
```

xcompmgr

```
put that command in a startup script otherwise you'll need to keep terminal open for it to run otherwise you can hit "ctrl+z" then enter the command "bg" to send it to background. But if you don't put it in a startup script you'll need to run it evertime you boot up.

Also you'll need your graphics drivers installed properly, and they need to support composition, or it needs to be enabled in your xorg.conf

---

### Post by steveneddy on 2010-07-09
Flux is redsquirrel's domain - and yabbadabbadont also - but I think ov3rcl0ck is right in the fact that you need to use xcompmgr - but I think the settings are in .fluxbon/startup

look here:

[http://linux.byexamples.com/archives/277/true-transparent-eye-candy-on-fluxbox/](http://linux.byexamples.com/archives/277/true-transparent-eye-candy-on-fluxbox/)

---

### Post by lolzwut on 2010-07-09
> **ov3rcl0ck said:**
> If you want composition, like transparency on terminal windows and all to work in Fluxbox, Openbox, Blackbox, and some others you'll need xcompmgr, make sure you have it with this command.
```

sudo apt-get install xcompmgr

```Then for basic composition just use
```

xcompmgr

```put that command in a startup script otherwise you'll need to keep terminal open for it to run otherwise you can hit "ctrl+z" then enter the command "bg" to send it to background. But if you don't put it in a startup script you'll need to run it evertime you boot up.

Also you'll need your graphics drivers installed properly, and they need to support composition, or it needs to be enabled in your xorg.conf



I did what you said and everything disappeared and started flashing it was almost impossible to see anything. I barely managed to kill the process. Seeing a graphics card problem? Or is there something besides that?

---

### Post by urukrama on 2010-07-10
If you have difficulties running xcompmgr, there might be a graphic cards problem. How old is your graphics card?

Xcompmgr, as far as I remembered does not give you true transparency, though. I just checked it and (unless I am doing something wrong) confirmed that. For true transparency you'll need transset. If you need help setting xcompmgr and transset up, have a look at [this]("http://urukrama.wordpress.com/openbox-guide/#xcompmgr") (it is about Openbox, but works the same in Fluxbox).

The native transparency Fluxbox offers is not true transparency. If you open your transparent menu or window over another window, you will see the desktop background below your menu or client, not the other window.

---

