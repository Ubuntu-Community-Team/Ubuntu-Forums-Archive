---
title: "Default password for openssh server"
date: 2014-02-16
forum: Networking &amp; Wireless
---

### Post by Bruce_Wayne on 2014-02-16
Does anyone know the default password for openssh?

---

### Post by ian-weisser on 2014-02-16
I don't understand...
Why would openssh-server have a default password? That would be quite the security hole.

It's supposed to use _your_ password. Or keys.

---

### Post by Bruce_Wayne on 2014-02-17
Every time I use my password it says permission denied.

---

### Post by ian-weisser on 2014-02-17
Have you configured /etc/ssh/sshd_config?
Do you have an account on the server?
Are you using the password for the server account? (That's a common mistake)

---

### Post by Bruce_Wayne on 2014-02-17
Could you guide me through it.

---

### Post by ian-weisser on 2014-02-17
Okay.
Do you have an account on the server, with a password?

---

