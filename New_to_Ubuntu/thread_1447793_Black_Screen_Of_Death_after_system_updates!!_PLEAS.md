---
title: "Black Screen Of Death after system updates!! PLEASE HELP!!"
date: 2010-04-05
forum: New to Ubuntu
---

### Post by maryalesia on 2010-04-05
Hi guys!

I just Officially Installed Ubuntu 9.10 on my gateway fx edition laptop. After I figured out the whole "nolacip" thing, I got the screen to work for the install. I rebooted, and everything worked fine: I logged in, had a desktop, etc. I installed some system updates, and clicked "restart now" when I was prompted.

That's when the problems began. 
In the boot-options menu, I have four different Ubuntu versions to choose from. Two generic, two recovery mode, different weird decible numbers. 

I get the white ubuntu logo, but I never get to the login screen. 

In recovery mode, "startx" sends me right back to the black screen, and 
# sudo apt-get remove xorg-driver-fglrx
# sudo dpkg-reconfigure -phigh xserver-xorg

gets me something about how no fglrx file exists, so none was removed, and no phigh file exists. 

I have absolutely no idea what I'm doing; all these commands I'm just copying and pasting from forums like these. I really, really need my desktop back ... 

Plese help!!

---

### Post by undecim on 2010-04-05
Try choosing the second normal mode from the Grub menu. (it's an older kernel version that may work better)

Also, what video card do you have? To find out, type
```
lspci | grep VGA
```
into a terminal to find out.

Also, you can press "e" when the normal mode is highlighted in the Grub menu to edit the entry. Remove "quiet splash" from the end of the kernel line to get rid of the ubuntu log screen (just for one boot) and get useful output. Press Ctrl+X after doing so to continue booting.

---

### Post by maryalesia on 2010-04-05
Hi guys. I'm a complete n00b, so bear with me. 

I installed Ubuntu (dual-booting with Vista), re-booted after install, and voi-la! A desktop. So I checked for any system updates, downloaded the files, and restarted my computer when prompted.

At the boot screen, I chose the first generic Ubuntu option (there were four different options) and never got past the white ubuntu logo. All I get is a black screen.

I re-booted in recovery mode, and typed "startx" because someone said something about it in a forum ... I think. Anyway, it got me right back to the black screen.

I then tried to reconfigure my xorg driver, and I got an error message saying that the file "phigh" does not exist. I have a sneaking suspicion that there IS no xorg driver installed in my system.

What is up?? Is it Grub? What the heck IS grub?? 

I'm so lost. Please, wonderful, smart people, help me get my computer to work again.

---

### Post by maryalesia on 2010-04-05
> **undecim said:**
> Try choosing the second normal mode from the Grub menu. (it's an older kernel version that may work better)

Also, what video card do you have? To find out, type
```
lspci | grep VGA
```
into a terminal to find out.

Also, you can press "e" when the normal mode is highlighted in the Grub menu to edit the entry. Remove "quiet splash" from the end of the kernel line to get rid of the ubuntu log screen (just for one boot) and get useful output. Press Ctrl+X after doing so to continue booting.

My video card is a nvidia geforce 9800M GTS. 

Hold on while I get my other computer up so I can read your instructions while I reboot ...

---

### Post by maryalesia on 2010-04-05
> **undecim said:**
> Try choosing the second normal mode from the Grub menu. (it's an older kernel version that may work better)

Also, what video card do you have? To find out, type
```
lspci | grep VGA
```into a terminal to find out.

Also, you can press "e" when the normal mode is highlighted in the Grub menu to edit the entry. Remove "quiet splash" from the end of the kernel line to get rid of the ubuntu log screen (just for one boot) and get useful output. Press Ctrl+X after doing so to continue booting.

Just tried it ... still a black screen. Could it be grub? I have no idea what "grub" is, by the way.

---

### Post by RemiemB on 2010-04-05
using startx does not work in Ubuntu.

Boot into recovery mode and, at command line, type

```
sudo /etc/init.d/gdm start
```

See what happens and keep us posted.

---

### Post by undecim on 2010-04-05
> **maryalesia said:**
> My video card is a nvidia geforce 9800M GTS. 

Hold on while I get my other computer up so I can read your instructions while I reboot ...

Go to recovery mode and make sure you have nvidia-glx-185 installed.

Type
```
sudo aptitude install nvidia-glx-185
```

---

### Post by maryalesia on 2010-04-05
> **RemiemB said:**
> using startx does not work in Ubuntu.

Boot into recovery mode and, at command line, type

```
sudo /etc/init.d/gdm start
```See what happens and keep us posted.

I got a message saying something about "since gdm is now an Upstart ..." 

but nothing else ...

---

### Post by maryalesia on 2010-04-05
> **undecim said:**
> Go to recovery mode and make sure you have nvidia-glx-185 installed.

Type
```
sudo aptitude install nvidia-glx-185
```

I'm getting a bunch of different errors that all end in:
Could not resolve 'us.archive.ubuntu.com'

---

### Post by JamezQ on 2010-04-05
To start a new gui session use this command.


```
startx -- :1
```

startx might not work but this does for me.

---

### Post by cariboo on 2010-04-05
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by maryalesia on 2010-04-05
will re-installing ubuntu fix this?
I just installed it today, so I don't have any files that I'm worried about.
Honestly, I'm irritated enough to just uninstall Ubuntu, but I don't know how to do that. It seems like a LOT of work. This is such a pain.

---

### Post by undecim on 2010-04-06
> **maryalesia said:**
> I'm getting a bunch of different errors that all end in:
Could not resolve 'us.archive.ubuntu.com'

If you can connect to a router with an ethernet cord, you can run
```
sudo dhclient
```
To connect to the internet and try again.

If you have to use wireless, [http://www.wikihow.com/Set-up-a-Wireless-Network-in-Linux-Via-the-Command-Line](http://www.wikihow.com/Set-up-a-Wireless-Network-in-Linux-Via-the-Command-Line) has a guide on connecting to a wireless network from command line interfaces like recovery mode.

---

### Post by maryalesia on 2010-04-06
SOLVED!!

I don't know how to change the thread to solved. One day I will learn ...

Anyway, yesterday I sort of had a breakdown. It went a little like this:

cue manic laughing!! cue crazy person deleting harddrive parameters!! cue a bazillion window's vista security alerts!!

cue my computer becoming a twelve pound paperweight!!!

muwahahaha

Excellence. Achieved. 

-----------------------------------------------------------------

Anyway, I totally crashed, and deleted GRUB. Who does that, you ask? A crazy person on a rampage, that's who. 

So today, with a clear mind and a firm grasp on sanity, I reinstalled Ubuntu thru live-disc mode, which I launched with safe graphics on and nolacip. It worked!!

I have no idea what was wrong before. I got through system updates and two restarts without a problem (that's where it all started before) and am just happy I can access all my windows files again *ahemiTunescoffcoff*. 

Thanyou all who helped!!

---

### Post by RemiemB on 2010-04-06
Nice one!

---

