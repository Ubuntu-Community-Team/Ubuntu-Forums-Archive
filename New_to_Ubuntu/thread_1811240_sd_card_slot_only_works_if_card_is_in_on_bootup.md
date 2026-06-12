---
title: "sd card slot only works if card is in on bootup"
date: 2011-07-24
forum: New to Ubuntu
---

### Post by CaptainMark on 2011-07-24
I've just installed 11.04  on my mums laptop, it went relatively problem free, one small hitch is that the SD card reader will not work unless a card is in when the laptop is turned on. If its powered up normally then it seems the card slot is not configured at all as fdisk -l doesn't even detect the card,  but when a card is in at boot it works normally so its not a driver being incompatible

It's a dell laptop. Has anyone heard of this issue before

---

### Post by amjjawad on 2011-07-24
> **CaptainMark said:**
> I've just installed 11.04  on my mums laptop, it went relatively problem free, one small hitch is that the SD card reader will not work unless a card is in when the laptop is turned on. If its powered up normally then it seems the card slot is not configured at all as fdisk -l doesn't even detect the card,  but when a card is in at boot it works normally so its not a driver being incompatible

It's a dell laptop. Has anyone heard of this issue before

Where is the problem? I can't see any :)

If you have an USB Drive in your hand that is not even plugged in. If your machine won't recognize it, do you call this an error or a problem?
As long as it works when you insert the Card, then it's fine :)

Hope I did not misunderstand your post ;)

---

### Post by Rex Bouwense on 2011-07-24
Hey Captain, try running Gparted when you insert the SD card into the reader to see if it recognizes it.  Perhaps it is not mounting automatically.  I have a Dell and it does strange things sometimes.

---

### Post by dcsoldschool53 on 2011-07-24
No, I have never heard of this issue before, but with Natty, anything is possible. Have you tried to sudo mount the card folder when it is not working, or put it in fstab.

---

### Post by CaptainMark on 2011-07-24
Yes you have completely mis read my post, i don't expect it to be detected until I plug it in but when I do nothing happens. It has to be in when the laptop is 'powered up' as in it has it has to be present during the act of booting the machine. Not fdisk or g parted pick it up and I cant give it an fstab entry with a device identifier,

---

### Post by Jacobonbuntu on 2011-07-24
> **dcsoldschool53 said:**
> No, I have never heard of this issue before, but with Natty, anything is possible. Have you tried to sudo mount the card folder when it is not working, or put it in fstab.
...putting in fstab is probably not a good idea, as you will get error messages on startup if the card is not present...

---

### Post by Jacobonbuntu on 2011-07-24
> **CaptainMark said:**
> Yes you have completely mis read my post, i don't expect it to be detected until I plug it in but when I do nothing happens. It has to be in when the laptop is 'powered up' as in it has it has to be present during the act of booting the machine. Not fdisk or g parted pick it up and I cant give it an fstab entry with a device identifier,

did you already install all updates? I had something like this with (only) one of my WD usb drives. the proble was gone after the updates.

---

### Post by amjjawad on 2011-07-24
> **CaptainMark said:**
> Yes you have completely mis read my post, i don't expect it to be detected until I plug it in but when I do nothing happens. It has to be in when the laptop is 'powered up' as in it has it has to be present during the act of booting the machine. Not fdisk or g parted pick it up and I cant give it an fstab entry with a device identifier,

In another words ... it will NOT be detected UNLESS you Plug it, turn your machine ON. Otherwise, no matter what, it's not detected.

Am I right?

Sorry, but it was NOT clear at the beginning!

---

### Post by CaptainMark on 2011-07-24
sorry, i was trying to word it correctly but this is right, it has to be inserted while the machine is off and then switched on to be functional, else it will not even be detected. ive found a launchpad bug report for it [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/763495](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/763495)

---

### Post by amjjawad on 2011-07-24
> **CaptainMark said:**
> sorry, i was trying to word it correctly but this is right, it has to be inserted while the machine is off and then switched on to be functional, else it will not even be detected. ive found a launchpad bug report for it [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/763495](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/763495)

It's ok ... it happens ;)

Well, I've been through TONS of issue with this 11.04 and I'm not surprised if this is yet another issue. Oh well!


