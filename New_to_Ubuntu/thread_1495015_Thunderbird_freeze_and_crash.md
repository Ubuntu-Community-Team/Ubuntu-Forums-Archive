---
title: "Thunderbird freeze and crash"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by candtalan on 2010-05-27
I have just started using a brand new machine (with Ubuntu 10.04) and have noticed that Mozilla Thunderbird has had a couple of freezes where I had to force quit and one crash when it just closed abruptly on me. I am not aware of data being lost. On the force quits, an email being written was automatically retained as a draft.

Any suggestions please about what procedures I could use to help capture useful information about the trouble here? What logs or other information can I use to help report this sort of thing?
tia

---

### Post by -humanaut- on 2010-05-27
When it crashes type ' dmesg ' from a terminal to get an instant idea of what happened. You could also try /usr/lib/thunderbird/error.log or from a terminal type:

locate log | grep thunderbird or locate log | grep error

---

