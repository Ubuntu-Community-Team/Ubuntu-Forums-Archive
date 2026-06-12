---
title: "samba password login prompt?"
date: 2008-08-30
forum: Networking &amp; Wireless
---

### Post by Crahzee on 2008-08-30
I recently installed mythbuntu and decided to setup the samba service. And whenever I try to connect from my windows machine it prompts me to login. So I try to login in but nothing I try works. Is their any way to make it not prompt to login?

I can post the config if need be.

---

### Post by bab1 on 2008-08-30
I assume this is a workgroup setup.  Is that correct?  If that is correct have you added the XP user to the smbusers database?  The login/password must [COLOR="Red"]**exactly**[/COLOR] the same as the XP user login.

See this for basic info: [http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/]("http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/")

---

