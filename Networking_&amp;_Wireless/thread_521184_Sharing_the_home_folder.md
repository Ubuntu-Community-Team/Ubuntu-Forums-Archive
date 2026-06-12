---
title: "Sharing the home folder"
date: 2007-08-09
forum: Networking &amp; Wireless
---

### Post by df9517 on 2007-08-09
I keep getting an error everytime I login saying that I am not alllowed to share my homefolder with writable rights. The permission should be at least 644.

I did some changes when trying to set up samba but I never got it to work properly. How do I change the permission back so that Linux wont bother me about this any more?

---

### Post by ddrichardson on 2007-08-09
Either chmod 644 /home/username or use Nautilus and change the permissions back by right clicking on your home folder.

---

### Post by df9517 on 2007-08-09
see below

---

### Post by df9517 on 2007-08-09
see below

---

### Post by df9517 on 2007-08-09
See below.

---

### Post by df9517 on 2007-08-09
My original problem still remains. Everytime I log in I get following message:

User's $home/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. Users $home directory must be owned by user and not writable by others.

Please someone. Guide me in what to do to correct this. Permissions and ownership is so difficult.

---

### Post by lars.vaerland on 2007-08-11
> **df9517 said:**
> My original problem still remains. Everytime I log in I get following message:

User's $home/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. Users $home directory must be owned by user and not writable by others.

Please someone. Guide me in what to do to correct this. Permissions and ownership is so difficult.

i got the same error-message as well. anyone got a suggestion?

---

### Post by lars.vaerland on 2007-08-11
> **lars.vaerland said:**
> i got the same error-message as well. anyone got a suggestion?

Ooops. should have searched forum a bit more before posting. sorry about that!

---

