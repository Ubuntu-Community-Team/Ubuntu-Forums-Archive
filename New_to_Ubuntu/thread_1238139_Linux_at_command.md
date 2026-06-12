---
title: "Linux at command"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by Alanta on 2009-08-12
Why can't I see the output from an at command?

If I use at command to run another simple command say ls in a say 2 minutes ahead of my current time. using atq I can see the job, but when the 2 minutes expires I see no output from the ls command that was supposed to happen. Why is this?

Thx

Alan

---

### Post by relay_man on 2009-08-12
Hi Alan

I think it may help for you to check a couple of things.

Have you looked at the man pages?

"man at"      (do not enter the quotes) at the command line will reveal all you would care to know about  "at".


Welcome to the forums.

---

### Post by 3rdalbum on 2009-08-12
You don't get any output in your terminal, because "at" is a daemon.

However, any stderr output gets mailed to you, I think? Not to your e-mail address, to your system mailbox.

---

### Post by Alanta on 2009-08-12
Thanks for your advise.

I have looked at the man pages for the at command.

I was expecting to see the ouput in the terminal just as if i had typed the command directly and pressed enter.

I am now not sure how I can check that any commands have worked by delaying them with the at command.

What I would like to do is at 01:35 apt-get dist-upgrade

This would then happen in my off peak period with my isp

Now not so sure if this will work !!

---

### Post by decoherence on 2009-08-12
> **Alanta said:**
> I am now not sure how I can check that any commands have worked by delaying them with the at command.


Like the manual says

> The user  will  be  mailed standard error and standard output from his commands, if any.

To check system mail, just type 'mail' and enter the number of the message you want to view (iirc)

---

### Post by unutbu on 2009-08-12
Do you have the exim4 (or any mail transfer agent) package installed? (To check, look for the program (file) /usr/sbin/sendmail.)
If so, the at command wil mail the output of the command to you.

If you'd rather not set up mail (even just local mail), 
then perhaps try making a script called ~/bin/apt-dist-upgrade
```

#!/bin/sh
apt-get dist-upgrade 1>~/apt-dist-upgrade.out 2>&1
```

Make it executable:
```

chmod +x ~/bin/apt-dist-upgrade
```

And then run it through "at" like this:
```

at -f apt-dist-upgrade 1:35

```
Look for the output in ~/apt-dist-upgrade.out

---

