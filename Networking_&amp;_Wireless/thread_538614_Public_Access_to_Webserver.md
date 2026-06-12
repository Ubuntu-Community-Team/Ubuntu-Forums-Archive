---
title: "Public Access to Webserver"
date: 2007-08-30
forum: Networking &amp; Wireless
---

### Post by darkness193 on 2007-08-30
I've set up a webserver using ubuntu edgy which includes php,mysql etc.... Now i'm trying to allow public access to it but I'm having some problems since the internet connection is a shared one and I can't set up port forwarding since I don't have access to the main router. Is there anyway to allow a domain name to pont to my server without having to set up port forwarding?

Thanks

---

### Post by cagey cretin on 2007-08-30
The router is the point where traffic is either allowed in or not. Without incoming port 80 being forwarded to your server, people can't get to it.

---

### Post by darkness193 on 2007-08-30
Ok it's just i thought there where applications that could do this.

---

### Post by cagey cretin on 2007-08-30
> **darkness193 said:**
> Ok it's just i thought there where applications that could do this.

Not unless there is any traffic pointed your way. Do you know the sys admin? Maybe he or she can point port 80 to you. Unless, it's pointing elsewhere...

---

### Post by darkness193 on 2007-08-30
Unfortuantly I can't get them to do that I've already tried. Thanks for your help

---

