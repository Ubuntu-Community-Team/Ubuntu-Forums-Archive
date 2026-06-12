---
title: "Sound driers"
date: 2011-06-08
forum: New to Ubuntu
---

### Post by timmy86 on 2011-06-08
Hi,

I am brand new to Ubuntu / Linux so maybe i threw myself in the deep end.
Anyway, i have installed Ubuntu as a second OS and its all fine and dandy, apart from i have no sound! iam assuming i need to install some drivers, but i dont have any of the CDs i got wth the soundcard etc. I also dont remember the specifics of the sound card, so i cant really help there either... can anyone help me?!

---

### Post by FormatSeize on 2011-06-08
> **timmy86 said:**
> Hi,
iam assuming i need to install some drivers, but i dont have any of the CDs i got wth the soundcard etc. I also dont remember the specifics of the sound card, so i cant really help there either... can anyone help me?!
What version of Ubuntu are you using? If it's 10.10 or later, the sound should work out of the box.
Also, you can find some information about your sound device by opening a terminal and entering the following command:
```
lshw
```
This will list all of your hardware devices. Your sound device should be listed as well.

---

### Post by timmy86 on 2011-06-08
here it is:
(hm cant paste)
C-Media Electronics CM838

---

### Post by timmy86 on 2011-06-08
But..an update for you...
i got it working (almost) by following a command i fund elsewhere - something like ASLAMIX ? i've got a bad memory. anyway, it loaded up a asic loking volume control and  turned on all the channels and it worked!(nearly -got music but no speech. possible centre speaker not working?) anyway i was then tweaking the settings in pulse vol control and my machine froze. had to turnj off and now its not working again...

---

### Post by jwcalla on 2011-06-08
If you're using 10.10 go to System -> Preferences -> Sound.

In the dialog, click the Hardware tab and verify that your device is listed.  Go through the various Profiles and press "Test Speakers" to verify the correct profile that's appropriate for your setup.

If the device isn't listed there's probably a different problem.

Sorry but I don't know how to do this in 11.04 if that's the version you're running.

---

### Post by timmy86 on 2011-06-08
yes im on 11.04 but i hae done the above but no luck...

---

### Post by timmy86 on 2011-06-08
Right. i'm back to where i was... i opened up alsamixer and turned on S/PDIF In Select and S/PDIF Loop. I now (when watching a movie on VLC) have music but no voice. on one film i have narrative, but still no speech... any ideas?

---

### Post by timmy86 on 2011-06-08
I have now got movie player working with my DVDs but still no speech...

---

