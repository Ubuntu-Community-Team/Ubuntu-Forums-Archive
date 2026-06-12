---
title: "Wireless card locking up laptop?"
date: 2006-07-26
forum: Networking &amp; Wireless
---

### Post by Vandrissen on 2006-07-26
Hey there everyone. I'd first like to introduce myself as a newly converted XP -> Ubuntu 6.06 user.

I think I'm doing pretty well so far. I was able to get my wireless card to work for a little while, but then something happened. A bit of background first though, so you'll understand what happened and can better help.

I had my laptop on and put in my PCMCIA wireless card into the respective slot and while it did show up in the administration - > networking application, it didn't show up as a selectable option under the connection properties. (Yes, it was activated.)

So I went to the connection name box in the connection properties and just typed in the right name for the card (ra0). It showed up and worked fine.

Then later on I took the card out of the laptop and turned the laptop off. While in the shutoff process, the part about closing down the network stuff, it froze up and stopped shutting down. I left it alone for a while and then it went to a text based looking screen and continued to just sit there.

Then I hit the power button and turned it off manually. Heres where the problems come in.

I start the computer later on with the wireless card already in, and it freezes during the network adapter part again. So I shut it off and turn it on without the card in and it works. Once Ubuntu opens though I put the card back in and try to do stuff. Nothing works though, its not frozen... but whatever application I try to open just doesn't open. If I remove the card again nothing goes back to working.

I've also gone back to the connection properties (after restarting with no card) and taken it off ra0 and put it on to eth0. Same problem happens when I try to put the wireless card in. The eth0 works though, and its what I'm using right now.

So, anyone have ideas? Thanks for reading, and any help would be much appreciated.

---

### Post by joes_meat on 2006-07-26
I have the exact same problem! I'm at my wits end trying to fix this.

My card is a Dlink G630 rev e. It has the RT61 chipset.

The funny thing is - it worked fine on the live CD.

---

### Post by joes_meat on 2006-07-26
Could it be an IRQ problem?

---

### Post by joes_meat on 2006-07-27
I ended up fixing it by re-installing Ubuntu.

Must have had a glitch on the first install.

Sorry I can't help your problem.

---

### Post by Vandrissen on 2006-07-27
Thanks for the help joes_meat, I've considered a reinstall, but wanted to see if there was something else I could do first.

If I can't get any help then thats what I'll resort to doing.

Also, is this really the right subforum for this, or is there a better place I could ask about it?

---

