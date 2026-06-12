---
title: "Directory Access Protocol"
date: 2008-03-07
forum: Networking &amp; Wireless
---

### Post by dragobr on 2008-03-07
I don't know much about networks, but but it seems that at my university they use DAP on a Windows network in order to authenticate clients.. is there a way to authenticate myself into this dap server using ubuntu?

---

### Post by Paris Heng on 2008-03-07
> **dragobr said:**
> I don't know much about networks, but but it seems that at my university they use DAP on a Windows network in order to authenticate clients.. is there a way to authenticate myself into this dap server using ubuntu?

Yes. Your campus network are using LDAP. Maybe you can look into the **wpa_supplicant** that support LDAP. I don't know so well about this. I think wpa_supplicant config file enable you to set all the required authentication, e.g. Radius, NAS, LDAP, so on.

---

