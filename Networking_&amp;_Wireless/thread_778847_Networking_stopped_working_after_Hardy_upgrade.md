---
title: "Networking stopped working after Hardy upgrade"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by markcjordan on 2008-05-02
Hi everyone, I had networking running fine on my intel wireless card before the hardy upgrade but it seems to have stopped working now. I've attached some relevant output from commands on my system; I'm dual-booting vista here so I don't have direct access to ubuntu at the moment, but I'd be happy to run any more commands if needed. Can anyone help? Many thanks!

Mark

---

### Post by stdunbar on 2008-05-02
Like myself, you've got the Intel 3945ABG wireless adapter.  The driver changed in 8.04 and it doesn't work.  Search this forum for a hack around - it isn't a great solution but basically you have to go backwards a bit.

---

### Post by markcjordan on 2008-05-02
> **stdunbar said:**
> Like myself, you've got the Intel 3945ABG wireless adapter.  The driver changed in 8.04 and it doesn't work.  Search this forum for a hack around - it isn't a great solution but basically you have to go backwards a bit.
Thanks for the hint. I ended up downloading the backports modules (linux-backports-modules-hardy-generic_2.6.24.16.18_i386) using vista, then installed them manually. Works great, and my wireless light seems to be working again :)

Mark

---

