---
title: "wifi network"
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by pixelized on 2008-11-12
i recently opened up a small internet cafe,4 computers connected to a wireless router which is directly connected to my broadband connection,now i have a dual boot system which runs on ubuntu and xp,i would like to use ubuntu on all 4 pc's however since its not yet being widely accepted her on our place,xp seems to be the prefered choice of my customers,how can i a fully control my 4 pc's using ubuntu on my wireless laptop,some users tend to go to malicious websites and porn sites

---

### Post by flyonthewall on 2008-11-12
probably depends a bit on how you define "fully control", since you have dualbooting systems.

Are you looking to : 
 - remotely choose the operating system + possibly engage a reboot?
 - remotely just shutting down the network for users surfing unwanted contents?
 - remotely taking control over the Ubuntu systems?
 - remotely taking control over the Windows systems?
 - all of the above?

---

### Post by superprash2003 on 2008-11-12
hope this helps [http://prash-babu.blogspot.com/2008/05/how-to-remote-control-windows-pc-from.html](http://prash-babu.blogspot.com/2008/05/how-to-remote-control-windows-pc-from.html)

---

### Post by enigmageek on 2008-11-13
Hello pixelized. What are the specs of your 4 cafe computers? Do they have enough ram and processor to run VirtualBox? I have Vista and XP running in Ubuntu via VBox. In case anything were to happen to the Windows systems, I can just revert to a "snapshot" I took when I first installed. Much easier and faster than re-installing Windows. If you can use virtualization your customers could still use XP but actually be running inside Ubuntu so they can't really mess anything up. If you don't want the choice of XP at bootup you can hide the Windows XP option in /boot/grub/menu.lst. Create a limited "guest" account, then install the kubuntu-desktop so Windows users would have a more familiar interface and put the needed programs as desktop icons. Hope this helps.
regards, Ray
Ubuntu Hardy 8.0.4.1-2.6.27.5
Vista and XP via VirtualBox

---

