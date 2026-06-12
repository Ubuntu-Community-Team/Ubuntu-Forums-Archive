---
title: "javascript not work in Firefox"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by cjv8888 on 2008-12-27
I have had this happened more than once when I clicked a javascript link in Firefox and nothing happened. 
The link will only work in Windows Internet Explorer , not even in Windows Firefox.
What can I do?
eg [this page]("http://www.fairtrading.nsw.gov.au/About_us/Online_services/Home_building_licence_check.html")

when you click on the start licence check then start licence search

---

### Post by cjv8888 on 2008-12-27
ie
The link works in Windows IE
but  does not work in Windows Firefox
and  does not work in Ubuntu Firefox

so it is forcing me to reboot back to Windows IE and be exposed to all the inherent risks.

---

### Post by cjv8888 on 2008-12-28
Anyone ?

---

### Post by Pollox on 2008-12-28
It works just fine for me in firefox in Ubuntu.  Have you verified that javascript is enabled in your firefox browser?  I.e. go to "edit", "preferences", click the "content" tab and make sure the "enable JavaScript" box is checked.  Also, make sure you don't have any extensions installed that might cause problems (e.g. Noscript would disable JavaScript on certain pages).

---

### Post by HereInOz on 2008-12-28
Confirming that the Javascipt works fine in Ubuntu Firefox for me.  If it doesn't work in either windows or Ubuntu with Firefox, it is possibly an extension which you have installed in both browsers which is disabling Javascript.

I checked both the mail and print-friendly icons, both of which call javascript, and they both work fine.

---

### Post by cjv8888 on 2008-12-29
I got this in the Firefox Error Console when I clicked on the Start Licence Search link:



Error: pendingChanges is not defined
Source File: [https://www.licence.nsw.gov.au/gls_eservice/18325/scripts/swecommon.js](https://www.licence.nsw.gov.au/gls_eservice/18325/scripts/swecommon.js)
Line: 73

What does it mean?

---

### Post by cjv8888 on 2008-12-29
> **HereInOz said:**
> Confirming that the Javascipt works fine in Ubuntu Firefox for me.  If it doesn't work in either windows or Ubuntu with Firefox, it is possibly an extension which you have installed in both browsers which is disabling Javascript.

I checked both the mail and print-friendly icons, both of which call javascript, and they both work fine.

My Javascript and java are both enabled in the Firefox

I have three extensions installed
Colorful Tabs
Foxmarks Bookmark synchroniser
Ubuntu firefox Modifications 0.5

Do you think any of these could be causing the problem?

---

### Post by cjv8888 on 2008-12-29
I found a way for the javascript to work, albeit temporarily.
I disabled the Ubuntu Firefox Modifications, restart Firefox,
the enabled the Ubuntu Firefox Modifications and restart Firefox.
Then the javascript will work, but only till I turned off the tab.

Then next time it does not work again?! :confused:

---

### Post by Temposs on 2008-12-29
The Ubuntu Firefox Modifications extension should not be causing a problem like that. What happens if you turn off all of the extensions?

---

### Post by cjv8888 on 2008-12-29
> **Temposs said:**
> The Ubuntu Firefox Modifications extension should not be causing a problem like that. What happens if you turn off all of the extensions?

It did not work.
It will only work if I re-enable the extension and restart Firefox with the tab/page already there.

---

### Post by Temposs on 2008-12-29
Something seems to be corrupted in your firefox installation. Try this in terminal:

sudo apt-get purge firefox

then:

sudo apt-get install firefox

---

