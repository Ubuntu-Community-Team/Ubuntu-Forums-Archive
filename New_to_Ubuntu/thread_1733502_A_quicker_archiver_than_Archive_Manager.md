---
title: "A quicker archiver than Archive Manager?"
date: 2011-04-19
forum: New to Ubuntu
---

### Post by Roger Allott on 2011-04-19
Archive Manager seems to be the default alternate on Ubuntu to WinRar on Windoze.

However, with WinRar, one can select the extent to which the programme goes through its compression algorithm - from 'Store' to 'Maximum'. Obviously, if you select Maximum, it can take ages to run the compression, and if you choose Store you get next to no reduction in file size but it zips through the task in next to no time.

I use archivers a lot to create split video files for uploading onto sharing sites, and as videos in a decent format can't really be compressed any further, the option I want to use is often 'Store'.

However, I don't have this option on Archive Manager, which means that when I create split .rar files on Ubuntu, it takes bl00dy ages and achieves next to no compression - the worst of both worlds.

Therefore, is there an alternative to Archive Manager that incorporates a user setting like one finds on WinRar?

---

### Post by seawolf167 on 2011-04-19
Couple things you might want to take a look at

1. *split* - to split a file into multiple segments

```
man split
```

2. tar - (3 different compression types; none, gz & bz2). You can filter this through *split* to split the files

```
tar cf file.tar files
tar czf file.tar.gz files
tar cjf file.tar.bz2 files
```

3. 7z - tons of compression options + the ability to split into multiple archives without using the *nix *split* command

```
sudo apt-get install p7zip-full
man 7z
```

---

