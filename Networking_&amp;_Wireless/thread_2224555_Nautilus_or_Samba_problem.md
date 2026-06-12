---
title: "Nautilus or Samba problem?"
date: 2014-05-16
forum: Networking &amp; Wireless
---

### Post by moonguide on 2014-05-16
I'm running Ubuntu 14.04 on a new machine. When I use Nautilus to 
connect to another machine on my local network sometimes it works and 
sometimes it doesn't. I don' t know if the problem is with Nautilus or 
Samba. I don't have any problems with Nautilus looking at the files on 
it's own machine, so I'm guessing the problem is with Samba, but it's 
Nautilus that dies.

This morning I clicked on Places > Network, then double clicked on 
Gateway-32-E-45. I got a dialog box that said:

[FONT=Fixedsys]Could not display “”.
The file is of an unknown type
[Select Application] [OK][/FONT]

I chose [Select Application]

Another dialog box opened with two options, both named Files. I chose 
the first one. The dialog box went away and Nautilus died.

I clicked on Places > Network > Gateway-32-E-45 again and got the normal 
Nautilus display of a number of directories on the Gateway machine. I 
double clicked on Public (the share on the Gateway machine) and got 
another dialog box:

[FONT=Fixedsys]Cold not open location ‘smb://gateway-32-e-45/public/’
Cache invalid, retry (internally handled)[/FONT]

After acknowledging that box I clicked on Places again and found "public 
on gate..." listed under "Browse Network" in the pane on the left hand 
side of the Nautilus window. I clicked on that and saw the files and 
directories on the Gateway Public share.

Any ideas on what might be going on? Any idea what log file(s) might 
have something to say about what's happening?

---

