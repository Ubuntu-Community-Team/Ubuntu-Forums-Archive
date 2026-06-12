---
title: "I can't access a share on my XP box from my Ubuntu box"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by y0diggity on 2008-04-26
Hi folks! I've been searching high and low via this forum as well as Google and have not come up with anything that has helped me with this. I know it's got to be something simple since every other problem I've had with Ubuntu has had a simple solution that I've found by searching for it, particularly on this forum. You guys are all so great when it comes to helping us newcomers!

So now for my  problem:
[LIST]I have a laptop running Ubuntu 7.10 that dual boots to XP (although I doubt that's relevant). I also have a PC that runs XP.[/list]
[LIST]
[*]The XP PC has several shared folders and drives. These are accessible to my XP partition on my laptop without any problems and always have been.
[/LIST]
[LIST]
[*]The Ubuntu also has a shared folder that the XP PC can access without any problems.
[/LIST]
[LIST]
[*]Ping works both ways.
[/LIST]
[LIST]
[*]On the Ubuntu laptop, the "smbtree" command produces a list of the entire network. All computers and shares are there and accuratae.
[/LIST]
[list]In the Places-->Network menu it shows the network, then the pc's. When I click on the icon for the "Basement" pc, the cursor spins for a while then it pops up a dialog box that says "The folder contents could not be displayed." Beneath that it says "Sorry, couldn't display all the contents of "Windows Network: basement"."[/list]

As I said, I'm new to this. I used to be a Redhat user (a veeeery long time ago), but as with everything, if you don't use it lose it. I don't remember the vast majority of things that I used to know so I'm really starting over.

Thanks for all the help you provide to us beginners here on these forums. Your patience is appreciated.

---

### Post by Monicker on 2008-04-26
I've seen that my wife's XP machine does not always show up in Places->Network.

Try Places->Connect to Server, Select Windows Share, then enter the ip/hostname and the share name.  That should work.  If the share has no security restrictions just leave the password blank.

---

### Post by y0diggity on 2008-04-26
That worked! I have honestly spent hours researching this issue and I've read about seriously lengthy processes that never worked. I knew it would be something simple. It even mounts it automatically on startup! Excellent! Thanks so much, I appreciate it.

---

