---
title: "need help with sendmail"
date: 2011-06-08
forum: New to Ubuntu
---

### Post by chazz_tsc on 2011-06-08
I want to be certain I'm posting in the right place, and I don't know where in the forums queries about sendmail should go, if anywhere. This is a pretty much stock Ubuntu 10.04.2LTS distribution running on relatively elderly hardware, and I'm having trouble with someone using it as a spam remailer; I need help closing the barn door, basically.

---

### Post by FormatSeize on 2011-06-08
Hi,
 
```
sudo /etc/init.d/sendmail stop
```
should do it.

---

### Post by JKyleOKC on 2011-06-08
Stopping the server will definitely close the barn door, but it will also disable your own email use.

I use postfix rather than sendmail, so the details may differ, but in my /etc/postfix/main.cf configuration file there's an entry "relayhost=" that defines all relay hosting. I have it set to an empty string to disable relaying. There's also a "mynetworks=" entry that defines the networks from which the server will accept traffic.

If you have something similar in the configuration file for sendmail, it should allow you to shut off the relay capability while retaining your own functionality.

---

### Post by chazz_tsc on 2011-06-08
umm... yeah.

@FormatSeize, in many forums I frequent, your comment would be seen as harmful code.

@JKyleOKC, sendmail has that facility, and it is in place as far as I know and supposedly working - at least it reports itself as working.

I have posted fuller details on the Server Platforms forum. The question here was "where do I post", and that seems to be the appropriate answer, so I will mark this thread answered and move there.

---

