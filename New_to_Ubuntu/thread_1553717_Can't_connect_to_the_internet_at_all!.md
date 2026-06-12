---
title: "Can't connect to the internet at all!"
date: 2010-08-15
forum: New to Ubuntu
---

### Post by Snapdragon19 on 2010-08-15
I recently installed Ubuntu 10.04 desktop edition onto my computer off an official CD. Everything seems to be working perfectly except for the fact that i can't connect to the internet at all. When i clicked on the little icon on the top bar both wired and wireless connections were greyed out with the text '(disconnected)' and '(device not ready)' next to them respectively. I tried right clicking on the icon and checked that everything was enabled, i checked my router was on, i looked through the help manual but it didn't help; I went to the network configuration application through the menu but it didn't see any wireless networks even though i know i'm within range of several. Does anyone have a solution?

I'm on a Dell Latitude D180 with an Intel pentium M 1.73GHz  processor with 2.00 GB of RAM and a 60 Gigabyte hardrive 10.5 gigabytes of which is dedicated to ubuntu, 49.5 gigabytes of which is dedicated to windows xp home edition SP2 (I'm planning on deleting windows as soon as i get everything working correctly in Ubuntu)

P.S. i couldn't connect when i was running of a live CD either but i assumed i would be able to after i installed Ubuntu.

---

### Post by corrytonapple on 2010-08-15
If you could connect using Windows, go to **System>Administration>Hardware Drivers** and download any drivers for your computer. If you could not connect using Windows, then you are out of range. See picture (I have no drivers to install)

---

### Post by Snapdragon19 on 2010-08-15
I can't download drivers on Ubuntu because i can only connect to the internet on windows.

---

### Post by corrytonapple on 2010-08-15
Click on the Internet Connect Icon up in the top menu bar, then click connect to new wireless network. Type the name of the network, the password (if any), and choose the security. If it does not work, keep playing around with different security levels.

---

### Post by Snapdragon19 on 2010-08-15
K, booting up Ubuntu now, brb.

---

### Post by corrytonapple on 2010-08-15
Also if there is a external antenna turn it off and then on if none of that helps.

---

### Post by Thomas Garman on 2010-08-15
I have a Belkin USB wifi adapter that I use for just this sort of problem, which I bought for $20.  I found that when I tried to install Ubuntu on my laptop and then again on my netbook that the broadcom drivers were not pre-installed so then my Ubuntu install (starting from 9.04 and continuing through 10.04) would never allow me to connect to the internet because my broadcom wifi card pre-installed in my laptop/netbooks had no Ubuntu drivers.  So, I would plug in my Belkin USB wifi adapter to my computers and Ubuntu would detect the wifi signal and then I would install the broadcom drivers.

So, go get yourself a USB wifi adapter.  ubuntu gnome network manager will detect it and you can get online.

---

### Post by corrytonapple on 2010-08-15
> **Thomas Garman said:**
> I have a Belkin USB wifi adapter that I use for just this sort of problem, which I bought for $20.  I found that when I tried to install Ubuntu on my laptop and then again on my netbook that the broadcom drivers were not pre-installed so then my Ubuntu install (starting from 9.04 and continuing through 10.04) would never allow me to connect to the internet because my broadcom wifi card pre-installed in my laptop/netbooks had no Ubuntu drivers.  So, I would plug in my Belkin USB wifi adapter to my computers and Ubuntu would detect the wifi signal and then I would install the broadcom drivers.

So, go get yourself a USB wifi adapter.  ubuntu gnome network manager will detect it and you can get online.
That will work but, there is an easier, cheaper, way. Also I doubt that he will be doing that many installs.

---

### Post by Thomas Garman on 2010-08-15
well, one thing I have learned from my short experience of using Linux is that the habit you get into of just buying a machine and slapping an OS onto it that you learned from using Windows machines your whole life doesn't fly because not every piece of hardware is going to work with Linux...  and so you have to be aware of what hardware you have before you jump into a Linux OS...

and in the end $20 for an instant solution to your wifi problem via a USB wifi device that works is cheaper than spending days and days googling around forums trying to find a solution.

AND YOU CAN RETURN THE DEVICE TO THE STORE YOU BOUGHT IT AT ONCE YOU ARE UP AND RUNNING.

So, how much is your time worth to you?

---

### Post by sanderj on 2010-08-15
@Snapdragon19

Can you post the output of 

```
lspci | grep -i  eth
```

here? So open a terminal, and type the command above, and copy-paste all output here. It will show which ethernet hardware is in your computer.

---

### Post by corrytonapple on 2010-08-15
I am guarenteed this will work. Thus, there won't be days of googling. See my sig. I would feel guilty buying a device and getting to use it for free. Anyway, s/he just wants it to work. If their time is worth something than flying down to the local Best Buy is not an option. Posting on the forums and getting an answer in a great community is free and quick.

---

