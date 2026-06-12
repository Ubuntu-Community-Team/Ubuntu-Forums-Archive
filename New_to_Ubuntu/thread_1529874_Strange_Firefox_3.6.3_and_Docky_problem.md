---
title: "Strange Firefox 3.6.3 and Docky problem"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by lmellor on 2010-07-12
When clicking the firefox button on docky I am presented with a second icon which has no icon and claims the window title to be 'Shiretoko Web Browser'.
The original icon (which worked fine prior to 3.6.6) has the title 'Firefox Web Browser'.

Would anybody be so kind as to shed any light upon this phenomena? I am baffled!

Thanks in advance.

---

### Post by lmellor on 2010-07-12
I have fixed it myself...

I created a new launcher on the desktop named firefox.desktop which contained the following code.

```
[Desktop Entry]
Categories=Application;Internet;Network;WebBrowser;
Comment=Browse the World Wide Web
Exec=firefox %u
GenericName=Web Browser
Icon=/usr/share/pixmaps/firefox.png
MimeType=text/html;text/xml;application/xhtml+xml;application/xml;application/vnd.mozilla.xul+xml;application/rss+xml;application/rdf+xml;image/gif;image/jpeg;image/png;
Name=Firefox Web Browser
NoDisplay=false
StartupNotify=true
StartupWMClass=Firefox
Terminal=false
Type=Application
Version=1.0
X-MultipleArgs=false
```

I then dragged this to docky (after having removed my previous launcher)

fired it up from there, it seemed to work.

:)>

---

### Post by lmellor on 2010-07-15
hmmm, the problem returned after a restart, how odd. Any ideas?

---

### Post by Muflon on 2010-08-18
Having the same problem here. Clicked on the Docky Firefox icon to load and then the question mark icon is displayed.

Muflon

---

### Post by Muflon on 2010-08-21
I have fixed my Firefox/Question Mark icons problem.

In gconf-editor the /apps/docky-2/Docky/Interface/DockPreferences/Dock1/Launchers had an entry for Firefox of file:///usr/share/applications/firefox.desktop

I searched for other files that contained the terms 'firefox' and 'desktop' on my system and found .local/share/applications/firefox-3.0.desktop

I renamed the firefox-3.0.desktop file and the problem was fixed.

I have no idea what the purpose of these desktop files are, so I would advise caution if you try the same thing.

Muflon

---

### Post by QuickBrownFox on 2010-09-04
Thank you so much Muflon. I have finally solved this problem with the following steps

1. Search for "firefox" in the home directory.
2. Delete any results ending in ".desktop".
3. Create a single launcher if required.

---

