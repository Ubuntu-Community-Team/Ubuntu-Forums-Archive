---
title: "bridge with ipw3945 not working in gutsy"
date: 2007-12-15
forum: Networking &amp; Wireless
---

### Post by raguerra on 2007-12-15
Hi,

After upgrading to gutsy (x64) i can't use my WiFi connection as a bridge for vmware, the bridge works perfectly with my ethernet connection, do i have to activate bridging for wireless somewhere?  It worked before updating :(

---

### Post by yottabit on 2008-01-09
I, too, am having the exact same problem, although I'm on gutsy x86 (native install though, no upgrade).

Using NAT works, however, but it causes timeouts of my VPN client inside the Windows XP VM. :(

Any ideas how to enable/fix the bridging?

J

---

### Post by h-kan on 2008-01-09
Dont know if this will do it for you but for me it worked.. 

(1) Download Hauke-m's patched vmnet.tar file from here:

[http://www.hauke-m.de/fileadmin/vmware/vmnet.tar](http://www.hauke-m.de/fileadmin/vmware/vmnet.tar)

(2) Go to /usr/lib/vmware/modules/source and rename the original vmnet.tar to vmnetOLD.tar or something like that.

(3) Copy Hauke-m's patched vmnet.tar to /usr/lib/vmware/modules/source/.

(4) Run vmware-config.pl.

Than start vmware ant select bridge and see if it works

---

### Post by yottabit on 2008-01-09
hmmm, I would really like to find a solution that does not involve me installing all the build tools on my system since space is limited...

I did just talk with a friend that suggested the ipw3945 does not work in promiscuous mode, and dmesg shows promiscuous...

He did suggest the iwlwifi userspace driver does work with bridging, and also suggested perhaps vmware-player works where vmware-server does not, so I'm going to try both of those next.

---

### Post by AhJah on 2008-01-16
hello

I've tried this solution, building kernel modules for vmnet still fails even if using the suggested vmnet.tar file.

i'm on Gutsy with kernel 2.6.22-14
```
Would you like to skip networking setup and keep your old settings as they are?
(yes/no) [yes] 

Extracting the sources of the vmnet module.

Building the vmnet module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmnet-only'
make -C /lib/modules/2.6.22-14-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /tmp/vmware-config0/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config0/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config0/vmnet-only/userif.o
/tmp/vmware-config0/vmnet-only/userif.c: In function ‘VNetCopyDatagramToUser’:
/tmp/vmware-config0/vmnet-only/userif.c:630: error: ‘const struct sk_buff’ has no member named ‘h’
/tmp/vmware-config0/vmnet-only/userif.c:630: error: ‘const struct sk_buff’ has no member named ‘nh’
/tmp/vmware-config0/vmnet-only/userif.c:636: error: ‘const struct sk_buff’ has no member named ‘h’
make[2]: *** [/tmp/vmware-config0/vmnet-only/userif.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmnet-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [vmnet.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmnet-only'
Unable to build the vmnet module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

I'm going to move to virtualbox, if I can successfully convert my exixting VM.

ciao
leo

---

### Post by yottabit on 2008-01-16
Okay so I gave up and decided to try some more methods. The iwlwifi still did not bridge my 3945 correctly with VMware Server or Workstation or Player, and I had reliability problems with it, so I went back to the ipw3945 driver.

Next I downloaded the latest ipw3945 source, enabled all of the promisc/monitor options in the makefile, and compiled. The new module loads fine in the kernel, and putting it manually into monitor mode via iwconfig did not report any errors. However, it still did not bridge with VMware.

On another note, I routinely use Etherape and it seems to work just fine with the stock ipw3945 module in the restricted modules, and with the one I custom-compiled. This operates in promisc, no? So perhaps the problem isn't with the wifi driver after all, but with VMware's bridging code?

---

### Post by raguerra on 2008-02-04
> **h-kan said:**
> Dont know if this will do it for you but for me it worked.. 

(1) Download Hauke-m's patched vmnet.tar file from here:

[http://www.hauke-m.de/fileadmin/vmware/vmnet.tar](http://www.hauke-m.de/fileadmin/vmware/vmnet.tar)

(2) Go to /usr/lib/vmware/modules/source and rename the original vmnet.tar to vmnetOLD.tar or something like that.

(3) Copy Hauke-m's patched vmnet.tar to /usr/lib/vmware/modules/source/.

(4) Run vmware-config.pl.

Than start vmware ant select bridge and see if it works

Thanks a lot!!! it works :)

---

### Post by h-kan on 2008-02-04
> **raguerra said:**
> Thanks a lot!!! it works :)

No problem!

Have in mind that this does NOT work if you upgrade to the 2.6.24 kernel...

---

### Post by ethridgt on 2008-02-22
h-kan's patched vmnet.tar file worked for me too.

Thanks.

---

### Post by Starks on 2008-02-22
patched vmnet does not work with ipw3945

---

### Post by eras2r on 2008-03-05
I had originally tried running h-kan's patched vmnet.tar on VMWare Server 1.04 under Gutsy.  This indeed did fix the bridging capabilities of the wireless card, however it gave me terrible CPU problems where vmware-vmx was eating up 100% of my CPU with an idle XP guest host.

In my simple brain I attributed this to the fact that h-kan's vmnet.tar is from the source of VMWare Workstation 6 and not Server 1.04.  So I read through his site on what he changed in the bridge.c file and made my own patched vmnet.tar that comes directly from the VMWare Server 1.04 source code.  After moving this to the /usr/lib/vmware/modules/source dir, and running vmware-config.pl I tested everything out.  Bridging worked and I had no CPU issues.

So I am attaching my vmnet.tar file that I created off of the VMWare Server 1.04 source.  If you've run the any-any patch or previously used another vmnet.tar or vmmon.tar you will want to clear out the /usr/lib/vmware/modules/source dir and copy over the original files from the vmware-server-1.04 tar.gz that comes from vmware's site.  Or simply re-install vmware-server.  Once you have the original files in place, simply copy my vmnet.tar over the original one in /usr/lib/vmware/modules/source.  Re-run vmware-config.pl.  Then you should be set.

This is currently working an tested on Ubuntu Gutsy 7.10 running kernel 2.6.22-14-generic on a Dell Latitude D820.

I am new to these forums and not sure whether I can attach this file to my post.  If it gets removed, please PM me if you have a website that this can be posted on for everyone to download.

Regards,
e

---

### Post by gpao1966 on 2008-03-09
Thanks eras2r!! It worked a treat for me on my VAIO. So far no CPU hogs yet.

---

### Post by Starks on 2008-03-11
Does any of these solutions require messing around with the wireless drivers?

---

