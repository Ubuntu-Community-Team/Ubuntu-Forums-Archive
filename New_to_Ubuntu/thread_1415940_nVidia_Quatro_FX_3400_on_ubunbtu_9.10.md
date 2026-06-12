---
title: "nVidia Quatro FX 3400 on ubunbtu 9.10"
date: 2010-02-25
forum: New to Ubuntu
---

### Post by anigodin on 2010-02-25
Hello People, (sorry for the long story)

After not being able to install an ATI graphic card, I got one of nVidia, hoping that it may work better (or work at all..).

After some tinkering I managed to get the computer starting with the nVidia card. its nVidia Quatro FX 3400 with two DVI connections. 
So far so good.

At first the card didnt work (only on windows, it's a dual boot machine). so I looked for a solution here and found some instructions how to install the driver using a terminal (or root shell). so I tried three drivers before I understood the problem was a missing power cord. once I pluged it in, the computer finally worked but the resolution was wrong.
So I got into the display and the nVidia config window opened. I managed to change the resolution to what I wanted (1680x1050) but I got a massage saying it cant save the changes. so the computer work with what I chose but after a restart it goes back to something else.

I looked in the 'Hardware driver' window and saw I heve 3 different nVidia drivers installed but none of the was active and I could not activate any of them.
So I opened synaptic removed two and left installed the one that had the word 'recommended' next to it in the 'Hardware driver' window. also I did a search in synaptic for my card and installed something else regarding the recommended driver. when I opened the 'Hardware driver' window again it presented this driver as active. this driver is driver version 185.

However, today when I stated the computer again the resolution again was not right and again when I changed it through the nVidia config window I got a massage saying the changes cant be saved.

Does anybody know what can be the problem? 
Many thanks in advance!

---

### Post by mickie.kext on 2010-02-25
> **anigodin said:**
> 

However, today when I stated the computer again the resolution again was not right and again when I changed it through the nVidia config window I got a massage saying the changes cant be saved.



Here is what you do about that. Open terminal (top paned, Applications --> Accessories --> Terminal) and type (or paste):

```
sudo nvidia-settings
```

It would ask about password and when you type NVIDIA X Server setting window will show up and now you can set resolution.

Explanation: When you start nvidia-settings normally, you are not privileged user so you can not make changes that could affect other users of computer. When you start with "sudo" in terminal, you do stuff as Administrator and you get to do what you want.

---

### Post by anigodin on 2010-02-25
Off course...

Silly me :-)

Thank you!

---

