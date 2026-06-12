---
title: "moving the [close, minimize, maximize] buttons"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by taith on 2010-05-17
i just upgraded to 10.4, and the close, minimize, maximize buttons are on the left of every window... how do i move them back to the right? i looked around, but didnt find anything useful :(

---

### Post by ubunterooster on 2010-05-17
[B][COLOR=DarkRed]

Minimize, Maximize and Close button placement.[/COLOR][/B]
A decision has been taken to move the placement to the left. Mark  Shuttleworth explained that this was because "something" is going to be  placed in the right hand area in the next release. Moving the buttons  now would help enable this change.
**[Update ][http://www.markshuttleworth.com/archives/333](http://www.markshuttleworth.com/archives/333)**

The buttons are in the old location on all default themes apart from  Ambiance,Radiance and Dust, If you still want the Ambiance ,Radiance or  Dust theme but with buttons on the right, choose one of those other  themes and use the Customize button to achieve what you want. e.g.
1. System > Preferences > Appearance
2. Select the theme icon "New Wave"
3. Click the button "Customize.."
4. Select tab "Controls" and select "Ambiance"
5. Select tab "Window border" and select "Ambiance"
6. Select tab "Icons" and scroll down and select "Ubuntu-mono-dark"
7. Select "Save Theme" to your choice.
**Using gconf-editor is not the right approach as this could bork  future themes. This change makes it easier for themes to do interesting  things with window borders.  Unfortunately, if the wrong approach  spreads, they won't be able to do that.**

---

### Post by drs305 on 2010-05-17
Note Added: This procedure may provide undesireable results with future theming plans for Ubuntu releases.

```
gconftool-2 --set --type string /apps/metacity/general/button_layout ":minimize,maximize,close" 
```

[COLOR="DarkRed"]:minimize,maximize,close[/COLOR]  - The colon determines which side the buttons are on. Entries to the left of the colon are at the top left; entries to the right of the colon are on the top right.

---

### Post by taith on 2010-05-17
sweet :P thanks :D

---

### Post by ubunterooster on 2010-05-17
umm[quote=philinux]**Using gconf-editor is not the right approach as this could bork   future themes. This change makes it easier for themes to do interesting   things with window borders.  Unfortunately, if the wrong approach   spreads, they won't be able to do that.**[/quote]

---

### Post by KdotJ on 2010-05-17
I think it's far too late for that if you ask me lol

---

### Post by ubunterooster on 2010-05-17
No, I can tell him before he tells it to someone else.

---

### Post by drs305 on 2010-05-17
I did not see ubunterooster's last lines or I would have either not made the post or learned more about the caution before presenting the command line option. I have not seen it presented elsewhere and would like to learn more about it's origin so I can give the proper advice on this forum. This command was presented numerous times in Launchpad bug reports with the full knowledge of the developers, including threads in which Mark Shuttleworth contributed. If he or anyone else mentioned this caution late in the development cycle I missed it, which is entirely possible.

On the other hand, the command I presented is easily reversible and 10.04 is an LTS version whose default theming is not likely to  change. I won't delete the post but will refrain from using it in the future until I conduct some further research. I've added a note at the beginning of my post.

Thanks for teaching me something.

---

### Post by MockY on 2010-05-17
[Ubuntu Tweaks]("http://ubuntu-tweak.com/") will make it possible to change it with a single mouse click, and gives you the ability to change many other things as well as a bonus.

---

### Post by ubunterooster on 2010-05-17
[**Ubuntu-tweak is another good alternative: Download  Now!**Version 0.5.4.1]("http://launchpad.net/ubuntu-tweak/0.5.x/0.5.4.1/+download/ubuntu-tweak_0.5.4.1-1_all.deb")

Edit: I missed seeing you had a link; I thought you did not.

---

### Post by drs305 on 2010-05-17
> **MockY said:**
> [Ubuntu Tweaks]("http://ubuntu-tweak.com/") will make it possible to change it with a single mouse click, and gives you the ability to change many other things as well as a bonus.

... Which uses the command I presented to change the metacity gconf-editor settings.  ](*,)

---

### Post by ubunterooster on 2010-05-17
> **drs305 said:**
> ... Which uses the command I presented to change the metacity gconf-editor settings.  ](*,)
The difference is it is simple for the beginner to change it back

---

### Post by drs305 on 2010-05-17
Reset to defaults:
```
gconftool-2 --unset /apps/metacity/general/button_layout
or
gconftool-2 --set --type string /apps/metacity/general/button_layout "minimize,maximize,close:"

```

But I'm a big fan of Ubuntu-Tweak and agree with you. I highly recommend it to beginners, especially for tasks such as removing older kernels.

---

### Post by KdotJ on 2010-05-17
> **ubunterooster said:**
> No, I can tell him before he tells it to someone else.

lol, I meant I think too many people have cone it the "incorrect" way already

---

### Post by ubunterooster on 2010-05-17
> **KdotJ said:**
> lol, I meant I think too many people have cone it the "incorrect" way already
oh. I understand you now.

---

### Post by inyoka on 2010-07-15
Thanks ubunterooster thats the best answer I have seen for the reasoning behind this decision.  I thought Ubuntu was just being annoying, but the new application bar proposal looks really nice :)

---

### Post by 3rdalbum on 2010-07-15
The alternative to gconf-editor, Ubuntu Tweak and choosing a new theme is simply to wait a couple of days.

No, there's no post-release update that moves the window buttons, but in a couple of days you'll be used to the new position, and you'll also be ready for the Windicators in Ubuntu 10.10.

---

