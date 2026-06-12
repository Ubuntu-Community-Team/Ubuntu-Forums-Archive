---
title: "Power Draw / Wattage program?"
date: 2011-07-04
forum: New to Ubuntu
---

### Post by Dubslow on 2011-07-04
Hey there,
I'm looking for a program that will tell me how many watts I'm using at a given time. I've tried powertop, but that says "no ACPI power usage estimate available". I'm pretty sure it's because I have an AMD processor, but whatever it is, it's not working. Does anybody know any other program I can use?

---

### Post by rosencrantz on 2011-07-05
Desktop or laptop?
For a laptop, do 
cat /proc/acpi/battery/BAT0/state
in a terminal.
According to this page
[http://tombuntu.com/index.php/2008/09/09/reduce-power-usage-with-powertop/](http://tombuntu.com/index.php/2008/09/09/reduce-power-usage-with-powertop/)
powertop should work with AMD. However, I get the 'no ACPI estimate' message too when I plug in my power cable.

---

### Post by Dubslow on 2011-07-05
Desktop. 600 watt PSU, AMD Phenom II X6 Thuban 1055 (Six core 2.8 GHz)

---

