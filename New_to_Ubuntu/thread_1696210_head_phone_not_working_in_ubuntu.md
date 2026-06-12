---
title: "head phone not working in ubuntu"
date: 2011-02-27
forum: New to Ubuntu
---

### Post by amar.elec on 2011-02-27
Hi,

I'hv installed ubuntu 10.10 on my laptop. Generally if the head phone is connected to laptop, the laptop speaker sound should go off. But its not happening..
Even on connecting the headphone, sound is coming through laptop speakers. u can say my headphone is not discoverable...I think some software needs to be installed. Can anyone help me on this...?:(

...amar

---

### Post by emoguitarist06 on 2011-02-27
Does sound come through your headphones and speakers?

I had this problem on my laptop on 9.10 but since 10.04 it was fixed, well at least for my Asus EeePC

Anyways it comes down to the kernel
run this code:
```
uname -a
```
and post your results so we can see what kernel you're currently running.
Also what is your laptop model?

---

### Post by amsterdamharu on 2011-02-27
Could you allso post the output of the following commands?

```
cat /proc/asound/card0/codec#* | grep Codec
cat /etc/modprobe.d/alsa-base
```

To execute the command(s) you can press alt + F2, type gnome-terminal and click run. Then copy one command and paste it in the terminal (black screen that showed up after you clicked run). Use the mouse to paste commands in the terminal.
Then you can select all the text in the terminal, right click and select copy. When pasting it here please wrap it in code tags: &#91;code][COLOR=Red]Your pasted stuff[/COLOR]&#91;/code]

---

