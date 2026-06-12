---
title: "dwl-g132"
date: 2006-08-08
forum: Networking &amp; Wireless
---

### Post by vista on 2006-08-08
I'm trying to set up a wireless usb adapter, dwl-g132,
like this: 

> 
$ cd /wlan
$ ndiswrapper -i athfmwdl.inf
$ ndiswrapper -i NetA5AGU.inf

I'm getting an error message when i try to run above code
in the terminal, my wlan folder is located on my desktop, 
Im a complete beginner here so should it be cd /desktop/wlan ????? 
Or what?

---

### Post by x64Jimbo on 2006-08-08
Do you have the sys files in that folder as well? What's your error message?

---

### Post by mjm115 on 2006-08-08
you have to put 'sudo' before your ndiswrapper commands.  Other than that, it should work.  Let me know, because I'm interested in purchasing this same adapter.

---

