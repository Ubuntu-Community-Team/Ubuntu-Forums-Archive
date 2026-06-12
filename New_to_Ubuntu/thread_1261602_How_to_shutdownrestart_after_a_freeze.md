---
title: "How to shutdown/restart after a freeze?"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by tahitiwibble on 2009-09-08
Please forgive me guys, I saw an excellent post on this subject a few months ago and didn't bookmark it unfortunately.

Sometimes, not too often, when I have a lot of windows open, my computer freezes, at least the program icons in the panel do anyway. I can usually close the programs and even save my work but neither of the 2 panels I ususally work with are operational any more. I can't even go to System>Shut Down any more.

Can I restart the program running the panels or something?
Is there at least a nicer way of doing it than hitting the reboot button on the box?
Is there something that I can do to help prevent this happening?

Many thanks for any help proffered.

---

### Post by nandemonai on 2009-09-08
> **tahitiwibble said:**
> Please forgive me guys, I saw an excellent post on this subject a few months ago and didn't bookmark it unfortunately.

Sometimes, not too often, when I have a lot of windows open, my computer freezes, at least the program icons in the panel do anyway. I can usually close the programs and even save my work but neither of the 2 panels I ususally work with are operational any more. I can't even go to System>Shut Down any more.

Can I restart the program running the panels or something?
Is there at least a nicer way of doing it than hitting the reboot button on the box?
Is there something that I can do to help prevent this happening?

Many thanks for any help proffered.

If it's not a complete freeze up you can use alt-F2 to bring up a run prompt.

From there you have a few options.

Restart panels - ```
killall gnome-panel
```
Restart X - ```
gksudo /etc/init.d/gdm restart
```
Restart machine - ```
gksudo reboot
```
Shutdown - ```
gksudo shutdown -h now
```

If you're unable to get a run prompt you can try switching to a TTY interface (text only).

Ctrl-Alt-F1
Then login and try: ```
sudo /etc/init.d/gdm restart
```

Note:

If it's just your panel that's freezing, it may be a particular applet you're running in the panel that's causing the freezes.

---

### Post by tahitiwibble on 2009-09-09
> **nandemonai said:**
> If it's not a complete freeze up you can use alt-F2 to bring up a run prompt.

Note:

If it's just your panel that's freezing, it may be a particular applet you're running in the panel that's causing the freezes.

Ok, that's magic nandemonai, thanks.

Although I hope I'll never need it any more :)

But, yes, it's rarely a total freeze. I wonder how I might track down an applet that may be causing it? It only happens with lots of programs running and lots of windows open.

Anyway, thanks again for the help. :)

---

