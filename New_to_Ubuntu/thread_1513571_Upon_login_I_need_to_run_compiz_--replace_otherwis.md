---
title: "Upon login I need to run compiz --replace otherwise compiz doesn't start on its own."
date: 2010-06-19
forum: New to Ubuntu
---

### Post by sdlynx on 2010-06-19
Title kind of says it all.  Basically everytime I log in compiz never starts and I have to do a compiz --replace.  Is there a way to get compiz to start on its own?

I didn't have this problem before I reinstalled 10.04.  I'd rather not just add compiz --replace to startup applications because I never had to before and I'm sure there's a more correct way of solving this.

Also, I have run Fusion Icon and Reload Window Manager has the same effect.  I checked everything and it looks fine (aka compiz is set for where it needs to be set).

---

### Post by lkjoel on 2010-06-19
Ok, type this in a terminal window (applications->accessories->terminal):
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install compiz python-compizconfig compizconfig-settings-manager compiz-fusion-bcop compiz-plugins compiz-dev compiz-gnome libdecoration0-dev compiz-core libemeraldengine0 emerald libdecoration0 compiz-fusion-plugins-main compiz-fusion-plugins-extra fusion-icon compizconfig-backend-gconf compizconfig-backend-kconfig gedit gedit-common
```Then type this
```
gedit
```That should open a new window.
In it, type this
```
#!/bin/bash
compiz --replace
```Save it as compizrun, then close the window.
Type this in the terminal window
```
chmod +x compizrun
sudo cp compizrun /etc/init.d/compizrun
```That should fix it.

---

### Post by sdlynx on 2010-06-20
lol that's basically doing the same thing as putting it in startup applications is it not?

---

### Post by yossell on 2010-06-20
This might work for you:

run gconf-editor from a terminal

navigate on the left hand window to desktop - gnome - session - required_components

select required_components.

On the right hand pane, windowmanager's value should be your default window manager -typically metacity

double click windowmanager and in the value box type compiz. 

Then log out and log back in again - and that should be your default. 


There used to be a save sessions key somewhere, which is even easier and better...but I can't find it for some reason.

---

### Post by lkjoel on 2010-06-21
Yeah it is sdlynx.

But I think that if you are using GNOME, you can enable desktop effects, which is compiz.

---

### Post by purecharger on 2010-06-24
I reported a bug for this issue:

[https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/597765](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/597765)

---

### Post by fattyz on 2010-06-25
I got it all working finally.  All the effects, the caps the distorted cube, the animation, almost everything.  I will say it's buggy as hell, reboots, lockups and even reinstalled a couple times.  But on this old dell laptop (inspiron 600m) that someone gave me, that couldn't even run xp (not worth waiting for it) it's nothing short of a miracle.  I do have to reset the options a lot after a restart.

It takes a lot to figure out, and you have to get used to checking dates on posts, i ended up reading a lot of stuff from 06, and i'm running 10.04.  But again, it'll save you having to buy a new computer, if you're enough of a geek to tweak it.

I can't believe the effects on what must be a tiny little graphics card! 

FattyZ

---

### Post by realzippy on 2010-06-25
BTW, *compiz --replace* in autostart is needed to run FSAA with NVIDIA also,so you can live with this "bug".
No more steps on the cube!

---

### Post by fattyz on 2010-06-25
Another tip, if I try to enable max effects while compiz is working (if I go to the menu system/preferences/appearance/visual effects) and check anything, it blows compiz out and I have to cold boot and reset a bunch of stuff like rotate cube and my cairo dock w/openGL (different app) vanishes.

So even though most tutorials tell you to set it to max, if you get compiz working and nothing is checked in the menu, leave it like that.

FattyZ

---

### Post by lkjoel on 2010-06-27
Do you want to mark it as solved?
Thread Tools->Mark this thread as solved

---

### Post by xyepblra on 2010-06-27
Guys, I'm not sure if my problem hasn't been solved already in one of the posts above, it's just a different wording I apply to discribing it in my case. I have my compiz installed and configured my own way and I like it a lot, but every time I start up my notebook I have to check the "Custom visual effects" option again and it works remarkably well untill I turn my notebook on the next time. Should I put compiz on autostart?
**yossell**, do I have to run gconf-editor as root? I'm asking this because I have different values for windowmanager settings for root and for myself (namely, gnome-wm for root and compiz for myself).

---

### Post by lkjoel on 2010-06-28
It doesn't save your setting?
I think something is wrong with your config file.

---

### Post by xyepblra on 2010-06-28
> **lkjoel said:**
> It doesn't save your setting?
I think something is wrong with your config file.
Yes, it surely is something wrong with my settings, and maybe it is the config file problem, but can somebody tell me what exactly? I merely am a newby.

---

### Post by lkjoel on 2010-06-29
Maybe you should remove the file, or type in a Terminal window
```
[sudo?] chmod +w yourfile.yourextention
```

---

### Post by xyepblra on 2010-06-29
> **lkjoel said:**
> Maybe you should remove the file, or type in a Terminal window
```
[sudo?] chmod +w yourfile.yourextention
```
**lkjoel**, do you mean ~/.config/compiz/compizconfig/config?
Here is what it says:
```
[gnome_session]
profile = 
plugin_list_autosort = true

```Are there any values or parameters missing?
Can you show your file?

---

### Post by xyepblra on 2010-06-29
> **lkjoel said:**
> Maybe you should remove the file, or type in a Terminal window
```
[sudo?] chmod +w yourfile.yourextention
```
Nope, did not help a thing.

---

### Post by lidex on 2010-06-29
What do you have here:
```
cat /etc/compizconfig/config
```

---

### Post by xyepblra on 2010-06-29
> **lidex said:**
> What do you have here:
```
cat /etc/compizconfig/config
```
Here it is:
```
[general]
integration = true
backend = ini

[gnome_session]
integration = true
backend = gconf

[kde_session]
integration = true
backend = kconfig
```

---

### Post by lidex on 2010-06-29
Yeah, same here. Try this. Go to compizconfig>effects>window decoration. Do you have this in 'Command' field:
```
/usr/bin/compiz-decorator
```
If not add it.

---

### Post by xyepblra on 2010-06-29
> **lidex said:**
> Yeah, same here. Try this. Go to compizconfig>effects>window decoration. Do you have this in 'Command' field:
```
/usr/bin/compiz-decorator
```
If not add it.
I do have it. I have had it before I quit the session I manually started my custom effects in, and I have had it after I started a new session with BEFORE I enabled custom effects manually again.

---

### Post by tekkidd on 2010-06-29
goto System>Prefrences>Startup Applications

in their add an entry called Compiz and for the command enter 

```
compiz --replace
```

---

### Post by lidex on 2010-06-30
This may help:
[http://www.jejik.com/articles/2008/10/how_to_properly_start_compiz_in_gnome/]("http://www.jejik.com/articles/2008/10/how_to_properly_start_compiz_in_gnome/")

---

