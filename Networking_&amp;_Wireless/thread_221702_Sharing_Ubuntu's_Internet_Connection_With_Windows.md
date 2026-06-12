---
title: "Sharing Ubuntu's Internet Connection With Windows"
date: 2006-07-23
forum: Networking &amp; Wireless
---

### Post by Dev05 on 2006-07-23
[FONT="Verdana"]**Hi everybody!**

I'm trying to get Ubuntu to share my Internet Connection with a Windows XP latptop trough Wireless. My card is correctly detected and I set it up the way I did in Windows (I have several OSes, among them WXP and Ubuntu. In XP the network works fine). This is the Network in some ASCII art:

[FONT="Courier New"]|----------------------------------------------------|
|   ********  ethernet
|   *Ubuntu* ----------> *ADSL Modem* --> *Internet*
|   ********
|      |
|   wireless (this is peer-to-peer)
|      |
| ************
| *Windows XP*
| ************
|----------------------------------------------------|[/FONT]

Now, I've set it up using System->Administration-Networking. It is detected as ra0. I wrote the ESSID and the WEP Key in ASCII. I left the Connection Configuration for IP with DHCP as there are no Static IP Addresses set-up. I Activated the Interface in the same tool and I still cannot connect to it from the laptop. One thing that I had to do in XP is to change the connection type from Infrastructure to Ad-Hoc and I have no idea on how to do that in Ubuntu. I tried looking in System->Administration->Device Manager but I didn't find anything relevant.

Can anyone guide a poor Windows guy? :-D 
Thanks!

And I forgot: The PCs are set in a Workgroup called HOME.
[/FONT]

---

### Post by Dev05 on 2006-07-25
Has any hacker already tried this??? Please... :(

---

### Post by shoggoth on 2006-07-25
i was under the impression from my own internet searches into the issue that doing this was almost impossible with two xp computers so i wouldnt think linux would be able to do it.

---

### Post by shoggoth on 2006-07-25
if anyone does know anything about internet connection sharing under winxp or how to do something of the same with winxp and ubuntu post some info :)

---

### Post by Dev05 on 2006-07-25
> **shoggoth said:**
> i was under the impression from my own internet searches into the issue that doing this was almost impossible with two xp computers so i wouldnt think linux would be able to do it.

[COLOR=black]Between two XP boxes? That's extremely easy! I'm sure this can be done with Linux, it's just that I don't know how. That's why you're hearing from me in this thread :-D.[/COLOR]

---

### Post by stormblue on 2006-08-04
First of all your card has to support ad-hoc mode.  Second run a command like this:

```
sudo iwconfig eth2 mode ad-hoc
```

If you want to get it back into managed mode try this:
```

sudo iwconfig eth2 mode managed
```

I would assume that if you had to put windows into ad-hoc mode, you would also have to put linux.  Managed mode is used to connect to routers.  Master mode is used to appear to be a router.

---

