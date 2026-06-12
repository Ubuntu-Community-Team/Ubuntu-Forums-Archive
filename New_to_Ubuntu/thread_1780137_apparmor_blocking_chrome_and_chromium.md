---
title: "apparmor blocking chrome and chromium"
date: 2011-06-11
forum: New to Ubuntu
---

### Post by iansane on 2011-06-11
Hi all,

I was posting in someone elses post here
[http://ubuntuforums.org/showthread.php?t=1380553](http://ubuntuforums.org/showthread.php?t=1380553)

But it seems that the security discussions forum is more for general discussion rather than getting help and judging by the low number of views and the high number of 0 replies, I'm guessing nobody reads that forum much?
Sorry if I'm wrong.

So my question is, does anyone know how to fix the problem of apparmor causing access denied on /dev/shm (shared memory) when trying to run chrome or chromium? If anyone has a working apparmor profile for either of these could you please post a copy of it? This started happening after installing the apparmor-profiles package which apparently makes some security changes to the system. Even with the chromium profile disabled it still has done something to the /dev/shm directory which is keeping me from being able to use chrome or chromium.

Thanks

---

### Post by andrewthomas on 2011-06-12
Check out this bug 

[https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/566788](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/566788)

---

### Post by iansane on 2011-06-12
Yeah thanks for the reply andrewthomas but that bug doesn't even touch on the root of the problem which is that the profile for chromium in apparmor.d is what is blocking the access and simply chmoding the directory is not fixing the issue and neither is disabling the profile.

I'll just keep reading through Bodi.zazen's intro and searching else where for learning how to grant permission through the profile on exactly what chrome needs to function while denying the rest.

Thanks

---

### Post by jtarin on 2011-06-12
I've had my own difficulties with this application. I'm not going to tell you how to circumvent security I will leave that up to each individual.  [A little education goes a long way.]("http://en.wikipedia.org/wiki/AppArmor");)

[And here.]("https://wiki.ubuntu.com/AppArmor")

---

### Post by jtarin on 2011-06-12
[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)

Some packages will install their own profiles, and additional profiles can be found in the apparmor-profiles package.

To install the apparmor-profiles package from a terminal prompt:

```
sudo apt-get install apparmor-profiles
```

---

### Post by iansane on 2011-06-13
> **jtarin said:**
> [https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)

Some packages will install their own profiles, and additional profiles can be found in the apparmor-profiles package.

To install the apparmor-profiles package from a terminal prompt:

```
sudo apt-get install apparmor-profiles
```

That is what caused the issue in the first place. The profiles in apparmor-profiles package is what is blocking it. However, as I am reading more and educating myself on the subject I see that adding the line
```

/dev/shm rw

```

in the profile should allow rw permissions. There are entries in the profile for /dev/shm/pulse-shm but no entry for the /dev/shm directory which I'm assuming is why it is giving the error access denied for /dev/shm

Giving permission with /dev/shm* rw like some have suggested in other forums and places gives the browser permission to write to any file in the /dev/shm directory which defeats the purpose just like chmod 777.

At any rate, I think I've figured out the problem and will have to test it later today when I have some time.

Thanks

---

### Post by iansane on 2011-06-13
> **jtarin said:**
> I've had my own difficulties with this application. I'm not going to tell you how to circumvent security I will leave that up to each individual.  [A little education goes a long way.]("http://en.wikipedia.org/wiki/AppArmor");)

[And here.]("https://wiki.ubuntu.com/AppArmor")

hmm... not sure what you mean by circumvent security. I'm trying to implement it, not circumvent it.

---

### Post by jtarin on 2011-06-13
What is the path to this file concerning chromium/chrome?

---

### Post by iansane on 2011-06-26
> **jtarin said:**
> What is the path to this file concerning chromium/chrome?

Sorry, I have been working on other things and missed the email notify that you had replied.

The path to the file is
/etc/apparmor.d/usr.bin.chromium-browser

For Chrome it would be
/etc/apparmor.d/opt.google.chrome.chrome

This chromium profile is installed when installing apparmor-profiles package. I just copied it for chrome.

Putting a sym link to both of them in the disable directory instructs apparmor to ignore/disable them when it checks app profiles so it's in effect like deleting them so they are will not be blocking access.

The disable directory is
/etc/apparmor.d/disable


I found the fix I think.
I was concerned about allowing chrome and chromium permission to write to the shared memory directory (/dev/shm) but in looking around through some of the contributed profiles at the link I posted above, I found that I can give them access to the /dev/shm directory only and then give them access to files in /dev/shm as needed rather than access to /dev/shm/*.

My whole problem I think came down to figuring out what line to add to the profile to give the necessary permissions without leaving it wide open and defeating the purpose of apparmor all together.

Fixes suggested on some other sites and posts to chmod -R 777 /dev/shm or to put the line in the profile /dev/shm/* rw  are not fixing the problem but are taking the quick easy work around of opening the shm directory up completely.

---

