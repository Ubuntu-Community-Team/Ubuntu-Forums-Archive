---
title: "PHP write user"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by gmxgeek on 2010-05-23
I have a PHP script that resides in a folder called /sub/www/sites-enabled/blah

The script takes a string and writes it to a file. The file write goes through fine if the file does not exist, however it uses root permissions to write it, and thus the file is locked to everyone but root. If the script runs again, it can't override it either.

If I move the script into another location (such as my home dir) then it writes it using www-data as it should.

/sub is an automounted partition, set in fstab

I'd like to keep the script in there if possible.

Any ideas as to how/why it is being written as root?

---

