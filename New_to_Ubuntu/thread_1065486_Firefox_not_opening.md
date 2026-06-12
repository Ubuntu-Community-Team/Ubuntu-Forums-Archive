---
title: "Firefox not opening"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by Calfaile on 2009-02-09
Hi, 

I'm very new to Ubuntu, so this might be an obvious error on my part.  I recently upgraded to 8.10.  Ever since, Firefox won't open.  When I click on the icon, I get an "opening firefox" tab on the taskbar, and then it disappears.  When I try running it through terminal, I get the following error message:

/usr/lib/firefox-3.0.5/firefox: symbol lookup error: /usr/lib/xulrunner-1.9.0.5/libxul.so: undefined symbol: sqlite3_prepare_v2

I've tried searching the forums and the web for "firefox symbol lookup error", but couldn't find anything useful.

Thank you in advance,

Calfaile

---

### Post by Shazaam on 2009-02-09
You might try re-installing xulrunner.

---

### Post by Calfaile on 2009-02-10
How exactly do you re-install xulrunner?

---

### Post by Shazaam on 2009-02-10
System>Administration>Synaptic Package Manager. Once it opens click "Reload" (upper left side).  Go next to the lower left and click the "Status" box" Then go to "Search" (upper right), once that opens type in xulrunner. It will open to a listing with everything related, right-click the green box and choose "Mark for Reinstallation" then click Apply.

---

### Post by Calfaile on 2009-02-10
Thanks for the instructions.  I reinstalled xulrunner but I'm still getting the same error.

---

### Post by hytek on 2009-04-13
Here is the cause and fix for me.

I needed sqlite 3.3.5 for a development project, and this placed the libs under /usr/local/lib/libsqlite*

Firefox I guess looks for the libs under /usr/local/lib first instead of /usr/lib/ and this grabbed the 3.3.5 version instead of the default 3.5.9 libraries.

As a test you could try this:
$sudo mkdir /usr/local/lib/temp [enter]
$sudo mv /usr/local/lib/* /usr/local/lib/temp/ [enter]
$firefox [enter]

See if this fixes it. If it does then it was a library you installed that broke it.

Cheers.

---

