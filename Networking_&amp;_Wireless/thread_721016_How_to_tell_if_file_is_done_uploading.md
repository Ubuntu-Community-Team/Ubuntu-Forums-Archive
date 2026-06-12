---
title: "How to tell if file is done uploading?"
date: 2008-03-10
forum: Networking &amp; Wireless
---

### Post by skiani on 2008-03-10
Hi,

Is there a way to tell when a file is done uploading? I have a samba share and I want to automatically start a process when the file is done uploading. Unfortunately it sees the file full size as soon as the upload starts so I can't monitor file size change. Thanks.

---

### Post by skiani on 2008-03-19
I will answer my question: smbstatus. My python code that does this:

```
File=<file to check>
CheckFileStatus=os.system("smbstatus -L | grep \""+File+"\"")
if CheckFileStatus==256:    #done uploading

```

---

