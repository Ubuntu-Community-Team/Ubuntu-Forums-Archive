---
title: "Share Problem"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by Whisp3r on 2010-05-26
I have two computers on a Netgear Router. I have install Samba on both, and have "shared" their Public folders under the user. I can see both shares without a problem on the Network. However, when I go to access one of the Shares, it asks me for my password? I have tried my user password from both computer with no success. Where do I setup a password for a shared folder?

---

### Post by fooman on 2010-05-26
to set a samba password,  run the following:

```
sudo smbpasswd -a <user name>
```~replace <user name> with your actual user name.  press enter and type in your new password.

when you finish....restart samba:

```
 sudo /etc/init.d/samba restart
```hope that helps.

---

