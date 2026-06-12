---
title: "Update failure"
date: 2010-05-30
forum: New to Ubuntu
---

### Post by dansaDisco on 2010-05-30
Hi guys, this recent week I've been having problems while trying to update ubuntu.

I get these errors when checking for updates:
```
Failed to fetch http://ppa.launchpad.net/http/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/reacocard-awn/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
```


At first I thought like, whatever, it's probably just down or something.

But then I tried again, and again, etc.

The weirdest part is the fact that it says "binary-amd64" as I have a x86 system, not a x64.

If anyone could help me solve this I'd appreciate it :)

---

### Post by fordguydude on 2010-05-30
> **dansaDisco said:**
> Hi guys, this recent week I've been having problems while trying to update ubuntu.

I get these errors when checking for updates:
```
Failed to fetch http://ppa.launchpad.net/http/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/reacocard-awn/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
```


At first I thought like, whatever, it's probably just down or something.

But then I tried again, and again, etc.

The weirdest part is the fact that it says "binary-amd64" as I have a x86 system, not a x64.

If anyone could help me solve this I'd appreciate it :)

I'm having the exact same problem. I was able to update previously, but not anymore. I figure it was a problem on the server end, but now I'm not sure.

---

### Post by josephellengar on 2010-05-30
> **dansaDisco said:**
> Hi guys, this recent week I've been having problems while trying to update ubuntu.

I get these errors when checking for updates:
```
Failed to fetch http://ppa.launchpad.net/http/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/reacocard-awn/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
```


At first I thought like, whatever, it's probably just down or something.

But then I tried again, and again, etc.

The weirdest part is the fact that it says "binary-amd64" as I have a x86 system, not a x64.

If anyone could help me solve this I'd appreciate it :)

You may want to try resetting your software sources.

---

### Post by Catharsis on 2010-05-30
Those PPAs don't exist anymore. Are they leftovers from a previous install that you upgraded from?

Try unchecking them through Software Sources: System->Administration->Software Sources->Other Software (Tab).

Then run
```
sudo apt-get clean
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by dansaDisco on 2010-05-31
Well, when trying to disable these sources it seems that they don't exist.. 
I tried to run this but it didn't work either.
```
sudo apt-get clean
sudo apt-get update && sudo apt-get upgrade
```

```
W: Failed to fetch http://ppa.launchpad.net/http/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/reacocard-awn/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

Any further suggestions?
I've attached a screenshot of my software sources.

---

### Post by Catharsis on 2010-05-31
> **dansaDisco said:**
> Well, when trying to disable these sources it seems that they don't exist.. 

They're the 7th and 9th from the top on that list.
```
http://ppa.launchpad.net/http/ppa/ubuntu lucid main
http://ppa.launchpad.net/reacocard-awn/ppa/ubuntu lucid main
```

---

### Post by dansaDisco on 2010-05-31
Oh, I'm blind :p

Well I disabled them and I was finally able to run a update without errors, so I guess that the problem's solved!

Thank you!

---

### Post by Catharsis on 2010-05-31
Glad to know you got it working! :)

Do you mind marking this thread as "Solved" by clicking "Thread Tools" at the top?

---

### Post by kistareddyd on 2010-08-02
> **Catharsis said:**
> Glad to know you got it working! :)

Do you mind marking this thread as "Solved" by clicking "Thread Tools" at the top?
  Thanks buddy "thussy gr8 hoooo" that means u r gr8

---

