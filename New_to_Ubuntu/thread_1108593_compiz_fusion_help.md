---
title: "compiz fusion help?"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by iam_newhere on 2009-03-27
hi, i am running xubuntu 8.04. and i installed compiz fusion and the problem is i dont know why i only have 2 desktops/workspaces on my bottom panel. 

i tried going into applications> settings> settings manager> workspaces and margins to change it to 4. but then no change. there's only two. how can i fix this so i can enable 3d desktop cube?


thanks!

---

### Post by Miljet on 2009-03-27
Just right click on the desktops applet, click on preferences, and set it for as many as you wish.

---

### Post by iam_newhere on 2009-03-27
> **Miljet said:**
> Just right click on the desktops applet, click on preferences, and set it for as many as you wish.

where exactly would i click? can you please tell me step by step please?
sorry im just a beginner.

---

### Post by Miljet on 2009-03-27
In the bottom right corner of your screen, right beside the trash icon. You say you only have two desktops. Right click on either of them, click properties, and change it to whatever you want.

---

### Post by iam_newhere on 2009-03-27
> **Miljet said:**
> In the bottom right corner of your screen, right beside the trash icon. You say you only have two desktops. Right click on either of them, click properties, and change it to whatever you want.

i did that and a window comes up and the only option is switch workspaces between the mousewheel.

the title of the window was pager btw.

---

### Post by oldos2er on 2009-03-27
The applet you're looking for is 'Workspace Switcher.' You can add it to your panel by right-clicking once, choose Add to Panel, Workspace Switcher.

---

### Post by iam_newhere on 2009-03-27
> **oldos2er said:**
> The applet you're looking for is 'Workspace Switcher.' You can add it to your panel by right-clicking once, choose Add to Panel, Workspace Switcher.

i right clicked on my bottom panel, i clicked add new item but i couldnt find 'workspace switcher' on the list.

any suggestions?

---

### Post by russo.mic on 2009-03-28
So,  Seems we have some uninformed people responding here on the forums.

Lets get your repo's done first, from a terminal (applications, accesories, terminal) type:
sudo apt-get update


First  if all, if your playing with compiz, the first thing you need to do is this:

1. from a terminal, (applications, accesories, terminal) type this:
sudo apt-get install compizconfig-settings-manager

Put in your passsword,

This will get you the settings app that will allow you to adjust the parameters of compiz to you heart's content.

From there, you want to go to (system, preferences, compizconfig settings manager), and find the general settings (should be the first thing in the list) and go to the desktop size tab.  The horizontal size fader is the one to adjust to get more workspace s with compiz.

Good luck!

Russo

---

### Post by Paqman on 2009-03-28
> **iam_newhere said:**
> i right clicked on my bottom panel, i clicked add new item but i couldnt find 'workspace switcher' on the list.

any suggestions?

That's because you're using XFCE, but he was giving you instructions for Gnome. Not your fault there at all. If you do what russo.mic detailed, you should get your cube up and running no problem.

Did you know that XFCE has a built-in compositor though? It's not as flashy as Compiz, but it does dropshadows, transparency, and allows you to run apps like Avant Window Navigator.  So if you're not bothered about having Compiz animations that would be a good way to go.

---

### Post by iam_newhere on 2009-03-28
i got it!

thanks to russo.mic and paqman!

:popcorn:

---

### Post by Miljet on 2009-03-28
So sorry for the misinformation. I completely did not notice that you were running Xubuntu. I'll try to read the post a little closer next time.

---

### Post by iam_newhere on 2009-03-28
> **Miljet said:**
> So sorry for the misinformation. I completely did not notice that you were running Xubuntu. I'll try to read the post a little closer next time.

its alright i got it fixed now. thanks anyways!

---

