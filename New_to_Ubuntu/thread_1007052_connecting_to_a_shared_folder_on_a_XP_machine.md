---
title: "connecting to a shared folder on a XP machine"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by pshootr on 2008-12-10
I read that samba can help with this. I also noticed under "places/connect to server" I see where I can choose "windows share" May be I don't need samba?  Could someone point me in the rite direction please? Thanks

---

### Post by Presto123 on 2008-12-10
Well...if Samba is required it SHOULD prompt you beforehand. Click on the menu under "Places" and find "Network"...a Window's network should be listed as such and you can click your way through the computers/files shared that way.

MOST Likely, Samba will be needed, but as I said, it should prompt.

---

### Post by cariboo on 2008-12-10
By default Ubuntu will connect to Windows shares, you need Samba for Windows to connect to Ubuntu shares. For Ubuntu to connect to windows share, the only thing you have to worry about is that the computers are all in the same workgroup.

Jim

---

### Post by iaculallad on 2008-12-10
When in your Nautilus browser, you could try connecting to your XP shared folder by (input the string below on location):

smb://xxx.xxx.xxx.xxx

Just replace the xxx.xxx.xxx.xxx with your own private IP.

---

### Post by Dedoimedo on 2008-12-10
Hello,

Of course, make sure the folder is shared on XP first :)
After that, go via Places > Network > Windows network > ...

Cheers,
Dedoimedo

---

### Post by pshootr on 2008-12-10
Thanks alot guys for the good info. sure enough the windows share showed up fine.

---

