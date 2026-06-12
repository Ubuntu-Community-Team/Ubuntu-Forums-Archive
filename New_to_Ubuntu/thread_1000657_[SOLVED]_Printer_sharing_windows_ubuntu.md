---
title: "[SOLVED] Printer sharing windows ubuntu"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by nothingspecial on 2008-12-03
My friend google is really letting me down with this one. Every bit of info I can find is either hopelessly outdated or the wrong way round.
I`m trying to help one of my bosses, who finds himself with a new pc running 8.10 to print to his other pc,s printer running windows.

All the info I can find tells me how to print from windows to a printer connected to ubuntu. I don`t have a windows pc for testing. 

Is it as simple as sharing the printer in windows and then showing printers connected to other systems on his ubuntu box?

Thanks

---

### Post by philinux on 2008-12-03
Yes you need to share the printer on the wondows box. Then on the buntu box add printer using "Windows printer via Samba".

I had a glitch with this. I had to find out the ip address of the windows box and manually add it as smb://192.xxx.xxx.xxx/printername

This helped me.
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by nothingspecial on 2008-12-03
Thanks.

---

