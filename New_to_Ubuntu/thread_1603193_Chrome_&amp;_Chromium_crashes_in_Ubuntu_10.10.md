---
title: "Chrome &amp; Chromium crashes in Ubuntu 10.10"
date: 2010-10-22
forum: New to Ubuntu
---

### Post by tacoz on 2010-10-22
After I installed Ubuntu 10.10 on my computer I have had the problem that both chrome and Chromium Crashes all the time. I do **_not_** have the problem in Ubuntu 10.4, only Ubuntu 10.10. And so far all the solution i have found don't help. Like "install libnss3" or "install libmoon".

Error:
```
:~$ /usr/bin/chromium-browser %U
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
[6029:6071:12637521931:ERROR:chrome/browser/sync/notifier/registration_manager.cc(127)] Registration failed with code: 12
[6029:6071:12637521974:ERROR:chrome/browser/sync/notifier/registration_manager.cc(127)] Registration failed with code: 12
[6029:6071:12637521993:ERROR:chrome/browser/sync/notifier/registration_manager.cc(127)] Registration failed with code: 12
[6029:6071:12637522009:ERROR:chrome/browser/sync/notifier/registration_manager.cc(127)] Registration failed with code: 12
[6029:6071:12637522027:ERROR:chrome/browser/sync/notifier/registration_manager.cc(127)] Registration failed with code: 12
[6029:6071:12637522047:ERROR:chrome/browser/sync/notifier/registration_manager.cc(127)] Registration failed with code: 12
[6029:6071:12637522064:ERROR:chrome/browser/sync/notifier/registration_manager.cc(127)] Registration failed with code: 12
[6029:6071:12637522081:ERROR:chrome/browser/sync/notifier/registration_manager.cc(127)] Registration failed with code: 12
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
Segmentation fault

```
And in this case I didn't do anything, just open Chromuim!
and no, I don't like using firefox!

Any idea what I should/can do?
Thanks.

Ps. It Crashes two thing doing this post!! :(

---

### Post by Chesamo on 2010-10-22
It sounds like you're on x64 Ubuntu, with the x86 version of Flash installed with the NS Plugin Wrapper, am I correct? Because according to the logs, nspluginviewer (a part of nsplugin) is causing Chromium to crash.

---

### Post by tacoz on 2010-10-22
Hmmm. Yes I'm on a 64bit Ubuntu! And I do not know if it is a 32bit flash installed! I didn't  manually installed it, the system did. I Then I will try to remove the flash and install a 64bit version myself and pray to tux, and hope that is the solution! =D
(Thanks by to way)

---

### Post by tacoz on 2010-10-22
I tried to remove Flash! And when i was on my way to Adobe's homepage it happened again!
```
:~$ /usr/bin/chromium-browser %U
[13855:13885:22559683368:ERROR:chrome/browser/sync/notifier/registration_manager.cc(127)] Registration failed with code: 12
[13855:13885:22559683415:ERROR:chrome/browser/sync/notifier/registration_manager.cc(127)] Registration failed with code: 12
[13855:13885:22559683433:ERROR:chrome/browser/sync/notifier/registration_manager.cc(127)] Registration failed with code: 12
[13855:13885:22559683451:ERROR:chrome/browser/sync/notifier/registration_manager.cc(127)] Registration failed with code: 12
[13855:13885:22559683468:ERROR:chrome/browser/sync/notifier/registration_manager.cc(127)] Registration failed with code: 12
[13855:13885:22559683491:ERROR:chrome/browser/sync/notifier/registration_manager.cc(127)] Registration failed with code: 12
[13855:13885:22559683509:ERROR:chrome/browser/sync/notifier/registration_manager.cc(127)] Registration failed with code: 12
[13855:13885:22559683528:ERROR:chrome/browser/sync/notifier/registration_manager.cc(127)] Registration failed with code: 12
Segmentation fault
```
This time I didn't have flash installed! So that wasn't the problem! :(
Any new ideas?

---

### Post by Paqman on 2010-10-22
How did you install Chromium? Is it the version in the Ubuntu repos?

---

### Post by tacoz on 2010-10-22
Yes.
It was the Chromium version Ubuntu software center provided.
And the version of chrome i have are the the one from googles homepage([http://www.google.com/chrome](http://www.google.com/chrome)).

---

### Post by tlareywi on 2010-10-23
Have you tried 'uninstalling' libmoon? That resolved the crash for me after upgrading to 10.10.

---

### Post by dundacil on 2010-10-24
My experience is the following:
on a clean 10.10 install, no problem whatsoever
on upgrading from 10.04.1 to 10.10, chrome crashes: in the latter case, removing libmoon cures the problem

I would be interested if anybody finds out what is apparently going wrong in the upgrading: I suspect some configuration file left over (I got some "wrong mime" warning while upgrading, incidentally)

The other strange think is that logging onto the upgraded machine via ssh I get a few messages: first a welcome to 10.10 message, but then, a few lines below, a welcome to 10.04.1 message and whether I want to upgrade to maverick:
New release 'maverick' available.
Run 'do-release-upgrade' to upgrade to it.

:)

---

### Post by tacoz on 2010-10-24
Yes I have removed libmoon again! :) (But I still have "libness3" installed)
I did make a clean install of Ubuntu 10.10, always do! :D

And after i had removed and reinstalled flash i also began to get warnings! This plus the first terminal text I posted!
```

(rpc_method_invoke_possible(plugin->connection))
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:2533):invoke_NPP_HandleEvent: assertion failed: (rpc_method_invoke_possible(plugin->connection))
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:1923):invoke_NPP_SetWindow: assertion failed: (rpc_method_invoke_possible(plugin->connection))
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:1854):invoke_NPP_Destroy: assertion failed: (rpc_method_invoke_possible(plugin->connection))
Segmentation fault

```

But the time between the last warning and the Segmentation fault are somethings over a minute! (If that are of any use!)

---

### Post by dundacil on 2010-10-24
OK, I sort of solved the problem at my end.
1. I removed libmoon and the associated plugins (sudo apt-get remove --purge libmoon)
2. I went to the Novel site and downloaded and installed their moonlight plugin ([http://go-mono.com/moonlight/](http://go-mono.com/moonlight/) I picked the 3.0 prerelease, it is on the right on the page: the URL of this prerelease is [http://go-mono.com/moonlight/prerelease.aspx](http://go-mono.com/moonlight/prerelease.aspx))

I opened firefox on a moonlight page and it started to work without problems. Then I opened chromium and repeated the procedure (went to Novel site etc) and chromium too, a few downloads later, started to work OK.

Now everything works fine, including watching movies/channels running under moonlight.

---

### Post by cejack on 2010-10-24
Not all Silverlight works but that's not a big deal.  

That's what we have VM's for...

Thanks for this post.  Helped me figure out my problem with Chrome and Chromium.

---

### Post by tacoz on 2010-10-30
I have tried it, but Chromium still crashes.

It have been longer time between the crashes, but it had always been random time period between them, so can't tell if it had help a little! But it wasn't the solution.

---

