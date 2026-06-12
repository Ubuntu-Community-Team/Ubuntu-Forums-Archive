---
title: "ebox packacge not found error"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by curtriley on 2009-06-16
I am following the instructions in the ubuntu server guide to install ebox but having no luck. If anyone out there can help a newbie, I would appreciate it. Thanks in advance.
 
I used the command:
 
[COLOR=blue]apt-cache rdepends ebox | uniq[/COLOR] 
 
and recieved this response:
 
[COLOR=blue]w: unable to locate package ebox[/COLOR]
 
I also tried:
 
[COLOR=blue]sudo apt-get install ebox[/COLOR]
 
and it said:
 
[COLOR=blue]reading package lists... Done[/COLOR]
[COLOR=blue]Building dependency tree[/COLOR]
[COLOR=blue]reading state information... done[/COLOR]
[COLOR=blue]E: Couldn't find package ebox[/COLOR]

[COLOR=black]Thanks again for any help,[/COLOR]
 
Curt

---

### Post by kerry_s on 2009-06-16
[https://help.ubuntu.com/community/eBox](https://help.ubuntu.com/community/eBox)

---

### Post by curtriley on 2009-06-16
This may not be THE way to do it, but I found A way to do it. I got an iso from the ebox website and re-installed ubuntu from the iso that included ebox

---

### Post by bereta on 2009-07-07
So can anyone explain how exactly you go about instaling ebox, I'm getting the same error that curtriley is getting. The webpage that kerrt_s gives is great but it tells me to do what I am already doing ( what curtriley stated at the top of the thread) and its not working.

Its worth noteing that I am behind a proxy. I know if that may have something to do with this. Is there some one that can point me in the right dirrection of how I would properly setup ubuntu server for an HTTP proxy?

---

### Post by MartijnNL on 2009-07-15
Have you tried adding the launchpad repository as described in the given link? 

deb [http://ppa.launchpad.net/ebox/ubuntu](http://ppa.launchpad.net/ebox/ubuntu) hardy main

And what version of Ubuntu are you using? Hardy or another one? Ebox is available for hardy but I'm not sure about other ubuntu versions.

I personally used this page instead and took the more ebox 1.2 repository.
[http://trac.ebox-platform.com/wiki/Document/Documentation/InstallationGuide](http://trac.ebox-platform.com/wiki/Document/Documentation/InstallationGuide)

Only one thing to note on that page:

The command

sudo apt-key add ....

should be

sudo-apt-key adv ...

---

### Post by mcduck on 2009-07-15
> **bereta said:**
> So can anyone explain how exactly you go about instaling ebox, I'm getting the same error that curtriley is getting. The webpage that kerrt_s gives is great but it tells me to do what I am already doing ( what curtriley stated at the top of the thread) and its not working.

Its worth noteing that I am behind a proxy. I know if that may have something to do with this. Is there some one that can point me in the right dirrection of how I would properly setup ubuntu server for an HTTP proxy?

Ebox is in the Universe-repository, you'll have to enable that first and then your command should work.

If you have Gnome installed, go to System/Administration/Software Sources and enable Universe on the Ubuntu Software-tab. If you are running the server version without a GUI this page should help: [https://help.ubuntu.com/community/Repositories/CommandLine#Adding%20the%20Universe%20and%20Multiverse%20Repositories]("https://help.ubuntu.com/community/Repositories/CommandLine#Adding%20the%20Universe%20and%20Multiverse%20Repositories")

---

### Post by MartijnNL on 2009-07-15
Addition: After install I couldn't find Ebox through FF. And uninstalling gives mayor headache and will probably result in a reinstall. Not very important as I was just testing, but still...

It is very incovenient that when you use Ebox you can't do any manual edits to configurations anymore. (As in using ssh and a text-editor.)

---

