---
title: "Before I make my ubuntu move"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by nVee on 2009-06-23
Hey Guys

I have been appointed to move our existing windows network over to a ubuntu network and I have little to NO linux skills, but knowing my friend google I am sure we should get to the other end.

But before I make my final move, I would like to ask if the following is possible and if you could appoint me in a direction on how to achieve the following (preferrable the shortest and most user friendly route).

We will have 1 dedicated server running 8.0.4 server and our workstations will be running ubuntu 9 (latest workstation version)


[LIST]
[*]Domain controller: We would like to specifically use the server as a domain controller because we are sharing a network with a call centre and would like to avoid and possible security bridges
[*]Internet manager: Our internet will be default route through the server but we would like to assign a bandwidth controller to each workstation and i may be pushing it here, but it would also be great to see a bandwidth report per individual user
[*]File Server: An obvious file server functionality, but we would like it if no workstation could save any files on their local machines but be entirely reliant on the server to save any documents, is that entirely possible?
[*]Web testing server: WE are a web development company and would like to run the server as a testing server for our PHP mySQL projects.
[*]Windows software: We use Photoshop and some other windows applications, and are deeply worried that there may be a compatibility issue with windows software. We were advised to run our windows software through WINE. Is wine secure, does the majority of Windows software work with Wine and can we expect and performance issues?
[/LIST]
I think to a degree this is it! I look forward to hear from you gurus soon!

---

### Post by philcamlin on 2009-06-23
i wouldent use wine because it isnt the greatest but id use gimp with comes with the install 

i have ubuntu on my pc and i love it best of all NO VIRUSES!

---

### Post by Celauran on 2009-06-23
Moving the server shouldn't give you any real trouble. If you're really dependent on Photoshop, I'd bet Gimp won't quite cut it, nor will Photoshop under Wine. In this case, it may well be best to leave the workstations on Windows. At the very least, set up a single Linux test workstation to see if either Photoshop under Wine is a viable option or if Gimp is a viable replacement.

Domain control and file serving can both be handled via Samba. It's fairly straightforward to setup and the documentation is, by and large, excellent.

Getting a LAMP stack up and running won't take more than a few minutes, so you're good there, too.

As for bandwidth monitoring and reporting, I'm sure apps exist for both, but this is something with which I have no experience.

---

### Post by DGortze380 on 2009-06-23
> **nVee said:**
> Hey Guys

I have been appointed to move our existing windows network over to a ubuntu network and I have little to NO linux skills, but knowing my friend google I am sure we should get to the other end.

But before I make my final move, I would like to ask if the following is possible and if you could appoint me in a direction on how to achieve the following (preferrable the shortest and most user friendly route).

We will have 1 dedicated server running 8.0.4 server and our workstations will be running ubuntu 9 (latest workstation version)


[LIST]
[*]Domain controller: We would like to specifically use the server as a domain controller because we are sharing a network with a call centre and would like to avoid and possible security bridges
[*]Internet manager: Our internet will be default route through the server but we would like to assign a bandwidth controller to each workstation and i may be pushing it here, but it would also be great to see a bandwidth report per individual user
[*]File Server: An obvious file server functionality, but we would like it if no workstation could save any files on their local machines but be entirely reliant on the server to save any documents, is that entirely possible?
[*]Web testing server: WE are a web development company and would like to run the server as a testing server for our PHP mySQL projects.
[*]Windows software: We use Photoshop and some other windows applications, and are deeply worried that there may be a compatibility issue with windows software. We were advised to run our windows software through WINE. Is wine secure, does the majority of Windows software work with Wine and can we expect and performance issues?
[/LIST]
I think to a degree this is it! I look forward to hear from you gurus soon!

I STRONGLY suggest that you set up a test environment before you migrate.

To the best of my knowledge, everything you are asking is doable in one way or another, but ti will take some tweaking and configuration.

Here's some info to get you started on your search.

