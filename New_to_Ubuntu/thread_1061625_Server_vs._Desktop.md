---
title: "Server vs. Desktop"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by Stefan_th on 2009-02-06
Hi,

I want to setup a small server at home, running on an old PC. It should run a small SIP PBX plus a video surveillance system (zoneminder).

Occasionally I want to have an x-windows session for tests, checking the system, etc.

I wonder if I should install the server version or the desktop version. Using the server version I would have to add an x-client to allow remote x-windows sessions from my Ubuntu notebook, right?

Would it make any sense to install the server version (to keep the system as lean as possible)? Would I get any performance advantage?
Or is the difference so small that I can install the desktop ISO which has the x-windows stuff already there?

Thanks for your opinion!
Stefan

---

### Post by sdennie on 2009-02-06
You probably won't notice the difference between the server and desktop versions in your case.  Having said that, a good solution might be to install the server edition and then add applications as you need them rather than going for a full blown desktop version.

---

### Post by HermanAB on 2009-02-06
SSH has X built in.  That is why SSH is normally used to control headless servers.

Try this:
$ ssh username@serveripaddress gnome-panel

Cheers,

Herman

---

### Post by cariboo on 2009-02-06
HermanAB

You have a typo, the command should be

```
ssh -X username@serveripaddress gnome-panel

```

Jim

---

