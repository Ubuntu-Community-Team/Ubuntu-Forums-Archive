---
title: "Problems with &quot;x server&quot; and graphics drivers"
date: 2010-11-10
forum: New to Ubuntu
---

### Post by The_gamefreak on 2010-11-10
alright so 1st off I'm very new to the system of how things work in this so details are very nice =]

alright so i have had Ubuntu 10.04 for 2 days now and have been desperately trying to get my graphics card drivers so i can run at my normal resolution with both of my monitors i have searched all over Google top and bottom for a working answer it might be that i don't understand how to make them work or i might just be $#!% auto luck either way im hopeing i can find an answer here.


so i have looked around and i found the linux drivers on nvidias site and i downloaded them once i figured out how to use em i get the error  

  ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at [www.nvidia.com]("http://www.nvidia.com").



 i have also used the find hardware drivers thing and nothing pops up i have found some drivers in Ubuntu software center but after installing thes it still gives me some crap about some "x server" and wont let me change my resolution or use my second monitor, if I'm going to have to mess with it anyway i might as well use the drivers i downloaded from nvidia site 

some answers i have found are
press cntrl alt f1 and put in 
sudo /etc/init.d/gdm stop

when i do that it doesn't recognize that as a command idk if i did it wrong or have to do something else 1st

also tryed "sudo service gdm stop" that got me somewhere but i dident really get anything

also sudo invoke-rc.d gdm stop that got kinda confusing and did not work

and the final thing was i found to run sudo rcconf from a terminal window the way it was explained sounds like the best thing but i have absolutely no idea how i would go about doing that


Thanks to anyone that takes the time to read this and answser my question(s) oh and if someone could give a way to at least get my resolution back without these drivers id also be great full thanks

oh and also (as if this wasn't long enough already) I'm sorry if i put this in the wrong place or whatever 1st time here

---

### Post by sandyd on 2010-11-10
> **The_gamefreak said:**
> alright so 1st off I'm very new to the system of how things work in this so details are very nice =]

alright so i have had Ubuntu 10.04 for 2 days now and have been desperately trying to get my graphics card drivers so i can run at my normal resolution with both of my monitors i have searched all over Google top and bottom for a working answer it might be that i don't understand how to make them work or i might just be $#!% auto luck either way im hopeing i can find an answer here.


so i have looked around and i found the linux drivers on nvidias site and i downloaded them once i figured out how to use em i get the error  

  ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at [www.nvidia.com]("http://www.nvidia.com").



 i have also used the find hardware drivers thing and nothing pops up i have found some drivers in Ubuntu software center but after installing thes it still gives me some crap about some "x server" and wont let me change my resolution or use my second monitor, if I'm going to have to mess with it anyway i might as well use the drivers i downloaded from nvidia site 

some answers i have found are
press cntrl alt f1 and put in 
sudo /etc/init.d/gdm stop

when i do that it doesn't recognize that as a command idk if i did it wrong or have to do something else 1st

also tryed "sudo service gdm stop" that got me somewhere but i dident really get anything

also sudo invoke-rc.d gdm stop that got kinda confusing and did not work

and the final thing was i found to run sudo rcconf from a terminal window the way it was explained sounds like the best thing but i have absolutely no idea how i would go about doing that


Thanks to anyone that takes the time to read this and answser my question(s) oh and if someone could give a way to at least get my resolution back without these drivers id also be great full thanks

oh and also (as if this wasn't long enough already) I'm sorry if i put this in the wrong place or whatever 1st time here

```

sudo killall gdm
```
would work.
starting computer in recovery mode would work as well (press shift/esc key during bootup_)

---

### Post by The_gamefreak on 2010-11-10
well i tryed recovery mode when i get back it gives me some stuff about not being on runlevel 3 and then if i say still go on it says im still running an x server then again i dont really know what im doing in recvoery mode so i might have done it wrong >.> as for the sudo killall gdm
gdm: no process found

EDIT: oh yea another question is all this stuff with my drivers the same in Ubuntu 10.10? because if it is i might as well update to that and then deal with this

---

### Post by sandyd on 2010-11-10
> **The_gamefreak said:**
> well i tryed recovery mode when i get back it gives me some stuff about not being on runlevel 3 and then if i say still go on it says im still running an x server then again i dont really know what im doing in recvoery mode so i might have done it wrong >.> as for the sudo killall gdm
gdm: no process found

EDIT: oh yea another question is all this stuff with my drivers the same in Ubuntu 10.10? because if it is i might as well update to that and then deal with this

just install the drivers from System -> Administration -> Hardware drivers then.

---

### Post by Spencer Caplan on 2010-11-11
> **The_gamefreak said:**
> well i tryed recovery mode when i get back it gives me some stuff about not being on runlevel 3 and then if i say still go on it says im still running an x server then again i dont really know what im doing in recvoery mode so i might have done it wrong >.> as for the sudo killall gdm
gdm: no process found

EDIT: oh yea another question is all this stuff with my drivers the same in Ubuntu 10.10? because if it is i might as well update to that and then deal with this


First thing: To switch to runlevel 3, from command line input "init 3" and it will bring you to that. Try stopping Gnome after switching to init 3. Let me know what happens then.

Second thing: The drivers would depend more on which kernel you are running, not which version of Ubuntu. If you are running 2.6.35-22 already then it shouldn't really make a difference as far as drivers go (I recommend being on the newest release regardless though) Also, what kind of computer / graphics card is this? Because there are issues varying levels of issues with some of both

---

### Post by The_gamefreak on 2010-11-11
ok 1st off my graphics card is a nvidia gtx460 
second when i go to administration hardware drivers nothing pops up for me to apply.
third if i go to runlevel 3 then try to stop it i get

 ** (gdm-binary:1763): WARNING **: Failed to acquire org.gnome.DisplayManager

** (gdm-binary:1763): WARNING **: Could not acquire name; bailing out

like i said im very new to this so if im doing something wrong... ive tryed recovery mode to get into root then the gdm stop witch is how i got the runlevel error and the x error in the same thing

 if i try this in the root thing it makes me login with takes me outa the "root". if i use sudo it works for the gdm but it gives me the error  that i just posted. 

Im probably makeing some really stupid mistakes here or doing something wrong...

---

### Post by The_gamefreak on 2010-11-11
well i updated to ubuntu 10.10 and my drivers poped up in the addtional drivers thing everything works perfectly now. thanks for the help i feel like an idiot now but thanks =]
:):):):)

---

