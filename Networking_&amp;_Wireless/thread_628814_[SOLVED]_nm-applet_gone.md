---
title: "[SOLVED] nm-applet gone"
date: 2007-12-01
forum: Networking &amp; Wireless
---

### Post by Guitar John on 2007-12-01
OK, I did something stupid and now I can't figure out how to undo it.  I right-clicked on the nm-applet (for Network-Manager) and I intended to move it over.  What I did instead was to click "Remove From Panel".  I tried un-installing and re-installing from Add/Remove Programs.  Nothing.

Help!  ](*,)

EDIT: Also tried going into "System>Preferences>Sessions" and un-ticking the Network Manager from Start-Up items.  Then I re-booted, re-ticked the box, and re-booted again.  That got me online with a wireless connection.  So nothing is broken, but the applet doesn't appear in the Panel.

---

### Post by victorbrca on 2007-12-01
This should resolve:

Alt+F2 => nm-applet

As long as yoru notification area is still there....

Vic.

---

### Post by Guitar John on 2007-12-01
> **victorbrca said:**
> This should resolve:

Alt+F2 => nm-applet

As long as your notification area is still there....

Vic.

That didn't seem to work.  I re-booted, and I'm still getting a wireless connection, but the applet is still not there.  The only way I know I'm online is by opening Firefox or when one of my weather applets refreshes.

---

### Post by victorbrca on 2007-12-01
Do you still see the notification area on your panel?

Vic.

---

### Post by Guitar John on 2007-12-01
No, there's just a blank area where the applet used to be.
The password is still in the Keyring Manager, which is probably how it is connecting on re-boot.

---

### Post by victorbrca on 2007-12-01
What happens if you open pidgin or Rhythmbox Music player? Do you see their icon on the panel?


Vic.

---

### Post by Guitar John on 2007-12-01
AH!  Now you're onto something.  I attached a screenshot from my wife's computer and you are correct.  An applet opens showing Rhythmbox is playing.  That is not showing up on my computer, either.  I know it used to.

BTW, thank you for helping me with this.
EDIT: Resolved, screenshot removed.

---

### Post by victorbrca on 2007-12-02
ok, should be easy them... right click on the panel, "add to panel". Then scroll all the way down to utilities. Click on "Notification area", then add. Check if the panel looks a bit different. If it does and it's not showing nm-applet, do on a terminal:

```
killall gnome-panel
```

If that doesn't work, save all ur open files and hit Ctrl+Alt+Backspace

Hope that's it...  

Vic.

---

### Post by Guitar John on 2007-12-02
\\:D/
You are my new hero!!
Thank you, so much.

---

### Post by victorbrca on 2007-12-02
no problem... I did the same thing before and it took me a while to figure it out... so I definitelly know ur pain... lol


Vic.

---

