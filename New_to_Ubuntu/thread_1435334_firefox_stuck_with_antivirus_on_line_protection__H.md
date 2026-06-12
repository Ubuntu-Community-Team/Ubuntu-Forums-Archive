---
title: "firefox stuck with antivirus on line protection  HELP"
date: 2010-03-21
forum: New to Ubuntu
---

### Post by medphys on 2010-03-21
Hi all,

Was searching the forums today when I clicked on a file about how to backup MBR file.  It launched  an on line virus scam and I cannot get out of Firefox.  I am running Ubuntu 9.10.  


Please HELP  How do I shut down Firefox and get rid of the antivirus??


Thanks in Advance

---

### Post by Jakey_TheSnake on 2010-03-21
Can't get out of firefox? Open up a terminal (Applications > Accessories > Terminal) and type "killall firefox".

---

### Post by medphys on 2010-03-21
Jakey_TheSnake

Thank You,  It worked.  I appreciate your quick reply.  Am writing it down for future use.

---

### Post by 2hot6ft2 on 2010-03-21
> **medphys said:**
> Hi all,

Was searching the forums today when I clicked on a file about how to backup MBR file.  It launched  an on line virus scam and I cannot get out of Firefox.  I am running Ubuntu 9.10.  


Please HELP  How do I shut down Firefox and get rid of the antivirus??


Thanks in Advance
In THIS forum? Where?

---

### Post by medphys on 2010-03-22
I am not sure and am trying to find it.  Will report back when I do.

---

### Post by Paqman on 2010-03-22
> **medphys said:**
> 
Thank You,  It worked.  I appreciate your quick reply.  Am writing it down for future use.

One that will work for any app is:

Alt-F2, then type:
```
xkill
```
and click on the offending app to kill it.

---

### Post by 2hot6ft2 on 2010-03-22
> **medphys said:**
> I am not sure and am trying to find it.  Will report back when I do.
Please do. This forum doesn't tolerate malicious commands or links.

---

### Post by mkvnmtr on 2010-03-23
If you are using gnome there is a kill switch you can add to the panel. Works like the xkill command but you do  not need to open a terminal. For me it is a must have because sometimes you can not get a terminal to open.

---

### Post by Gone fishing on 2010-03-23
I suppose it maybe possible that your mozilla profile is damaged or infected it maybe necessary to delete the .mozilla directory in you profile.

However, where did you find the link? I've found no malicious advise on these forums.

---

### Post by oldsoundguy on 2010-03-23
> **mkvnmtr said:**
> If you are using gnome there is a kill switch you can add to the panel. Works like the xkill command but you do  not need to open a terminal. For me it is a must have because sometimes you can not get a terminal to open.

+1 .. it is called Force Quit and is in the panel applet library. VERY HANDY!

As far as FF hanging up.  I have had it happen when I clicked on a malware file that was embedded in a site waiting on some poor Windows user.  Especially those "scans" that claim to clean and speed up your computer.

When I find those kinds of sites, I catalog and report them to another forum I belong to that assists Windows users.

---

### Post by uRock on 2010-03-23
Also using Ctrl+W closes the window. I just did a few searches for "backup MBR ubuntu" and came up with no threads with crazy links. If you are not running the NoScript add-on, now is a good time to install it.

---

### Post by dE_logics on 2010-03-23
Hummm...interesting.

Can you give us the link?

---

### Post by egalvan on 2010-03-23
For rock-solid MBR information, none other than our own hermanAB has an excellent web site...
here is the link to the MBR part...

[http://members.iinet.net.au/~herman546/p6.html](http://members.iinet.net.au/~herman546/p6.html)

---

### Post by 2hot6ft2 on 2010-03-23
> **egalvan said:**
> For rock-solid MBR information, none other than our own hermanAB has an excellent web site...
here is the link to the MBR part...

[http://members.iinet.net.au/~herman546/p6.html](http://members.iinet.net.au/~herman546/p6.html)
+1
I haven't been to his site in about 10 years. Nice to see that he's still keeping it up. Thanks for the link.
:guitar:

---

