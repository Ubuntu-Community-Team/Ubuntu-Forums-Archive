---
title: "windows and ubuntu question"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by Extract_Here on 2010-02-07
Okay so I have a 320gb hdd that has karmic on it and a 160gb hdd that is used for extra space. I just got windows 7 and i want to put it on the 160 so i can dual boot to windows 7 to play pc games. Now I know that you can play some older pc games with wine which I do. I'm currently running diablo 2 with wine and it works great. but it doesnt work with more high powered games like oblivion GOTY. Im not looking for virtualbox or vmware suggestions Im just wonder how i will be able to boot from each hdd when i start up the computer most of the time i will be booting to linux because i really dont like windows and nothing important will be on my windows comp except for games that i cant run on linux. I know i have to format my 160hdd so win7 can be put on it. its just how will i select between which i want to boot too. I know if i was dual booting off the same hdd it gives you an option but im not sure about this. I really dont want to have to go into the bios everytime to change my boot order so i can get on either one. So if anyone is doing the same thing or knows how to pick between each OS without switching the bios every time. It would be much obliged.  thank you very much in advance :D

---

### Post by mikewhatever on 2010-02-08
After installing W7, boot Ubuntu and run <sudo update-grub> from Terminal. Hopefully, that will detect the newcomer and add it to Grub's menu.

---

### Post by Paqman on 2010-02-08
> **mikewhatever said:**
> After installing W7, boot Ubuntu and run <sudo update-grub> from Terminal. Hopefully, that will detect the newcomer and add it to Grub's menu.

You'll need to [reinstall Grub]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") after installing Windows. Windows isn't very good at detecting other operating systems and bootloaders, and tends to steamroller them during install.

---

### Post by nhasian on 2010-02-08
here's what your looking for:

[https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu](https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu)

---

### Post by mikewhatever on 2010-02-08
> **nhasian said:**
> here's what your looking for:

[https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu](https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu)

Probably a dumb question, why wouldn't Windows boot after its installation? And how would restoring the MBR from before Windows might help booting it?

---

### Post by nhasian on 2010-02-08
if Ubuntu is already installed first, and you install windows after it, the windows NT Loader (the windows boot manager) will overwrite Grub (or grub2 if your using karmic+) and you will no longer have the option to boot back into Ubuntu.  Ubuntu will still be there on the hard disk, but you wont be able to choose to boot to it untill you re-install the Grub bootloader.  did that clear things up?

> **mikewhatever said:**
> Probably a dumb question, why wouldn't Windows boot after its installation? And how would restoring the MBR from before Windows might help booting it?

---

### Post by Extract_Here on 2010-02-08
Im doing this on two separate hdds. the 320gb just has karmic and the 160gb hdd had nothing on it. my plan was to disconnect the 320 inside my comp then leave the empty 160 pluged in so I can install win7 on it. [SIZE=4]Then when I turn my comp off and turn it back on how will I switch from win7 and 9.10 with out having to switch the bios boot order? [/SIZE]

---

### Post by nhasian on 2010-02-08
dont disconnect any drives.  if you do, then the grub bootloader will not detect both operating systems properly and then you WILL have to keep changing the boot order in the bios hehe

---

### Post by Extract_Here on 2010-02-09
ahh see im having to change my boot in the bios now how do i make it not do that?

---

### Post by nhasian on 2010-02-09
leave both drives installed.  boot into ubuntu.  then open a terminal and enter:

```
sudo update-grub
```

grub2 should automatically pick up windows and add it to the menu next time you boot.

---

