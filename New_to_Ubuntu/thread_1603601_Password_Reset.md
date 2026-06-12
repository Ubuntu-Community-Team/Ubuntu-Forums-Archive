---
title: "Password Reset"
date: 2010-10-22
forum: New to Ubuntu
---

### Post by daoki82 on 2010-10-22
Hey guys. How do you reset your password? More specifically, what do you do if you for some reason forgot your password, and therefore are unable to do anything administrative-related on the system. I use the SAME password for everything that requires a password, but for whatever reason it's not recognized on my netbook. I feel like a complete idiot, but if anyone can help me I'd greatly appreciate it.

Thanks!

---

### Post by JustinR on 2010-10-22
> **daoki82 said:**
> Hey guys. How do you reset your password? More specifically, what do you do if you for some reason forgot your password, and therefore are unable to do anything administrative-related on the system. I use the SAME password for everything that requires a password, but for whatever reason it's not recognized on my netbook. I feel like a complete idiot, but if anyone can help me I'd greatly appreciate it.

Thanks!

Hi,
Restart your computer and go to the grub menu - if you restart and it doesn't show, restart again but press and hold the 'Shift' key down until it appears. Scroll down to the second option with the arrow keys, (Recovery Mode). Once it finishes loading to a blue window - go to 'Root' and press 'Enter'

Then type in 'passwd USERNAME' and type in your new password. Type Exit and click 'Resume Normal Boot'

---

### Post by daoki82 on 2010-10-22
> **JustinR said:**
> Hi,
Restart your computer and go to the grub menu - if you restart and it doesn't show, restart again but press and hold the 'Shift' key down until it appears. Scroll down to the second option with the arrow keys, (Recovery Mode). Once it finishes loading to a blue window - go to 'Root' and press 'Enter'

Then type in 'passwd USERNAME' and type in your new password. Type Exit and click 'Resume Normal Boot'

When I hold down shift, it goes from the Dell start up screen (where you can press 0 or 2 for set up options), to a single line of text as follows..

MBR 2FA:

I can't type anything in, but can only hit enter, which then starts up Ubuntu. Am I doing something wrong?

---

### Post by JustinR on 2010-10-22
> **daoki82 said:**
> When I hold down shift, it goes from the Dell start up screen (where you can press 0 or 2 for set up options), to a single line of text as follows..

MBR 2FA:

I can't type anything in, but can only hit enter, which then starts up Ubuntu. Am I doing something wrong?

Okay, I guess you can try pressing and holding 'Shift' after the Dell Logo disappears.

---

### Post by daoki82 on 2010-10-22
OK, that's not working. Any other suggestions?

---

### Post by JustinR on 2010-10-22
> **daoki82 said:**
> OK, that's not working. Any other suggestions?

Yes, so you aren't seeing the grub menu anyways on boot up?

---

### Post by Sef on 2010-10-22
Read Psychocats: [How to Reset your Password in Ubuntu.]("http://psychocats.net/ubuntu/resetpassword")

---

### Post by daoki82 on 2010-10-22
> **JustinR said:**
> Yes, so you aren't seeing the grub menu anyways on boot up?
No, upon turning it on, it goes directly to session under anonymous user. Tapping shift anytime prior to the ubuntu logo appearing takes me to this blank screen with MBR 2FA: 

I previously had added a 2nd user on for personal use, but everytime I turned on, it started under anonymous, and I'd have to switch user to use it. Then, upon updating, my firefox stopped working, so I deleted the other user completely, leaving anonymous, since its the first thing it logs into anyway. I did buy this from someone who installed both ubuntu and upgraded the hard drive space and such, so does this sound like an improper set up? I only spent like 180 for it, so if it sounds screwy I can just scrap it.. It's turning into a headache.

---

### Post by JustinR on 2010-10-22
> **daoki82 said:**
> No, upon turning it on, it goes directly to session under anonymous user. Tapping shift anytime prior to the ubuntu logo appearing takes me to this blank screen with MBR 2FA: 

I previously had added a 2nd user on for personal use, but everytime I turned on, it started under anonymous, and I'd have to switch user to use it. Then, upon updating, my firefox stopped working, so I deleted the other user completely, leaving anonymous, since its the first thing it logs into anyway. I did buy this from someone who installed both ubuntu and upgraded the hard drive space and such, so does this sound like an improper set up? I only spent like 180 for it, so if it sounds screwy I can just scrap it.. It's turning into a headache.

You can reinstall if you like - but we can continue if you want.
I would suggest following the PsychoCat Tutorial link posted above - if shows you how to reset your password, even if you can't get to your GRUB Screen. It requires an Ubuntu Live CD - if you need any help we're still here!

---

