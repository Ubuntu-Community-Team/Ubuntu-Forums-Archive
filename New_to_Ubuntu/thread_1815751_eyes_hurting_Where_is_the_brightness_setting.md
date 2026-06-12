---
title: "*eyes hurting* Where is the brightness setting?"
date: 2011-07-31
forum: New to Ubuntu
---

### Post by WubiAR on 2011-07-31
Hello,

I just recently installed Xubuntu 11.04 and I want to adjust the  brightness levels. I tried using the corresponding buttons on my laptop,  but they aren't working. Where can I find the brightness settings on  the OS?

I tried this thread: [http://ubuntuforums.org/showthread.php?t=794362](http://ubuntuforums.org/showthread.php?t=794362) , but "Power Manager" didn't have that setting. The laptop I am using is a Dell Inspiron 15R.

---

### Post by Toz on 2011-07-31
Open a terminal window and type in the following command:
```
lsmod | grep i915
```
If it returns a result, then this kernel might help:[https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight]("https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight")

---

### Post by WubiAR on 2011-08-01
> **Toz said:**
> Open a terminal window and type in the following command:
```
lsmod | grep i915
```If it returns a result, then this kernel might help:[https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight]("https://launchpad.net/%7Ekamalmostafa/+archive/linux-kamal-mjgbacklight")


I see. I ran the commands through the terminal, and downloaded the packages for that PPA. However, my brightness keys still do not work. I am going to try out the Kernel Boot procedure tomorrow. Do you have any other suggestions? I see you have the same distro. and are running the same version. What model is your system? Were you able to get your brightness settings working, or were they already working? I installed Xubuntu 11.04 on my Toshiba laptop and the brightness keys are already working fine for that.

---

### Post by pierreyy on 2011-08-01
hey i dunno much bout xubuntu but on my laptop (ubuntu) its Fn+ F6/F7   hope it works...

---

### Post by Toz on 2011-08-01
> **WubiAR said:**
> I see. I ran the commands through the terminal, and downloaded the packages for that PPA. However, my brightness keys still do not work. I am going to try out the Kernel Boot procedure tomorrow. Do you have any other suggestions? I see you have the same distro. and are running the same version. What model is your system? Were you able to get your brightness settings working, or were they already working? I installed Xubuntu 11.04 on my Toshiba laptop and the brightness keys are already working fine for that.

Did you run these commands?
```
sudo add-apt-repository ppa:kamalmostafa/linux-kamal-mjgbacklight/ppa
sudo apt-get update
sudo apt-get dist-upgrade

```

What says:
```
uname -r
```

I have a Compaq 8510p and the brightness keys work out of the box. Can you also try the following:

1. Check your bios to see if there are any settings in there about brightness that might be preventing the function keys from working. (Or possibly a bios update?)

2. Try out the following kernel parameters:
```
acpi_backlight=vendor
acpi_osi=Linux
acpi_osi=\"Linux\"
```

If it still doesn't work, open a terminal window, type in the following commands, and post back the results:
```
lspci -vnn
sudo dmidecode -s system-product-name
```

---

### Post by JC Cheloven on 2011-08-05
I think I posted [here]("http://ubuntuforums.org/showthread.php?p=11122964#post11122964") a nice solution. Hope it helps.

---

### Post by MarjaE on 2011-10-17
I've got working brightness keys but not the same brightness range I had in standard Ubuntu. Right now it's at minimum brightness and my eyes are hurting because the white is too bright. This is NOT a Toshiba Toobrite! I had made sure I could dim the screen to usable levels before accepting this machine.

---

