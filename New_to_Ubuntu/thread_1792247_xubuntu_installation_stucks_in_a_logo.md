---
title: "xubuntu installation stucks in a logo"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by scottdrakkarious on 2011-06-28
i love ubuntu(32 bit) which i have successfully installed in my old desktop pc.So i decided to put xubuntu 11.04 in my brand new hp 64 bit laptop(windows 7 pre-installed in it).
my laptop details are:
processor: core i3-380m,2.53 ghz
graphics: ati radeon, 1gb
ram: 3gb,ddr3
harddisk: 320 gb
i downloaded xubuntu 11.04 (desktop.amd64.iso) for my 64 bit laptop and burned it to a dvd.After inserting dvd in my laptop while booting i am asked to select a language.After selecting language i am shown with a screen : try xubuntu,install xubuntu,check for errors,etc like things.When i select try xubuntu or select install xubuntu i am simply shown with a xubuntu logo.Previously i waited for 1 hour thinking that it is a installation procedure but it badly stucks there and my laptop makes noisy sound and gets heated up and completely hangs no button works ,so i completely remove my battery to turn off my laptop.I tried this procedure 6 times since yesterday but everytime it stucks in a logo making loud noise and heating my laptop
i am a newbie for linux plz explain the solution of this problem in simple language
thanks in advance

---

### Post by Alwimo on 2011-06-28
That has happened to me too. I downloaded and burned the .iso again and it worked.
 
I don't think you will get much benefit from the 64 bit version with just 3gb of RAM, by the way.

---

### Post by linuxyogi on 2011-06-28
```
md5sum image.iso
```Compare the hash here [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by Alwimo on 2011-06-28
I'll hopefully build on the post by linuxyogi.
 
Save the xubuntu 11.04 iso you downloaded in the home folder of your Ubuntu PC. Open up the terminal and copy/paste "md5sum xubuntu-11.04-desktop-amd64.iso" without the quotation marks into the terminal (Ctrl+Shift+v is how to paste in the terminal, not Ctrl+v).
 
If it says anything other than "f1b224166bea923042e53b0e9d5ff63f" then it the .iso is corrupted and you should download it again.

---

### Post by scottdrakkarious on 2011-07-06
thanks for ur reply, i checked md5 checksum-it is exactly the same.I think many people hv same problem,no matter what u do ubuntu installation 11.04 stucks in a logo on em64t platforms,also my ubuntu 32 bit doesnt install in my laptop,same problem as xubuntu(64-bit)

i hv one doubt-can we really install ubuntu 32 bit on em64t architecture?

---

### Post by Alwimo on 2011-07-06
Yes, you can install 32-bit Ubuntu on 64-bit computers.

---

### Post by scottdrakkarious on 2011-07-07
i have already said about my laptop details - which one is better for my laptop(ubuntu 32 or 64 bit) i have 3gb ram and em64t processor

---

