---
title: "apt URLs in Firefox don't work"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by coldReactive on 2009-09-26
Every time I install Ubuntu, apt:// urls don't work in firefox by default. Nor in 3.5 with ubuntuzilla. Is there a package I need to get Firefox to handle them?

---

### Post by marshmallow1304 on 2009-09-26
There's an apturl package, but I thought it was installed by default.  It's probably worth checking though.

---

### Post by coldReactive on 2009-09-26
apturl is installed, but it doesn't work.

---

### Post by SteelCore on 2009-09-26
I just tried apt://flightgear on my 9.04 and it worked.  I don't have anything added to my installation except the 'restricted extras'.

---

### Post by coldReactive on 2009-09-27
> **SteelCore said:**
> I just tried apt://flightgear on my 9.04 and it worked.  I don't have anything added to my installation except the 'restricted extras'.

Why use restricted extras, when I can do the same (and more complete) with the comprehensive multimedia guide thing.

---

### Post by philinux on 2009-09-27
Yeh, apturl is installed by default. Working here. Must be a FF issue. Proxy maybe.

Try this in a terminal.

```
apturl apt:apturl
```

You should get a popup telling you apturl is already installed.

---

### Post by coldReactive on 2009-09-27
> **philinux said:**
> Yeh, apturl is installed by default. Working here. Must be a FF issue. Proxy maybe.

Try this in a terminal.

```
apturl apt:apturl
```

You should get a popup telling you apturl is already installed.

Yep, installed. But firefox has this error:

> Firefox doesn't know how to open this address, because the protocol (apt) isn't associated with any program.

But doing the below...

> Type in "about:config" in the location bar
right click, select New --> String

name of string should be: "network.protocol-handler.app.apt" and set it to apturl

causes a "What program should firefox use to open apt: links?" Dialog that never goes away if I press OK while apturl is selected.

---

### Post by philinux on 2009-09-27
I've just checked in FF prefs>apps and I have an entry for content type apt which uses apturl as the default.

Have you tried it like this apt:apturl in FF. It works without the //s.

---

### Post by coldReactive on 2009-09-27
What a roundabout way of doing things. After adding the **network.protocol-handler.app.apt** I had to go to Preferences > Applications then reset the handler to /usr/bin/apturl by browsing.

Works now. -_-

---

### Post by sisco311 on 2009-09-27
try:
```
sudo apt-get install firefox-3.5-gnome-support
```
or for firefox 3.0:
```
sudo apt-get install firefox-3.0-gnome-support
```

[http://ubuntuforums.org/showthread.php?t=1240210]("http://ubuntuforums.org/showthread.php?t=1240210")

or create a new file:
```
gksu gedit /etc/firefox-3.0/pref/apturl.js
```
for firefox 3.5:
```
gksu gedit /etc/firefox-3.5/pref/apturl.js
```
copy and paste this lines:
```
pref("network.protocol-handler.app.apt","/usr/bin/apturl");
pref("network.protocol-handler.warn-external.apt",false);
pref("network.protocol-handler.app.apt+http","/usr/bin/apturl");
pref("network.protocol-handler.warn-external.apt+http",false);

```
save the file and restart firefox.

if still doesn't work, go to Edit -> Preferences -> Applications tab, search for apt and select apturl in the *action* tab. restart firefox (if needed).

Edit: too late. :)

---

