---
title: "Typing in Japanese"
date: 2010-04-22
forum: New to Ubuntu
---

### Post by ambient007 on 2010-04-22
I would like to set my new ubuntu 9.10 installation up so I can switch between typing in English and Japanese characters.

I have already 'installed' the Japanese language in Language Support with Translations, Input Methods and Extra Fonts boxes checked.

Under windows I had to install an Input Method Editor (IME), do I need to do something similar here? Where are the settings so I can set this up?

---

### Post by benmoran on 2010-04-22
Ok, this is pretty easy but it might not be so obvious. 
Go back to "**Language Support**", and look for where it says "**Keyboard input method system**". Change this to **iBus**. iBus is the input framework. 
Then you can manually start iBus from the System-Preferences menu, or just restart your PC. It will load at startup from now on. 

Next step is to select an imput method. Right click on iBus in the system tray (it probably has an icon that looks like a keyboard), and go to preferences. Then click on the **input method tab**. Select an input method (You can Japanese, **Anthy**. The one with the gold crown) and click add. Feel free to remove the English spell check thing that's installed. 

That should do it.

---

### Post by ambient007 on 2010-04-22
Thanks a lot 

Ok, so I can get it to work in word processor but for some reason I cannot use it here.

---

### Post by ambient007 on 2010-04-22
> **ambient007 said:**
> Thanks a lot 
 
Ok, so I can get it to work in word processor but for some reason I cannot use it here.
 
 
bump?

---

### Post by ambient007 on 2010-04-23
page 3 bump....please help!!
 
ta

---

### Post by Irihapeti on 2010-04-23
> **ambient007 said:**
> Ok, so I can get it to work in word processor but for some reason I cannot use it here.

By this, do you mean it won't work in Firefox?

---

### Post by cjv8888 on 2010-04-23
Have you installed scim? 
After installing, then run SCIM input method setup from the Preference menu. Log out and log in, then you should see the icon at the notification area.

---

### Post by Irihapeti on 2010-04-23
> **cjv8888 said:**
> Have you installed scim? 
After installing, then run SCIM input method setup from the Preference menu. Log out and log in, then you should see the icon at the notification area.

That was going to be my suggestion if iBus can't be made to work. I like Scim myself, but the problem is that development seems to be at a standstill, so I see it as a last resort.

---

### Post by benmoran on 2010-04-23
You know, I had that same problem with Ubuntu 9.04, using SCIM. Japanese input worked everywhere except Firefox. I tried a bunch of stuff, but couldn't fix it short of a reinstall. I don't think the problem lies with iBus or SCIM, but rather with Firefox.

---

### Post by Irihapeti on 2010-04-23
I'm able to use iBus in Firefox in Lucid.&#12288;I didn't use Karmic for very long and it was a while ago, so I don't really remember what happened there.

I've found that installing ibus-anthy and the anthy server, and then choosing the anthy version with the gold crown, not the m17n version, works well. Mind you, I know almost no Japanese &#12395;&#12411;&#12435;&#12372;&#12288;&#26085;&#26412;&#35486; (I'm pretty sure the kanji is correct - not sure about the hiragana.)

---

### Post by cjv8888 on 2010-04-23
&#21487;&#20197;&#29992;

scim does work in Firefox in Karmic.

Just hard to make it show up in the panel.

---

