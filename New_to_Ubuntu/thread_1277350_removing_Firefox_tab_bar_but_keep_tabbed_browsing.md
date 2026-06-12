---
title: "removing Firefox tab bar but keep tabbed browsing"
date: 2009-09-28
forum: New to Ubuntu
---

### Post by coldReactive on 2009-09-28
How can I make the tab bar disappear when I have multiple tabs? Exa: I want to be only able to switch tabs via CRTL+Tab. I don't want a userChrome method, because it's too hard for me to remember to back that up every time, plus, I go between windows and ubuntu a lot.

---

### Post by lovinglinux on 2009-09-28
I'm afraid you can't do that. Nevertheless, you could install [Stylish](https://addons.mozilla.org/en-US/firefox/addon/2108) and create a script to reduce the height of the tab to zero. I'm not sure this is possible, but there are themes and scripts that modify the tabs shape, so I guess you could try it.

If you don't want to use Stylish, you could create a userChrome.css file instead.

[http://lifehacker.com/software/firefox/geek-to-live--consolidate-firefoxs-chrome-210542.php](http://lifehacker.com/software/firefox/geek-to-live--consolidate-firefoxs-chrome-210542.php)
[http://lifehacker.com/301520/best-firefox-userchromecss-tweaks](http://lifehacker.com/301520/best-firefox-userchromecss-tweaks)

---

### Post by CuddlyCombine on 2009-09-28
You could hide it by downloading the FoxTab addon for Firefox; however, that brings on complications of its own (namely, the tabbing process becomes akin to Vista's method). That's the only way I know of aside from the above method.

---

### Post by davidmj10 on 2009-09-28
If you do figure out how to do that I would definitely like to hear how it is done.

---

### Post by lovinglinux on 2009-09-28
Complementing my previous post...

[Here](http://forums.mozillazine.org/viewtopic.php?f=7&t=11688&start=0) you can find instructions on how to set the tab hight. Unfortunately, is not that simple. I reduced the tab height and tab text size to zero, but the tabs are still displayed.

Nevertheless, I have found an extension that hides the tab bar. I haven't tried it tho.

[Hide Tabbar 0.7.2 ](https://addons.mozilla.org/en-US/firefox/addon/12716)

---

### Post by coldReactive on 2009-09-28
> **lovinglinux said:**
> Complementing my previous post...

[Here](http://forums.mozillazine.org/viewtopic.php?f=7&t=11688&start=0) you can find instructions on how to set the tab hight. Unfortunately, is not that simple. I reduced the tab height and tab text size to zero, but the tabs are still displayed.

Nevertheless, I have found an extension that hides the tab bar. I haven't tried it tho.

[Hide Tabbar 0.7.2 ](https://addons.mozilla.org/en-US/firefox/addon/12716)

hide tabber still doesn't hide the bar itself, there's still a large blank space.

I don't know how to create stylish stuff though.

---

### Post by philinux on 2009-09-28
Works here by doing this in prefs.

---

### Post by coldReactive on 2009-09-28
> **philinux said:**
> Works here by doing this in prefs.

Have to install tab mix plus, thanks. Oh and also, if you have stylish, and it is editing the tab bar, then you will have a blank area even if you set it that way, philinux.

---

