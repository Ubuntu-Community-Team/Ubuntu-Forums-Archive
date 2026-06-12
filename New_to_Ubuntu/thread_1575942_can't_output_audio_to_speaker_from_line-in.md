---
title: "can't output audio to speaker from line-in"
date: 2010-09-16
forum: New to Ubuntu
---

### Post by ReplicateThis on 2010-09-16
Hello!  I have two PCs side by side, and have recently tried to bail from the Micro$oft bandwagon and installed Ubuntu 10.04 Lucid on both machines.  For sound on my old WinXP setup, I had the sound output from PC 1 going to the line in of PC 2, then output to to the speakers, allowing me to "daisy-chain" the audio and hear both PCs.  I have read that this can cause some impendance issues and distortion, and reverses the left and right channels, but it has always worked well enough for my purposes.

When I realized this doesn't work out of the box, I looked it up on the forums, and found most folks pointing to ALSAmixer.  So I installed and fired it up, and it seems the line-in on the PC with the speakers is not muted or anything. (screenshot attached)

I've also seen that sending the sound through the network is an option, but to me it is not a good one as I also sometimes jack an electric guitar or bass through the line-in of the PC as well.

My question is what should I try next to get my PC to be able to output sound to the speakers from the line-in jack.

---

### Post by ReplicateThis on 2010-09-17
This is a shameless bump, as well as a wish to everyone to have a great Friday!

Still can't get sound to go from the first PC to the second, and the ALSA seetings seem good as far as I can tell.  This is what most "instructables" on the forum and google say to do, so I'm not sure if I'm doing something wrong?  Screenshot of the ALSA settings are in the post above...

Thanks, and TGIF! ):P

---

### Post by migs73 on 2010-09-17
Try putting ALSA on the other PC as well, and making sure the output is not muted.:)

---

### Post by ReplicateThis on 2010-09-17
I'll admit I whacked my self in the head for that - should've been a no brainer...  :rolleyes:

I've now installed ALSA on the PC without speakers.  Nothing is muted, but on checking with headphones, I still get no sound out of the line out port.  I am getting sound out of the speaker out port in my headphones, but when I try plugging the speaker out to line in on the other PC still no sound.

Is it possible something is muted that is not indicated by ALSA?

Thanks!

---

### Post by migs73 on 2010-09-17
Try looking under System--> Preferences --> Sound and click on the hardware and input/output tabs to see if everything looks in order. If your hardware is not listed, open a terminal (Applications --> Accessories --> Terminal) and type in;
```
lspci
```

That is a lowercase L at the beginning.

This will list (ls) the hardware on your PCI (pci) bus. Post the output from it here. 
After that I hope someone else cleverer than me can step in, because I'll be getting lost!!

---

