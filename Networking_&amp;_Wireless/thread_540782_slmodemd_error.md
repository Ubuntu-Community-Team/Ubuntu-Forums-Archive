---
title: "slmodemd error"
date: 2007-09-02
forum: Networking &amp; Wireless
---

### Post by Locutus_of_Borg on 2007-09-02
Hello, I am new to linux and recently installed Kubuntu 7.04 and am trying to use dial-up to connect.  I used scanModem and followed all the directions I could find for my Intel Corporation 82801G  modem.  I installed slmodemd and ALSA drivers that were recommended, but when I try to dial, I get "period size 48 not supported by playback (64)" within the terminal window that is running the slmodem deamon..I also get a "No carrier" message in the KPPP dialer window.  I searched for a while and came across a patch for this problem from [Hell Labs]("http://helllabs.org/blog/20070710/slmodem-period-size-48-not-supported/") and another suggestion from a different site addressing this problem: 
```
I'm not sure if this is a issue in alsa, it seems to be slmodemd's fault. slmodemd requests a period size of 48 using snd_pcm_hw_params_set_period_size_near() in setup_stream() and aborts if alsa returns anything different. Newer alsa versions return 64, and this should be gracefully handled by slmodemd. The following quick-and-dirty patch to slmodemd allows it to start and communicate, but proper error handling must be implemented:

diff -rud slmodem-2.9.11-20060727-orig/modem/modem_main.c slmodem-2.9.11-20060727/modem/modem_main.c
--- slmodem-2.9.11-20060727-orig/modem/modem_main.c 2005-09-22 10:05:27.000000000 -0300
+++ slmodem-2.9.11-20060727/modem/modem_main.c 2007-07-09 16:26:15.000000000 -0300
@@ -379,11 +379,13 @@
                ERR("cannot set periods for %s: %s\n", stream_name, snd_strerror(err));
                return err;
        }
+#if 0
        if ( rsize != size ) {
                ERR("period size %ld is not supported by %s (%ld).\n",
                    size, stream_name, rsize);
                return -1;
        }
+#endif
        rsize = size = use_short_buffer ? rsize * dev->buf_periods : rsize * 32;
        err = snd_pcm_hw_params_set_buffer_size_near(handle, hw_params, &rsize);
        if (err < 0) {
```
[Above from second to last reply, here.]("https://bugs.launchpad.net/ubuntu/+source/sl-modem/+bug/47809")

My question is, how/where do I add the above patches to get slmodemd to work correctly?  I did ask this question in the beginners section of this forum, but got no response and thought this would be a more appropriate place to ask.  Thank you to anyone who can help.

=^_^=

---

### Post by Auax on 2007-09-03
Bump for much needed help.

---

### Post by Locutus_of_Borg on 2007-09-03
thanks for the bump :)

i am really hoping to get this working so i can stop using microsoft produts ;p

---

### Post by Auax on 2007-09-05
Much welcome... it doesn't seem like anybody wants to help though. :\

---

### Post by Locutus_of_Borg on 2007-09-05
i doubt many people use dial-up so perhaps no one familiar with this problem has seen this post?

---

### Post by Auax on 2007-09-09
Possibly... I guess we should keep bumping it.

Have you made the topic at Kubuntuforums yet?

---

### Post by Locutus_of_Borg on 2007-09-13
yes, i made it there, and even less replies...

i suppose i can wait a few more weeks before we get proper cable internet, and in the mean time, make due with using wireless, and just use windows for dial-up...

=>_<=

---

### Post by Locutus_of_Borg on 2007-09-26
lalalalala

wawawawawaaaahh

---

### Post by Locutus_of_Borg on 2007-09-26
i tried re-installing teh sl-modem-daemon package, missing ungrab_winmodem and slamr modules.

hlp plz

---

### Post by _duncan_ on 2007-09-26
I have no experience working with modems that use ALSA drivers, but have used sl-modem-daemon with the open-source smartlink drivers past couple of years. So please view my post with the proverbial grain of salt.

In my case, the newer sl-modem-daemon package that comes with feisty (2.9.10+2.9.9d+e-pre2-5ubuntu1) doesn't work for my modem, but the older edgy package does (2.9.10+2.9.9d+e-pre2-5build1).

If you're desperate, you may want to give the older sl-modem-daemon package a try. Here's the link:

[http://packages.ubuntu.com/edgy/misc/sl-modem-daemon]("http://packages.ubuntu.com/edgy/misc/sl-modem-daemon")

---

### Post by Locutus_of_Borg on 2007-09-26
thanks, i will try that and cross my fingers

---

### Post by wvczombie on 2007-10-25
I tried installing the old slmodem package but got the same error.  This is obviously a problem throughout the slmodem history as I have tried all the available compiled versions from their site.

I really need a compiled slmodemd that will handle the new period size.

VERY FRUSTRATED!

---

### Post by Locutus_of_Borg on 2007-10-25
the latest sl-modem-daemon handles the period size error, but produces a new one:
"cannot setup hw params for playback: invalid argument"

have not been able to find fix/help on this issue anywhere

---

### Post by wvczombie on 2007-10-25
What version is that?  I have version 2.9.11 which is still giving the period error.  Did I miss a new version?

---

### Post by Locutus_of_Borg on 2007-10-25
I have SLMODEMD.gcc4.1.tar.gz that i got from [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)

---

### Post by wvczombie on 2007-10-25
I guess I stand corrected.  I forgot that I had reverted back to a pre-release version.  Once put back to the same version, I get the same results.

---

### Post by Locutus_of_Borg on 2007-10-25
yeah,i wish someone would figure out a fix for that..

---

### Post by mickeyWD on 2008-01-04
Hi,
I'm using slmodem
 
```
WvDial Modem<*1>: NO CARRIER
... ATDnumber
WvDial <Warn>: No Carrier! Trying again.
```
also for me.

---

