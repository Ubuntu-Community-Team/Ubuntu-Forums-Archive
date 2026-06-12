---
title: "synaptic package manager error mssg"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by htfqueen on 2009-08-19
I think I've completely screwed up my Ubuntu 8.04.  When I try to access the package manager I get this message:
 
E: Unable to write mmap - msync (28 No space left on device)
E: The package list or status file could not be parsed or opened
E:_cache->open() failed, please report
 
In addition my browser is no longer working.  I have a connection to the internet but when I try to connect with the browser the ball spins and then disappears. 
 
I'm about ready to throw in the towel here!  Tell me what I need to do to get this system working please!
 
A frustrated user:(

---

### Post by michy99 on 2009-08-19
It looks like you have a full partition. What is the output of this command?```
df -h
```

---

### Post by htfqueen on 2009-08-19
Filesystem           Size      Used    Avail   Use%   Mounted on
/dev/sda             3.4G      3.4G      0      100%   /
varrun                501M     116K   501M      1%    /var/run
varlock               501M       0       501M     0%    /var/lock
udev                   501M     36K     501M     1%    /dev
devshm               501M       0      501M      0%   /dev/shm
lrm                     501M     1.9M    499M      1%   /lib/modules/2.6.24-24-lpia/volatile
overflow              1.0M      20K   1004K      2%   /tmp
gvfs-fuse-daemon 3.4G     3.4G       0     100%   /home/peggy/.gvfs

---

### Post by michy99 on 2009-08-19
Yep, that's the problem alright. To learn how to fix it, read this thread:

[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

---

### Post by drs305 on 2009-08-19
3.4GB is too small to run an ubuntu install effectively. I've written a post about new installations which create a 2.3GB partition. If yours is a new install, the situation is not quite identical but close enough that this thread may provide some guidance:

[http://ubuntuforums.org/showthread.php?p=7658271#post7658271]("http://ubuntuforums.org/showthread.php?p=7658271#post7658271")

There are instructions on how to reinstall with a larger Ubuntu partition and also a link on how to expand the / partition if you prefer doing that.

Added: michy99 was quicker and posted the link to the second link I mentioned.  ;-)

---

