---
title: "Linux server gone?!?!?!"
date: 2010-06-27
forum: New to Ubuntu
---

### Post by breeness on 2010-06-27
Hi I have been getting help all day from you nice folks and I just tried to reboot my server...
Then I got disconnected from it through my shell, so I went back to the original machine to try and ferret out the problem. There is nothing but a cursor on a blank, black screen!!

What happened?!

---

### Post by CharlesA on 2010-06-27
What was being done to it before the reboot?

---

### Post by Windows Nerd on 2010-06-27
We need more information, which is probably why there is no posts in response to an otherwise simple problem (or so it seems). Would you mind specifying:

What do you mean you were disconnected from your shell...do you mean you were SSHing into the sever and got disconnected by SSH at reboot?

Then you say that you try to go back to the original machine (I am assuming you mean your server by this) and fix the problem. You say that there is nothing but a cursor on a blank, blank screen...from this I think you are saying you attached a monitor to your server and tried to use it then., though I am not sure.

Did you boot the machine up after you had attached the monitor or before?

You are asking us "What happened!?", but when you are not being specific, we have no idea what happened either, and cannot help you troubleshoot the problem.

Scott

---

### Post by breeness on 2010-06-28
Sorry! I just was kinda like... WHAT?!?!?!?!


I was logged in through SSH on a different computer. I think I was trying to "find" the external HDD I had plugged into the linux box. I read someone on another post said they had to reboot their system to "see" the drive they installed, so I decided that might be my issue.

I typed sudo reboot. it said something like "rebooting NOW" and then it stayed that way for a very long time. After some more time, my ssh terminal said I'd been disconnected. I tried getting in again with the static IP, and no dice. I tried the other IP addresses it sometimes was assigned by the router, just in case, and it didnt seem to access it, so I went back to the linux box itself. It had restarted and all that I saw was the blank text cursor in the bottom.

After trying to type thinsg with no luck, I manually turned the computer off and on. I saw the familiar COMPAQ screen as it began turning on, but then nothing but the cursor :( I kinda gave up at that point and decided to go back to regular UBUNTU till I find a better solution.

Maybe I am just not ready for Linux command prompting :(

---

### Post by Windows Nerd on 2010-06-28
> **breeness said:**
> Sorry! I just was kinda like... WHAT?!?!?!?!


I was logged in through SSH on a different computer. I think I was trying to "find" the external HDD I had plugged into the linux box. I read someone on another post said they had to reboot their system to "see" the drive they installed, so I decided that might be my issue.

I typed sudo reboot. it said something like "rebooting NOW" and then it stayed that way for a very long time. After some more time, my ssh terminal said I'd been disconnected. I tried getting in again with the static IP, and no dice. I tried the other IP addresses it sometimes was assigned by the router, just in case, and it didnt seem to access it, so I went back to the linux box itself. It had restarted and all that I saw was the blank text cursor in the bottom.

After trying to type thinsg with no luck, I manually turned the computer off and on. I saw the familiar COMPAQ screen as it began turning on, but then nothing but the cursor :( I kinda gave up at that point and decided to go back to regular UBUNTU till I find a better solution.

Maybe I am just not ready for Linux command prompting :(
Your SSH session likely ended because you rebooted the computer.

Hmm can you boot a LiveCD of any sort?
By seeing the Compaq screen I am assuming the server gets past the BIOS...does GRUB (or whatever bootloader you are using) load at all?

Scott

---

