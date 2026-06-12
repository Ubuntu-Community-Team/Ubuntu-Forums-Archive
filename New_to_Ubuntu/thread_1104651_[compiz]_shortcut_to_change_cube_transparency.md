---
title: "[compiz] shortcut to change cube transparency?"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by aliksy on 2009-03-23
Is there a way to make it so I can change the cube's transparency with a key/mouse shortcut?  Apparently my computer doesn't like playing youtube where it's showing on all 4 faces at once, but generally speaking i like being able to see all my  desktops at once.

ubuntu 8.10 intrepid ibex..  I am new at this and don't know what else you would need to know.

---

### Post by drs305 on 2009-03-23
First, welcome to the ubuntu forums!

As you haven't gotten any responses, and with the preface that I don't use the cube, this may work. If you have the time and inclination to play around with it:

My instructions below are for a panel shortcut, but you could easily make them a keyboard shortcut with the same commands via gconf's metacity section. I would make the shortcuts and see if they work first, then commit them to keyboard shortcuts.

In gconf-editor there are settings for the opacity of the cube - one setting for when it is rotating and the other for when it is static.
These are found in:
/apps/compizconfig/profiles/Default/plugins/cube/screen0/options
Open gconf-editor:
```

gconf-editor /apps/compizconfig/profiles/Default/plugins/cube/screen0/options

```
Note your current settings (0-100) for your active_opacity and inactive_opacity.

Now make two shortcuts. If you need help on how to make a shortcut you can do a search of these forums or post back (I'll be gone but someone can help you). I would assume you need to change the inactive_opacity settings.

In one, replace **XX** with your current inactive_opacity value:
```

gconftool-2 --type string --set /apps/compizconfig/profiles/Default/plugins/cube/screen0/options/inactive_opacity 'XX'

```

In a second shortcut:
```

gconftool-2 --type string --set /apps/compizconfig/profiles/Default/plugins/cube/screen0/options/inactive_opacity '100'

```

You could put the two shortcuts on your panel and click to switch  back and forth. 

I am fairly certain the values should be for inactive_opacity and the value 100, but if it doesn't work you could play with a different value and the active_transparency setting.

Best of luck.

---

### Post by aliksy on 2009-03-24
Hm. That's not the path on my computer but I think I found what you're talking about.  
/apps/compiz/plugins/cube/screen0/options/inactive_opacity

Ok.. if I change it in gconf-editor, it works.  If I change it in the compiz configeration thing, it works and I can see the number change.  But when I try to make a shortcut to do it (launcher on the desktop), there is no change even though the number in gconf-editor will show 0 afterwards.  I have done something wrong?

(Thank you for the reply, too.)

---

### Post by drs305 on 2009-03-24
I have the compiz configuration settings manager installed, which is probably why the paths are slightly different. By the way, ccsm is a great tool, you can install it with:
```
sudo apt-get install compizconfig-settings-manager
```
You start it with System, Preferences, CompizConfig Settings Manager or in terminal "ccsm".

The reason it may not work in the shortcut is that compiz has to be refreshed. One command that I use to do this is "compiz --replace" but that is overkill. Using this command normally works for me but every once in a while it freezes up my system. If you decide to use it you would follow the gconf command with "&&" so it runs the second command, and end it with "&" so the terminal is freed up. **There is probably a better command to refresh compiz and hopefully someone will provide it**.

*I would not try this until you can afford to reboot should the refresh command lock up your screen*:
```

gconftool-2 --type string --set /apps/compiz/plugins/cube/screen0/options/inactive_opacity '100' && compiz --replace &

```

If you install ccsm remember that you may need to replace the string you found with the gconf string I first presented.

---

