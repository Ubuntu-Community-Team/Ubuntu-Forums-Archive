---
title: "Lost panel at top of screen"
date: 2010-11-04
forum: New to Ubuntu
---

### Post by Dan Lucier on 2010-11-04
I just got a Starling netbook from System76 yesterday. I was changing some visual settings and trying to figure out why the webcam wouldn't work, and I somehow lost the panel at the top of the screen. I cannot figure out why this happened or how to get it back. Does anyone have any ideas? This is my first foray into the netbook edition (10.04 by the way) and I'm still pretty new to Ubuntu in general.

I found[URL="http://ubuntuforums.org/showthread.php?t=790719&highlight=Lost+panel+top+screen"] a forum about this from two years but none of the advice helped. 

Thanks.

---

### Post by sanderd17 on 2010-11-04
the difference is that you are using the 10.04 netbook remix, not the normal gnome version. The netbook remex only has 1 panel I think (to save space).

I believe you tried a reboot. If you press ALT+F2, do you see a command input window? If not, you have disabled the gnome panel service. If you see it, the problem is somewhere else.

---

### Post by Dan Lucier on 2010-11-04
Thanks for the quick reply. Yes, I have rebooted several times. Alt+F2 does not do anything. How do I enable Gnome panel service?

---

### Post by sanderd17 on 2010-11-04
you still have the side bar do you? So can you access a terminal?

if you do, execute

```

gconf-editor

```

go to /desktop/gnome/session and look at the key "required_components_list", does it have "panel" as one of it values?

if not, add the value "panel" to it, just like windowmanager and filemanager should already be there as values.

---

### Post by Dan Lucier on 2010-11-04
Panel is listed along with windowmanager and filemanager. 

I was able to get the panel to reappear after entering:

killall gnome-panel

but it wouldn't stay after rebooting and I realized I have other problems with my windows. I have no minimize, maximize, or close buttons in my windows. In fact, they have no borders on the side or bottom either.

---

### Post by sanderd17 on 2010-11-04
you've been trying some visual effects? it looks like compiz took over some gnome things but you removed compiz from it and are left with nothing.

can you install compizConfig Settings Manager? open it and try to change some window settings.

I don't see how this can be related to the panels though, normally compiz doesn't take over the panels.

---

### Post by Dan Lucier on 2010-11-04
I have compizConfig Settings Manager, and yes, I did make some change there before. I thought that might be the source of my problem.

Which settings should I change? When you say Window settings, do you mean Window Management  or Effects? I just changed some of them and rebooted. No luck.

---

### Post by sanderd17 on 2010-11-04
maybe you can try to uninstall coompiz with its stettings:

```

sudo aptitude purge compiz

```

Then try a reboot or a re-login and see if you have your things back.

in any case, you can reinstall compiz with its settings manager. All settings will be erased with the purge command.

---

### Post by Dan Lucier on 2010-11-04
I tried the command and then rebooted. No luck.

Do I need to reinstall compiz at this point?

---

### Post by Dan Lucier on 2010-11-04
I'm thinking I should just reinstall Ubuntu. I just got the computer yesterday so it's not like I have much on it. Is there any reason I should not do this. I can get the System76 drivers right?

---

### Post by sanderd17 on 2010-11-06
If you're willing to reinstall ubuntu, I would go for that. maybe you can install the regular ubuntu (not the netbook edition), delete your panels and use a dock like AWN instead to save space.

If you want the netbook edition, I would suggest 10.04, 10.10 uses Unity which is not quite stable.

---

