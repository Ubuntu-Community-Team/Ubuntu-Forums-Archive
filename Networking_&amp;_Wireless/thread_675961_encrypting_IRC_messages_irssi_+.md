---
title: "encrypting IRC messages: irssi + ?"
date: 2008-01-23
forum: Networking &amp; Wireless
---

### Post by tuxandpuffy on 2008-01-23
Hello everybody!

Does anyone knows a way to encrypt client to client a multi-user IRC conversation ? If possible, just with a key that anyone who wants to be able to decode the enrypted messages must have, not GPG and all that.

My client is irssi with tor (with a mapaddress in the /etc/tor/torrc). But I discuss on IRC with people who sometimes have others IRC client so if it would be a quite widely used tool it'd be easier. After hours on the net, the only potential solutions I found are FiSH and encrirc which both don't seem to be very widely used so I doubt a little on their effectiveness and reliability. So if someone knows a widely used and resonably secure way or confirm me that FiSH or encrirc are reliable it would be nice. :)

---

### Post by tuxandpuffy on 2008-01-25
update: I 've tried a script called blowjob.pl (official site of irssi) but it isn't up to date, and crypt::CBC seems to have changed in the meantime so the script works at the beginning and then it crashes. So if somebody got a solution :)...

---

### Post by Roque2 on 2008-01-25
Fish is widly used, I have used fish for about 6 years.

---

### Post by tuxandpuffy on 2008-01-26
Yeah, thanks, it works very well. Thank you for answering.  in case somebody else would have troubles installing FiSH I recommand you the steps at the end of this web page (forum of FiSH), just replace, everywhere it appears, the irssi version by the one you have.
url: [http://fish.sekure.us/forum/viewtopic.php?t=145](http://fish.sekure.us/forum/viewtopic.php?t=145)

:)

---

### Post by kevdog on 2008-01-26
Pidgin could do this with the otr plugin or encryption plugin.  sorry if this is a little bit of topic.

---

### Post by DeHorde on 2008-03-16
> **tuxandpuffy said:**
> update: I 've tried a script called blowjob.pl (official site of irssi) but it isn't up to date, and crypt::CBC seems to have changed in the meantime so the script works at the beginning and then it crashes. So if somebody got a solution :)...

Look here for an updated blowjo.pl: [http://blog.phrog.org/wp-content/uploads/2008/02/blowjob.pl]("http://blog.phrog.org/wp-content/uploads/2008/02/blowjob.pl")

---

