---
title: "Blank Screen on Startup"
date: 2010-12-10
forum: New to Ubuntu
---

### Post by helpdrew on 2010-12-10
I was trying to solve a 'no shutdown problem' and being the absolute newest of the newbes I did something and now Ubuntu will not start. The computer starts but after seeing the 10.10 screen and watching the walking little lites, the computer makes a bongo sound, goes to a blank screen. at this point the only thing I can do is hold the power button until the machine shuts down. I inserted the cd I used when I installed the system. Pressing the space ber several times brings me to the Ubutu boot screen. but I cannot reinstall the system, nor can I run the system from the disk. Ubuntn was running fine before I messed with it. Any suggestions on how to get the system back.

---

### Post by cariboo on 2010-12-10
Can you start in recovery mode, select failsafeX from the menu to get to the desktop?

---

### Post by helpdrew on 2010-12-11
Thanks for the quick reply [[COLOR=#d40000]**cariboo907**[/COLOR]]("http://ubuntuforums.org/member.php?u=77104") but I cannot do anything except select from the boot menu

---

### Post by sikander3786 on 2010-12-11
Which graphics card is there?

Assuming you did some damage to your graphics drivers/settings, here is a workaround.

Press and hold down Shift key from Bios screen until Grub menu pops up. Highlighting the first entry, press 'e' to edit it. Navigate to the words "quiet splash", delete them and type "nomodeset" in their place. Pressl Ctrl + X to continue boot. Can you see the desktop now?

If that doesn't work, we need a few more details.

---

### Post by helpdrew on 2010-12-11
Thank you for that instruction. I was able to get to the Grub menu and typed as you provided. When I did the ctrl+x a lot of text scrolled on the screen but I am right back to the blank screen.

---

### Post by owise1 on 2010-12-11
what type of PC are you using?
have you tried to boot from the live CD?
have you tried "ctrl alt F1 at your black screen to see if you could get a console?

---

### Post by helpdrew on 2010-12-11
I am using a Sony Laptop PCG-993L. tried using the CD I made that I used to install Ubuntu 10.10 but that only gets me to the blank screen. I was able to get into the boot screen on the cd where I attempted to run from the cd but that did not work. I also tried to reinstall Ubuntu but that did not work either. 
By following [sikander3786]("http://ubuntuforums.org/member.php?u=806649") instructions I am able to get into the Grub Menu. First I tried the "nomodeset" and that did not help. I then selected the recovery mode and that brough me to the login prompt. I put in my user name and password but it does not recognize be.

---

### Post by sikander3786 on 2010-12-11
Go to Recovery mode in Grub menu (2nd on the list) > Drop to root shell and post the output of this command.

```
lspci | grep VGA
```

And also, try reconfiguring your graphics.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

Note, capital 'X' for X11.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Reboot:

```
sudo shutdown -r now
```

Let the computer boot normally without nomodeset. What happens?

---

### Post by helpdrew on 2010-12-12
Thanks for the instruction [sikander3786]("http://ubuntuforums.org/member.php?u=806649"). Here is what happends.
I typed* lspci | grep VGA*
Response: 00:02 [COLOR=red]VGA [/COLOR][COLOR=black]compatible [/COLOR][COLOR=black]controller : Intel Corporation[/COLOR]
[COLOR=black]83915 Chipset graphic controller (CGA) (rev 11)[/COLOR]
[COLOR=black][/COLOR] 
[COLOR=black]Then I typed *sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old*[/COLOR]
[COLOR=black]*Response mv: cannot stat 'ETC/X11/xorg.conf" : no such file or directory*[/COLOR]
[COLOR=black][/COLOR] 
[COLOR=black]I stopped there since I was getting error responses.[/COLOR]

---

### Post by sikander3786 on 2010-12-12
It is an intel graphics chip.

Those instructions should work.

Did you type capital ETC?

> Response mv: cannot stat 'ETC/X11/xorg.conf" 

It is case sensitive so make sure there is no typo while you type. It needs to look like this.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

---

### Post by helpdrew on 2010-12-12
Sorry the CAPS were in my reply but not on the screen. I tried the command again and very carefully typed it exactly as you have it here . Results were the same; *Response mv: cannot stat 'etc/X11/xorg.conf" : no such file or directory*
Now help me understand if I am where I should be. I am typing these commands after the following text - *[EMAIL="root@Keitha-Desk"]root@Keitha-Desk[/EMAIL]:~#*
Keitha-Desk is the name I gave to the desktop I am trying to access.

---

### Post by sikander3786 on 2010-12-13
No wonder. Modern X deals directly with the graphics stuff and doesn't need an xorg.conf unless it is manually created.

Anyhow, try to reconfigure your graphics.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Reboot and see if that helped. If not, highlight the first entry in Grub menu and press 'e' to edit it. Navigate to words "quiet splash", delete them and type "nomodeset" in their place. Press Ctrl + X to continue boot. If that doesn't help either, repeat the process 3 more times and replace 'nomodeset' with these words, one by one.

1. i915.modeset=1
2. i915.modeset=0
3. xforcevesa

---

### Post by helpdrew on 2010-12-14
[sikander3786]("http://ubuntuforums.org/member.php?u=806649")  [COLOR=black][FONT=Verdana]Thank you so much for your effort and patience. However, I am at a total frustration point. The system was working just fine until I tried to fix a &#8216;no shut down&#8217; issue. I have not put any data of real consequence on the machine. At this point I will be satisfied if someone would show me how to reinstall the system from scratch. When I started, the machine had Windows XP (sp3) on it. The original install was mostly painless. I would like to get back to that. I can get to the command prompt but nothing that has been suggested has helped beyond that. It was a valient effort!!!![/FONT][/COLOR][COLOR=black][FONT=Verdana]Should I do an fdisk and boot from the cd and redo the install?[/FONT][/COLOR]

---

### Post by sikander3786 on 2010-12-14
> I was trying to solve a 'no shutdown problem' and being the absolute newest of the newbes I did something and now Ubuntu will not start.

Actually we don't know what you did and what you mean by "something". So, if above suggestions didn't work, it is not a graphics problem.

Regarding a new install, you can always start a new thread and many members will jump in and help you.

Good Luck!

---

### Post by helpdrew on 2010-12-14
Thank you for your help.I will start a new thread.

---

