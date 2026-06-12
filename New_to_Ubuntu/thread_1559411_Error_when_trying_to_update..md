---
title: "Error when trying to update."
date: 2010-08-23
forum: New to Ubuntu
---

### Post by furiousjason on 2010-08-23
When running the update manager I get an error.

Failed to fetch [http://ppa.launchpad.net/murrine-daily/pp/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/murrine-daily/pp/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by gdonwallace on 2010-08-23
Your getting the standard 404 page not found error.  The same you would get browsing the internet sometimes.

You may want to check the PPA for that and make sure something has not changed.  The easy way is to copy and paste the URL into a browser and try to open it.  Whomever owns that program may be doing something to the site and has it down for maintenance.  Either way, you can keep trying the update and it should get through eventually.

---

### Post by howefield on 2010-08-23
> **furiousjason said:**
>  [http://ppa.launchpad.net/murrine-daily/pp/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/murrine-daily/pp/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

Did you manually type this in ?

You might be missing an "a" from ppa... shouldn't the line read

[http://ppa.launchpad.net/murrine-daily/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/murrine-daily/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)

---

### Post by furiousjason on 2010-08-23
> **howefield said:**
> Did you manually type this in ?

You might be missing an "a" from ppa... shouldn't the line read

[http://ppa.launchpad.net/murrine-daily/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/murrine-daily/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)


I copied and pasted that from the error window.

---

### Post by beew on 2010-08-23
The link works. Maybe just temporarily down.

---

### Post by furiousjason on 2010-08-23
Sounds good. I'll give it a few days and retry. Thanks for your help!

---

### Post by mhgsys on 2010-08-23
ERHM! **furiousjason**

> **beew said:**
> The link works. Maybe just temporarily down.

I'm sure **beew **ment the link is working in the answer of **howefield.**

> **howefield said:**
> Did you manually type this in ?

You might be missing an "a" from ppa... shouldn't the line read

[http://ppa.launchpad.net/murrine-daily/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/murrine-daily/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)


Your link indeed is missing an "a" from ppa...

---

### Post by furiousjason on 2010-08-23
> **mhgsys said:**
> ERHM! **furiousjason**



I'm sure **beew **ment the link is working in the answer of **howefield.**




Your link indeed is missing an "a" from ppa...


The link is automatic in the update manager. Is there a way to edit it for the update manager?

---

### Post by mhgsys on 2010-08-23
Yes; 
The line should be located in either /etc/apt/sources.list or /etc/apt/sources.list.d/
(I think it's in /etc/apt/sources.list.d/)

in a terminal use **cd** to navigate to the /etc/apt/sources.list.d/
```
cd /etc/apt/sources.list.d/
```
and typ ```
ls
``` to get the list of files located in there

You can use gksudo gedit to edit the files there; 
[B][U]
example[/U][/B]:
```
gksudo gedit /etc/apt/sources.list.d/team-xbmc-ppa-lucid.list
```
(the xbmc ppa)

or when it's in /etc/apt/sources.list
```
gksudo gedit /etc/apt/sources.list
```

edit;
Ps:
After editing the file you needed to edit; save the file and try running update manager again

---

### Post by furiousjason on 2010-08-23
Alright so I edited the files, rebooted and tried again. It did not work. Found the sources list through the directory and opened it and found the link under other software. In there it allowed me to edit the link. Ran the update and no errors. Thanks for the help!

---

