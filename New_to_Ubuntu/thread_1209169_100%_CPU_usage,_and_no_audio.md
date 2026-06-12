---
title: "100% CPU usage, and no audio"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by metallicamaster3 on 2009-07-10
For some reason my CPU usage is at 100%. When I go to reboot, I get warned that "Unknown Application" is trying to start, and that's what's probably causing my CPU to be so high... HELP! My temperatures at 100% CPU usage all the time come to about 50C.

My audio doesn't work. I forgot to enable it in the BIOS, but now it still won't work after enabling. lspci reveals this:

> 00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
        Subsystem: Biostar Microtech Int'l Corp Device 820f
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
        Memory at efff4000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>Anyone have any ideas on these?

I'm on 64-bit Jaunty.

---

### Post by QIII on 2009-07-10
Type

top

in the CLI.

Click CTRL + C to get back to the command line.

Post the results.

---

### Post by metallicamaster3 on 2009-07-10
I've ran top looking for the culprit already, and there hasn't been anything that's used the incinerating amount of CPU. System Monitor nor top reveals the culprit -- in top I'll see the most CPU usage app such as Xorg which uses maybe 6% ~_~.

---

### Post by QIII on 2009-07-10
Do you have Vino running?

---

### Post by metallicamaster3 on 2009-07-10
Aha! I disabled Vino and everything is nice now :). Thanks!!

---

### Post by metallicamaster3 on 2009-07-10
Now I just need to find a way to get my audio working. I know I have to use the snd-hda-intel module, but I can't enable it because it doesn't exist. Also; it didn't come up as available in lspci as mentioned in the first post.

---

### Post by QIII on 2009-07-10
Vino is a CPU hog of biblical proportions.  It's usually the first thing I ask about when people say there is nothing suspicious in top.

As for the sound, there are several things to work through for possibilities.

You might want to close this thread (Edit your first subject line and put "SOLVED: " in front of it.

Search the forums first for an answer.  If you can't find one, start a new thread.  It is usually best to have one subject per thread.

But I need to go to bed.

---

### Post by Cato2 on 2009-07-10
metallicamaster3 - try the Fixing Sound Problems link in my signature, it has a series of steps you can follow to try to sort this out.

FWIW I have the same sound driver, but underlying hardware varies - I ended up disabling PulseAudio (on Ubuntu 7.10) and using ESD, but you may find that's not necessary.

---

### Post by lovinglinux on 2009-07-10
> **QIII said:**
> Vino is a CPU hog of biblical proportions.  It's usually the first thing I ask about when people say there is nothing suspicious in top.

Me too and the problem was always this on every post I suggested this fix.  ;)

---

