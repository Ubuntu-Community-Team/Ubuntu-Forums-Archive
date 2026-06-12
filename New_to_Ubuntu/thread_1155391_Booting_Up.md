---
title: "Booting Up"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by Hovercat on 2009-05-10
When I start... I choose the normal Kernel boot, the first selection, then it takes me to this DOS like thing. What do I type to get to my desktop? Please Help.

---

### Post by taurus on 2009-05-10
What happens when you type **startx** at the prompt, after you've logged in with your username and password.

Did you install the desktop version or the server version?

---

### Post by Hovercat on 2009-05-10
> **taurus said:**
> What happens when you type **startx** at the prompt, after you've logged in with your username and password.

Did you install the desktop version or the server version?

I got Desktop, I can't get to my desktop or log in, but i'll try typing startx when I get to that DOS thing.

___________________________________________
Edit:

No luck with startx. It replies:
bin/sh/: startx not found

---

### Post by Hovercat on 2009-05-10
> **taurus said:**
> What happens when you type **startx** at the prompt, after you've logged in with your username and password.

Did you install the desktop version or the server version?


And... I'm using Ubuntu for my Hl2dm SRCDS server, should I use Desktop or server?

---

### Post by Bölvaður on 2009-05-10
depends what you are going to do with it. Is there any reason to have gui? Will you be doing server only stuff?
The basic question is what you are going to be doing with it.


Also when booting you see this thing called GRUB, either hidden or not.

If it is hidden then you have to press ESC when it asks you to to get it shown.

If it is displayed then press E to edit the boot option and add "xforcevesa" at the end of the line or "vga=791" (the number there depends on what graphical card you have and represents the resolution and range of colours in bits to be displayed with the default (safe graphic mode) VESA driver.

After logging in you can download and install drivers for your graphical card from
System &#8594; Administration &#8594; Hardware Drivers


If this does not work then you should have tried **startx** first ;) which you should do.

---

### Post by krzysz00 on 2009-05-10
attach /var/log/syslog please

---

### Post by Hovercat on 2009-05-10
> **krzysz00 said:**
> attach /var/log/syslog please


I've never used Ubuntu, or any Linux program.... so I have no clue what the hell you are talking about.

---

### Post by krzysz00 on 2009-05-10
1. find a flash drive
2. plug it in to the pc with the "DOS-like thing" (actually called a shell)
type dmesg, and look for any output regarding sd<something>
3. type mkdir /mnt/usb
4. type mount -t vfat /dev/(the sd<sonething> (add a 1 on if there wasn't a 1 already at the end)) /mnt/usb/syslog.txt
5. type cp /var/log/syslog /mnt/usb
6. type umount /mnt/usb
7. take out the drive
8. put it in the computer you're posting from
9. On the drive a file named "syslog.txt" will exist. Attach it to your next post

---

### Post by Hovercat on 2009-05-11
> **Bölvaður said:**
> depends what you are going to do with it. Is there any reason to have gui? Will you be doing server only stuff?
The basic question is what you are going to be doing with it.


Also when booting you see this thing called GRUB, either hidden or not.

If it is hidden then you have to press ESC when it asks you to to get it shown.

If it is displayed then press E to edit the boot option and add "xforcevesa" at the end of the line or "vga=791" (the number there depends on what graphical card you have and represents the resolution and range of colours in bits to be displayed with the default (safe graphic mode) VESA driver.

After logging in you can download and install drivers for your graphical card from
System &#8594; Administration &#8594; Hardware Drivers


If this does not work then you should have tried **startx** first ;) which you should do.

Like I said... I plan on using it for VALVe's Source Dedicated Server. And may I ask what the hell is GUI?

---

### Post by Hovercat on 2009-05-11
I just want to turn on my computer and run my servers... I now installed the server edition, how to I get to my desktop on THAT. Do I need to Dual Boot? Cause I *can* do that :P

---

### Post by LequidMetal on 2009-05-11
> **Bölvaður said:**
> depends what you are going to do with it. Is there any reason to have gui? 

He def needs GUI   :D

> **Hovercat said:**
> Like I said... I plan on using it for VALVe's Source Dedicated Server. And may I ask what the hell is GUI?

GUI will make your life a lot easier . what is it , then ? .... please check wikipedia's article on the same

---

### Post by webwiller on 2009-05-11
GUI means you have a graphic environment, like a desktop;) If you choosed the server edition IT WONT have a graphic environment, which means that the dos-shell you get is exactly what you installed and you have to do your server work through giving it commands from the dos-like command line.

If what you need is a home-pc for your medias, docs, webbrowsing and everything you need to install desktop edition. I dont really know what server works you can do from a desktop edition in case you needed both.

---

### Post by Bölvaður on 2009-05-11
if you have server set up now you can just install a desktop (but there really isn't any reason to have it... most servers dont have graphical user interface [gui] because it is waste of resources and useless to the administrators).

for desktop login and type

sudo apt-get install ubuntu-desktop

you may need to restart your xserver in order to use the desktop as soon as it has been installed.
Alternatively you can turn the pc down and wait for it to boot up again, but it takes like 40 seconds vs 5.

---

### Post by Hovercat on 2009-05-11
> **Bölvaður said:**
> if you have server set up now you can just install a desktop (but there really isn't any reason to have it... most servers dont have graphical user interface [gui] because it is waste of resources and useless to the administrators).

for desktop login and type

sudo apt-get install ubuntu-desktop

you may need to restart your xserver in order to use the desktop as soon as it has been installed.
Alternatively you can turn the pc down and wait for it to boot up again, but it takes like 40 seconds vs 5.

Thank You. You definitely made this easier for me :D


__________________________________________________
EDIT:

After the setup finishes for the sudo command, it starts up ubuntu, normally, then my monitor turns off and my computer is un-responsive. Help?

---

### Post by Hovercat on 2009-05-11
You know what.... **** it, i'ma do Dual boot.

---

### Post by Hovercat on 2009-05-13
:D I got it to work, and my servers run amazingly. Thank you :D I downloaded Ubuntu 9.0.4 and it works AMAZING...

---

