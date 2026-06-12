---
title: "[SOLVED] display low resolution problem"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by suganet666 on 2008-12-07
Hi.Someone help me please.I'm totally newb to linux.Just 5 days ago watched video about Ubuntu on Youtube and made decision.Read several simple guide how to install.Downloaded Ubuntu 8.10 iso image from official site.Using Nero made live cd.First tried using MS VirtualPC in XP.Ok.Go real.Installation went perfectly.Triple boot.XP Pro SP3,Vista Ultimate SP1,Ubuntu 8.10.Ubuntu bootloader installed to own partition.Using EasyBCD added to Vista bootloader.Logged in.Awesome everything new unfamiliar very exciting.Until i found out that my native display resolution impossible or more correctly not achievable my own.I'm just average windows guy.Commandline=Nightmare.My display Acer AL1916W 19inch widescreen native resolution 1440x900@60.I lost my display support cd,manual.No result on Acer site.In XP I found those figures looking at display properties  Vert56-76, Horiz30-82.My display card ASUS Nvidia FX 8600GT 512mb.Installed recommended driver.No 1440x900.After visiting this site tried manually edit xorg.conf file 4 times.Last one was most unsuccessful.Just reinstalled everything from a scratch.Sorry for my "excellent" english.

---

### Post by crwmike on 2008-12-07
Have you installed the restricted drivers, System > Administration > Restricted Drivers Manager. 

If that doesn't work, try installing **Envy**, serch for it in Synaptic. After installing, run it and select Install Nvidia driver.

---

### Post by suganet666 on 2008-12-07
> **crwmike said:**
> Have you installed the restricted drivers, System > Administration > Restricted Drivers Manager. 

If that doesn't work, try installing **Envy**, serch for it in Synaptic. After installing, run it and select Install Nvidia driver.
no.i will try it.thanks for help

---

### Post by billgoldberg on 2008-12-07
This happens because your graphics card doesn't have it's driver installed yet.

The user above has given good advice on the steps to take.

--

Did that solve you problem?

--

Since you are new, check out my Codecs and Costomization guides in my signature.

---

### Post by suganet666 on 2008-12-07
No.In Nvidia X server Settings my widescreen lcd display as crt 1024x768 4x3.biggest possible resolution 1360x768.Using synaptic could not find Envy.

---

### Post by m_l17 on 2008-12-07
Give this a try:

[http://ubuntuforums.org/showthread.php?t=975058]("http://ubuntuforums.org/showthread.php?t=975058")

---

### Post by suganet666 on 2008-12-07
Thanks man.It works.Everything ok except in x server my lcd display still as crt.But it's small problem i think.Again thanks.

---

