---
title: "Headphone/Speaker issue"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by The_Proffessor on 2009-06-19
I'd be willing to bet that this is a common problem among new users. It's been bugging me for a while and I was wondering if there was anything to be done about it. Whenever I plug headphones or any other form of external speaker into my laptop, sound still comes out the normal speakers as well as the headphones. Not a huge problem, but it does somewhat defeat the purpose of headphones. What's a guy to do?

---

### Post by Sealbhach on 2009-06-19
If your soundcard is hda-intel then you could probably put an option in your sound config file in /etc/modprobe.d/alsa-base.conf

For example, on my laptop, I only get sound from the laptop speakers, until I put in an option in that config file, so that I get sound from external speakers. 

Can you give some information on your hardware by giving the output from the termninal from the command:

```
aplay -l
```

Just copy and paste the command.

.

---

### Post by The_Proffessor on 2009-06-19
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

Odd thing is I get sound from external speakers, just I continue getting sound from the internal ones as well.

---

### Post by The_Proffessor on 2009-06-19
ah, figured it out. I just need to mute the front speakers independently and the external speakers keep on playing. Just with most OS' the front speakers shut off automatically. Cool beans. :lolflag:

---

### Post by Sealbhach on 2009-06-19
OK, that's good. But if you want to, try adding this line to the end of your alsa-base.conf file.
```

sudo gedit /etc/modprobe.d/alsa-base.conf
```

add this line at the end and reboot:

```
options snd-hda-intel model=3stack

```

You can delete the line if it doeasn't work or causes problems.

.

---

### Post by ubseamus on 2009-06-28
Thanks for the info Sealbhach.  I've I'm having the same issue with my laptop on both 8.04 and 9.04.But this didn't work for me. 

Did this fix work for you Professor.

Thanks

---

