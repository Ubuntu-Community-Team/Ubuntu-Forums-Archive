---
title: "How to download a file from a server in Terminal?"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by kylejn on 2009-04-10
Sorry if this is a stupid question, but I've been trying to figure it out for about an hour now and still have no idea what I'm doing.

I've ssh'ed into my school server in Terminal, but I don't know the syntax to do what I want. Basically, I've got a folder that I want to copy to my local desktop, but I don't know how to do it.

What's the proper command for this?

Thanks!

---

### Post by bodhi.zazen on 2009-04-10
use wget

wget [http://server.com/path/to/file](http://server.com/path/to/file)

---

### Post by unutbu on 2009-04-10
Option #1:
You could use rsync like this:
```
rsync --verbose -ae ssh  user@ipaddress:/path/to/remote/folder/ /path/to/local/folder/
```
The rsync command can be run on the local machine or the server (if it has rsync).

Option #2:
Or you could tar the directory:
On the server:
```
tar cf archive.tar /path/to/directory
```

On the local machine:```

scp user@ipaddress:/path/to/archive.tar /path/to/local/dir
tar xvf archive.tar
```

---

### Post by kylejn on 2009-04-10
Holy crap, it worked! You all are geniuses.

Thanks!

---

### Post by MrWES on 2009-04-10
does scp have the recursive command to copy directories?

---

### Post by bodhi.zazen on 2009-04-10
> **MrWES said:**
> does scp have the recursive command to copy directories?

yes

scp -r

[http://linux.die.net/man/1/scp](http://linux.die.net/man/1/scp)

---

### Post by MrWES on 2009-04-10
> **bodhi.zazen said:**
> yes

scp -r

[http://linux.die.net/man/1/scp](http://linux.die.net/man/1/scp)

Got it -- thanks.

Wow -- scp is a very nice tool to copy files from my server to my laptop -- and with a progress meter taboot.

Bill

---

