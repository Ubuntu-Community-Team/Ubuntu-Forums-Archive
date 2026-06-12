---
title: "Cant boot ubuntu 11.4 from flash drive"
date: 2011-06-10
forum: New to Ubuntu
---

### Post by DitVit on 2011-06-10
i have went into BIOS and put the first boot order as removable disk and saved the changes, but when i restart my computer, my originial OS, windows xp, starts up like normal. i placed the same flash drive into another computer, also using windows xp, and was successfully able to boot ubuntu friom the flash drive. The computer that wasnt able to boot ubuntu recognizes the flash drive but for some reason cant boot from it. . thanks for reading ^^

---

### Post by jtarin on 2011-06-10
Upon starting your computer do you have the F11 option of choosing boot devices?

---

### Post by DitVit on 2011-06-10
i have tried that. i clicked removable discs and then picked my flash drive( it was only one in selection screen). after that, it just simply starts up windows  xp.normally. can this maybe be a virus? this computer that i want to instill ubuntu b4 was unusable until i system restored it which probably didnt remove all the viruses. :(

---

### Post by jtarin on 2011-06-10
> **DitVit said:**
> i have tried that. i clicked removable discs and then picked my flash drive( it was only one in selection screen). after that, it just simply starts up windows  xp.normally. can this maybe be a virus? this computer that i want to instill ubuntu b4 was unusable until i system restored it which probably didnt remove all the viruses. :(OK you USB flash is not set up properly. Format it as FAT 32 then reinstall Ubuntu to it. Where did you get the directions for installing to USB?

---

### Post by DitVit on 2011-06-10
i got my instructions from the ubuntu website. however, i clicked the the download and install option instead of the try it from usb and cd option. i am not tech savy at all so i am clueless to how to format my usb as FAT 32. if you dont mind to show me how. thanks a lot i really appreciate ur help :)
 
im guessing if i follow the try it from usb and cd option on the ubuntu website it will show me how to formate the usb? :S ok nvm, i just cheked, pretty much the same steps. do u mind showing me how to format my usb? :P

---

### Post by jtarin on 2011-06-10
Go [here]("http://www.softpedia.com/get/System/Hard-Disk-Utils/HP-USB-Disk-Storage-Format-Tool.shtml") and download the HP USB Disk Storage Format Tool to your Windows desktop and install and run. It is the best way to accomplish this.

---

### Post by Joe of loath on 2011-06-10
If the USB stick worked on another PC, how can it not be formatted properly?

OP, how old is the PC that doesn't work?

---

### Post by jtarin on 2011-06-10
> **Joe of loath said:**
> If the USB stick worked on another PC, how can it not be formatted properly?

OP, how old is the PC that doesn't work?Whoops that one went right by me.....sorry OP.:oops:

---

### Post by peperomia on 2011-06-10
I'm with, Joe of loath - if the other computer booted fine off the  flash drive, then it's clearly not a problem making the flash drive bootable. [The  age of the BIOS or the flash drive could definitely be a problem]("http://www.damnsmalllinux.org/wiki/index.php/USB_Booting#BIOS_Limitations"), though.

---

### Post by beew on 2011-06-10
It has to do with the BIOS rather than the flash drive. My laptop is like that too, even though I have set the BIOS' boot sequence to usb device first it still stubbornly boots into the internal drive and it doesn't matter what OS is installed. It was like that before with Win and now it is the same with Ubuntu. 

In order to boot off an external drive or a flash drive I have to press esc to get the one time boot menu to choose the usb, in other computers the key to bring up the one time boot menu may be F10, F11 or something like, there should be a message on the screen to tell you that when you boot. 

With my computer even that sometimes doesn't work and I have to get into the one time boot menu twice.

BTW,  my laptop is 1.5 years old only and it is quite good on everything else. Ubuntu rocks on it. :)

On the other hand I have a 6 year old hand me down crappy laptop , I can boot into usb with no problem.

---

### Post by jtarin on 2011-06-10
> **beew said:**
> It has to do with the BIOS rather than the flash drive. My laptop is like that too, even though I have set the BIOS' boot sequence to usb device first it still stubbornly boots into the internal drive and it doesn't matter what OS is installed. It was like that before with Win and now it is the same with Ubuntu. 

In order to boot off an external drive or a flash drive I have to press esc to get the one time boot menu to choose the usb, in other computers the key to bring up the one time boot menu may be F10, F11 or something like, there should be a message on the screen to tell you that when you boot. 

With my computer even that sometimes doesn't work and I have to get into the one time boot menu twice.

BTW,  my laptop is 1.5 years old only and it is quite good on everything else. Ubuntu rocks on it. :)

On the other hand I have a 6 year old hand me down crappy laptop , I can boot into usb with no problem.I suggested the F11 on post #2

---

### Post by DitVit on 2011-06-10
this comp is like 5 years old  :( but ther other computer that is able to boot from the flash drive is 6uyrs old. gahhhhh i hope someone will have a solution to this >:(. 
i dont know if this helps but when i formated the usb drve to FAT32, the computer no longer recognized the flash drive to be a bootable device when i go into the boot menu. Before, when i did not format that usb drive to FAT32 the computer recognized that the flashdrive was a bootable device in the boot menu but when i click it to boot,, windows xp(the OS that is currently on the comp) just starts up liek normal.

---

### Post by peperomia on 2011-06-11
Are you absolutely sure you're moving the correct device to the top of the boot list? [This user]("http://superuser.com/questions/113151/ubuntu-wont-boot-from-usb-memory-stick") found that "Removable Dev" in the boot list wasn't actually his USB memory stick. S/he had to go into the Hard Drives menu and move the USB there to the top of the list.

---

### Post by VOT Productions on 2011-06-11
Go into the full BIOS (DEL, F2, F12, etc) then search for Boot Order and choose USB-HDD/Your device, etc, whichever is there, and reboot.

---

### Post by jtarin on 2011-06-11
> **DitVit said:**
> 
i dont know if this helps but when i formated the usb drve to FAT32, the computer no longer recognized the flash drive to be a bootable device when i go into the boot menu. Before, when i did not format that usb drive to FAT32 the computer recognized that the flashdrive was a bootable device in the boot menu but when i click it to boot,, windows xp(the OS that is currently on the comp) just starts up liek normal.No that doesn't actually help as you told me by private message that it would boot and you did get an Ubuntu desktop, but the booting was intermittent....not dependent on the USB flash.You told me it was mostly due to you choosing the wrong boot device and once even wiping the Ubuntu install accidentally off the USB.

---

