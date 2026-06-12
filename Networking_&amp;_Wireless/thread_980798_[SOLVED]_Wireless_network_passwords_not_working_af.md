---
title: "[SOLVED] Wireless network passwords not working after 8.10 upgrade"
date: 2008-11-13
forum: Networking &amp; Wireless
---

### Post by dtd2932 on 2008-11-13
Hey guys,

Not sure what information if any that you need from me, but my wireless adapter is just a piece of crap generic Chinese USB 802.11g.

I was using it in my 8.04 install, and it worked perfectly out of the box, on my WPA2 protected network. I just upgraded to 8.10 and now it can't connect. It can connect to networks without a password, but with the password enabled... it just tries to connect and the password screen pops up again.

It is not an incorrect password, as I am connected right now on my laptop fine.

And as I said above, it worked perfectly fine on the 8.04 install, but as soon as I upgraded to 8.10, it won't do passworded networks. So I highly doubt it's the wireless adapter.

I searched around google and these forums and didn't see anything else like my problem, but if I missed something blatantly obvious... my apologies ;-).

Thanks for any help...

Update: I just reinstalled because I couldn't figure it out and that worked... The only reason I didn't do this at first is I didn't feel like setting up my servers again (and don't have any external drives to save the config files on).

---

### Post by miatawnt2b on 2008-11-13
I have similar problems running the NetworkManager 7.0 SVN for hardy.

-J

---

### Post by natehall on 2008-11-13
Did it switch from a passphrase to a 128 bit key? That's the problem I've been having. By getting into the computer broadcasting the signal I was able to put in the 128 bit code directly. If you do that be sure you use the capital lock for the hexadecimal digets.

---

### Post by dtd2932 on 2008-11-13
Yes it does switch the password to the encrypted one, so that's not the problem. unless its encrypting it wrong but i dunno why it would do that...

---

