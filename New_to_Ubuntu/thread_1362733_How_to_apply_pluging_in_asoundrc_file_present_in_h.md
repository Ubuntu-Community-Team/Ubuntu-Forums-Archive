---
title: "How to apply pluging in asoundrc file present in home directory"
date: 2009-12-23
forum: New to Ubuntu
---

### Post by vipin.balakrishnan on 2009-12-23
Hi,

   I'm using Ubuntu 8.04 LTS and kernal 2.6.24-26-generic. I want to know how we can apply plugging in asoundrc. For example if I have define a route. How can I apply this route to my default sound card through asoundrc. Please help me on this....

pcm.s51 {
    type route
    slave.pcm surround51
    slave.channels 6
    ttable.0.0 1
    ttable.1.1 1
    ttable.2.2 0.5
    ttable.3.3 0.5
    ttable.5.5 0.5
}

---

### Post by vipin.balakrishnan on 2009-12-23
Hi

  Please any one help me on this.

The above pluging which i created for route can be test by  this command. But I dont know how to apply this for default. Please help me on this.

**speaker-test -Dplug:s51 -c6 -l1 -twav.**

---

### Post by bodhi.zazen on 2009-12-23
I believe you simply put that information in 

~/.asoundrc

You may need to log off and back in for your changes to take effect.

---

### Post by vipin.balakrishnan on 2009-12-23
Hi,

 when I try do that only my two speaker is still working. But if I test my speakers using speaker test command

**speaker-test -Dplug:s51 -c6 -l1 -twav**. I can able to here the sound from all.Now just I try to mute the front left channel by changing the config below. That was happening correctly. So Other channel only not recognizing through this config. Can anyone help me on this. Please..
[B]
pcm.s51 {
type route
slave.pcm surround51
slave.channels 6
ttable.0.0 1
ttable.1.1 1
ttable.2.2 0.5
ttable.3.3 0.5
ttable.5.5 0.5
} [/B]

---

### Post by vipin.balakrishnan on 2009-12-24
Hi 
 
  Please anyone has answer on my problem.

---

