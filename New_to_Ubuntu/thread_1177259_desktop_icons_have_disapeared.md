---
title: "desktop icons have disapeared"
date: 2009-06-03
forum: New to Ubuntu
---

### Post by heidipj on 2009-06-03
Hi there,
I just installed Ubuntu Notepad on my Acer Aspire One. (I removed the existing Windows XP). 

The install seemed to go well but the default desktop in the notepad ubuntu version was quite ugly with the open folder layout showing and I prefer the clean desktop with the icons up the top of the screen. So in preferences I changed the desktop and when I restarted I just get a the brown desktop wallpaper with no top ubuntu icons, applications link or login restart options. I can only right click the mouse and get folder options etc. 

Wondering if Ubuntu hasn't recoginised the small size of my screen? Any ideas how to get it to reset and show my icons at the top of the screen?

Thanks
Heidi

---

### Post by stephanvaningen on 2009-06-03
You can verify if it is not just a screen-resolution-thing by pressing Alt-F1: normally this opens the applications-drop-down-menu: does it?

---

### Post by heidipj on 2009-06-03
Tried alt + f1 but nothing happened... Did I mention I am total newbie to Linux?

---

### Post by stephanvaningen on 2009-06-03
You don't need to ;) we're in "Absolute Beginners Talk", right? :)

What now comes is a bit 'techie', but anyway....

Try this:
-Press Ctrl-Alt-F1 (this shows a monochrome text screen with login options)
-Log in with the same account that has the menu bar issue
-Type this command to log out from the X-session:
```
gnome-session-save --kill
```
-Delete the files .gnome, .gnome2, .gconf, .gconfd and .gnome2_private by typing these commands:
```
rm ~/.gnome
rm ~/.gnome2
rm ~/.gconf
rm ~/.gconfd
rm ~/.gnome2_private
```

Now go back to the login screen by pressing Alt-F7

---

### Post by heidipj on 2009-06-03
OK. I seem to have found out what the problem is (but not actually fixed it yet). Apparently this is the 'desktop-switcher' bug and it's documented here: [http://www.ubuntu.com/getubuntu/releasenotes/904#Missing%20GNOME%20panels%20in%20Ubuntu%20Netbook%20Remix%20after%20using%20the%20desktop-switcher%20application]("http://www.ubuntu.com/getubuntu/releasenotes/904#Missing%20GNOME%20panels%20in%20Ubuntu%20Netbook%20Remix%20after%20using%20the%20desktop-switcher%20application")
With the 'solution' here [https://bugs.launchpad.net/desktop-switcher/+bug/349519](https://bugs.launchpad.net/desktop-switcher/+bug/349519)

By 'solution' I mean that there are a lot of replies and I haven't actually fixed it yet but at least if I search for 'desktop-switcher' in the folder manager I can find the shortcut and launch it. If I switch back to 'netbook' mode then my desktop works fine. It's just so ugly!

---

