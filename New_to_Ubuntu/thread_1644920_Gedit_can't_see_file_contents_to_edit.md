---
title: "Gedit can't see file contents to edit"
date: 2010-12-13
forum: New to Ubuntu
---

### Post by Calais225 on 2010-12-13
I want to open alsa-base.confile using gedit so that I can add one line to the file.  the line is supposed to allow my Dell vostro to shut off the speaker when headphones are inserted.

When I use gedit to get the above file, it shows up just as a folder and I can't see the contents to figure out where to add the line, supposed to go at the end but can't find the end, beginning or middle.
Nada.

Must be a simple way to view the contents but I can't find it.

---

### Post by Quackers on 2010-12-13
What are you typing into the terminal?

---

### Post by Calais225 on 2010-12-13
I typed gedit alsa-base.confile

---

### Post by Calais225 on 2010-12-13
I am using version 10.10 and followed a thread on how to solve this.

---

### Post by Quackers on 2010-12-13
In a terminal try
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
But please make sure that's the correct file before changing anything. It may even be worth copying the file to a spare folder before making changes.

---

### Post by Calais225 on 2010-12-13
Okay, did that and it opens the same window as I had previously but there is no lines of code or anything, just the cursor.

This is what I had before but didn't know how to add the needed line.  It was supposed to be added to the end of the file's contents I thought.

---

### Post by Quackers on 2010-12-13
Hmm, I would suspect then that you need to find a different file to change. If you were following a guide written a long time ago things could have changed.

---

### Post by Calais225 on 2010-12-13
Oops, I mistyped  your line.

Now I have code.

---

### Post by Calais225 on 2010-12-13
I will add the new line and test my sound.  and report back.

---

### Post by Quackers on 2010-12-13
Aha! :-)  I just checked that file on my system and it is not empty.
Good luck :-)

---

### Post by Calais225 on 2010-12-13
Nope, no joy, no muting of the speaker.  Better check my typing given my fumble fingered approach this evening.

---

### Post by Quackers on 2010-12-13
You could try a reboot, once you are sure it is the correct file.
Also, did you save the amended file?

---

### Post by Calais225 on 2010-12-13
good idea, tried a reboot, but still no mute.  Poetic but unsatisfactory.

Will go and check my typing and saving to confirm.

---

### Post by Calais225 on 2010-12-13
checked all my typing, saved, rebooted and still sound blaring from speakers...

this worked the last time i did this on my pure ubuntu but this is now Linux Mint....should be using the same ALSA for audio

I wonder how to check that?

Maybe Mint uses something different, that's the only thing I can figure.  By the way, this is a dual boot so it has pure Ubuntu and Mint Ubuntu on it.

????

---

### Post by Quackers on 2010-12-13
Try the change in Ubuntu and see if it works there?

---

### Post by Calais225 on 2010-12-13
Yup, it did.  I fixed that last week and there was great celebration in the household.

So, today, I thought I would see if it worked or would work in Mint.  

Now I am checking Synaptic to see if there are some files missing by comparing my Ubuntu partition to what is installed in Mint.

Slow process as i have to go back and forth between the two.

But, thanks for getting me to the point where I can see the contents of the alsa file.

this may take a while but I will post any progress.

thanks for the help.

---

### Post by Quackers on 2010-12-13
You're welcome. Good luck in your quest :-)

---

### Post by Calais225 on 2010-12-14
Solved:

I realized this morning that when I added the computer model number to the line of code, I used a capital letter for Dell.  Went back in, changed it to dell and all is good.

Now I can listen to my jazz and use Skype without annoying others.

Thanks again to Quackers and Ubuntu for continuing my education.  It's a good thing to keep this 66 year old brain firing on as many neurons as I have left.  (after a mispent youth)

---

