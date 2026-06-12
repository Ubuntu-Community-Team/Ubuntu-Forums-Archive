---
title: "No sound after installing alsa 1.023"
date: 2010-10-02
forum: New to Ubuntu
---

### Post by SandyM on 2010-10-02
I wasfacing a problem of occasional sond loss after ubuntu booting, The problem was occasional since ubuntu used to regain its voice after 2-3 reboots.

The problem was accompanied with sudden disappearance of volume icon from panel with no option to add it again.

Of late  I have also seen pronged boot of ubuntu stretching upto 7-8 minutes.

I was advised by Someone from the community to upgrade to alsa 1.023 and since thn I have completely lost my ubuntu's voice.

Please help or else I have to re-install Ubuntu.

---

### Post by lidex on 2010-10-03
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by SandyM on 2010-10-03
> **lidex said:**
> Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

Following is the link
 [http://www.alsa-project.org/db/?f=708d427b36f3b5549b0592b5eaaf451ae7833d69](http://www.alsa-project.org/db/?f=708d427b36f3b5549b0592b5eaaf451ae7833d69)

I think the problem is that Ubuntu is not recognizing my intel hardware, however hardware is fine as I am not facing any problem in windows.

---

### Post by lidex on 2010-10-03
Interesting. Can you post this output for me please:
```
sudo lshw -C multimedia

```

It appears that alsa does not recognize your soundcard. What is the make/model of your pc/laptop?

---

### Post by SandyM on 2010-10-05
> **lidex said:**
> Interesting. Can you post this output for me please:
```
sudo lshw -C multimedia

```

It appears that alsa does not recognize your soundcard. What is the make/model of your pc/laptop?

Here is the outcome of the command

*-multimedia            
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:30 memory:e2220000-e2223fff

I have noticed that my sound is going off and on. After your last post I went to 'sound' in preference menu and noticed that no hardware was shown. After an hour or so I just randomly checked and was amazed to see that my hardware was there. Then again few hours later when I tried to play the movie,there was no sound. I rechecked 'sound' , only to find that my sound card was gone again.During all this time I never shutdown my PC.

Now when I ran the command asked by you, and writing this post ubuntu is benevolent enough to recognize my hardware and sound. But only god knows upto when.

---

### Post by lidex on 2010-10-05
Try this
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**

---

### Post by SandyM on 2010-10-08
> **lidex said:**
> Try this
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**

Both the commands returned with "no such file or directory" comment

---

### Post by lidex on 2010-10-08
> **SandyM said:**
> Both the commands returned with "no such file or directory" comment

That's OK. Any changes?

---

