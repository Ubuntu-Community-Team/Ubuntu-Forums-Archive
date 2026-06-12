---
title: "My touch pad stopped working!"
date: 2010-07-29
forum: New to Ubuntu
---

### Post by 7azem on 2010-07-29
So i noticed that this problem started by the time i installed a new touch pad driver for my Windows OS. When I switched to Ubuntu, the touch pad wasn't working for some reason, It's not the Function key, and I went to the website of the company that I installed the driver from to install a new one for my Ubuntu, but there are no Based on linux drivers!

Putting in mind that it was working before that!

So is there anyway that i see what are my missing drivers for my hardware inside Ubuntu? .. something like the Hardware manager in Windows!

and if it helps, would it solve the problem if i downloaded any based on linux driver from the internet?

Btw, the driver I'm using on Windows is from Synaptics.
and My Computer is an LG Netbook 110, with the Ubuntu Desktop Version!

please help! and thank you very much! :)

---

### Post by LunaticHiatus on 2010-07-29
Linux is a monolithic kernel. Which means the drivers are applied to the kernel itself so almost every driver is built in and should work out of box with the exception of certain proprietary drivers such as Graphics card and Broadcom wireless drivers.

However, I'm not real sure what your implying. It seems like you said that your touchpad ceased to work when you installed adriver for it on windows. Which makes it sound like your dualbooting windows and ubuntu. If you installed a driver on your sides side of your dualboot, it would have no effect on the ubuntu side.

---

### Post by 2uk_ on 2010-07-29
I'm not sure if it will help but it worked for me when this happened in Windows.
You should have automatic system restore points.
Restore the system to the most recent one.

Also try going into synaptics, click 'custom filters' and then 'broken'
if there is something wrong it might show up here

---

