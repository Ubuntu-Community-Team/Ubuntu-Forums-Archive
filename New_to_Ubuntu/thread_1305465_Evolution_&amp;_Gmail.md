---
title: "Evolution &amp; Gmail"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by Famicube64 on 2009-10-29
I can't seem to set up Evolution correctly for Gmail usage. I can send mail with SMTP through Evolution, but when I use Send/Receive to get my mail it comes up with an error in the status bar.

```
Error while Fetching Mail.

Failed to read a valid greeting from POP server pop.gmail.com
```

I'm running a clean Ubuntu 9.10 install from this morning.

---

### Post by werecatomega on 2009-10-29
it might be easier to use thunderbird. go to Applications/Accessories/Terminal and type in sudo apt-get thunderbird. it will ask for your password so enter it and it should do it.

if you want to use evolution though, i'm not completely sure about that.

---

### Post by Famicube64 on 2009-10-29
Actually, I really don't like Thunderbird's design. Evolution is much more integrated in Ubuntu so I'd really like it to work. Thanks, though.

---

### Post by servicetech on 2009-10-29
I've never had much luck with evolution, kept crashing on me. Went back to thunderbird.

---

### Post by pythonscript on 2009-10-29
What settings are you using to set up gmail in Evolution? Since gmail supports it, I would *highly *recommend using IMAP instead of POP. It's a more robust service, and it also syncs both ways, instead of only one way like pop. If you're interested, I can post further instructions on how to set that up with gmail/evolution. Otherwise, let me know what settings (port, SSL or no, etc) in using gmail's pop through evolution.

---

### Post by danastasio on 2009-10-29
try using IMAP

* Server Type: IMAP
* Server: imap.gmail.com
* Username: (your gmail account)
* Use Secure Connection: SSL encryption
* Authentication Type: Password

that should solve your problem, works for me!

---

### Post by sliketymo on 2009-10-29
> **Famicube64 said:**
> I can't seem to set up Evolution correctly for Gmail usage. I can send mail with SMTP through Evolution, but when I use Send/Receive to get my mail it comes up with an error in the status bar.

```
Error while Fetching Mail.

Failed to read a valid greeting from POP server pop.gmail.com
```I'm running a clean Ubuntu 9.10 install from this morning.
  Famicube,You may need to log into gmail account,click on the settings,choose the forwarding tab,and enable pop,and IMAP. I am using gmail with Evolution,and have for quite some time without any problems.

---

### Post by Famicube64 on 2009-10-29
Alright, I'll give IMAP a try. I've set it up before, so I should be alright.

Edit: Well, it works now. Thanks for the IMAP tip.

---

### Post by pythonscript on 2009-10-29
> **Famicube64 said:**
> Alright, I'll give IMAP a try. I've set it up before, so I should be alright.

I personally think it's a much better service than POP. Obviously, enable it in gmail, and another feature you can implement with IMAP (not POP) is the advanced IMAP controls in gmail labs. With these, you can control what labels show up in your IMAP client, which is nice if you have a million labels in your gmail account but don't want to have a million folders in your client (this is the case for me).

---

### Post by Famicube64 on 2009-10-29
I tend to keep my account simple, no labels for me. Thanks for the help.

---

### Post by sailthesea on 2009-10-29
This happened to me too and eventually I realised I hadn't configured UFirewall to allow pop/smpt I didn't even know it was active 
 I felt really stupid;)

---

