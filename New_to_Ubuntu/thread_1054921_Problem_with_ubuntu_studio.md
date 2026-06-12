---
title: "Problem with ubuntu studio"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by Yannick0 on 2009-01-30
Hi
I've used now ubuntu for 2 weeks and I decided to install ubuntu studio. But, when it's installed, I don't see any desktop, just a black srceen with the terminal. 
Can anyone tell me what I did wrong?

---

### Post by neu2buntu on 2009-01-30
did you install ubuntu-studio on its own or inside your ubuntu through synaptic?

---

### Post by Yannick0 on 2009-01-30
I downloaded the iso image and burned it on DVD. I installed it in it's own partiton

---

### Post by neu2buntu on 2009-01-30
havnt installed it on its own yet,so not 2 sure you could always install it inside your ubuntu through the synaptic manager,  i dont know if it is a terminal login as default... u could always try >Ctrl > Alt >backspace to see if it lets u log in to desktop?




try in the terminal ```
login
```
or ```
startx
```  or key in Alt f7 perhaps

---

### Post by LowSky on 2009-01-30
the command **startx **should get you to the GUI if you cave a cursor screen, if not, you will need to reboot and try the recovery option and choose xfix.

If you want ubuntu can be upgraded to Ubuntu studio by adding a  few packages from synaptic or the following command will install everything studio can offer.

```
sudo apt-get install ubuntustudio-desktop ubuntustudio-graphics ubuntustudio-video ubuntustudio-plugins ubuntustudio-audio
```

---

### Post by Lunx on 2009-01-30
> **LowSky said:**
> the command **startx **should get you to the GUI if you cave a cursor screen, if not, you will need to reboot and try the recovery option and choose xfix.

If you want ubuntu can be upgraded to Ubuntu studio by adding a  few packages from synaptic or the following command will install everything studio can offer.

```
sudo apt-get install ubuntustudio-desktop ubuntustudio-graphics ubuntustudio-video ubuntustudio-plugins ubuntustudio-audio
```

I just installed a heap of stuff straight from synaptic, currently downloading the audio package. I think it probably best if you install inside Ubuntu, then if you have compatability probs etc, it should be easier to remove the offending packages.

---

### Post by LowSky on 2009-01-30
actualy you could do the same thing in studio as it really isn't anything but preinstalled packages. just add the package ubuntu-desktop, and remove the studio packages.

---

### Post by Yannick0 on 2009-01-30
It was the desktop which wasn't installed. Now it works, thank you

---

