---
title: "Amilo 1650 Wireless Button Problems"
date: 2007-11-26
forum: Networking &amp; Wireless
---

### Post by sharpycore on 2007-11-26
Hi,
After a long search through the forums, I've managed to get the drivers working for the Broadcom 4318 in my FSC Amilo 1650 (note, NOT Amilo 1650g). However, the hardware button to turn the wireless card on/off is a bit of a stumbling block. There are solutions for the Atheros card that come with the Amilo 1650g but nothing comparible for the Broadcom card that comes with the 1650.
I'm running Gutsy, 64bit and have the drivers running using ndiswrapper, I just can't come up with a way to coax the hardware button into working. I've checked and there are no such options in the BIOS or any updated BIOS on the FSC website that would allow such a thing.
This is my first time round with Ubuntu and I'm getting the hang of things but neither google or the forum search has any way to solve this.
Thanks,
Tom

---

### Post by sharpycore on 2007-11-27
After some more searching, I have solved this and I am posting from ubuntu! So, some slightly tricky steps...

1: Turn off, disconnect the power and get yourself a small screwdriver, some scissors and some tape. Make sure to earth yourself before opening the computer.
2: Open the larger of the two removable panels in the bottom of the laptop. The wireless card should be labelled and if not, it's the little card nearest to you if you have the fan at the top right.
3: Push the clips holding it in sideways and it'll pop it out. Take it out being careful not to tug on the other wires attaching it to the board.
4: Look top down at the card, the same way round and way up as it came out. Count along the pins left to right from the little notch you find on the side that plugs into the motherboard.
5: Mask off the 6th and 7th pin with the tape (again, counting left to right). It's tricky to do but not too hard,
6: Put the card back in, and providing your drivers are all installed the card should just work without the hardware switch (although the light won't come on).

Boom.

---

### Post by afuchi on 2007-12-14
I have same laptop and it's been a kind of head ache to get wifi working with linux.
Tryng to do that about 6 months now.
Still..that sounds interesting..have to try it when i finish my workingtay at night :P
Lets hope the best!
Anyone else tryed that?

---

