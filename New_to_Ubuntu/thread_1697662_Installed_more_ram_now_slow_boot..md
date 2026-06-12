---
title: "Installed more ram now slow boot."
date: 2011-03-01
forum: New to Ubuntu
---

### Post by sb23 on 2011-03-01
Hello,

I have only been running ubuntu (10.10 64 bit) for a couple of days. I recently went from 4gb ram to 8gb. Now when i boot it takes for ever. It will load the login screen lightly slower than 4gb ram but then the mouse and keyboard will be unresponsive for over a minute ( the lights on my mouse MS sidewinder dont even go on). after i log on everything is fine.

Sorry for the lack of information , help would be greatly appreciated.

Thanks

---

### Post by seawolf167 on 2011-03-01
[LIST=1]
[*]Are the RAM DIMMs the correct speed for your motherboard?
[*]Are the DIMMs the same speed as eachother?
[*]Are the DIMMs set in BIOS to run at the same speed as eachother?
[*]Have you checked to ensure there are no faulty addresses?
[/LIST]
To check for bad RAM:
When you go to bed tonight or have a couple hours you don't need to use your computer, run the "MemTest" entry in the GRUB menu instead of selecting to boot into Ubuntu. Let it run overnight and after a couple hours (or in the morning) check to see if there are any errors that have surfaced. There may be some bad RAM sectors.

---

### Post by pressko on 2011-03-01
i want to test my RAM 2 . Can u tell me how to enter in the GRUB's menu ?

---

### Post by seawolf167 on 2011-03-01
> **pressko said:**
> i want to test my RAM 2 . Can u tell me how to enter in the GRUB's menu ?

The GRUB menu should display automatically upon starting up your computer. If it doesn't, you'll need to edit the config file

```
sudo gedit /etc/default/grub
```

and change the first lines to be something like this:

```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
```

Once you have made those changes, run

```
sudo update-grub
```

and you'll be able to see it upon reboot

---

### Post by sb23 on 2011-03-01
> **seawolf167 said:**
> 
[LIST=1]
[*]Are the RAM DIMMs the correct speed for your motherboard?
[*]Are the DIMMs the same speed as eachother?
[*]Are the DIMMs set in BIOS to run at the same speed as eachother?
[*]Have you checked to ensure there are no faulty addresses?
[/LIST]
To check for bad RAM:
When you go to bed tonight or have a couple hours you don't need to use your computer, run the "MemTest" entry in the GRUB menu instead of selecting to boot into Ubuntu. Let it run overnight and after a couple hours (or in the morning) check to see if there are any errors that have surfaced. There may be some bad RAM sectors.

Hi All the ram is the correct speed, ddr3 1333mhz and i have set the voltage to 1.5v and had a look at the timings and they seem correct, i am no expert though. The ram is all the same, kingston valueram. Do you want me to run memtest on them?

Thanks

---

### Post by seawolf167 on 2011-03-01
> **sb23 said:**
> Do you want me to run memtest on them?

I suggest doing this anytime you replace, upgrade or change the RAM in any system. Many headaches can be solved knowing that it is/isn't your RAM. I've had to RMA numerous DIMMs because they were not 100% from the factory.

---

### Post by Immolatus on 2011-03-01
What mobo are you running? AMD/Intel. I ask because some motherboards require you run speeds above 1066(ddr2 or ddr3) in dual channel mode. This means RAM only installed in first and third slot from CPU. If this is the case, your mobo will auto scale back the RAM speed to 1066(native), this is a noticable difference.

---

### Post by pressko on 2011-03-01
> **seawolf167 said:**
> The GRUB menu should display automatically upon starting up your computer. If it doesn't, you'll need to edit the config file

```
sudo gedit /etc/default/grub
```and change the first lines to be something like this:

```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
```Once you have made those changes, run

```
sudo update-grub
```and you'll be able to see it upon reboot


Man , 

Everything is like u said but no GRUB menu ... any suggestions ?

---

### Post by davidmohammed on 2011-03-01
if you are using grub2 (default in lucid and maverick) then just press and hold the shift key immediately after power-on.  This will display grub and the kernels & memtest options

---

### Post by sb23 on 2011-03-01
just an am3 motherboard, ill run memtest tonight. how long should i run it for and if it has errors does this mean that is the problem?

---

### Post by seawolf167 on 2011-03-01
Just leave it on overnight, the more cycles is runs the better (time won't hurt you here - when I'm testing a new overclock scheme I'll typically run my last stable settings for ~50 hours or more to ensure everything is rock solid)

If you get any errors in memtest, return the RAM, its not worth trying to parse out that bad address if you just bought it

---

