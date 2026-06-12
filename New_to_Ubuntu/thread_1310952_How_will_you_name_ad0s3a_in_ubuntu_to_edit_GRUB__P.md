---
title: "How will you name ad0s3a in ubuntu to edit GRUB ? Plz read"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by dalfish on 2009-11-02
Dear All 


                I am a newbie to PCBSD I have installed PCBSD 7.1 on 

ados3b swap
ados3a ufs filesystem PCBSD 7.1 

i have already installed ubuntu 9.04 on my HDD so in order to keep the GRUB i untick the PCBSD boot loader in the installation. Now i cannot boot into PCBSD I done some research about GRUB editing and gave the following in the GRUB 

title PCBSD 7.1
root (hdo 3 a)
kernel /boot/loader
boot


The PCBSD came in the GRUB at the start up but It says no such partition 
please help me to name the partitions correctly so that i can use the PCBSD 7.1 
I would like to learn about the PCBSD and Ubuntu naming convention for partitions
Please help


Regards


Ashik

---

### Post by spiderbatdad on 2009-11-02
at the very least there is a typo in your post..."hdo" is not a valid partition. hd0 (zero) is. did you make the same mistake in grub? What you are looking for may be (hd0,3)

---

### Post by Hazey on 2009-11-02
Hi guy,

do you use commas in your "root"-Section?

Hazey

---

### Post by dalfish on 2009-11-02
I have tried putting commas and corrected the O to zero but it still says ERROR 22 NO SUCH PARTITION 
PCBSD was installed in  /dev/sda3 but it repeatedly  says the same ERROR 22 NO SUCH PARTITION

---

### Post by ibuclaw on 2009-11-02
> **dalfish said:**
> I have tried putting commas and corrected the O to zero but it still says ERROR 22 NO SUCH PARTITION 
PCBSD was installed in  /dev/sda3 but it repeatedly  says the same ERROR 22 NO SUCH PARTITION

Clarification, sda**3** ???

FYI:
[LIST]
[*]hd0,0 = sda1
[*]hd0,1 = sda2
[*]hd0,2 = sda3
etc...
[/LIST]


```

title PCBSD 7.1
root (hd0,2,a)
kernel /boot/loader
boot

```


If that fails you:

```

title PCBSD 7.1
root (hd0,2)
chainloader +1

```

Regards
Iain

---

### Post by dalfish on 2009-11-02
Dear tinivole 

I thank you sincerely The second option really worked. It booted PCBSD for the first time.
If you have an idea how to configure display card in PCBSD 7.1
I have been presented with the following message 

Starting X
rm: /etc/x11/xorg.conf no such file or directory
Auto detected settings failed
using failsafe VESA 1024X 768

I have NViDIA graphics card Winfast  px6200 TC graphics card           GPU Nvidia GE FORCE 6200

---

### Post by ibuclaw on 2009-11-02
> **dalfish said:**
> Dear tinivole 

I thank you sincerely The second option really worked. It booted PCBSD for the first time.
If you have an idea how to configure display card in PCBSD 7.1
I have been presented with the following message 

Starting X
rm: /etc/x11/xorg.conf no such file or directory
Auto detected settings failed
using failsafe VESA 1024X 768

I have NViDIA graphics card Winfast  px6200 TC graphics card           GPU Nvidia GE FORCE 6200

It's been a while since I tried BSD, but weren't NVIDIA drivers detected/used automatically?

If not, it may be the vesa drivers that are interfering, and putting:
```
vesa_load="NO"
```
In the **/boot/loader.conf** file may resolve it (or render your system unusable from GUI until you remove it).

Regards
Iain

---

