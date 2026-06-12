---
title: "[SOLVED] Vitrualbox guest additions install problem"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by Charlie Chick on 2008-12-25
Hello Everybody,

Am I the only saddo sitting by the computer on Christmas morning?

I installed Xubuntu 8.10 inside Virtualbox and I can't get the Guest Additions to install. I mounted the iso file and it shows on the Xubuntu desktop. If I click it to install it says that I must have root priveliges. 

After looking at the help files, I tried opening the terminal and typing their suggestion: **su ./VBoxLinuxAdditions-x86.run** but it didn't work. I then replaced su with sudo but it also didn't run. Now I'm stuck. Can anybody help, please?

Wishing you all, and especially the hardworking experts who answer all our stupid questions, a very merry Christmas and a happy New Year.

Charlie

---

### Post by Elfy on 2008-12-25
Although the file look slike it's on the desktop - it's mounted on the cdrom

Try 

```
cd cdrom
sudo ./Vbo<tab>
```

Tab should autocomplete the name for you - useful :)

If it's not in cdrom try cdrom0

No you're not the only one using your pc - happy xmas and all that :D

---

### Post by Charlie Chick on 2008-12-25
Thanks for your help. It didn't *quite* work as you suggested, but the important clue was that it was it was mounted on the cd rom and not the desktop. Trying cd cdrom didn't work, so I went to the CD ROM in Places and noticed that it wasn't mounted. I mounted it and then selected 'open in terminal'. Only then was I able to install the guest additions.

Thanks once again for your help and Merry Chrismas to you!

Charlie

---

