---
title: "Help me! A Wireless Catastrophe."
date: 2007-11-04
forum: Networking &amp; Wireless
---

### Post by Securitron on 2007-11-04
Hello.  I am a student currently in college with a serious wireless problem, and I'm hoping you all could help me.

I currently own a Dell Inspiron E1505.  My wireless is Intel PROSet Wireless.  Whenever I lose my wireless connection, it will not let me enable it again.  Pressing FN+F2 (IE: Turn Wifi On) Does not work.  It tells me to "Click  Enable Radio" But will not actually let me click "Enable Radio".

Everyone else in the dorm seems to have little problems anymore with their wireless, yet mine dies 10-20 minutes after I reboot.  

Sometimes when I reboot it will work again, sometimes it won't.

I am really desperate for help.  Anything you can offer would be deeply appreciated.

~Securitron

---

### Post by Ferrat on 2007-11-05
use 

```
lspci -nn | grep Network
```

to findout what driver you are using, sounds like the RT driver problem, in that case there is a great fix :)

---

### Post by Securitron on 2007-11-05
I'm sorry, I'm really dumb.. What does that mean?

~Securitron

---

