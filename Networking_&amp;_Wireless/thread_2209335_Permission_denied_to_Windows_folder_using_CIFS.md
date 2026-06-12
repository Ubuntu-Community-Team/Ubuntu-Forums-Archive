---
title: "Permission denied to Windows folder using CIFS"
date: 2014-03-05
forum: Networking &amp; Wireless
---

### Post by halvorlu on 2014-03-05
I'm trying to access a folder on a Windows share which is mounted using mount.cifs, but keep "Permission denied" errors. The folder essentially has the path //server/share/folder1/subfolder1. I can mount //server/share and list the folders in it, but when I do "cd folder1" or "cd folder1/subfolder1", I get "Permission denied". When I access the share through Windows, I can access both folders. It might be relevant that I do not have permissions to view other subfolders (folder1/subfolder2 etc.), but this is intentional (company security policy). So: How can I access subfolder1?

---

