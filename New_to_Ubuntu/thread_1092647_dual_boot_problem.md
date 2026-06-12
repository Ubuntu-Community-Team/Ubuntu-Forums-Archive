---
title: "dual boot problem"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by csu1 on 2009-03-10
I've been using Ubuntu 8.04 this past eighteen monts but I needed to install XP on my notebook for work, here is what happened:

Using G-Parted live CD I created a 15gb NTFS partition on my drive and then booted up the XP install disk. After the installation of XP on next boot there was no OS choices menu as there should be, I re-booted with the G-Parted live CD to check the partitions were intact and noticed that the NTFS partition was the only partition with 'boot' under the flag description. When I change the flag of my ext2 Ubuntu partition to 'boot' nothing happens at startup and the word 'GRUB _ ' is displayed.

How can I have both Ubuntu and XP as options in the OS choices menu? please help, thank you.

---

### Post by Jose Catre-Vandis on 2009-03-10
This howto is all over the forum :)

Boot up your PC with your Ubuntu Live CD

Once you are at the desktop, open a Terminal
```
sudo grub
```
This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands
```
find /boot/grub/stage1
```
This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3
commands)
```
root (hd?,?)
```
Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Finally exit the grub shell
```
quit
```

Reboot and you should have a grub menu once again, hopefully with choices for Ubuntu and Windows. If for whatever reason windows is not there you will need to do a bit more work:
```
sudo nano -w /boot/grub/menu.lst
```
Scroll down to the bottom of the file and add this:
```
# Windows
title           Windows
root            (hd0,?)
savedefault
makeactive
chainloader     +1
```
where ? is the number of your windows partition. So, if it is /dev/sda4 you would put a 3.

Restart and your windows boot option should be there.

---

### Post by csu1 on 2009-03-10
I followed that.

I don't have a screenshot as i'm on another PC but when the setup command was entered the first two lines read "error(not fatal)" and the last line read succeeded.

It still boots up into XP:(

---

### Post by csu1 on 2009-03-10
...ok, i'm stupid!

I've tried searching for "dual boot" - "dualboot" and guess what?

All I get is general help post upon other general help posts...?

What sections are guides and tutorials in?

Why are there no sticky's?

It is a mess in here, how do you expect anyone to find anything...

*signs up to the unanswered post team*

The OP has no resolution!

Resolve me!!!:?:

---

### Post by meierfra. on 2009-03-10
In order to get a clearer picture of your setup, I suggest to boot from your Ubuntu Live CD (the Ubuntu install CD), download the Boot Info Script to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by ivanvajar on 2009-03-10
Look closely at what **Jose Catre-Vandis** posted. Are you sure that you did EXACTLY what he said about

> find /boot/grub/stage1

---

### Post by kansasnoob on 2009-03-10
Listen to Meierfra!

Seriously, no one knows better when it comes to boot problems!

---

### Post by Jose Catre-Vandis on 2009-03-11
> **csu1 said:**
> I followed that.

I don't have a screenshot as i'm on another PC but when the setup command was entered the first two lines read "error(not fatal)" and the last line read succeeded.

It still boots up into XP:(

Bet you did what I always do
```
setup (hd0,1)
```

 when it should be:

**setup (hd0)**

---

