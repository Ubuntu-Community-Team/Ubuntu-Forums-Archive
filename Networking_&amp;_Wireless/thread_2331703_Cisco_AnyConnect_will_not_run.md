---
title: "Cisco AnyConnect will not run"
date: 2016-07-25
forum: Networking &amp; Wireless
---

### Post by Kerry Lange on 2016-07-25
I'm trying to get Cisco AnyConnect to run in 16.04 without success.  I keep running into the same error message and AnyConnect will not run.  Here's the error message I get:

```
Warning: vpnagentd.service changed on disk. Run 'systemctl daemon-reload' to reload units.
```

If I run systemctl daemon, the command processes and nothing changes.  AnyConnect will not run.  The icon appears as though the program is installed but when I click it, the icon appears in the menu bar momentarily, goes away, and nothing more happens.  I've run a system monitor to watch what happens but I don't see a Cisco or AnyConnect process run.  

Any ideas of what to change?

BTW, AnyConnect is required by my workplace.  I can't use OpenConnect or any other vpn software.

---

### Post by houstonbofh on 2016-07-25
I think AnyConnect will still require the OpenConnect libraries to integrate with networking.  [https://technicalsanctuary.wordpress.com/2016/05/28/installing-cisco-anyconnect-vpn-on-ubuntu-16-04/](https://technicalsanctuary.wordpress.com/2016/05/28/installing-cisco-anyconnect-vpn-on-ubuntu-16-04/)

---

### Post by Kerry Lange on 2016-07-25
> **houstonbofh said:**
> I think AnyConnect will still require the OpenConnect libraries to integrate with networking.  [https://technicalsanctuary.wordpress.com/2016/05/28/installing-cisco-anyconnect-vpn-on-ubuntu-16-04/](https://technicalsanctuary.wordpress.com/2016/05/28/installing-cisco-anyconnect-vpn-on-ubuntu-16-04/)

Thanks for the suggestion!  I've tried that (added the OpenConnect manager, etc.) but still no joy.

---

### Post by houstonbofh on 2016-07-26
Well, I am stumped.  You might try opening a TAC request with Cisco if your company has smartnet.

---

### Post by Kerry Lange on 2016-07-27
Actually, I was wrong.  OpenConnect works fine, at least from the command prompt.  I used the following (found in another post) and it worked for me:

```
sudo openconnect vpn.name.com
```

I then used the default RDP client and was able to work from my desktop as though at my work desk.

---

