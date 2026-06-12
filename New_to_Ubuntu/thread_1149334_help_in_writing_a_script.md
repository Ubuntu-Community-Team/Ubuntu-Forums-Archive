---
title: "help in writing a script"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by akkad on 2009-05-05
i have ubuntu server,am looking to create a script that executes every one hour, it should compress(tar.gz) a directory and move the resulted tar file to another directory, how the script should look like?

---

### Post by slakkie on 2009-05-05
> **akkad said:**
> i have ubuntu server,am looking to create a script that executes every one hour, it should compress(tar.gz) a directory and move the resulted tar file to another directory, how the script should look like?


For the every hour part, have a look at cron (man cron).

The actual script is something like this:

```

TAR_DIR=/path/to/dir
ARCHIVE_LOC=/path/to/archive

# Tar the directory to /path/to/archive/yyyymmddhhmmss.tgz
tar zcvf $ARCHIVE_LOC/$(date +%Y%m%d%H%M%S).tgz $TAR_DIR

```

If you want to start with shell scripting look at this page: [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

Good luck!

---

