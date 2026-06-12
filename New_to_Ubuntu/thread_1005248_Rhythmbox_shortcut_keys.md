---
title: "Rhythmbox shortcut keys"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by Nazty_Nayt on 2008-12-08
Hey I was wondering if this is possible or not.  I want to know if there's a shortcut I can set up for my rhythmbox audio player.  I want to set it up so I can press something on my keyboard to skip a track when I'm not looking at the player.

For instance let's say I have the play open, and it's on shuffle.  I'm browsing the web, and a song comes on that I want to skip, but I don't want to close the browser, and switch over to the player to skip, and then go back.

Is this possible, if so could someone walk me through it?

---

### Post by abrussak on 2008-12-08
Check out the man page for rhythmbox-client...

```
man rhythmbox-client
```

I have mine set up through the hotkey section in ubuntu-tweak

---

### Post by Nazty_Nayt on 2008-12-08
Well I pulled it up, but I'm not sure how to exactly set this up.  It seems like all I can do is press enter and scroll down, I see next, and previous, but don't know how to set it up?

---

### Post by catchytune on 2008-12-08
> **Nazty_Nayt said:**
> 
For instance let's say I have the play open, and it's on shuffle.  I'm browsing the web, and a song comes on that I want to skip, but I don't want to close the browser, and switch over to the player to skip, and then go back.

For this purpose you could try out foxytunes [http://www.foxytunes.com/](http://www.foxytunes.com/) which is compatible with Rhythmbox too. You don't have to leave your browser then and you also can skip etc. using the multimedia keys of your keyboard.

A second option is right-clicking the Rhythmbox symbol in your tray, and you choose what you want to do in the pull-down menu.

---

### Post by claytronic on 2010-04-24
> **abrussak said:**
> Check out the man page for rhythmbox-client...

```
man rhythmbox-client
```

I have mine set up through the hotkey section in ubuntu-tweak

Thanks for the tip! Rhythmbox is much more useful with hotkeys. :guitar:

---

### Post by petko10 on 2010-10-24
Guys don't know how no one's seen it - just set your Preferences->Keyboard Shortcuts . Actually I get how no one's seen that , because I was looking for the same thing up until now but as it usually is with linux there is a smart solution .
Btw I set my play/next/previous/vol up/vol down on alt+C/V/X/D/F . Handiest placement I thought of .

---

### Post by rebs on 2011-02-01
rhythmbox-client seems like a good start, but it lacks an shuffle option. Also the gnome Keyboard Shortcuts does not have a build in solution for  shuffle.

So, does anybody have an idea how i could install a shuffle shortcut?

cheers rebs

---

### Post by rebs on 2011-02-02
i have found a way!

i wrote a little script:

```

#!/bin/sh

prestate=`gconftool -g /apps/rhythmbox/state/play_order`

if test $prestate = "linear"
then
`gconftool -s /apps/rhythmbox/state/play_order -t string shuffle`
else
`gconftool -s /apps/rhythmbox/state/play_order -t string linear`
fi

```

And then set a shortcut under 'Preferences->Keyboard Shortcuts' to the script.

cheers rebs

---

### Post by Hawkoon on 2011-02-19
> **rebs said:**
> i have found a way!

i wrote a little script:

```

#!/bin/sh

prestate=`gconftool -g /apps/rhythmbox/state/play_order`

if test $prestate = "linear"
then
`gconftool -s /apps/rhythmbox/state/play_order -t string shuffle`
else
`gconftool -s /apps/rhythmbox/state/play_order -t string linear`
fi

```And then set a shortcut under 'Preferences->Keyboard Shortcuts' to the script.

cheers rebs

This is great, rebs, I had forgotten about gconftool! I can add shuffle to my lirc remote now with this
```
begin
        prog = irexec
        button = KEY_SHUFFLE
        repeat = 0
        config = gconftool -s /apps/rhythmbox/state/play_order -t string shuffle
        config = gconftool -s /apps/rhythmbox/state/play_order -t string linear
end
```

Thanks!

---

