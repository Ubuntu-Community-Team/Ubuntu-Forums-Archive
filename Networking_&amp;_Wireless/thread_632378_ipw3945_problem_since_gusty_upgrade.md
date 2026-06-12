---
title: "ipw3945 problem since gusty upgrade"
date: 2007-12-05
forum: Networking &amp; Wireless
---

### Post by yakovyarmo on 2007-12-05
i i am using intel pro 3945 and the ipw3945 but it always disconnect after a while.
so i tries to compile a new ipw 3945 but i didnt manage to do so because i am a newbie.
and then i tried to use the iwl3945 but it didnt find any networks when i did the iwlist scan.
what can i do?? i am really frustrated.

---

### Post by Kleenux on 2007-12-05
Mine works ok, now. Have a look to [this thread]("http://ubuntuforums.org/showthread.php?t=631735"), just in case.

---

### Post by yakovyarmo on 2007-12-06
it works but it disconnects all the time

---

### Post by heldal on 2007-12-07
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/network-config/+bug/158045](https://bugs.launchpad.net/ubuntu/+source/network-config/+bug/158045) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				ipw3945 has its problems, and is no longer actively developed. It is also a closed-source driver. There is an alternative open-source driver iwl3945 in development. A lot has been done to this in the last few months, so the version included in gutsy is already quite outdated. Several people have reported it to be a better alternative, and hopefully there will be an update available shortly to further improve matters. See the attached link to launcpad for more information, including instructions on how to change driver.

---

### Post by yakovyarmo on 2007-12-08
how do i install iwl3945 on the gusty??

---

### Post by heldal on 2007-12-09
> **yakovyarmo said:**
> how do i install iwl3945 on the gusty??

You most likely have it already as it is included with the standard kernel-module package. All you need to do is to swap as described in the bug-discussion linked above ([https://bugs.launchpad.net/ubuntu/+source/network-config/+bug/158045/comments/4](https://bugs.launchpad.net/ubuntu/+source/network-config/+bug/158045/comments/4))

---

