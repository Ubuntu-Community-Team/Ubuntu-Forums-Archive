---
title: "Why are there additional Instances of Ubuntu after Updating"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by VolStan on 2008-12-02
I partitioned a drive with 1 primary (NTFS) partition, 1 primary (ext3) partition and an extended partition.  I installed Windows XP Pro on the NTFS partition and Ubuntu 8.04 on the ext3 partition.  I had no problems during this process.  When I booted up the computer afterwards, I was presented with the Ubuntu load, its recovery mode, its memtest, etc and the Windows XP.  Still no problems.  Once I booted into Ubuntu, I was notified that there were updates to download and install.  I confirmed the action, and the Update Manager performed the downloads and installations without a hitch.  Then it said it needed to be restarted, so I did so.  

Upon restarting the computer, there was an additional instance of Ubuntu and its corresponding recovery mode listed among the boot up choices.  What?  Why?

Since then I have installed another set of updates and there is a third instance of Ubuntu and its corresponding recovery mode.  Why is this?  

I have more updates now that need to be downloaded and installed, but I really don't care to have any more instances of Ubuntu in my list.  All I really need is the single instance of Ubuntu, its recovery mode, etc and Windows XP.  How do/Can I edit this list? Is there some way I can make it where it does not continue to do this?

I am completely new to Ubuntu.  I have only on rare occasions perused other Linux installs.

BTW, each of these instances appear to boot up the same Ubuntu install. (As opposed to having multiple installs.)  Any changes I make to Ubuntu is still there regardless which of these "instances" I click on.  I just need to get rid of the older ones AND make it where it will not continue to show any others except the latest one... and XP, of course.

---

### Post by Diabolis on 2008-12-02
You get one of those entries every time that your kernel is updated. Each option is a different installation. Seems like all of them are the same because changes from kernel to kernel are not dramatic or not noticeable for the average user.

You can remove the extra kernels with:
```
sudo apt-get autoremove
```

And then remove their entries by deleting them in this file:
```
sudo gedit /boot/grub/menu.lst
```

---

### Post by laffinet on 2008-12-02
These additional instances get created every time there is an update to the kernel. I guess the idea is that you have the possibility to load the old kernel should something not work with the new one.

You can remove the additional entries by editing the file /etc/boot/grub/menu.lst

Edit: diabolis beat me to it...

---

### Post by VolStan on 2008-12-02
> **Diabolis said:**
> You get one of those entries every time that your kernel is updated. Each option is a different installation. Seems like all of them are the same because changes from kernel to kernel are not dramatic or not noticeable for the average user.

You can remove the extra kernels with:
```
sudo apt-get autoremove
```

And then remove their entries by deleting them in this file:
```
sudo gedit /boot/grub/menu.lst
```

**Thanks.  Remember, I'm a novice to this.  So do I open a terminal to enter the above code to remove the extra kernels?**

---

### Post by Diabolis on 2008-12-02
You execute this in a terminal:
```
sudo apt-get autoremove
```

It actually removes all the packages that you don't need anymore, but since the extra kernels are not needed by the system, they will be removed too.

You execute this in a terminal too. The command sudo is used in the beginning so the following command will be executed as root. You have to do it like that because you are modifying a file that doesn't belong to you. The owner of all the files outside your home folder is root. The word in bold is the text editor that you want to use to open the file *menu.lst*.
```
sudo **gedit** /boot/grub/menu.lst
```
An "equivalent" to this, would be sudo notepad /boot/grub/menu.lst

---

### Post by Simplicius on 2008-12-02
You may want to keep the last working kernel, so that if you are having problems with the new kernel you still can use the old one.

---

