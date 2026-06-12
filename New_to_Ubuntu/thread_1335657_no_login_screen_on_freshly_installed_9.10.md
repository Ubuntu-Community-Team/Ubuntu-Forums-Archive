---
title: "no login screen on freshly installed 9.10"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by swampranger on 2009-11-23
Hi Help, I recently installed ubuntu 9.10 
I get   ERROR: No such Device: bad2qa6d1-5111-433c-695b-dodb762a8790
Failed to boot default entries
 
 
What should I do? It all seems to be installed did everything right as far as I can tell.

---

### Post by Buuntu on 2009-11-23
Hmm weird, it seems to not be detecting your main device... Make sure you are booting to the correct hard drive in the BIOS first off.  Grub could be pointing to an incorrect device but since its a fresh install it's highly unlikely.  Does this error happen before or after you get to grub (the menu that lets you select which partition to boot off)?

---

### Post by swampranger on 2009-11-23
After Grub gives me  linux 2.6.31-14

---

### Post by wrgb2 on 2009-11-23
Try booting into command prompt in recovery mode.  Run the command:

sudo update-grub

and restart.  See if that helpss.

---

### Post by swampranger on 2009-11-23
I tried that not sure I did it right but it didn't help. I selected recovery mode hit enter then hit 'C then it goes back to the previous screen that give the options again?

---

### Post by lhb1142 on 2009-11-23
Do you happen to have TWO (or three) BIOS passwords enabled? I have an Acer Extensa 5620-6419 and its BIOS allows the use of three passwords: Supervisor, User, and Hard Drive.

I used all three when I was using 'Hardy' but when I upgraded to 'Intrepid' (8.10), the computer would not boot. I figured out that it was that Hard Drive password which was fouling things up so I disabled it.

I still have the other two passwords active - and the computer boots up fine. If you have some similar arrangement in your BIOS, try disabling it. Also click on the Restore Defaults in your BIOS; there may have been some inadvertent change which could be causing a problem.

Best of luck! ):P

---

### Post by swampranger on 2009-11-23
ok I'll give more info. I really don't know much of what I'm doing. Bios i'm only barely familiar with. Its my old HP NC 6000 I paid to have a new hard drive installed after the old one fried. I downloaded the UBUNTU 9.10 from the UBUNTU site burned it as instructed and installed it as instructed. It works when I use the do not change computer option. After install and removal of the CD I get the aforementioned issues. I think WRGB2 or Ihb1142 might be onto something if I knew how to do what they were telling me. I really am a beginner here.

---

### Post by wrgb2 on 2009-11-24
When you get the recovery mode menu, choose Drop to root shell command prompt with networking.  The type update-grub (you shouldn't need the sudo, sorry) and restart.

Edit: Sorry, I forgot 9.10 makes this easier - boot into recovery mode and choose Update Grub from the menu and restart.

---

### Post by coyotesx5 on 2009-11-24
I've been a Debian Linux user for 9 years and just installed a new WD 250 GB 2.5" form factor drive into my son's old Dell 9100 laptop, into which I am attempting to install Ubuntu.  It's Windows XP O/S was fried by a particularly vicious set of viruses masquerading as a demo antiviral program, so I decided to do a format on the drive and install Ubuntu 9.10.  Geez....and I was told the bugs were few and infrequent!

After a completely uneventful install, upon reboot here's what happens after the P.O.S.T.:

For 2 millisecs, a flash of GRUB, then the word "error".  Then...

"error:no such device: f94e64fe-fb0c-44ff-9638-3d5161d8f309

Failed to boot default entries

Press any key to continue."

So, do I assume that the coder(s) screwed up, or is Ubuntu 9.10 incompatible with
my old Dell 9100 laptop?  I do not see it listed in any    Compatibility list.

---

