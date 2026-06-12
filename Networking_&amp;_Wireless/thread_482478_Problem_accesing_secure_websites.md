---
title: "Problem accesing secure websites"
date: 2007-06-23
forum: Networking &amp; Wireless
---

### Post by Aathos on 2007-06-23
Since installing Fiesty, I have not been able to access several secure sites, such as my bank, and cell phone, but also I have not been able to get to windows live mail.  I haven't changed any security settings.  I have tried using other browsers besides Firefox, but I have the same problem.  These sites work fine in Firefox on Windows XP, so I think it must be a Ubuntu problem.  I am connecting through a wireless connection, if that makes a difference. 

What happens is that when I try to log in to any of these sites, it takes really long to load, and I get a time out error.  I don't know what sort of information would be useful, but I will gladly provide any settings/configurations that you ask for.  

Thanks

---

### Post by Beatbreaker on 2007-06-25
I've noticed this too with my bank website - I used Opera and it seems to be fine with that (the Bans site does not support Opear though so i'd like to use firefox instead) i just don't know what's causing the problem -when i access the page the popup window for the bank details is entirely black. 

..same black screen?

---

### Post by Aathos on 2007-06-25
No, I don't get a black screen.  I get a "the connection was reset" error in Firefox, and a "website dropped the connection" error in epiphany.  I know that the website is not down, or busy because it only happens in Ubuntu.  I can go to a windows computer an it works fine.  I can get to the login page, the problem occurs when I try to login.

---

### Post by Beatbreaker on 2007-06-28
humm i havent seen that one - can anyone else help?

---

### Post by Aathos on 2007-07-07
bump

---

### Post by cmpscimdry on 2007-10-08
A friend of mine is having the same problem.  I am currently her computer go to guy so I need to know how to fix this problem.  Anyone have any ideas?

---

### Post by callan79 on 2007-10-09
> **Aathos said:**
> Since installing Fiesty, I have not been able to access several secure sites, such as my bank, and cell phone, but also I have not been able to get to windows live mail.  I haven't changed any security settings.  I have tried using other browsers besides Firefox, but I have the same problem.  These sites work fine in Firefox on Windows XP, so I think it must be a Ubuntu problem.  I am connecting through a wireless connection, if that makes a difference. 

Hi,

I'm not sure if this will even help you, but I just want to make sure that your Internet connection does not go through two routers?

I use secure sites at home and it works, but I work for an Internet Provider and have seen some customers use two routers in a row and have this same problem. For example a customer might plug a wireless router into the router we supply, but if they plug their computer directly into the first router then everything works.

I just want to make sure this is not your issue.

Cheers
Callan

---

### Post by ninja0nfire on 2007-10-09
I am having the same problem with Gutsy 7.10 :(

---

### Post by Aathos on 2007-10-09
I have not found a solution, but I do believe that I have found the problem.  I am not connecting through two routers.  Our DSL modem has a built in wireless router.  It seems that the problem is with the driver for the wireless card.  My wireless card worked without any trouble in 6.10, but when I installed Fiesty, I had to use ndiswrapper to get it to work.  I posted my wireless card problems in [this]("http://ubuntuforums.org/showthread.php?t=416876") thread.

---

### Post by ninja0nfire on 2007-10-10
I am also using ndiswrapper, with Win98 driver for RLT8187B.

---

### Post by disneyfriedhistory on 2007-10-11
I had a similar problem with an aironet router (i think) and it turned out that the MTU rate wasn't adjusting properly.  Or something like that.  I had to log into the router and adjust the MTU rate to something like 1497 or 1494.  I can't remember, it's been a while.  But playing with that got sites like yahoo! mail to work.

---

### Post by fallingleaf on 2007-10-11
Is anybody who's having this problem using Wicd?  See thread here: [http://ubuntuforums.org/showthread.php?p=3515132](http://ubuntuforums.org/showthread.php?p=3515132)

---

### Post by Aathos on 2007-10-11
I have been using wcid, but  my problems predate my switch from network-manager.  I don't remember if I tried to access the sites when connected via ethernet.  I usually only use a cable when I am fooling with my wireless.  I have a desktop, and setting up a wired connection requires moving all my hardware.  I will try the test version of wcid, but it seems like you had a different problem, so I doubt that it will help.

@ disneyfriedhistory:
     I have no idea what you are talking about.

---

