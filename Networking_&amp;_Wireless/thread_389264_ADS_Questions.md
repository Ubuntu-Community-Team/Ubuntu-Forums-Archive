---
title: "ADS Questions"
date: 2007-03-20
forum: Networking &amp; Wireless
---

### Post by burnt_soul on 2007-03-20
Hello!

I am trying to join the ADS realm in my workplace. I am not knowledgeable about Kerberos, and my company is not exactly "Linux Friendly" so they are no help either. I need help figuring out how to configure things so that my machine is a member of the domain, I can log in with my ADS credentials, I can create SMB shares & access shares over the network, etc.

The first problem I have is that I am not allowed to join my machine to the "COMPANY.COM" realm. I must join the "ENG.COMPANY.COM" realm. However my credentials come from the "COMPANY.COM" realm. In other words, my machine must be "computer.eng.company.com" but my credentials are "user@company.com" or "COMPANY\user".

The second question is, how can I determine the necessary information about my realm from an existing Windows system? When configuring Kerberos settings, it asks for the KDCs and Admin Servers. Windows does not require this information; where does it get the info from? And can I just look on a Windows machine to determine this info?

Thanks for your help!

---

### Post by maheshjagadeesan on 2007-04-04
> **burnt_soul said:**
> 
The second question is, how can I determine the necessary information about my realm from an existing Windows system? When configuring Kerberos settings, it asks for the KDCs and Admin Servers. Windows does not require this information; where does it get the info from? And can I just look on a Windows machine to determine this info?


Ah, my friend, this is something that I've been breaking my head over for many weeks too! I'd been trying to find out the name of the PDC of my domain and have drawn up naught till date! :-( Please let me know if you find something

---

