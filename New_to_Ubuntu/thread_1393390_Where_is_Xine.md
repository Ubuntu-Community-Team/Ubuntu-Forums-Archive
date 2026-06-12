---
title: "Where is Xine?"
date: 2010-01-29
forum: New to Ubuntu
---

### Post by asharpham on 2010-01-29
I am using Ubuntu 9.10. I just downloaded xine using Synaptic but can't find it anywhere. It doesn't appear in any of the menus.

My actual problem is I'm trying to find something that will play DVDs. Movie Player doesn't, MPlayer doesn't, VLC doesn't. I've downloaded things like libdvdcss2 but nothing has worked. I thought Xine might do it but can't find it and I don't know why it's not in the menu.

Please can anyone help.

Alan.

---

### Post by warfacegod on 2010-01-29
> **asharpham said:**
> I am using Ubuntu 9.10. I just downloaded xine using Synaptic but can't find it anywhere. It doesn't appear in any of the menus.

My actual problem is I'm trying to find something that will play DVDs. Movie Player doesn't, MPlayer doesn't, VLC doesn't. I've downloaded things like libdvdcss2 but nothing has worked. I thought Xine might do it but can't find it and I don't know why it's not in the menu.

Please can anyone help.

Alan.

Right click you Menus and select Edit Menus. Look in Sounds and Video and put a check next to xine.

Do you have restricted extras enabled in software Sources?

---

### Post by asharpham on 2010-01-29
Yes, restricted extras is ticked. I looked in "Edit Menus" Sound & Video but Xine is not listed.

Interestingly, within an hour of posting the message I have had some success in playing a dvd through Movie Player. I followed instructions on installing Medibuntu including the installation of libdvdcss2 (which I had already downloaded but hadn't made any difference). I also followed instructions on installing w32codecs. Something worked as i can now play a DVD in Movie Player - but I don't know what did it.

The above installations were via the Terminal, not Synaptics.

However, there is still no sign of xine.

Alan.

---

### Post by SuperSonic4 on 2010-01-29
Xine and Xine-ui are different.

The former is a phonon backend and default in KDE. The latter is a self-standing movie player using the xine engine

---

### Post by elliotn on 2010-01-29
go to terminal and type xine

---

### Post by asharpham on 2010-01-29
That must be my problem. I downloaded xine, not xine-ui. I went to Terminal and typed xine but got the message "Command not found".

Should I uninstall xine or let sleeping dogs lie?

Alan.

---

### Post by dolphinaura on 2010-01-29
let xine be and just install xine-ui

---

### Post by asharpham on 2010-01-29
Unfortunately xine-ui hasn't helped but despite this, my problem has been solved and I can now play DVDs using Movie Player. Thank you to all of you who helped. I really appreciate it.

Alan

---

