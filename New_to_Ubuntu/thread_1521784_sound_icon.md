---
title: "sound icon"
date: 2010-07-01
forum: New to Ubuntu
---

### Post by DarinB on 2010-07-01
I have a real newbie question.
I added my nvidia config icon to my pannel and then tried to delete the standard hardware driver icon and the sound icon went with it?? how can i get just the sound icon back to regulate the volume.

---

### Post by s.fox on 2010-07-01
Hello,

I think that comes with the notification area.

**Right click on panel -->add to panel --> notification area**

Hope this helps,

-Silver Fox

---

### Post by qubic on 2010-07-01
> **DarinB said:**
> I have a real newbie question.
I added my nvidia config icon to my pannel and then tried to delete the standard hardware driver icon and the sound icon went with it?? how can i get just the sound icon back to regulate the volume.

You can try this because it worked for me. This will restore the panel to default and u ll **loose** any changes u did to the panel.  But I am new, you may get better suggestions.


> gconftool-2 --shutdown

rm -rf ~/.gconf/apps/panel

pkill gnome-panel

---

### Post by DarinB on 2010-07-01
notification area replaced did not include the sound speaker. 
deleting the panel was not a good idea because my panels are very customized and it would be a pain to re do them. 
I did save the /.gconf so i could replace it..
i am at the same point how to get the sound icon back in notification area.
the other sound controls to add are not as functional unless there is an app i can get to do the same i liked that i could put my mouse over it and use my scroll to increase or decrease the volume...
any other ideas that does not involve throwing out my panels. 
maybe edit the config file in /.gconf/apps/panel ??

---