I'll have a look at the link you provided.

Currently, I have nothing in mind but hope someone else does :)

---

### Post by amjjawad on 2011-07-24
So, it's confirmed ... I see :)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/763495](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/763495)

Is it a Fresh Installation? I'm not going to suggest to go back to 10.04.3 but I guess eventually, I'll do it :D

---

### Post by westie457 on 2011-07-24
Hi could you run ```
lspci
``` in a terminal twice. Once booting with the card in and once booting without the card. Then paste the output in a new reply for each clicking on the # menu bar and pasting between the CODE tags. Hopefully this will tell us something about your hardware.

---

### Post by CaptainMark on 2011-07-24
i can maybe try tomorrow, im due to go round for dinner but they expect you to talk at least a bit when you visit dont they,
i know.... mums!!! :P

---

### Post by amjjawad on 2011-07-24
> **CaptainMark said:**
> i can maybe try tomorrow, im due to go round for dinner but they expect you to talk at least a bit when you visit dont they,
i know.... mums!!! :P

Just go for your dinner and forget Ubuntu now ;)

We will be waiting for you :)

Have a great one!

---

### Post by CaptainMark on 2011-07-24
urm, im too far gone, linux is permanently present in my head, its fused too deep to remove

---

### Post by amjjawad on 2011-07-24
> **CaptainMark said:**
> urm, im too far gone, linux is permanently present in my head, its fused too deep to remove

TELL ME about it :D

---

### Post by Jacobonbuntu on 2011-07-24
> **CaptainMark said:**
> urm, im too far gone, linux is permanently present in my head, its fused too deep to remove


.....I read in a post today, someone has had 3 computer "crushes" in 4 years time :)
I am curious who he is having dinner with...

---

### Post by amjjawad on 2011-07-24
> **Jacobonbuntu said:**
> .....I read in a post today, someone has had 3 computer "crushes" in 4 years time :)
I am curious who he is having dinner with...

Oh no, not again?! LOL :D

---

### Post by westie457 on 2011-07-25
> **CaptainMark said:**
> i can maybe try tomorrow, im due to go round for dinner but they expect you to talk at least a bit when you visit dont they,
i know.... mums!!! :P

We have a solution that should work. Do we give it to you now or leave it until after dinner at your mums.

Just kidding. :lolflag:
 We could go through the whole process of diagnostics to check various things and wasting time until it goes right or you could do this > First, for the SD card reader there are a few posts floating about point out that it only works if the card is inserted at boot time. There is a fix to this ([http://ubuntuforums.org/showthread.php?t=1309991](http://ubuntuforums.org/showthread.php?t=1309991)) that worked for me (Dell L501X, Kubuntu 10.10), basically add "pciehp.pciehp_force=1" to your kernel arguments. 
e.g. sudo nedit /etc/default/grub ; then add the line above to the end of of "GRB_CMDLINE_LINUX_DEFAULT" string, then "sudo update-grub" -- this shoudl fix your SD card.


Enjoy your dinner, do the above. Shout out HOORAY it works. Then mark this as solved please.

---

### Post by CaptainMark on 2011-07-25
i plan on trying that script tonight ive got it all saved on usb ready to go

---

### Post by amjjawad on 2011-07-25
> **CaptainMark said:**
> i plan on trying that script tonight ive got it all saved on usb ready to go

We'll be waiting for your feedback ;)

---

### Post by CaptainMark on 2011-07-26
i didnt get a chance to go round in the end but i can tell you that i emailed the script to my brother who put it in place and the script works fine, its a work around but hopefully the bug report gets actioned upstream, i dont hold out much hope as there are so many bug reports on launchpad not going anywhere, makes me wish i had the knowledge to code well enough to do something about it

---

### Post by amjjawad on 2011-07-26
> **CaptainMark said:**
> i didnt get a chance to go round in the end but i can tell you that i emailed the script to my brother who put it in place and the script works fine, its a work around but hopefully the bug report gets actioned upstream, i dont hold out much hope as there are so many bug reports on launchpad not going anywhere, makes me wish i had the knowledge to code well enough to do something about it

At least something worked :)

NO OS is perfect so we need to live with that fact and understand it :)

---

