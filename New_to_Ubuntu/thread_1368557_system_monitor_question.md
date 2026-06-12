---
title: "system monitor question"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by clay woodruff on 2009-12-30
why is it when i'm viewing my system monitor to try and figure out what app is causing my CPU to spike the only thing active is firefox and system monitor, everything else says sleeping. is it a firefox thing........ANOTHER firefox thing. or whats up.

---

### Post by jbrown96 on 2009-12-30
It's probably Firefox (actually Flash specifically). It will sometimes freeze up on me for a second and cause a CPU spike. It's usually due to the poor quality of Flash for Linux. See if you notice on sites with lots of flash (ads typically use lots of flash). Ad block plus is a very good firefox extension that keeps Firefox from having CPU spikes.

---

### Post by clay woodruff on 2009-12-30
yeah i have that installed. tried a few tweeks but nothing really worked. isnt there something else to use, other than firefox or adobe. ohh yeah and im still curious as to why my sys mon. says all apps sleeping except firefox and sys mon. i just tried something i opened a streaming video and had terminal running along side with command top running, and what is spiking along with firefox is xorg. why is that

---

### Post by jbrown96 on 2009-12-30
Xorg runs the graphical environment. If Firefox or the terminal wants to change something on screen, then it sends commands to Xorg, which executes them. Xorg does all the animating. 

This is substantially different than how Windows works. In Windows, each window (aka process) draws itself. This is noticeable when a program freezes; the window will freezes and the graphics from other windows will get "stuck" in the frozen one. It's usually difficult to close these programs.
In Linux, Xorg draws all the windows, so if a program freezes, then the actual window (i.e. the title bar with the minimize, maximize, and exit buttons) is still responsive, so the whole system stays more stable and you can close the frozen program easily.

In KDE, there is a good browser called Arora that uses Webkit, which is the best rendering engine available. You can install it with ```
sudo apt-get arora
``` It is in heavy development, so it lacks a few features, but I have found it to be stable and very fast.

Then there's Google Chrome, wich also uses Webkit. There is an Ubuntu package available from Google that is very easy to install. It has more features than Arora, and I have found it to be comparable in speed. It's very good.

---

