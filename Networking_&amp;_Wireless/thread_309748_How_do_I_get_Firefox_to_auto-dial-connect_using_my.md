---
title: "How do I get Firefox to auto-dial-connect using my 56k internal modem?"
date: 2006-11-30
forum: Networking &amp; Wireless
---

### Post by lukon on 2006-11-30
Yep.

How do I get Firefox to auto-dial-connect using my 56k internal modem?

---

### Post by daniminas on 2006-11-30
You can use wvdial:

> sudo wvdialconf

Then edit the file to put the right phone number/user/etc:

> sudo gedit /etc/wvdial.conf
//You will see something like this:
[Dialer Defaults]
Modem = /dev/ttyS2
Baud = 57600
Init = ATZ 
Init2 = AT
S11=50
Phone = 555-4242-the-phonenumber
Username = my-user
Password = my-password


And to connect to the internet:

> sudo wvdial

And.. open your web browser and.. that's it..

=)

---

### Post by lukon on 2006-11-30
daniminas,

I happen to be typing this to you through a successful modem connection and FireFox session. However, I had to have a dialer make the connection first, then start FireFox. But at least this means I've managed to get that much figured out.

However, as I read your answer to my question, I'm a bit confused. You include a step where I should type "> sudo wvdial" into the Terminal. If this step is done to establish the modem connection to my ISP, then your reply is not really an answer to my question. I asked how to get FireFox to AUTOMATICALLY dial the ISP when I start a FireFox session.

If, on the other hand, I misunderstand your instructions, perhaps typing "> sudo wvdial" is supposed to be a one time thing that will make FireFox do the automatic dialing from that point on.

So, may I ask which it is?

---

### Post by daniminas on 2006-11-30
AUTOMATICALLY ](*,) .. may be some unknown plugin :-k  ..

---

