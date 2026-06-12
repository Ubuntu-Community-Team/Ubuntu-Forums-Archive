---
title: "LIVE CD start in Classic?"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by skooter1121 on 2011-04-29
11.04 Can the live cd 'Desktop' version default to the Classic menu rather than unity?

Seems I'm unable to log out of the LIVE version to select the Classic version.

Any ideas?

Or is there a 11.04 live version available for default classic?


SFS

---

### Post by beew on 2011-04-29
Don't think so. The changed settings wouldn't be saved in the CD so it would be lost at reboot. If you want to save changes make a live usb with persistence, it is a lot faster too. Live CD is so yesterday :)

---

### Post by mc4man on 2011-04-29
They removed the log out option from the live session for some nonsense reason

Try either 
Ctrl+Alt+SysRq+k 
or search keyboard in the dash > layouts > options > and enable the 'key sequence to kill..' and use that (Ctrl+Alt+backspace
Then login using ubuntu as the  username, no password, pick classic from the dropdown

---

### Post by skooter1121 on 2011-04-29
Thanx for the reply.



Not sure what a 'live usb with persistence.' I know how to make a live usb, from a cd, or ISO but how to keep any updates/changes? Is there a special make boot system disk software for this?

SFS

---

### Post by mc4man on 2011-04-29
This may be an easier way to produce a logout  from live session (in power button dropdown
In terminal
```
gconftool-2 -s -t bool /apps/indicator-session/suppress_logout_menuitem false
```

---

### Post by corncob on 2011-04-29
Strange!  My live (64 bit) CD starts up with the classic desktop.  I just thought that's what it did.  I am having problems though  --  I'm only given the choice of overwriting windows or 'something else' (manually setting up partitions).  I think there should be a 3rd choice (install along side windows) so I'm downloading it again (its taking forever).

---

### Post by SketchMan3 on 2011-04-30
The logout option is under the "System" menu now.

---

