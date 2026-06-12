---
title: "dual boot problem"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by hreikin on 2009-12-31
i installed ubuntu on my laptop, and left some unpartitioned space so i could install xp for using photoshop/bf2 and other things

i installed xp and now dont get an option to boot into ubuntu :S

what do i need to do to get the dual boot option ?

any help greatly appreciated

---

### Post by Hreinsi on 2009-12-31
Try install win first thats the easy way:P

---

### Post by hreikin on 2009-12-31
> **Hreinsi said:**
> Try install win first thats the easy way:P


i dont want to have to do it again, i had ubuntu for a couple of weeks before i got round to putting xp on it aswell so dont really want to start from scratch :P

does anybody know what i need to do ?

---

### Post by thatguruguy on 2009-12-31
Are you sure that ubuntu is still on the computer?

If so, you can try to reinstall grub2.  [https://help.ubuntu.com/community/Grub2#Reinstalling from LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

### Post by theozzlives on 2009-12-31
You need to re-install GRUB. Which version of Ubuntu you using? How you go about it depends on if you're using GRUB Legacy, or GRUB2.

---

### Post by Sef on 2009-12-31
> i installed ubuntu on my laptop, and left some unpartitioned space so i could install xp for using photoshop/bf2 and other things

i installed xp and now dont get an option to boot into ubuntu :S

what do i need to do to get the dual boot option ?

any help greatly appreciated

Try the ozzlives suggestion.   What happened is that Windows bootloader only sees Windows oses.   Hence, it will not pick up Ubuntu.  GRUB, on the other hand, will see both Windows and Linux.

---

### Post by hreikin on 2009-12-31
im using ubuntu 9.10 but i dont have a live cd for 9.1, i think i may have one for 8.04 tho will that work with the link in the post above ?

EDIT: lol i just read the link, it needs to be 9.10 or later :(

---

### Post by thatguruguy on 2009-12-31
> **theozzlives said:**
> You need to re-install GRUB. Which version of Ubuntu you using? How you go about it depends on if you're using GRUB Legacy, or GRUB2.

According to his avatar box thingy, he's using 9.10.

---

### Post by thatguruguy on 2009-12-31
> **hreikin said:**
> im using ubuntu 9.10 but i dont have a live cd for 9.1, i think i may have one for 8.04 tho will that work with the link in the post above ?

EDIT: lol i just read the link, it needs to be 9.10 or later :(

Can you not download the 9.10 iso and burn it from windows?

---

### Post by theozzlives on 2009-12-31
> **hreikin said:**
> im using ubuntu 9.10 but i dont have a live cd for 9.1, i think i may have one for 8.04 tho will that work with the link in the post above ?

EDIT: lol i just read the link, it needs to be 9.10 or later :(

No, 8.04 uses GRUB Legacy. 9.10 uses GRUB2, you'll need to download and burn a CD so you can use it to install GRUB.

---

### Post by hreikin on 2009-12-31
> **thatguruguy said:**
> Can you not download the 9.10 iso and burn it from windows?

i could try, altho i dont know if i have any disks here :P

ill just follow the link if i can get a disk and post back here if not

---

### Post by theozzlives on 2009-12-31
> **hreikin said:**
> i could try, altho i dont know if i have any disks here :P

ill just follow the link if i can get a disk and post back here if not

If you're out of CDs, and have a flash drive, and your system can boot off USB, you can download unetbootin and boot off the flash drive.

---

### Post by hreikin on 2009-12-31
> **theozzlives said:**
> If you're out of CDs, and have a flash drive, and your system can boot off USB, you can download unetbootin and boot off the flash drive.

im giving that a try altho i dont think it will work as my flash drive is password protected, but we will see

EDIT : it didnt work, im just gonna install xp over it all and then install ubuntu if anyones bothered :P

thanks for the help guys

---

