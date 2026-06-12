---
title: "can't download poker stars"
date: 2010-07-08
forum: New to Ubuntu
---

### Post by beelzebufo on 2010-07-08
I have read around on here and it sounds like you can play on poker stars fairly easily on ubuntu, but I can't seem to download the .exe file.  it just keeps redirecting me to the mac download, how can I get around this?  I have used wine with full tilt and it works just fine.

---

### Post by SpyderBite on 2010-07-09
> **beelzebufo said:**
> I have read around on here and it sounds like you can play on poker stars fairly easily on ubuntu, but I can't seem to download the .exe file.  it just keeps redirecting me to the mac download, how can I get around this?  I have used wine with full tilt and it works just fine.

Download and Install wine from the repos. Go to the PokerStars website and download the Windows installer and save it. Go to your downloads, right click on the pokerstars install .exe and choose install with Wine (or something to that tune).

You're ready to rock.. Complete with a desktop shortcut and all.. I play PokerStars every night in Ubuntu with zero problems except that it doesn't play nice in Full Screen mode. :)

Enjoy.. and may your hand suck when you're at my table! ;)

---

### Post by beelzebufo on 2010-07-09
thanks man, I know how to use wine, I had ft working, now it's not for some reason, but that's a different issue, I can't dl the .exe file from pokerstars is what the problem is, can't figure out why... I go to ps.com and click their dl link, it takes me to the mac dl page, where there is a link to the windows dl page, which I click on, then I click the download software link with the .exe file and it just takes me back to the mac dl page... I don't get it

---

### Post by marshmallow1304 on 2010-07-09
They're probably trying to be clever with OS detection and it's not working very well.  Right-click the Windows download link and click "Copy Link Location".  Open Applications->Accessories->Terminal.  Run

```
wget [Ctrl+Shift+v]
```

When it's done, the file will be something like download_...=.cgi.  Rename it to PokerStarsInstall.exe then run with Wine.

---

### Post by SunnyRabbiera on 2010-07-09
Install user agent switcher for firefox and make it identify as IE

[https://addons.mozilla.org/en-US/firefox/addon/59/](https://addons.mozilla.org/en-US/firefox/addon/59/)

This also helps for some sites that like IE only.

---

### Post by beelzebufo on 2010-07-09
that worked perfect marshmallow, thanks a lot

---

