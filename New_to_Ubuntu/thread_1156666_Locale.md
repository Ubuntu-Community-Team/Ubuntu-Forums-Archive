---
title: "Locale"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by disappearedng on 2009-05-11
Hey everyone

I have tried switching my default language to Chinese, (by switching to zh_CN.gb2312 locale). However, this has caused my entire gnome-desktop to be in Chinese.. but everything works great after that.

Is there a way for me to preserve my locale (en_CA.UTF-8) while getting applications like gneom-terminal to display encodings with zh_CN.gb2312? 

Thx

---

### Post by Dill on 2009-05-11
You may be able to use SCIM to switch between languages without changing the locale. See [https://help.ubuntu.com/community/SCIM#Using%20SCIM](https://help.ubuntu.com/community/SCIM#Using%20SCIM)

Cheers,
Dill

---

### Post by disappearedng on 2009-05-12
@Dill
I think you misunderstood me. I am not talking about inputting. Linux by default stores characters with utf-8 (someone in ubuntu-cn told me) and apparently the problem is when you are using the encoding gb1830.. and something doesn't match up.

Right now, I am writing a parser and within gnome-terminal, I am seeing all these junks from improperly parsed chinese words. However, if I switch my locale to zh, everything works fine. 

Is there a way for me to preserve the validity of my output while keeping my menus, firefox defaults to English?

---

