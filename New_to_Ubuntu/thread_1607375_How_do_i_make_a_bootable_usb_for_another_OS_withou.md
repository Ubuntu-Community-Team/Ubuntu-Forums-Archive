---
title: "How do i make a bootable usb for another OS without affecting Ubuntu?"
date: 2010-10-27
forum: New to Ubuntu
---

### Post by Shadow15991 on 2010-10-27
Hi everyone. i'm a new user since september. i used to work under wxp. my computer was as slow as a snail. or even worse. someone told me linux was faster and more reliable. i downloaded ubuntu and have used it ever since. the reason is that i'm an engineer and most of the programs i need won't run on wine. like SolidWorks (2010) or CamWorks (2009) or my NC editors. even my robot SIM program doesn't works. i cannot teach anything to the robot (RoboCell) so i realized that i had to make a partition to my HDD, and install wxp in less than 20GB. My HDD has 320GB. but here comes the frenzy. my CD-drive doesn't works. how can i make a startup usb in Ubuntu? or how do i do the whole thing?
note that i'm not preferring W$xp, i have to use my apps.  

Thanks in Advance

---

### Post by sikander3786 on 2010-10-27
I don't really know if there is any successful method of installing XP from a USB stick regardless of Ubuntu or Windows as the source. For Linux there are a handful of tools.

Kind of an irrelevant answer but if you've got a Windows XP image, you can consider mounting it with any disc mount software under Ubuntu and install it in Virtualbox or any other Virtual Machine server as you'll be able to run both Ubuntu and Windows simultaneously.

[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

---

### Post by ironic.demise on 2010-10-27
> **Shadow15991 said:**
> Hi everyone. i'm a new user since september. i used to work under wxp. my computer was as slow as a snail. or even worse. someone told me linux was faster and more reliable. i downloaded ubuntu and have used it ever since. the reason is that i'm an engineer and most of the programs i need won't run on wine. like SolidWorks (2010) or CamWorks (2009) or my NC editors. even my robot SIM program doesn't works. i cannot teach anything to the robot (RoboCell) so i realized that i had to make a partition to my HDD, and install wxp in less than 20GB. My HDD has 320GB. but here comes the frenzy. my CD-drive doesn't works. how can i make a startup usb in Ubuntu? or how do i do the whole thing?
note that i'm not preferring W$xp, i have to use my apps.  

Thanks in Advance

Idea #1: Install WINE, A compatability layer that allows running of many .exe files.
Idea #2: As sikander said, use Virtualbox (sudo apt-get install virtualbox-ose) and make a virtual XP computer
Idea #3: Look up "BART PE"
Idea #4: use the startup disk creator to install a winxp iso (Doubtful to work)
Idea #5: Google a way to make a USB bootable and just place the contents of a WinXP iso.

Tip: I think using the term W$ is frowned upon here, I'm not 100% but I think it's a bit slanderous and that's not what people here are about... and most people don't care if you have a Windows partition still, You need it for some things... I still have one so I can play Maplestory and my girlfriend can play The Movies and the sims.

---

### Post by sikander3786 on 2010-10-27
> use the startup disk creator to install a winxp iso (Doubtful to work)

It is intended for Ubuntu only. You need a Windows specific tool to do that and I couldn't find one for Windows version prior to Vista.

> I think it's a bit slanderous and that's not what people here are about

As far he is dual booting Ubuntu or running Windows as a guest, it is fine ;-)

---

### Post by C.S.Cameron on 2010-10-27
I know what you mean needing a little XP, I'm a mechanical engineer myself.
My experience is that Vbox is too slow for Acad let alone SolidWorks.
My biggest wish is that Wine would work decently with these programs.
It is easy installing W7 from a pendrive, format it in NTFS, set boot flag and extract the iso or copy the CD contents to it. (all possible in Ubuntu).
I understand the procedure for making an XP install USB is available on the EEE PC page and can be found elsewhere on the net. 
Good luck

---

### Post by Shadow15991 on 2010-10-28
thanks man. as you see. solidworks is soooooo slow running on virtualbox. i'll try w7. i totally agree that linux is waaaaaaaaaaaaaaaaaaay better than w$. but there's no software like the ones i need for linux. 

long life to the penguins!!! Specially if they throw rocks to the windows!!!

---

### Post by beew on 2010-10-28
> **ironic.demise said:**
> 
Tip: I think using the term W$ is frowned upon here, I'm not 100% but I think it's a bit slanderous and that's not what people here are about....

Frowned upon by whom? This is not about the people, but the company. The number one and only mandate of Corporations is  by definition and BY LAW $ for shareholders, this is hardly controversial or slanderous, you think M$ is offering a community service?:confused:

---

### Post by ironic.demise on 2010-10-28
> **beew said:**
> Frowned upon by whom? This is not about the people, but the company. The number one and only mandate of Corporations is  by definition and BY LAW $ for shareholders, this is hardly controversial or slanderous, you think M$ is offering a community service?:confused:

My apologies, I must've been wrong.
Seems I just see it too many places in a negative context, carry on.
By the way, I didn't know that... nice tidbit

---

