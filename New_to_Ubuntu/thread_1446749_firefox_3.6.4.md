---
title: "firefox 3.6.4"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by saintnefarious on 2010-04-04
a friend of mine offered to "sort my laptop" now i have Firefox 3.6.4 installed. i hate it! how do i go back to an earlier version.

---

### Post by EssexEagle on 2010-04-04
> **saintnefarious said:**
> a friend of mine offered to "sort my laptop" now i have Firefox 3.6.4 installed. i hate it! how do i go back to an earlier version.

I don't know myself, but did you mean to mark this thread as solved?  People who might be able to help are unlikely to read it.

---

### Post by Silent Warrior on 2010-04-04
First thing I'd try: Open Synaptic (type 'gksu synaptic' in a terminal if you don't find it in the menus), refresh repositories (might as well look over them for suspicious third-party entries and untick them for this run), find firefox - either 'firefox' or 'mozilla-firefox' - and click its entry so that it is highlighted/highlit. Then click Package (Alt+P) and Force version... to something else. 3.5 or whatever there is.
Did that work?

---

### Post by The Cog on 2010-04-04
As far as I can yell, there is no 3.6.4 yet. Mozilla's web site only offers 3.6.3. Where did you get it from?

---

### Post by lovinglinux on 2010-04-04
Open "System >>> Software Sources >> Other Software" and check if you have a line with **ubuntu-mozilla-daily**, **ubuntu-mozilla-security** or **mozillateam/firefox-stable**. Then go to "System >> Synaptic Package Manager" , find Firefox and mark it for re-installation.

---

### Post by saintnefarious on 2010-04-04
its a pre release version which i dont think they are going to use anyway called namoroka. i found a solution on another thread but thanks anyway to everyone!

---

