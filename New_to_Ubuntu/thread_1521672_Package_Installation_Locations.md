---
title: "Package Installation Locations"
date: 2010-07-01
forum: New to Ubuntu
---

### Post by jonny2vests on 2010-07-01
Hi,

Often I install a package, whether via the terminal or a gui, and I have no idea where it is installed.  I have not yet found a log that explicitly tells me where these things go.

For instance, this morning I installed perl-doc-html, which I understand to be be html man pages for perl.  I can't find them.  Often I install a gui driven package, but I have to hunt for the shortcut in the menu bar or I have to create it myself once I've found the executable.  Is there a better way of doing this?

So, in summary, how do I find out where things have been installed?  Is there a log or some other means?

Cheers,

Jon

---

### Post by diesch on 2010-07-01
Select the package in Synaptic, click on the toolbar item "Properties" and go to the "Installed files" tab.

Documentation is usually at /usr/share/doc/<PACKAGENAME>/, for perl-doc-html see  /usr/share/doc/perl-doc-html/html/index.html

---

### Post by jonny2vests on 2010-07-01
Awesome - thanks pal.

---

