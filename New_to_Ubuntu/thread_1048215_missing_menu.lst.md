---
title: "missing menu.lst"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by ankitguptag18 on 2009-01-23
my menu.lst is missing can any one tell me how to reinstall grub as i cannot start my comp....

---

### Post by ET! on 2009-01-23
boot from live cd and type update-grub

---

### Post by caljohnsmith on 2009-01-23
Are you sure only your menu.lst is missing and nothing else? Did you accidentally delete it or do you know how it was lost? I think it would help to get a clearer picture of your setup first, so how about booting your Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what it will take to get Ubuntu booting OK again.

---

