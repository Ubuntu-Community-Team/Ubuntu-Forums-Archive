---
title: "Problems with starting Ubuntu from burned cd"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by enrico68 on 2009-01-22
Let's see if anyone experienced this same problem: I tried to burn the ISO file on the cd with Nero, but it didn't work, it kept giving me writing errore messages. Then I used imgburn, the free utily, and I got to burn the cd, well. After that, I rebooted the pc from the cd just burned, I got to the Ubuntu initial screen, chose the language, and tried to start it, but I got another error message: unable to read the cd,reboot, and at the same time there was a weird noise, like a clicking, in the cd drive, as if the cd was just spinning loosely...I thought my cd drive might have some kind of a problem, so I tried to reboot my pc this time with the originl windows xp cd, and it worked, so it can't be my cd drive. What could be the problem?

---

### Post by Stalker72 on 2009-01-22
Burn the CD at lowest possible speed, like 2.4x.

After that, check the [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM").

Stalker72

---

### Post by enrico68 on 2009-01-22
> **Stalker72 said:**
> Burn the CD at lowest possible speed, like 2.4x.

After that, check the [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM").

Stalker72

Hi Stalker, I did that already, the lowest speed I can get is 4x, did the md5sum check as well, and all is fine, I know the ISO file is not corrupted. Could that be a problem with the physical cd? Tonite I'll get a new one and try all over again. All I know for sure is that md5sum checks.Any more input?

---

### Post by Stalker72 on 2009-01-22
You could try alternative burning software.

Did you check that the CD is completely empty?

Stalker72

---

### Post by enrico68 on 2009-01-22
> **Stalker72 said:**
> You could try alternative burning software.

Did you check that the CD is completely empty?

Stalker72

I did check that, and tried two different burning softwares, I am really lost here, I don't undestand what could be possibly wrong, what concernes me is the noise I hear coming form the cd drive when I try burning or installing Ubuntu, but I know my cd drive works fine...

---

### Post by Elfy on 2009-01-22
I see that you checked the md5sum - have you checked the cd integrity with the boot menu option?

---

### Post by enrico68 on 2009-01-22
> **forestpixie said:**
> I see that you checked the md5sum - have you checked the cd integrity with the boot menu option?

I am sorry Forestpixie, how do you do that??

---

### Post by atomizer on 2009-01-22
I have heard that Nero doesnt always burn iso correct.

I would suggest try yet another burning software

IsoRecorder always worked for me......

[http://isorecorder.alexfeinman.com/isorecorder.htm]("http://isorecorder.alexfeinman.com/isorecorder.htm")

---

### Post by Stalker72 on 2009-01-22
> **enrico68 said:**
> I am sorry Forestpixie, how do you do that??
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

Stalker72

---

### Post by Stalker72 on 2009-01-22
> **atomizer said:**
> I have heard that Nero doesnt always burn iso correct.

I would suggest try yet another burning software

IsoRecorder always worked for me......

[http://isorecorder.alexfeinman.com/isorecorder.htm]("http://isorecorder.alexfeinman.com/isorecorder.htm")
I recommend K3b or the integrated burning tool in Gnome.

Stalker72

---

### Post by Michael.Godawski on 2009-01-22
I guess forestpixie meant the Check CD for defects:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Or?

---

### Post by enrico68 on 2009-01-22
> **atomizer said:**
> I have heard that Nero doesnt always burn iso correct.

I would suggest try yet another burning software

IsoRecorder always worked for me......

[http://isorecorder.alexfeinman.com/isorecorder.htm]("http://isorecorder.alexfeinman.com/isorecorder.htm")

As a matter of fact, Nero just won't do it, I'll try another burning software, thanks atomizer

---

