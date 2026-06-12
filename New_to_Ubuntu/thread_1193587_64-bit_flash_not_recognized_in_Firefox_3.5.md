---
title: "64-bit flash not recognized in Firefox 3.5"
date: 2009-06-21
forum: New to Ubuntu
---

### Post by jbrown96 on 2009-06-21
I have Firefox 3.5 (beta 4) installed on 64-bit Kubuntu 9.04. I've used the 64-bit flash alpha ([download link]("http://labs.adobe.com/downloads/flashplayer10.html")) with a lot of success in the past; it works very well for video. However, I can't get it to work anymore.

Here's what I did
1) ```
sudo apt-get remove flashplugin-nonfree flashplugin-installer
```
2) Restarted firefox and verified at youtube that flashplayer is not installed
3) uncompressed the tar ball from adobe and moved the plugin into .mozilla/firefox-3.5/plugins/ and .mozill/firefox/plugins/ (just to be safe)

It seems like flash still isn't being recognized. Is there something else to I need to do to get it to work?

Thanks.

---

### Post by drs305 on 2009-06-21
Try copying the libflashplayer.so file to ~/.mozilla/plugins. You may have to make the plugins subfolder first.

Added: With FF 3.5, on my installation it appears the file needs to be placed in **[COLOR="DarkRed"]/usr/lib/mozilla/plugins[/COLOR]**.

---

### Post by jbrown96 on 2009-06-22
Ahaa. That did it. I thought it had to be a plugins folder inside firefox, but it's just in .mozilla

---

### Post by compu73rg33k on 2009-06-28
I copied libflashplayer.so to ~/.mozilla/plugins but the plugin is still not showing. Any other ideas?

Both plugins/ and libflashplayer.so have permissions of 755

---

### Post by drs305 on 2009-06-28
> **compu73rg33k said:**
> I copied libflashplayer.so to ~/.mozilla/plugins but the plugin is still not showing. Any other ideas?

Both plugins/ and libflashplayer.so have permissions of 755

compu73rg33k,

I checked my new FF 3.5 installation and found that on my installation FF 3.5 now needs *libflashplayer.so* in ***[COLOR="DarkRed"]/usr/lib/mozilla/plugins[/COLOR]***.  

Just for reference, I also now find it in:
*/usr/lib/firefox-addons/plugins/* and 
*/usr/lib/firefox/plugins/* 
although I renamed these two and FF 3.5's flash still worked fine.

---

### Post by philinux on 2009-06-28
> **compu73rg33k said:**
> I copied libflashplayer.so to ~/.mozilla/plugins but the plugin is still not showing. Any other ideas?

Both plugins/ and libflashplayer.so have permissions of 755

```
sudo updatedb

then

locate libflashplayer.so
```

---

### Post by compu73rg33k on 2009-06-28
> **philinux said:**
> ```
sudo updatedb

then

locate libflashplayer.so
```

I think you misunderstood me. I copied the plugin to the directory correctly, but for information's sake here's the results of locate libflashplayer.so since it still doesn't work when I put it in /usr/lib/mozilla/plugins

```

**$ locate libflashplayer.so**
/home/me/.mozilla/plugins/libflashplayer.so
/home/me/Desktop/firefox/plugins/libflashplayer.so
/usr/lib/browser-plugins/libflashplayer.so
/usr/lib/firefox/plugins/libflashplayer.so
/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/iceweasel/plugins/npwrapper.libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so

```

---

### Post by clicks on 2009-06-29
Have you checked the platform of your browser? An 32bit Firefox can't execute 64bit Plugins, regardless of the underlying CPU capabilities. Enter **about:buildconfig** in your address bar and have a look at the build platform target - the Mozilla Firefox packages are compiled against i686 (32bit).
In this case you can simply install the 32bit version of Flash and it will work.

---

### Post by patrick2901 on 2009-06-30
I had the same promblem a few minutes ago - the following solution worked for me on kubuntu 9.04 amd64:
[http://blogue.q-be.ca/lang/en/2009/06/03/firefox-flash-player-ubuntu/](http://blogue.q-be.ca/lang/en/2009/06/03/firefox-flash-player-ubuntu/)

These were my steps to upgrade from Firefox 3.0 to 3.5:

1. Downloaded Firefox 3.5final from official site: [www.getfirefox.com](www.getfirefox.com) (.tar.gz)
2. Uninstalled the old Firefox 3.0 via kpackagekit in order to install the new version.
3. $ sudo chown patrick:users /usr/local/bin (is this a security problem!? I don't know)
4. Extracted the complete archive into /usr/local/bin using ark - a "firefox" folder was created below.
5. Modified my existing desktop icon, pointing to "/usr/local/bin/firefox/firefox %u" now.
6. Doubleclicked the icon and entered youtube - flash was not available... Closed The browser.
5. Maybe this step was not required, but I tried it before I found the final solution: uninstalled the packages "flashplugin-installer" and "flashplugin-nonfree", then re-installed both. Didn't work.
6. $ sudo ln /usr/lib/flashplugin-installer/libflashplayer.so /usr/local/bin/firefox/plugins/libflashplayer.so
8. Doubleclicked the firefox icon and have fun now ;)

---

### Post by ilautar on 2009-07-03
Do not do step 3, you mess up your permissions. If this is a multi-user/service machine, you will have problems (actually, you will probably have them anyways).

You can install FF to your home folder w/o changing ownership of system files.

Put libflashplugin.so to /usr/lib/browser-plugins/, works for me. But I use x64 flash with x64 FF 3.0, 3.5 has not been precompiled as x64 yet (at least I cannot find it).

The one on getfirefox is NOT compiled for x64 (AMD64), 64-bit flash will not work.

---

