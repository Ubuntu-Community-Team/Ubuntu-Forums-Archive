---
title: "What files are in what repositories?"
date: 2010-03-27
forum: New to Ubuntu
---

### Post by slughappy1 on 2010-03-27
I have added several ppa repos and I would like to see then individually. Is there a way to search through just one repo at a time, and not just a list of all ppa repos in Synaptic?

---

### Post by Silent Warrior on 2010-03-27
I don't know how it's set up in Ubuntu - using Mint 8 at the moment - but in Mint 8's Synaptic there is a filter set to list packages by origin. I take it this is what you're looking for?

Hm, or maybe not - I have a few PPAs enabled myself, but they're not separated; all listed as originating from launchpad.net (imagine that).
One thing you COULD do - which would be quite a lot of bother - is to open the repository-GUI and untick every repository except the one you want to inspect, then Reload. You'll have to set everything back properly when you're done, though. A bit of a snag.

---

### Post by slughappy1 on 2010-03-27
That's where I first went and realized that they are all clumped together.

---

### Post by drs305 on 2010-03-27
You can open Synaptic. In the left pane, select *Origin*, then in the top left pane select the repository you wish to explore. I don't currently have any ppa's enabled but I would not expect them to be all listed as one entry.

---

### Post by slughappy1 on 2010-03-27
They are listed as [LIST=1]
[*]ppa.launchpad.net/main
[*]ppa.launchpad.net/universe
[/LIST] So yes they are clumped together, which is NOT what I want.

---

### Post by drs305 on 2010-03-27
> **slughappy1 said:**
> They are listed as [LIST=1]
[*]ppa.launchpad.net/main
[*]ppa.launchpad.net/universe
[/LIST]. So yes they are clumped together.

They may be listed one after the other, but from your list they are shown independent of one another. 

If you click on one, you should see the contents of that repository only (for instance, what is in ppa.launchpad.net/main). You shouldn't be able to select more than one listing in the upper left pane so you should see the contents of one repository section at a time (free, non-free, main, restricted, universe, multiverse, etc).

---

