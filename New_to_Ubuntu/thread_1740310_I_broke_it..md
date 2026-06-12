---
title: "I broke it."
date: 2011-04-26
forum: New to Ubuntu
---

### Post by garl on 2011-04-26
I accidentally removed the chat/broadcast icon from my panel, so I was looking for a way to set it back to default. I checked in an old thread and it said to type this in the terminal:
sudo debconf gnome-panel
Once I did that, I got an error and closed the terminal. Where it use to say my username in the right hand corner, it now says root. And in places, all the documents, pictures, etc. are missing. Help!

---

### Post by cipherboy_loc on 2011-04-26
Log out and log back in. That will fix the root issue, but I have no idea on how to fix the gwibber(?) issue.


Cipherboy

---

### Post by garl on 2011-04-26
Ok, I'll try that. The command actually did bring the icon back, but messed up everything else. :P

---

### Post by yetiman64 on 2011-04-26
> **garl said:**
> Ok, I'll try that. The command actually did bring the icon back, but messed up everything else. :P

What is messed up now ?  

The mail/chat icon exists on the Indicator applet, and can usually be re-added to to panel by right clicking the panel, choose "add to panel" and add back the Indicator applet from the list. The command you used may have reset the panels to default. Does this appear to be the case?

BTW did you notice you also lost the volume icon when you lost the mail/chat icon? Both are on the Indicator applet.

---

### Post by garl on 2011-04-26
> **yetiman64 said:**
> What is messed up now ?
When I typed in the command from my initial post, my username in the right hand corner said  root and I couldn't access my documents, pictures, etc. After I logged out and back in, the icons were still missing. Then I did: gconftool --recursive-unset /apps/panel && killall gnome-panel

Adding Indicator Applet to panel seems simple enough (in case I make the same mistake twice). Now I know, thanks. (:

---

