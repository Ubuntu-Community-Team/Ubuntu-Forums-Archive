---
title: "Password Issue when adding printer from Windows 7"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by happy_pig on 2010-11-23
Hi
I have tried to find the answer by searching but I can't find it.

I am trying to add a printer to my 10.10 laptop that is attached to my Windows 7 machine.
I access this Windows machine via my wireless network.

I go to the Printing,add printer area in accessories, I click on the Windows printer via Samba, then I browse for my printer, the SMB Browser shows my Windows network under the share column. I then click on the arrow and it goes to my PC (where the printer is attached to).
The problem occurs when I then click on the PC name I get a box that says - You must log in to access DESKTOP (my pc windows name), there are three inputs required Username, Domain and password.
I am not sure what to put here? I have tried a number of combos that might work but access is denied.

Can someone help? let me know what info you need?

Thanks in advance

---

### Post by cariboo on 2010-11-26
Use your Windows 7 user name and password, and whatever ever workgroup name you are using,

---

### Post by sandyd on 2010-11-26
> **happy_pig said:**
> Hi
I have tried to find the answer by searching but I can't find it.

I am trying to add a printer to my 10.10 laptop that is attached to my Windows 7 machine.
I access this Windows machine via my wireless network.

I go to the Printing,add printer area in accessories, I click on the Windows printer via Samba, then I browse for my printer, the SMB Browser shows my Windows network under the share column. I then click on the arrow and it goes to my PC (where the printer is attached to).
The problem occurs when I then click on the PC name I get a box that says - You must log in to access DESKTOP (my pc windows name), there are three inputs required Username, Domain and password.
I am not sure what to put here? I have tried a number of combos that might work but access is denied.

Can someone help? let me know what info you need?

Thanks in advance
Thats because your using windows homegroups.
samba doesn't work with them.

---

### Post by Tamalin on 2010-11-26
I managed to get around a problem like this by setting up the printer as an LPD printer.  Then I could find it without too much work.  There is an overview at [http://technet.microsoft.com/en-us/library/cc731857.aspx](http://technet.microsoft.com/en-us/library/cc731857.aspx)

Good Luck!

---

