---
title: "New Install Decided to Lock Up"
date: 2011-01-25
forum: New to Ubuntu
---

### Post by Elaphae on 2011-01-25
Briefly: Just built computer. New HDD, Mobo about a year old. Partitioned the disk into 3 sections and installed XP pro on one. Worked fine, no problems for 2 days. Tried installing Ubuntu from USB and CD - failed. I then installed direct from the site. Ubuntu installed to second partition. (Install USB and CD made on the Apple G4 I am using now, I did check the Windows option when making them).

Worked fine and I was getting the hang of it. Booted and rebooted several times and was always given the choice of which OS to use.

I noticed a window telling me that there were a number of files I needed to update so, I updated. Got to Grub and as I read it the powers that be wanted me to install it as well so I did.

Rebooted.
Now I get some info from my BIOS (same as usually) followed by the message:
error: no such device: 57962db2-1ade-4bf6-bb27-d481c6da68d0.
grub rescue>

Suggestions? Help? There is no data on the computer as yet and no programs other than what came with the install and Skype. As a last resort I can try and reformat the drive but would rather not if it can be avoided.

---

### Post by Quackers on 2011-01-25
May be worth having a look here, if you used wubi
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by Elaphae on 2011-01-25
On the way to the link now. Is WUBI the Ubuntu Windows installer? I'll read the thread anyway, new with Ububtu and need all the knowledge I can get.

---

### Post by Elaphae on 2011-01-25
Yes, that is what I needed, thanks Quackers. (Now if I can understand what to do... LOL)

---

### Post by Quackers on 2011-01-25
All the details are there. Just take your time and double check things. You'll be fine :wink:

---

### Post by Elaphae on 2011-02-02
It worked fine. hen I was forced not to use the computer for a few days due to an injury. Started it up today and updated windows drivers - no problems. Restarted a couple of times in Windows (XP) with no problem. Got ambitious and decided to see if I can install play WoW on ubuntu - booted fine into Ubuntu.

I checked and there were updates suggested for ubuntu (69 in all) so I installed them. I had forgotten that THIS is what had caused the original problem. On restart I get the same error message re: root grub. I looked at the suggestions made (THAT WORKED THE LAST WEEK) and discovered that 1 my XP cd never loads and 2 my live cd for ubuntu seems to  get stuck on the load screen (blue, "ubuntu and f dots that go from white to red.

I would like to fix this again but cannot see how, need help.

Also I looked at several other threads concerning this root grub problem and see much conflicting data. Once you folks help me fix this I would like to put up a web page offering 1 - prevention of getting into this if possible and 2 the method to fix the problem. I provide web hosting and would love to donate the space to keep others from (what for me has been) hours of frustration.

So, at this point I cannot boo into anything but the BIOS screen. XP cd now does not show up, ubuntu cd seems to lock on start. I have high blood pessure that is climbing. Need help to fix this again. I have about 6 hours exp with unbuntu, 5 of which involve trying to figure out boot grub...

---

### Post by Elaphae on 2011-02-02
Just found out that the 'Home, page p, end, delete'' keys and they seem to toggle from the locked up start screen to a screen with data, now way to copy and paste it but it ends with:  rm: cannot stat '/root/ect/init/huclock-save.comf':Input/output error

---

### Post by Quackers on 2011-02-02
Sorry about your problems, but I am not a wubi expert at all. I can only direct you to the same thread as before. As the problem seems to be post-update related there may be other people having the same problem.
Regarding the cd's not booting, have you changed the bios settings to make the cd drive the first boot option?

---

### Post by Elaphae on 2011-02-02
I'll double check that the cd is set for boot - I think it is but never mind double checking.

I saw several new threads regarding the grub rescue boot problem. My main concern is that till I figure it out the new computer is useless.

---

