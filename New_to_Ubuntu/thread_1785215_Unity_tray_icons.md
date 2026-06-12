---
title: "Unity tray icons"
date: 2011-06-18
forum: New to Ubuntu
---

### Post by beew on 2011-06-18
I reactivated tray icons for open applications by changing the whitelist to ['all'] in dconf-editor. Now tray icons appear when I open applications but when there are non default tray icons (e.g VLC, LibreOffice) on the panel, the volume control stops working. 

Does anyone experience the same problem?

---

### Post by jtarin on 2011-06-18
I don't, but then again I'm not using Unity.:p

---

### Post by beew on 2011-06-18
> **jtarin said:**
> I don't, but then again I'm not using Unity.:p

Thanks for trying to bump the thread but you don't have to do it just 10 minutes after I posted. :)

---

### Post by jtarin on 2011-06-18
> **beew said:**
> Thanks for trying to bump the thread but you don't have to do it just 10 minutes after I posted. :)Is 3 hours sufficient?:P

---

### Post by hubertofliege on 2011-06-22
How did you get tray icons back?  My password manager (KeePassX) always sits in the tray, and without a tray, it just disappears, but keeps running in the background.  I really want my tray icons back.

---

### Post by beew on 2011-06-25
> **hubertofliege said:**
> How did you get tray icons back?  My password manager (KeePassX) always sits in the tray, and without a tray, it just disappears, but keeps running in the background.  I really want my tray icons back.
I get them by whitelisting all applications on the panel. First install  dconf-tools from Synaptic. Then open a terminal to type>   dconf-editor When the dconf-editor appears go to desktop >  Unity > panel and change the value of systray-whitelist to ['all']  (you have to enter it exactly as I write here including the square  blacket) You may have to reboot or logout and login for that to take  effect. If it doesn't work, open dconf-editor again and make sure that  the value of systray-whitelist has not reverted to default.

---

### Post by beew on 2011-06-25
Well this is the workaround. If you click the logoff button (on the far right on top) first and move the cursor to the volume control it would work. This is yet another weird bug possibly because the global menu has messed up the top panel just for a few pixels that most people probably wouldn't care about.

---

