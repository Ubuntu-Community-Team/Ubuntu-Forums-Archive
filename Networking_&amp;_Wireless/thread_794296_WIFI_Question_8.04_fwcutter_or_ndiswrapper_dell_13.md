---
title: "WIFI Question 8.04 fwcutter or ndiswrapper dell 1390"
date: 2008-05-14
forum: Networking &amp; Wireless
---

### Post by Aaronb2245 on 2008-05-14
I just upgraded to 8.04, and the install used the fwcutter to set up my wireless. After the install I can see wireless networks however I can't connect to one. 

When I used fiesty I simply used ndiswrapper with the dell 1390 driver (my wifi card) and it worked flawlessly. My question is how do I get rid of what the installation did with the fwcutter so I can use ndiswrapper with the original driver from dell. My understanding is that the fwcutter installs the driver into the kernel rather than a module. If this is so can it still be black listed the way things can with ndiswrapper.

Before I go installing ndiswrapper and the driver I want to make sure I don't make a mess of things. 

Thanks Ppl
Aaron:guitar:

---

### Post by maclenin on 2008-05-14
Aaron:

I would take a peek at this [**post**]("http://ubuntuforums.org/showpost.php?p=4644002&postcount=373")...it might help you answer your question.

Good luck!

---

### Post by Aaronb2245 on 2008-05-14
> **maclenin said:**
> Aaron:

I would take a peek at this [**post**]("http://ubuntuforums.org/showpost.php?p=4644002&postcount=373")...it might help you answer your question.

Good luck!

I took a look at the post you linked for me, and I then blacklisted the mods the person blacklisted on that thread then I installed ndiswrapper and my driver however my card is simply not being recognized. This is wierd I've installed my wireless driver many times with ndiswrapper on 7.10 with no problems. I'm sure my problem has something to do with the fwcutter tool during the initial OS installation.

If anyone has any info on how to get ride of what was done on install to set up the wireless (fwcutter) please let me know. This is very frustrating.

Aaron:confused:

---

### Post by Aaronb2245 on 2008-05-15
> **Aaronb2245 said:**
> I took a look at the post you linked for me, and I then blacklisted the mods the person blacklisted on that thread then I installed ndiswrapper and my driver however my card is simply not being recognized. This is wierd I've installed my wireless driver many times with ndiswrapper on 7.10 with no problems. I'm sure my problem has something to do with the fwcutter tool during the initial OS installation.

If anyone has any info on how to get ride of what was done on install to set up the wireless (fwcutter) please let me know. This is very frustrating.

Aaron:confused:

FOUND SOLUTION:

To remove what was done on install "fwcutter" do this

sudo aptitude remove b43-fwcutter

Here is a link to where I found the solution to my problem and this link should work for anyone with a Broadcom card >> [http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

---

