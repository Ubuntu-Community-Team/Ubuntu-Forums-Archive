---
title: "Appearance keeps closing"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by steigerjb on 2009-08-12
I can't open Appearance settings. It'll open for like a second and then close automatically.

I have tried opening both ways:

-right click desktop > Change Desktop Background
-System > Preferences > Appearance

:confused::confused::confused:

---

### Post by CatKiller on 2009-08-12
You've tried *two ways*, but that's not *all ways*, grasshopper :)

Running ```
gnome-appearance-properties
``` in a Terminal may give you some clues as to what's going wrong.

---

### Post by steigerjb on 2009-08-12
> **CatKiller said:**
> You've tried *two ways*, but that's not *all ways*, grasshopper :)

Running ```
gnome-appearance-properties
``` in a Terminal may give you some clues as to what's going wrong.

```
joe@joe-ubuntu:~$ gnome-appearance-properties
Gtk-Message: Failed to load module "globalmenu-gnome": libglobalmenu-gnome.so: cannot open shared object file: No such file or directory
Gtk-Message: Failed to load module "globalmenu-gnome": libglobalmenu-gnome.so: cannot open shared object file: No such file or directory
/home/joe/.themes/Aureus-Mariux/gtk-2.0/gtkrc:129: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/joe/.themes/Aureus-Mariux/gtk-2.0/gtkrc:199: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/joe/.themes/Aureus-Mariux/gtk-2.0/gtkrc:236: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/joe/.themes/Aureus-Mariux/gtk-2.0/gtkrc:256: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/joe/.themes/Aureus-Mariux/gtk-2.0/gtkrc:325: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/joe/.themes/Murrina-LiNsta/gtk-2.0/gtkrc:71: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/joe/.themes/Murrina-LiNsta/gtk-2.0/gtkrc:1009: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.

(gnome-appearance-properties:16940): appearance-properties-WARNING **: Unknown Tag: _name


(gnome-appearance-properties:16940): appearance-properties-WARNING **: Unknown Tag: _name


(gnome-appearance-properties:16940): appearance-properties-WARNING **: Unknown Tag: _name


(gnome-appearance-properties:16940): appearance-properties-WARNING **: Unknown Tag: _name


(gnome-appearance-properties:16940): appearance-properties-WARNING **: Unknown Tag: _name


(gnome-appearance-properties:16940): appearance-properties-WARNING **: Unknown Tag: comment


(gnome-appearance-properties:16940): appearance-properties-WARNING **: Unknown Tag: _name


(gnome-appearance-properties:16940): appearance-properties-WARNING **: Unknown Tag: _name


(gnome-appearance-properties:16940): appearance-properties-WARNING **: Unknown Tag: _name


(gnome-appearance-properties:16940): appearance-properties-WARNING **: Unknown Tag: _name


(gnome-appearance-properties:16940): appearance-properties-WARNING **: Unknown Tag: _name


(gnome-appearance-properties:16940): appearance-properties-WARNING **: Unknown Tag: comment


** (gnome-appearance-properties:16940): CRITICAL **: gnome_desktop_thumbnail_factory_lookup: assertion `uri != NULL' failed
Segmentation fault
joe@joe-ubuntu:~$ 

```

---

### Post by steigerjb on 2009-08-14
anybody?

---

### Post by CatKiller on 2009-08-14
> **steigerjb said:**
> ```
** (gnome-appearance-properties:16940): CRITICAL **: gnome_desktop_thumbnail_factory_lookup: assertion `uri != NULL' failed
Segmentation fault

```

Well, I think that's the problematic bit. But I don't know what it means.

---

### Post by steigerjb on 2009-08-14
> **CatKiller said:**
> Well, I think that's the problematic bit. But I don't know what it means.

haha, yeah me either :lolflag:

---

### Post by CatKiller on 2009-08-14
You could try changing the theme through gconf-editor, in case it's just a problem with the theme you're using. I believe the keys are /desktop/gnome/interface/gtk_theme, ../icon_theme and /apps/metacity/general/theme. Change them to something that's worked before, like Human.

I'm not that optimistic, though, I'm afraid.

---

