---
title: "How to build bridging support (CONFIG_BRIDGE) as a kernel module?"
date: 2011-07-18
forum: New to Ubuntu
---

### Post by lahorilion on 2011-07-18
Hello guys, I am all new to Linux (just a week) and I have been given this task of installing openvswitch in Ubuntu, I have completed most of the stuff but I am stuck in a step because I don't know How to build bridging support (CONFIG_BRIDGE) as a kernel module.

I am facing the following error:
        [COLOR=Red][I]ERROR: Module bridge does
        not exist in /proc/modules[/I][/COLOR]

Openvswitch FAQ says:
     [I]   If "/sbin/rmmod bridge" fails with [COLOR=Red]"ERROR: Module bridge does
        not exist in /proc/modules"[/COLOR], then the bridge is compiled into
        the kernel, rather than as a module.  Open vSwitch does not
        support this configuration (see "**Build Requirements"**).[/I]

Build Requirements:
       [I][B]The Open vSwitch datapath requires bridging support
      (CONFIG_BRIDGE) to be built as a kernel module[/B].  (This is common
      in kernels provided by Linux distributions.)  The bridge module
      must not be loaded or in use.  If the bridge module is running
      (check with "lsmod | grep bridge"), you must remove it ("rmmod
      bridge") before starting the datapath.[/I]

So, what to do now?

Any help will be highly appreciated,
Thanks.

---

