---
title: "Some many (frustrating) things to report...."
date: 2009-03-08
forum: New to Ubuntu
---

### Post by DrakeGis on 2009-03-08
I have (since the beginning of the year) a HP Pavilion tx2500. I'm running Ubuntu 8:10 on this laptop. I works OK most of the time, however I have some problems I can't fix yet:

1 - Audio
The laptop has 2 outputs for sound (left and right). I plug my (only) one (male) plug into one of them to have sound in (external) speakers and not in the speakers of the laptop, same thing with my headphones (to avoid bother other people in the room). However, almost every time I reboot I have to switch the plug to the other output to obtain the same results (no output in the internal speakers and output in my headphones/external speakers). I don't know if it is Ubuntu or the kernel or alsa or pulseaudio.

2 - Evolution.
I love the integration of evolution with the desktop, however sometimes when I use PGP evolution crashes the whole system (not ony the e-mail client). I wrote to the evolution development team, and I have no answer. Thus, in a few days I'm going to start my migration to Thunderbird. It's really sad. More important I have no idea how to look in the system log to try to detect What/Who is causing the problem.

3 - The Network Manager/Management.
This is also another "randomly on-off" situations. I'm connected to my home (I should say "the house where I live") wireless (which I don't administrate). Sometimes, I just can't connect, so I need to reboot (yes, reboot) until the network manager allows me to connect. I tried restarting the network from console, I tried running dhclient from the console, no results. I need to restart, and the "voila" the network is running.

4 - Sessions.
I'm clearly a bit stupid because I don't understand how to work with sessions. I tried to save my (current) session, so the next time I start my computer I have OpenOffice open in the document I'm working, firefox in the newspaper I read, etc, etc. I tried, System->Preferences->Sessions and in the Options tab i checkthe box ( Automatically remember ...). Then I reboot, and .... nothing ! The same old desktop, no application (re)started. So, I tried the other way, I installed ubuntu tweak 0.4.6 and tried the same thing (Session Control).... with the same result !!!

5 - Hibernation.
Mainly because of the failure to remember the applications in the state that they were before logging out, I tried to use hibernation. A total disaster, although I must confess that I was running some simulations very CPU demanding when I tried to use it. I'm going to try later today or this week and see....

