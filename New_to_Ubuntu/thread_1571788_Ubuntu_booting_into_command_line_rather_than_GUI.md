---
title: "Ubuntu booting into command line rather than GUI"
date: 2010-09-10
forum: New to Ubuntu
---

### Post by mysteriousknome on 2010-09-10
Hello, I am very very new to ubuntu and linux in general and I need help. My computer used to boot up into the desktop just fine but after doing a partial uggrade, it absolutely refuses to boot into the desktop and all i get is a command where it asks me to put in a username and password. I guess a better way to put is that the GUI for the desktop doesn't boot and all I get is a black screen with command line functions. I am running ubuntu 10.10 beta, what should I do? Should I go back to 10.04 LTS?

---

### Post by Saint_ on 2010-09-10
Hm, well I'm not very good at this but perhaps I can offer some help. After you login via the command line, try typing ```
gnome-session
or
*sudo /etc/init.d/gdm start*
```

---

### Post by Rubi1200 on 2010-09-10
Beta=bugs

Beta releases are not recommended if you want a stable environment.

Did this happen with 10.04?

Try running ```
startx
``` at the command line and see what happens.

---

### Post by mysteriousknome on 2010-09-10
> **Rubi1200 said:**
> Beta=bugs

Beta releases are not recommended if you want a stable environment.

Did this happen with 10.04?

Try running ```
startx
``` at the command line and see what happens.

I put in the command you gave me and I am still stuck in command line. As for this happening in 10.04, I never experienced this unless it was something I did to make it happen. Please remember I am very new to linux and I thought that after upgrading I would still have access to my desktop (obviously not the commmand line version of my desktop, The GUI). I hope this helps.

---

### Post by Saint_ on 2010-09-10
Can you tell us what happened after you typed startx and pressed enter?

---

### Post by mysteriousknome on 2010-09-10
> **Saint_ said:**
> Can you tell us what happened after you typed startx and pressed enter?

a bunch of text appeared on screen, so much so that it would be a real hassle to put all of it in. After all the text, i was back to square one with a blank line and cursor ready to put in more text. Maybe I would have been better off just staying at 10.04. That is what I started with when I first started using linux, it was a real hassle though because I suffered from purple screen of death and the computer randomly just crashed and I had to restart it but eventually I got it fixed and it worked fine after being updated with update manager. Installation has also been troubling for me, its very hit and miss sometimes it goes off without a hitch and sometimes I have to restart and restart and restart before I finally can hit the install screen.

---

### Post by Saint_ on 2010-09-10
I see..so once you ended up back with the blinking cursor did you try typing either of these? ```
gnome-session
or
*sudo /etc/init.d/gdm start*
```
You can go back to 10.04 if you're ok with starting over and possibly losing personal data, but I'm sure someone will come along here soon with a definitive fix.

---

### Post by Rubi1200 on 2010-09-10
What graphics card do you have installed?

---

### Post by mysteriousknome on 2010-09-10
> **Rubi1200 said:**
> What graphics card do you have installed?

Not sure. Here are the specs I do know:

Dell Optiplex GX260
256 mb RAM
20 GB Hard Drive

The only thing I do know is that I got it to run so I meet the minimum requirements and only just. I have garbage for hardware.

---

