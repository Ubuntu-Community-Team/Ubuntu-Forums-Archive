---
title: "CPU runs slower on Linux than Windows?"
date: 2009-09-19
forum: New to Ubuntu
---

### Post by harisund on 2009-09-19
Ok guys here's the deal - 
Computer: ASUSTeK Computer INC. 900HD 0501
Graphics: Mobile Intel(R) 915GM/GMS,910GML Express Chipset Family
External Monitor:DELL 1901FP [Monitor] (1280x1024)

I use the netbook by connecting an external monitor, keyboard and mouse. Here are the questions I have - 

My glxinfo gives me the vendor as SGI or something. How do I get correct Intel drivers? 

I am trying to watch Hulu and other videos, and on Windows XP, the videos play smoothly. I don't multi task when watching Hulu on either OS, since then the video tends to get choppy. But if I only watch the video or full screen it on WIndows XP, it works just great. But on Ubuntu, the video is extremely frame by frame. Why is this? Wrong graphics driver? Any solution? 

Next, I have a gnome-system-monitor applet on my Gnome panel. When I mouse over it, it shows me a CPU usage percentage, but when I do open the gnome-system-monitor application, the sum of CPU usage percentages don't add up. gnome-system-monitor uses up some 3% or 4% or something, firefox uses quite less and still the applet shows 100%. What's the catch?

---

### Post by ankspo71 on 2009-09-19
Hi,

The gnome system monitor chews up alot of resources for some reason, so I prefer to go to the terminal and type in the word [ top ] instead. Top is a non graphical task manager. The results might be more comparable to your applet's results, and much better than that of gnome's system monitor.

Btw, I have read here that adobe doesn't make a good version of flash player for linux yet. It seems to run rough unless you have a high end computer. I'm hearing 64 bit linux might even be worse. If you use firefox, I can recommend a great extension called "stop autoplay", which works good for sites like youtube or sites that use multiple flash objects on a page causing flash player to run really rough. It helps eliminate that by letting you click on only the flash files you want to run.

I hope this helps somehow.
James

---

### Post by Liolikas on 2009-09-19
Intel drivers are called xf86-video-intel and there is no others.

>But on Ubuntu, the video is extremely frame by frame. 
>What's the catch? 
Intel drivers version you have is buggy and do not work well. 
You have options:
Get newer drivers. 2.8.x they are cool and they will be in Ubuntu 9.10.

OR


Use x11 sth. like that as video output (fixes only movie things but not games etc.
Install mplayer:
sudo apt-get install mplayer
command. Then:
mplayer -vo list
mplayer -vo help
Commands give available video outputs (vo).
mplayer -vo x11 video.xx
Should work or something like that. Maybe you do mot like that way so chose forst OR. Thry Ubuntu alpha even 9.10 alpha 6 may work much better for ya. ;)

---

### Post by Liolikas on 2009-09-19
........ .........
Xubuntu 6.06 you have?!?

---

### Post by harisund on 2009-09-19
> **ankspo71 said:**
> Hi,

.... terminal and type in the word [ top ] instead. ....
... adobe doesn't make a good version of flash player for linux .....
..."stop autoplay", ....

Thanks. First, yeah I think I am better off using the top. I just hope gnome-terminal doesn't end up using system resources !!

Second, yeah Flash on Linux sucks :( And I do use Flashblock 

> **Liolikas said:**
> 
.... xf86-video-intel ...
... newer drivers. 2.8.x they are cool and they will be in Ubuntu 9.10.
OR
Use x11 sth. like that as video output (fixes only movie things but not games etc.
Install mplayer:
sudo apt-get install mplayer
command. Then:
mplayer -vo list
mplayer -vo help
Commands give available video outputs (vo).
mplayer -vo x11 video.xx
Should work or something like that. Maybe you do mot like that way so chose forst OR. Thry Ubuntu alpha even 9.10 alpha 6 may work much better for ya. ;)

(1) I will try the xf86-video-intel driver. 
(2) What do you mean by "2.8.x they are cool"? 
(3) I am not quite sure what you are referring to by the rest of your post. x11 sth? Also, does this help in playing Flash videos like Hulu and YouTube? 

> **Liolikas said:**
> ........ .........
Xubuntu 6.06 you have?!?

Ah long story. I used to be a Ubuntu user back in the day and used to actively post in the forums here too.  Eventually I stopped using Ubuntu and went back to Windows because .. ah well. We have all been there. 

Lately I have received a couple of old laptops etc, and machines that don't have CD ROM drives, so it's back to Ubuntu. And frankly, I am pretty impressed with 9.04 compared to 6.06

---

### Post by NoaHall on 2009-09-19
Flash on Linux does NOT suck. The 64 bit flash is better than the 32 bit one on 32 bit!

Follow the link bellow to install 64 bit flash.

---

### Post by shae on 2009-09-19
[https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance](https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance)

This is a good place to start concerning your flash performance.

---

### Post by ankspo71 on 2009-09-19
> **NoaHall said:**
> The 64 bit flash is better than the 32 bit one on 32 bit!

I didn't know about this flash tip, thanks. Maybe now I will have a smoother flash on my other comp... the celeron one.
James

---

### Post by harisund on 2009-09-19
> **NoaHall said:**
> Flash on Linux does NOT suck. The 64 bit flash is better than the 32 bit one on 32 bit!

Follow the link bellow to install 64 bit flash.

This installs 64 bit Flash on a 32 bit operating system? What is "better than 32 bit one on 32 bit" mean?

---

### Post by NoaHall on 2009-09-20
No, I mean 64 bit flash on 64 bit Ubuntu is better than the 32 bit one on either the 32 bit Ubuntu or the 64 bit ubuntu.

---

### Post by Liolikas on 2009-09-20
(2) What do you mean by "2.8.x they are cool"?
They work very well for me I have similar card and had problems with old drivers.
(3) I am not quite sure what you are referring to by the rest of your post. x11 sth? Also, does this help in playing Flash videos like Hulu and YouTube?
Sadly but not much so try to grab better drivers..You can download youtube video with youtube-dl but stuck with Hulu.

---

### Post by automaton26 on 2009-09-20
I had a low-spec laptop and found that videos were smoother in Opera 10, rather than Firefox 3.

Probably because it uses less memory.

---

### Post by 3rdalbum on 2009-09-20
Full-screen Flash is not as smooth as full-screen 1080p Blu-ray for me; must be a problem with the Flash Player.

So I just use the Compiz "zoom" function instead whenever I want to look at a Flash movie in full-screen.

---

