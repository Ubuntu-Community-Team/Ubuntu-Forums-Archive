---
title: "Video card problems, how to test vram, etc"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by Hospadar on 2009-04-30
I've been having some very strange problems lately.  When I boot up ubuntu (jaunty), after about a minute, the screen will start to flash in a seizure-inducing fashion and very soon after the mouse will stop working.  I thought, bummer, I'll try a re-install.  I have a separate home partition and I don't mind doing it, so often it's a lot less hassle than troubleshooting.

I burned a fresh copy of kubuntu (I've been meaning to try it anyways, and just on the off chance it was a gnome probem, I thought it would be a good idea)

Basically the same issue, but instead of seizure inducing flashes, there were flickering horizontal lines, after a couple minutes only the mouse worked, then shortly after, that stopped working as well.

The odd part is, I pressed the power button (not long enough to force a shutdown, but in the way where it would normally bring up the shutdown menu), and I could hear the livecd spin up, and after a little while (about as long as it takes to boot down) the cd popped out, as if it had successfully booted down (although the display still showed the same frozen kubuntu desktop until I held down the power button long enough for the machine to shut off)

If I never go into X,  (for example boot in recovery mode and drop to root terminal), text mode will basically work fine, but even there, some of the characters will flash other characters.

Bottom line, to me, this sounds like hardware failure.  I'm running a memtest right now, and will leave it running all night, so if that turns out to be the culprit, great.  I'm wondering if there are ways to test video memory or other components.  What log files should I be looking in to attempt to figure out what is failing?  This is a laptop so I can't really remove any parts and see if the problem goes away.

I will probably also try installing an ssh server, and then see if I can ssh into the machine after a crash (which would certainly indicate a video problem)

Just wondering if anyone has had problems like this and if they ever figured out what was up.

Also, it's an Nvidia 8400M GS in a dell lappy

---

