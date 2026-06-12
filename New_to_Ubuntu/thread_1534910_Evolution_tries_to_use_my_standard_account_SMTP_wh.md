---
title: "Evolution tries to use my standard account SMTP when sending Hotmail"
date: 2010-07-20
forum: New to Ubuntu
---

### Post by auh2o on 2010-07-20
I've set up my Hotmail address alongside my real address (set as standard) in Evolution. Everything works except sending mail from the Hotmail address. When I do, Evolution tries to use the outgoing SMTP server for my *Standard* account, not my Hotmail account. Why is that, and how do I change it?

---

### Post by gandaran on 2010-07-20
evolution always uses the predefined setup email account to send mail
you can change that to Hotmail or just select to use Hotmail when composing email.

---

### Post by auh2o on 2010-07-21
What do you mean by "select to use Hotmail"? Just choosing the Hotmail address to send from when composing a new mail is obviously not enough. And if I have to change my standard account every time I want to send a mail, then what's the reason for even allowing multiple accounts? Either I'm missing something, or this is incredibly stupid.

---

### Post by gandaran on 2010-07-22
> Just choosing the Hotmail address to send from when composing a new mail is obviously not enough
correct, exactly what I meant, this works or at least for me works, check the Hotmail smtp setup, could be you haven't set it up correctly.

---

### Post by aflog on 2010-09-28
I have the same issue.

- I have three accounts:
- 1x gmail (default)
- 2x hotmail.

When I try to send a message from the hotmail account (yes, I've selected the right 'from' address, and yes the smtp is set up fine afaik), I press send/receive and it goes through the receiving and gets to the sending where it says 'smtp: smtp.gmail.com' which is the server for the **default** account, not the hotmail ones. The hotmail ones should be: smtp.live.com. help anyone?

---

