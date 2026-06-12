---
title: "How to find all pictures with files over 100 kilobytes recursively?"
date: 2010-04-17
forum: New to Ubuntu
---

### Post by puppymagic on 2010-04-17
How do I find files over 100 kb recursively?

I tried

find * -size +100k

and got this

bash: /usr/bin/find: Permission denied 

thanks Ubuntu gurus

---

### Post by unmole on 2010-04-17
Try the graphical search from Palces>Search fro Files. You can set options for file size, filename extention etc.

---

### Post by Rayve on 2010-04-17
I believe, but am not certain, that find defaults to recursively - so searching in your current directory will search your current directory and all subdirectories. 

See here for some assistance:

[http://www.linux.com/archive/feed/55377](http://www.linux.com/archive/feed/55377)
[http://www.cyberciti.biz/faq/find-large-files-linux/](http://www.cyberciti.biz/faq/find-large-files-linux/)
[http://www.softpanorama.org/Tools/Find/finding_files_with_the_specific_size.shtml](http://www.softpanorama.org/Tools/Find/finding_files_with_the_specific_size.shtml)

So, to find all files greater than 100kb on your filesystem, the following should work:

```
 find / -size +100k 
```

---

### Post by oldfred on 2010-04-17
sudo

sudo find / -name '*' -size +1G    # files larger than 1GB

or maybe what you want

sudo find / -name '*.jpg' -size +100k    # jpg files larger than 100k

---

