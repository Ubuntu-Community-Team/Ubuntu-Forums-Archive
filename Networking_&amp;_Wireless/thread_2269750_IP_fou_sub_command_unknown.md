---
title: "IP fou sub command unknown"
date: 2015-03-17
forum: Networking &amp; Wireless
---

### Post by Harry.k on 2015-03-17
After reading [this]("http://lwn.net/Articles/614348/") article about tunneling over UDP, I tried the command "[COLOR=#000000]ip fou add port 5555 ipproto 4" on my remote Ubuntu server. On doing this, I get an error that says object "fou" is unknown. Fou is also missing from the list of subcommands listed in "IP help". What can I do to get fou?[/COLOR]

---

### Post by papibe on 2015-03-17
Hi Harry.k.

Which version of Ubuntu are you running?

Could you open a terminal, run these commands and post back the output (you can copy/paste the text)? 
```
lsb_release -a

uname -a
```
That article seems to detail a new feature for kernel 3.18. I believe you would have to be running 15.04 (beta) to get those features.

Regards.

---

### Post by Harry.k on 2015-03-17
Oh... I just skipped over the first paragraph... my bad.

```
$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty
```

```
$ uname -a
Linux ip-*-*-*-* 3.13.0-44-generic #73-Ubuntu SMP Tue Dec 16 00:22:43 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

How can I switch to 3.18 without changing to 15.04?

---

### Post by papibe on 2015-03-17
You can.

The task is called 'installing a upstream kernel'. You can read the basics here: [Kernels Mainline Builds]("https://wiki.ubuntu.com/Kernel/MainlineBuilds").

Although you can find 3.18, I'd recommend selecting the one they are using right now, which is v4.0-rc4.

This is an advance task and there's no guaranties you would not run into problems.

If you are just testing that feature, installing 15.04 on a VM could be an easier and safer alternative too.

Hope it helps. Let us know how it goes.
Rega

---

### Post by noanonymity00 on 2015-04-27
I get the same error on 15.04.  Any thoughts?  Has anyone successfully used the example from the original post?


No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid

Linux 3.19.0-15-generic #15-Ubuntu SMP Thu Apr 16 23:32:37 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

---

