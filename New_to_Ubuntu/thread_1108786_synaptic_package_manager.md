---
title: "synaptic package manager"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by interceptorV8 on 2009-03-28
i just visited getdeb.net for some software updates and found it pretty useful but they don't have everything i use (like k9copy for example)

updated abi-word through synaptic by adding the deb line in the repositories...  BUT...

my question is... 

is there a way to update multiple programs at once through synaptic package manager INSTEAD of having to add deb lines to the repository for each program?  

like i mentioned i check getdeb.net every few months, but a lot of the programs i use have updates but aren't listed.  AND compiling the tar.gz files NEVER seems to work with me.

---

### Post by 3rdalbum on 2009-03-28
Yes, you can add a repository that contains more than one program. What repository did you add for Abiword?

As for K9Copy, a friend of mine on Intrepid needed a later version. Rather than compile it from source, I just took the Jaunty .deb of the later version, extracted it in File Roller, and placed all the files from it into the relevent folders in the filesystem. As I was upgrading to a point release, all the dependencies from the older version still worked fine with the new version.

[COLOR="Red"]WARNING: DO NOT try to update core parts of the system in this way unless you REALLY know what you're doing![/COLOR] The same goes for compiling new versions of core services.

---

### Post by hyper_ch on 2009-03-28
check my signature to some additional 3rd party repositories - be cautious however to which ones you add.

---

### Post by Simian Man on 2009-03-28
If you need very up to date software, perhaps Ubuntu isn't the right distro for you.

---

