---
title: "Desktop lag"
date: 2009-08-29
forum: New to Ubuntu
---

### Post by exicer on 2009-08-29
I get lag when maximizing windows in ubuntu, and am unsure why! This is a fresh install, and I have done nothing other than install some packages. The problem occured even before this was done, however.

[http://www.youtube.com/watch?v=1Uyl5Ovve0Q](http://www.youtube.com/watch?v=1Uyl5Ovve0Q)

Don't know if the video helps! Listen to when the click occurs compared to when the window maximizes.

Thanks.

---

### Post by s.fox on 2009-08-29
Hi,

Could you tell us more about your specifications of your hardware?

Many thanks,

-Silver Fox

Edit:  Could be graphics driver,  hardware spec will help us out here. :D

---

### Post by exicer on 2009-08-29
Yup. Running Asus p5kc mobo, intel qc 6700, ati radeon 4870, 4gb ddr2 ram.

Hope that helps.

---

### Post by scrooge_74 on 2009-08-29
I see the windows coming up and down pretty fast, what is wrong with that? Want more responsiveness? Don't use desktop effects

---

### Post by exicer on 2009-08-29
Well, if you listen to when I click the mouse and compare it to when the window maximises, there is enough of a lag that it might get annoying (for me anyway!). In any case, it doesn't occur in windows so I'm sure it doesn't have to occur in Ubuntu! 

Ps There is no issue with minimizing.

---

### Post by exicer on 2009-08-30
No one has any ideas? :(

I tried switching desktop effects to all different levels, but to no avail. I also tried changing the driver to the proprietary version, same problem.

---

### Post by tgeer43 on 2009-08-30
It's an apparent bug in Jaunty affecting various Radeon cards which can be read about here:

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/381003](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/381003)

Check out post #3 for an easy workaround.

tgeer

---

### Post by exicer on 2009-08-30
I tried installing the XServer with no backfill - but there seems to be no improvement. I do not know how to confirm if I installed this correctly, however - can anyone tell me how? :)

---

