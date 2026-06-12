---
title: "sftp filename help"
date: 2007-09-25
forum: Networking &amp; Wireless
---

### Post by rara on 2007-09-25
so I have to download a file from a remote computer, but unfortunately the file is in a folder that was named with a space. 
I've tried: 
```
get /s/bach/k/under/user/workspace/file name/file
get /s/bach/k/under/user/workspace/"file name"/file
get /s/bach/k/under/user/workspace/"'file\ name'"/file
get /s/bach/k/under/user/workspace/"'file name'"/file
get /s/bach/k/under/user/workspace/"file\ name"/file
get /s/bach/k/under/user/workspace/'file\ name'/file
get /s/bach/k/under/user/workspace/'file name'/file
get /s/bach/k/under/user/workspace/file%20name/file
get /s/bach/k/under/user/workspace/"file%20name"/file
get /s/bach/k/under/user/workspace/'file%20name'/file
get /s/bach/k/under/user/workspace/"'file%20name'"/file
```

and none work... they all just return the same 'file not found' error... how can I access this folder?

---

### Post by spd106 on 2007-09-26
Can you use a wildcard or use mget and just pull all of the files? 

I'm not an ftp expert, but these have served me well in the past.

---

### Post by wirelessmonkey on 2007-09-26
Try cd'ing to /s/bach/k/under/user/workspace/

then cd "file name"

then mget fil*

---

