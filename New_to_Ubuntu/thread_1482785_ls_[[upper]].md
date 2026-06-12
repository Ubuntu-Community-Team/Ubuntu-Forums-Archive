---
title: "ls [[:upper:]]*"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by andreas.wpv on 2010-05-13
ls works fine, but when I have a link in the directory (to a harddrive, i.e. diskdirectory1) it lists all files on the diskdirectory1 as well. Is that normal?

Additionally, when using wildcards (like in the title), the wildcard works fine for the working directory, but when listing the files of the linked directory, it lists all files, not just the one matching the wildcard.... Did I do something wrong? (ubuntu 9.04, all updates).
it looks like this:


$ ls [[:upper:]]*
$ Last.txt  Test

Andreas-Documents:
955_colourscultures.png
Adobe
Adobe PDF
citavi

[and so on]

---

### Post by squaregoldfish on 2010-05-14
To prevent ls from listing the contents of directories, use the -d flag.

If you do want to list the contents of a directory, I don't think it's possible to get it to filter the contents. When you pass a search pattern to ls in this way, it will only be used to decide what gets listed. Since your directory name matches the criteria, it will list the contents of that directory, but it won't apply the filter.

If you want something more flexible, the find command will almost certainly fit your needs.

Steve.

---

