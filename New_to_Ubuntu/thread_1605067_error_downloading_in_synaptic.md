---
title: "error downloading in synaptic"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by jcoffey on 2010-10-24
i tried downloading computertemp and this is the error i got...

"E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory"

i have only used ubuntu (10.10, macbook 6,1 , 32-bit) for a few hours and have no clue what i messed up.  i did edit my fstab and couldn't boot until i fixed it through the live cd.  but i was trying to enable noatime so i dont think that is connected to this?

---

### Post by lisati on 2010-10-24
Do you have something else like Software Center or Update Manager open? If so, closing them should help.

---

### Post by jcoffey on 2010-10-24
I don't have anything else running that I know of. Would either of those run in the background, and if so a restart should clear this up? I apologize, I have several failed attempts of ubuntu installs on my MacBook and want to get this one right. I can't boot into osx anymore, but that's a different problem

---

### Post by SuaSwe on 2010-10-24
Afaik this error is normally caused by having Software Centre/Update Mgr running. If you run 'top' in Terminal, can you see 'apt' or any other suspicious processes in there? If you can't see anything telling, post the output here. :)

---

### Post by jcoffey on 2010-10-25
I will try that when i get home, im at work for the next 12 hours :(  Thanks for the quick replies though, sorry i cant be as prompt!

---

### Post by jcoffey on 2010-10-25
i will admit im not sure what i am looking for exactly, but this is the output of 'top'.

edit:  i looked a little closer at top for a while live, and I have no idea what whiptail is or why its using 100% of my processor?

---

### Post by sikander3786 on 2010-10-25
> **jcoffey said:**
> i will admit im not sure what i am looking for exactly, but this is the output of 'top'.

edit:  i looked a little closer at top for a while live, and I have no idea what whiptail is or why its using 100% of my processor?
It doesn't show anything that much informative.

If you are sure no other package managers are running, did you try a simple reboot?

---

### Post by jcoffey on 2010-10-26
the reboot worked.  Im sorry to have not tried it sooner, i have just been so busy with work lately.  any chance anyone can help with my other problem.  i tried booting into osx in verbose mode and the first time it hung up at airport: handshake with en1 or something close...then i tried again, and it got stuck at still waiting for root.  just prior i had to edit fstab in recovery mode.  i had been rebooting (hard boot) to get back in to osx to find out how to save to fstab when its write only.  i got it straightened out, booted into ubuntu to make sure it worked, then reset the PRAM (command option p and r) and then switched back to osx.  it froze at the boot screen so i did verbose to see why. thats when i got the errors.  if this isnt the place to ask for this kind of help, i apologize.

---

### Post by jcoffey on 2010-10-27
any ideas on not being able to boot into mac?  if i can boot from the cd, what would i do, just select the startup disk again?

---

### Post by sikander3786 on 2010-10-27
> **jcoffey said:**
> any ideas on not being able to boot into mac?  if i can boot from the cd, what would i do, just select the startup disk again?
It'd be better to ask this question in Apple Users sub forum.

---

