---
title: "Sharing Issue"
date: 2008-08-02
forum: Networking &amp; Wireless
---

### Post by wbrokow1 on 2008-08-02
I have a new hardy install and I can't seem to share any folders.
It gives an error saying I don't have permissions.
any guidance is appreciated.
Thanks

---

### Post by K2712 on 2008-08-02
Are you trying to share files with a Windows or Linux machine?

---

### Post by wbrokow1 on 2008-08-03
Both.
I will post another reply with the complete error message.
I am not at that computer now.
THanks

---

### Post by wbrokow1 on 2008-08-03
Here is the exact error I receive when I try to share a directory:

```

'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.

```

---

### Post by bubbahana on 2008-08-05
I am having the exact same issue.  New install and can't share folders with the same error message.

---

### Post by eival on 2008-08-05
follow these directions, it worked fine for me for with Hardy 8.04
i used the NAT share


[http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/](http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/)

---

### Post by Baelus on 2008-08-05
I don't know much about usershares, but it looks like this worked for somebody:

[http://ubuntuforums.org/showthread.php?t=825965]("http://ubuntuforums.org/showthread.php?t=825965")

---

