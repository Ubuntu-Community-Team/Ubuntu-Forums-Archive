---
title: "Chain Booting Error using GRUB"
date: 2011-05-13
forum: New to Ubuntu
---

### Post by sual0001 on 2011-05-13
Hi all,

I intent to have a boot partition installed with GRUB Legency for chain booting of windows 7, 11.04 Ubuntu Desktop and 11.04 Ubuntu Server.

I found this [guide]("http://ubuntuguide.org/wiki/Lucid_Multiple_OS_Installation") online and followed it.

Drive was partition according to the guide with:
/dev/sda0: Windows7
/dev/sda3: Grub Boot partition
/dev/sda5: 11.04 Ubuntu Desktop
/dev/sda6: 11.04 Ubuntu Server

Next,windows 7 OS is installed.

Next, 11.04 Ubuntu Desktop was installed.

However i was stuck at the [Reinstall Grub to MBR ]("http://ubuntuguide.org/wiki/Lucid_Multiple_OS_Installation#Reinstall_Grub_to_MBR") step.
Below is what the terminal displayed.

[I]grub> find /boot/grub/stage1
find /boot/grub/stage1

Error 15: File not found[/I]

How can i troubleshoot this error for this step?

---

### Post by jtarin on 2011-05-13
11.04 does not use Legacy Grub....it uses Grub 2.......[go here.]("http://ubuntuforums.org/showthread.php?t=1195275")
You have "/dev/sda3: Grub Boot partition" marked but you want to install Grub to MBR....why?

---

### Post by QLee on 2011-05-13
[QUOTE=sual0001]
I intent to have a boot partition installed with GRUB Legency for chain booting of windows 7, 11.04 Ubuntu Desktop and 11.04 Ubuntu Server.

I found this [guide]("http://ubuntuguide.org/wiki/Lucid_Multiple_OS_Installation") online and followed it.
...
However i was stuck at the [Reinstall Grub to MBR ]("http://ubuntuguide.org/wiki/Lucid_Multiple_OS_Installation#Reinstall_Grub_to_MBR") step.
Below is what the terminal displayed.[/QUOTE]

Did you follow all the steps above that section and did it seem to go OK with no errors? As jtarin states, Natty uses grub-pc by default, did you follow the uninstall and install legacy GRUB and copy the files necessary to your boot partition?

[QUOTE=sual0001][I]grub> find /boot/grub/stage1
find /boot/grub/stage1

Error 15: File not found[/I]

How can i troubleshoot this error for this step?[/QUOTE]

Well, if you followed the guide correctly that command should have found two instances of the file. You could mount the boot partition and look for the files with a browser. If it was my system (and I chose to stick with legacy) I would follow the step-by-step on the site for, Remove Grub 2 and install Grub Legacy through again to see if everything was done correctly.

On the other hand, it is probably a good time in history to consider using GRUB2 (grub-pc) and that is what I recommend. Neither of your Ubuntu installs is from the era of legacy GRUB and if you spend a bit of time learning GRUB2, I expect you could accomplish your booting goals with modern software.

---

### Post by jrev on 2011-05-13
Otherwise you can execute the bootinfo script that will tell you all about grub situation.
You can start your system with the super_grub_disk2 and pass the following commands :
sudo grub-install /dev/sdx (x = a, b ou c) according to the place you need grub2 to be installed 
 then sudo update-grub to take into account the eventual other OS :P

---

### Post by QLee on 2011-05-13
> **jrev said:**
> Otherwise you can execute the bootinfo script that will tell you all about grub situation.
You can start your system with the super_grub_disk2 and pass the following commands :
sudo grub-install /dev/sdx (x = a, b ou c) according to the place you need grub2 to be installed 
 then sudo update-grub to take into account the eventual other OS :P

You should re-read the thread, sual0001 isn't trying to install GRUB2.

---

### Post by oldfred on 2011-05-13
You still should run boot info script. Anyone with multiple installs or multiple drives needs to know and at least start to understand the output from the script. It really helps to know what is installed where and documents lots of details in case you need them. 

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply, Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

And if using Natty the next version of the script tells more:
Get last development version of Boot Info Script:
```
wget -O boot_info_script.sh 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh;hb=HEAD'

```I still have a small grub legacy grub only partition but have few things it chains to anymore. I do have multiple drives and chain from one MBR to another but with grub2. A grub only partition requires lots of manual updates and good understanding of what is where.

Grub2's os-prober auto finds other installs really well and if primarily booting an install with grub2, I think it best to use grub2. You can just add chain entries it you want in 40_custom.

Grub2 does not like to be installed to a partition boot sector (PBR) as that is less reliable as it has to use block lists or hard coded addresses which may change on an update or fsck and force a reinstall of grub2 to make it work again.

---

### Post by Jose Catre-Vandis on 2011-05-13
If you can start again, it is really just easier to:

Do your partitioning
Install W7
Install Desktop (grub2 to MBR) - will pick up W7
Install Server (grub2 to /dev/sd* where server is installed)

Add a menu entry in 40_custom to chainload Server  - e.g.

```

menuentry "Server" {
        insmod ext2
        set root=(hd0,*)
        multiboot /boot/grub/core.img
}
```

which will redirect you to the Server grub

---

