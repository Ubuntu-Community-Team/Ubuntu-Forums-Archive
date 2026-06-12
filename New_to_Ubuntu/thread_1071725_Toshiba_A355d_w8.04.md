---
title: "Toshiba A355d w\8.04"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by jerzydirtracer on 2009-02-16
I am getting a new Toshiba A355D series satellite laptop, does anyone have any experiences with this series laptop? Will Ubuntu recognize everything including the webcam and sata port? It is unfortunate that it comes with vista, but that will be history. I want to start with a fresh copy of Ubuntu 8.04. 

Thanks

---

### Post by 0xbaadf00d on 2009-03-26
Hi, I also just got this laptop, dual booting with ubuntu 8.04

Ive had a few problems that have been fixed, and some not, so im curious how you have done.  I have atheros wireless (working after recompiling ath9k driver) w/ amd turion x2.

screen resolution works after updating system, but function keys and speakers/headphones have been a problem. Have you been able to fix?

---

### Post by jerzydirtracer on 2009-03-28
I tried to boot 8.04 lts and am having problems. It wont boot properly. I am currently working on the problem. Hopefully I should figure it out.

---

### Post by jerzydirtracer on 2009-03-28
Oh, thanks it is good to know that the wireless works. that was my biggest concern.

---

### Post by 0xbaadf00d on 2009-03-28
for the sake of completeness, here is how I got the wireless working:
[http://ubuntuforums.org/showpost.php?p=5535562&postcount=3](http://ubuntuforums.org/showpost.php?p=5535562&postcount=3)

I have had boot problems also. they started when I tried to fix speaker and function key issues.  I tried replacing various shell scripts with no success yet.

echo “10&#8243; > /proc/acpi/video/VGA/LCD/brightness

found in [http://ubuntuforums.org/showthread.php?t=383062](http://ubuntuforums.org/showthread.php?t=383062)

only works part of the time, other times it is just ignored or wont write to file.  Ill post here if I can get this stuff workking right.

---

### Post by 0xbaadf00d on 2009-03-28
fixed brightness problem.  Not a pretty fix, but it works in the meantime.

first
```
sudo su
``` or 
```
sudo -s
```

then

```
cat /proc/acpi/video/VGA/LCD/brightness
```

this will show supported brightness levels

in my case, 0,10,20,30,40,50, 60, 70


so for min brightness on my machine::
```
echo -n 0 > /proc/acpi/video/VGA/LCD/brightness
```

max:
```
echo -n 70 > /proc/acpi/video/VGA/LCD/brightness
```

**Note*********
Settings brightness to numbers other than those listed is ignored


next up: to fix headphones and speakers.

---

### Post by jerzydirtracer on 2009-03-28
I tried 3 different 8.04 discs, 2 orig. discs did what I said in my original post, one I burned, they worked on my old toshiba, I know modprobe has something to do with video, maybe that is the problem, also during boot the kernel hangs on the cups system, yet I downloaded and burnt Mandriva one and loaded it live and worked perfect, even the intel wireless worked. I know it might be a travesty to some to use mandriva, but if it works, I will go to it, it is still Linux, so technically I wont be straying too far from Ubuntu. the only thing is it comes with kde which I will switch to gnome.  Besides I am going to pick up a new hd and use it for Linux and save the windblows hd for reference and as a usb hd.

---

### Post by 0xbaadf00d on 2009-03-29
I just tried the mandriva liveCD.  Fn keys work now, but the volume knob does not. Neither do headphones:(

---

### Post by jerzydirtracer on 2009-03-29
Every thing seems to work with Mandriva live, this is what I might go with. No offence to Ubuntu.

---

