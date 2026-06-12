---
title: "Internet Puzzle..."
date: 2009-11-07
forum: New to Ubuntu
---

### Post by Desert Sailor on 2009-11-07
I could sure use some help from the Ubuntu Guru's here assembled.  Here is the puzzle.  I am dual booting Win-xp on one partition, and a new fresh install of 9.10 on my second partition.  Both systems boot and seem to work perfectly except for Internet access. 

I am in the process of switching from Comcast to Qwest DSL. (The Comcast in my neighborhood is grossly over sold and while it works great in the mornings, by afternoon it isn't much better than dial-up) I configured my Qwest Actiontec modem using the install disk in the Windows partition, and it works fine there, but when I switch to Ubuntu 9.10 it doesn't work.  Ubuntu sees the eth0 connection and reports it's connected, but when you open FireFox, no pages will load. 

Now here's the kicker....  If I go back to the Comcast connection, (reboot the modem and system) Ubuntu works fine (that's how I am typing this now), 

I still have 9.04 on another partition and I think I will try that with the Quest DSL and report.  

If there is something simple that I am missing, please let me know.  This just doesn't make sense that one provider would work and the other one wouldn't.

---

### Post by yeats on 2009-11-07
> I configured my Qwest Actiontec modem using the install disk in the Windows partition, and it works fine there, but when I switch to Ubuntu 9.10 it doesn't work. Ubuntu sees the eth0 connection and reports it's connected, but when you open FireFox, no pages will load.

It's possible that your new router is not letting Ubuntu through because it is a different OS behind the same MAC address.  Some routers are configured to reject that by default.  See if your new router outputs any logs that might confirm (or negate) this.

---

### Post by quickdraw on 2009-11-07
I'm no guru, but I do remember that DSL was actually ppoe.

[http://www.techotopia.com/index.php/Connecting_an_Ubuntu_Linux_System_to_a_DSL_Modem](http://www.techotopia.com/index.php/Connecting_an_Ubuntu_Linux_System_to_a_DSL_Modem)

See if that helps you. I hope it does.

---

### Post by Desert Sailor on 2009-11-07
Thanks Chris, I'll try to check this, the DLS Modem is a POS Actiontec supplied by Quest, I have a new modem on order, and hope it will solve the problem.  

However, I did test one other question.  I still have my old 9.04 install as a boot option and when I boot 9.04 everything works fine.  In fact, I am typing this now from my 9.04 install on my Qwest DSL network.  So I don't think it's a OS problem, but rather something different in 9.10.  

Don't want to hijack my own thread, but it seems that 9.10 wasn't quite ready for prime time.  Perhaps, I'll just use 9.04 a little longer in hopes that they patch some of the 9.10 problems. 

I am a Linux newb, and have to rely on this forum and the updater to keep my system working.

---

### Post by yeats on 2009-11-07
> Don't want to hijack my own thread, but it seems that 9.10 wasn't quite ready for prime time. Perhaps, I'll just use 9.04 a little longer in hopes that they patch some of the 9.10 problems.

That sounds wise.  I always wait a bit (at least 2-3 weeks) before upgrading my "production" computers for this exact reason.  Paying attention to what people are reporting here on the Forums is a great way to learn what the bugs/common problems are.  Good luck ;-)

---

### Post by quickdraw on 2009-11-07
> **Desert Sailor said:**
> 
Don't want to hijack my own thread, but it seems that 9.10 wasn't quite ready for prime time.  Perhaps, I'll just use 9.04 a little longer in hopes that they patch some of the 9.10 problems.

That's why I never cared for cutting edge stuff like alphas, betas, and early releases. I can't figure things out for myself. lol.

---

### Post by yeats on 2009-11-07
> That's why I never cared for cutting edge stuff like alphas, betas, and early releases. I can't figure things out for myself. lol.

VirtualBox is a good way to run these and explore without risking anything important.  I've been running Ubuntu testing in VBox since January and it's fun to watch the system change/evolve.  Oh, and break! :-)

---

