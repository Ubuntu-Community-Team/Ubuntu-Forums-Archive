---
title: "Links referring to local files don't work in Ubuntu"
date: 2010-08-13
forum: New to Ubuntu
---

### Post by the_jezster on 2010-08-13
I think this is a Linux/Ubuntu issue rather than HTML/browser related, so I hope I'm asking in the right place:

Why, on a Webpage, can't I click on a link that refers to a local file? eg <a href="file:///home/jez/Documents/docs/internet.htm">local file</a> 

Well, I can click, but nothing happens.  When I copy the link and paste it into the address field, then it *does* open just fine, it's just that links don't work.

The same thing happens in both Firefox and Chrome, hence my guess that it may be a Linux/Ubuntu issue.

In Windows, local files open just fine eg <a href="file:///C|/jez/docs/internet.htm">local file</a>

Thanks...

---

### Post by cjtemple on 2010-08-13
Try to reference it with out the file
[HTML]
<a href="/home/jez/Documents/docs/internet.htm">Link here</a>
[/HTML]

---

### Post by diesch on 2010-08-13
For security reasons most browsers, like Firefox, do not follow links to file:// URIs in remore web pages.

I guess in Windows it only works with Internet Explorer.

---

### Post by the_jezster on 2010-08-21
Thanks cj, it works when using your suggestion.

What I don't understand though is that the link shown when you hover over the link is the exact same file:///home/jez/Documents/docs/internet.htm that was previously coded into the HTML but which didn't work.

Thanks also diesch, but file:/// links to local files work fine in both Firefox and Chrome in Windows...

---

