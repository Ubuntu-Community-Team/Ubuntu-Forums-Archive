---
title: "Ubuntu-Mac shared folder"
date: 2009-10-25
forum: New to Ubuntu
---

### Post by Loki57701 on 2009-10-25
I created a shared folder on my ubuntu box that I can access with my mac using samba. The only way I can connect to the shared folder from my mac is by entering my ubuntu accounts login/psswd when the prompt comes up. I want to add another user to samba but the guides I'm following online arent working, it seems theres no easy way to add a user to samba for some reason.

I tried 
```
sudo smbpasswd -a chris
```
and after I enter and confirm a password I get an error:

```
Failed to add entry for user chris
```
(I've tried other user names just to be sure)

Am I suppose to add the new user by editing /etc/samba/smb.conf?

---

### Post by Loki57701 on 2009-10-25
Ok well apparently I'm just retarded. If you download:

```
sudo apt-get install system-config-samba
```

Theres an option under the "preferences" menu that clearly says "samba users" and you can easily add users..

---

### Post by swerdna on 2009-10-25
> **Loki57701 said:**
> I created a shared folder on my ubuntu box that I can access with my mac using samba. The only way I can connect to the shared folder from my mac is by entering my ubuntu accounts login/psswd when the prompt comes up. I want to add another user to samba but the guides I'm following online arent working, it seems theres no easy way to add a user to samba for some reason.

I tried 
```
sudo smbpasswd -a chris
```
and after I enter and confirm a password I get an error:

```
Failed to add entry for user chris
```
(I've tried other user names just to be sure)

Am I suppose to add the new user by editing /etc/samba/smb.conf?

You can only add users who pre-exist as Ubuntu users, was that it?

---

