---
title: "CPU Temperature info"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by myolbug on 2009-05-31
I am running 9.04 64bit on a desktop. I want to know if I can monitor temps on my CPU etc without having to go into the BIOS to look at it.  I tried XSensors but it just gives me blank window.

FYI I have: AMD Athlon(tm) 64 X2 Dual Core Processor 4400+
            GeForce 6150SE nForce 430
            MSI K9N6PGM2-V motherboard
The computer is only a few months old.  The BIOS is whatever version it shipped with, I don't want to reboot right now.

Thanks

---

### Post by Arup on 2009-05-31
sudo apt-get install lm-sensors hddtemp gkrellm

sudo sensors-detect

say yes to all probes and then you have to hit enter twice and final yes to write to config file.

Reboot and fire up gkrellm from applications>system tools and select all the sensors of your choice. You need to have medibuntu repos enabled from [www.medibuntu.org](www.medibuntu.org)

---

### Post by sodainmay on 2009-05-31
sudo apt-get install acpi
when you installed acpi ,you can acpi -t to check cpu temperature ,and man it to get a further use

---

### Post by presence1960 on 2009-05-31
as you can see there are a few. In Synaptic install sensors applet or in terminal run > sudo apt-get install sensors-applet
Once installed right click on your gnome panel, select add and choose Hardware Sensors Monitor. Add to your Panel. Right click and choose preferences to configure. 

Note these will always be in your Panel.

---

### Post by myolbug on 2009-05-31
I have used the one given by Arup.  I like it and it gives me a way of keeping tabs on everything, 
Thanks

---

