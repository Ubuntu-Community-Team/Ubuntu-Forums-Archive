---
title: "Pidgin and IMing"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by shasocastris on 2009-02-01
After installing all of the packages to get GAIM/pidgin onto my laptop, it won't let me sign in.

After I activate Pidgin (and I've entered the password and user name), it says 

Could not connect to authentication server: Connection refused

I've only entered my screen name and password into the Modify Account window. Should I do something else? Thanks.

Cheers!

---

### Post by hAvAAck on 2009-02-01
ensure your password is correct. Or try to sign on to a different account. What type of account is it?

---

### Post by Sunspore on 2009-02-01
Hi, if ur taking about msn, make sure that ur server is this" messenger.hotmail.com

---

### Post by ugm6hr on 2009-02-01
> **shasocastris said:**
> After installing all of the packages to get GAIM/pidgin onto my laptop, it won't let me sign in.

Installing what packages?  Ubuntu has pidgin installed as default.

Won't let you sign into what IM network?

I have (and still do) use it successfully for Yahoo, Google and MSN.

Presumably you have an account with the IM network you are trying to access... (the username and password are for the IM service, not Ubuntu)

---

### Post by shasocastris on 2009-02-01
This is an AIM account. Sorry. And yes, I do have one.

I went to Synaptics Package Manager, searched for GAIM (yes, I did have to install it), and installed everything except:
festival-gaim
kmess
libbeagle-dev
pidgin-musictracker
python-beagle

Does this help?

Cheers!

---

### Post by ugm6hr on 2009-02-01
Sorry - I have never used AIM.

But - just to let you know - you didn't have to install anything.

Those gaim* packages in the (Hardy) repository are all dummy packages that just point to the (already default installed) pidgin* packages.

So you haven't really installed anything (just dummy packages).

EDIT: Apparently I do have an AIM account - presumably a leftover from when I had AOL internet many years ago - I just signed into it with Pidgin without any difficulty.

username: username (without @aol.com etc)
password: as expected
server: login.messaging.aol.com
port: 5190

Do you use a proxy for internet?
I don't think your firewall would have anything to do with this, since I have port 5190 closed with ufw.  However, if you don't have uPnP on your router, that might cause problems.

---

### Post by shasocastris on 2009-02-01
Thanks. It works now :D

Cheers!

---

