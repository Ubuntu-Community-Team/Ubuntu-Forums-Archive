---
title: "Have to type in keyring password to connect to wifi network"
date: 2011-03-02
forum: New to Ubuntu
---

### Post by johnflubber on 2011-03-02
After a clean install of ubuntu 10.10, everytime I boot up and try to connect to my home wifi network im prompted to enter my keyring password. Anyway to stop this and just connect to my network automatically? and this network is checked as auto in my edit connections menu.

---

### Post by josephmills on 2011-03-02
> **johnflubber said:**
> After a clean install of ubuntu 10.10, everytime I boot up and try to connect to my home wifi network im prompted to enter my keyring password. Anyway to stop this and just connect to my network automatically? and this network is checked as auto in my edit connections menu.
when  you set up ubuntu where you hard wired in?

---

### Post by beew on 2011-03-02
It is a pest, I just got rid of it. Go to Places >  Home, click on the file menu to show hidden files, then go to the folder .gnome2, open it and delete the folder called keyrings. Next time when you try to connect the keyring thing will show up to ask you to set a password, at this point you can pick a new password which you can remember, or set it to your login password or simply leave it blank and click ok,--that is what I did,-- it will then ask you if you want to go ahead with unsafe storage, just say yes and then it won't bother you again. I am not the CIA I don't need two layers of passwords just to connect to the bloody internet

---

### Post by johnflubber on 2011-03-02
Thanks after deleting the 'keyring' folder I wasn't prompted to set a new password at startup, and I can connect to my network automatically.

---

