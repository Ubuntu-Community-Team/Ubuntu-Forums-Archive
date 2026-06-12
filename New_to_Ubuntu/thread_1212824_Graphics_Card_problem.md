---
title: "Graphics Card problem"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by mosaabJ on 2009-07-14
Hello,
Yesterday I saw on one of the sites a thread talking about Graphics card drivers on Ubuntu and how you have to install the driver on your own and I followed what the guy said including downoading a software to install the graphic card driver and then the software asks you for the graphic card you have and then after following these steps and restarting my computer the screen is mashed up and you don't see anything basically theres nothing you can see.

---

### Post by Jimmyfj on 2009-07-14
Open a terminal: Programs>Accessories>Terminal and run the following command:

```
sudo dexconf
```

Then reboot your computer, which should now start up with the default Wesa-driver loaded. 

Go to System>Administration and start the program Hardware Drivers. Use that program to install your graphics card driver. Be sure to select the suggested driver for your card.

---

### Post by mosaabJ on 2009-07-14
How can I do that when I can't open Ubuntu

---

### Post by philinux on 2009-07-14
Boot the machine, press esc key when grub appears. Use arrow down key to choose recovery mode. When menu appears choose xfix. When thats done chose resume normal boot.

Post back if not ok.

---

### Post by mosaabJ on 2009-07-14
I did that but no use

---

### Post by Jimmyfj on 2009-07-14
Try to do the same, hit the Esc-key when GRUB loading and choose to boot up in safe mode. Or, if possible, boot up into a command prompt. Then login as you would do in graphics mode and switch to root mode by sudo and your password.

When in root mode enter the command I gave you above.

---

### Post by 3rdalbum on 2009-07-14
> **mosaabJ said:**
> Hello,
Yesterday I saw on one of the sites a thread talking about Graphics card drivers on Ubuntu and how you have to install the driver on your own

You must have taken something out of context; the idea is with Ubuntu that you *don't* have to install a driver manually, it will be provided for you in System > Administration > Hardware Drivers, or automatically activated for you.

When you say "I did that but no use", can you please be more specific? What exactly happened? When you go to the doctor, you don't say "Doctor, I have pain, can you give me something to fix it", you give him as much information as possible so he can work out the problem and prescribe a treatment.

---

### Post by mosaabJ on 2009-07-14
> **3rdalbum said:**
> You must have taken something out of context; the idea is with Ubuntu that you *don't* have to install a driver manually, it will be provided for you in System > Administration > Hardware Drivers, or automatically activated for you.

When you say "I did that but no use", can you please be more specific? What exactly happened? When you go to the doctor, you don't say "Doctor, I have pain, can you give me something to fix it", you give him as much information as possible so he can work out the problem and prescribe a treatment.

The program I was talking about is Envy.
I am not really sure that the problem is from this because it required that the computer should be restarted but I didn't do that until a day later after installing VMWare on my computer and the computer was stuck so I had to press the switch off button on the PC and then I faced the problem I was talking about

---

