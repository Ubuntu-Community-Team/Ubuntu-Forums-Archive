---
title: "Hello you either have JavaScript turned off or an old version of Adobe's Flash Player"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2009-09-14
As of Friday, September 11, 2009, I'm getting blocked -or- dissed -whatever - from any site using Flash. I'm referring to both Youtube and GizmoProject (phone call dial pad)

1 - Is there a way to fool these pages into not caring about which Flash player I'm using

2 - Is there a Linux/Ubuntu upgrade if the foregoing doesn't work?

3 - Is this a Microsoft "conspiracy" to annoy non M$ users?

---

### Post by zerhacke on 2009-09-14
Try this.

sudo apt-get install ubuntu-restricted-extras

at a terminal.

OR

Open Synaptics and search for the ubuntu-restricted-extras package.

Install.  Close all Firefox windows.  Open Firefox and navigate to your flash page.

Ubuntu-restricted-extras is a metapackage that installs all kinds of useful stuff for you, including the latest Flash package.

---

### Post by por100pre1 on 2009-09-14
It seems JavaScript is disabled in your browser. Both pages work fine here using Firefox. If using Firefox try checking if JavaScript is enabled. If using FF with NoScript be sure to allow those whole pages.

---

### Post by Mark_in_Hollywood on 2009-09-15
I have the Chrome icon on my desktop.

This was resolved by adding:

/opt/google/chrome/google-chrome **--enable-plugins**

I believe an update from the repositories may have changed this.

Thanks, community.

---

