---
title: "Remove bottom panel with command line"
date: 2010-10-05
forum: New to Ubuntu
---

### Post by fatality_uk on 2010-10-05
Total brain fade this morning! Could someone tell me how to remove the bottom panel using the command line please.

Cheers

---

### Post by Najand on 2010-10-05
Well you need to have some knowledge of gconf-editor or gconftool. 
For command line you may use the gconftool.
First of all use the "-g" attribute to get the list of your current panels:
```

gconftool -g /apps/panel/general/toplevel_id_list

```
You will receive something like:
[I][bottom_panel_screen0,top_panel_screen0]
[/I]
Then You should set the value for the "toplevel_id_list" using "-s"
for example if you only want the top panel in the above example:
```
gconftool -s /apps/panel/general/toplevel_id_list -t string "[top_panel_screen0]"
```
Then if you restart your gnome the bottom panel is gone.
I think it helps you.
(I haven't checked the code, so please be don't run any commands you don't know what it does.

---

### Post by fatality_uk on 2010-10-05
Just for interest, it should be **gconftool-2 --set [keyname]** to set keys. e.g **gconftool-2 --set /apps/nautilus/preferences/click_policy --type string "double"**
But that's not what I was looking for. I'll check some of my scripts. Sorry for not being clear.

---

### Post by Najand on 2010-10-05
Well, in fact you that is a differnt tool called **"gconftool-2"** which is very similar to **"gconftool"**.
Well, I am afraid I don't know any other ways. You may still change the keys directly by editing the **"%gconf.xml"** XML file under the **.gconf directory**. 
In panel case it is **".gconf/apps/panel/general/%gconf.xml"**. You may write a shell script to find and change the keys, but it is still the same solution.
Sorry for taking your time.

---

### Post by fatality_uk on 2010-10-05
Hi Najand,

Thanks for the posts so far. I did have a script somewhere, covering this in part, but I have managed to lose it!! What I want to do is delete the following entry

/apps/panel/toplevels/bottom_panel_screen0

so entering ```
gconftool-2 --recursive-unset /apps/panels/toplevels/bottom_panel_screen0
```

Just clears the data underneath that and not that directory
Can't seem to do it for some reason!!!

n.b. this is a clean, default install so I know that the panels could be anywhere but as it stands, it's pretty much all default entries.

---

### Post by fatality_uk on 2010-10-05
Just wondering if anyone might have any ideas re above?

---

### Post by fatality_uk on 2010-10-06
Well googling results in me being able to get rid of ALL the panels, but not the bottom one alone through the command line (Bash#) Hmm, temrinal gurus "where for art thou?"

---

### Post by drs305 on 2010-10-06
I can kill the bottom panel by renaming (it makes a very small panel at the top):
> ~/.gconf/apps/panel/toplevels/bottom_panel_screen0/background

I renamed it *bottom_panel_screen0[COLOR="Red"]x[/COLOR]*, refreshed the panels and the bottom panel disappeared. Don't know how persistent it will be.

```

mv ~/.gconf/apps/panel/toplevels/bottom_panel_screen0  ~/.gconf/apps/panel/toplevels/bottom_panel_screen0[COLOR="Red"]x[/COLOR]
killall gnome-panel

```

---

### Post by fatality_uk on 2010-10-07
> **drs305 said:**
> I can kill the bottom panel by renaming (it makes a very small panel at the top):


I renamed it *bottom_panel_screen0[COLOR="Red"]x[/COLOR]*, refreshed the panels and the bottom panel disappeared. Don't know how persistent it will be.

```

mv ~/.gconf/apps/panel/toplevels/bottom_panel_screen0  ~/.gconf/apps/panel/toplevels/bottom_panel_screen0[COLOR="Red"]x[/COLOR]
killall gnome-panel

```

Many thanks. Will try that later!

---

### Post by fatality_uk on 2010-10-07
Tried that but didn't work unfortunately. After **killall** the bottom panel reappeared above the top panel.

This is an OEM install before I prep for end user. The idea is to use the OEM install as a base, script any changes post install and the prep for the end user so they then register it under their log in details.

It's looking like I will have to intervene manually then.
Thanks for the help guys

---

