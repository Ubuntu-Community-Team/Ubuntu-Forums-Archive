---
title: "Key ring issue"
date: 2007-06-10
forum: Networking &amp; Wireless
---

### Post by soulence on 2007-06-10
I have forgotten my primary keyring password 
Is there a way to find this out or do i have to reformat?

---

### Post by spd106 on 2007-06-11
I think the only way around this is to delete the keyrings. Each application will then prompt you to create a new keyring.

---

### Post by satbunny on 2007-07-19
Please could you tell me (as root) how to delete the keyrings. Mine just ain't behaving.

---

### Post by spd106 on 2007-07-19
The keyring is owned by the user, so you shouldn't need root privileges to delete it. You just need to enter the user's password to decrypt the stored keys. 

The keyrings are stored under ~/.gnome2/keyrings/

---

### Post by satbunny on 2007-07-19
Thanks, deleted it. Forgot pasword, started again.

---

