---
title: "How To create Backup Domain Controller (when PDC doesn't have LDAP)?"
date: 2013-12-10
forum: Networking &amp; Wireless
---

### Post by feroz216 on 2013-12-10
[COLOR=#333333][FONT=UbuntuRegular]After searching & reading tutorials i understand that LDAP should be installed & configured on PDC to create a BDC. As i created PDC with samba without LDAP.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]My question is are..[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]1). Is it safe to configure LDAP on my running PDC (12.4.1 Server) so that i can create BDC ?[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]2). Is there any other option to create BDC without doing anything on my running PDC?[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Thanks in advance.[/FONT][/COLOR]

---

### Post by bashiergui on 2013-12-11
By "running PDC" do you mean "in production?" If you don't get any answers you might set up a test environment and see if it breaks there first.

---

### Post by feroz216 on 2013-12-12
> **bashiergui said:**
> By "running PDC" do you mean "in production?" If you don't get any answers you might set up a test environment and see if it breaks there first.
Yes, it's in production. Test server is one option.

---

### Post by bashiergui on 2013-12-12
Pretty sure I fail at interneting if I don't give you this meme.


If you can demonstrate that you understand what business processes will be affected if something goes wrong, that you understand the cost to the business if those processes go down, and you have a plan to back out/revert if things go wrong, then yeah do it in prod. Get your boss to sign off on it for a little job security, too.

---

