---
title: "Built in wireless not recognizing networks"
date: 2010-01-06
forum: New to Ubuntu
---

### Post by hockeymonkey8424 on 2010-01-06
Hi all. I am very new to ubuntu. I installed it after my hp laptop with vista 32-bit crashed and wouldnt restore or even re-load vista off of a disc. I then installed Ubuntu but i have not had any luck connecting to my wireless network. any suggestions would be appretiated.

---

### Post by Zoot7 on 2010-01-06
What sort of Wireless card do you have?

---

### Post by -kg- on 2010-01-06
Also, what is the model number of your laptop?  There are various guides for HP laptops available on the site.

To find the wireless "card" that you have installed, open a terminal window (Applications/Accessories/Terminal - on the top toolbar at the left) and enter the command below:

```
lspci
```

Either copy and paste the results here (if possible) or write down the type of wireless card you have from the list of devices shown.

---

### Post by hockeymonkey8424 on 2010-01-07
The computer is a HP pavillion dv2000 laptop. Im going to be honest i typed the code into the terminal and i dont know what half of the stuff that comes up means. But from what i got out of it I believe that it is an AMD K8 [athlon64/opteron] wireless card.

---

### Post by mikewhatever on 2010-01-07
> **hockeymonkey8424 said:**
> The computer is a HP pavillion dv2000 laptop. Im going to be honest i typed the code into the terminal and i dont know what half of the stuff that comes up means. But from what i got out of it I believe that it is an AMD K8 [athlon64/opteron] wireless card.

That looks more like the CPU, but it shouldn't be showing in lspci. You should post all of the output if possible. If there is no internet on that computer, write the output to a file with <lspci > ~/Desktop/lspci.txt>, then grab lspci.txt from the Desktop and attach to your next post.

---

### Post by derekmbarnes on 2010-01-07
> **mikewhatever said:**
> That looks more like the CPU, but it shouldn't be showing in lspci. You should post all of the output if possible. If there is no internet on that computer, write the output to a file with <lspci > ~/Desktop/lspci.txt>, then grab lspci.txt from the Desktop and attach to your next post.

Also: Terminal labels the wireless card as "Network controller;" it should be near or at the bottom of the list. Example:

```
07:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)

```

---

### Post by LuisGMarine on 2010-01-08
By "not recognizing" your networks you mean that you can't see them listed under networks right?  Or you see them and you just can't connect to them?

---

