---
title: "fan control"
date: 2011-02-02
forum: New to Ubuntu
---

### Post by ben889 on 2011-02-02
I love how quiet ubuntu is on this but i took notice that my temp idles about 70 and jumps over 80 and from what i read about my cpu critical temp is about 70c. is there a simple program i can get to run more cooler

---

### Post by quadproc on 2011-02-02
> **ben889 said:**
> took notice that my temp idles about 70 and jumps over 80 and from what i read about my cpu critical temp is about 70c. is there a simple program i can get to run more cooler
Which version of Ubuntu are you running?  I ask because 10.04 initially had a kernel problem which would sometimes spin the CPU and dramatically run up the power consumption.  If this is the problem then you need a later kernel.

For temperatures as high as you have, there is something wrong with the cooling system.  Was heat paste used when installing the CPU (it should have been)?  Is the CPU cooling fan(s) working properly?  Are the air intakes unrestricted?  Is the computer filled with dust or lint?  Are you overclocking?

quadproc

---

### Post by ben889 on 2011-02-02
no its a laptop and my temps never been this high until i gave windows the boot. with windows it seemed like the fan was constantly going though butthen i was doing a lot of authoring of dvds.

im using 10.10 
on acer aspire 5520

---

### Post by cloyd on 2011-02-02
I was able to control my fan with this:

                      use command acerhdf
 

 open or create this file
  


 /etc/modprobe.d/acerhdf.conf
The file contains only this
 options acerhdf interval=5 fanon=58000 fanoff=53000 kernelmode=1
 

 This will turn the fan on at 58 C and off when it is down to 53 C. Everything I found on this command said keep the two values 5 degrees C apart. You may have to play with the values, and I am assuming that the command works with your system. 

I had problems with 10.04 and excessive heat . . . though not as extreme as yours. Newer kernels helped a lot. However, the command I show here is the only thing I have found to directly control the fan. I've thought I could try to cool it down to 45 or 50, but I would probably not have much battery life, and it probably wouldn't cool it that much anyway.

If I could remember the links where I found this, I'd give them, but I bet the community documentation would help.

---

### Post by ben889 on 2011-02-02
im not really worried about battery life as i always have it plugged in and i never run it off the battery

---

### Post by cloyd on 2011-02-02
I did find it on Community docs.  I was especially for acer aspires and 9.04. It helped me on my  gateway netbook, and in 10.04. The community docs did reccomend a bit higher range . . . 56 to 61 maybe . . . give it a try. It helped me.  I used 53 to 58. I wasn't that concerned about battery life. 

I have to tell you, I was getting concerned about temps in the 60's . . . still, this helped.

---

### Post by ben889 on 2011-02-02
> **cloyd said:**
> I was able to control my fan with this:

                      use command acerhdf
 

 open or create this file
  


 /etc/modprobe.d/acerhdf.conf
The file contains only this
 options acerhdf interval=5 fanon=58000 fanoff=53000 kernelmode=1
 

 This will turn the fan on at 58 C and off when it is down to 53 C. Everything I found on this command said keep the two values 5 degrees C apart. You may have to play with the values, and I am assuming that the command works with your system. 

I had problems with 10.04 and excessive heat . . . though not as extreme as yours. Newer kernels helped a lot. However, the command I show here is the only thing I have found to directly control the fan. I've thought I could try to cool it down to 45 or 50, but I would probably not have much battery life, and it probably wouldn't cool it that much anyway.

If I could remember the links where I found this, I'd give them, but I bet the community documentation would help.


sorry im a new to linux but i opened a terminal and typed acerhdf and i got command not found so i typed sudo acerhdf and got a reply command not found
would it be easier just to make one and put it in the modeprobe.d folder?
and if it is how do i do that from the terminal?

---

### Post by cloyd on 2011-02-02
> **ben889 said:**
> sorry im a new to linux but i opened a terminal and typed acerhdf and i got command not found so i typed sudo acerhdf and got a reply command not found
would it be easier just to make one and put it in the modeprobe.d folder?
and if it is how do i do that from the terminal?
/etc/modprobe.d/acerhdf.conf


