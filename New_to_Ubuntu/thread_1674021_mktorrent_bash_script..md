---
title: "mktorrent bash script."
date: 2011-01-23
forum: New to Ubuntu
---

### Post by glh5 on 2011-01-23
Hello,

I have about 100 directories (all in the same directory) I want to create a torrent metadata file for. All the directories have 'gnvr' in their name. So I decided to write a script for this.

So far I have this:

```
#!/bin/bash

cd ~/torrents/completed/                     
PATH_NAME=~/torrents/completed/*gnvr/
TRACKER_URL=http://tracker.url.org/announce    

mktorrent -v $PATH_NAME -p -a $TRACKER_URL
```

But when I use the script mktorrent only creates a metadata file for the first directory (in alphabetical order).

So the thing I need to add in order to make files for all directories is some kind of loop.

What is the easiest way to do this?

---

### Post by gmargo on 2011-01-23
Something like this?
```

find . -type d -name '*gnvr' -exec mktorrent -v {} -p -a $TRACKER_URL \;

```

---

### Post by glh5 on 2011-01-23
Thanks, it works! :D

---

