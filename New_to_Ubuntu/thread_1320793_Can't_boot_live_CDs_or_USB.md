---
title: "Can't boot live CDs or USB?"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by Tahakki on 2009-11-09
When trying to boot from the Karmic or Hardy CDs, or my GParted Live USB, it works fine - right up until the X server starts. This makes the screen go all white, with colours moving around. This is only in terminal 7, Ctrl + Alt + F1/2/3/4/5/6/8 all drop me into the command line.

It happened when I had installed Karmic using the alternate installer, but editing the X server fixed it.

Oddly, this has only started happening recently. I've had that Hardy disc since April '08, and it's never failed me.

I can boot my Damn Small Linux USB stick fine, though.

Help?! I haven't changed my hardware at all, and I just can't understand why my Hardy disc no longer works?

Please, please help me. It's rather essential as I need to edit my partitions ASAP.

---

### Post by wrgb2 on 2009-11-09
In Hardy you could try sudo xfix from the command line.  It's not in Karmic.  This should work from the USB boot, but I'm not sure about the Live CD.

---

### Post by Tahakki on 2009-11-09
Hmm, I'll give it a go, thanks.

I don't understand why my CD isn't working now when it did perfectly a while back. Since, nothing has changed save the HD partitions.

---

### Post by Bunnybugs on 2009-11-09
Well, could be some scratch on your disc?

---

### Post by Tahakki on 2009-11-09
Not likely if it's affecting an old disc, a brand new disc and a USB stick.

I tried xfix, but the command doesn't exist on the Hardy CD.

Perhaps I should make myself clearer as to the nature of this white screen. It is NOT just a pure white screen like you get sometimes when switch user doesn't work properly. It's the whole 'hardware malfunction' looking screen - it starts black, glows to a sort of pixellated yellow and then fades to completely white with a big black line across the middle.

Any ideas?

---

### Post by wrgb2 on 2009-11-09
Do you have a third party driver installed and using desktop effects?

---

### Post by LewRockwell on 2009-11-09
Slip in a Puppy Linux LiveCD Disk and see what happens

the pupster provides both vesa and xorg and if neither work you should suspect your hardware has failed

.

---

### Post by Tahakki on 2009-11-10
I booted Puppy with Xorg and it ran fine.

Should I try Vesa or is that irrelevant? Any more ideas?

---

