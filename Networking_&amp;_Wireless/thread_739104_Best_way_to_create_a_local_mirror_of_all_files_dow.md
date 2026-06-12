---
title: "Best way to create a local mirror of all files downloaded by Firefox?"
date: 2008-03-29
forum: Networking &amp; Wireless
---

### Post by alvevind on 2008-03-29
I am looking for a method to create a local mirror of **all files** Firefox downloads and store them permanently in a directory on my harddisk.

I am **not** talking about regular caching here. And I am **not** talking about actively choosing a specific file for download.

What I want is that whenever a file is downloaded by Firefox during a normal browsing session, be it a html-file, gif-image, js-script, mp3-soundfile, or whatever, that file should be stored automatically in a preconfigured directory on my harddisk.

Example:
I configure (myhomedirectory)/automirror/ as the storage location.
I then enter "http://www.mozilla.org/index.html" in Firefox.
The page is shown as normal.
At the same time all the files Firefox downloaded in order to show that page (html, images, scripts, everything) are being stored in my directory.

So when I close Firefox, and look into my /automirror/ directory I find all the files exactly as they were fetched by Firefox:
(myhomedirectory)/automirror/www.mozilla.org/index.html
(myhomedirectory)/automirror/www.mozilla.org/css/base/content.css
(myhomedirectory)/automirror/www.mozilla.org/js/__utm.js
(myhomedirectory)/automirror/www.mozilla.org/images/feature-logos1.png
etc.

(Filesystem-incompatible URLs would of course need to be rewritten. The point is that absolutely everything should be stored, in a human-readable logical structure.)

I am looking for a simple and efficient and configurable way to do this.
I assume some kind of local proxy application would be the easiest way.

Any suggestions for an existing Firefox add-on or separate proxy application that could be used for this purpose?

If nothing out-of-the-box comes to mind, are there toolkits that would be appropriate to use as a basis for developing something like this? XUL? Curl? Squidcache? (I am complete newbie to network and Firefox programming.)

---

