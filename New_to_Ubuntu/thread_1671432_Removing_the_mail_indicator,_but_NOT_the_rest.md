---
title: "Removing the mail indicator, but NOT the rest"
date: 2011-01-20
forum: New to Ubuntu
---

### Post by jermza on 2011-01-20
Next to my speaker icon in the top panel, the little mail icon appears.  I don't want to remove that.  What I want to remove is the Evolution bit in the dropdown ("Mail", "Compose New Message" and "Contacts").  I am using Thunderbird, and have managed to install a nice little extension that shows me new mail in the same way as Evolution.

But since I am not using Evolution, I don't want those menu options, but I still want my Chat and Broadcast messages to remain.

Is this possible?

**EDIT:**

And, for whatever reason, is there a way to revert the changes at a later stage?

---

### Post by nomko on 2011-01-20
> **jermza said:**
> Next to my speaker icon in the top panel, the little mail icon appears. I don't want to remove that. What I want to remove is the Evolution bit in the dropdown ("Mail", "Compose New Message" and "Contacts"). I am using Thunderbird, and have managed to install a nice little extension that shows me new mail in the same way as Evolution.
 
But since I am not using Evolution, I don't want those menu options, but I still want my Chat and Broadcast messages to remain.
 
Is this possible?
 
**EDIT:**
 
And, for whatever reason, is there a way to revert the changes at a later stage?
 
 
I'm not quite sure which one you have to remove, but in synaptic search for indicator-me and indicator-message. I thought that indicator-me is for social networking.

---

### Post by pastalavista on 2011-01-20
Open synaptic package manager, search and remove "indicator-messages" or ```
sudo apt-get remove indicator-messages
``` To undo, just re-install it.

---

### Post by shoot2kill on 2011-02-28
I have just tried doing this as i am now using postler for email, and it creates its own entry in the menu.

however, after doing
```

sudo apt-get remove indicator-messages
killall gnome-panel

```

it removes the whole messages menu, including the envelope icon on the panel. i am just wanting to remove the mail items within the menu. 

any help greatly appreciated, thanks

---

