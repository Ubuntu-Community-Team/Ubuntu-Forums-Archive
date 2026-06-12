---
title: "Running hot"
date: 2010-08-07
forum: New to Ubuntu
---

### Post by L2U2K2E on 2010-08-07
I am new to ubuntu and running lucid on a msi GX630 laptop. My computer seems to be running much too hot, even during idle, but much more so when moving files. Is there anything I can do to fix this? I temperature control program or some sort of CPU scaling?



thank you. feel free to ask for more info, but please tell me where to find it. ubuntu is still unfamiliar to me.

---

### Post by aidenscool09 on 2010-08-07
Try adding the CPU Scaling Monitor applet to your GNOME Panel. (Right click the bar at the top in a blank area and select Add to panel...) and add it there. Then try lowering it to a lower setting.

---

### Post by L2U2K2E on 2010-08-07
thank you! Thats fairly helpful. now I can limit the usage of my CPU. any other useful tips?

---

### Post by Mrandersonjr on 2010-08-07
Check your idle and critical temperatures in the bios, it might be set too high.
Optionally, try installing cpu-freq-utils. Or acpi. If acpi is already install, it could be that the critical temperature is set too high, it reads off the bios critical temperature, so adjust that, and you should have a cooler computer. If that doesn't work, try a lighter window manager like xfce or fluxbox.

---

### Post by L2U2K2E on 2010-08-08
In my bios there doesn't seem to be any way to adjust my critical temperatures or even view them.

---

### Post by bodhi.zazen on 2010-08-08
Either there is an aberrant process using excessive CPU or you may need to clean the laptop. Make user the fan is working and the vents are clean.

You can use top to determine if there is a process using excessive CPU.

---

### Post by L2U2K2E on 2010-08-09
I'm sorry, You guys are a little over my head. What is TOP? cpu-freq-utils? acpi?   I'm not sure how to check any of these things


Also, I am aware that my laptop might require cleaning, but If I open it I will void my warranty   :/

---

### Post by Ozymandias_117 on 2010-08-09
> **L2U2K2E said:**
> I'm sorry, You guys are a little over my head. What is TOP? cpu-freq-utils? acpi?   I'm not sure how to check any of these things


Also, I am aware that my laptop might require cleaning, but If I open it I will void my warranty   :/

top is a command line utility that will show what processes are using the most processor power. acpi is a program that runs in the background and automatically scales your processor back (Among other things).

---

### Post by L2U2K2E on 2010-08-09
The top command does not show anything alarming. Xorg is the only program even noticeably using system resources.

acpi does confuse me though. when I type "acpi" in the terminal, it comes back with "Battery 0: Charging, 71%, 00:36:05 until charged"
That doesn't seem to have any information except about the battery.

I'm confused. what should I be doing?

---

### Post by Peter09 on 2010-08-09
There are two useful apts for a laptop which may help.
 
[http://packages.ubuntu.com/lucid/laptop-mode-tools](http://packages.ubuntu.com/lucid/laptop-mode-tools)
 
```
sudo apt-get install laptop-mode-tools
```
 
and
 
Powertop
 
```
sudo apt-get install powertop
```
 
laptop-mode-tools makes sure your laptop is set to laptop mode, while running powertop in a terminal will show you what is using power on your system. 
 
All these things contribute to your machine getting hot. Obviously if you are asking it to do some serious work its going to get hot whatever you do.

---

### Post by vitothegreat on 2010-08-09
Your laptop needs to get cleaned. I've had the same problem for about 6 months and I always thought that the overheating is due to excessive CPU usage, however, last week my laptop started rebooting randomly and I found out that the CPU was overheating. So I cleaned the cooler, applied new thermal grease and it now works perfectly.
If your laptop is still under warranty then just take it where you bought it and have guys clean it.

---

### Post by bodhi.zazen on 2010-08-09
> **vitothegreat said:**
> Your laptop needs to get cleaned. I've had the same problem for about 6 months and I always thought that the overheating is due to excessive CPU usage, however, last week my laptop started rebooting randomly and I found out that the CPU was overheating. So I cleaned the cooler, applied new thermal grease and it now works perfectly.
If your laptop is still under warranty then just take it where you bought it and have guys clean it.

This ^^

---

### Post by L2U2K2E on 2010-08-10
^^  that seems to be exactly the answer. thank you. Apparently my warranty is up so I need to do everything myself though. I opened up my laptop as much as I could and sprayed it down with compressed air which worked great and already has lowered the temperature. 

I also bought I syringe of thermal paste, but I am not sure what to do with it. Any guidance on that? I am much more clueless on laptops than I should be.

---

### Post by Mobidoy on 2010-08-10
> **L2U2K2E said:**
> ^^  that seems to be exactly the answer. thank you. Apparently my warranty is up so I need to do everything myself though. I opened up my laptop as much as I could and sprayed it down with compressed air which worked great and already has lowered the temperature. 

I also bought I syringe of thermal paste, but I am not sure what to do with it. Any guidance on that? I am much more clueless on laptops than I should be.

You have a heatsink on your laptop CPU, you should remove it and, use a dry cloth to remove old thermal paste from your CPU and the heatsink then, you apply some thermal paste (pea size) on the cpu, put back the heatsink and you are done. The heatsink when put back will take care of spreading the paste on all the surface. Dont put too much though so it does not get all over.

You can look [this page]("http://www.insidemylaptop.com/apply-thermal-grease-laptop-processor/") to get a good idea.

---

### Post by vitothegreat on 2010-08-11
Here are a few great references on how to apply thermal paste:

[http://www.hardwaresecrets.com/article/How-To-Correctly-Apply-Thermal-Grease/274/5](http://www.hardwaresecrets.com/article/How-To-Correctly-Apply-Thermal-Grease/274/5)

[http://www.techpowerup.com/printarticle.php?id=134](http://www.techpowerup.com/printarticle.php?id=134)

Also, I suggest you clean the cooler very well. There is usually some dust in parts you don't normally see from the outside, so you have to take out the fan and apply compressed air from the inside of the cooler. Then clean the remaining dirt with a paper towel or anything you're comfortable with. Clean the fan itself too. 
If you're not very familiar with laptops and particularly with coolers, just know that there's nothing you can mess up, so do it with confidence ;)

---

