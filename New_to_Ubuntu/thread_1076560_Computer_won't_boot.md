---
title: "Computer won't boot"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by Peter1234123 on 2009-02-21
I put together this computer about a year ago, and it hasn't booted for about 2 months, I'm just getting around to fixing it, because I've been busy lately. When I start it up, I get 1 long beep, and the fans keep running, but there's no POST messages, or any other beep codes. I tried a different video card, that I'm sure works, and I still get the boot error, I replaced the heatsink on the CPU, as I thought it might have been overheating, still get the error. I tested the power supply on a different computer, and tried another one, I still get the beep. I think that the motherboard may be dead, anyone have any advice? 

The specs are: 4 GB DDR2 800, Core 2 Quad Q6600 (2.4 ghz, not OC'd), Nvidia GeForce 8600GT, also tried an old PCI ATI card, and a Coolermaster power supply, and a Gigabyte motherboard. ([http://www.newegg.com/Product/Product.aspx?Item=N82E16813128059](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128059))

Any help would be greatly appreciated, thanks.

---

### Post by piroko on 2009-02-21
> **Peter1234123 said:**
> I put together this computer about a year ago, and it hasn't booted for about 2 months, I'm just getting around to fixing it, because I've been busy lately. When I start it up, I get 1 long beep, and the fans keep running, but there's no POST messages, or any other beep codes. I tried a different video card, that I'm sure works, and I still get the boot error, I replaced the heatsink on the CPU, as I thought it might have been overheating, still get the error. I tested the power supply on a different computer, and tried another one, I still get the beep. I think that the motherboard may be dead, anyone have any advice? 

The specs are: 4 GB DDR2 800, Core 2 Quad Q6600 (2.4 ghz, not OC'd), Nvidia GeForce 8600GT, also tried an old PCI ATI card, and a Coolermaster power supply, and a Gigabyte motherboard. ([http://www.newegg.com/Product/Product.aspx?Item=N82E16813128059](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128059))

Any help would be greatly appreciated, thanks.

I don't think the motherboard is dead, otherwise it wouldn't beep. 
Lemme do some searching and I'll get back to you on this.

What BIOS do you run? do you know?

---

### Post by Kareeser on 2009-02-21
Has it ever booted?

Check the 12V ATX power cable to the motherboard. It is a 2x2 plug that should be plugged in near the CPU fan.

---

### Post by Peter1234123 on 2009-02-21
Yes, it booted up until 2 months ago, perfectly, it's running the stock BIOS, as I never flashed it, all the plugs are plugged in, the only thing I can think of is that the CPU is in fact overheating, or the board is dead. But you're right, I don't understand why it would beep if* the board was dead.

---

### Post by RedRat on 2009-02-21
> **Peter1234123 said:**
> Yes, it booted up until 2 months ago, perfectly, it's running the stock BIOS, as I never flashed it, all the plugs are plugged in, the only thing I can think of is that the CPU is in fact overheating, or the board is dead. But you're right, I don't understand why it would beep if* the board was dead.

I had a similar problem a few months back. I was caused, by of all things, an overheating BIOS chip. My BIOS chip had a small heat sink attached and held by screws, the screws had become loose and one had fallen out so that the heat sink was not firmly laying on top of the BIOS chip. Since I didn't have the appropriate screws, I took it to a repair shop and they got replacement screw in. Take a look at your BIOS chip and see if you have heat sink on it and it may have worked loose.

---

### Post by Peter1234123 on 2009-02-21
It's definitely not a CPU problem, the computer doesn't turn on automatically, the button still needs to be pushed in order for it to boot up. And when you hold the button for 5 seconds, it shuts off, I checked with different RAM, same problem.

---

### Post by Peter1234123 on 2009-02-21
I don't believe that my BIOS has a heatsink, the North and South bridge heatsinks are firmly attached though.

---

### Post by Peter1234123 on 2009-02-21
One Beep, Blank or Incorrect Display  	Video Display Circuitry.

That's what I found, but I don't understand it, because I changed the video card, I even used a PCI card, when my main one is PCI Express...

---

### Post by paydaydaddy on 2009-02-21
I think that your board has Award bios. Please confirm. If so, your post code suggests a memory problem. In Award bios, 1 long followed by 2 short beeps indicates video problem. Do you see any display when attempting to start up? Can you get to bios? Can you run memtest?

---

### Post by newbee70 on 2009-02-21
I agree with paydaydaddy;

My system acts the same way once in awhile, always seems to be dust on the modules, or a bad connection.

try removing all but one memory module, check it for dust and dirt,and reboot. if it boots check and add the next module, reboot.

if it doesn't reboot the with the first module you try, remove it and check a second module..

---

### Post by Peter1234123 on 2009-02-21
I believe it is Award BIOS, I tried that, I'll try it again, and you're right, it probably is a memory problem, if I'm correct POST checks memory first, then CPU, I plugged the stock heatsink into the CPU fan slot (I use one that uses a system fan port instead of CPU fan), and it beeped before the fan started spinning, I'll try testing the RAM one at a time.

---

### Post by Peter1234123 on 2009-02-21
I tried, and a new thing is occurring, the computer starts up, beeps, then shuts down, restarts, beeps, and keeps running*, but with no display.

---

### Post by newbee70 on 2009-02-21
> **Peter1234123 said:**
> I tried, and a new thing is occurring, the computer starts up, beeps, then shuts down, restarts, beeps, and keeps running*, but with no display.

Ok, what did you try? 

I should have asked how comfortable you are with hardware troubleshooting before I suggested you remove and check individual modules.

if you tested individual modules, did you make sure it came completely up before checking the second module?

and did you make sure it was in the 1'st memory slot?

---

### Post by Peter1234123 on 2009-02-21
I know how to remove RAM modules, don't worry, I removed all 4, then tried each one, separately, in each slot, nothing solved it. I'm starting to think that it isn't a RAM problem..

---

### Post by RedRat on 2009-02-21
Methinks that if it isn't in the  BIOS chip and your RAM is Ok, you might have some motherboard problem. How old is the board?

---

### Post by Peter1234123 on 2009-02-21
less than a year and a half. It either could be a board problem, and maybe some controller is fried, but then I don't know why it's detecting an error in post, or booting, and controlling the fans at all, for that matter. I also don't know why it would test the hard drive (I hear it spinning). This happened once before, and it was a heatsink problem, I had to buy a new one to replace it. But I have a 100% copper Zalman heatsink, the fan is about 140mm. I'll buy another heatsink, and just test it, just in case, then if it doesn't work I'll just buy a new board, I guess.

---

### Post by RedRat on 2009-02-21
Have you had any power outages or surges? Depending on your power supply, particularly if they have minimal capacity (say 350 watts or less) power surges or power outages can sometime fry board components. If your CPU is still OK, you might just need to replace the board and these are not terribly expensive nowadays.

---

### Post by presence1960 on 2009-02-21
Do you have your mobo manual? it will tell you exactly what error is causing a certain beep. I finally started to download it from gigabyte's site, but the speed is so slow on their site.

---

### Post by homey69 on 2009-02-21
i had the same issue but with an abit board. try resetting your cmos? first try the jumper pin, if no dice then take out the battery, unplug, discharge capacitors by pressing power button, wait 20 mins or so... then put back everything and try again.

*actually if you have your mb manual there should be instructions in there better than mine, ha.

edit; also try re-seating your cpu... and if you do get your machine back on and plan on keeping the board, try not to go longer than a day or so without powering it on, and don't unplug for longer than a few seconds, if at all. sounds crazy but that's what's worked for me and i have the exact problem.

---

### Post by presence1960 on 2009-02-21
here it is from the manual for your mobo:

> Q: What do the beeps emitted during the POST mean?
A: The following Award BIOS beep code descriptions may help you identify possible computer problems.
(For reference only.)
1 short: System boots successfully
2 short: CMOS setting error
1 long, 1 short: Memory or motherboard error
1 long, 2 short: Monitor or graphics card error
1 long, 3 short: Keyboard error
1 long, 9 short: BIOS ROM error
Continuous long beeps: Graphics card not inserted properly
Continuous short beeps: Power error


---

### Post by Peter1234123 on 2009-02-22
I tried unplugging the battery and resetting CMOS multiple times, I didn't try removing the capacitors, but they are soldered onto the board...so I don't want to try. I checked the manual but there's nothing about 1 long beep. I assume that it is the CPU overheating, as this happened to a friend of mine with the same board, it also happened to me, but I didn't pay any attention to it, because I was using a stock heatsink, sometimes it booted fine, sometimes it made 1 long beep, and restarted, I assumed that nothing was wrong, and I was going to replace the heatsink anyways, so I did, and the error went away, then I unseated the processor, because I wanted to reapply thermal paste, and I stripped a screw on the heatsink, so it wasn't perfectly over the CPU, thus not cooling it properly, and that's where I am now. I ordered a new heatsink from Newegg, if it fixes the problem I'll reply again, if not...then I'll try a new board I guess :(

---

### Post by homey69 on 2009-02-22
don't physically remove the capacitors, that's not what i meant... discharge the leftover power they hold by pressing the power button while unplugged lol

anyway, your board has the same chipset as mine, p35, which is known to have the cmos/power no post/double boot issue... if you don't resolve your issue with new hs try the reset cmos thing again, as i'm pretty sure that's what's going on

don't touch the capacitors

---