Ok. It has been a while. Navigate to (with the file browser) to  /etc/modprobe.d   (this is the path to the file you want . . . folder modprobe.d within folder etc.

Within folder modprobe.d there should be a file named acerhdf.conf.  Open this file with gedit and change it to read :      options acerhdf interval=5 fanon=58000 fanoff=53000 kernelmode=1
Save it

this will set the fan to go on at 58 C and to shut it off when it goes down to 53 C. 

IF you find the file but cannot gain access to it because it says you do not have permission, open nautilus in the terminal with command: sudo nautilus
THis will open  a file browser window with root permissions. Be careful while you are in here. Navigate to the /etc/modprobe.d folder. 
(if such a folder doesn't exist, try to create it.)
open the acerhdf.conf file.

IF the file doesn't exist, create it in the proper folder (/etc/modprobe.d with gedit) If folder access is denied to you, open gedit in terminal with sudo gedit.  Put the above mentioned line into the file, and save it in folder /etc/modprobe.d and filename acerhdf.conf 

I hope this works. Be careful with sudo-ed commands . . . they can allow you to do things you really shouldn't do. Yet, if you want to be in control of your system, you have to use them sometime. Don't play with things you don't have adequate knowledge or instruction about so that you don't harm your system. (most of us do from time to time, and we learn to fix them. However, if there is a big assignment due or important deadline to meet, it isn't a good time to learn how to fix things.) If you open nautilus or gedit with sudo, get out as soon as you are done. 

I made the statement that "I hope it works with your system." That the command has the word "acer" in it suggests that it might not work with all systems. Mine is a gateway, and I know that there is a strong relationship between gateway and acer. 

Good luck. I'm going to leave the computer on for about 30 more minutes, then I'll probably turn it off. I will be back on line in the morning. It is cold, snowy and icy here . . . won't be going much of anywhere unless there is some kind of emergency. Hope I've helped you. Let me know.

---

### Post by ben889 on 2011-02-02
OK will do.



thanks

---

### Post by ben889 on 2011-02-02
i did it i guess i have to restart for it to take effect.

thanks this has to be the best Linux community there is

---

### Post by ben889 on 2011-02-02
so far so good its sitting idle with each core at about 60 haven't put a load on it yet to see how high it will go but its good to hear the fan running again. also i dont have to worry about school and my computer right now i have one at school and im only going to be starting net+ next week.


but any way i really do appreciate the help THANKS

Ben


putting under stress still runs a little hot at 74c but dosnt jump over 80 now

---

### Post by cloyd on 2011-02-03
I am glad I could help. 

If I could tell you how, it would probably be a good idea to check and see if there were any dust inside your machine that blocks airflow. My son had a similar problem, and took his machine apart and found a big ball of fuzz in the machine. My son is different from me . . . he can take things apart, and _usually_ get them back together. I can rarely get them back together. I take mine to a tech for anything requiring that on a laptop or netbook. I _do not_ reccomend taking a laptop or netbook down oneself.  

Ubuntu is a great way to learn more about your computer. It is also a great way to have a virus free, relatively crash free, fast booting, system with tons of good available free software. I hope you stick with it, and maybe along the way get someone else interested in it.

---

### Post by ben889 on 2011-02-03
haven't started a+ yet but taking this apart isn't a problem.


once again thanks for the help now that this is solved i just have one more thing to take care of and its by-bye windows

---

### Post by GrouchyGaijin on 2011-02-04
I'm running 10.10 on a Dell Inspiron 1520.  After reading this I'm a bit concerned because Conky lists both of my CPUs are running at 74 C when they are not stressed.  According to Conky they heat up to +90 C if I'm doing something strenuous like rendering some video.

Can the acer fan control command do any damage if I try to run it on a Dell?

---

### Post by cloyd on 2011-02-04
> **GrouchyGaijin said:**
> I'm running 10.10 on a Dell Inspiron 1520.  After reading this I'm a bit concerned because Conky lists both of my CPUs are running at 74 C when they are not stressed.  According to Conky they heat up to +90 C if I'm doing something strenuous like rendering some video.

Can the acer fan control command do any damage if I try to run it on a Dell?
I'm not an expert, just a user who has liked his ubuntu. I don't see how acer command could _not_ help. I would suspect that if it is only supported for acer and gateway, that nothing would happen . . . and at the most all you'd get would be "command not supported" or something like that.  If you must create the config file, and it doesn't work, then just delete it. However, with temps like you are reporting, you may have more of a problem than just the fan settings.

Another thing . . . you may be able to do a google search on your processors and find out what their critical temps actually are . . . though I'd definitely be concerned with the 90's.

---

### Post by GrouchyGaijin on 2011-02-04
I think the temp being shown in my conky is not correct.
I installed i8kmon and there is about a 10 degree difference in reported temps.

[IMG]http://jfniendorf.org/cpu-temp.png[/IMG]

Does anyone have any advice?

---

### Post by cloyd on 2011-02-04
Have you tried sensors in the terminal?

There is also an apt you can add to your panel called "computer temperature monitor.

The panel apt is kind of handy to have . . . when I run conky, I can't see any shortcuts on my desktop . . . and I kind of like it that way. However, there are times when I don't want conky, but I still want to monitor the processor temp.

I wouldn't think that a system with only a 37% load on the processors would be that hot unless something else were going on. The problem could be ventilation, or a kernel problem. However, if you have been looking at these temps for a year or so, and you're still up and running, maybe the reported temp _is_ incorrect.  I'd try a third way of checking the temperature and see what it says. 

I'm not familiar with i8kmon, but I want to try check it out.

By the way . . . we may want to start a new thread here if we continue this conversation . . . I think we're hijacking somebody else's thread.

---

### Post by GrouchyGaijin on 2011-02-04
> **cloyd said:**
> Have you tried sensors in the terminal?

There is also an apt you can add to your panel called "computer temperature monitor.

The panel apt is kind of handy to have . . . when I run conky, I can't see any shortcuts on my desktop . . . and I kind of like it that way. However, there are times when I don't want conky, but I still want to monitor the processor temp.

I wouldn't think that a system with only a 37% load on the processors would be that hot unless something else were going on. The problem could be ventilation, or a kernel problem. However, if you have been looking at these temps for a year or so, and you're still up and running, maybe the reported temp _is_ incorrect.  I'd try a third way of checking the temperature and see what it says. 

I'm not familiar with i8kmon, but I want to try check it out.

By the way . . . we may want to start a new thread here if we continue this conversation . . . I think we're hijacking somebody else's thread.

Good idea - I'll start a new thread.

---

### Post by GrouchyGaijin on 2011-02-04
Here is the new thread.

[http://ubuntuforums.org/showthread.php?p=10427713#post10427713](http://ubuntuforums.org/showthread.php?p=10427713#post10427713)

---