Domain Controller -  My suggestion is always to subnet your network appropriately, then domain controllers become less of an issue and are typically not needed. If that is not feasible (it sounds like you're assigned a subnet that you share with another department), maybe this will help? 

[https://help.ubuntu.com/community/LDAP-Samba_PDC_(for_Linux_and_Windows)?highlight=(pdc)|(samba](https://help.ubuntu.com/community/LDAP-Samba_PDC_(for_Linux_and_Windows)?highlight=(pdc)|(samba))

Proxy - [http://ubuntuforums.org/showthread.php?t=700202](http://ubuntuforums.org/showthread.php?t=700202)

File Server - Easy, which kind would you like? I suggest I suggest sshfs for security, I'm happy with it. You can certainly limit users access to the local file system. Not a problem. To get you started: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Web Server - No problem. Apache2, mySQL, PHP, all in the repos or option during installations for the server addition.

Windows Software - Tricky. Look at GIMP. WINE is not a reliable solution for mission critical environments IMO. You may have to run a virtual machine for some windows software. You're best option is to find a Linux alternative if possible (usually is).

File formats are your key to compatibility, not the program. OpenOffice can save in .doc or .odf for use with Microsoft Office. YOu can get a .pdf distiller. GIMP will save in various formats. Just make sure there's not a proprietary format that you need and can't utilize.

Good Luck.
Google is your friend.
Don't get discourage, this is a large project that will take a lot of troubleshooting and configuration, but it's doable.

---

### Post by paul_be on 2009-06-23
You may also consider using the LTS version for the desktops as well. (8.04)

[http://www.ubuntu.com/news/ubuntu-8.04-lts-desktop](http://www.ubuntu.com/news/ubuntu-8.04-lts-desktop)

---

### Post by nVee on 2009-06-23
Its a huge crossover from Photoshop to Gimp, plus we use Illustrator and Flash as well and like to use the 3 programs together (smartobjects) makes things so much simpler.

Any other suggestions apart from WINE?

---

### Post by Celauran on 2009-06-23
> **nVee said:**
> Its a huge crossover from Photoshop to Gimp, plus we use Illustrator and Flash as well and like to use the 3 programs together (smartobjects) makes things so much simpler.

Any other suggestions apart from WINE?

You could try running Windows from within a virtual machine and installing the required apps on said vm.

---

### Post by nVee on 2009-06-23
Wow that was fast :)

I think my biggest short comings is that I dont quite know what can be done with Linux, so when you mention techno phrases, I immediately have no idea where to start :)

We fortunetaly have a testing enviroment ready, and I have already installed the server and 1 desktop OS, and i plan to finalise this tomorrow (well finalise as in get started)

---

### Post by nVee on 2009-06-23
Would that mean that I have to run a VM on each desktop client? That would kinda take away the whole point of crossing over to open source :) hahaha but i appreciate your answer to a possible solution.

Our reason for moving over is obviously to save money on the long run and also support the underdog. Where I stay there are NO linux users for probably a 500km radius :) So we want to give it a go and see if it can work for our industry. 

Our biggest priority obviously is a domain controller, file sharing, bandwidth monitoring, blocking facebook and social networking websites (and a SA based chat program called mxit) and lastly run our sites on a testing enviroment before deployment.

---

### Post by nVee on 2009-06-23
and before I forget, we have a variety of windows applications like our accounting software (quickbooks) which does unfortunetaly require a win enviroment or at minimum a windows emulator.

---

### Post by jonobr on 2009-06-23
Remving my comments as in the time it took to write, the answers were given

---

### Post by Mornedhel on 2009-06-23
You can check if your applications run smoothly under Wine here : [http://appdb.winehq.org/](http://appdb.winehq.org/)

Running Photoshop CS2 flawlessly was one of the goals of Wine 1.0, but later versions of Photoshop will probably not run as well.

---

### Post by HavocXphere on 2009-06-23
Bonus points for enthusiasm :popcorn: ...but I'd suggest starting small and doing things in steps. Nothing kills a migration to linux faster than an overly ambitious schedule.

Unix/linux is traditionally strong on the network front, so maybe start with the internet access server. Ideally, do the trial & error on another box, so that the box currently performing that function can just be plugged in if you mess something up with the linux box. The last thing you want is a CEO breathing down your neck because the network is down.;)

