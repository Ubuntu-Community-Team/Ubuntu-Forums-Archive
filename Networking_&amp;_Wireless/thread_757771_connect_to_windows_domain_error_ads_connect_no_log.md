---
title: "connect to windows domain error: ads_connect: no logon servers"
date: 2008-04-17
forum: Networking &amp; Wireless
---

### Post by boomer84 on 2008-04-17
I have setup samba/kerberos to connect to my windows 2k3 domain which it does in the terminal under root no problem but when I try to connect to the server using the initial GUI logon prompt it says "no logon servers"

I have setup PAM as stated on the tutorial:

file: /etc/pam.d/common-account

account sufficient       pam_winbind.so
account required         pam_unix.so

file: /etc/pam.d/common-auth

auth sufficient pam_winbind.so
auth sufficient pam_unix.so nullok_secure use_first_pass
auth required   pam_deny.so


but still nothing

---

