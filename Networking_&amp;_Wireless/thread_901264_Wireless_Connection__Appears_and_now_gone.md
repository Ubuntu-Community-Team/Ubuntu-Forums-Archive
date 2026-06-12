---
title: "Wireless Connection / Appears and now gone"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by bbrownatl on 2008-08-26
Ok, I installed Ubuntu and was able to connect to our home wireless network. Now, I can’t.  Actually, if I click on the connection icon at the top right it does not even list the option of a wireless connection.  However, if I right click, it shows “Edit Wireless Properties” of which I can see my home wireless connection and the respective key entered.  What am I doing wrong to not be able to connect to my wireless connection?

I appreciate your time and insight.

Thanks,
Brian (Newbie Ubuntu convert and loving it!!)

---

### Post by Sam Lars on 2008-08-26
Could you post the output of the following?
```
lspci | grep Network

ifconfig

iwconfig

iwlist scanning
```

---

### Post by bbrownatl on 2008-08-26
Sam,

I need a little more guidance.  Where and how do I post the output of the following (as per above)?  Is it through Applications > Accessories > Terminal?  Again, I'm a newbie in the world of Ubuntu and really liking it.

Thanks for your assistance.

Brian

---

### Post by Sam Lars on 2008-08-26
Yes, open up a terminal from that menu and put the commands in one by one.  Copy the output of each one and post it here.

---

