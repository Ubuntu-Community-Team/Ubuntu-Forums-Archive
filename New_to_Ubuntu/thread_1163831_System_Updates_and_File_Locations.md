---
title: "System Updates and File Locations"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by Franc88 on 2009-05-19
Hi,

I've been using Ubuntu off and on for the last year.  I was wondering, what happens to all the files that are downloaded by the Update Manager?  Do they replace the old existing files or do they get saved with the old files?

If they do not replace the existing files, where can I go to check and delete the old files so its not taking up space.  What command do I need to use to list files by date.

I'm sure this must be a very basic question, directory search and files search, but I've still trying to figure this out.

Any help would be appreciated.

---

### Post by skymera on 2009-05-19
the .DEB files are kept in /var/cache/apt/archives

And yes, when new updates are installed old versions are replaced.

You don't need to worry about anything.

You can clean out the cache by:

```
 sudo apt-get clean 
```

---

