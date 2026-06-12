---
title: "Download management puzzle:  Ubuntu vs Wind"
date: 2007-03-03
forum: Networking &amp; Wireless
---

### Post by Michl on 2007-03-03
{New:  if you go to my last post, you will see there is a 
solution to this puzzle.  I am thinking that maybe this
is a solution to the many dial-up modem problems that
people seem to have in ubuntu.}

I use the diql-up modem USR 5610b without any problems in
Ubuntu -- except when downloading.

For example, when downloading in Ubuntu, my modem keeps
disconnecting, say every 5 or so minutes.  I've just been trying
to download a 19mb file and just had to give-up.  (This does
not happen when doing email, for example, although even
there it disconnects more often than in windows, but not
every five minutes.)

This happens if I download with synaptic, firefox, anything, even
from the terminal.  The terminal is nice because I never lose
the cache with wget -c, but in synaptic sometimes the cache is
lost and I must start all over again.

But the download manager in Windows 2k has no problems.  It
was just downloading for an hour without a glitch, and I have
downloaded all night long without a glitch.

I have tried adding S=255 to the init string, S15=128, changing
the speed up and down, but none of this has worked.

There HAS to be a way of configuring this very modem to do
the same in Ubuntu.  I just can't accept that Ubuntu is inferior
in managing downloads. 

Someone has to know how.

Michael

---

### Post by Michl on 2007-03-05
Ok, let me be briefer:

Why does my modem (USR 5610b) disconnect every five minutes
with Ubuntu when downloading (Synaptic, wget, firefox, whatever)
but in Windows (2k) I can download all night without it ever
disconnecting?

Help!
Michl

---

### Post by Michl on 2007-03-06
Well, here is the solution.  Windows does a better job
automatically fine-tuning the data commands for the
dial-up modems than at least does gnome-ppp or wvdial. 

Per instructions (I should have thought of this...but
I didn't) from USR, I simply compared the dial-up
log-in Windows and Ubuntu.  There were so many more
data commands in Windows.  So I looked them up and located 
ones that seemed relevant, and tried them out.  Well, Eureka, this 
is the one that did the trick:
S19=0
I noticed that when downloading, there are times when
there is no data activity and after that it jumps way high
and continues.  Well, without S19=0, the modem would
hang-up during those times.  S19=0 disables this timer
and now my modem downloads and downloads at least
as good as under Windows.  Actually, without the annoying
disconnects, it is much faster in Ubuntu

Yippee. :guitar: 
Michael

---

