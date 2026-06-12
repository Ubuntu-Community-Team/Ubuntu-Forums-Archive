---
title: "Wine won't work now..."
date: 2010-10-25
forum: New to Ubuntu
---

### Post by kip152 on 2010-10-25
The file is not marked as executable. Blocked Wine start

I was able to download and use Zet 8 with Wine on my old Ubuntu 9.04
10.10 will not allow this.
Any way around this?
CAUTION: I am not even a newbie, I'm a pre-fetus, as far as tech intelligence goes.

---

### Post by lindsay7 on 2010-10-25
Did you right click on the file and set it as executable under permissions.

---

### Post by kip152 on 2010-10-26
You mean right click on Zet 8? Nothing like set executable is there.

---

### Post by Rahul dev on 2010-10-26
hi 
this is working fine on my pc. You should install Wine 1.2 package and then right click at Zet 8 setup and open it with winhlp32.

that will work fine.

---

### Post by ronnielsen1 on 2010-10-26
> You mean right click on Zet 8? Nothing like set executable is there.

Right click > Choose Permissions tab and then click allow executing file as program

---

### Post by kip152 on 2010-12-05
When I right click setup exe all I get is:
Open
Open containing folder
Go to Download Page
Copy download link
Select all
Remove from list

---

### Post by kip152 on 2010-12-05
1st I downloaded and installed Wine. No problem. Then I downloaded Zet choosing 
open with Wine. That's when I got the no permission message. Then I downloaded Zet choosing save. Then I tried to open with Wine. Same message. When I right click Zet in downloads, there is no place to select permissions - it's just not there.

---

### Post by @TAN on 2011-01-08
Well there seems to be an issue working with the new wine version in  GUI. If you use the Terminal it will work fine. Just go to your  directory where the .exe file is located using the terminal and type  wine <file name you want to execute>. For those using GUI, wait  for the wine developers to find a solution.

---

### Post by vivek.pandey on 2011-01-08
> **ronnielsen1 said:**
> Right click > Choose Permissions tab and then click allow executing file as program

even i have similar problem i went permissions..but wen i tried to select the checkbox  allow executing file as a program...its not getting selected even though i m loged in admin acount.. pls help

---

