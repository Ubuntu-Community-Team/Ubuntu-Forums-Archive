---
title: "2 versions of firefox on the same computer?"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by northwestuntu on 2009-04-03
i have firefox 3.08 as my main browser.  would it be possible to have firefox beta 3.5 on here also and have ubuntu keep them both updated without having to keep installing new betas?

also don't want them sharing profiles.  i would like to them to be separate.

thanks

---

### Post by gandaran on 2009-04-03
yes, you can install the mozilla firefox version and still keep the ubuntu firefox and I believe you can also install it in /home/user, this way installing in home would make it easy to update, you just click the update icon in firefox.

---

### Post by northwestuntu on 2009-04-03
what's the easiest way to install the firefox beta?  i doubt there are any debs?

---

### Post by taurus on 2009-04-03
Download the .tar.gz and unpack it in your $HOME.  Then, change to the new directory, firefox, and run it from there.

```
./firefox
```
Also, you can create a launcher on the top panel for the new firefox if you wish.  When you want to use it, just click the icon instead of running it through a terminal.

---

### Post by northwestuntu on 2009-04-03
awesome.  thanks.

---

### Post by gandaran on 2009-04-03
northwestuntu
can you post the download link for the beta, I cant find it!

edit:
okay I found it but I'm disappointed, mozilla's firefox uses the same ubuntu firefox profile and messed up my addons.

---

### Post by taurus on 2009-04-03
> **gandaran said:**
> northwestuntu
can you post the download link for the beta, I cant find it!

[http://quality.mozilla.org/events/2009/apr/14/firefox-35-beta-4](http://quality.mozilla.org/events/2009/apr/14/firefox-35-beta-4)

---

### Post by kanikilu on 2009-04-03
> **gandaran said:**
> northwestuntu
can you post the download link for the beta, I cant find it!

edit:
okay I found it but I'm disappointed, mozilla's firefox uses the same ubuntu firefox profile and messed up my addons.

You've probably already found this out, but you'll want to run the new version with ```
./firefox -ProfileManager
``` to create a new profile for the new version.

---

### Post by ashwinhgtx on 2009-04-03
> **gandaran said:**
> northwestuntu

edit:
okay I found it but I'm disappointed, mozilla's firefox uses the same ubuntu firefox profile and messed up my addons.

Same problem here. How do I keep the two versions of Firefox from sharing profiles? The beta version checks for updates as soon as I start it up.
Also Flash doesn't seem to be working on the beta version.

---

### Post by Bios Element on 2009-04-03
> **ashwinhgtx said:**
> Same problem here. How do I keep the two versions of Firefox from sharing profiles? The beta version checks for updates as soon as I start it up.
Also Flash doesn't seem to be working on the beta version.

Read the post just above yours. You missed it. >.>

---

### Post by gandaran on 2009-04-03
> Also Flash doesn't seem to be working on the beta version
flash and every media plugin is working fine in the new beta profile, if flash doesn't work for you could be due to flash not being installed in the file system, find the libflashplayer.so file in your system and copy to the new beta profile plugins folder.

---

### Post by northwestuntu on 2009-04-05
> **kanikilu said:**
> You've probably already found this out, but you'll want to run the new version with ```
./firefox -ProfileManager
``` to create a new profile for the new version.

so you will need to open up the profile screen everytime to choose between both versions?

the beta can't run independent?

---

