---
title: "nautilus script and avast"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by lance bermudez on 2010-05-10
avast -c / -r=/home/ubuntu/report.txt

how do i write a nautilus script that will let me scan a file or dir using avast in nautilus? i have tried

avast -c "@" -r=/home/ubuntu/report.txt

does not work.

---

### Post by ankspo71 on 2010-05-10
Digging through my old scripts, I am able to come up with:

> #!/bin/bash

for name
do
	 avast -c -r=/home/ubuntu/report.txt "$name"
done

Or

> #!/bin/bash

for name
do
	 avast -c "$name" -r=/home/ubuntu/report.txt
done

These are untested though because I don't use antivirus. Edit: or Gnome :)

---

### Post by ankspo71 on 2010-05-12
I found another nautilus script for Avast on the internet. 
[http://www.grumz.net/?q=node/331](http://www.grumz.net/?q=node/331)
After looking the site over, it might require 'nautilus-actions' too.
Another:
[http://www.grumz.net/?q=node/323](http://www.grumz.net/?q=node/323)

---

