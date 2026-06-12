---
title: "xubuntu text so small it is unreadable"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by Bavitz on 2009-07-08
Hi,

I am very new to ubuntu and recently installed xubuntu hardy heron on my aging HP vectra P4. All was going well untill I attempted to change the resolution of my monitor and mess around with the text sizes. I have managed to resize most of the text so that it is a good size, but the 'taskbar' menus are miniscule - so small I cannot read the list of applications even with a magnifying glass, I can see the icons, just not the text descibing what they are. All other text is fine. I am using an ATI radeon graphics card with dual monitors. Can anyone help please?

---

### Post by winotree on 2009-07-08
I'm assuming you're using Firefox as your browser?  If so increase your *minimum font size* in Preferences | Content | Fonts and Colors | Advanced.  Hope this helps you.  If you've already tried this perhaps it'll help someone else.  ;)

EDIT - also check Settings | Appearance | Fonts as this seemed to me to be a more system-wide change.  Speaking of which you could add this 

/* global font */
* {
  font-size: 9pt !important;
  font-family: sans-serif !important; 
}

to your userChrome.css in your Firefox profile -- changing the font size and font family to something more suitable to your tastes.

---

### Post by Bavitz on 2009-07-09
Thanks Winotree,

I set my minimum font size and upon restart the problem was resolved :p:p

Bavitz

---

