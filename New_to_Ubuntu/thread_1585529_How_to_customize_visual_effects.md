---
title: "How to customize visual effects?"
date: 2010-09-30
forum: New to Ubuntu
---

### Post by robfuller on 2010-09-30
Hello,

How can I customize which visual effects are active? I have selected "normal" visual effects in the Appearances Preferences box, and I want to keep it on "normal" (because I use Docky, which needs it). But I prefer some of the specific visual effects which come with the "none" setting. For example, I don't want transparent window title bars, and I find the basic window-switcher (the thing which appears when you press ctrl-tab) much easier to use than the "normal" one.

Can I somehow deselect these specific effects, while still keeping the "normal" setting? Do I need to install Compiz to do this?

Thanks in advance,
Rob

---

### Post by punkdrummer09 on 2010-09-30
> **robfuller said:**
> Hello,

How can I customize which visual effects are active? I have selected "normal" visual effects in the Appearances Preferences box, and I want to keep it on "normal" (because I use Docky, which needs it). But I prefer some of the specific visual effects which come with the "none" setting. For example, I don't want transparent window title bars, and I find the basic window-switcher (the thing which appears when you press ctrl-tab) much easier to use than the "normal" one.

Can I somehow deselect these specific effects, while still keeping the "normal" setting? Do I need to install Compiz to do this?

Thanks in advance,
Rob

I would say go with Compiz, and see what you can do from there.

---

### Post by emoguitarist06 on 2010-09-30
Install CCSM just open the Software Center and type CCSM in the search box

That's the Compiz configuration editor where you can every single effect

---

### Post by robfuller on 2010-09-30
OK, yes, I've installed CompizConfig. But... it's kind of overwhelming, and I have no idea what 90 per cent of the options mean. Can anyone tell me specifically how to activate the basic application switcher (the one used with the "none" visual effect ssetting), and how to make window borders non-transparent?

---

### Post by emoguitarist06 on 2010-09-30
are you thinking of the **ALT+TAB** application switcher?

Unfortunately I'm personally at work on this crappy Windows XP so I can't walk you through it but I think it's under "windows" or "utility" category near the bottom of CCSM.

**[COLOR="Red"]ANYONE ELSE?[/COLOR]**

---

### Post by robfuller on 2010-09-30
Yes, that's right, it's the alt-tab switcher I'm talking about. (Sorry for the mistake in my original post.) As I said, it's not obvious how to achieve this from CCSM. Hope someone can help...

---

### Post by emoguitarist06 on 2010-09-30
Try this solution 
[http://ubuntuforums.org/showthread.php?t=1426969](http://ubuntuforums.org/showthread.php?t=1426969)

The settings are under "Window Management" then "Application Switcher".

---

### Post by emoguitarist06 on 2010-09-30
It looks like according to this forum
[http://ubuntuforums.org/showthread.php?t=1128838](http://ubuntuforums.org/showthread.php?t=1128838)
there's no way to have the ALT+TAB look like metacity's while running compiz

---

### Post by robfuller on 2010-10-01
OK. Thanks very much for looking up those references for me.

---

### Post by mcduck on 2010-10-01
> **robfuller said:**
> OK, yes, I've installed CompizConfig. But... it's kind of overwhelming, and I have no idea what 90 per cent of the options mean. Can anyone tell me specifically how to activate the basic application switcher (the one used with the "none" visual effect setting), and how to make window borders non-transparent?

Like others have already said, the window switcher is a feature of the window manager, and when you use visual effects you are using Compiz as your window manager, as opposed to Metacity. (The options in the Appearance dialog switch between Metacity ("none" and two different pre-configured settings for Compiz (normal & extra). 
As the options there are just presets, changing any option will mean that you aren't using that preset any more and instead the Appearcne dialog tells you that you are using "custom" settings now. This makes no difference from any application's point of view, if some document for Docky claims that you need to have this set to "normal" for Docky to work it probably tries to just tell you that you need to *at least* have it on normal, meaning that you need to be using Compiz as your window manager.

So, you can't use the window switcher from Metacity while you aren't running Metacity. On the other hand Compiz actually includes several different plugins for this purpose, so I'm sure you'll find one that you like if you try the different options. :)

All right. Then to the window border transparency. Easy fix. Press Alt-F2 and run "gconf-editor". Use that to browse to apps/gwd and set the "metacity_theme_active_opacity" and "metacity_theme_opacity" both to "1".

---

### Post by robfuller on 2010-10-01
Great, thanks, McDuck. The Metacity settings for opacity in gconf-editor seem to be working, even when I'm using Compiz.

OK, so now I have another (related) question: every time I shutdown and restart, my system reverts to visual effects setting "none" (i.e. Metacity), and I have to change it manually to "normal" using System > Preferences > Appearance. Any idea how to make that a default setting?

---

