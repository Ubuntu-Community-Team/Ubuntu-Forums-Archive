---
title: "clean install 10.04 problems"
date: 2010-11-14
forum: New to Ubuntu
---

### Post by Dermot Doyle on 2010-11-14
Hi All,
I am trying a clean install of 10.04 lts on my Dell Inspiron 1525 running 8.04, but with no success. I have downloaded 10.04 and burnt it to a CD as per the instructions on the download site. I have restarted the computer with the CD in the drive, but it boots to the hard drive. I have checked that all of the files have downloaded. I have restarted the computer and got into the boot menu, but it doesn't offer me the option to boot from the CD drive. Now what do I do? Cheers.

---

### Post by spiky001 on 2010-11-14
select the little man at the bottom when cd boots

---

### Post by Dermot Doyle on 2010-11-14
I'm sorry, I have no idea what you are talking about. I should have mentioned that I am not very computerate.

---

### Post by matt_symes on 2010-11-14
Hi

Have you tried setting the boot order in the BIOS?

Kind regards

---

### Post by Dermot Doyle on 2010-11-14
Hi, I *think* that's what I've tried to do. If I press escape as it starts up I get into a menu, but it only offers me the various kernels of 8.04 to choose from. Is that not the BIOS menu and if not, any ideas on how to et into it?
Cheers

---

### Post by matt_symes on 2010-11-14
Hi

I believe you need to press F2 to get into the BIOS on your machine when it first boots up. There will be a boot option there to change the boot order. I dont believe what you have done so far is correct. I dont actually have a dell so i am unfamiliar with the BIOS on that machine. However that would be the first thing i would check. 

EDIT: Just found this for dell's

**DELL**  
[LIST]
[*]After switching on your computer, let the DELL logo appear  before pressing the F2 key until Entering Setup  is displayed on the  screen.
[*]Previous versions of DELL might require to press CTRL+ALT+ENTER to access the BIOS set up menu.
[*]The DELL laptops will use the Fn+ESC or Fn+F1 keys to access the BIOS set up.
[/LIST]
Make CDROM your first boot device and HDD (or something similar) your second 

Kind regards

---

### Post by Dermot Doyle on 2010-11-14
F2 did the job. Thanks for that.

---

