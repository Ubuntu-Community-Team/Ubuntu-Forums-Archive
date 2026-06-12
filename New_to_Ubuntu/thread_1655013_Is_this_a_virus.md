---
title: "Is this a virus?"
date: 2010-12-29
forum: New to Ubuntu
---

### Post by Zundap on 2010-12-29
Hi, every one, i am having big problems with Ubuntu 10.10, it appears to be a virus to me, although i was given to unsderstand that its impossible to get a virus with UBUNTU. There are various problems that have recently started happening, they are as below.

Suddenly freezes sometimes, (but not always), when i am using Firefox and Open Office at the same time.

Some times, (but not always) in Open Office, when i try to scroll down the page only the top fraction of the page about 1/8th actually scrolls and when i try to scroll up, only the botom 1/8th of the page scrolls up. 

Some times (but not always) when i click in the google search box in the top right hand corner of Firefox, the courser takes off at speed moving to the right, leaving behind a trail of small dash's, i have to shut Firefox to stop it, strangely though this had not happened for a while.

Sometimes (but only very occasionally) its freezes, when installing updates.

Sometimes, when i am using Open Office, in fact quite regularly, when i click on the page i an writing on, instead of jut placing the curser on the page, it selects an amount of text and then and no matter what else i try to do, it just keeps selecting an amount of text.

Just now, i noticed an update notice was on the task bar, so clicked it and it asked for the password as usual, i put the password in and it said intalling up date, it went through update procedure, then gave a message saying that, i was already up to date and was last updated 1 hour ago. But in fact i had not been updated 1 hour ago, because i had only just logged on for the first time to day.

Another problem that happens all the time in Open Office, is when i go back to correct a mistake, by deleting a couple of wrong letters and try to type in new characters, it starts deleting more letters, as i put put the new letter in, this starts and stops regularly at will, while writing a page.

I have had these problems before with previous installation of UBUNTU 8.04

All the above faults stop, once i shut down and reboot, but then they start happening a gain after wile, this is driving me nuts, could anyone please help, any advice would be greatly appreciated, thanks.

---

### Post by audiomick on 2010-12-29
Hallo. I am not going to be able to sort this out for you, but I can tell you the following.

A virus is not impossible in Ubuntu, it is just very unlikely. Where there are millions of viruses aimed at windows and other MS products, and Apple products to, I believe, there are only a hand full aimed at Linux.

You say that you had these problems in a previous install of 8.04. This indicates hardware problems, I think. Did you do a fresh install to get your current system, or did you use the automatic update function? 
If it was a fresh install, then your problem is practically certain to be with your hardware. If it was an update, it might be some software thing that was retained through the update.

To make it easier for people to help, perhaps you could post
-which Ubuntu you are using
-was it a fresh install or not, and how long ago. Did you have problems immediately after the install/ update?

-some information about your computer: is it a laptop or a desktop? What make and model?

My first thought is that you have a problem with your RAM, or a messed up Gnome config or install, but I think it would be wise to get some other opinions. ;)

---

### Post by mr_bigmouth on 2010-12-29
Try updating your video drivers, and if that doesn't help, try installing more RAM.

---

### Post by sda123 on 2010-12-29
> **Zundap said:**
> Hi, every one, i am having big problems with Ubuntu 10.10, it appears to be a virus to me, although i was given to unsderstand that its impossible to get a virus with UBUNTU. There are various problems that have recently started happening, they are as below.

Suddenly freezes sometimes, (but not always), when i am using Firefox and Open Office at the same time.

Some times, (but not always) in Open Office, when i try to scroll down the page only the top fraction of the page about 1/8th actually scrolls and when i try to scroll up, only the botom 1/8th of the page scrolls up. 

Some times (but not always) when i click in the google search box in the top right hand corner of Firefox, the courser takes off at speed moving to the right, leaving behind a trail of small dash's, i have to shut Firefox to stop it, strangely though this had not happened for a while.

Sometimes (but only very occasionally) its freezes, when installing updates.

Sometimes, when i am using Open Office, in fact quite regularly, when i click on the page i an writing on, instead of jut placing the curser on the page, it selects an amount of text and then and no matter what else i try to do, it just keeps selecting an amount of text.

Just now, i noticed an update notice was on the task bar, so clicked it and it asked for the password as usual, i put the password in and it said intalling up date, it went through update procedure, then gave a message saying that, i was already up to date and was last updated 1 hour ago. But in fact i had not been updated 1 hour ago, because i had only just logged on for the first time to day.

Another problem that happens all the time in Open Office, is when i go back to correct a mistake, by deleting a couple of wrong letters and try to type in new characters, it starts deleting more letters, as i put put the new letter in, this starts and stops regularly at will, while writing a page.

I have had these problems before with previous installation of UBUNTU 8.04

All the above faults stop, once i shut down and reboot, but then they start happening a gain after wile, this is driving me nuts, could anyone please help, any advice would be greatly appreciated, thanks.

I think thats because ubuntu 10.10 is a beta, so there are not so much bugs when it is stable

---

### Post by audiomick on 2010-12-29
> **sda123 said:**
> I think thats because ubuntu 10.10 is a beta,
Umm, no, I don't think it is...

---

### Post by Zundap on 2010-12-29
Thanks for the reply radiomick, I am using a desktop computer computer, version 10.10, i was thinking that it was a virus, because everything worked ok for a while after the installation, it worked ok for about a month, which why i thought it was a virus.

I have also had that problem with the curser in the Google search box, when i ran this on windows and that time it did turn out to be a virus. 

Thanks again for your idea's. :p

---

### Post by mcduck on 2010-12-29
> **sda123 said:**
> I think thats because ubuntu 10.10 is a beta, so there are not so much bugs when it is stable

10.10 hasn't been a beta for a long time, it was released in October. :D

Also the OP mentions having the same problems with previous versions, which pretty much rules out anyhting related to a certain Ubuntu release, and of course even the very unlikely chance of a virus being the problem.

It really sounds like a hardware (or driver) related problem.

Also it was mentioned that the problem starts after the system has been running for a while. Which would also indicate a hardware- or possibly heat related issue.

I'd start by the simplest and easiest thing to test, running the memtest from Ubuntu's boot menu (or live-CD). And keep in mind that running the test once doesn't tell you anything, most memory-related problems start happening after the RAM has been stressed for a while (and after fist error more start appearing a increasing speed), so memtest should be ran for a long continuous period. I recommend letting it run over night at least.

..and of course make sure the computer is clean, all coolers are properly attached and fans are working. Graphics problems like that could simply be a result from overheating GPU.

---

### Post by audiomick on 2010-12-29
> **mcduck said:**
> 
Also it was mentioned that the problem starts after the system has been running for a while. Which would also indicate a hardware- or possibly heat related issue.

I'd start by the simplest and easiest thing to test, running the memtest .... I recommend letting it run over night at least.

Yep. If you haven't seen memtest run, it might be confusing. The relevant thing is that if the RAM, which is what it is testing, is ok, it will show zero errors. Any errors at all indicate a problem.

> 
..and of course make sure the computer is clean, all coolers are properly attached and fans are working.Also very good advice. Open up the case and go at it very carefully with a soft brush and a vacuum cleaner. Remove the power cable of the computer from the power first.

---

