---
title: "Cannot get Add/Remove Applications or Synaptic Package Manager Working"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by TRANQU111TY on 2009-01-01
I'm getting this error:

```
The package cache file is corrupted
E: _cache->open() failed, please report.
```

This was after I ran 

sudo dpkg --configure -a

Because I had this problem:

```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
```

How can I completely uninstall the whole package manager and install it again so that it works properly?

Thanks for reading!

---

### Post by f37u5g0d on 2009-01-01
fsck is the file system check utility for linux.  Use it!  It usually can fix correpted files.  For instructions on how to use it run man fsck or google it there probably is a wiki.

---

### Post by stderr on 2009-01-01
A bug as been filed regarding this behaviour: [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/257639]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/257639")

It would appear that everything still works OK. From looking over the comments there, it would appear that running

```
sudo dpkg --configure -a
```
 
and

```
sudo apt-get update
```

a couple times should make the error message bugger off for a while. It doesn't look like a proper solution's been figured out though.

As for removing and reinstalling apt... hmm... my initial reaction is that's not a great idea ;) but I'm not sure if it's *possible*.

---

### Post by hansdown on 2009-01-01
Hi TRANQU111TY.

You need to use ```
sudo dpkg --configure -a
```

---

### Post by TRANQU111TY on 2009-01-01
It appears to be working fine now. Hopefully it stays like that.

---

### Post by TRANQU111TY on 2009-01-01
Every time I open up Add/Remove Applications I always have the reload box pop-up but the only error I get now is:

```
W: GPG error: http://packages.medibuntu.org intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
```

---

### Post by adult swim on 2009-01-01
did you add the medibuntu gpg key?  if not run 
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

---

### Post by TRANQU111TY on 2009-01-01
> **adult swim said:**
> did you add the medibuntu gpg key?  if not run 
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Thanks. Now the only problem I have is that every time I open up Add/Remove Applications it says 'The list of available applications is out of date' and it has the option to 'Reload'.

---

### Post by adult swim on 2009-01-01
does it work when you click reload?

---

### Post by HotShotDJ on 2009-01-01
> **TRANQU111TY said:**
> 'The list of available applications is out of date' and it has the option to 'Reload'.I would avail myself of that option and go ahead and reload.

---

### Post by TRANQU111TY on 2009-01-01
> **adult swim said:**
> does it work when you click reload?

> **HotShotDJ said:**
> I would avail myself of that option and go ahead and reload.

Oh yeah. I click reload every time but it keeps telling me it is out of date whenever I open 'Add/Remove Applications'.

---

### Post by HotShotDJ on 2009-01-01
> **TRANQU111TY said:**
> Oh yeah. I click reload every time but it keeps telling me it is out of date whenever I open 'Add/Remove Applications'.What happens if you open System --> Administration --> Synaptic Package Manager?

---

### Post by adult swim on 2009-01-01
try starting fresh with add/remove.  if its open, close it down and then run
```
sudo apt-get install --reinstall app-install-data app-install-data-commercial
```
then open it back up and see if the error persists

---

### Post by stderr on 2009-01-02
Maybe the update didn't run for some reason. Just run in a terminal: 

```
sudo apt-get update
```

... should clear it.

---

### Post by TRANQU111TY on 2009-01-02
> **HotShotDJ said:**
> What happens if you open System --> Administration --> Synaptic Package Manager?

It just opens like normal. No pop up windows appear.

> **adult swim said:**
> try starting fresh with add/remove.  if its open, close it down and then run
```
sudo apt-get install --reinstall app-install-data app-install-data-commercial
```
then open it back up and see if the error persists

It's still persisting unfortunately. Thanks anyways.

> **stderr said:**
> Maybe the update didn't run for some reason. Just run in a terminal: 

```
sudo apt-get update
```

... should clear it.

Sorry this didn't fix it. Thanks for trying though.

---

### Post by prvteprts on 2009-04-26
I was able to stop that irritating "The list of available applications is out of date" popup. 

I opened Administration/Software Sources and under the Ubuntu Software tab, I unchecked one of the options, specifically the one for Software restricted by copyright (multiverse). It prompted me for a reload, did that, and closed Software Sources. I opened Add/Remove once more and it did not ask me to reload anymore. I opened Software Sources again, checked the multiverse again, reloaded, and it was done.

I read in a post in launchpad that this happens when sources.list is more recent than any file in /var/lib/apt/lists/ so I think doing the workaround above forces some files in /var/lib/apt/lists/ to be "refreshed" making it more recent than sources.list. That's just my theory, though. :)

---

