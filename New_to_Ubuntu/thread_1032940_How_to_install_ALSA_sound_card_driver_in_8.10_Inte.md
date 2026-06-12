---
title: "How to install ALSA sound card driver in 8.10 Interpid?"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by taylor102387 on 2009-01-06
](*,) OK, I have posted this issue five times in the last day and I have made no progress. Here are all of the threads:

[HTML]
http://ubuntuforums.org/showthread.php?t=1032852
http://ubuntuforums.org/showthread.php?t=1032861
http://ubuntuforums.org/showthread.php?t=1032795
http://ubuntuforums.org/showthread.php?t=1031995
http://ubuntuforums.org/showthread.php?t=1032029
[/HTML]

If I continue this, it's going to drive me mad!!!:evil: I simply dont get why every assumes that my sounds muted? "IT'S NOT!" To prove it, here is what I get when I type in "aplay -l" in a terminal: 

```
taylor@Taylor-laptop:~$ aplay -l
aplay: device_list:215: no soundcards found...
```

And it was working just hours before. And to show that Ubuntu has found it, here is what I get when I type in "lspci -v" in a terminal

```
taylor@Taylor-laptop:~$ lspci -v
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Hewlett-Packard Company Device 30a5
	Flags: bus master, fast devsel, latency 0, IRQ 7
	Memory at d0340000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel
```

I really just need to install the hda-intel drivers. So please give me a resonable anwser and tell me some shell commands. And stay on for a couple on miniutes to quick reply, because I am montering this post.     
Please
:confused:

---

### Post by gettinoriginal on 2009-01-09
These are all the sound issue threads that I have used and solved the issue:
[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506),
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012),
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by d0cta ew on 2009-01-09
@ Taylor-

I just installed Intrepid on Wednesday, I'm having the sound card problem as well.  I'm going to try these threads that gettinoriginal posted (thanks btw :D); repost here if any of them work for you, it'll be a few hours before I can try them.

---