### Post by Snapdragon19 on 2010-08-15
Back, could not connect to wireless by creating a new network but i could establish a VEEEEERY slow connection by tethering my nexus one. I'm back on windows because the connection was to slow, ill post that terminal thing in a minuet.

P.S. @sanderj how do i make that line: |
(i know nothing about code)

---

### Post by corrytonapple on 2010-08-15
Is it wired or wireless your trying to get?

---

### Post by Snapdragon19 on 2010-08-15
> **corrytonapple said:**
> Is it wired or wireless your trying to get?

Wireless

---

### Post by sanderj on 2010-08-15
> **Snapdragon19 said:**
> 

P.S. @sanderj how do i make that line: |
(i know nothing about code)

Is it on the key above your ENTER button? If so, press SHIFT, and then that key, release key and release SHIFT.

HTH

---

### Post by sanderj on 2010-08-15
> **Snapdragon19 said:**
> Wireless

Oh. Does your wired ethernet/Internet work?

---

### Post by Snapdragon19 on 2010-08-15
The key above my enter button is backspace, so no. I don't have a number pad if that helps.

---

### Post by Snapdragon19 on 2010-08-15
It works but my computer is upstairs and my router is downstairs.

---

### Post by sanderj on 2010-08-15
> **Snapdragon19 said:**
> It works but my computer is upstairs and my router is downstairs.

So the title "Can't connect to the internet at all!" could better be something like "Can't connect to the internet via Wifi"...

---

### Post by jtarin on 2010-08-15
> **Snapdragon19 said:**
> The key above my enter button is backspace, so no. I don't have a number pad if that helps.
The key to the left of the back-space key. The one to the right of the "=+" key. The "\ |" key.

---

### Post by Snapdragon19 on 2010-08-15
Apparently i have an abnormal keyboard: [IMG]http://picasaweb.google.co.uk/112576039978009500574/20100815?authkey=Gv1sRgCPmXjonHvd6ysAE#slideshow/5505743266591273154[/IMG]

If image doesn't work go to this link: [http://picasaweb.google.co.uk/112576039978009500574/20100815?authkey=Gv1sRgCPmXjonHvd6ysAE#slideshow/5505743266591273154](http://picasaweb.google.co.uk/112576039978009500574/20100815?authkey=Gv1sRgCPmXjonHvd6ysAE#slideshow/5505743266591273154)

---

### Post by corrytonapple on 2010-08-15
Its the one above tab and next to 1.

---

### Post by Snapdragon19 on 2010-08-15
K but for some reason none of the change keys give me that line.
Nothing = `
Shift = ¬
Ctrl = Blank
Fn = Blank
Alt = Blank

---

### Post by corrytonapple on 2010-08-15
Got it. Use the on screen keyboard. Go to **Applications>Accessories>Terminal. T**here is an easier way to do this but I do forget. Anyway type:
```

onboard

```When it opens, hit shift then |. It is above return. Do this when needed when entering the command. When you are done with it close the terminal. When it asks, kill the process.

---

### Post by jtarin on 2010-08-15
> **Snapdragon19 said:**
> Apparently i have an abnormal keyboard: [IMG]http://picasaweb.google.co.uk/112576039978009500574/20100815?authkey=Gv1sRgCPmXjonHvd6ysAE#slideshow/5505743266591273154[/IMG]

If image doesn't work go to this link: [http://picasaweb.google.co.uk/112576039978009500574/20100815?authkey=Gv1sRgCPmXjonHvd6ysAE#slideshow/5505743266591273154](http://picasaweb.google.co.uk/112576039978009500574/20100815?authkey=Gv1sRgCPmXjonHvd6ysAE#slideshow/5505743266591273154)

No....you have a LAPTOP keyboard, not a desktop keyboard. I missed that in your first post.

---

### Post by Snapdragon19 on 2010-08-16
Hooray it's working! I used the tethered internet from my nexus one to download a new driver (took all night 'cause it's so slow but it was worth it) and now it's working perfectly! Thanks for all your help. :)

---

### Post by sanderj on 2010-08-16
Some questions/remarks:

How did you do the tethering? Not via Wifi, I guess?

Was the proprietary wifi driver automatically offered & downloaded & installed via the "hardware" icon in Ubuntu top bar? If so, I think first connecting your PC via wired ethernet/internet could have helped...

---

### Post by Snapdragon19 on 2010-08-16
I tethered my nexus one via the USB to micro USB cable that came with it and to answer your second question: yes.

---

### Post by corrytonapple on 2010-08-16
You are welcome.:popcorn:

---

### Post by ezli09 on 2010-08-16
Kept getting the my wireless network says "disconnected" error. Dell Latitude D620 with a Broadcom wireless card. Went to System>Administration>Hardware Drivers, clicked on the first option, activated it, turned the wireless radio off then back on, and VOILA! found my wireless network and it's working now...sweet!

---

