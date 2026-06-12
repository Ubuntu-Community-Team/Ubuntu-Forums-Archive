---
title: "wireless network won't accept WPA2 key"
date: 2009-07-15
forum: New to Ubuntu
---

### Post by NewbuntuUser777 on 2009-07-15
I just installed ubuntu netbook remix on a machine that dual boots winXP.

In winXP I was able to connect to my wireless network.

In unr, it asks for my key, and I enter it, it processes for awhile and then asks for the key again.  This keeps repeating.

---

### Post by NewbuntuUser777 on 2009-07-15
bump

---

### Post by germanix on 2009-07-15
Not sure if this will solve your problem but, the WPA key is normally a 16 digit number code and the WPA2 key is a password that you selected at some time. Make sure that it is this password that you are entering and not the 16 digit key. I say this because I had this problem in the past untill I realised my mistake. If this is not the case with you then hopefully someone else will come to your aid.

---

### Post by NilsE on 2009-07-15
If I remember correctly you also have a choice with wpa2 to use either personal or enterprise so try both.  Also remember it is case sensitive if you are using the password key option.

---

### Post by NewbuntuUser777 on 2009-07-15
Thanks to everyone for their suggestions.



I think I've figured it out.

I'm using WPA2 personal.  Which is fine.  The problem was that I was using TKIP+AES as the encryption method.

When I change to AES only, it works fine.

This is a tad bit annoying since TKIP+AES is more secure, but I got it working anyway.

Thanks!

---

### Post by niteshifter on 2009-07-15
> **NewbuntuUser777 said:**
> Thanks to everyone for their suggestions.

...

This is a tad bit annoying since TKIP+AES is more secure, but I got it working anyway.

An FYI: TKIP+AES is somewhat misleading - that is not cipher chaining as in one algorithm feeds the other, it is an OR: the link will use either TKIP (actual cipher: RC4) or AES for the encryption depending upon the capabilities of the endpoints. Of the two AES is the more robust.

---

