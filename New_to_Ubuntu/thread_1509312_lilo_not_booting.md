---
title: "lilo not booting"
date: 2010-06-14
forum: New to Ubuntu
---

### Post by rangerx52 on 2010-06-14
so i'm not totally new to linux, but i am outside my realm in this question. last distro i used was mandrake 9, not onto ubuntu 10.4

i have ubuntu on a 320gb drive, freshly formatted. i had xp on a 1tb ntfs drive, installed beforehand. When i installed, i said yes when it asked if i wanted to use a bootloader, and selected lilo.

so i boot up, and it goes straight to ubuntu. 

i went to the software download center, and found lilo listed there, and clicked install. A popup appeared, and quickly closed by itself- i caught part of it, saying that something needed to be configured first, but i didnt have a chance to see what file it was that needed configuring, let alone what i needed to do with it.

rebooted, lilo didnt start. went back to the download center, removed lilo, and reinstalled it- this time no popup. it doesnt list it under the installed programs list either, but a search does show files present on the computer. i just find it odd that nothing is added to the administrator tools list to allow configuration.

would anyone know what exactly i'm supposed to do to actually get it to boot to lilo instead of straight to ubuntu?

---

### Post by mbzn on 2010-06-14
Haven't heard of lilo in years... Try removing lilo and replacing it with grub. Most Ubuntu users use it and should be able to give you better help with it.

---

### Post by sandyvong on 2010-06-14
The problem was that old installations were running an old version of  LILO and 2.4 kernels. When I copied the new ramdisk over and the new 2.6  kernel over to running systems, I was running lilo meant for the old  days. The new version of LILO works fine, however I have some chicken  and egg stuff going on with this tricky update.

---

### Post by mbzn on 2010-06-14
Can you access the lilo screen? Lilo needs to first mount your win partition before it will load it. other than that i don't really have much knowledge on the matter. Good luck, hope one of the Guru's can help you out.

---

### Post by rangerx52 on 2010-06-14
> **sandyvong said:**
> The problem was that old installations were running an old version of  LILO and 2.4 kernels. When I copied the new ramdisk over and the new 2.6  kernel over to running systems, I was running lilo meant for the old  days. The new version of LILO works fine, however I have some chicken  and egg stuff going on with this tricky update.

you posting in the right thread?

for me, its a fresh install on a fresh partition, with the current updated version of lilo.

however i'm not married to it or anything- any significant difference between it and grub or grub2?

---

### Post by rangerx52 on 2010-06-14
and no, i cannot access the lilo screen. it's like it doesnt even exist. i install from the download center, and then it sits there, with a little message at the bottom saying something about a maintenance status, and does not get added to the list of installed programs. 

i never see any prompts, or options, or menu items, or anything at all. just boots straight to ubuntu without any dialogues when i boot.

---

### Post by mbzn on 2010-06-14
Could it be possible that you have grub2, and loading with that. you could try pressing shift when loading to verify

---

### Post by rangerx52 on 2010-06-14
i'll give that a shot next time i'm on that computer.

btw, is there an advanced mode for ubuntu? its very nice, and works wonderfully, but the controls and everything seem kind of, well... simplistic and Mac-ish

---

### Post by Joe of loath on 2010-06-14
> **rangerx52 said:**
> 
btw, is there an advanced mode for ubuntu? its very nice, and works wonderfully, but the controls and everything seem kind of, well... simplistic and Mac-ish

...The Terminal?

---

