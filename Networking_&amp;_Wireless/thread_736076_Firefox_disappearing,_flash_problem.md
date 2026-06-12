---
title: "Firefox disappearing, flash problem"
date: 2008-03-26
forum: Networking &amp; Wireless
---

### Post by adamcknowles on 2008-03-26
Hi,

I recently upgraded to Gutsy (Xubuntu), and since then I've been getting problems with Firefox disappearing when I try to connect to specific web pages.  I'm sure that it is a Flash related problem, as it only seems to occur on webpages which use Flash. I can temporally solve it by reinstalling Flash 9 (in /usr/lib/firefox) and Firefox doesn't disappear again for the rest of the session.  The trouble is that next time I log in, I get the same problem again.

I've tried running Firefox from the terminal and when it disappears I get the following output:

> The program 'gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 115 error_code 8 request_code 145 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

If anybody has any ideas on how to permanently fix this problem, I'd be grateful, as I don't want to keep re-installing Flash every time I go on the Internet.

Thanks,

Adam

---

### Post by Eiríkr on 2008-03-26
Search around the Forum, or maybe Google; I recall reading recently that Adobe's Linux Flash implementation is horribly buggy.  I think any permanent fix would depend on either a) Adobe getting off its toucas and fixing the Linux Flash plug-in, or b) someone else creating a replacement.  I don't know about you, but I'm not going to hold my breath on either one... :-|

Cheers,

Eiríkr

---

