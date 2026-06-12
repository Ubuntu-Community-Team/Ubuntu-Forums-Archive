---
title: "Zend Optimizer just totally locked my system!"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by k3lt01 on 2010-02-14
The title pretty well says it all. I have been surfing the net all morning and went to go into a forum I have been in a few times already this morning. All of  sudden this strange page come up, to do with a thing called Zend Optimizer (I'd attach a screenshot but for some reason atm I can't do that) and my system jammed right up. I had to use the power button to reboot.

After I rebooted and started firefox it went back to that page but I back tracked before anything happened.

Has anyone else had this happen? Is this a cross platform trojan or something?

---

### Post by mikewhatever on 2010-02-14
From what I understand, browser exploits are usually cross platform. Try the following command, and then relaunching Firefox:

mv .mozilla .mozilla-old

---

### Post by k3lt01 on 2010-02-14
Everything seems to be fine now, I was surprised it could lock my system up like it did. I think I'll do some searching on the issue cause at least 1 other person on the other forum was affected.

---

### Post by sandyd on 2010-02-14
> **k3lt01 said:**
> Everything seems to be fine now, I was surprised it could lock my system up like it did. I think I'll do some searching on the issue cause at least 1 other person on the other forum was affected.

Zend Optimizer is for webservers (youll probably use it in your server thats in your sig). It decrypts zend-encoded files and optimizes php compilation.
[offtopic]
I personally find xcache faster tho.
[/code]


It was likely the flash that killed the system. Ive had it happen a few times before,

---

### Post by k3lt01 on 2010-02-14
I took a look at the website for it since my last post. I thought there was a trojan or something affecting the other forum, I suppose it is possible that it did. What gets me is how it affected my little old Acer, that is why I am still a little suspicious about it.

---

