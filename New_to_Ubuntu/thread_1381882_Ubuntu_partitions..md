---
title: "Ubuntu partitions."
date: 2010-01-15
forum: New to Ubuntu
---

### Post by DeeDez on 2010-01-15
Hi everyone, I have a dual boot laptop (Windows 7 and Ubuntu9.04) with 3 unallocated partition spaces that I would like to add to my Ubuntu9.04.  What's best way to go about this?  Be gentle, I'm still learning linux.

---

### Post by raymondh on 2010-01-15
> **DeeDez said:**
> Hi everyone, I have a dual boot laptop (Windows 7 and Ubuntu9.04) with 3 unallocated partition spaces that I would like to add to my Ubuntu9.04.  What's best way to go about this?  Be gentle, I'm still learning linux.

Kindly post a screenshot of gparted.  

If you're not familiar with that, access gparted thru system > admin > partition editor.  To take a screenshot you can either press the PRNTSCR key or, access the camera thru applications > accessories.  Save the screenshot to desktop (or any place/folder you wish).  To post it here, click on the ATTACH (paperclip) icon in the toolbars > browse for your screenshot > upload.

You can use gparted to 'add those partitions'.  I would just like to have a visual of your HD to be sure about the steps/process to do so.

Regards,

Raymond

---

### Post by DeeDez on 2010-01-15
> **raymondh said:**
> Kindly post a screenshot of gparted.  

If you're not familiar with that, access gparted thru system > admin > partition editor.  To take a screenshot you can either press the PRNTSCR key or, access the camera thru applications > accessories.  Save the screenshot to desktop (or any place/folder you wish).  To post it here, click on the ATTACH (paperclip) icon in the toolbars > browse for your screenshot > upload.

You can use gparted to 'add those partitions'.  I would just like to have a visual of your HD to be sure about the steps/process to do so.

Regards,

Raymond


Thanks Raymond, thus far.  I didn't previously mention that I had not installed Win7 (assuming it would go over smoothly).  I've completed the install but with only a little problem (I hope).  Now, when my computer boots, there's no option to dual boot. So I can't get to the partition editing yet.  Any suggestions?

---

### Post by audiomick on 2010-01-15
Hallo. This is a little confusing. You say you have a dual boot laptop with Win7 and Ubuntu, and then you say you haven't installed win7.

Please tell us again exactly what you think is installed, and what are you trying to do right now.

---

### Post by Grenage on 2010-01-15
Is Ubuntu installed yet?  If not, you can still load up using it as a live CD.  If it's not yet installed you can easily install it, Ubuntu will sort out your dual-boot grub config automatically.  You just have to be careful that you don't use the whole drive; if in doubt follow **raymondh**'s advice.  Use the live CD and post a gparted screenshot.

---

### Post by raymondh on 2010-01-15
confused as well :confused:

What OS do you have installed right now? 

Raymond

---

### Post by DeeDez on 2010-01-15
Sorry guys.  I currently have Windows 7 and Ubuntu 9.04 installed on my laptop.  Some how, installing Win7 skips the dual boot menu options during start up.

---

### Post by audiomick on 2010-01-15
So you installed or re-installed windows after Ubuntu was installed. That overwrites Grub, which needs to be fixed.

There are instructions here
[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

that will get you sorted out.

---

