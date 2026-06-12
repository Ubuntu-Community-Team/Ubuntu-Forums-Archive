---
title: "laptop Wont come back from Sleep Or hibernate.. and my sound sucks"
date: 2009-10-19
forum: New to Ubuntu
---

### Post by R3fr4cti0n on 2009-10-19
i thought this was aproblem across the board but apparently its with certain hard wear, so i have a Hp tx2z not sure what to even look for to fix the problems with the crappy (low) sound and it not coming back from hibr or sleep any help would be GREAT
THANKS!

---

### Post by coldReactive on 2009-10-19
Did you press the power button when you wanted it to wake back up? Or a key?

---

### Post by fuzzyllama on 2009-10-19
You did not mention what version you are running, or what the problems you are experiencing actually are.

I too had issues with my HP not returning from hibernate and sketchy sound functionality with 8.04.  Upgrading to 9.04 solved my particular issues.  This may or not be the solution for you.  Please post more info :)

---

### Post by QIII on 2009-10-19
I see from your signature that you have a custom build, which may bear on the problem.
 
How much RAM do you have and how much have you set aside for your swap? Suspend is usually not an issue, since the RAM doesn't actually shut down.  Hibernate (often called "suspend to disk") may cause problems if the swap is smaller than the RAM.  The RAM state cannot be saved completely, causing issues.  (Windows dynamically allocates space for this.  That's a point for them.)

I'll do some research on the particular model and see if anything comes up with regard to Sleep and audio.

---

### Post by R3fr4cti0n on 2009-10-20
> **coldReactive said:**
> Did you press the power button when you wanted it to wake back up? Or a key? 

I flick the mouse pad and press keys

> **fuzzyllama said:**
> You did not mention what version you are running, or what the problems you are experiencing actually are.

I too had issues with my HP not returning from hibernate and sketchy sound functionality with 8.04.  Upgrading to 9.04 solved my particular issues.  This may or not be the solution for you.  Please post more info :)



I am using 9.04 and when ever i try to put the computer to sleep or into hibernate and retun to use it after i do that, it will not reurn for that sleep/hibernate state that i put it in. and my sound is very quite like i have the volume down low, no matter if i turn it up lound its still softer than, say, windows volume. you know what i mean?

> **QIII said:**
> I see from your signature that you have a custom build, which may bear on the problem.
 
How much RAM do you have and how much have you set aside for your swap? Suspend is usually not an issue, since the RAM doesn't actually shut down.  Hibernate (often called "suspend to disk") may cause problems if the swap is smaller than the RAM.  The RAM state cannot be saved completely, causing issues.  (Windows dynamically allocates space for this.  That's a point for them.)

I'll do some research on the particular model and see if anything comes up with regard to Sleep and audio.

The problem was there form the very first fresh install, and i only messed with gedit.conf so this leads me to believe that is has something to do with the kernals (or drivers) something that has been the from the start.

i am running 3 gigs of ram

thank you

---

### Post by R3fr4cti0n on 2009-10-20
Bump

---

### Post by nevets04 on 2009-10-20
This sometimes happens to me, I just turn it off and on a bunch of times till something shows up :)

---

### Post by Mike_IronFist on 2009-10-20
> **R3fr4cti0n said:**
> i thought this was aproblem across the board but apparently its with certain hard wear, so i have a Hp tx2z not sure what to even look for to fix the problems with the crappy (low) sound and it not coming back from hibr or sleep any help would be GREAT
THANKS!

If you're patient, the newest Ubuntu release, Karmic Koala, comes out in just 7 days. I had issues with suspending/hibernating in Jaunty myself, on my Compaq laptop - but I've been bug-testing/using Karmic for a little while now, and those issues have disappeared!

Just have a little patience, it may help. Wait a week, upgrade to Karmic when it comes out, and then come back if you still have problems.

---

### Post by flyerbrooks on 2009-10-20
I had the same low sound coming out of my latop using Jaunty 9.04 and i was able to fix it by selecting a different driver and speaker setup from the "volume control>preferences"

---

### Post by fuzzyllama on 2009-10-23
> **QIII said:**
> Hibernate (often called "suspend to disk") may cause problems if the swap is smaller than the RAM.  The RAM state cannot be saved completely, causing issues.  
 

Adding to what QIII said - it is strongly recommended to set the swap to 2x the size of the ram, or in your case:
      4GB ram x2 = **8GB** swap partition.

Here is a good doc that walks you through setting up and configuring your swap partition.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Try re-sizing to 8GB and let us know if it solves the issue...


As for the sound issue - What is the make and model of your sound card?  What make and model was detected by Ubuntu?  What driver is it using?  Is the problem across the board, or only certain apps?  Have you tried a different set of phones, or speakers?

---

