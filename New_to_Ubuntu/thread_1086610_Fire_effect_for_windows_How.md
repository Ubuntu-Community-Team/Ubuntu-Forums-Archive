---
title: "Fire effect for windows? How?"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by Gp. on 2009-03-04
I've got compiz enabled and all those cool effects, but I've seen on youtube theres a fire effect. When you close a window it burns up in flames. How did they get this? The video I watched the guy also had a tone of extra 3d effects loaded in.

My question is how !?

Thanks :D

---

### Post by albandy on 2009-03-04
sudo apt-get install compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-unsupported

this will install a compiz manager and some plugins.

Then you will see in system-->preferences an entry called compizconfig

---

### Post by jaminux on 2009-03-04
Open a terminal and type:

sudo apt-get install compizconfig-settings-manager

After installation there is now an entry for this in System > Preferences

The is a setting for fire in there, as well as a lot of other stuff.

---

### Post by Gp. on 2009-03-04
CompizConig Settings Manager installed, but I can't find the fire option out of all these options?

---

### Post by billgoldberg on 2009-03-04
> **Gp. said:**
> CompizConig Settings Manager installed, but I can't find the fire option out of all these options?

Look for "animations".

In there you can set what is to happen when for instance you close a window. 

Edit the current effect and replace it with the fire effect.

Make sure you are running Compiz Fusion and the animations effect box is tagged.

If you are not sure you are running Compiz Fusion to to system -> appearance and in the most right tab, pick the bottom option.

Then set the animations effects.

If you are interested in theming Ubuntu, click on the link in my signature to my How-To.

---

### Post by scottuss on 2009-03-04
When you run the settings manager there is a textbox at the top left called "filter" just type fire into that. If it doesn't appear, you don't have that plugin installed.

---

### Post by jaminux on 2009-03-04
This is strange. In Ubuntu 8.10 all I have to do is get compizconfig-settings-manager and then "Paint fire on the screen" is under effects.

I was assuming you used 8.10 though... might not be the case.

---

### Post by Gp. on 2009-03-04
Yes, I have paint fire on screen option.
but I want the effect where you close a window and the window burns up.

---

### Post by jaminux on 2009-03-04
ah :/ just read the fire bit of the original post and assumed

---

### Post by Gp. on 2009-03-04
Watch this:

[http://www.youtube.com/watch?v=V_XXuEPqErk](http://www.youtube.com/watch?v=V_XXuEPqErk)


You'll see it in here.

---

### Post by scottuss on 2009-03-04
Apologies, I got the wrong end of the stick.

Firstly, activate the Animations Add-On plugin from the settings manager. Then activate Animations. Go into Animations settings and
click the "close animation tab" 

You need to give it window rules (the windows that will set on fire) Click the new button and add some rules. Select Burn as the animation effect from the drop down box.

Some example settings:

```

(type=Normal | Dialog | ModalDialog | Unknown) & !(name=gnome-screensaver)

(type=Menu | PopupMenu | DropdownMenu)

(type=Tooltip | Notification | Utility) & !(name=compiz)


```

---

### Post by Gp. on 2009-03-04
Hi,
There is no burn option? Theres other ones, just not burn? :S

---

### Post by billgoldberg on 2009-03-04
> **Gp. said:**
> Hi,
There is no burn option? Theres other ones, just not burn? :S

I just checked, there also isn't a Burn option anymore for me.

Not the I use it as it looks really cheesy.

Try looking for the plugin in google.

---

### Post by Gp. on 2009-03-04
What should I be googling exactly? :S

---

### Post by JPtux on 2009-03-04
> **Gp. said:**
> What should I be googling exactly? :S

It's under the Animations Add-on as stated previously. You need to activate that plugin first.

---

### Post by Gp. on 2009-03-04
I have.

There is no burn option.

See attachment.

---

### Post by skymera on 2009-03-04
Do you have the extra effects enabled?

These are in CCSM next to (or near) Animations

---

### Post by Gp. on 2009-03-04
No I didn't, but I found it now!

Thanks guys! :)

Ubuntu on!

---

### Post by jaminux on 2009-03-04
> **billgoldberg said:**
> I just checked, there also isn't a Burn option anymore for me.

Not the I use it as it looks really cheesy.

Try looking for the plugin in google.

This is weird. I copied and pasted your exact command after you posted them (to test burn) and it worked fine for me.

---