6 - Video drivers/Rotation.
I choose (erroneously) to have ATI video... I thought well, ATI and AMD are now friends and AMD allways was very friendly with the open source community and Linux, so ATI is going to have a increadible good open source drivers and try to compite with NVIDIA in the "user friendly" front (because clearly can't compite in quality, speed, performance, etc.). WRONG ! I'm still using binary (close) drivers, that are bad for reproducing video (the area were the video is reproducing keep refreshing, then the reproduction is a set of flashed images). One of my friends told me that it is because Compiz and the video driver are not talking correctly to each other.... I'm able to reproduce video correctly if I use VLC and set the output to X11. Supposedly because of the same reason, the scripts for rotation of the screen using xrandr . I'll try this week with the new ATi drivers (9.2)

7 - Eclipse.
I have to install manually Ecplise Gamynede (version 3.4.x), because Ubuntu repositories have the previous to the previous version (3.2.x). Yes, really really old repositories, which made me think about it, If no one is going to update that packages.... do we really need that there ?


One more thing: Don't get me wrong. I'm really glad and thankful to the ubuntu community, but I guess that this are things that still make Ubuntu (and linux) hard to access to the regular user.


[http://mevsmyos.blogspot.com/](http://mevsmyos.blogspot.com/)

---

### Post by kansasnoob on 2009-03-08
> **DrakeGis said:**
> I have (since the beginning of the year) a HP Pavilion tx2500. I'm running Ubuntu 8:10 on this laptop. I works OK most of the time, however I have some problems I can't fix yet:

1 - Audio
The laptop has 2 outputs for sound (left and right). I plug my (only) one (male) plug into one of them to have sound in (external) speakers and not in the speakers of the laptop, same thing with my headphones (to avoid bother other people in the room). However, almost every time I reboot I have to switch the plug to the other output to obtain the same results (no output in the internal speakers and output in my headphones/external speakers). I don't know if it is Ubuntu or the kernel or alsa or pulseaudio.

2 - Evolution.
I love the integration of evolution with the desktop, however sometimes when I use PGP evolution crashes the whole system (not ony the e-mail client). I wrote to the evolution development team, and I have no answer. Thus, in a few days I'm going to start my migration to Thunderbird. It's really sad. More important I have no idea how to look in the system log to try to detect What/Who is causing the problem.

3 - The Network Manager/Management.
This is also another "randomly on-off" situations. I'm connected to my home (I should say "the house where I live") wireless (which I don't administrate). Sometimes, I just can't connect, so I need to reboot (yes, reboot) until the network manager allows me to connect. I tried restarting the network from console, I tried running dhclient from the console, no results. I need to restart, and the "voila" the network is running.

4 - Sessions.
I'm clearly a bit stupid because I don't understand how to work with sessions. I tried to save my (current) session, so the next time I start my computer I have OpenOffice open in the document I'm working, firefox in the newspaper I read, etc, etc. I tried, System->Preferences->Sessions and in the Options tab i checkthe box ( Automatically remember ...). Then I reboot, and .... nothing ! The same old desktop, no application (re)started. So, I tried the other way, I installed ubuntu tweak 0.4.6 and tried the same thing (Session Control).... with the same result !!!

5 - Hibernation.
Mainly because of the failure to remember the applications in the state that they were before logging out, I tried to use hibernation. A total disaster, although I must confess that I was running some simulations very CPU demanding when I tried to use it. I'm going to try later today or this week and see....

6 - Video drivers/Rotation.
I choose (erroneously) to have ATI video... I thought well, ATI and AMD are now friends and AMD allways was very friendly with the open source community and Linux, so ATI is going to have a increadible good open source drivers and try to compite with NVIDIA in the "user friendly" front (because clearly can't compite in quality, speed, performance, etc.). WRONG ! I'm still using binary (close) drivers, that are bad for reproducing video (the area were the video is reproducing keep refreshing, then the reproduction is a set of flashed images). One of my friends told me that it is because Compiz and the video driver are not talking correctly to each other.... I'm able to reproduce video correctly if I use VLC and set the output to X11. Supposedly because of the same reason, the scripts for rotation of the screen using xrandr . I'll try this week with the new ATi drivers (9.2)

7 - Eclipse.
I have to install manually Ecplise Gamynede (version 3.4.x), because Ubuntu repositories have the previous to the previous version (3.2.x). Yes, really really old repositories, which made me think about it, If no one is going to update that packages.... do we really need that there ?


One more thing: Don't get me wrong. I'm really glad and thankful to the ubuntu community, but I guess that this are things that still make Ubuntu (and linux) hard to access to the regular user.


[http://mevsmyos.blogspot.com/](http://mevsmyos.blogspot.com/)

Regarding the audio I'd look here:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Regarding ATI video I'll repeat my repitition of this rant from:

[http://distrowatch.com/weekly.php?issue=20090302#news](http://distrowatch.com/weekly.php?issue=20090302#news)

> Since being bought by AMD in 2006, we were promised improved Linux drivers for ATI video cards. Recently AMD released a second batch of information on their hardware to the open source community, which helps to feed into the radeonhd driver, but their closed source proprietary driver still remains, well, closed. The driver has always been second rate, but now it has gotten to the point that Arch Linux developers have decided to dump it all together. Developer Eduardo Romero writes: "The ATI Catalyst drivers are in a pitiful state and AMD is doing close to nothing to improve the situation, they just take Linux as a joke. At least, that is the impression one gets when NVIDIA releases great drivers for Linux." He and Andreas Radke have decided to drop the driver out of the supported package trees and have pushed it back onto the community to maintain. They are instead going to concentrate on the free and open source radeonhd driver: "The radeonhd driver, which is in extra, shows some promise." After many years, the battle for open source graphics drivers is still ongoing. 

More here:

[http://www.archlinux.org/pipermail/arch-dev-public/2009-February/010394.html](http://www.archlinux.org/pipermail/arch-dev-public/2009-February/010394.html)

It appears that ATI/AMD have decided that Linux is not a serious alternative! It's sort of like the Lexmark printer dilemma!

Well, to me that means ATI and Lexmark are no longer alternatives!

---

