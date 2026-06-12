---
title: "Stellarium again"
date: 2011-03-18
forum: New to Ubuntu
---

### Post by weezyrider on 2011-03-18
When I first joined, I complained about Stellarium installing and not running. I've just found some other information, and want to know if it pertains to the problem.

Apparently Myself and owner are 2 different people to Ubuntu. I discovered that Stellarium is going under owner and is not even in the list of programs under usr. I finally found it, and it's under owner, hidden somewhere else. It did this before I reinstalled Ubuntu, so it isn't the reinstall. 
My Dell XP laptop does this also, and it infuriates me. I changed everything over to my name, but Dell's XP in its wisdom, still sticks downloads under OWNER. If I delete owner, I can't get to the hosts file. But as administrator, I can at least get to the Hosts file.
 
Thanks,
Weezy

---

### Post by oldos2er on 2011-03-18
It's normal for everything in /usr to be owned by root; not only is it normal, it's required for the system to work as designed.

It's not clear to me what exactly you mean by "owner." "Owner" is one of the types of file permissions used by Linux: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by weezyrider on 2011-03-18
I install Stellarium, It doesn't run. I finally tumbled to usr, and it's not in that section, under my account anywhere. I read thru every file under my account. Yet software center says it's installed. I did a search and it came up under owner. Couldn't get any other information on it. Even tho the icon is there, if you click on it, it does nothing. Every other program that I use is under my usr account. KStars installed under my usr account. Why isn't it installing where it is supposed to?  Thanks

---

### Post by akakingess on 2011-03-18
I just installed Stellarium and it shows up in the Applications-->Science menu for me to launch from there. As oldos2er stated, you shouldn't be accessing the /usr directory unless you know what you are doing and should have root privileges even then. Anything that you want easy access to should go into your /home/username directory, and if you want you can create a shortcut (called a link within Linux) in your home folder and then launch it from there. Hope this helps, if not, let us know if you are still having issues.

---

### Post by oldos2er on 2011-03-19
> **weezyrider said:**
> I install Stellarium, It doesn't run. I finally tumbled to usr, and it's not in that section, under my account anywhere. I read thru every file under my account. Yet software center says it's installed. I did a search and it came up under owner. Couldn't get any other information on it. Even tho the icon is there, if you click on it, it does nothing. Every other program that I use is under my usr account. KStars installed under my usr account. Why isn't it installing where it is supposed to?  Thanks

"usr" isn't an account, it's a directory. Do you mean "user"?

Can you run ```
which stellarium
``` in a terminal, and post the output here?

---

### Post by daggerstab on 2011-03-19
To quote myself from the previous threads:

> **daggerstab said:**
> **weezyrider**,

This error message is bad news:

> drmRadeonCmdBuffer: -22. Kernel failed to parse or rejected  command stream. See dmesg for more info.It means that the crash is caused by your graphics card's driver. You have an ATI Radeon, right?

As far as I know, it has been fixed in the latest kernel/driver, so you can:

[LIST]
[*]wait and see if a fix is released for the current version of Ubuntu;
[*]wait two months for Ubuntu 11.04 Natty Narwhal to be released in the end of April;
[/LIST]
(...)

> **daggerstab said:**
> A user who had reported the same error  message like you has reported that the problem is fixed by updating from  these two PPAs:

[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa") 
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")

It's possible that only the first may be sufficient.

See comment #50 and later here:
[https://bugs.launchpad.net/ubuntu/+source/stellarium/+bug/481669](https://bugs.launchpad.net/ubuntu/+source/stellarium/+bug/481669)

---

### Post by oldos2er on 2011-03-19
I thought this thread sounded familiar.

weezyrider, did you resolve your video card problems? Have you tried the Stellarium PPA?

---

### Post by weezyrider on 2011-03-19
I read everything. I don't touch. I've read thru almost every file on XP. Gives me an idea of what's there. I'm still not familiar with the names in Ubuntu. There is a directory that is similar to programs in Windows. Everything else that I'm using is listed there. 

I've had some programs that just install to C on windows. Pfaff and Adobe will do that.      There are icons showing that Stellarium is installed. Software center says it is installed. There is nothing wrong with the video card as it has passed every test in that system test. I can run the heavy duty graphic desktop. (I don't care for it)  

Stellarium simply will not open. I can find the pieces and parts, for example, the graphics, astronomical lists, etc. There just doesn't seem to be any type of exe or whatever Ubuntu calls the file, anywhere.   I've seen this with Windows. I've uninstalled an embroidery digitizing program via its uninstaller. It left everything behind but the executable. The folder is still there, the link is still there, any digitized files of mine are still there, I can access them. I can access icons, help files, but since there's no exe, it won't launch.   This is exactly what Stellarium is doing. All the pieces and parts except the part that launches it are there. So either the executable is missing, in another place, or there's a bad link. The icon you click on to launch is just dead. I'm getting the program thru Software center. 

I searched with anything that could search in Ubuntu, and one search result had it as installed, but it looked like it was under owner, sort of greyed out and I have no permission. I'm used to getting the whole path in windows. W

---

### Post by klytu on 2011-03-19
> **weezyrider said:**
> I read everything. I don't touch. I've read thru almost every file on XP. Gives me an idea of what's there. I'm still not familiar with the names in Ubuntu. There is a directory that is similar to programs in Windows. Everything else that I'm using is listed there. 

I've had some programs that just install to C on windows. Pfaff and Adobe will do that.      There are icons showing that Stellarium is installed. Software center says it is installed. There is nothing wrong with the video card as it has passed every test in that system test. I can run the heavy duty graphic desktop. (I don't care for it)  

Stellarium simply will not open. I can find the pieces and parts, for example, the graphics, astronomical lists, etc. There just doesn't seem to be any type of exe or whatever Ubuntu calls the file, anywhere.   I've seen this with Windows. I've uninstalled an embroidery digitizing program via its uninstaller. It left everything behind but the executable. The folder is still there, the link is still there, any digitized files of mine are still there, I can access them. I can access icons, help files, but since there's no exe, it won't launch.   This is exactly what Stellarium is doing. All the pieces and parts except the part that launches it are there. So either the executable is missing, in another place, or there's a bad link. The icon you click on to launch is just dead. I'm getting the program thru Software center. 

I searched with anything that could search in Ubuntu, and one search result had it as installed, but it looked like it was under owner, sort of greyed out and I have no permission. I'm used to getting the whole path in windows. W

Try opening a terminal window and typing: ```
stellarium
``` What happens? If the program doesn't run when you do this, can you copy and post the output (if any) that appears?

---

