---
title: "Update Manager-help decipher"
date: 2011-03-31
forum: New to Ubuntu
---

### Post by bk60544 on 2011-03-31
>>When I use Update Manager and check for updates, I get the message "Failed to download repository information".  When I get details, the following appears:
W:Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/maverick/Release.gpg)  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.getdeb.net/dists/lucid-getdeb/games/source/Sources.gz](http://archive.getdeb.net/dists/lucid-getdeb/games/source/Sources.gz)  404  Not Found
, W:Failed to fetch [http://archive.getdeb.net/dists/lucid-getdeb/games/binary-i386/Packages.gz](http://archive.getdeb.net/dists/lucid-getdeb/games/binary-i386/Packages.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.
>>Can someone please explain the above, and how to correct.
THANKS!

---

### Post by Locke_99GS on 2011-03-31
These errors shouldn't prevent you from performing an update, it is simply letting you know that there were problems checking certain repositories.

The first warning about the sevenmachine ppa looks odd to me. It is looking for a hostname "ppa.launchpad.net:http" which is all sorts of wrong. I wouldn't know where to begin.

The other two are because the files or the repo doesn't exist. I thought that getdeb stopped working last year?? I may be wrong. 

Simplest method to resolving these warnings is to remove these repositories from your sources.list. (or disable them in the software srouces application)

---

### Post by bk60544 on 2011-03-31
Thanks for the reply Locke_.  "Remove repositories...?"  This is the "Absolute Beginner" section.  A bit more guidance, please.

---

### Post by Blasphemist on 2011-03-31
This may be the only or even best way to remove repositories but try this. Launch the Synaptic package manager, select repositories from the settings menu. On the other software tab look for the repositories in your error. Highlight and remove.

---

### Post by bk60544 on 2011-04-02
Thanks Blas.  Looks like your suggestion works!!  Will mark thread SOLVED.

---

