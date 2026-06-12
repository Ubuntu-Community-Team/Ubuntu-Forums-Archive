---
title: "Samba - mounting/ passwd problem"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by Ordes on 2009-06-19
On my second PC i try to setup up two different shared folders (from two different accounts in ubu): 

1) public  (is user account)
2) only me  (is sudo account)

(both have different passwords, and are all added to smbpasswd, and enabled)

When i mount "public":
1) i get asked for the username/password, folder is mounted

When i mount "only me"
1) Under the default share options, i dont get asked for the password, it mounts it right away,
 --> the strange thing here is that under "public-account" & default settings i do get asked username/ passwd, even when permission "Others-Access" is enabled, how come i dont get asked the same on a different account, with different user/ passwd?

2) I change the permissions, (others no access), than i do get asked for the username/ passwd, but in the end i always get the message "unable to mount smb share".

What shall i do?

My aim is to have 
1) shared folders under public- user account, where everyone in my network can have access
2) to have a shared folder only me-user account, so only i have access to it

thanks

ps: none of the passwords are saved on the client machine..

---

### Post by Ordes on 2009-10-14
didnt know about ssh... as they are both linux machines, i removed smb, and use ssh now. everything runs smooth

---

