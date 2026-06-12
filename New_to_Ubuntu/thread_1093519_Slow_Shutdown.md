---
title: "Slow Shutdown"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by s.fox on 2009-03-11
Hi,

I had a bit of a problem earlier shutting down earlier.  It took over 10 minutes before I finally just pulled the plug because I had to leave my house and was running late.   Before I pulled the plug I had been logged out and the monitor had gone into standby.  The fans and the lights were however still on.

Is something wrong with my computer?  Is their anyway to check?   Does anyone have any thoughts?  Sorry for all the questions, but I would really like to know what I can do about it.

Many thanks.
-Ash R

---

### Post by kanikilu on 2009-03-11
How did you shutdown (GUI, CLI)? Check your logs. I honestly don't know off hand where the shutdown gets logged, but /var/log/messages, /var/log/syslog, /var/log/dmesg are the usual suspects. Also maybe next time see what happens if you try shutting down from the command line: ```
sudo shutdown -h now
``` Also, does a reboot work? Either from the GUI or with ```
sudo shutdown -r now
```

---

### Post by s.fox on 2009-03-11
I shut down via the GUI.  I shall check the logs.

Thanks for the suggestion.

EDIT:  Strange,  I don't appear to have the folders that you mentioned in your post.

---

### Post by s.fox on 2009-03-11
Okay I have just rebooted and shutdown ,y computer from terminal.   My computer shutdown within 30 seconds, but a message did briefly appear in the terminal.  I did not have chance to read it,  as it was so quick.    I am guessing this went into some kind of log.

Anyone know where these logs are kept?   The folders mentioned above don't seem to exist.

Many thanks,

Ash R

---

### Post by kanikilu on 2009-03-11
> **Ash R said:**
> The folders mentioned above don't seem to exist. They are not directories, they are files.
```
cd /var/log
nano messages
nano syslog
...
```

If not nano, use your editor of choice, gedit, vi, whatever.

---

### Post by s.fox on 2009-03-11
Ahh, I thought they were files.  Thank you for the clarification.

The syslog has loads of messages that all pretty much like this

```
kernel: [ 3289.181799] yealink: unexpected response fd
```

The messages log is empty.  Is the message above anything to worry about?

Once again thank you for all the help.

---

### Post by kanikilu on 2009-03-11
I've never heard of it before, but 'yealink' seems to be a type of USB phone, right? I'm not sure if that's what could be causing a problem (or if that error's even something to worry about), but maybe try disconnecting it before your next shutdown attempt and see what happens :?:

---

### Post by s.fox on 2009-03-11
Oh,  its my VOIP USB phone.  After a bit of googling it looks like Yealink would be the chip set it uses.  I shall try unplugging it just before I shutdown later.

Once again,  many many thanks for your time with this matter.

EDIT:  Looks like its all sorted.  No more error messages.  Thank you everyone.

---

