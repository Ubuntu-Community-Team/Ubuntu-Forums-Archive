---
title: "Sound vanishes"
date: 2010-09-22
forum: New to Ubuntu
---

### Post by frank cox on 2010-09-22
Recently I switched my gui in 9.04 to Xubuntu to try it out and I keep losing the sound. Never had any problems in Gnome.
TIA

---

### Post by I8NY on 2010-09-23
is xubuntu using alsa or pulseaudio for the driver? and does the sound work for some apps or does it not work at all?

---

### Post by frank cox on 2010-09-23
> **I8NY said:**
> is xubuntu using alsa or pulseaudio for the driver? and does the sound work for some apps or does it not work at all?

Thanks for the reply.

Well I assumed it used the same alsa driver as in Ubuntu. When I had the problem I booted into Ubuntu and reset the sound,perhaps that was unwise.
There is a different layout in Xubuntu and I was in a hurry . Later today I will figure out how to change the sound configuration in Xubuntu and let you know what it says.

As far as I can tell  the sounds does not work on any of the programs.

---

### Post by lkjoel on 2010-09-23
> **frank cox said:**
> Recently I switched my gui in 9.04 to Xubuntu to try it out and I keep losing the sound. Never had any problems in Gnome.
TIA
Try Fix your sound! in my signature.

---

### Post by frank cox on 2010-09-23
> **lkjoel said:**
> Try Fix your sound! in my signature.

Thanks!

That did it.

---

### Post by lkjoel on 2010-09-23
> **frank cox said:**
> Thanks!

That did it.
Good. Now follow the instructions here: [http://ubuntuforums.org/showpost.php?p=9872284&postcount=4]("http://ubuntuforums.org/showpost.php?p=9872284&postcount=4")

---

### Post by frank cox on 2010-10-28
> **lkjoel said:**
> Good. Now follow the instructions here: [http://ubuntuforums.org/showpost.php?p=9872284&postcount=4](http://ubuntuforums.org/showpost.php?p=9872284&postcount=4)

I appreciate all your instructions. After reinstalling oss for the third time it finally occurred to me I needed to type sudo in front of the CPanel.sh .
Now that it is actually installed I need to know how to use it. This is what I get:


CPanel 0.1.3b

Usage: ./CPanel.sh [OPTIONS] [FUNCTION]

Available Functions:
  osspart1      Install OSS, part 1
  osspart2      Install OSS, part 2
  ossupdate      Update OSS
  ossrepair      Repair OSS

Available Options:
  -q, --quiet      No prompts

Should I update?  The only problem I have is when I try to open the volume control it tells me I don;t have any gstreamer plugins even though I loaded every one I found .
Is there another gui volume control or could you tell me how to fix this one.
Thanks

---

