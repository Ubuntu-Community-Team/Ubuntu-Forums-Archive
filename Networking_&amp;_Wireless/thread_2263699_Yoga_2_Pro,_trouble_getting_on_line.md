---
title: "Yoga 2 Pro, trouble getting on line"
date: 2015-02-02
forum: Networking &amp; Wireless
---

### Post by jrh74 on 2015-02-02
I have installed ubuntu 14.04.1 LTS on a flash drive in order to try Ubuntu on my windows lap top.  I have managed to boot to the flash drive and get Ubuntu running but have not been able to get on line.  When i start Firefox, a box drops down which says "Server not Found" and, as a subtitle, "Firefox can't find the server at start.ubuntu.com.  For what its worth, I went to "Settings" and under "Networking" noted that under "Proxy" is "none" and under "wireless", nothing is listed and there is a toggle indicating that wireless is "off" and I'm unable to change it to "on".  My lap top is a Yoga 2 Pro with windows 8.1 (64 bit) which is has a wireless connection to DSL which was working ok during my session on ubuntu.  Can anyone help me get around this problem?

---

### Post by jeremy31 on 2015-02-02
You might be able to enable wifi with ```
sudo modprobe -r ideapad_laptop
``````
sudo rfkill unblock all
```

---

### Post by jrh74 on 2015-02-02
Thanks Jeremy.  Is this the only way?  I'm new to this and was hoping not to get into code writing (command line stuff) quite so quickly.

---

### Post by chili555 on 2015-02-02
All of us, including Jeremy and even me, were new to Linux and especially Ubuntu at one time. We understand your anxiety and frustration. 

All laptops use a little helper module that translates button presses that only laptops have into action. In your case, please turn on the wireless. In most laptops, the module works perfectly. In some, it doesn't work for one or two functions and, sadly, in a laptop or two, it doesn't work at all. In those cases, no amount of fiddling and coding can ever coax the wireless to life! There are a few 150 post threads here about those!!!

In your case, the Yoga 2 Pro issue is well known and probably easily solvable. If Jeremy's idea is correct, and I think it is quite correct, when you copy and paste those two commands into a terminal, you will have wireless immediately! You will praise young Jeremy, rightfully, and he will give you quick easy instructions to make it permanent. We believe you will never have to worry about it again.

I hope you feel at ease with the simple steps Jeremy will suggest to correct your problem.

---

### Post by grahammechanical on 2015-02-02
You can copy and paste the command from the post straight into the terminal.

Regards.

---

### Post by Pilot6 on 2015-02-03
If you update kernel, wifi will work well without removing ideapad_laptop.
Just run

sudo apt-get install linux-generic-lts-utopic

and reboot. The issue has been fixed.

---

