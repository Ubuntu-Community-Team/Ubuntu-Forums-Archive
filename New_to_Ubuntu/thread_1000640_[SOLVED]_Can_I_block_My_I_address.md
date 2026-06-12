---
title: "[SOLVED] Can I block My I address?"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by nakama85 on 2008-12-03
In windows you could with software. Is there a way with ubuntu?

---

### Post by linux_tech on 2008-12-03
Yes you can block ip address using ip tables firewall. 
Its easy enough to do some example instructions are here:
[http://www.cyberciti.biz/faq/how-do-i-block-an-ip-on-my-linux-server/](http://www.cyberciti.biz/faq/how-do-i-block-an-ip-on-my-linux-server/)

---

### Post by albandy on 2008-12-03
What is an I address? If you mean IP address you can use de ubuntu firewall ufw, exist a GTK frontend to manage it.

---

### Post by nakama85 on 2008-12-03
> **albandy said:**
> What is an I address?

Sorry I missed a letter

---

### Post by nakama85 on 2008-12-03
Thanks Guys. What I am really after is just blocking it from 1 site(thepiratebay.org) is this possible?

---

### Post by albandy on 2008-12-03
Yes, you can with iptables by command line, or using gufw the ufw frontend.

Type 
sudo apt-get install gufw
then 
sudo gufw

---

### Post by Kellemora on 2008-12-03
Don't know if blocking your IP address would do any good if you are not T1 or T3 connected to the internet.
Your ISP assigns you an IP, it's like your address, else they wouldn't know where to send your data to.  When you connect to a web site, your ISP is sending an IP also, either yours or a link to yours through themselves.

So I might ask a question.  If you don't give them your address, how can they send data back in your direction?

TTUL
Gary

---

### Post by anjilslaire on 2008-12-03
Try using an anonymous proxy service.

Although, once you get your torrent file from the 'Bay, its a whole 'nother ball of wax to mask your IP while the torent is active...

---

### Post by nakama85 on 2008-12-03
> **anjilslaire said:**
> Try using an anonymous proxy service.

Although, once you get your torrent file from the 'Bay, its a whole 'nother ball of wax to mask your IP while the torent is active...

So all in all I should not upload the Dark Knight full dvd iso that I have. As much as I want to share with those that share with me it sounds just a bit to risky

thanks for the replies!

---

### Post by bapoumba on 2008-12-04
You should not share copyrighted material. Simple. Closing the thread.

---

