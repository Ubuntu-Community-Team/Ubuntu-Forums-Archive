---
title: "boot up"
date: 2011-03-07
forum: New to Ubuntu
---

### Post by ECET on 2011-03-07
OK...when I boot up...I have a dual boot system.....Ubuntu has 6 different "choices" for me to click on, versus windows with 2 choices. On the Ubuntu choices, 3 of the choices are "recovery"......I understand what these choices are...they are from when I have installed updates....my question is how do I remove the older "choices" I do not want to see all of this on bootup.....thanks.....

---

### Post by Foxheadz on 2011-03-07
Try running ```
sudo apt-get autoremove
``` then running ```
 sudo update-grub
```

---

### Post by ECET on 2011-03-07
I did this foxheadz...and I rebooted and I still have 6 "versions" of option/choices to pick from....this did not delete any of them.....please help...

---

### Post by Foxheadz on 2011-03-07
In synaptic look of linux image and delete all the ones you don't need (the ones with the lower numbers) then run sudo update-grub.

---

### Post by ECET on 2011-03-07
ok....I have synaptics manager....but I dont see where or how to find these images to delete them.....I am sorry for my ignorance...but I am learning as fast as I can....please advise as you would a child so that I may get this done tonite.....thanks again!

---

### Post by ECET on 2011-03-07
TTT.....sorry folks...I just want to try and get this one resolved before I head off to bed......

---

### Post by ECET on 2011-03-07
I still need help with this.....please advise.....

---

### Post by MrPok on 2011-03-08
Hi there,

A little google gave me this:
[http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/](http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/) 

Follow the steps. Really easy, you will have it done in minutes. ;)
I just did I myself again today.

---

### Post by Dutch70 on 2011-03-08
Either open synaptic & search for "image-2", mark the older ones for removal & apply. Be very careful not to remove the latest one. 

Or install Ubuntu tweak and it will remove your old kernels. However, It's a good practice to keep at least one old kernel in case of problems with a new one.

---

### Post by migrate from windows on 2011-03-08
Pls google for Grub Customizer and install ...its easy GUI helps to hide all unrequired lines.


or  add this ppa and install using software centre

 **ppa:danielrichter2007/grub-customizer**

---

### Post by ECET on 2011-03-08
Thanks guys.....these last few posts helped out tremendously.....I appreciate your help!.....

---

### Post by Dutch70 on 2011-03-08
> **ECET said:**
> Thanks guys.....these last few posts helped out tremendously.....I appreciate your help!.....

Great! Can you tell us the method that you used & mark this thread solved so others can find it?

---