Look at this:
[http://en.wikipedia.org/wiki/SmoothWall](http://en.wikipedia.org/wiki/SmoothWall)
(Paying special attention to the See Also Section.)

Most of those ^^^ can do usage logging etc.

---

### Post by Celauran on 2009-06-23
> **nVee said:**
> Would that mean that I have to run a VM on each desktop client? That would kinda take away the whole point of crossing over to open source :) hahaha but i appreciate your answer to a possible solution.

Our reason for moving over is obviously to save money on the long run and also support the underdog. Where I stay there are NO linux users for probably a 500km radius :) So we want to give it a go and see if it can work for our industry. 

Our biggest priority obviously is a domain controller, file sharing, bandwidth monitoring, blocking facebook and social networking websites (and a SA based chat program called mxit) and lastly run our sites on a testing enviroment before deployment.

Given the number of native Windows applications you have and must continue to have, I'm going to restate my opinion that you ought to keep the workstations on Windows. Give PS a try under Wine on the test station you've already got set up and see how that goes, but I'll admit I'm a little skeptical. It's unfortunate that your first exposure to Linux on the desktop has to be "sorry, that probably won't work" but better to be up front now than let you find out the hard way.

Pretty much everything looks good for the server side of things, though. I've got a number of LAMP boxes set up here, some also sharing files with Windows via Samba, and with other Linux machines via NFS and the whole experience has been generally painless.

---

### Post by LowSky on 2009-06-23
running your backend on Linux will save you a ton of money, enough that keeping windows on the users' workstations will not seem to cost so much.

---

### Post by Paqman on 2009-06-23
> **Celauran said:**
> it may well be best to leave the workstations on Windows.

Definitely. If you have a lot of Windows apps that you need, use Windows. Wine is a workaround that occasionally works really well, but the majority of Windows apps run badly on it, or not at all.

You should see plenty of benefit from switching your servers over to Linux. Worry about migrating the workstations later.

---

### Post by Mortus Pryde on 2009-06-23
What no one has yet mentioned though, and may not be possible as I am still a beginner myself, is perhaps run the Windows VM on a server and give them terminal access to the server. This would if possible, in escence drop you to 1 Windows licence only for your operation. At least for now, you can still look at Linux native alternatives for production software that uses common file formats and encourage there use.

---

### Post by SunnyRabbiera on 2009-06-23
You may also consider crossover office, its based on wine but at times can be more stable and is mainly used for commercial use.
But personally wine has not failed me yet, heck I find wine more stable then windows.

---

### Post by stalkier on 2009-06-23
My thought is that this is going to take more time than you are thinking. If this is REALLY what is wanted/needed then stick to it. It will be bumpy at times but will be well worth it.

---

### Post by Sealbhach on 2009-06-23
You might want to check out Gimpshop, it's GIMP with a Photoshop front:

[http://www.gimpshop.com/](http://www.gimpshop.com/)

But it may not have the functionality you need.

.

---

### Post by ACupOfCoffee on 2009-06-24
Gimpshop is based on an old version of GIMP. I've tried to use it and (at least on Windows) it's very buggy and unstable. Also, development is dead last time I checked.
 
Flash... eww, that won't be pretty. Am I right in assuming that the interconnectedness of the Creative Suite will weigh heavily on this? If so you don't want Linux. As far as trying to cut costs with moving to open source there's really no point ifyou have to turn around and get Windows running in a VM on your workstations. That route is usually at least as expensive if not more so than staying with Windows in the first place.

---

### Post by golusweet on 2009-06-24
Photoshop CS2 works In Jaunty using wine 1.1.20 

What does not work 
# Occasionally hides the active project requiring one to go to Window > Arrange > New window for

    * This appears to be an issue with the Compiz cube

# Occasionally complains about inadequate permissions. I've always fixed this by restarting GDM

    * sudo killall gdm
    * sudo gdm

# Adobe Updater
# The browse function 

:D

---

