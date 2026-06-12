---
title: "Single-pixel font rendering?"
date: 2011-02-17
forum: New to Ubuntu
---

### Post by J-mz on 2011-02-17
Hopefully a quite simple question, although from looking at older threads, perhaps not.
I have my system font preferences set up to my liking - which is the sharp, thin character rendering that I'm used to from WinXP.  (I think of it as single-pixel - no apparent effects, and characters that aren't thick enough to even look really black.)

So the top panel (clock etc) and system menus are looking good.  "Applications Places System" all look good.  

There's a marked difference though, between these and the characters in Firefox and Thunderbird.  Firefox's own menus, and the text in webpages, are soft and what I call fuzzy.
Thunderbird is different, but also not showing the sharpness I want.

Question: how can I get applications to use the same font rendering as the system is doing?  Open Office looks good - it's own menus, and document fonts are very sharp.

Thanks!  I know there are beaucoup threads around this area, but none seemed directly to address the difference between the system fonts and those displayed by applications.

---

### Post by The Cog on 2011-02-17
The only font adjustment I'm aware of is in System / Preferences / Appearance / Fonts. It sounds as though you want either full hinting or to disable antialiasing. Be warned that Firefox won't change its font rendering until you quit and restart it, which makes comparison difficult - saving screenshots can help there.

---

### Post by J-mz on 2011-02-18
Yes, I'm happy with my system font settings.

It's the webpage, email, and application-menu rendering that's no good in some apps.
Looking at the rendering in WinXP right now: there's no difference between the system menus, the desktop icon names, Firefox's own menus, and this text that I'm writing now.  It's all fine and sharp.

Under 10.10, I haven't worked out how to get that consistency.  I don't understand why the same three apps - Sunbird, Firefox, Thunderbird - *seem* to be using the system fonts under WinXP, but seem not to be doing so under 10.10.

Cheers.

---

### Post by tgalati4 on 2011-02-18
If you want your webpages to look like MS, you need to install ttf fonts:

tgalati4@tpad-Gloria7 ~ $ apt-cache policy ttf-mscorefonts-installer 
ttf-mscorefonts-installer:
  Installed: (none)
  Candidate: 2.6
  Version table:
     2.6 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Packages

To install:

sudo apt-get install ttf-mscorefonts-installer

---

### Post by J-mz on 2011-02-21
Thanks.  It's not that I want webpages to "look like MS" - it's that I want them (and T'bird messages, etc) to look like Ubuntu system menus / desktop icon names, which display sharply.
So while I appreciate your suggestion, I don't get why apps can't just use the same fonts the system menus are using...
Cheers.

---

### Post by J-mz on 2011-03-04
Hmm.  No takers?

It's particularly curious (to me) that it's not just the system menu characters that are sharply displayed, but that the Open Office word processor does fine too, while none of my Mozilla apps look sharp. 

By the way, how is OO able to display Arial and Times New Roman, even though they're not included in the font options?

I think that's beside the point, though.  I've got Firefox and Thunderbird fonts all set to Ubuntu, but Ubuntu font in Open Office looks much better.  So it's not about which font, it's about the display of a given font, from what I can tell.

Cheers.

---

