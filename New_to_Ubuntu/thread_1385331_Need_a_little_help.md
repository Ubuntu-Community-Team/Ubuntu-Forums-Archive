---
title: "Need a little help"
date: 2010-01-19
forum: New to Ubuntu
---

### Post by SymphonicNerd on 2010-01-19
recently got smart and couldn't take windows crashing or the dreaded blue screen of death, been interested in learning linux for a while so i switched from windows to ubuntu. I immediately fell in love it. my inner nerd has proven quite strong and i for-see a long road ahead enjoying the benefits of linux. i have some of the basic commands down. My question is how can i use the terminal to control my battery output? says my charge can hold 99% but that only last 30 minutes while on windows it would go 2 hours.... im sure theres a way to fix this i just haven't found it yet. Also im converting vga to s-video on a small Sharp tv for an additional monitor. it will mostly only ever be used as a terminal but i was wondering if there is anything i should know before attempting my new project. 

And thank you ubuntu community, been reading the threads for a while now and you have helped make the transition easily. Ubuntu rocks and i'll never go back to a non-linux pc again

Symphonic :D

PS- unrelated but can anyone tell me while almost all linux distros are free except red hat? the price alone matches that of windows and based on my research didn't seem any more or less stable then other distros. thanks

Problem solved, thank you guys!

---

### Post by mbzn on 2010-01-19
As for the battery, I don't know how in the terminal...

Red hat offers a hand to hand support center on a well proved stable system, basicly they take freeware and spend money on it and hire people to do what we do on the forum and that's what you pay for. I believe it may also include some non free software and big books when you buy it.

---

### Post by SymphonicNerd on 2010-01-19
Thanks for informing me about red hat, still curious on how i can alter my batter power, i like to learn to use the terminal to control so i'll keep looking or maybe someone here will know

---

### Post by dmillerct on 2010-01-19
> **SymphonicNerd said:**
> Thanks for informing me about red hat, still curious on how i can alter my batter power, i like to learn to use the terminal to control so i'll keep looking or maybe someone here will know

I am not sure what you mean by "alter from a terminal". You can control the power settings from System -> Preferences -> Power Management.

If you want to see your current battery state in a terminal you can do that as well. Is that what you are asking for?

---

### Post by SymphonicNerd on 2010-01-19
not quite, is there no way in the terminal to alter how much battery output is being used? i found the power management but it wouldnt let me alter the battery output. in windows you can choose your batter power based on needs such as energy saver or exceptional performance.... maybe this is part of the flaw of windows? but i still thought i would be able to adjust battery output from a command in the terminal

Thanks again

Symphonic

---

### Post by achase79 on 2010-01-19
powertop is a good program for finding and limiting power consumption.  it is terminal based

cpufrequtils is good for newer processors so it steps down the processing power in low need situations to conserve power.

---

### Post by SymphonicNerd on 2010-01-19
thanks, will i be able to find support when trying to use powertop in the terminal the first couple times? trying to avoid any major issues for the time being until i have a better understanding of how to fix things.

---

### Post by achase79 on 2010-01-19
it is a relatively simple program.  If you want more accurate results and the ability to enact changes within powertop you will have to run it along with the sudo command.

---

### Post by SymphonicNerd on 2010-01-19
thank you, ill consider this problem solved =) gonna get myself acquainted with powertop as soon as i figure out what happened to my tty1 =\

Symphonic

---

