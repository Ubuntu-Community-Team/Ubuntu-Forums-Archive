---
title: "FireFox shuts down unexpectedly"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by jfluet on 2009-01-24
this started happening today, it seems to happen every time i open a link FF closes unexpectedly , mostly when i go to torrent sites like thepiratebay or isohunt. when i reopen FF i try to restore section but it crashes right away. i tried opening FF in the terminal and it give me.

 failed to initialize shared library /usr/lib/firefox-addons/plugins/libflashplayer.so [libnss3.so: cannot open shared object file: No such file or directory]
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue vari able 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
GCJ PLUGIN: thread 0x805e128: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x805e128: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x805e128: NP_GetValue
GCJ PLUGIN: thread 0x805e128: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x805e128: NP_GetValue return
GCJ PLUGIN: thread 0x805e128: NP_GetValue
GCJ PLUGIN: thread 0x805e128: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x805e128: NP_GetValue return

i also opened port 6881 (i think it was) today could this effect it?
i am running Ubuntu H H 8.04 with FF 3.0 i also have adobe flash player 10.
any ideas???
~~~~~~~~~~~~Edit~~~~~~~~~ 
ok so this seems only to happens we i go to torrent sites, and its driving me nuts

---

### Post by WatchingThePain on 2009-01-24
Hi,
You might try disabling any extensions or plug-ins to see if that helps.
Opening another port won't affect firefox. Is 6881 for utorrent? because that would of course slow browsing down, but not damage the browser.

---

### Post by jfluet on 2009-01-24
> **WatchingThePain said:**
> Hi,
You might try disabling any extensions or plug-ins to see if that helps.
Opening another port won't affect firefox. Is 6881 for utorrent? because that would of course slow browsing down, but not damage the browser.

what command do i use to disable plug-ins?
and 6881 is for BitTorrent, is UTorrent better cuz i like BitTorrent?

---

### Post by WatchingThePain on 2009-01-25
In firefox Click the 'tools', then 'Add-ons' Then theres a section for extensions and another for plugins. If they contain any plugins or extensions right click on the plugin and choose disable then restart Firefox.

P.S. If Firefox wont even start then
1. Click start button 
2. All programs 
3. Mozilla Firefox 
4. Mozilla Firefox (safe mode) 
This way if your Firefox won't start at all you can use it in safe mode and disable/uninstall extensions that caused the problem.

---

### Post by jfluet on 2009-01-25
There is no start button in Linux/ubuntu. and i dont have windows. but disabling add-ons/plugins worked! i think is was icedtea or shockwave that was causing the problem,
thanks for the help

---

### Post by WatchingThePain on 2009-01-25
Excellent, silly me I am an ex windows user and the brainwashing has not worn off yet!. Just to close if you ever want to try a different browser Opera is the best I have found.

---

### Post by cpinokc on 2009-01-27
I seem to be having the exact same problem, but I can't open it up long enough to change the plugin settings. Is there a way I can disable them without opening it up?

I've been using Opera and really like it, but I still like Firefox better, and there are so many sites that allow FF but not O. :(

---

