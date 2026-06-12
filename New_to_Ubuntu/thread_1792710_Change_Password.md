---
title: "Change Password"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by createdcreature on 2011-06-28
When I change my password, the next time I log in it says that the login keyring did not get unlocked when I logged into my machine. However, when I change back to my old password, it works fine. What can I do to solve it. I use ubuntu 10.04, not 11.04 as it says.

---

### Post by mcduck on 2011-06-28
> **Robert Moyse said:**
> When I change my password, the next time I log in it says that the login keyring did not get unlocked when I logged into my machine. However, when I change back to my old password, it works fine. What can I do to solve it. I use ubuntu 10.04, not 11.04 as it says.

The keyring gets unlocked automatically when you log in if the keyring password is the same as the login password.

However, if you change your login password, the keyring password doesn't get automatically changed, so you'll need to change it yourself as well. (the reason is that some people might want a different passwords for login and keyring, or might use multiple keyrings).

The keyring password can be changed using the "Passwords and Encryption Keys"-tool, just right-click the "passwords:login"-keyring and select "Change Password". Set it to same as your current login password and the keyring should once again unlock automatically.

---

