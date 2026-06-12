---
title: "No networking with 8.04 LiveCD but 6.06 LiveCD works"
date: 2008-09-27
forum: Networking &amp; Wireless
---

### Post by Jonam on 2008-09-27
I've tried searching these forums for a solution but have not been able to find anything that will get networking (either wireless or wired) working with my 8.04 LiveCD on my laptop. The same laptop boots with an original 6.06 liveCD and works fine on either wireless or wired.

My laptop is a Compaq nc6400 with Broadcom BCM5753 ethernet and an Intel 3945ABG wireless. The only thing I notice using dmesg is a line that says:

eth0: no IPv6 routers present

Under 8.04, being a LiveCD, I cannot change the aliases file to disable IPv6. Trying to enable wireless, I note that the wireless light does not come on when enabled. I have to use dmesg to find out the status. Running:

$ sudo dhclient eth0

returns no IP address allocation. My router (D-link DI624) does not see the laptop either. 

I was keen to upgrade to 8.04 but seeing that I cannot get even basic (wired) networking going on a known 6.06 working machine, I am reluctant to switch over at this stage. I would appreciate any help to resolve this issue.

Regards,

Jonam

---

