---
title: "Thinking of going back to Hardy..."
date: 2009-06-14
forum: New to Ubuntu
---

### Post by Troll_the_Great on 2009-06-14
Hy all! I had Hardy installed for over a year and yesterday I bought a new hard-drive and installed Jaunty. I must say that till now I'm not so pleased with it...
   My screen flickers from time to time (I had the same problem with Hardy, but after I installed the video drivers using Envy it stopped). In Jaunty, Envy looks different and was of no help, especially because it crashes every time I close it and tells me to fill some bug report.
   The second problem I have is with Warcraft III. I installed Wine and the game won't even start, I get the memory error when I press the icon (with or without the -opengl). I tried different versions of wine, with no luck (1.23, 1.19, 1.05, 1.04). In Hardy, with older versions I had no problems.
   So my question is: can I return to Hardy without changes to my personal files from my Home folder? I have a 320 GB drive, divided into 3 partitions: one NTFS with windows XP (for my brother mostly, I haven't used windows in over 6 months), and 2 ext3 partitions - one for boot (/) and one for home.If, when I install Hardy, I format the boot partition and chose the other one as home, will I lose something?
   I have to go for a couple of hours, so please leave your answers and I will respond when I will get back.
  Thanks in advance!

PS: If you can give me a solution for my problems, may be I will give Jaunty another try...

---

### Post by Jazzy_Jeff on 2009-06-14
It would help to know your system specs.

---

### Post by gradinaruvasile on 2009-06-14
I would say u have an ati card not supported anymore in Jaunty...

---

### Post by Troll_the_Great on 2009-06-14
> **Jazzy_Jeff said:**
> It would help to know your system specs.

I have an ASUS laptop (F3T model) with the following specs: AMD Turion X2 1.6 Ghz processor, 2 GB RAM, nVidia GeForce Go 7600 video adapter and a 320 GB Samsung hard drive.

---

### Post by gradinaruvasile on 2009-06-14
> **Troll_the_Great said:**
> I have an ASUS laptop (F3T model) with the following specs: AMD Turion X2 1.6 Ghz processor, 2 GB RAM, nVidia GeForce Go 7600 video adapter and a 320 GB Samsung hard drive.

OOps.. my bad.
Ok.. What driver u have installed?

---

### Post by gradinaruvasile on 2009-06-14
U could try this one:
[http://www.nvidia.com/object/linux_display_ia32_185.18.14.html]("http://www.nvidia.com/object/linux_display_ia32_185.18.14.html")

---

### Post by csl5010 on 2009-06-14
Wine supports Warcraft 3. I suspect your hardware isn't support by 9.04?
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154)

---

### Post by presence1960 on 2009-06-14
if you have a separate /home partition use the "manual" install option at the Prepare disk space window of the partitioner. Highlight your intended root partition click edit and set all the parameters. Then highlight your separate /home partion. click edit. set parameters  such as partiition type, use as (filesystem) and mountpoint (/home) **Make sure the format box is UNTICKED!!** If it is ticked it will format your /home partition! proceed with the install and your separate home partition will be set and will automount when you run Ubuntu. This will appear seamless to you . it will be in your user folder automatically.

---

### Post by lovinglinux on 2009-06-14
> **presence1960 said:**
> if you have a separate /home partition use the "manual" install option at the Prepare disk space window of the partitioner. Highlight your intended root partition click edit and set all the parameters. Then highlight your separate /home partion. click edit. set parameters  such as partiition type, use as (filesystem) and mountpoint (/home) **Make sure the format box is UNTICKED!!** If it is ticked it will format your /home partition! proceed with the install and your separate home partition will be set and will automount when you run Ubuntu. This will appear seamless to you . it will be in your user folder automatically.

You can safely install Hardy following the excellent explanation above, but I would give Jaunty a second chance. I had some issues with performance in Jaunty, but after some tweaks and recent updates I'm pleased with it.

I think you don't need Envy anymore. Jaunty comes with a nice tool for activating the video drivers. Go to "System >> Administration >> Hardware Drivers", choose the driver version you want and activate it. I have nVidia 7300 GT and there are 3 driver versions available and they all work.

---

### Post by Troll_the_Great on 2009-06-14
Thx guys for your answers. I will try the new video driver and see how it works. If it's not, then bye bye Jaunty and hello good old Hardy!
PS: could the video driver be the culprit for the memory errors in Warcraft?

---

### Post by Troll_the_Great on 2009-06-17
Hello again!

I have troubles installing the driver. It tells me I should stop the X server and then install. How do I do that?

---

### Post by ~sHyLoCk~ on 2009-06-17
> **Troll_the_Great said:**
> Hello again!

I have troubles installing the driver. It tells me I should stop the X server and then install. How do I do that?

CTRL-ALT-F1

sudo /etc/init.d/gdm stop

---

### Post by Troll_the_Great on 2009-06-17
Thx guys for all your answers, but the driver didn't worked so I installed 8.04 ... :) Maybe at the next LTS (10.04 I think) I will switch, but till then I will remain with Hardy.
Cheers!

---