### Post by doas777 on 2008-12-02
yep. command line instructions are a lot less cumbersome for online support (and many computery folks are ... well... computery). it works (or doesn't) the same way for everyone, whereas everyones desktop is differant.

you can copy and paste in your terminal with 'ctrl + shift + c' and 'ctrl + shift + v' or just right click.

the second command is asking you to open a file that contains configuration information for grub.  before you do that, first run this to back up your file (to menu.lst.bak):
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak

```

now open the file as described, and start scrolling down.
keep going until everyline doesn't have a '#' sign at the beginning ('#' is a comment mark, and essentially disables the line). 

your looking for somthing like this:
```

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		ab704f5d-3040-417d-8077-25f8c72187b4
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=ab704f5d-3040-417d-8077-25f8c72187b4 ro splash vga=789 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		ab704f5d-3040-417d-8077-25f8c72187b4
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=ab704f5d-3040-417d-8077-25f8c72187b4 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		ab704f5d-3040-417d-8077-25f8c72187b4
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ab704f5d-3040-417d-8077-25f8c72187b4 ro splash vga=789 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		ab704f5d-3040-417d-8077-25f8c72187b4
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ab704f5d-3040-417d-8077-25f8c72187b4 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		ab704f5d-3040-417d-8077-25f8c72187b4
kernel		/boot/memtest86+.bin
quiet

```

If I wanted to, I could remove an old kernel from my grub menu, by deleting the block for that kernel. I want to keep a recovery mode option and memtest so i won't touch those. I'll delete the blocks for 2.6.27-7-generic from the middle.

heres my file now:
```

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		ab704f5d-3040-417d-8077-25f8c72187b4
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=ab704f5d-3040-417d-8077-25f8c72187b4 ro splash vga=789 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		ab704f5d-3040-417d-8077-25f8c72187b4
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=ab704f5d-3040-417d-8077-25f8c72187b4 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, memtest86+
uuid		ab704f5d-3040-417d-8077-25f8c72187b4
kernel		/boot/memtest86+.bin
quiet

```

so now i have 3 entries, normal boot, recovery mode (for latest kernel) and memtest.

just save your file and reboot.

have fun,
franklin

---

### Post by kansasnoob on 2008-12-02
I like to use Startup-Manager:

[http://www.psychocats.net/ubuntu/startupmanager](http://www.psychocats.net/ubuntu/startupmanager)

In the following screenshot you can see that you can limit the number of kernels to display:

[ATTACH]95064[/ATTACH]

But whenever there is a kernel update I temporarily change that to 2 just in case the new kernel doesn't work for me.

---

### Post by procharged on 2008-12-02
ok im new as well (just installed ubuntu last night) and have everything working well but am having this same thing after updating. im gonna go ahead and do what you said but, which kernal do i delete-is the newer one on the top or bottom. proabaly a dumb question but thanks in advance.

---

### Post by oldos2er on 2008-12-02
Since gedit is a graphical program, please use "gksu" in place of sudo to call it:

gksu gedit /etc/apt/sources.list.

 Also, you can use Synaptic Package Manager to uninstall old kernels; it will update grub for you.

---

### Post by doas777 on 2008-12-02
the highest version number (2.6.27.xx) is the latest one. the newest is almost always the top one. just leave it alone.

Kansasnoob makes a great point about [Startup-manager]("http://www.ubuntugeek.com/startup-manager-change-settings-in-grub-grub2-and-usplash.html"). it may be the best tool for ya.

good luck,
franklin

---

### Post by Diabolis on 2008-12-02
You can tell which kernel is older by their release numbers:
Newer -> Ubuntu 8.10, kernel 2.6.27-9-generic
         Ubuntu 8.10, kernel 2.6.27-7-generic

The new kernel is always added at the top of the list.

---

### Post by doas777 on 2008-12-02
> **oldos2er said:**
> Since gedit is a graphical program, please use "gksu" in place of sudo to call it:

gksu gedit /etc/apt/sources.list.

 Also, you can use Synaptic Package Manager to uninstall old kernels; it will update grub for you.

I've wondered for a while why 'sudo gedit ...' works while most other gui apps won't appear. for some reason it and a handful of others work just fine with sudo. kinda weird, but i dig it.

have fun

---

### Post by oldos2er on 2008-12-03
"I've wondered for a while why 'sudo gedit ...' works while most other gui apps won't appear."

 Using sudo to call graphical applications creates potential problems. Here's why: 
[http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

---

### Post by fr34k on 2008-12-11
> **oldos2er said:**
> Since gedit is a graphical program, please use "gksu" in place of sudo to call it:

gksu gedit /etc/apt/sources.list.

 Also, you can use Synaptic Package Manager to uninstall old kernels; it will update grub for you.

Since i found similar packages for the 2.6.27.9.13, I unmarked these four packages in synaptic

linux-image-2.6.27.7-generic
linux-restricted-modules-2.6.27.7
linux-headers-2.6.27.7-generic
linux-headers-2.6.27.7

It automatically cleaned up my /boot and /boot/grub/menu.lst of those 2.6.27.7 files and entries.

Thanks oldos2er

---

