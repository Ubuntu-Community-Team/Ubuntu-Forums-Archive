---
title: "Troubles with large attach in Evolution"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by xumuk37 on 2010-04-04
Few days ago I tried to send a mail with a large attach and it still trying to send it. How do I cancel sending? When I go to sended folder it hangs up... Is there some way to cancel all sending messages in evolution?

---

### Post by da burger on 2010-04-04
Not sure but you can force evolution to close.

First try pressing Alt+F2 and type in ```
xkill
``` your cursor should change to a cross and clicking evolution will hopefully close it.

If that doesn't work open a terminal (Applications > Accessories > Terminal) and type in ```
ps aux | grep evolution
```. It should return something like ```
Your name  **_NUM_** lots of other numbers evolution
```.

Take the number I've highlighted and type into a terminal ```
kill NUM
``` where NUM is the number we got from the last command.

---

### Post by Nisal on 2010-04-04
little tip dont attach big files just upload them to free uploading site and send the link

---

### Post by xumuk37 on 2010-04-04
da burger, thanks, but I don't want to kill evolution) I only want to cancel all sending queue...

Nisal, it's what I did after) but now I need to cancel what it's trying to send...

Thanks anyway.

Some other suggestions?

---

### Post by phillw on 2010-04-04
> **xumuk37 said:**
> da burger, thanks, but I don't want to kill evolution) I only want to cancel all sending queue...

Nisal, it's what I did after) but now I need to cancel what it's trying to send...

Thanks anyway.

Some other suggestions?

Hi, I am still a trainee but I have asked for advice. The suggestions are that you please provide the following information.

can you post ```
 ls .evolution/cache/tmp
```

also > there is an option in evolution to backup = do that first, then just rename .evolution to evolution in nautilus then restart it then apply the backup

The moving of the evolution directory with nautilus is pretty straight forward, but if you need help, please ask :-)

Regards,

Phill

---

### Post by da burger on 2010-04-04
I would have thought (but could be wrong) that killing evolution would clear it, or at least pause it so you could clear it.

---

### Post by xumuk37 on 2010-04-04
Hi, sorry for late I wasn't in) Here it goes...

calendar.log.4E07kc  calendar.log.Yj5Wh3  mail.log.7qoJfb  mail.log.RcmJCV
calendar.log.aHXKEG  calendar.log.Z5eXqX  mail.log.PaidII  mail.log.Xkpts9

---

### Post by phillw on 2010-04-04
Hi,

would you rename the .evolution directory to .evolution_backup, then reboot.

That should clear the file that wishes to try and transfer whilst retaining all your user information.

from Nautilus you need to enable 'view hidden files', else it can be done from a terminal prompt 

please do try what has been suggested to assist you. If you are unsure about moving the .evolution directory over, please do ask.

Regards,

Phill.

---

### Post by xumuk37 on 2010-04-04
Thanks, it was helpfull)

---

