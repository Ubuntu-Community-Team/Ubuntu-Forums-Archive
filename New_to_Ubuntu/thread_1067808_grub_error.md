---
title: "grub error"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by ryanlbowen on 2009-02-12
i have just installed ubuntu 8.1 on my HP dv6000 laptop, to dual boot with windows vista...

i had to partition the drive in windows disk management, and then i installed ubuntu on that...i tried to add another 2gig partition yesterday for swap space.  however, when i restarted, i got a "Grub Error 17"

i did research, but nothing i found worked...i can't put a live cd in, though i can hook up my external hard drive (on which ubuntu is intalled), and run from there.  from there, i can mount both my vista partition and my ubuntu partition...i formatted the 2gig partition for swap space, but i still cannot boot either vista or ubuntu unless booting from the external drive...

i'm freaking out, because i can't use my computer - any help???

---

### Post by caljohnsmith on 2009-02-12
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop on the external drive, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by ryanlbowen on 2009-02-12
ok thanks man, i'll do that as soon as i get back to my desktop

i really appreciate the speedy response...thanks ubuntu community!

---

