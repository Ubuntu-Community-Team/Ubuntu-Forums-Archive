---
title: "How return usplash theme to default"
date: 2009-05-27
forum: New to Ubuntu
---

### Post by mvalviar on 2009-05-27
Hi, I installed kubuntu-desktop on my ubuntu install. I like it and I want to keep it. However I still prefer the gdm and the default ubuntu usplash. I was able to revert back to gdm but I don't know how to revert to the default usplash can anyone help please?

---

### Post by Didius Falco on 2009-05-27
> **mvalviar said:**
> Hi, I installed kubuntu-desktop on my ubuntu install. I like it and I want to keep it. However I still prefer the gdm and the default ubuntu usplash. I was able to revert back to gdm but I don't know how to revert to the default usplash can anyone help please?

Right-click the **Fast User Switcher** (where you go to log out, hibernate, shut down, etc.) and choose **Setup Login Screen**. You'll be asked for your password, then choose the **Local** tab. You can choose one to always use, or pick a variety and have it choose between them randomly, depending on how you set it up.

Regards,

Didius

---

### Post by kukibird1 on 2009-05-27
> **mvalviar said:**
> Hi, I installed kubuntu-desktop on my ubuntu install. I like it and I want to keep it. However I still prefer the gdm and the default ubuntu usplash. I was able to revert back to gdm but I don't know how to revert to the default usplash can anyone help please?

In terminal type 

sudo update-alternatives --config usplash-artwork.so
 

follow the onscreen instructions

then type

sudo dpkg-reconfigure usplash

when you reboot you will have the default ubuntu usplash again .

You still need to use the setup login screen option to get the default ubuntu login screen for gdm.

---

### Post by mvalviar on 2009-09-10
Perfect.

---

