---
title: "Issues with wireless/networking tool"
date: 2008-10-27
forum: Networking &amp; Wireless
---

### Post by juiceman on 2008-10-27
Hey guys, 
I have this perpetual issue with the wireless configuration tool in ubuntu. This has been something that has persisted through 8.04 and is also present in 8.10.  I had hoped that a new version of ubuntu would have this resolved, but apparently not so.

I have a thinkpad r40 with built in wireless.  The drivers are detected and it works fine when I go through these routines... the problem is that ubuntu has a bug in it or something that makes me go through this 'routine' every time instead of just working correctly.

To make wireless connect correctly to my WEP Hex passworded wifi router I must do the following (i can do anything else i want before this, but it won't work until these steps have been done):
1) Attempt WEP 128 bit Passphrase connection (not hex) to the router, password hidden, but with my password of 1111111111  (hidden)
2) It kicks me back asking for a password again, but this time for some reason it looks really long (masked/hidden).  I change the connection to a 40/128 HEX connection, tic the SHOW PASSWORD box, and now for some reason the password I was using is converted to a long string of letters and numbers.   I delete this and replace it with the correct pass of 1111111111. 

Then I hit connect and it connects correctly.

What is the problem here?  It obviously is not my router, and it can't be a hardware issue because it does work fine once this silly routine is completed.  What can I do?  I try to create the connection in the 'wireless' section, but it won't work that way either.. it kicks me back, and if I try to do the correct settings (step 2 above) without doing step 1, it won't work.  Thats why this routine is so annoying; it forces me to do wrong things just to trigger the correct 'bug' or whatever to make the correct things then work correctly.

HELP!

EDIT:  Update.  I have found that I cannot simply get the system to connect properly by doing the above steps.  Those above steps end up being the last two steps that happen, but I am finding myself futzing around between manual, hidden, and simply clicking on the detected one for my router and various WEP modes and such.... the last 2 steps are always exactly what you see above, though.  wtf is this crap.

---

### Post by juiceman on 2008-10-28
da sexy booty go bump bump bump

---

### Post by juiceman on 2008-10-29
if this is any help, this is the LSPCI output for my card.

02:02.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)


Also.. a little more detail.

In all cases for WEP, beit 40/128 hex or 128 passkey, when it is trying to connect I will get BOTH green dots.  It is only at the last moment that it will kick back and ask me for the key again....  and then it is just a matter of the sequence I described earlier to make it finish and connect correctly.

---

### Post by juiceman on 2008-11-01
another bump

---

### Post by juiceman on 2008-11-05
another bump...


wireless networking still acts inconsistently....  wtf


someone please start to care...  please.

---

