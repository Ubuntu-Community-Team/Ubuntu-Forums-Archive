---
title: "Kiosk Information Point"
date: 2010-12-29
forum: New to Ubuntu
---

### Post by GTEM19889 on 2010-12-29
I have been trying to develop an information points at our club for some time now but more recently decided to do this with Ubuntu instead of Windows for various reasons.
 
Basically I take a very old (but reliable) Compac Deskpro EN with 40GB hard disk and around 500Mb Ram. 
 
The idea is to:
1. Load as thin an operating system as possible,
2. should boot straight into web-browser (Full screen mode)
3. Only buttons offered in browser must be Back,Forward,Recent Pages, Refresh,Stop & HomePage (I have tried autohide but unfortunately this offers Close Restore & Minimise also)
4. The webbrowser must also be able to view or play other content such as Video, Podcasts & Midi files (so so firefox plug-ins is what I am thinking)
 
I have modified the mouse provided with this computer to not allow the right mouse button to be used, by opening the mouse up and cutting off the pin used for the right mouse button. This limits users to only navigate through the website homepage which was also set up with this in mind (as it is not there for people to browse anything but the clubs webpages.
 
To complete this I also need a screen saver that could cycle through various pre-specified webpages every couple of minutes.
 
I have no requirement to charge people for their time or limit their usage as most sites I have been looking at refer me to cybercafe software.
 
If anybody else has done this or something similar I would appreciate any advise

---

### Post by davidmohammed on 2010-12-29
sounds like an interesting project.

[This]("https://wiki.ubuntu.com/kioskFluxbox") is some info using quite an old version of ubuntu.  Suggest you could use it as a template.

... can I suggest, when you complete your project, you update this web-page so that others learn from your experiences but using a newer version of ubuntu.

---

### Post by GTEM19889 on 2011-01-09
How to get rid of Close Restore and Minimize???

In Firefox I am using Autohide 1.8.2 to only show the Navigation Toolbar. 
As I have modified the navigation toolbar to only have Back,Forward,Recent Pages, Refresh,Stop & HomePage

Unfortunately when in fullscreen mode the Close Restore and Minimize buttons apear on the right of the Navigation Menu

I need to get rid of these buttons and struggling to get past this hurdle. 

If anybody has any idea how this can be done I would really appreciate some input.

---

### Post by Kasami on 2011-01-09
You can install the CompizConfig Settings Manager, go down to "Window decoration" and go inside and delete "any" in decoration windows. I had to delete it by hand but it seemed to work. The thing is that those buttons are controlled by Metacity or the window decorator installed, not firefox.

-- Edit --

You can use a plugin like:
[https://addons.mozilla.org/en-US/firefox/addon/1659/](https://addons.mozilla.org/en-US/firefox/addon/1659/)

That is designed for this but you will have to stop it being able to quit on alt-f4

---

### Post by NickJones on 2011-01-09
Pump the control keys and the F keys with glue so they can't be pressed?
What is the need to "lock it down" anyway, your standard 14 year old that goes to cyber cafe's installs keyloggers and comes back with some passwords, that's not going to happen in Linux, and it's so easy to re-install linux that you could just re-flash all of the machines every night.

---

### Post by NickJones on 2011-01-09
Through Ubuntu Tweak you can remove the close button under "Window Manager Settings", meaning one less way someone could close Firefox.

---

### Post by GTEM19889 on 2011-01-09
The R-Kiosk Add on looks like its worth trying.

NickJones - No need for me to glue the FKeys, the Keyboard is completely removed as per first post. This application also avoids me having to modify the mouse by cutting the right mouse button pin out

Only problem I have now is the navigation bar disappears completely

According to:
[https://addons.mozilla.org/en-US/firefox/addon/1659/](https://addons.mozilla.org/en-US/firefox/addon/1659/)

You can enable Navigation toolbar by adding the following to user.js:
user_pref("rkiosk.navbar", true);

Problem is I dont know how to do that. Where is user.js?

---

### Post by radar2020 on 2011-01-09
> You can enable Navigation toolbar by adding the following to user.js:
user_pref("rkiosk.navbar", true);

Problem is I dont know how to do that. Where is user.js?

You can find information about user.js here.

[http://kb.mozillazine.org/User.js_file](http://kb.mozillazine.org/User.js_file)

---

