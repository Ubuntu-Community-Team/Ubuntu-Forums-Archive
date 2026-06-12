---
title: "Root access"
date: 2011-07-17
forum: New to Ubuntu
---

### Post by sks24 on 2011-07-17
I need to know how to gain root access so I can create a file in /etc/ppp/peers/ so I can maybe get a wireless card going.  

I went to "users and groups" and changed the account type to "Administrator" but, apparently, that's not sufficient to do what I need to do. According to these instructions from ATT: "Root access is required to create connection scripts and run the PPPD dialer."

I'm able to get in the "peers" folder.  I just can't create the file according to the instructions. ("Create a file in "/etc/ppp/peers/" named "gprs-connect-chat" and paste the following information into it.")  
Thanks in advance, Scott

---

### Post by wolfen69 on 2011-07-17
```
gksu nautilus
```

---

### Post by Cybie257 on 2011-07-17
The method I use, within a terminal window, is:

sudo -i

This will put you into root/su mode without having to constantly type sudo before every command you run.


-Cybie

---

### Post by sks24 on 2011-07-17
Thanks Mister Hippie + Cybie!

Quick question: will the root access terminate upon reverting the user type to "Custom"? (which is where it was before I changed it to "Administrator.")

Thanks again,
Scott

---

### Post by alphacrucis2 on 2011-07-17
> **sks24 said:**
> Thanks Mister Hippie + Cybie!

Quick question: will the root access terminate upon reverting the user type to "Custom"? (which is where it was before I changed it to "Administrator.")

Thanks again,
Scott

in the case of sudo -i it will revert when you either type exit, or close the terminal shell. In the case of gksudo nautilus, it applies  to that instance of nautilus until you close it.

---

### Post by bodhi.zazen on 2011-07-17
See also : [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by sks24 on 2011-07-19
Thank you very much bodhi.zazen,

I really, really like that quote.  I'll be using it, ubetcha.

---

