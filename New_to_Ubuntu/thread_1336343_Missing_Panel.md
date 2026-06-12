---
title: "Missing Panel"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by gronez on 2009-11-24
Hi,

i managed to delete the panel-field that has stuff like volume control, or shows what programs are running. I hope you know what i`m talking about. Being that this field is rather useful, I would like to get it back. I`ve seen there`s an option to add stuff to the panel, but this does not hold what I want.
So, could anybody here point me to where I might find what I`m looking for? 

thx,
gronez

---

### Post by Dr Belka on 2009-11-24
You can right click an existing panel and use that to add a new panel.  After you drag and position the new panel on one of the edges of your screen, you can then right click on the panel, and and add things to the panel.  You are probably looking for either the system tray or the window list.  Did you delete the top or bottom panel?

---

### Post by 73ckn797 on 2009-11-24
If worse comes to worse, you can get the panels back up to the OEM state just after installation by running the following command using terminal.

Go to Applications/Accessories/Terminal

Paste this command in: ```
gconftool-2 --recursive-unset /apps/panel
```

Restart the computer and all will be back to normal. You will lose any launchers that you placed there.

---

### Post by gronez on 2009-11-24
Thanks for your quick responses, I just figured it out. In the 'add to panel' menu, it`s called 'notification area', I just wasn`t sure what to look for, but it`s all fine now.

---

### Post by 73ckn797 on 2009-11-24
> **gronez said:**
> Thanks for your quick responses, I just figured it out. In the 'add to panel' menu, it`s called 'notification area', I just wasn`t sure what to look for, but it`s all fine now.

Recommend that you go to "Thread Tools" at the top of this thread and mark the problem "Solved". It could be a help to someone else.

Glad you fixed things.

My recommendation was because I had lost the volume icon but right clicking and adding to panel would not work.

---

