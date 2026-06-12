---
title: "can't see Ubuntu Machine from Windows Machines."
date: 2006-08-21
forum: Networking &amp; Wireless
---

### Post by wheels5894 on 2006-08-21
I installed from the text based install program and was dleighted to see that the install had correctly installed networks and that I could see and access the windows machine on the network and use the Internet. I have had no trouble opening and using files sitting on the Windows machines. however, the windows machines cannot see the Ubuntu machine so that it cannot be used a a shared network resource. 

Anyone any ideas for how make this happen please?

---

### Post by meng on 2006-08-21
What happens if you enter into the address bar (from windows):
\\(ip address of machine you're trying to access)

---

### Post by wheels5894 on 2006-08-21
Thanks for your reply. Just checked this out. When I enter the IP address I receive a message saying the address was not found despite being able to see and use the machines from the Ubuntu machine. Very odd.

---

### Post by meng on 2006-08-21
Okay, have you made any changes to samba configurations for your Ubuntu machine? Have you specified which folders on your Ubuntu machine will be shared folders? Is there a firewall in place?
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by Iowan on 2006-08-21
In the back of my mind (what's left of it), I'm thinking Samba.
But first... can you ping the Ubuntu Machine from a Windows Machine?

---

### Post by wheels5894 on 2006-08-22
Thanks for the suggestion. I was thinking SAMBA must be the problem but I had hoped it might be auto configured. Anyway, I can't ping it as it. Does that help the diagnosis?

---

### Post by wheels5894 on 2006-08-22
Update on Ping. Just rebooting the machine and nnow I can ping it but it still doesn't show up. Any ideas? Putting its IP address into Windows networking doesn't find it wither.

---

