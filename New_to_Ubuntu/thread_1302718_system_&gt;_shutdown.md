---
title: "system &gt; shutdown"
date: 2009-10-27
forum: New to Ubuntu
---

### Post by mvalviar on 2009-10-27
I remember having shutdown, lockscreen, and log out option right under the system menu but they aren't there anymore. How can I bring them back? I tried edit menus but I can do it from there.

---

### Post by Jason Cook on 2009-10-27
I am hoping an answer is found to this. Some of my menu items disappeared.

---

### Post by rustutzman on 2009-10-27
Right click the panel. "Add to panel" "Indicator session applet" I think that's the name.

Russ

---

### Post by mvalviar on 2009-10-27
I think you're referring to the fast user switcher applet. I don't want that on my panel. My wife wants the options I mentioned under the system menu.

---

### Post by philinux on 2009-10-27
system>admin>login window

Click the local tab, make sure Show Actions Menu is ticked.

---

### Post by mvalviar on 2009-10-27
The checkbox is ticked.

---

### Post by pootan on 2009-10-27
Right click the panel >add to panel then choose Shut Down, Log Out and Lock Screen

Edit: Ahh, I see you said under system menu. I had these in 8.10 and lost them after upgrade to 9.04

---

### Post by kestal on 2009-10-27
curious, you do not have "User Switcher" running, do you? (where you can see your username), because if that is up and running, those options get moved from System to when you click on your username. Not sure if this applies in this case or not.

If there is no other workable solution, what you could do is edit the menu and add logout and shutdown. the commands to use would be:

gnome-session-save --shutdown-dialog
gnome-session-save --logout-dialog

I think. However the downside to this is that its not places at the very bottom. Though you could create a separator above it and it doesn't look that bad.

---

### Post by pootan on 2009-10-27
Further reading here:

[http://ubuntuforums.org/showthread.php?t=1133933](http://ubuntuforums.org/showthread.php?t=1133933)

---

### Post by mvalviar on 2009-10-27
Weird, I don't have fusa yet I don't have those options under system menu. I guess I'll just have to do what you suggested and wait for a karmic upgrade.

---

### Post by pootan on 2009-10-27
The only way I got menu back was to Use Ubuntu Tweak and click System>Security and check disable Fast User switching and then unchecking it. This showed a panel object related to fast user switching on the right hand corner of the panel. After I deleted it the menu options reappeared under the system menu. 

So if you have the panel object for fast user switching as a panel object then you need to remove it from your panel to get your menu back or alternatively use the workaround in the thread I posted. If you have Disable Fast user switching enabled in ubuntu tweak then any panel objects related to Fast User Switching will be hidden but still on your panel.

---

