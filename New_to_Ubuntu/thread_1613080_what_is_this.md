---
title: "what is this???"
date: 2010-11-04
forum: New to Ubuntu
---

### Post by jamesidw on 2010-11-04
I don't know wat I did but this pc wont start properly. I get a black screen with the following text repeating itself, 
" [drm:intel_fb restore] *ERROR* failed to restore crtc configuration"
does anybody know how to fix this?

---

### Post by wilee-nilee on 2010-11-04
Since you have been so careful to give a good description I suggest a sledge hammer.;)

---

### Post by jamesidw on 2010-11-04
Ha ha...that option is out! I'm trying to fix broken packages from the recovery console, any other suggestions that don't involve sledgehammers?

---

### Post by Clever_Username on 2010-11-04
You might find [this]("http://ubuntuforums.org/showpost.php?p=9932369&postcount=5") link useful

---

### Post by wilee-nilee on 2010-11-04
> **jamesidw said:**
> Ha ha...that option is out! I'm trying to fix broken packages from the recovery console, any other suggestions that don't involve sledgehammers?

Are you installed via wubi?

---

### Post by linux18 on 2010-11-04
it's not easy but this shell sledgehammer could work ctrl+alt+f1 to get to shell, but if you cant; reinstall and salvage the home dir via live cd :

rm -vrf $HOME/.config
sudo rm -vrf /root/*
sudo dpkg-reconfigure -a
sudo apt-get update
sudo aptitude -f install

---

### Post by jamesidw on 2010-11-04
I am not installed via wubi...I just had no idea wat a sledgehammer was:confused: so i figured wilie-nilie was referring to "hulk smash". I stand educated.
Since i can get to the root shell wat do i do next?

---

### Post by wilee-nilee on 2010-11-04
> **jamesidw said:**
> I am not installed via wubi...I just had no idea wat a sledgehammer was:confused: so i figured wilie-nilie was referring to "hulk smash". I stand educated.
Since i can get to the root shell wat do i do next?

Actually I jokingly meant that. Before we get to far into tweaking boot a live Ubuntu cd and run the bootscript that is linked in my signature. Post the text from the generated file from running the script. Post it in code tags by clicking on the # in the reply panel, you will see this [code] [ /code] put the text between.

---

### Post by linux18 on 2010-11-04
follow the commands I listed in my above post and be careful there is a "sudo rm" in there

---

### Post by jamesidw on 2010-11-04
uh... I run the commands you gave me as root so I omitted the sudo, could that be why it still gives me the same black screen? I did not think it would. Also, alot of things went wrong with the "apt-get update" because it could not access any of the repositories! i'm checking my connection via the command line using "ping google.com" 
thanx keep it coming

---

### Post by wojox on 2010-11-04
> **jamesidw said:**
> I don't know wat I did but this pc wont start properly. I get a black screen with the following text repeating itself, 
" [drm:intel_fb restore] *ERROR* failed to restore crtc configuration"
does anybody know how to fix this?

Your kernel is messed up. Do you have another to boot into?

---

### Post by jamesidw on 2010-11-04
Besides using another pc to access this forum, I've got zip! I have a boot cd but I have no idea how to fix the problem without reinstalling

---

### Post by jamesidw on 2010-11-04
O.k so I tried to download the boot_info_script but for some reason the download won't start:mad: and after reading about it I REALLY want it. I also fixed the failed repositories issue, turned out I forgot to use a root shell with networking. But even then when I run the commands that you gave me I still come out with the same result.

---

### Post by linux18 on 2010-11-04
are you using an ethernet cable, if so ' dhclient eth0 ' will get networking working.

---

### Post by mastablasta on 2010-11-04
> **jamesidw said:**
> Besides using another pc to access this forum, I've got zip! I have a boot cd but I have no idea how to fix the problem without reinstalling
 
 
He is refering to another kernel. Linux leaves a few old kernel on your disk in case something goes wrong during update or kernel so you can reverse to old kernel.
 
i don't know how to access it (sicne i have dual boot and this is done automatically) i think you need to hold shift upon boot to get to GRUB menu and then select older kernel there and press enter to start with older kernel.
 
or this:
[http://www.easy-ubuntu-linux.com/grub-menu-visible.html](http://www.easy-ubuntu-linux.com/grub-menu-visible.html)

---

### Post by jamesidw on 2010-11-04
Going offline now...will try again when another pc with net is available.

---

