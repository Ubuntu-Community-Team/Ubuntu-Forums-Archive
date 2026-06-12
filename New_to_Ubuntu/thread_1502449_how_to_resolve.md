---
title: "how to resolve"
date: 2010-06-05
forum: New to Ubuntu
---

### Post by chandrav23 on 2010-06-05
Hi

i tried to change my root password and it has been resolved but i found some quarys?
 
i did as below steps.

boot through
1. Ubunut 9.04 kernal 2.6  28 genaric (recovery mode)
2. enter e to edit
3. kernal /boot/vm
4. e to edit
5. after (ro single )  i typed rw init=/bin/bash
6. press enter
7. b for boot
8. root@(none)# passwd wtn
9. password updated successfully

From this sessaion how to come out(login screen) could u pls advise also i typed (exti) as below
10. root@(none)# exit
11. hit enter button

My system hanged and i got below msg.
kernal panic -not syncing : attempt to kill  init

I restarted forcefully.

How to resolve it..............

thanks
ch

---

### Post by cariboo on 2010-06-05
You don't enable the root account from grub. Try booting from the Live CD and fix grub, Go [here]("https://wiki.ubuntu.com/Grub2") and scroll down to Recover Grub 2 via LiveCD, and follow the instructions. I would suggest you have a look at [this]("https://help.ubuntu.com/community/RootSudo") document, before trying to enable the root account again.

---

