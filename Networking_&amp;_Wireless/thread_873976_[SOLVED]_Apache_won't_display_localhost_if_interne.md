---
title: "[SOLVED] Apache won't display localhost if internet not connected"
date: 2008-07-29
forum: Networking &amp; Wireless
---

### Post by phucough on 2008-07-29
Hi there,

I can't always get my laptop connected to the internet and I installed LAMP on it in order to work on a web site that I was previously working on using WAMP.

I got the whole thing working perfectly except for one thing (that was never a problem on Windows) - with the internet not connected, any attempt to access localhost or the files therein throws up an error in Firefox about not being able to access it whilst offline.

Does anybody have any idea how to bypass this? Cheers all.

---

### Post by ibutho on 2008-07-29
Can you post the contents of your /etc/hosts file. Make sure you have the following line
```
127.0.0.1	localhost
```
When trying to access the webserver, use localhost or 127.0.0.1.

---

### Post by phucough on 2008-07-29
Hi,

Cheers for your reply. I do have localhost in the /etc/hosts file... however having actually looked at the problem again now, it turns out the error (as I forgot) is actually:

```

Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Fatal error: Unknown: Failed opening required '/home/tom/public_html/index.php' (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0
```

Any ideas? I think I tried last week to get to the bottom of it but must have failed. Looks like a php problem too, should have posted it elsewhere really... oops.

---

### Post by phucough on 2008-08-02
Well I'm marking this thread as "solved" because there isn't an option to mark as "stupid". I've just asked in the phpfreaks forum... Cheerios!

---

