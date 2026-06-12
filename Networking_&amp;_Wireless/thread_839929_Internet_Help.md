---
title: "Internet Help"
date: 2008-06-24
forum: Networking &amp; Wireless
---

### Post by dobroschi on 2008-06-24
Hello fellow Buntu`ers ... WARNING AND SORRY... my issue is in windows but isnt limited to it. I have At n t  yahoo dsl cable internet... and in windows when i ctrl+alt+delete and go to the networking pane...  it says local area connection ... Netowrk Utilization: always stays under 1 PERCENT ... this irritates me a lot and makes me Believe that this is why my bitcomet and http downlaods are so damn slow... (varying around 50kb - 170kb AT MAXIMUM) and come to say that when i bought the ATT yahoo subscription it said 75- kbps or something... is there any way to increase the networking usage??? i feel like killing myself with this internet now since i discovered this. :confused: ... and also when i look at my bitcomet peers... theyr liek downloading with like 600kbps-6MBps ... and im downlaoding at 60kbps ... not cool HELP

SORRY FOR NOT HAVING TO DO  WITH UBUNTU BUT IM NOT FAMILAIR WITH FORUMS AND DONT LIKE TO REGISTER TO OTHER FORUMS BECAUSE IT COULDHAVE TOOK TO MUCH TIME... AND I NEEDED TO RELEAVE MY FEELINGS lol... thanx and sorry

---

### Post by dmizer on 2008-06-25
> **dobroschi said:**
> Hello fellow Buntu`ers ... WARNING AND SORRY... my issue is in windows but isnt limited to it. I have At n t  yahoo dsl cable internet... and in windows when i ctrl+alt+delete and go to the networking pane...  it says local area connection ... Netowrk Utilization: always stays under 1 PERCENT ... this irritates me a lot and makes me Believe that this is why my bitcomet and http downlaods are so damn slow... (varying around 50kb - 170kb AT MAXIMUM) and come to say that when i bought the ATT yahoo subscription it said 75- kbps or something... is there any way to increase the networking usage??? i feel like killing myself with this internet now since i discovered this. :confused: ... and also when i look at my bitcomet peers... theyr liek downloading with like 600kbps-6MBps ... and im downlaoding at 60kbps ... not cool HELP

SORRY FOR NOT HAVING TO DO  WITH UBUNTU BUT IM NOT FAMILAIR WITH FORUMS AND DONT LIKE TO REGISTER TO OTHER FORUMS BECAUSE IT COULDHAVE TOOK TO MUCH TIME... AND I NEEDED TO RELEAVE MY FEELINGS lol... thanx and sorry

short answer: i don't think you have a problem.

long answer: i suspect you're looking at a collective download speed in bittorrent.  sometimes i can get over 100kbps, but only on stuff like an ubuntu iso where there are loads of super high speed seeds.  60kbps and lower is much more common, but of course it all depends on the speed of your peers, and how many peers you're connected to.

as for your network usage, you're looking at the difference in speed between your network card, and your broadband modem.  your network card can handle way more speed than your broadband modem can process, so you get low network usage percentages.  this would increase if you had lots of computers on your local network all swapping files internally.

here's more information: [http://www.homenethelp.com/web/explain/about-network-speeds.asp](http://www.homenethelp.com/web/explain/about-network-speeds.asp) so, since your network adapter is capable of 100Mbps, and your broadband modem is only capable of 75kbps, you're getting less than 1% of your network adapter's total capacity (about 102400 Kbps).

---

