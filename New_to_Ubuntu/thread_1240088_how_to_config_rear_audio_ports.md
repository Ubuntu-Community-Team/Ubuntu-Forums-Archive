---
title: "how to config rear audio ports"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by redfoxkt on 2009-08-14
Hello I have been searching the internet and the forums for a good time now and i cant seem to find the answer to my question. Question is how do i configure the rear audio ports....to better explain my situation i have a Sub-woofer plugged into the blue port..and my speakers in the green...but my blue port doesnt work or some where its turned off because sound wont play through the sub.

im running Ubuntu 9.04

Thanks for the help

---

### Post by bear24rw on 2009-08-14
go in terminal and type
```
alsamixer
```

then you adjust the individual channels

---

### Post by matthewbpt on 2009-08-14
what sound card do you have? this can be driver dependent, for example on mine I had to change a switch in alsamixer to add line to /etc/modprobe.d/alsabase.conf, reboot, this gave me a new option in alsamixer to switch between 2 channel and 6 channel mode, and switching to 6 channel mode enabled my rear speaker output.

Run the following in the terminal and post the output here,

```
aplay -l
```
and
```
aplay -L
```

---

### Post by redfoxkt on 2009-08-19
> **matthewbpt said:**
> what sound card do you have? this can be driver dependent, for example on mine I had to change a switch in alsamixer to add line to /etc/modprobe.d/alsabase.conf, reboot, this gave me a new option in alsamixer to switch between 2 channel and 6 channel mode, and switching to 6 channel mode enabled my rear speaker output.

Run the following in the terminal and post the output here,

```
aplay -l
```and
```
aplay -L
```

umm idk what the sound card is..its a onboard soundcard..i have a asus p5n-e Sli MB...and ill try that thx

---

### Post by redfoxkt on 2009-08-19
ok ill try that in a second thanks

---

