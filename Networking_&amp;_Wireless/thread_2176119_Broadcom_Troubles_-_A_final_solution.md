---
title: "Broadcom Troubles - A final solution"
date: 2013-09-22
forum: Networking &amp; Wireless
---

### Post by Linux-sgt on 2013-09-22
Hello all. Firstly, I just want to say that this is not another broadcom complaint - there are already numerous threads to deal with that. Secondly, this story is meant to help others find a quick and easy solution to their problem.

I recently grabbed a used laptop to replace my old Dell laptop. I found a quite acceptable HP Elitebook 8750p, 2.8Ghz proc, threw in 16GB RAM, and figured I would be peachy to set up my Fedora/Ubuntu/Windows machine. I primarily use Ubuntu of course. I had no Idea that I was about to jump into the pits of hell for the next 12 hours. 

I threw in my bootable USB to start the process, and figured I'd begin with Ubuntu. When I began the install, I was surprised to see the wireless was unresponsive, but continued offline anyway. After the install, I still had no access to wireless. Turns out, I had a Broadcom 43228 chip inside... I hardwired and tried to install the STA driver update. System failure (running 12.04 - same happened after overwriting with 13.04), couldn't install. So I installed B43, fwcutter, wl, whatever I could. I tried every command run in terminal, every forum solution and fix I could find. Here ends the first day, 9 hours later, and it sucked.

In the morning I was happy to wake up with a sense of determination. I noticed that when I shut down Windows (original, primary partition) the wireless indicator on the laptop would flick off. It seemed that the WLAN card was being disengaged every time I shut down from primary. I turned over the laptop, opened the bottom, pulled out my WLAN card, and grabbed my friends laptop. I did the same to his, swapped chips, and the moment I saw the lock screen, Ubuntu immediately connected to my router. I was stunned, so I decided to boot up the other laptop with my previous card in it - it runs on windows 8. I was stunned to see a BIOS prompt that stated that the WLAN card was encrypted and must be removed for windows to start up. My mind nearly exploded.

I am in telecom in the Canadian Armed Forces, and as such I am familiar with hardware that is security restricted. This is the first time that I have EVER seen a WLAN card like this. I called up the owner of the store where I bought the computer, a fellow Linux user, and asked him about how he acquired a restricted device laptop. He had no idea it had an encrypted card, but simply stated that a 'corporation' sold it to him. I laugh now, because the side of the laptop is cut open where a laptop locking device once kept this baby secure. Restricted WLAN, removed lock? I have no clue where this came from, but can only speculate...

So anyway, not that this is a huge problem for others, I thought I would offer these words of wisdom to other Ubuntu users who have Broadcom WLAN cards and have trouble getting the drivers to work: BUY A NEW CARD. I went to the local computer superstore, bought a $20 Intel card, and it worked fantastically. To be honest, if the B43, wl, or fwcutter, solutions don't work, save yourself the hassle, go out and splurge on a $20 card. I wish I had. It would have saved me 12 hours, multiple installs, and a massive headache.

Cheers, Jon

---

