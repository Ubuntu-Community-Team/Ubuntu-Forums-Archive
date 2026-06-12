---
title: "Finding libraries version"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by Eniac on 2009-03-12
Hi guys, I'm having a problem installing lightning for thunderbird on ubuntu.

so im checking the system requirements and they mention the version of the libraries it needs.

my question is, being a total ubuntu noob, how do i find out the actual version of the libraries i need ?

This is the sysreqs for lightning:
Linux kernel - 2.2.14 or higher with the following libraries or packages:

    * glibc 2.3.2 or higher
    * XFree86-3.3.6 or higher
    * gtk+2.0 or higher
    * fontconfig (also known as xft)
    * libstdc++5
      (Many modern Linux distributions only package libstdc++6, which is incompatible with Lightning. Therefore please install the package "libstdc++5" or "compat-libstdc++" on your system before installing Lightning)


ive tried searching the synaptic package man. for glibc and its only finding the docs and the source (and neither are installed)

is there a more command-line way of finding out if its installed ?

Thanks.

---

### Post by agim on 2009-03-12
How are you trying to install lightning/thunderbird? Are you using apt, or installing from source?

sudo apt-get install thunderbird should take care of any dependencies, same for lightning.

---

### Post by Eniac on 2009-03-12
*clunk* why did i not look into synaptic first for lightning.

anyway, i was installing for the downloaded .xpi file and it didnt work.

i tried with sudo apt-get install lightning and the installation worked but lightning doesn't work in TB. i get the same error message :

Error: installLocation has no properties
Source File: file:///usr/lib/thunderbird/components/nsExtensionManager.js
Line: 4034

i did some research on that and only could find a bug entry that says to delete/rename extension.rdf, which i did, and it didn't fix it.

i could try deinstalling TB, then re-installing from apt-get, then re-install lightning as well ?

and that doesn't answer my first question, how do i find out my system has the proper libraries required by lightning ?

Thanks.

---

### Post by agim on 2009-03-12
To find out what you have installed, you can also go into synaptic and search the package. 
To get things working, you may have to uninstall all of the things you installed trying to get it to work initially. Then remove thunderbird and lightning completely, and reinstall from synaptic.

Also, this may help.
[http://support.mozilla.com/tiki-view_forum_thread.php?comments_parentId=216761&forumId=1](http://support.mozilla.com/tiki-view_forum_thread.php?comments_parentId=216761&forumId=1)

---

### Post by Eniac on 2009-03-12
yeah, the article you mentionned is the one i looked at.

i uninstalled tb and lightning, then reinstalled from synaptic and it still didn'T work, plus, i had a new error message :)

but looking at my addons, i think i found out what is going on, without being able to fix it ATM. I recently migrated from Winxp to Ibex and made a backup of my profile and mail from TB in windows. Then i pointed TB in Ibex to the profile i had in windows. Everything works, i got my old mails and all, but now its making me suspect the addons arent working because some files are meant for windows in there.

ill google around to try to find out how i can keep all my email account config and old emails and fix that problem.

Thanks for your help

---

