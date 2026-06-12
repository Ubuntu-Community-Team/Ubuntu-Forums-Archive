---
title: "Messed up Gnome!"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by NWSmart on 2008-12-10
While trying to improve speed I (foolishly) shut down various Gnome services us the Session Preferences Window.

Now my system is far from how it was or how I want it. Can't get the same number of desktops, and there are no minimise/maximise/close buttons on any windows (which are fixed to the upper tool bar!)

Can anyone point me in the right direction to get my system back to the 'norm'

Thanks in advance

---

### Post by donkyhotay on 2008-12-10
Are you able to restore the services you shut down previously?

---

### Post by NWSmart on 2008-12-10
No - not sure how to. I have however got some of it working again by going into Appearances and setting visual effects back to Extra

---

### Post by donkyhotay on 2008-12-10
In gnome go to system > administration > services, This will open a utility that allows you to customize what services do/don't start with gnome. I'm pretty certain this is what you used to disable the services as it's the easiest way to access enable/disable these from a completely GUI environment. Be careful what you shut down here as selecting the wrong thing will have unusual results. If in doubt turn on everything and if you want to disable a service disable each service one at a time and then test it to make certain there are no unintended consequences.

---

### Post by NWSmart on 2008-12-10
Hi donkyhotay,
Thanks for that. Nearly everything in that Services list is ticked and started (with a couple exceptions for Braille and the like that I definitely dont need).

Don't recognise any of the ones that I foolishly stopped earlier using the Sessions Preferences.

Things are better now but not quite the same. Still looking to see where to get the info to reload Sessions Preferences with what I had before

Jim

---

### Post by kansasnoob on 2008-12-10
I would run:

```
sudo apt-get install --reinstall ubuntu-desktop
```

That should bring you back to square #1 unless you've removed actual "Ubuntu system" stuff.

---

### Post by NWSmart on 2008-12-11
Hi Kansasnoob,

Thanks for that advice - I'll give it a go when I get home this evening.

---

### Post by NWSmart on 2008-12-11
Oh dear - must have messed up quite a bit. Doing the desktop reinstall has not really helped. At the moment the system boots into one appearance and I have to always change it back to one of the other themes and set the higher level of visual effects. For some reason the system does not seem to remember any of these changes once I shut down.

Another oddity is that I have lost the shut down option - I have to log out and then shut down from the splash screen!

Hope this makes some sense to someone out there. Really appreciate the help you guys give
Jim

---

### Post by cb34 on 2008-12-12
maybe after you set all the services how you want, and also maybe going into PREFERENCES->SESSIONS and setting things in there, go to the OPTIONS tab and click --remember currently running apps-- before you log out and in.

also.. besides the built in SERVICES in to the ubuntu menu. I use a tool from the repo called BootUp-Manager.. it is slightly more powerful in that it has many more options.
(click advanced at the bottom for all the options/settings)

be careful what u fiddle with though.. as was said before.. you can totally screw your system... even more than it is now..lol.. :P

cya.. hope this helps.

---

### Post by cb34 on 2008-12-12
there is also this tool in the repo.. very powerful tool.. so again.. be careful man..

sysvconfig

helped me quite a bit to fine tune my system. :)

peaz.

---

### Post by donkyhotay on 2008-12-12
Sounds like the services are still installed it just doesn't launch them when you start gnome. Try creating a new user account and logging into it. If everything is normal in the new user account then just migrate your files over and delete the messed up one, it'll probably be easier then trying to repair everything.

---

### Post by cb34 on 2008-12-12
about the SHUTDOWN button.. i also dont have one bcuz i use avant-window-navigator and i have to either click log-off, then from the login screen.. shutdown.
or i press ALT-F1 to bring up the old original ubuntu menu which does have the shutdown button there.

but anywayz.. what i found myself doing all the time now when i need to shutdown the computer...

in SETTINGS->PREFERENCES->Power Management i set it so i just press the power button on my pc, and a screen pops up asking me if i wanna shutdown or logoff.

its the best iMO.. you want to shutdown just hit the button on the computer.

works like a charm.. and im not sure if that power management tool is there with a default ubuntu install.. in the repo.. its something like gnome-power-manager.. or it mnay be installed, but not showing up on the memu.. for that.. you go into SETTINGS->PREFERNCES->MAIN MENU and make it viewable from there.

cya.

but there is an option to show or not show the shutdown button.. somewhere.. i just dont remember where.. got to find it in gconf-editor probably.

---

