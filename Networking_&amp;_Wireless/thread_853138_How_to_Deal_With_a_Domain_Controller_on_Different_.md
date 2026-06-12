---
title: "How to Deal With a Domain Controller on Different Subnet"
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by jperrella on 2008-07-08
I am attempting to integrate Ubuntu 804 clients into a windows network with roaming user accounts and Active Directory. I have Likewise installed with the gui. When I go to connect to the domain using likewise I receive the following error:

Error code: CENTERROR_COMMAND_FAILED (0x00002014)

Backtrace:
    main.c:297
    djmodule.c:158
    djfirewall.c:685
    djfirewall.c:601

I believe this is because the domain controller is on a different subnet. For windows clients we use an lmhosts file to rectify the problem.

Is there a similar solution in linux, or do i have to do something completely different?

---

### Post by c0lin on 2008-08-16
I'm getting the same error. But our domain controller isn't on a different subnet and I've never had to change the lmhosts file on the Windows machines.

Oh and the linux equivalent of lmhosts is /etc/hosts I believe.

---

### Post by c0lin on 2008-08-16
Ok I dealt with the "Error code: CENTERROR_COMMAND_FAILED (0x00002014)" error by adding the IP address of the domain controller and the host name to the hosts file:
```
127.0.0.1 localhost
127.0.1.1 computername.cra.local computername
10.6.1.10 cra.local
```

Edit:
After getting passed the 0x2014 error I received this error when attempting to join: "Error: Unable to join domain [code 0x0008000e]". I read somewhere (don't remember where) to change the nsswitch.conf. I said change the "hosts:" line from whatever it is to: "hosts: files dns mdns4_minimal mdns4 winbind". After I changed that line my ubuntu laptop successfully joined.

---

