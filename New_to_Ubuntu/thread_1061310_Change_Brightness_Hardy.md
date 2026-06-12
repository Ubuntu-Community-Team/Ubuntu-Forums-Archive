---
title: "Change Brightness Hardy"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by NeoIndigo on 2009-02-05
Hi, 

I tried to reduce my screen brightness. However, I could not find where to do it. 

I am using Toshiba Satellite and Ubuntu Hardy. 

Any ideas ? 

Thanks,

---

### Post by RomeReactor on 2009-02-05
Hi. What video card are you using? If it's nVidia, and you're using the proprietary driver, open NVIDIA X Server Settings; should be located in 'System->Administration', or in 'Applications->System Tools', or to open it from the terminal:
```
gksudo nvidia-settings
```
Then select "X Server Color Correction" and you can change the brightness there.

Probably the Catalyst Control Center has that option for ATI cards.

---

### Post by NeoIndigo on 2009-02-05
> **RomeReactor said:**
> Hi. What video card are you using? If it's nVidia, and you're using the proprietary driver, open NVIDIA X Server Settings; should be located in 'System->Administration', or in 'Applications->System Tools', or to open it from the terminal:
```
gksudo nvidia-settings
```
Then select "X Server Color Correction" and you can change the brightness there.

Probably the Catalyst Control Center has that option for ATI cards.

Hi, 

I went to check the Hardware Drivers, but there is no drivers returned. How do I know what video card i am using ? Is there any other ideas to do this ? 

Thanks for your help,

---

### Post by RomeReactor on 2009-02-05
You can issue either of these commands in a terminal (Applications->Accessories->Terminal):
```
lspci | grep VGA
```
or:
```
lshw -c display
```
This last one will also tell you which driver the card is using.

---

### Post by emarkd on 2009-02-05
Are there brightness keys on your keyboard?  My Dell Inspiron has them and they "just work"

---

### Post by Ptero-4 on 2009-02-05
If you have no drivers listed there it might be because you have an Intel card (as I do in my laptop). To check type lspci -v | grep "VGA" in a terminal window and it should show a line telling what video card you have.
Also install the toshset and toshutils packages they´re in the repos.

---

### Post by NeoIndigo on 2009-02-08
yes you are right, my graphic card is intel. This is the details:

 Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03) (prog-if 00 [VGA controller])

@emarkd : I am using toshiba satellite, I saw the brightness button together with F6 and F7. I assume the way to use that is by pressing Fn + F5. However, nothing happens. 

What do we need toshset and toshutils packages for ? 

Do you guys know what I should do ? 

Thanks again,

---

### Post by NeoIndigo on 2009-02-08
Hey guys, 

Do you know how to set up the hotkeys for toshiba satellite ? Like (Fn + F6 or F7) 

Thanks,

---

