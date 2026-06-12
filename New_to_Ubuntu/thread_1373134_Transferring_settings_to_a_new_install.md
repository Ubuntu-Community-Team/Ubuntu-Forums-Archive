---
title: "Transferring settings to a new install?"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by Rhythmdvl on 2010-01-05
I currently have Ubuntu Server 8.1 installed on a pair of drives in RAID 1. I am about to completely lobotomize the box, repurposing the current drives and replacing them with two completely blank drives. I want to install the current 9.1 version, and have a similar setup (RAID 1, SAMBA, LAMP, GUI). I would also like  the two or three pieces of hardware to work as they do now (i.e., I had to [manually install ]("http://ubuntuforums.org/showthread.php?t=881156") onboard LAN drivers).

There are a few very minor changes to the desktop/setup that I've made, but nothing major. Is there a settings transfer wizard or helper app that will make things go smoother?


(I have no idea if this will make a difference, but I just dragged a kicking and screaming XP box into Windows 7. Give a few of the headaches, I figured it was wise to ask.)

Hardware:
Asus P5KPL
Intel E2180
82G33/G31 Express Integrated Graphics Controller

---

### Post by bodhi.zazen on 2010-01-05
You can "transfer" most of the settings if you wish by backing up your home directory.

May I ask, why are you running a graphical desktop on a server ? If you are looking for a graphical interface take a look at webmin.

---

### Post by Rhythmdvl on 2010-01-06
Thanks. 

Why am I still using the GUI? Because even though I grew up with DOS and am comfortable working with a command line, I've grown old and soft with time. (Wait a second, it's time for my applesauce.)

OK, back. 

It's running as a server because its main purpose is to act as a file server and Web testing platform. My wife and I run a editorial/design consultancy out of our home, so having a central location for files is crucial. We build the occasional Web site, so being able to test locally saved a lot of progress-bar time too. Most of the time it ran headless, but I had it connected to one of my monitor’s inputs and the USB mouse/keyboard went through a switch so I could access it directly. 

Besides the comfort factor of a GUI, there were times when we had extra help in the office or when my main machine was down for some reason -- having a familiar(esque) environment to work in made sense for us.

---

### Post by falconindy on 2010-01-06
Copy over /etc as well, as you've probably made some changes to the files in there.

---

