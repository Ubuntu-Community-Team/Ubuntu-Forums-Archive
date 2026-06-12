---
title: "compiz cube background"
date: 2010-06-28
forum: New to Ubuntu
---

### Post by cthom on 2010-06-28
i want to change the 3d cube background. i've looked at other posts concerning this, the problem is i don't have a 'skydome' option in my settings. the only image options are for top and bottom of the cube. i only installed lucid a few days ago and compiz just today, so i'm pretty sure everything is up to date. trivial but i need a solution :)

---

### Post by lkjoel on 2010-06-28
Just enable Skydome.
Then go to a Terminal (Applications->Accessories->Terminal) window and type
```
sudo apt-get update
sudo apt-get upgrade
```
That will keep everything up to date

---

### Post by cthom on 2010-06-28
i have no enable skydome option. there is no mention of it anywhere.

looking at compizconfig settings> Cube Caps.i have options for top/bottom colour, top/bottom image. nothing for background.

---

### Post by lkjoel on 2010-06-28
Type this
```
sudo apt-get install ccsm
ccsm
```

---

### Post by cthom on 2010-06-28
i've looked through it, but again no background option. :(

i've seen screenshots of the settings manager with skydome on it, so i'm wondering if i need another plug-in?

---

### Post by lkjoel on 2010-06-28
Sorry I forgot a package. Do this instead:
```
sudo apt-get install compizconfig-settings-manager compiz-fusion-plugins-main compiz-fusion-plugins-extra
```

---

### Post by cthom on 2010-06-28
i got all those earlier i'm afraid. i got almost everything i wanted to work going apart from 2 things, water and the cube background. i'm not too bothered about painting ripples lol :)

---

### Post by lkjoel on 2010-06-28
Is compiz installed correctly?

---

### Post by cthom on 2010-06-28
i think so. i see a lot of effects working nicely. everything compiz related in synaptic was installed apart from -bcop -dev-dbg and the kde variants.

---

### Post by Python Jedi on 2010-06-28
When you open up ccsm, go to Dektop Cube>Behavior.  There should be a line at the bottom with a plus by it that says "Skydome".  open that up and there should be a check box labeled  "Skydome" check that, and you should be good to go.  If that line isn't there, let me know.

---

### Post by lkjoel on 2010-06-29
What version of Ubuntu do you use?
And what variant do you use?
Ubuntu version = 8.04, 10.04, 9.10 etc...
Ubuntu variant = Ubuntu, Kubuntu, Xubuntu, Ubuntu studio etc...

---

### Post by cthom on 2010-07-01
doh!!!! i'm so sorry, i found it in Appearance (next to behaviour) #-o

---

### Post by cthom on 2010-07-01
..

---

### Post by edgekrusher187 on 2010-07-01
I have done everything mentioned in this thread but still do not see the Background image option under the appearance tab for Desktop Cube.

---

### Post by bigsmitty64 on 2010-07-01
> **edgekrusher187 said:**
> I have done everything mentioned in this thread but still do not see the **Background image** option under the appearance tab for Desktop Cube.
It doesn't say "**background image**" it says "Skydome Image" , hope this helps ya.

---

### Post by edgekrusher187 on 2010-07-01
I figured that out. I was more looking for a way to have a different wallpaper in the various workspaces.

---

### Post by bigsmitty64 on 2010-07-01
In ccsm....Utility/wallpaper, and add your pics, but you can't have icons when you do this.

---

### Post by edgekrusher187 on 2010-07-01
I have that enabled, and have four different wallpapers loaded in utilities->wallpapers but I can't figure out how to apply a different one to each workspace. I'm just getting back into the Linux world so... 

Thanks for the help.

---

### Post by bigsmitty64 on 2010-07-01
Try this,
Open a terminal, and type "**gconf-editor**"  (without quotes) and hit enter.

The gconf editor will open

Under **[COLOR=Teal]Apps->Nautilus->Preferences[/COLOR]**  you'll find a checkbox next to "Show Desktop".  Un-check this checkbox. click OK and reboot (if needed.)

---

### Post by lkjoel on 2010-07-01
> **lkjoel said:**
> Sorry I forgot a package. Do this instead:
```
sudo apt-get install compizconfig-settings-manager compiz-fusion-plugins-main compiz-fusion-plugins-extra
```
Try that.

---

