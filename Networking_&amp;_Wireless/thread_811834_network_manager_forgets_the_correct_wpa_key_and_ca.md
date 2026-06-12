---
title: "network manager forgets the correct wpa key and cannot connect on restart"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by CrinkElite on 2008-05-29
Hi folks, I've been having a problem with network manager in ubuntu gutsy.
I'm using the correct driver for my card (bcm 4306)
when I log on I have no wireless connection. If I open the properties tab in network manager I see that the eight letter wpa code which should be entered has converted to a very long code of approximately 50-60 letters, I cannot view this code as it is blacked out with those round dot thingies. so I enter the correct eight letter code and I can access the internet. 
however if I open up the network manager properties tab again I see that the code has immediately changed back to the a long code again, If I then press ok to close NM. I lose the connection. If I dont open NM I can continue using the net until I reboot or log off at which point the code will return to the 50-60 character incorrect password.
I think this may have started happening after I updated the system a few months ago. Its not a major problem but it is becoming quite annoying.
do you thing I should try reinstalling NM?      
thanks for reading and thanks in advance.

---

### Post by leandromartinez98 on 2008-06-23
I have the same problem in Hardy, in a vaio laptop with intel 3945 a/b/g.

I connect to the wireless network (either WEP or WPA). If I get disconnected,
or the next time I try to connect, the conection fails. If I go to the
"Edit wireless networks..." there is a different passphrase (actually a sequence
of letters and number) that does not seem to be related to the original one.

If I go Applications->Passwords and encryption keys, chose the password (which
is there), and see it, it is not the password I put and neither the one
that is visible in the "Edit wireless..."

It does not seem that the password is being forgotten, but actually that 
some encription is not being well communicated through the system, in such
a way that the password is changed.

The same network works nice with WICD, but I would like to stay with the
standard distribution if possible.

I think this is a bug. I will try to post it as one.

---

### Post by dancresswell on 2008-06-23
I had the problem in 7.10 and still have the problem in 8.04.  Its a pain in the butt.  I avoid restarts just for this issue.  I've yet to see a fix even though it appears to be a widespread problem and has been for a long time.

---

### Post by leandromartinez98 on 2008-06-23
Yes, there are many posts on that. I'm worried for the fact that
this is being considered a bug on NM with only medium importance. The
failure of nm-applet is a major problem for Ubuntu. My brother
simply had to give up linux because of that.

Anyway, in my case Wicd did the work (not in my brother's though), athough
not perfectly (it does not connect automatically on startup, but does
not ask for passwords and the connection is perfectly stable).

---

### Post by AndyBeals on 2010-03-17
Years later, and it is *still* a problem, last seen right now on a virgin Karmic install.

---