### Post by steigerjb on 2009-08-15
> **CatKiller said:**
> You could try changing the theme through gconf-editor, in case it's just a problem with the theme you're using. I believe the keys are /desktop/gnome/interface/gtk_theme, ../icon_theme and /apps/metacity/general/theme. Change them to something that's worked before, like Human.

I'm not that optimistic, though, I'm afraid.

I am using a Ubuntu theme already...dust

---

### Post by jrothwell97 on 2009-08-15
Segmentation faults are tricky. My advice is to report this as a bug and hope for the best - unfortunately, there's not much more I think you can do for now :(

---

### Post by steigerjb on 2009-08-15
> **jrothwell97 said:**
> Segmentation faults are tricky. My advice is to report this as a bug and hope for the best - unfortunately, there's not much more I think you can do for now :(

k, i reported it in launchpad

---

### Post by steigerjb on 2009-08-18
they actual closed my launchpad bug report :(

> "Thank you for taking the time to report this bug and helping to make
Ubuntu better. However, your crash report is either missing or
challenging to deal with as a ".crash" file. Please follow these
instructions to have apport report a new bug about your crash that can
be dealt with by the automatic retracer.

If you are running the Ubuntu Stable Release you might need to enable
apport in /etc/default/apport and restart.

If you are using Ubuntu with the Gnome desktop environment - launch nautilus and navigate to your /var/crash directory and double click on the crash report you wish to submit."

I have no idea what they mean. There is nothing in the /var/crash folder.

So its now up you all here to help me

---

### Post by philinux on 2009-08-18
Open your home folder. ctrl h to dhow hidden files. Open .themes and delete or rename the offending themes in there.

.themes/Aureus-Mariux/

.themes/Murrina-LiNsta

---

### Post by steigerjb on 2009-08-19
> **philinux said:**
> Open your home folder. ctrl h to dhow hidden files. Open .themes and delete or rename the offending themes in there.

.themes/Aureus-Mariux/

.themes/Murrina-LiNsta

nope

**gnome-appearance-properties**

```
joe@joe-ubuntu:~$ gnome-appearance-properties

(gnome-appearance-properties:4417): appearance-properties-WARNING **: Unknown Tag: _name


(gnome-appearance-properties:4417): appearance-properties-WARNING **: Unknown Tag: _name


(gnome-appearance-properties:4417): appearance-properties-WARNING **: Unknown Tag: _name


(gnome-appearance-properties:4417): appearance-properties-WARNING **: Unknown Tag: _name


(gnome-appearance-properties:4417): appearance-properties-WARNING **: Unknown Tag: _name


(gnome-appearance-properties:4417): appearance-properties-WARNING **: Unknown Tag: comment


(gnome-appearance-properties:4417): appearance-properties-WARNING **: Unknown Tag: _name


(gnome-appearance-properties:4417): appearance-properties-WARNING **: Unknown Tag: _name


(gnome-appearance-properties:4417): appearance-properties-WARNING **: Unknown Tag: _name


(gnome-appearance-properties:4417): appearance-properties-WARNING **: Unknown Tag: _name


(gnome-appearance-properties:4417): appearance-properties-WARNING **: Unknown Tag: _name


(gnome-appearance-properties:4417): appearance-properties-WARNING **: Unknown Tag: comment


** (gnome-appearance-properties:4417): CRITICAL **: gnome_desktop_thumbnail_factory_lookup: assertion `uri != NULL' failed
Segmentation fault
joe@joe-ubuntu:~$ 

```

---

### Post by Kriblom on 2009-08-20
I had the same problem after trying to change periodically the wallpaper via a script.

I just removed the "~/.gnome2/backgrounds.xml" and it now re-works !

Seems if the xml file points to a non-existant picture, gnome-appearance will crash :/

---

### Post by steigerjb on 2009-08-20
> **Kriblom said:**
> I had the same problem after trying to change periodically the wallpaper via a script.

I just removed the "~/.gnome2/backgrounds.xml" and it now re-works !

Seems if the xml file points to a non-existant picture, gnome-appearance will crash :/

nope

---

### Post by Volt9000 on 2009-08-21
I checked my system and found that I didn't have that library that's being referenced (globalmenu-gnome).

So I did some Googling and it appears that module is used by [this](http://code.google.com/p/gnome2-globalmenu/).

I also found a post on another website where someone has the same issue. So here's the link, lemme know if it works for you.

[http://magnus-k-karlsson.blogspot.com/2009/02/remove-gnome-globalmenu.html](http://magnus-k-karlsson.blogspot.com/2009/02/remove-gnome-globalmenu.html)

---

### Post by steigerjb on 2009-08-22
> **Volt9000 said:**
> I checked my system and found that I didn't have that library that's being referenced (globalmenu-gnome).

So I did some Googling and it appears that module is used by [this](http://code.google.com/p/gnome2-globalmenu/).

I also found a post on another website where someone has the same issue. So here's the link, lemme know if it works for you.

[http://magnus-k-karlsson.blogspot.com/2009/02/remove-gnome-globalmenu.html](http://magnus-k-karlsson.blogspot.com/2009/02/remove-gnome-globalmenu.html)

still nope

---

### Post by steigerjb on 2009-08-22
```
joe@joe-ubuntu:~$ gnome-appearance-properties

(gnome-appearance-properties:13892): appearance-properties-WARNING **: Unknown Tag: _name


(gnome-appearance-properties:13892): appearance-properties-WARNING **: Unknown Tag: _name


(gnome-appearance-properties:13892): appearance-properties-WARNING **: Unknown Tag: _name


(gnome-appearance-properties:13892): appearance-properties-WARNING **: Unknown Tag: _name


(gnome-appearance-properties:13892): appearance-properties-WARNING **: Unknown Tag: _name


(gnome-appearance-properties:13892): appearance-properties-WARNING **: Unknown Tag: comment


(gnome-appearance-properties:13892): appearance-properties-WARNING **: Unknown Tag: _name


(gnome-appearance-properties:13892): appearance-properties-WARNING **: Unknown Tag: _name


(gnome-appearance-properties:13892): appearance-properties-WARNING **: Unknown Tag: _name


(gnome-appearance-properties:13892): appearance-properties-WARNING **: Unknown Tag: _name


(gnome-appearance-properties:13892): appearance-properties-WARNING **: Unknown Tag: _name


(gnome-appearance-properties:13892): appearance-properties-WARNING **: Unknown Tag: comment


** (gnome-appearance-properties:13892): CRITICAL **: gnome_desktop_thumbnail_factory_lookup: assertion `uri != NULL' failed
Segmentation fault
joe@joe-ubuntu:~$ 

```

---

### Post by steigerjb on 2009-08-25
anybody know??? it's getting REALLY frustrating.

---

### Post by steigerjb on 2009-08-28
anybody know???

---

### Post by Muddville on 2009-08-31
> **CatKiller said:**
> You've tried *two ways*, but that's not *all ways*, grasshopper :)

