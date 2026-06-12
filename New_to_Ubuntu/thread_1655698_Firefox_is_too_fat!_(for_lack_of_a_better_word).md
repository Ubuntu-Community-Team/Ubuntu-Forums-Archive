---
title: "Firefox is too fat! (for lack of a better word)"
date: 2010-12-30
forum: New to Ubuntu
---

### Post by Arwen17evenstar on 2010-12-30
The top toolbars in ubuntu firefox always takes up more screen area than the windows version.
[windows screenshot.](http://img560.imageshack.us/img560/3375/windows.jpg)
[ubuntu screenshot](http://img407.imageshack.us/img407/1162/ubuntub.jpg)
this one is KDE, but I use Gnome as well and it also takes up a lot of area.

Using smaller icons in firefox doesn't help. It's the height of the tabs and toolbars themselves.

What are some possible ways to get ubuntu firefox looking more like windows firefox aka taking up less screen space?


This has likely already been asked somewhere in the vast spaces of the net. But I don't know where to look or what key words to use to find what I need.

---

### Post by Vi3tHoneyX on 2010-12-30
[COLOR="DarkRed"]They look like the same size in those screen shots of yours... [/COLOR]**=/**

---

### Post by Version Dependency on 2010-12-30
Are you using the same fonts in both Windows and Ubuntu...and the same size?

---

### Post by Wtower on 2010-12-30
> **Vi3tHoneyX said:**
> [COLOR=DarkRed]They look like the same size in those screen shots of yours... [/COLOR]**=/**

Actually they don't, for me at least. And to be perfectly honest with you, although it doesn't feel important to me, I do agree. But I guess it is a matter of toolbar height in gnome or something, and possibly is different with other themes installed (haven't checked).

---

### Post by Arwen17evenstar on 2010-12-30
> **Vi3tHoneyX said:**
> [COLOR=DarkRed]They look like the same size in those screen shots of yours... [/COLOR]**=/**

they're not. 
ubuntu is  taking up almost two toolbars more space (height-wise) compared to windows.

> **Version Dependency said:**
> Are you using the same fonts in both Windows and Ubuntu...and the same size?
I'm using the default settings for windows firefox and the default settings for ubuntu firefox. I haven't changed anything.

I just tried setting the font smaller in ubuntu and all that does it make the text smaller, but doesn't change the height.


I tried this to change the fonts -> [font changer add-on]("https://addons.mozilla.org/af/firefox/addon/162063/")
but once again it just makes the text smaller without actually changing the height of the toolbar.

---

### Post by Version Dependency on 2010-12-30
> **Arwen17evenstar said:**
> I'm using the default settings for windows firefox and the default settings for ubuntu firefox. I haven't changed anything.

That may be the difference.  See if setting Ubuntu to the same font as Windows helps (assuming you have the Microsoft core fonts installed on Ubuntu).

---

### Post by inobe on 2010-12-30
on any platform i use f11, i can't stand looking at that stuff :lol:

if i want another tab, i simply hover above and it magically appears.

---

### Post by inobe on 2010-12-30
> **Version Dependency said:**
> That may be the difference.

or the difference could be the version of firefox ?

---

### Post by mcduck on 2010-12-30
> **Arwen17evenstar said:**
> they're not. 
ubuntu is  taking up almost two toolbars more space (height-wise) compared to windows.


I'm using the default settings for windows firefox and the default settings for ubuntu firefox. I haven't changed anything.

I just tried setting the font smaller in ubuntu and all that does it make the text smaller, but doesn't change the height.


I tried this to change the fonts -> [font changer add-on]("https://addons.mozilla.org/af/firefox/addon/162063/")
but once again it just makes the text smaller without actually changing the height of the toolbar.
If you haven't resized the images, they seem to be pretty much the same size give or take about 10 pixels.. :D

Anwyay, set a smaller font size (keep in mind that if you have icons in the toolbar, then the toolbar will always stay large enough to fit those icons, so setting font size smaller than the icon size is would make no difference), install more compact GTK theme, move stuff up to the menu bar (I usually place url bar & search bar there, and move bookmarks to the main toolbar, whic allows me to disable the bookmarks toolbar).

Setting the toolbar icon size to compact & icons only will save you almost a full toolbars height of space as well.

And perhaps make your tab bar scrollable instead of what you are using now. That will remove one more toolbar from your setup.

You can also set Gnome to use compact toolbars, which reduces the icon size slightly making the toolbars a bit smaller. I'm not sure if that affects Firefox, though, as it's not actually a GTK application.

---

### Post by DavidRaid on 2011-01-30
I had the same issue as you.
I managed to 'fix' it.

Go into your user folder and then into .mozilla (you might need to 'show hidden files' in the menu), then into your profile folder (it'll be named after a combination of numbers and letters.default) then into the 'chrome' folder.

Once here, edit the file 'userChrome.css', and if it isn't there, create an empty file and name it that. Close Firefox first and then open it in gedit and delete whatever is in it, then paste

#PersonalToolbar {
height: 22px !important;
margin-top: 1px !important;
margin-bottom: -1px !important;
padding: 0px !important;
}
.bookmarks-toolbar-items {
margin-top: -6px !important;
margin-bottom: 7px !important;
}

Finally, save and open Firefox.

Your bookmarks bar will be as thin as the one in Windows is. I experimented until it was almost pixel for pixel.

---

### Post by Vaphell on 2011-01-30
if you aim at saving vertical screen estate specifically you can save a lot of space with addons and a bit of creativity.
Tab Kit allows you to have tabs in tree form on the left (on widescreen displays the horizontal space is much less valuable so it makes perfect sense to have tabs on the side) => you save 1 row of space.
Another thing you can do is to move stuff around in customize mode. You can actually move layout items to the menu bar (the one with File Edit View...) - i have my bookmarks there so another row is saved.

---

### Post by NightwishFan on 2011-01-30
Has to be the fonts, if I set my fonts to 9 it shrinks like a toolbar length, and the fonts in windows are always tiny.
Edit: The QT theme DOES seem to waste a little bit of space as well. Seems ok on gtk.

---

### Post by MickS on 2011-01-30
A good add on to try is Hide GUI Bars, that gets rid of the lot, I use it occasionally on my netbook  [https://addons.mozilla.org/en-US/firefox/search/?q=hide+gui+bars&cat=all&x=0&y=0](https://addons.mozilla.org/en-US/firefox/search/?q=hide+gui+bars&cat=all&x=0&y=0) The keys to press are Ctrl+Shift+A. I have put that in because if you download and install it, when you restart Firefox you will find them all gone and toggling that combination brings them back.


Mick

---

### Post by chriswyatt on 2011-01-30
I set all my fonts to 8 as the default size was waaaaay too chunky for my liking.

---

### Post by DavidRaid on 2011-01-30
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=182360&stc=1&d=1296430117[/IMG]

Here's what the bookmark bar looks like with the chrome edit I suggested earlier. It's just as thin as Windows now.

---

### Post by walt.smith1960 on 2011-01-30
How about a compact theme, like [Littlefox for Firefox]("https://addons.mozilla.org/en-US/firefox/addon/littlefox-for-firefox/") ?  Or similar more to your taste?

---

### Post by Frogs Hair on 2011-01-30
Two colors of the same theme , there are Personas that are thiner , but it takes time to find them.
[https://addons.mozilla.org/en-US/firefox/addon/bloomind-ft-graphite/](https://addons.mozilla.org/en-US/firefox/addon/bloomind-ft-graphite/)
[https://addons.mozilla.org/en-US/firefox/addon/bloomind-ft-deepdark/](https://addons.mozilla.org/en-US/firefox/addon/bloomind-ft-deepdark/)

---

### Post by DavidRaid on 2011-01-31
If you are looking for a way to slim Firefox down, I'd definately try one of the addons and/or personas that've been suggested here, but since you specifically said you would like it thin 'like Windows' then I'm taking that to imply you don't want to lose toolbars.

I'd suggest eFirefox by seahorsepip [https://addons.mozilla.org/en-US/firefox/addon/efirefox/]("https://addons.mozilla.org/en-US/firefox/addon/efirefox/") and the bookmarks toolbar tweak I posted. The bookmarks bar is the only toolbar that is different from the windows version, I've compared screenshots and the other toolbars are more or less the same heights.

---

### Post by philinux on 2011-01-31
Addon "Classic Compact" does the trick for me.

---

### Post by bwestover on 2011-01-31
If minimalist is your thing, try Chrome.

Faster, Lighter, always up to date and works 99% of the time for me. The other 1%, I drag out FF and suffer through its MASSIVE toolbars ;)

---

### Post by weedeater64 on 2011-01-31
Really?? Your griping about real estate with all that crap at the top of your windows window?

How about you right click up there and clean things up to suit?

---

### Post by arnab_das on 2011-01-31
okay do something.

1. if u dont need it, remove your bottom panel. you can right click and then hit delete panel.

2. second, right click on your top panel and then go to panel properties. try autohide or show hide options there.

this will result in a substantial real estate increase. try it out.

---

### Post by hansolo4949 on 2011-01-31
Okay, from what I've seen, the problem is NOT firefox, but Ubuntu. The reason firefox is "fatter" in Ubuntu is because the top menu bar on ANY application (the one with, close, minimise, maximise, someone please tell me if there is a better term for this) is larger than windows'. So, you will have to change the top menu bar (for lack of a better word) settings, in Ubuntu, or change the theme, so that it will be smaller.


Hope that helps!

---

