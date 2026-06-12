---
title: "How many Firefox things do I need?"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by myolbug on 2009-07-12
I thought I would share the results of *aptitude search firefox*.  It seems that I have a lot of results and I would love to know how to clean this up.  What are dummy packages?
Also, I have FF 3.1 and 3.5 and I don't know how to merge them together.  I installed 3.5 as a beta and it just upgraded that and not 3.1



i   firefox                         - meta package for the popular mozilla web b
i A firefox-3.0                     - safe and easy web browser from Mozilla    
i A firefox-3.0-branding            - Package that ships the firefox branding   
p   firefox-3.0-dev                 - Development files for Mozilla Firefox     
p   firefox-3.0-dom-inspector       - dummy upgrade package for firefox-3.0-dom-
p   firefox-3.0-gnome-support       - Support for Gnome in Mozilla Firefox      
p   firefox-3.0-venkman             - dummy upgrade package for firefox-3.0-venk
p   firefox-3.1                     - dummy upgrade package for firefox-3.1 -> f
p   firefox-3.1-branding            - dummy upgrade package for firefox-3.1 -> f
p   firefox-3.1-dbg                 - dummy upgrade package for firefox-3.1 -> f
p   firefox-3.1-dev                 - dummy upgrade package for firefox-3.1 -> f
p   firefox-3.1-gnome-support       - dummy upgrade package for firefox-3.1 -> f
i A firefox-3.5                     - safe and easy web browser from Mozilla    
i   firefox-3.5-branding            - Package that ships the firefox branding   
i   firefox-3.5-dbg                 - firefox-3.5 debug symbols                 
i   firefox-3.5-dev                 - Development files for Mozilla Firefox     
i   firefox-3.5-gnome-support       - Support for Gnome in Mozilla Firefox      
p   firefox-dev                     - meta package pointing to the latest develo
p   firefox-dom-inspector           - meta package for firefox-dom-inspector    
p   firefox-gnome-support           - meta package pointing to the latest gnome-
p   firefox-granparadiso            - dummy upgrade package for firefox-granpara
p   firefox-granparadiso-dev        - dummy upgrade package for firefox-granpara
p   firefox-granparadiso-dom-inspec - dummy upgrade package for firefox-granpara
p   firefox-granparadiso-gnome-supp - dummy upgrade package for firefox-granpara
p   firefox-greasemonkey            - firefox extension that enables customizati
p   firefox-launchpad-plugin        - Launchpad firefox integration             
p   firefox-libthai                 - dummy upgrade package for firefox-libthai 
p   firefox-linky                   - firefox extension to handle web and image 
p   firefox-sage                    - Lightweight RSS and Atom feed reader for F
p   firefox-showcase                - Showcase provides a new way to manage your
p   firefox-trunk                   - dummy upgrade package for firefox-trunk ->
p   firefox-trunk-dev               - dummy upgrade package for firefox-trunk ->
p   firefox-trunk-dom-inspector     - dummy upgrade package for firefox-trunk ->
p   firefox-trunk-gnome-support     - dummy upgrade package for firefox-trunk ->
p   firefox-trunk-venkman           - dummy upgrade package for firefox-trunk ->
p   firefox-ubuntu-it-menu          - Firefox extension for a quick browse of Ub
p   firefox-webdeveloper            - web developer extension for the Firefox we
p   mozilla-firefox-adblock         - advertisement blocking extension for web b

---

### Post by northern lights on 2009-07-12
Only the packages with an 'i' flag are installed. See [Accessing Package Information]("http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/ch02s02s02.html") in the aptitude reference guide.

Remove either the 3.5 beta or the 3.0 using Synaptic or [apt-get]("http://linux.die.net/man/8/apt-get").

---

### Post by myolbug on 2009-07-12
> **northern lights said:**
> Only the packages with an 'i' flag are installed. See [Accessing Package Information]("http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/ch02s02s02.html") in the aptitude reference guide.

Remove either the 3.5 beta or the 3.0 using Synaptic or [apt-get]("http://linux.die.net/man/8/apt-get").

Thank you for the advice and the information.  I will read it now.

---

### Post by GCoffee on 2009-07-12
Firefox is installed by default. However, if you have removed it or whatever go to:

Applications > Add/Remove...

In the search box in the upper right hand corner type in: "firefox"

Scroll down the page until you come to "Firefox Web Browser"

Tick it to install firefox and all the required components.

---

