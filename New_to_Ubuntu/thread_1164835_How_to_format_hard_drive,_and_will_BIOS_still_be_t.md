---
title: "How to format hard drive, and will BIOS still be there?"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by Zachx65 on 2009-05-20
I just bought a new laptop from Best Buy a couple days ago. When I got it I wiped Windows and installed Jaunty. Now I'm not so sure I want this laptop, and would like to return it. Problem is I don't have a Windows recovery CD, and am not sure if they'll take it back the way it is, if they did I'd have to pay at least the 15% restocking fee. I was thinking of removing Jaunty, so when it boots there's no OS to load. I could say it was defective, get them to take it back and hopefully avoid a fee.

I'm wondering how to format it like that, and if the BIOS will still be there. I figure if they don't take it back I could just pop the Ubuntu CD and tell it to boot from the CD drive. Any ideas?

I know I'm an idiot for not making a recovery disc when I first got it. Thanks...

---

### Post by Game Over on 2009-05-20
Maybe just remove Jaunty and take it back... 

"Uh... this thing is not working. Can I get my money back?"

---

### Post by NikoC on 2009-05-20
This might work:
Pop in ubuntu live cd, boot from it
Start 'gparted' via ALT + F2 and entering 'gksudo gparted'
This will allow you to reformat your harddrive.

BIOS settings will remain untouched!

edit: you could also download and burn the gparted livecd which is available at: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by pastalavista on 2009-05-20
If you want to return it, you could borrow someone's Windows Install disk but enter your own user authorization code, which should be on a sticker somewhere, usually the bottom of the laptop. You'd still have to download some drivers, probably.

---

### Post by cbanakis on 2009-05-20
First, the computer should have came with recovery disks, if it didn't thats not your problem.
whether you have Ubunto Windows or nothing on it should not matter either.
as long as your within the time frame for the return policy, you wont have any issues if you just bring it back as is.

If they are going to charge you a restocking fee is kind of a coin toss.

Everyone who works there is authorized to waive the restocking fee, so if your persistent it not wanting to pay it, they will most likely waive it for you.

Just tell them the battery doesnt last as long as advertised and your not happy with it.

There is not a laptop on the planet that lasts as long as advertised, so thats as good a reason as any.

Whatever software or lack there of they find on the computer should not matter at all.

And no, the bios is stored on a chip in the computer, not on the hard drive.

You would have to learn how to erase the bios, and then you would need to go out of your way and do it on purpose, it cannot happen by mistake.

---

### Post by pastalavista on 2009-05-20
> **cbanakis said:**
> First, the computer should have came with recovery disks, if it didn't thats not your problem.
whether you have Ubunto Windows or nothing on it should not matter either.
as long as your within the time frame for the return policy, you wont have any issues if you just bring it back as is.

If they are going to charge you a restocking fee is kind of a coin toss...



Most lower priced PC's only come with a recovery partition and some have particular warranty exlusions because of the nature of the deal. You get what you pay for. The OP "wiped" his hard drive before considering what he was wiping, which was not only his installation of Windows, but also the partition that contained the factory restore data.

---

### Post by cbanakis on 2009-05-20
I forgot about that, either way it shouldnt really matter.

I am sure that the inhouse Geeksquad has recovery disks, and they no doubt have a bench setup for them to reinstall OS's on returned computers all day long

---

### Post by ainsworth_t on 2009-05-20
If you want to wipe the hard drive, try using Darik's Boot and Nuke ([http://www.dban.org](http://www.dban.org)). No need to worry about the BIOS, it's stored in ROM on the motherboard.

---

### Post by Zachx65 on 2009-05-20
Thank you all for the replies. I really appreciate it. ):P

---

