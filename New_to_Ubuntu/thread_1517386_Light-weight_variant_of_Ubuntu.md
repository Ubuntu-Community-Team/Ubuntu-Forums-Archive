---
title: "Light-weight variant of Ubuntu"
date: 2010-06-25
forum: New to Ubuntu
---

### Post by haygun on 2010-06-25
I am new on the Ubuntu train and have been dual booting it on my MacPro for a little over a month. I love what is being done! I would like to install Ubuntu on an older Pentium 4 PC. I have tried installing 10.0.4, but it runs VERY slowly. I am wondering if there is a better version that I could use that would make the machine run a bit more smoothly.

Thanks

---

### Post by VH-BIL on 2010-06-25
What do you mean slowly? is this with desktop effects running?

---

### Post by haygun on 2010-06-25
Basically I do a clean install and have made no changes but it is VERY slow. Opening up Firefox takes over a minute. When I type, the computer lags behind what I am typing. It is just painful to use. I had XP and it ran "okay", much faster. I am just trying to transition to Ubuntu.

---

### Post by VH-BIL on 2010-06-25
Is compiz enabled?

---

### Post by I8NY on 2010-06-25
open the terminal and type "top", see if xorg is using a 100% CPU.  I have had problems with xorg using up all the cpu, i think i did a reinstall to fix it.

---

### Post by ssulaco on 2010-06-25
> **haygun said:**
>  Opening up Firefox takes over a minute. 
If you have extensions in use,try disabling one at a time.

---

### Post by VH-BIL on 2010-06-25
> **I8NY said:**
> open the terminal and type "top", see if xorg is using a 100% CPU.  I have had problems with xorg using up all the cpu, i think i did a reinstall to fix it.

That can be a graphic driver issue as well. if xorg is running high cpu try using the vesa driver just to check if you get the same results.

---

