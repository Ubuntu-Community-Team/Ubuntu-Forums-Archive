---
title: "Package dependencies cannot be resolved."
date: 2011-05-01
forum: New to Ubuntu
---

### Post by DayLite on 2011-05-01
Instruct me how to resolve this:confused: I went to the Synaptic Package Manager and nothing showed up under 'broken packages'.

[IMG]http://inlinethumb32.webshots.com/47391/2908462050056553245S425x425Q85.jpg[/IMG]

---

### Post by oldos2er on 2011-05-01
In Synaptic, click the 'Reload' button. If that doesn't work, check Settings, Repositories, Ubuntu software tab, and make sure all the boxes under 'Downloadable from the Internet' are checked, then Reload again.

---

### Post by DayLite on 2011-05-01
> **oldos2er said:**
> In Synaptic, click the 'Reload' button. If that doesn't work, check Settings, Repositories, Ubuntu software tab, and make sure all the boxes under 'Downloadable from the Internet' are checked, then Reload again.

I am :confused: This is what it showed. I don't know how to fix it?

[IMG]http://inlinethumb14.webshots.com/48141/2895249840056553245S500x500Q85.jpg[/IMG]

---

### Post by oldos2er on 2011-05-01
To get the gpg key, in a terminal, run ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID
``` where KEYID is the alphanumeric shown in the error msg.

For the 404 errors, I would disable those PPAs.

---

