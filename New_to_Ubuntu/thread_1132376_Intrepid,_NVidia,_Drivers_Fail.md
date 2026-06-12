---
title: "Intrepid, NVidia, Drivers Fail"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by Ascendaeus on 2009-04-21
my "Problem" I'm Having A lot of trouble. Somebody Persuaded me, too install Intrepid, under the Pretenses that it works better for games, or something, and that took like two hours, and when it was done, automatic shut-down and re-start, then, it's all messed up, low graphics mode and what not.but i'm used to that, see, on hardy, every time i restarted, i would have to enter the terminal and stop gnome, sh the nvidia thing, and start gnome in order to get the graphics card running, now apparently i need to get off the 173 version get the 180 version, in the Software sources. i did that and got the Loki update, and that doesn't do anything,.. i can't open that, and that is not a directory, i don't know. yeah i'm an a-hole for not using google first or something, Here's My REAL Problem, Bought 1200$ worth of Computer parts from NEWEGG. Apparently, Windows Doesn't Like GEFORCE or GSkill or AMD or something and won't install, I can't enable any desktop effects and the damn thing has like, mood swings or something, one day i can full screen videos, the next day, if i try to do that, it will close that program, Now ive got my sources all messed up i ALWAYS have a RED download arrow for the upgrades, which Means, i think not to do it, uhhmm, this (LINUX) is VERY COMPLICATED how come,...... it doesn't work "well There could Be a THOUSAND Reasons for That, Junior!" if The (FREESOURCE) Society wants to bring an end to Microsoft's Stranglehold on the Video game industry, they will make their next OS with some Consideration, on this matter, the games. don't. work...............................................

---

### Post by ugriffin on 2009-04-21
Ok, ok, relax. Here's what to do:

Download the Linux drivers from NVIDIA.com.
move the drivers to your home folder and rename them to a simple name such as "drivers.run"
CTRL+ALT+F1
Type: "sudo /etc/init.d/kdm stop for kde and sudo /etc/init.d/gdm stop for GNOME.
Type: "sudo sh /home/yourusername/drivers.run"
Follow the instructions. Respond Yes to everything.
Type: "sudo /etc/init.d/kdm or gdm start"

You're good to go.

---

### Post by steve101101 on 2009-04-21
make sure you don't do anything without first thinking / researching otherwise you will just be worse off.

---

