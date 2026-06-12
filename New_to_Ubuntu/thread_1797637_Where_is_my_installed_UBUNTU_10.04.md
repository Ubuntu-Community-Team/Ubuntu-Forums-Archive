---
title: "Where is my installed UBUNTU 10.04"
date: 2011-07-05
forum: New to Ubuntu
---

### Post by Eastwood1 on 2011-07-05
I installed Ubuntu 10.04 LTS onto a External HD 320 G. Took some time. Choice was made for me by live CD. In the end it ordered a restart. Windows 7 came up. I am sure Ubuntu is somewhere but do not know how to look for it. Please help. (LTS Life's to Short:()

---

### Post by abybaddi on 2011-07-05
You've to enable booting from external HDD. And check whether boot flag is on.

To select boot device either change your bios settings or tap F8 after POST and then select USB-HDD.

---

### Post by Mark Phelps on 2011-07-05
Linux OS's don't care about the boot flag...

But, you need to ensure that you installed GRUB to the external drive, and you DO need to then boot from that drive.

Don't make the mistake of installing GRUB to your internal drive. Doing that will risk corrupting Win7 and rendering it unbootable.

---

### Post by Eastwood1 on 2011-07-05
> **Mark Phelps said:**
> Linux OS's don't care about the boot flag...
 
But, you need to ensure that you installed GRUB to the external drive, and you DO need to then boot from that drive.
 
Don't make the mistake of installing GRUB to your internal drive. Doing that will risk corrupting Win7 and rendering it unbootable.
 
I am a novice so please bare with me. What happens when I want to use Win 7 again. Swambo- (She who always must be obeyed) is still hooked on Win 7?:)

---

### Post by vivek.pandey on 2011-07-05
you directly go to windows means your grub is not installed .. try installing
you need a live cd though

---

### Post by seawolf167 on 2011-07-05
> **Eastwood1 said:**
> I am a novice so please bare with me. What happens when I want to use Win 7 again. Swambo- (She who always must be obeyed) is still hooked on Win 7?:)

Windows will still work - what you are doing is installing GRUB in the MBR, then it points to the Windows 7 loader in the Windows partition boot record. You have to make sure that you select to install to the external drive or it could overwrite the Windows loader and you will have to use a Windows rescue disk to restore it and be able to boot to Windows.

---

### Post by tgm4883 on 2011-07-05
> **vivek.pandey said:**
> you directly go to windows means your grub is not installed .. try installing
you need a live cd though

That is not entirely true. It is likely installed, but not to the drive he is booting from.

---

### Post by vivek.pandey on 2011-07-05
> **tgm4883 said:**
> That is not entirely true. It is likely installed, but not to the drive he is booting from.

thanx for your correction .. i indeed didnt know this.. it wil be interesting if this is the exact problem and he gets to fix it with a live cd...

---

### Post by abybaddi on 2011-07-06
Connect the HDD before starting your PC.
> **abybaddi said:**
> 
Tap F8 after POST and then select USB-HDD.


> **Eastwood1 said:**
> I am a novice so please bare with me. What happens when I want to use Win 7 again. Swambo- (She who always must be obeyed) is still hooked on Win 7?:)

Just disconnect the HDD before starting the PC to go back to windows7.

---

### Post by Eastwood1 on 2011-07-06
> **tgm4883 said:**
> That is not entirely true. It is likely installed, but not to the drive he is booting from.
 I used the live CD for installation. What is GRUB. The external HDD is 320 G and Internal is 1Tbyte. Do I now 'overinstall' because Ubuntu is not there to uninstall. Use the live CD for uninstall????

---

### Post by oldfred on 2011-07-06
This will tell us what is installed where. Use liveCD and download script and run it:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by tgm4883 on 2011-07-06
> **Eastwood1 said:**
> I used the live CD for installation. What is GRUB. The external HDD is 320 G and Internal is 1Tbyte. Do I now 'overinstall' because Ubuntu is not there to uninstall. Use the live CD for uninstall????

Do as the previous posters have suggested. When booting you need to select the USB drive to boot from.

---