Running ```
gnome-appearance-properties
``` in a Terminal may give you some clues as to what's going wrong.

Same problem here on a new installation of Netbook Remix/Acer Aspire One.  Terminal message is:
(gnome-appearance-properties:3987): appearance-properties-WARNING **: Could not load user interface file: Duplicate object id 'hbox1' on line 1910 (previously on line 29)

...all of which is more Greek to me than most Windows error messages.  :-0

---

### Post by steigerjb on 2009-08-31
someone help me and Muddville :confused:

---

### Post by JerichoKru on 2009-08-31
Have you tried re-installing that particular program with APT/Synaptic?  It seems to me that something got corrupted at some point.

---

### Post by Muddville on 2009-08-31
> **JerichoKru said:**
> Have you tried re-installing that particular program with APT/Synaptic?  It seems to me that something got corrupted at some point.

No, but I see that Update Manager is doing the same thing.  It opened properly once this morning and just hangs and stops before opening now - pretty much the same thing as Appearance, which I've never been able to open.  Just installed this yesterday and am still getting used to how it works, but I'll look for some documentation on reinstalling stuff.

I guess it's a good thing this isn't Windows or I'd probably be reinstalling the whole bloody thing.  :-P

Update: Still looking for "Appearance" in Synaptics but I found Update Manager and reinstalled, to no avail.  Reported bug.

---

### Post by LowSky on 2009-08-31
Is this happening in 9.04 or are you using the Alpha of 9.10 because I had a similar issue on 9.10.

