---
title: "Software to printing posters"
date: 2010-04-19
forum: New to Ubuntu
---

### Post by Paddy Landau on 2010-04-19
I've hunted around for a solution, but with no success.

I have a single-page document, and I'd like it to print large, over several pages, to make a poster.

For example, the document is a single A4 page. I'd like it to print over four (i.e. 2x2) A4 pages, so that I can stick them together to make a single A2 poster.

*In case I've made myself unclear, the two attachments (not the real document) indicate what I'd want; the original would be [the A4]("http://ubuntuforums.org/attachment.php?attachmentid=153747&stc=1&d=1271680906"), and the final would be [four A4 pages ]("http://ubuntuforums.org/attachment.php?attachmentid=153748&stc=1&d=1271680910")intended to be stuck together.*

The original document is in Open Office Writer, but of course I could save it as PDF or some other format.

Is there any software that will let me do that?

---

### Post by kellemes on 2010-04-19
[PosteRazor]("http://posterazor.sourceforge.net/") seems to be the one. (it's in the repositories)

Not sure what this is..
[http://www.blockposters.com/]("http://www.blockposters.com/")

---

### Post by Paddy Landau on 2010-04-19
Hmm, thanks, these do only images.

My document is Open Office (combination of words and images).

I found the solution, though. The repository has a program called 'poster'. From Open Office, print to a file; then use poster to convert the file; then use either lpr or Document Viewer (Evince) to print the final result.

My command was as follows, where orig.ps was the file that Open Office created and poster.ps was the file to print to the printer.
```
poster -v -p A2 -c 13x13mm -o poster.ps orig.ps
```

---

