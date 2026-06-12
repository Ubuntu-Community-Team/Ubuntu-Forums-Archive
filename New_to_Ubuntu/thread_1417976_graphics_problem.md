---
title: "graphics problem"
date: 2010-02-28
forum: New to Ubuntu
---

### Post by paker on 2010-02-28
When I start gnometrtis, I get this (screen shot attached). I just get the frame of the tetris window. I can see the desktop. What's going on?

9.10 fresh install
amd 785g onboard video
AMD Phenom II X2 555 

Thanks.

---

### Post by drpjkurian on 2010-02-28
Hi
I hope you do not have any other graphics problem. If so please try reinstallation of the game through Add remove option or Ubuntu software centre.

---

### Post by 3rdalbum on 2010-02-28
> **drpjkurian said:**
> Hi
I hope you do not have any other graphics problem. If so please try reinstallation of the game through Add remove option or Ubuntu software centre.

drpjkurian, that only has any effect if the program's binary is damaged - which is exceedingly rare on Linux. This does not look like a 'corrupted program' problem.

If you are using Desktop Effects, try disabling them; there are known issues with Compiz and OpenGL (3D) programs coexisting on ATI graphics cards.

If your graphics card is supported by ATI's proprietary driver, then try installing that if you haven't already.

---

### Post by paker on 2010-02-28
Thanks. As instructed, removed and reinstalled tetris, removed compiz, rebooted. It's working now. Thanks. By the way, I know nothing about desktop effect, compiz, opengl. I am already using the ATI proprietary driver.

One more thng. The screen blinks speckled red/blue a few seconds before the ubuntu theme music plays. No other graphics issue yet. This computer is a new build, my first ATI graphics.

---

### Post by drpjkurian on 2010-03-01
HAPPY TO KNOW THAT IT IS SOLVED.
pLEASE MARK THE THREAD AS SOLVED

---

### Post by undecim on 2010-03-01
> **paker said:**
> The screen blinks speckled red/blue a few seconds before the ubuntu theme music plays.

My ATI card shows a bunch of randomly colored/textured/texted squares in a grid across my screen when it loads (reminds me of old arcade games starting up). Perfectly harmless. It's just the video card initializing.

And as drpjkurian said, please mark this thread as solved if you don't have any more related questions. (using the "thread tools" menu)

---

### Post by paker on 2010-03-04
The problem is more serious than tetris.

To recap,

a new build
ubuntu 9.10 32bit
Biostar TA-785GE 128M
AMD 785G onboard graphics
Phenom II X2 555 BE
proprietary ATI driver that comes with 9.10

Problem: all kinds, computer hangs randomly, speckled screen during bootup, computer turns itself off, daily occurrence.

Solution:

AMD's ATI driver site 
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)
Download installer file xxx.run
sudo sh xxx.run

The new build is stable overnight. I will update again in a week. By the way, no speckled screen during bootup.

---

### Post by paker on 2010-03-12
I should have checked this forum before buying a motherboard with ATI graphics, AMD 785G chip. I tried 1) what comes with ubuntu 9.10, 2) proprietary driver that 9.10 recommends, and 3) what's on AMD's web. None would last a few days without a graphics problem, too slow, freeze, turns computer off, restarts, etc. 

Finally gave up and bought an nVidia graphics card. It's been working for 2 days without a hiccup.

UPDATE: It's been about a week, No problem at all with nvidia GT 240. I using the nvidia priprietary driver that 9.10 recommended.

---

