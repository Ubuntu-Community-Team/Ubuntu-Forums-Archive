---
title: "rsync log has strange field: &quot;&gt;f?????????&quot;"
date: 2010-10-01
forum: New to Ubuntu
---

### Post by oregonbob on 2010-10-01
On Ubuntu 8.10 server the log file for rsync has a strange field that I do not see on Redhat or Centos, a sample line:
[COLOR="Blue"]2010/09/30 20:42:00 [22174] >f????????? home/taunya/F11/Crescent.pdf[/COLOR]

Googling I see it is a code, such as ">" means written to destination. But why is this set as default in Ubuntu and is it documented? All those ">f????????" look alarming and I have to explain to users it is not an error if I even interpret them correctly.

---

### Post by Paddy Landau on 2010-10-01
Have a look at the manual for rsync ([FONT=Courier New]man rsync[/FONT]) and look for [FONT=Courier New]--itemize-changes[/FONT] (it occurs more than once in the manual). Specifically:
> an unknown attribute replaces each letter with a "?" (this can happen when talking to an older rsync).In other words, a question-mark means nothing. You can ignore it.

---

