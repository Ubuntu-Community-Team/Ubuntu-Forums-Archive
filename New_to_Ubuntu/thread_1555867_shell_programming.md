---
title: "shell programming"
date: 2010-08-18
forum: New to Ubuntu
---

### Post by enuckon on 2010-08-18
Hello, what would a shell script look like that captures text from a given web page and saves it in a text file?  Can it be done with shell commands?  Thanks, E.

---

### Post by hudsonl on 2010-08-18
> **enuckon said:**
> Hello, what would a shell script look like that captures text from a given web page and saves it in a text file?  Can it be done with shell commands?  Thanks, E.

This should do it:

#!/bin/bash
#
echo -n "Enter the website url: "
read website
echo -n "Enter ouput filename: "
read outfile
wget -q -O /dev/stdout http://$website  > $outfile

---

