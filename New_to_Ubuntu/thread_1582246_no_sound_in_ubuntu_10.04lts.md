---
title: "no sound in ubuntu 10.04lts"
date: 2010-09-26
forum: New to Ubuntu
---

### Post by TONY612 on 2010-09-26
Iam using dell studio 1450 powered by ubuntu 10.04LTS. Everything except sound works perfectly in it. Not even a beep sound. I have installed alsa as in reply to a question like this, but i didn't worked. Plz help me....

---

### Post by danroyds on 2010-09-26
I have the same problem on a acer aspire 7730 had no sound for two weeks,looks ubunte is rubish on sound think i will be going back to m/s,unless there is a fix,HELP!

---

### Post by Paqman on 2010-09-26
> **TONY612 said:**
> I have installed alsa as in reply to a question like this, but i didn't worked.

Can you post a link or tell us exactly what you've done already? You may need to undo what you've done already before we can get it fixed.

---

### Post by Paqman on 2010-09-26
> **danroyds said:**
> I have the same problem on a acer aspire 7730 had no sound for two weeks,looks ubunte is rubish on sound think i will be going back to m/s,unless there is a fix,HELP!

I'd suggest starting your own thread, since it's unlikely that you've got the same problem as the OP, and trying to fix two different problems in one thread would get confusing.

---

### Post by 0N3 on 2010-09-26
Have you tried installing gnome-alsamixer? See if nothings muted?

sudo apt-get install gnome-alsamixer

---

### Post by xieon on 2010-10-02
> **0N3 said:**
> Have you tried installing gnome-alsamixer? See if nothings muted?

sudo apt-get install gnome-alsamixer

I had this problem each time I did a clean install. The first time I had to unmute rythmbox in sound options, the second time I entered the code above then went to output connector, changed it and perfect.

---

### Post by lidex on 2010-10-03
> **TONY612 said:**
> Iam using dell studio 1450 powered by ubuntu 10.04LTS. Everything except sound works perfectly in it. Not even a beep sound. I have installed alsa as in reply to a question like this, but i didn't worked. Plz help me....

OK, but alsa is in the default install.
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by ahmadnissar on 2012-02-20
> **lidex said:**
> OK, but alsa is in the default install.
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```Choose the upload option and provide a link for the output.
the out put link is:
[http://www.alsa-project.org/db/?f=c056d816c230ef92739153a71491ef2f962bbf32](http://www.alsa-project.org/db/?f=c056d816c230ef92739153a71491ef2f962bbf32)

---

### Post by overdrank on 2012-02-20
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

