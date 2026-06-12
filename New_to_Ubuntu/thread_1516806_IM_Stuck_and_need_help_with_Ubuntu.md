---
title: "IM Stuck and need help with Ubuntu"
date: 2010-06-24
forum: New to Ubuntu
---

### Post by princennamdi on 2010-06-24
[FONT=Trebuchet MS][SIZE=2]i had everything working fine an hour ago, then i had a new idea:idea:, and icreated another partition /dev/sda8, about 1.5 gb,  i added another menu entry to grub to boot from sda8,  then i used [Unetbootin]("http://www.google.com.ng/search?q=unetbootin&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a&safe=active") to deploy [GParted]("http://www.google.com.ng/search?hl=nl&safe=active&client=firefox-a&hs=q25&rls=com.ubuntu%3Aen-US%3Aunofficial&q=gparted&aq=f&aqi=&aql=&oq=&gs_rfai=") Live ISO on that partition, ie  instead of on a removable disk.
:lolflag:

when i restarted, i was greeted with the unetbootin screen like [this]("http://www.linuxreaders.com/wp-content/uploads/2009/05/unetbootin.png"), and it listed the option for 
Gparted, Gparted blah blah blah, memtest86 and boot from hard disk(if any)
fine i could now use GParted, but that was the only OS accessible, no GRUB screen

i then booted from my live ubuntu 9 cd and did the normal grub repair i used to do

[B]sudo grub
root (hd0,4)
setup (hd0)
exit
[/B]
and restarted.....
now whenever i turn on my system, it boots into grub....not the grub boot menu, it boots into a grub terminal, and thats it.....i can access neither my win7 nor ubuntu 9 nor ubuntu 10 nor the GParted os nor even memtest86.....

what do i do?

from the grub terminal, i tried
[B]
kernel /vmlinuz root=/dev/sda7 ro vga=791
boot[/B]

it would start doing some work, then it freeze on this message

_**init: plymouth main process (57) killed by segv signal**_

please how do i get my grub back???

[/SIZE][/FONT]

---

### Post by warfacegod on 2010-06-24
Reinstall GRUB2, section #13: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

