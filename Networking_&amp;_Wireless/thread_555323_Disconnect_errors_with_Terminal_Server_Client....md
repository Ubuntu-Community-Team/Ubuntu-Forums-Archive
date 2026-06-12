---
title: "Disconnect errors with Terminal Server Client..."
date: 2007-09-20
forum: Networking &amp; Wireless
---

### Post by ZeusABJ on 2007-09-20
I am using the Terminal Server Client to connect to administer a Windows 2003 server at home. Every time I close the RDP window, a dialog box pops up stating that an error has occurred and it automatically attempts a reconnect in 30 seconds. I know this is minor, but its just irritating enough to make me want a solution. Because I leave my server running on several tasks I need the ability to disconnect from it without logging out. Is there a way simply disconnect from the server without generating that message? I've been trying to figure this out fro some time now and I keep coming up empty handed. Also is there an easy way to disconnect while in full screen mode? For the life of me I can't figure out how to perform either of these tasks. 

Please help!

---

### Post by xtemplarx on 2007-09-25
Drat!  I saw the thread and hoped there would be a solution to this within.  I'm having the same problem, of course.  I daresay that everyone who uses the TSC that comes with Ubuntu (I'm using feisty) experiences the same thing.

It'd be nice if the client could disconnect cleanly.  What gives?

T

---

### Post by ZeusABJ on 2007-10-15
> **xtemplarx said:**
> Drat!  I saw the thread and hoped there would be a solution to this within.  I'm having the same problem, of course.  I daresay that everyone who uses the TSC that comes with Ubuntu (I'm using feisty) experiences the same thing.

It'd be nice if the client could disconnect cleanly.  What gives?

T

I have no idea, but we aren't the only ones:

[http://ubuntuforums.org/showthread.php?p=3535144#post3535144](http://ubuntuforums.org/showthread.php?p=3535144#post3535144)

Maybe if we all band together and keep posting requests for help on that thread someone will take notice and offer a solution. Its worth a shot!

---

### Post by kvasimongo on 2007-10-29
I reinstalled my computer the other day, and got this problem again. Since i couldnt remember how i fixed it last time, i tried searching here. But, as far as i can tell there is no fix to be found. Untill now!

As i was searching i remembered how to fix this:

Using either tsclient or gnome-rdp, the solution to connect to a Windows XP or 2003 maching is simple;

tsclient: Choose protocol RDP v5
gnome-rdp: On the saved session, under General, choose Windows XP/2003. This i assume sets the protcol version to RDP v5

Hope this works for you people, it worked for me :)

---

### Post by xtemplarx on 2007-10-29
> **kvasimongo said:**
> I reinstalled my computer the other day, and got this problem again. Since i couldnt remember how i fixed it last time, i tried searching here. But, as far as i can tell there is no fix to be found. Untill now!

As i was searching i remembered how to fix this:

Using either tsclient or gnome-rdp, the solution to connect to a Windows XP or 2003 maching is simple;

tsclient: Choose protocol RDP v5
gnome-rdp: On the saved session, under General, choose Windows XP/2003. This i assume sets the protcol version to RDP v5

Hope this works for you people, it worked for me :)

I got excited hoping this would do it for me!  I switched to v5 and STILL get the disconnect errors every time I'm finished with an RDP session, no matter how I disconnect. 

OH well.  I do think the v5 version acts a bit better, though.  :D

---

### Post by minutezero on 2007-11-07
[http://ubuntuforums.org/showthread.php?t=86131]("http://ubuntuforums.org/showthread.php?t=86131")

---

