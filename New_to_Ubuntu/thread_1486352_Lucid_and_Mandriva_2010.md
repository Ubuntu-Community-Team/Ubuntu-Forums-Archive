---
title: "Lucid and Mandriva 2010?"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by Butthead on 2010-05-17
Okay, I've read all the threads about the trouble with the Grub2 bootloader and various versions of Windows, but how about getting Lucid's Grub2 to load Mandriva 2010 (and it's Legacy Grub)?

I have Lucid Lynx currently installed to SATA HD sda (which is 40 Gig).

And I want to re-install Mandriva PowerPack 2010 to a second SATA HD sdb (which is 160 Gig) and have it boot up correctly afterwards.  

I must have read of 75 different ways of accomplishing this on the Web so far (each one somewhat different), so what's the tried and true method if anyone on the forum here has actually accomplished that? :confused:

I really would appreciate any help.  Messing around with Grub boot menu is one of the things I really don't like doing (usually ends up as a complete re-install for me). :D

(Or maybe :sad: would be more appropriate?).

---

### Post by ubunterooster on 2010-05-17
get lilo via synaptic?

---

### Post by Butthead on 2010-05-18
> **ubunterooster said:**
> get lilo via synaptic?

Would it be easier to configure & get up and running correctly than the Grub2 boot-loader seems to be? :-k

I thought Grub2 was supposed to be an improvement over Legacy-Grub?  Seems it's not such a hot improvement if it isn't backwards compatible? :confused:

---

### Post by -humanaut- on 2010-05-18
Don't use Mandrivia's bootloader use (K)Ubuntu's instead you should have alot less problems.

---

### Post by Butthead on 2010-05-19
> **-humanaut- said:**
> Don't use Mandrivia's bootloader use (K)Ubuntu's instead you should have alot less problems.

I did use Kubuntu's Grub2 bootloader.  That's when I get this error trying to boot Mandriva 2010 (on HD sdb) off it:

Kernel Panic - VFS: Unable to mount root fs on unknown-block (0,0)

Probably something easy to fix, if I wasn't such a Grub dummy.

---

### Post by SwatKat on 2010-05-19
Install Mandriva's bootoader in its root partition while reinstalling Mandriva
Edit 40_custom file of grub2 in Kubuntu and chainload Mandriva and any other os you have
Update-grub
Reboot and make sure the chainload entries work
Disable os prober.

Works for me...
You'll have to go through 2 bootloader menus, but I actually like that.

---

### Post by Butthead on 2010-05-20
Hi SwatKat,

Can you tell me what exactly you added in your Edit 40_custom file?  I saw this guy's page, but when I tried what he suggested, it still didn't work for me.

[http://melpctec.blogspot.com/2009/11/dual-booting-mandriva-2010-with-grub2.html]("http://melpctec.blogspot.com/2009/11/dual-booting-mandriva-2010-with-grub2.html")

On a positive note, if any future releases of Linux you decide to dual-boot on your computer use the Grub2 boot-loader, they should install pretty easily in Lucid.  I have a version of Lucid installed (and booting together nicely) on both HD's in my computer now. :guitar:

---

### Post by SwatKat on 2010-05-21
I have Mandriva on /dev/sda9 of the first hard disk, so I added
menuentry "Mandriva 2010" {
    set root=(hd0,9)
    chainloader +1
}

Yours would have to be something like
menuentry "Mandriva 2010" {
     set root=(hd1,X)
     chainloader +1
 }
hd1 since you are installing on a second hard disk. X is the number of the partition in which you have installed Mandriva on the second disk. The partition counting starts from 1.
And chainloading works only if the Mandriva's bootloader is installed in its root partition. 

Good Luck!

---

### Post by Butthead on 2010-05-21
Hi SwatCat,

Thanks for all the help!

One of the things confusing me is that "fdisk" shows that the Mandriva install lists two Linux partitions on sdb (one located at sdb1 and the other at sdb6).  I assume I load the first (sdb1) one, right (i.e. - (hd1,1)? :confused:

---

### Post by SwatKat on 2010-05-21
Add the one with an * next to it when you fdisk. Its probably the first one.  Then make your 40_custom executable

```
sudo chmod +x /etc/grub.d/40_custom
```
update-grub
Reboot and enjoy Mandriva :).

---

### Post by Butthead on 2010-05-22
Okay, thanks for the help, SwatCat!

Two quick questions though?

What does putting "chainloader +1" on the bottom of the script do?

And why would I have to make my 40_custom file executable before running the update-grub command? :confused:

I do appreciate everyone's help with this though! :guitar:

---

### Post by SwatKat on 2010-05-24
To the best of my knowledge, the command chainloader+1 redirects to bootloader of other operating systems . In this case it directs grub2 to boot Mandriva's legacy grub. That is why its important to have Legacy grub installed in Mandriva's root partition specified by the argument (hdx,y) which is the boot block in that partition. ie, when you say

set root=(hd1,X)
     chainloader +1

you are redirecting grub2 to a bootloader in (hd1,x) and then that bootloader shows and you choose what to boot from there. That is also the reason you have to go through 2 bootloader menus. When you chainload, you first get the grub2 menu and on selecting Mandriva you get the mandriva's grub menu. 

 As for making 40_custom executable , its explained in the grub2 basics thread here
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
I took the liberty to copy and paste a portion of it 

```

[LIST]
[*]/etc/grub.d/
[LIST]
[*]The  files in this folder are read during execution of "update-grub"  or "update-grub" commands. The  contents are imported into /boot/grub/grub.cfg

The order of the entries in the grub menu is based on the order of the  file names. File named with a starting numeral are run before those  beginning with a letter. The order the files are run determines the menu  order in grub.cfg.
Custom entries can be added to the "40_custom"  file or in a newly created file. 
 [B]
Any file created must be executable in order to be included in the grub.cfg file during the "update-grub"  command[/B].
[LIST]
[*]00_header
[*]05_debian_theme:  Set background and  text colors, themes
[*]10_hurd  Locates Hurd kernels
[*]10_linux  Locates Linux kernels based  on results of the "lsb_release" command.
[*]20_memtest86+:  If the file  /boot/memtest86+.bin exists, it is included as a menu item.
[*]30_os-prober:  Searches for Linux and  OS's on other partitions and includes them in the menu.
[*]40_custom: A template for adding custom  menu entries which will be inserted into grub.cfg  upon execution of the "update-grub"  command. This and any other custom file must be made executable to allow  importation into grub.cfg.
[/LIST]
 
[/LIST]
 
[/LIST]
 

```I hope this answers your questions. I dont claim to be an expert in any of these topics, so anyone feel free to correct me if I am wrong.

@Butthead, so you can see that you are just adding entries to the grub2 menu by making 40_custom executable. Your grub2 will look the same with a few added entries. Even if your custom entries dont work ( which is highly unlikely since chainloading works like a charm) you can always boot as usual into ubuntu. So go ahead and feel free to experiment with 40_custom. You are not doing anything damaging :).

---

### Post by Butthead on 2010-05-24
Hi SwatCat,

Okay, thanks for the explanation! :guitar:

The reason I thought I'd ask is that Mel (that guy who wrote original article on the Web on how to get Lucid and Mandriva working together installed on two different HD's under Grub2) sent me a script that works great for me, I don't have to make it executable first, and Mandriva shows up as a choice in the Grub2 boot menu (no double boot menus show up for me).

I put this little script he gave me at the end of my 40_custom file:

echo "Adding Mandriva2010-test on
sdb1" >&2

cat << EOF

menuentry "Mandriva" {
linux (hd1,1)/boot/vmlinuz

initrd (hd1,1)/boot/initrd.img
}
EOF 

Run "sudo grub-install" in the terminal, and at the next boot-up, Mandriva automagically appears in the Grub2 boot loader. =D>

The really strange thing is that I tried a similar script before, and it didn't work for me. :confused:

Must have been some special snippet of code he added to this new script that did it.

I'd be tempted to try yours out, but since it's working so well for me now...:-\" 

Anyway, thank you again for your assistance.  I really do appreciate you helping me out!

---

