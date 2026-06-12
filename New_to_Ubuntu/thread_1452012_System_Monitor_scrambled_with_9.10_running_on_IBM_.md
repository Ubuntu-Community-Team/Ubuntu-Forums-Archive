---
title: "System Monitor scrambled with 9.10 running on IBM X31"
date: 2010-04-11
forum: New to Ubuntu
---

### Post by ben1986 on 2010-04-11
Hi,  I installed Ubuntu Netbook Remix to my IBM Thinkpad X31, but it couldn't hack the graphics required for the fancy new desktop display, and would scramble the names of the icons, and flash static everywhere when I moved the mouse. Disabled maximus, disabled netbook-launcher, got everything how I like it again (basically classic Ubuntu).  Disabled the system notifications, because they showed up as a solid black bar, but now I find that System Monitor is scrambled when I open it up.  This is a problem, because I'm running banshee, and it's having issues with scanning my music collection, but I can't open system monitor to kill the process.

I found this bug report, which seems also to contain a solution, but I'm not confident at all about implementing it.  

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/491538](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/491538)

Any guidance would be appreciated, is this something I should be doing?  Or should I just leave it alone, and hope that Lucid fixes it, since it apparently didn't happen in Jaunty?

Thanks to anyone who can give me a hand.

---

### Post by venicequeen7706 on 2010-04-11
I don't know enough to advise either way about that fix, but if all you are looking to do is monitor and kill processes you can do that from the terminal. use the command "top" look for in the right hand column for the process you want to kill then look to the left column for that process' PID then use the command "kill -9 PID" to kill the process.

---

### Post by ben1986 on 2010-04-20
Cheers, I'll use that for now.  Ubuntu runs ok, I think its just the computer is getting really old.  Bit annoying!  Ill post here if the Lucid update on the 29th changes anything

---

### Post by ben1986 on 2010-04-29
For anyone finding this post in the future I just updated to the 10.04 Release Candidate, and it was fixed, and my ancient X31 Thinkpad happily runs the netbook remix desktop effects (might still disable them though).  System monitor loads merrily.

---