I would reinstall the ubuntu-desktop package, maybe delete any themes you installed recently

the bug soes exist on Launchpad... the fix is to remove the offending icon themes

---

### Post by steigerjb on 2009-09-01
> **LowSky said:**
> Is this happening in 9.04 or are you using the Alpha of 9.10 because I had a similar issue on 9.10.

I would reinstall the ubuntu-desktop package, maybe delete any themes you installed recently

the bug soes exist on Launchpad... the fix is to remove the offending icon themes

didn't help

---

### Post by Muddville on 2009-09-03
Found a way to initiate the update check sans Update Manager.  Once available updates were installed, Update Manager and Appearance worked properly.  Life is good.  :)

---

### Post by steigerjb on 2009-09-03
> **Muddville said:**
> Found a way to initiate the update check sans Update Manager.  Once available updates were installed, Update Manager and Appearance worked properly.  Life is good.  :)

fix mine Muddville...what do I do??????

---

### Post by ks07 on 2009-09-03
> **steigerjb said:**
> fix mine Muddville...what do I do??????
If you want to update without the update manager type into a terminal:
```
sudo apt-get update
```
then
```
sudo apt-get upgrade
```

I'm guessing this is what Muddville did, as this is how the update manager works behind the scenes.

---

### Post by steigerjb on 2009-09-03
> **ks07 said:**
> If you want to update without the update manager type into a terminal:
```
sudo apt-get update
```
then
```
sudo apt-get upgrade
```

I'm guessing this is what Muddville did, as this is how the update manager works behind the scenes.

that didn't help me ks07

---

### Post by Windows Nerd on 2009-09-03
> **Muddville said:**
> ...all of which is more Greek to me than most Windows error messages.  :-0
Haha. That one made me laugh. 

Maybe installing an alternate theme manager might help? Because the current one looks like it has been corrupted. Thats all I can think of at the moment.

Scott

---

### Post by steigerjb on 2009-09-03
got a private message:

[QUOTE=Najmudin]Hi
I followed you problem since the begining,sorry for your frustration.
I don't know if this will help you.
Try to open your home folder > Ctrl+H to show hidden files > delete .icons & .themes folders.
logout and select "gnome" from session, then log in.
I hope this can help.:neutral:[/QUOTE]

nope

---

### Post by steigerjb on 2009-09-06
I gotta get this fixed [-o< We gotta call in the Ubuntu Forum staff in on this one...get some answers.

I attached a video. Maybe I am not describing it right.

Somebody help me PLEASE! :sad::!:#-o:frown:](*,)

---

### Post by steigerjb on 2009-09-09
Somebody help me PLEASE!

---

### Post by steigerjb on 2009-09-10
bump?

---

### Post by steigerjb on 2009-09-14
bump. someone help me plz

---

### Post by yzfvie on 2009-09-14
I think I have a similar problem with several applications.
I installed google earth and skype. Both applications worked fine the first time I used them.
 The next day, I tried to use them again and found that they would not activate at all in the "Applications" pull down menu. They were in the "Internet"  list.
Today, I tried to remove the software using "add/remove" and found that this option would appear for a second and disappear from my desktop. I then tried "Synaptic applications" in "System" menu and saw the same results.

What is going on???

---

### Post by steigerjb on 2009-09-15
idk

---

### Post by steigerjb on 2009-09-18
bumping again

---

### Post by shae on 2009-09-19
Have you tried creating a new user and see if it experiences the same problem?

---

### Post by ibuclaw on 2009-09-20
If creating a new account doesn't work, then try reinstalling the apps affected.
```
sudo aptitude reinstall gnome-control-center libgnome-desktop-2-11
```

Regards
Iain

---

### Post by steigerjb on 2009-09-21
> **tinivole said:**
> If creating a new account doesn't work, then try reinstalling the apps affected.
```
sudo aptitude reinstall gnome-control-center libgnome-desktop-2-11
```

Regards
Iain

nope

---

### Post by steigerjb on 2009-09-21
i am going to try upgrading to karmic koala and see if that fixes it

---

### Post by steigerjb on 2009-09-22
upgrading didn't fix it. and it broke my desktop effects (I have none now :( )

---

### Post by steigerjb on 2009-09-24
reinstalled Jaunty, problems solved

---

