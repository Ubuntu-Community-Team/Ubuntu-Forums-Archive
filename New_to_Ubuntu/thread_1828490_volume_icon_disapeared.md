---
title: "volume icon disapeared"
date: 2011-08-19
forum: New to Ubuntu
---

### Post by vagelism on 2011-08-19
Hello to all!
I lost the volume icon from my panel....
I click add to panel but I can not find it there!
Any ideas?
Thank you!

---

### Post by n213978745 on 2011-08-19
Would you mind to give us details about click to "add" to the panel?

If you are using Ubuntu 11.04, and you want to reset the panel
try moving the following to trash:
$HOME/.gconf

log out and log in and see if this works.  Your computer should be re-create the .gconf under your home directory and your panel should be reset.  If it works, you can delete the .gconf from trash, or restores it in case making it worse.

---

### Post by vagelism on 2011-08-19
> **n213978745 said:**
> Would you mind to give us details about click to "add" to the panel?

If you are using Ubuntu 11.04, and you want to reset the panel
try moving the following to trash:
$HOME/.gconf

log out and log in and see if this works.  Your computer should be re-create the .gconf under your home directory and your panel should be reset.  If it works, you can delete the .gconf from trash, or restores it in case making it worse.

So I go to the panel and right click there. I select "add to panel.."
Then a list of many small aplets appear ... but the icon with the speaker is not there to select it.
THANK YOU.

---

### Post by abnordude on 2011-08-19
Is there an icon called indicator applet in add to panel....
If yes click that.....

---

### Post by vagelism on 2011-08-19
> **abnordude said:**
> Is there an icon called indicator applet in add to panel....
If yes click that.....

Yes it is and works great!
Thank you!

---

