---
title: "Wi-Fi suddenly flaky"
date: 2007-05-06
forum: Networking &amp; Wireless
---

### Post by Jonathan Harford on 2007-05-06
I got my Broadcom 4318 Wi-Fi to work by installing this package:
[http://ubuntuforums.org/attachment.php?attachmentid=30328&d=1177147133](http://ubuntuforums.org/attachment.php?attachmentid=30328&d=1177147133)
which I found in this thread:
[http://ubuntuforums.org/showthread.php?t=197102&highlight=install+ndiswrapper](http://ubuntuforums.org/showthread.php?t=197102&highlight=install+ndiswrapper)

...and it worked beautifully for a few days. 

Now, though, I'll type a domain name in the URL bar of Konqueror, and the throbber will throb for a minute before Konqueror tells me that it can't get there (e.g. "Unable to locate google.com"). Then I'll try a different URL (or even just try a few times to reload the initial URL) and konq will connect just fine! The same happens when I click a link: there's a 80% chance the link will take a minute to resolve into a Konqueror error page.

I connect to the same WPA-enabled router via WinXP on the same laptop, so it's definitely something Feisty's doing differently from Windows.

Can anyone advise? Thanks.

---

### Post by Jonathan Harford on 2007-05-09
Well, I used ndiswrapper instead.

It was a struggle. But now I seem to have wireless!

---

