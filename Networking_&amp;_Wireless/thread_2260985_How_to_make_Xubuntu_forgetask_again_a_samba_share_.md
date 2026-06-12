---
title: "How to make Xubuntu forget/ask again a samba share user/pass?"
date: 2015-01-15
forum: Networking &amp; Wireless
---

### Post by riksoft on 2015-01-15
Client: Xubuntu 14.04
Server: Mint 13

I have some share dirs on Mint 13 and are all user/pass protected, but  Xubuntu ask for user/pass ONLY ON SOME of them, despite are all configured the same in /etc/samba/smb.conf.
I've changed the shared name in the smb.conf on Mint (server) and Xubuntu (client) actually starts to ask user/pass correctly.

So the problem is that Xubuntu has saved somewhere the wrong user/pass.
Question: **How do I make Xubuntu (client) forget every samba password? Where do I find the keyring file to delete?**

---

### Post by riksoft on 2015-01-15
Got it!
Samba actually doesn't have any keyring/cache to cause that problem. It's only a bad interpretation of the problem on my part **because of a bug in Thunar**.
When I copy a file from Xubuntu to the shared dir on Mint, the size of the file isn't updated. That made me think Xubuntu get connected as a guest, hence the question above about deleting credential.

But the real problem is not the network/credential/access as guest, the problem is simply _Thunar that doesn't update the size_ even refreshing the window 100 times. ](*,)

---

### Post by riksoft on 2015-01-15
And the problem of the refresh it's only on Xubuntu (Thunar), not on samba, because doing the same test with Lubuntu the overwritten file is immediately shown with the correct new size.

So the problem has now turned into:
**Anyone know how to make Thunar refresh the size of the files?**
It would be OK even if I had to press F5 / CTRL+R every time.

---

### Post by riksoft on 2015-01-15
I've tried some other distros with XFCE and they all have this problem (e.g. Mint 17 XFCE). The refresh doesn't work there either and the only solution I've found is to change dir and return back.
On the contrary Lubuntu works correctly despite it's lightness.

---

