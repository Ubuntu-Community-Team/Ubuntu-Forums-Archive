---
title: "White screen at login after upgrade to 8.10"
date: 2009-10-13
forum: New to Ubuntu
---

### Post by jesudeus on 2009-10-13
i attempted to upgrade to 8.10. everything went smooth, then i restarted and at the time when the login screen should pop up it turns white and freezes. I believe it has to do with my unichrome video driver and thought i might need to go to the openchrome driver. those are my thoughts, but i am open to suggestion.

---

### Post by anewguy on 2009-10-13
At the time of the white screen, hold down CTRL/ALT and press F1.  Does a text screen come up asking you to log in?  If so, you could try reconfiguring X to use the VESA driver and see if you get X windows back.  If so, you could work from there to get your openchrome driver.

Dave :)

---

### Post by dineshs on 2009-10-13
I also had the same problem and not being an expert reloaded ubuntu in safe graphics mode,which worked for me.I think experts in this forum can suggest easier methods

---

### Post by anewguy on 2009-10-13
Let me know if the CTRL/ALT F1 gets you to a log in prompt.  We can go from there.

Dave :)

---

### Post by jesudeus on 2009-10-13
ill get back to you on that after i get home from work.

---

### Post by jesudeus on 2009-10-13
ok the ctr+alt+f1 works.

---

### Post by anewguy on 2009-10-13
First, log in to this text terminal using your normal userid and password.

Then, copy and paste in the following:

sudo dpkg-reconfigure xserver-xorg <press enter>

When the prompt for type comes around, just choose VESA for now, then finish up.

Then, copy and paste in the following:

sudo /etc/init.d/gdm restart <press enter>

After X restarts, hold down CTRL/ALT and press F7 - this should get you to a X window login screen - try logging in again and see what happens.

BTW - if you are looking for the openchrome driver because of a Via S3 Unichrome graphics adapter, be aware that you may not be able to do everything like compiz, etc. - just depends.  I had a Gateway laptop that had that graphics adapter in it and I had to install openchrome, but it wasn't the best and I eventually just got rid of the laptop.

dave :)

---

### Post by jesudeus on 2009-10-13
it never asked anything about video graphics, just the key board.

---

### Post by jesudeus on 2009-10-13
xorg.conf has no section for driver either

---

### Post by jesudeus on 2009-10-14
ok i fixed it. tried to use vesa, got a little farther but still froze. so i just compiled the openchrome driver and used it. got the instructions from here= [https://help.ubuntu.com/community/OpenChrome]("https://help.ubuntu.com/community/OpenChrome"). i dont really use compiz so this will work until i upgrade again.

---

