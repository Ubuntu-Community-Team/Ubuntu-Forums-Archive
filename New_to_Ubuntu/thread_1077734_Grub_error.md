---
title: "Grub error"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by cheesedoodle on 2009-02-22
Hi i signed up for the forums half an hour ago and i was wondering if anyone could tell me how to make new posts? thanks. my reason is when i turn on my other laptop it says:

GRUB Loading stage1.5


GRUB loading, please wait...
Error 

i was wondering if anyone knows what this means.

---

### Post by overdrank on 2009-02-22
Hi and welcome. I moved your post to its own thread. In the  Absolute Beginner Talk forum you will see a new thread button in the upper left corner.

---

### Post by caljohnsmith on 2009-02-22
Which Grub error do you get? In order to get a clearer picture of your setup, how about booting your Ubuntu Live CD (the Ubuntu install CD), download the **Boot Info Script** to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

