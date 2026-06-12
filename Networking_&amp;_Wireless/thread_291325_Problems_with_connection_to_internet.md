---
title: "Problems with connection to internet"
date: 2006-11-02
forum: Networking &amp; Wireless
---

### Post by scallywag on 2006-11-02
Ok folks, I'm so new to Linux that I have no idea what to do. My son sent me this laptop with ubuntu istalled on it. I haad to reinstall it after the first time I used it because something went terribly wrong. Now Here is the problem. I could not connect to internet at all using anything. Not Firefox or the Mail program or anything. My son found something I had to change to enable Firefox to work but I still can't connect with Evolution Mail or using  Easyubuntu to get the codex I need. Nothing seems to work but Firefox. This is a wire connection not wireless and I run through a router and my Dsl Modem. Any help would be a Godsend as I am so ignorant of this system.

---

### Post by Paul41 on 2006-11-03
This may help.
[http://doc.gwos.org/index.php/DisableIPV6](http://doc.gwos.org/index.php/DisableIPV6)

What did you change if Firefox to get it to work?

---

### Post by stream303 on 2006-11-13
What a nice son!  I'll bet he found the way to disable IPV6 for Firefox.  Your hardware combination may not implement it well, so I'd try disabling IPV6 globally:

Create a file named **bad_list** in **/etc/modprobe.d** containing just this one line:
[B]
alias net-pf-10 off[/B]

Either reboot or restart networking and lets see how that goes...

---

### Post by mips on 2006-11-13
The above should do the trick.

---

