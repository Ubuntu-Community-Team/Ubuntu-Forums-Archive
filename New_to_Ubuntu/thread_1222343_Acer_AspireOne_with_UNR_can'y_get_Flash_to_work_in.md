---
title: "Acer AspireOne with UNR can'y get Flash to work in Opera"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by PureRicanGringo on 2009-07-24
For some reason I can't flash to work in Opera. I have verified that it is intalled in synaptic. I even re-installed it, and I have verified that it works in Firefox. I have made sure that plugins are enabled, but I am stuck.

---

### Post by darolu on 2009-07-24
Yeah this is a common Opera problem, you have to copy the libflashplayer.so file from /usr/lib/mozilla/plugins to /usr/lib/opera/plugins/
```
sudo cp /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/opera/plugins/
```

Note: depending on how you install it, the file's name may be: flashplugin-alternative.so

---

### Post by PureRicanGringo on 2009-07-25
> **darolu said:**
> Yeah this is a common Opera problem, you have to copy the libflashplayer.so file from /usr/lib/mozilla/plugins to /usr/lib/opera/plugins/
```
sudo cp /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/opera/plugins/
```

Note: depending on how you install it, the file's name may be: flashplugin-alternative.so

Man, thank you so much for the advice. I think we are on the right track, but I still can't get flash to work for me in Opera. I tried pasting both options you gave me into terminal, the first time came back saying "no such" something or other but the second version seemed to go OK, but when I went to the adobe test page, still no go on the Flash portion. Any ideas?

---

### Post by k3lt01 on 2009-07-25
Do a manual search for the file to confirm it is there and its name. Once you have done that modify the terminal line to suit and give it a go.

---

### Post by darolu on 2009-07-26
> **PureRicanGringo said:**
> Man, thank you so much for the advice. I think we are on the right track, but I still can't get flash to work for me in Opera. I tried pasting both options you gave me into terminal, the first time came back saying "no such" something or other but the second version seemed to go OK, but when I went to the adobe test page, still no go on the Flash portion. Any ideas?
Are you using the latest Opera version? Try installing the one you download from [http://www.opera.com/browser/download/](http://www.opera.com/browser/download/) it has a Ubuntu binary (.deb file) so you only have to double click it to install.

---

