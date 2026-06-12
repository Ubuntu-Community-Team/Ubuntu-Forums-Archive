---
title: "Setting up wireless internet on my Dell D505 laptop"
date: 2007-07-15
forum: Networking &amp; Wireless
---

### Post by T.M.O.S on 2007-07-15
Im have  a lot of trouble setting up wireless internet on my Dell d505 latop, can someone please help. I just dont know where to start!!!

---

### Post by jw5801 on 2007-07-15
As a start type ```
lspci
``` and post the output so we can see what wireless card you have as the solution will depend entirely on this!

---

### Post by T.M.O.S on 2007-07-15
Sorry im a comlete n00b, where do i type this

---

### Post by jw5801 on 2007-07-15
No probs! You'll need to open up a "terminal" which can be found under Applications > Accessories > Terminal in your gnome menu. The command-line is an incredibly useful tool and you'll find you use it a lot in linux. It's really easy to use and generally just involves following other peoples posts/instructions! Might be a bit daunting at first (with all the commands people say to use that mean nothing), but you get used to it. All you have to do is ask if you're wondering what a command does or how to use it. The one I gave you above simply lists a bunch of your hardware (video cards, sound cards ethernet cards etc). We'll be looking for something that says either Ethernet controller, or Network controller to see what wireless card your laptop has.

---

