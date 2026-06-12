---
title: "Need to Clean Up Ubuntu and Slow Down Processors"
date: 2010-01-12
forum: New to Ubuntu
---

### Post by turboopugsleylx on 2010-01-12
Hey guys,

Is there a function within Ubuntu that is akin to defragging and cleaning your registry files in windows? I remember starting Ubuntu in safe mode that did something like this it seemed....just want to make sure everything with my system is optimized and running as fast as it can...

Secondly I ran a command on here recently that cause my processors to turn to full on 100% of their Mhz as opposed to being on demand...what command do I need to use to switch them back to a "scale power on demand type setting"?

Thanks
Turbo

---

### Post by s.fox on 2010-01-12
Hello,

Take a look at [this]("http://ubuntuforums.org/showpost.php?p=2443456&postcount=5") for information on defragging. 

-Silver Fox

---

### Post by JC Cheloven on 2010-01-12
AS for the cpu speed:

- right-click on a pannel (perhaps the upper one)
- select "add to panel"
- search for CPU frequency monitor, and add it
This allows you to control the cpu freq.

Cheers

---

### Post by turboopugsleylx on 2010-01-12
I have the monitor but when I switch it to half speed nothing happens...it doesnt work

---

### Post by turboopugsleylx on 2010-01-12
> **Silver_fox_ said:**
> Hello,

Take a look at [this]("http://ubuntuforums.org/showpost.php?p=2443456&postcount=5") for information on defragging. 

-Silver Fox


Also is there anyway to force thise or make it take a less amount of reboots?

---

### Post by wojox on 2010-01-12
# Force File System Check

```
sudo touch /forcefsck
```

---

### Post by turboopugsleylx on 2010-01-12
When I did the force command nothing happened...restarted nothing happened as well...

---

### Post by turboopugsleylx on 2010-01-12
What should I do?

---

### Post by ssulaco on 2010-01-12
> **wojox said:**
> 
```
sudo touch /forcefsck
```
wojox's command should work for you,are you asked for your password after you execute the command?,did you copy and paste the command.........if you typed in manually there is a space between h and /

---

### Post by turboopugsleylx on 2010-01-12
Heres all that happened...

chris@chris-desktop:~$ sudo touch /forcefsck
[sudo] password for chris: 
chris@chris-desktop:~$ 


entered password and it went back to prompt...

---

### Post by JC Cheloven on 2010-01-12
> **turboopugsleylx said:**
> I have the monitor but when I switch it to half speed nothing happens...it doesnt work

Then it may be that your cpu/motherboard don't support cpu scalling. Nothing to do in that case.

Hint: Many desktop pc's doesn't allow cpu scalling. Most laptops do.

EDIT: you said that you ran some command before. What was it? I think it's cpufreq-selector. It should be run as root. Check the manpages:  ```
man cpufreq-selector
```

---

### Post by tom.swartz07 on 2010-01-12
> **turboopugsleylx said:**
> Heres all that happened...

chris@chris-desktop:~$ sudo touch /forcefsck
[sudo] password for chris: 
chris@chris-desktop:~$ 


entered password and it went back to prompt...

you could always just run fsck right from a livecd
```
sudo fsck
```

I dunno if that will get the same results youre looking for, but it basically does the same thing

---

### Post by ssulaco on 2010-01-12
> **turboopugsleylx said:**
> 
entered password and it went back to prompt...
Yes it will go back to prompt.....it requires a  reboot after this.

---

### Post by turboopugsleylx on 2010-01-13
> **JC Cheloven said:**
> Then it may be that your cpu/motherboard don't support cpu scalling. Nothing to do in that case.

Hint: Many desktop pc's doesn't allow cpu scalling. Most laptops do.

EDIT: you said that you ran some command before. What was it? I think it's cpufreq-selector. It should be run as root. Check the manpages:  ```
man cpufreq-selector
```

[http://ubuntuforums.org/showthread.php?t=1371258](http://ubuntuforums.org/showthread.php?t=1371258)


heres the thread with the command I did....my processor went from 1350Mhz to 2700 Mhz when i ran the command...now I cant get it back to where it adjusts cpu usage under load....the CPU monitor in the lower right hand didnt do anything when i adjusted it...

---

### Post by turboopugsleylx on 2010-01-13
This one below even when I reboot does nothing....the other one warns me about running on a mounted system...which I am hesitant to do anyways....any ideas?
sudo touch /forcefsck

---

### Post by turboopugsleylx on 2010-01-13
Any Ideas?

---

### Post by louieb on 2010-01-13
> **turboopugsleylx said:**
> This one below even when I reboot does nothing...sudo touch /forcefsck

All that command does is create a file named /forcefsck - did you look in the / directory to see if its there? 

You'll know fsck ran if the file is gone after reboot. 
How do you know **fsck** did not run on reboot?

---

