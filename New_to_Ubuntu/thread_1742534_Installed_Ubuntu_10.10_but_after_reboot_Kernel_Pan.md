---
title: "Installed Ubuntu 10.10 but after reboot Kernel Panic, Not Syncing"
date: 2011-04-28
forum: New to Ubuntu
---

### Post by 645dood on 2011-04-28
Hi, I have Win7 64bit dualbooted with Ubuntu 10.10 64bit (Win7 first). Went through the installing process of Installing Ubuntu 10.10, everything went OK no errors at this stage and when prompted to reboot I did so. I went though Grub to get into Ubuntu but could not I got the error message "Kernel Panic, Not Syncing". As I am a noob can anyone advise how I can fix this. I apologies in advance if this has already been discussed if so can anyone point me in the right direction. Thanks, 645dood.

---

### Post by jtarin on 2011-04-29
Grub2 is not able to locate your kernel. Did you change the boot order in the bios to install Ubuntu? If yes go back and change it to have the device where Ubuntu is boot first.

---

### Post by 645dood on 2011-04-29
Hi, Apologies for not understanding, I do have the Bios to boot from the CD first then to the HDD, When I get to grub on the fist line is Kernal 2.3.35.31 (I enter here when I get the stuff up) second line is the same with recovery mode and I believe the last entery is Win 7. Let me knwo if this is OK, thanks again 645dood.

---

### Post by begage1 on 2011-04-29
I had the exact same problem with 10.10.  I downloaded version 10.04 lts instead and it worked fine.
If you go to [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) you can get the download and then burn the ISO image to a CD.  If you've never done that the instructions are on that page as well.  Version 11.04 was also just released but I haven't tried it yet.  I know 10.04 worked out for me.  Good luck!

---

### Post by 645dood on 2011-04-29
[URL="http://ubuntuforums.org/member.php?u=1289813"]Hi begage1, [COLOR=Black]Can I simply overwright 10.10 or do I need to do a fresh install. I am concerned it will wipe out my Win 7 entery at Grub. Thanks, 645dood.[/COLOR]
[/URL]

---

### Post by 645dood on 2011-04-29
Hi, Can someone please help me resolve this, Thank You, 645dood

---

### Post by 645dood on 2011-04-29
JTarin, No I did not change the boot order at all I went into to bios to see if I can but I see no where to do so. I have Win7 and Mint 10 booted on my 4 year old Dell laptop with no problems what so ever. Any advice regarding the Kernal Panic error is greatly appreciated, 645dood.

---

### Post by jtarin on 2011-04-29
> **645dood said:**
> JTarin, No I did not change the boot order at all I went into to bios to see if I can but I see no where to do so. I have Win7 and Mint 10 booted on my 4 year old Dell laptop with no problems what so ever. Any advice regarding the Kernal Panic error is greatly appreciated, 645dood.
Do you have a Live CD? You need to boot with it and reinstall Grub, might be a place to start.

---

### Post by 645dood on 2011-04-29
Jtarin, Thank you, I have just upgrades to 11.04 from the live cd which seems to have fixed the Kernal Panic, Not syncing problem. Thank you to all who have helped me, this forum is absolutely a must for the Ubuntu user, 645dood

---

### Post by begage1 on 2011-04-29
You should still be able to keep Win7.  It will ask you as you go through the install process.  10.04 should also install over 10.10 without losing you Win7.

---

