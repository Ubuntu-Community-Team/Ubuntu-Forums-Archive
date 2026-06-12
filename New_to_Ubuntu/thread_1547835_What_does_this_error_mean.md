---
title: "What does this error mean?"
date: 2010-08-07
forum: New to Ubuntu
---

### Post by Moriarty123456 on 2010-08-07
Hello Chums,

What does this mean?:
```
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock the list directory
```

....and what do I do about it? I'm trying to upgrade from Bluefish 1.0.7 that I got in the Ubuntu software centre to BF 2.0 that's the current version. Following the instructions on the bluefish web page resulted in the above message.

I already tried updating the normal way through the upgrade centre and still have the old version of BF. Is there a better way to do this?

Many thanks.

---

### Post by 23dornot23d on 2010-08-07
[Bluefish]("http://bluefish.openoffice.nl/download.html")

It is in Synaptic Package manager .......

System - Administration - Synaptic Package manager

( Search in there and download it ...  should be ok I just did it and it worked ok )

---

### Post by Moriarty123456 on 2010-08-07
Thanks 23dornot23d!

I'm all over it like a Chihuahua lovin' a Great Dane. :-\"

---

### Post by 23dornot23d on 2010-08-07
lols .... loads of others too I think [Eclipse]("http://www.eclipse.org/") is quite a well used one too the one you chose is ok

HTML / DHTML editors

1) [Quanta Plus.]("http://quanta.sourceforge.net/")
2) [Bluefish.]("http://bluefish.openoffice.nl/")
3) WebMaker.
     4) [Screem.]("http://www.screem.org/")
     5) Toppage.
     6) [WebDesigner.]("http://webdesigner.linuxave.net/")
     7) [ScriptEditor.]("http://scripteditor.mozdev.org/")
  
[August]("http://www.bostream.nu/johanb/august/"). 

[FCKeditor]("http://freshmeat.net/projects/fckeditor/").

---

### Post by surfer on 2010-08-07
this usually means that you are trying to run apt-get (dpkg or something other that will lock your package database) without root permissions.

```

**sudo** apt-get update

```
will avoid that.

or it means that some other process already owns the lock.

---

### Post by Moriarty123456 on 2010-08-07
Thanks again.

The one on the software centre and package manager seems to be version 1.0.7. The new one is v2.0. Just in case anyone else wants it I had to delete the previous version first (hence the confusion) and then follow the instructions [here]("http://bfwiki.tellefsen.net/index.php/Installing_Bluefish#Installing_2.0.0_.28current_stable.29_on_Ubuntu_9.04_or_newer").

2.0 seems to be a big improvement IMHO.

Cheers Ubuntu folk.

---

### Post by 23dornot23d on 2010-08-07
The [version 2 of bluefish downloaded ok]("http://i34.tinypic.com/2rz9xsp.jpg") for me because I am running maverick 10.10 .... 

sorry, did not realise the old version downloaded in Lucid 10.04

---

### Post by andrew.46 on 2010-08-09
Well, actually there is a bug fix update for Bluefish to *2.0.1*. You easily build your own if you like:

Howto: Build the newest version of Bluefish under Ubuntu
[http://ubuntuforums.org/showthread.php?t=1426958](http://ubuntuforums.org/showthread.php?t=1426958)

Andrew

---

