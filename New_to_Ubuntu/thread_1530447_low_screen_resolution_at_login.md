---
title: "low screen resolution at login"
date: 2010-07-13
forum: New to Ubuntu
---

### Post by Arkish0 on 2010-07-13
hello! im runing ubuntu 10.04 on my laptop ive been having a problem ..maybe 1 time every 10 times i turn on my computer (or return to login screen after restart) the resolution of my screen changes to a lower one.. if i proceed to input the password and enter to my desktop its all weird.. the elements and panels are missplaced due to the low resolution..i can fix this in two ways.. 

once i log in i just change the monitor resolution .. but then i have to put in place all the elements in my desktop and panels on their appropriate place

the other way is to restart the computer when i see the low resoultion at the login screen.. after restarting normally it gets ir rigth and if i put the password it will show my desktop just as it should....

is there any way to fix this? .. i dont want to restart my computer every time i see this hahahah


BTW as i said this never happens once im logged in .. just when i start my computer

thenks! =)

---

### Post by TechBeastie on 2010-07-13
Check to see if you have an xorg.conf file (usually located at /etc/X11/xorg.conf).  If you don't, you might want to create one with your desired resolution set as the default.   [See this page]("https://wiki.ubuntu.com/X/Config/Resolution#Setting%20resolution%20changes%20in%20xorg.conf") for more detailed instructions.  

Good luck!

---

### Post by Arkish0 on 2010-07-14
yess! i didnt have the xorg.conf file, i googled this name and i found lots of information on how to do it! but i think it really depends on your computer so i guess there is no need to put my file here!  

thanks so much =)

---

