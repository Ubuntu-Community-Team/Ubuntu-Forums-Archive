---
title: "filesystem error"
date: 2011-07-17
forum: New to Ubuntu
---

### Post by jimmybenny on 2011-07-17
I'm very new to Linux and its shown me how very little I know about computers, tho I still enjoy it very much. I've been using lucid for a few months and wanted to try 11.04 so I installed it on a new partition. After I did so I decided I didn't like it and want to remove it. So instead of doing the research and uninstalling it properly I just deleted the partition. So now upon reboot all I get is the "error: unknown filesystem. Grub rescue >" screen. Can anyone help me fix this issue?

---

### Post by jimmybenny on 2011-07-17
Ok, so in an effort to right my wrong I reinstalled 11.04 and now my system is back to normal. Now can anyone tell me how to properly uninstall 11.04 and how to remove the partition so that lucid has my whole hard drive again? And also I have 3 swap spaces on the drive, what are those?

---

### Post by Mark Phelps on 2011-07-17
When you installed Ubuntu to its own partition, you overwrote the Master Boot Record (MBR) of the drive. So now, it will always try to run GRUB, even AFTER you remove Ubuntu.

Do you have an MS Windows disk that you can use to restore the MBR?

---

### Post by oldos2er on 2011-07-17
Are you using grub2 on Lucid? If you boot into Lucid, and run **sudo grub-install /dev/sda** (assuming Lucid is on sda), reboot, and if everything's working properly, you should be able to safely delete 11.04. 

Your problem was caused by the fact that only part of grub2 is stored in the MBR, all the info it needs to boot is stored in /boot/grub/, /etc/grub.d/, and /etc/default/grub. When you deleted the partition, this info was lost. See [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

You should only need one swap partition. [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by amjjawad on 2011-07-17
> **jimmybenny said:**
> Ok, so in an effort to right my wrong I reinstalled 11.04 and now my system is back to normal. Now can anyone tell me how to properly uninstall 11.04 and how to remove the partition so that lucid has my whole hard drive again? And also I have 3 swap spaces on the drive, what are those?

Hello and Welcome :)

You did not provide more details but I'll try to explain in general and hope that would be the same as your case.

You first had Ubuntu 10.04 installed. Assuming it was the ONLY OS installed in your machine, then [**GRUB2**]("http://www.google.com/url?sa=t&source=web&cd=2&ved=0CCgQFjAB&url=https%3A%2F%2Fhelp.ubuntu.com%2Fcommunity%2FGrub2&rct=j&q=grub2&ei=4gEjToeRHc2D-waV4_nNAw&usg=AFQjCNFtwBF0yjuAud1Xx-Ol-8PUzYwRXw&sig2=ehKKr6nbRUfCOahOIugfUQ&cad=rja"), the boot loader of Ubuntu 10.04 is installed in the [**MBR**]("http://en.wikipedia.org/wiki/Master_boot_record") of your HDD.

After installing any other OS, whether it's Windows or Linux, the user needs here to decide **"where to install the boot loader of the new/other OS".**
Most of users don't pay much attention to this step and just install the boot loader of the new OS to the MBR of the HDD. That will definitely overwrite the MBR, hence any information stored there will be overwritten. 

If that what happened in your case then the boot loader of Ubuntu 11.04, which is still GRUB2, has overwritten your MBR. When you removed/uninstalled/formatted Ubuntu 11.04, the root partition got removed, hence most of GRUB files got lost. That explains why you were unable to boot your machine.

In that case, [Re-installing GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2") is what you need.

How to avoid Re-installing GRUB2?

Whenever you install another OS, make sure NOT to install the boot loader to the MBR, but instead, install the boot loader of the 2nd OS into the same root partition. For example, if you're installing Ubuntu 11.04 into sda5 then make sure you install the boot loader in sda5 NOT sda. You can do that during the installation, I guess step #4.

After the installation is done, reboot and login to Ubuntu 10.04 which is the first OS you installed. From Terminal, run this command:

```
sudo update-grub

```

And you are good to go.

ALL the above is NOT hard to understand but you need some basic knowledge and you need to understand what is going on ;)

Good luck!

---

### Post by Zill on 2011-07-17
> **jimmybenny said:**
> ...I've been using lucid for a few months and wanted to try 11.04 so I installed it on a new partition...
You may like to know that you don't need to actually *install* Ubuntu (and most other Linux distros) in order to try it out!

Most Linux CDs (including Ubuntu) are "live" CDs, which means you can run them *without* installing to your hard drive.  This option is usually present when you boot from the CD.  You can then try out the distro and verify it works with your hardware and that you like the way it works.  Everything will load more slowly than when installed to the HDD but it will give you a good feel for the distro.  If you like the distro there is usually an install option on the desktop.  If not just shutdown, remove the CD and boot to your original hard drive OS.

---

### Post by jimmybenny on 2011-07-17
I REALLY appreciate all the help. I'll let you know how I make out. Cheers

---

### Post by amjjawad on 2011-07-18
> **jimmybenny said:**
> I REALLY appreciate all the help. I'll let you know how I make out. Cheers

Waiting for your feedback :)

---

