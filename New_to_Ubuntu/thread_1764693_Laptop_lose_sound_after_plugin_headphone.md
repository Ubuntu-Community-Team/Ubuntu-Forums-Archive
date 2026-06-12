---
title: "Laptop lose sound after plugin headphone"
date: 2011-05-22
forum: New to Ubuntu
---

### Post by luckymancvp on 2011-05-22
I have a laptop Asus K42JE-VX089 install Ubuntu 10.10 LTS 2

Normal, I play music from my build in laptop speaker. But, I plugin a headphone then play music, I still hear music from headphone.

But when I plug out headphone, It didn't play music from laptop speaker. 

Now, If I want to listen to music, I must plugin headphone. 

How do I fix this problem ?

---

### Post by luckymancvp on 2011-05-22
Please help me fix this. Now, I can' listen to music without headphone

---

### Post by luckymancvp on 2011-05-23
No one help me :confused:

---

### Post by luckymancvp on 2011-05-24
Pls help me :(

---

### Post by Lateralis on 2011-05-24
I had a vaguely similar problem.  I found on my Fujitsu Siemens laptop that the speakers wouldn't work, but the headphones would.  In 10.10 and 11.04, the speakers refused to work until I edited one of the kernel options for the driver.  

So, I don't know how much I will be able to help you, but lets start by gathering some information.  Open up a terminal (Applications -> Accessories -> Terminal) and then type in the following:

```

sudo lshw -C sound

```

Copy and paste the ouput of that command between "code" tags for easy reading.  (In the advanced post editor, the code tag button looks like a "#".)

Also, type the following into a terminal

```

wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh

```

This will download and run a script from the ALSA project website that will gather an enormous amount of information about your sound card and currently used driver.  When it asks you to upload the file to the ALSA website, type 'y' for yes and copy/paste the link to the results into this thread.

---

### Post by luckymancvp on 2011-05-24
> **Lateralis said:**
> I had a vaguely similar problem.  I found on my Fujitsu Siemens laptop that the speakers wouldn't work, but the headphones would.  In 10.10 and 11.04, the speakers refused to work until I edited one of the kernel options for the driver.  

So, I don't know how much I will be able to help you, but lets start by gathering some information.  Open up a terminal (Applications -> Accessories -> Terminal) and then type in the following:

```

sudo lshw -C sound

```

Copy and paste the ouput of that command between "code" tags for easy reading.  (In the advanced post editor, the code tag button looks like a "#".)

Also, type the following into a terminal

```

wget  -O alsa-info.sh && bash alsa-info.sh

```

This will download and run a script from the ALSA project website that will gather an enormous amount of information about your sound card and currently used driver.  When it asks you to upload the file to the ALSA website, type 'y' for yes and copy/paste the link to the results into this thread.


Thanks for response

----

----

This is result of command sudo lshw
```
*-multimedia            
       description: Audio device
       product: Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:17 memory:f0040000-f0043fff
  *-multimedia
       description: Audio device
       product: 5 Series/3400 Series Chipset High Definition Audio
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:22 memory:f7a00000-f7a03fff
```


And here is the link

[http://www.alsa-project.org/db/?f=68485a5025cb18fc2f04bc376f6266f96fe73a8b]("http://www.alsa-project.org/db/?f=68485a5025cb18fc2f04bc376f6266f96fe73a8b")

---

### Post by luckymancvp on 2011-06-12
Haizz :(:(:(

---

