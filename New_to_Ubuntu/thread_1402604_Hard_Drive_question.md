---
title: "Hard Drive question"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by Extract_Here on 2010-02-09
I have two hdds 1 has winxp the other has 9.10. when im using karmic i dont want the other hard drive to be on and spinning the same when im on windows. I dont want to have to disconnect them from the power supply every time i dont want one of them on. So is there a way to turn one of them off without opening up the case? 

thank you in advance;)

---

### Post by warfacegod on 2010-02-09
Unmount it.

---

### Post by warfacegod on 2010-02-09
Sorry, in Windows it's "Safely Remove Hardware..."

---

### Post by tom.swartz07 on 2010-02-09
> **Extract_Here said:**
> I have two hdds 1 has winxp the other has 9.10. when im using karmic i dont want the other hard drive to be on and spinning the same when im on windows. I dont want to have to disconnect them from the power supply every time i dont want one of them on. So is there a way to turn one of them off without opening up the case? 

thank you in advance;)

Im not too sure about what you could do on the Windows level, perhaps just "safely remove" the drive -i.e. unmount it?


Of course, you could always do a casemod and add in a little power switch for your other drive! :popcorn:

---

### Post by Extract_Here on 2010-02-09
when im on windoze xp it doesnt even show the other hdd does that mean its not on?

---

### Post by cascade9 on 2010-02-09
Nah, thats probably just XP has no idea what EXT3/4 is (or whatever filesystem you are using).

---

### Post by tom.swartz07 on 2010-02-09
> **Extract_Here said:**
> when im on windoze xp it doesnt even show the other hdd does that mean its not on?

I wouldnt go that far. It may not 'see' it, but im sure it knows that somethings there. 

I forgot about the fact that Microsoft doesnt recognize ext filesystems.

Im afraid im out of solutions! 
:bows out gracefully:

---

### Post by Extract_Here on 2010-02-09
Okay, do you think its bad that the other one stays up and running? 

Also I have to change my boot order every time to decide which one to boot too. Is there a solution to that?

Is it possible that I could disable the other hdd in the bios and it wouldn't start up?

---

### Post by tom.swartz07 on 2010-02-09
> **Extract_Here said:**
> Okay, do you think its bad that the other one stays up and running? 

Also I have to change my boot order every time to decide which one to boot too. Is there a solution to that?

Is it possible that I could disable the other hdd in the bios and it wouldn't start up?

It certainly shouldnt hurt the drive unless you pick up the whole case and dropkick it down a flight of stairs. 

The drives are made to spin for a long time, and for the most part if the drive isnt being read from/written to it should go to slow spin or stop after a period of time.

---

### Post by warfacegod on 2010-02-09
> **Extract_Here said:**
> Okay, do you think its bad that the other one stays up and running? 

Also I have to change my boot order every time to decide which one to boot too. Is there a solution to that?

Is it possible that I could disable the other hdd in the bios and it wouldn't start up?

Aside from the power consumption, there isn't anything "bad" about letting it spin.

You'll need to be more specific about you second question.

You *could* disable it from the BIOS but if you wanted to use it again, you'd have to go back and enable it again. Not much of a solution.

In Windows, you can tell it to "Spin down discs when not in use". Frankly, I don't remember how to do that but it's probably in power management somewhere.

---

### Post by warfacegod on 2010-02-09
Tom, wouldn't your VGA converter thingy work here?:tongue:

---

### Post by Extract_Here on 2010-02-09
Do you think its bad for my comp that when i want to boot into windows i have to go into the bios and change which hard drive to boot from or is that okay? If its bad what should i do?

---

### Post by warfacegod on 2010-02-09
> **Extract_Here said:**
> Do you think its bad for my comp that when i want to boot into windows i have to go into the bios and change which hard drive to boot from or is that okay? If its bad what should i do?

It's okay for your computer, it just sounds like a royal pain.

Next time you are in Ubuntu, make sure your Windows drive is mounted, then open a Terminal:

```
sudo update-grub
```

---

### Post by Extract_Here on 2010-02-09
What will that do? 

Im primarily in linux all the time i just play games on windows.

---

### Post by cascade9 on 2010-02-09
> **Extract_Here said:**
> Okay, do you think its bad that the other one stays up and running? 

Also I have to change my boot order every time to decide which one to boot too. Is there a solution to that?

Is it possible that I could disable the other hdd in the bios and it wouldn't start up?

Provided that you have power savings (or however your manufacturer phrases it) on, the HDD will spin downa nd park after 'x' amount of minutes. You can change that 'x' figure in the BIOS with every modern machine I've ever seen. 

You could probably either play with grub or the windows bootloader so that you dont need to change boot order to boot to a different OS. Its not any sort of problem to go into your BIOS and change the booting drive though. 

You could possibly change your BIOS so that the unused drive isnt detected, but that could mean that your HDD will just spin forever (depending on your BIOS). Thjat would be bad. Anyway, its a right pain in the butt, it makes changing boot order seem almost fun.

---

### Post by tom.swartz07 on 2010-02-09
> **warfacegod said:**
> Tom, wouldn't your VGA converter thingy work here?:tongue:

hardy har har. :P

---

### Post by Extract_Here on 2010-02-09
That term. cmd helped a lot now i don't have to go into the bios it just gives me a menu of which to boot too. Thanks all of you guys for your information and suggestions. Now I feel better about my computer situation. Thanks a ton again!!:popcorn::):o

---

### Post by cascade9 on 2010-02-09
> **Extract_Here said:**
> Thanks all of you guys for your information and suggestions. Now I feel better about my computer situation.

No problems, good to see another happy customer. That is over 15 now! :biggrin:

---

### Post by warfacegod on 2010-02-09
Take me off the list, I'm not happy anymore.:tongue:

---

### Post by warfacegod on 2010-02-09
> **Extract_Here said:**
> What will that do? 

Im primarily in linux all the time i just play games on windows.

Hopefully it will add Windows to your GRUB menu so that all the hassle is removed from choosing which OS you want to boot into.

---

### Post by cascade9 on 2010-02-10
> **warfacegod said:**
> Take me off the list, I'm not happy anymore.:tongue:

*lie mode engaged*  OK, your removed from the list.....so your happy now and I can readd you? :P 

Honestly, sorry, you werent on the list. Your happiness is obsolete anyway :P

---

### Post by warfacegod on 2010-02-10
> **cascade9 said:**
> *lie mode engaged*  OK, your removed from the list.....so your happy now and I can readd you? :P 

Honestly, sorry, you werent on the list. Your happiness is obsolete anyway :P

Every computer in my house is obsolete and will stay that way unless I decode to solder any new graphics card into my laptop.:twisted:

---

