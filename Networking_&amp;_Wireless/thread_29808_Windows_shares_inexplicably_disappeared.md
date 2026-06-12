---
title: "Windows shares inexplicably disappeared"
date: 2005-04-25
forum: Networking &amp; Wireless
---

### Post by Rehevkor on 2005-04-25
Up until just now, I was able to browse my windows shares via Places -> Network Servers without a problem, but they're not visible anymore. I can see the Windows Network icon in there, but there's nothing in that folder.

I haven't made any changes to this system or anything else on the network that I can attribute this to. How can I re-configure this thing to see my network shares?

Thanks.

---

### Post by kmyram on 2005-04-26
Have you tried with smbtree? Type that command at the prompt (Applications > System Tools > Terminal) and check the output.

---

### Post by Rehevkor on 2005-04-26
[QUOTE=kmyram]Have you tried with smbtree? Type that command at the prompt (Applications > System Tools > Terminal) and check the output.[/QUOTE]
 I ran that, but nothing happened.

---

### Post by Rehevkor on 2005-04-29
[QUOTE=Rehevkor]I ran that, but nothing happened.[/QUOTE]
 Anyone have a clue about this?

---

### Post by Rehevkor on 2005-05-01
Ok, I discovered that if I type smb://192.168.0.100 (the local IP of a Windows PC on my network) I can browse the shares normally. I can't view them through Places -> Network Servers, however.

I found an old thread in the Hoary development section where a lot of people were discussing an issue with Nautilus being unable to browse network shares. Could I be experiencing this?

---

