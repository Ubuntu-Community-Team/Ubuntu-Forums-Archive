---
title: "Is window size default changeable?"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by jwaclawsky on 2009-04-06
Whenever I open a program in Ubuntu 8.04 the window size fills the entire screen instead of a smaller window (I have a 24" monitor). Is there some setting I can change so when I open a window it opens in a smaller size other than full screen? ...or remembers its previous size from the last time it was opened?   Thanks

---

### Post by drs305 on 2009-04-06
Often the default for window size is to return to the same size as it was when closed unless something else overrides it. 

If you use compiz there is a setting for "windows rules" which enables you to set the opening size.

Install the compiz settings manager:
```
sudo apt-get install compizconfig-settings-manager
ccsm  # opens the configuration manager
```
Or open it with: System, Preferences, CompizConfig Settings Manager: Windows Management, Windows Placement, Size Rules tab.

I searched through gconf-editor but did not find a setting which defaults all programs to open maximized. I used the search term "maximized".

---

### Post by jwaclawsky on 2009-04-06
ok, I installed compizconfig using the terminal window. Installed fine but when I typed in sscm I got:

GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

Anyone know what this means?  Thanks

---

### Post by jwaclawsky on 2009-04-06
Rebooted the system and found CompizConfig Setting Manager under system > preferences > advanced desktop effect settings. Window Rules was checked with size rules of 5000  3000. But when I open a new window it still goes to full screen. The same problem as before. Help please, anyone. Thanks

---

### Post by drs305 on 2009-04-06
> **jwaclawsky said:**
> GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

Anyone know what this means?  Thanks

There is an invalid input in one of the compiz settings. Open up gconf-editor and return it to the default or "unset" it:
```

gconf-editor /apps/compiz/plugins/scale/allscreens/options/initiate_edge

```
Right click on the value and change it. On my machine, the setting is "Disabled". You could also try the "Unset" option - on my machine it returns a blank field.

It might be the reason things weren't working earlier. You might try opening and closing some apps to see if they open in the correct manner before messing with other compiz settings in the manner I offered in the earlier post.

---

### Post by LowSky on 2009-04-06
you should have typed ccsm... just kidding

you could open file manager (nautilus) and search to that folder and remove whatever file is causing the issue
/apps/compiz/plugins/scale/allscreens/options/initiate_edge

---

### Post by jwaclawsky on 2009-04-06
ok, I unset key. It had [] as the value. now there is nothing there and I can run "ccsm" from the terminal without any errors. Now I am back to my original problem. I will reboot before I go any further   ...just in case.

---

### Post by jwaclawsky on 2009-04-06
Ok, I rebooted and I am back to my original problem that whenever I open a program in Ubuntu 8.04 the window size fills the entire screen instead of a smaller window (I have a 24" monitor). Is there some setting I can change so when I open a window it the window size is the same size as it was when closed?  

"ccsm" works without error from the command line in the terminal window. I also tried checking Window Rules with size rules of 5000 3000. But when I open a new window it still goes to full screen. The same problem as before. Anyone have any other ideas. Thanks

---

### Post by drs305 on 2009-04-06
I don't know what resolution you are running and granted you have a 24" screen, but try something much smaller, say 1000 800 just to see if it will work. 

Other than that, I hope someone will offer a working solution for you.

---

### Post by jwaclawsky on 2009-04-06
screen resolution doesn't seem to make any difference. It's a pain having to resize every time I open a window. BTW, I am using a netbook to drive the 24"monitor. It works well except for the full screen windows on start up. Could that I have two displays going (one on the netbook) have anything to do with it?

---

### Post by tajmahall on 2009-04-26
Sounds like the same problem I was having. Under gconf-editor, I managed to find a folder

/apps/maximus

which has an option to toggle whether new windows are automatically maximized (no_maximize). (I'm just using metacity.)

Hope this solves it for you too.

---

### Post by jwaclawsky on 2009-04-26
I went to the /maximus folder as you suggested (previous post). There was no option that you suggested. The folder just has 3 entries:

binding
exclude_class
undecorate

Maybe I need to add something to one of these entries or specify a new entry? I still have the same annoying problem of windows open as full screen on my 24" monitor. You can see a new window beginning to open at its original smaller size and then something takes over and maximizes it to full screen. If anyone has any suggestions I would be very grateful. Thanks

---

