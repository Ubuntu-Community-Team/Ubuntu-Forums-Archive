---
title: "kinda hard wget/grep question"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by earthpigg on 2010-03-11
how would i go about issuing the command to:

"download this page, and every page it directly links to"

i suspect this will somehow involve downloading the first page, and then using grep to find everything in quotes following "<a href=", and then piping that into a plain text file which can be fed to wget... or something like that.

edit: nvm, solved it myself.

if anyone else comes across this --

wget -r [www.website.com](www.website.com)

to make it only update your local copy, and not download the whole thing over:

wget -rN [www.website.com](www.website.com)

to spread the load out by waiting 5 seconds between downloads:

wget -w 5 -rN [www.website.com](www.website.com)

---

