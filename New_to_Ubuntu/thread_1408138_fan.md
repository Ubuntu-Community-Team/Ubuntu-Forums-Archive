---
title: "fan"
date: 2010-02-16
forum: New to Ubuntu
---

### Post by dzon65 on 2010-02-16
The last couple off days,the cpu goes up 80/90% without an appearing cause.Even when nothing is running,just desktop,the cpu goes way up,fan turning like crazy.I checked the monitor and everything looks normal,everything taks it's normal part.This is a very leightweight install and cpu very rarely goes past 30% as does the ram.It's as if something's running on the background,using A LOT.Anyone an idea?Added a screenshot when it starts rising,no prog running,out of the blue.(conky's a bad color but....)

---

### Post by switch10 on 2010-02-16
How often do you clean the dust out?  My laptop overheats like crazy if I don't blow the dust out at least once every few months.

---

### Post by dzon65 on 2010-02-16
BTW,I did a full 9.10 install,just to check.Same problem.Sudden bursts of high cpu.

---

### Post by dzon65 on 2010-02-16
> **switch10 said:**
> How often do you clean the dust out?  My laptop overheats like crazy if I don't blow the dust out at least once every few months.
Quite often.Well,often enough.It's clean right now.And yet,fan still turning.Not at full speed though,that only happens with those sudden cpu outbreaks.Never even heard this laptop before.

---

### Post by freak42 on 2010-02-16
look in
System -> Administration -> System Monitor -> Processes (sort by % CPU)
or on the command line with 'top'

and report back the application that uses up your cpu ressources when it happens again the next time.

---

### Post by dzon65 on 2010-02-16
Everything exept monitor   and screenshot util is NOT on.Yet cpu up and rising.I was thinking of cpu frequency but have no idea to set it.Right now it's 1.60 Ghz,that's quite a normal setting,no?

---

### Post by dzon65 on 2010-02-16
Check it out.Fan is going like crazy right now.

---

### Post by dzon65 on 2010-02-16
Managed to set cpu freq to 600 MHz (was 1.60).Much better,but still,processors still way up 70%.What's a good balance between cpu freq and "fast" working?

---

### Post by niffcreature on 2010-02-16
i have had this happen to actually, with various applications using the network, i think. what happens to me is that i close it when the cpu gets run up all the way, and the cpu is still at 100%, so i open the monitor and nothing there is nothing that is running it more than 6%. then it just slowly goes down... NOT the just the fan, the cpu usage. which is strange. normally when a process dies it ends immediately.
but the last part is beside the point.
what i think is really going on is that there is some kind of newly hidden process in 9.10
but that is just a guess. no idea. ive just never seen my cpu being used without finding a process using it.

---

### Post by dzon65 on 2010-02-16
Something defenetily wrong.Cpu going up to 100% and staying there.Never,ever had this before.

---

### Post by 3rdalbum on 2010-02-16
Even when you are running "just the desktop", there are still other programs running in the background. The desktop itself is a number of different programs. One of those MUST be thrashing the CPU.

Help us to help you. Open System Monitor and click on the tab that shows the list of running programs. Click on the "% CPU" heading above the list (twice, I think) to order the list by CPU use, so that the most CPU-heavy program is at the top. Watch for one of your programs to start using the CPU heavily. When you find out which program it is, tell us and we'll probably have some ideas about how to proceed.

---

### Post by lockalidiot on 2010-02-16
I have the same thing...

---

### Post by dzon65 on 2010-02-16
> **3rdalbum said:**
> Even when you are running "just the desktop", there are still other programs running in the background. The desktop itself is a number of different programs. One of those MUST be thrashing the CPU.
 
Help us to help you. Open System Monitor and click on the tab that shows the list of running programs. Click on the "% CPU" heading above the list (twice, I think) to order the list by CPU use, so that the most CPU-heavy program is at the top. Watch for one of your programs to start using the CPU heavily. When you find out which program it is, tell us and we'll probably have some ideas about how to proceed.
 
3rd,I already did,when nothing's running,4% goes to gnome,15% to system monitor.I'll have to get back to you later cause I'm on a work windows thing.
Anyway,this is areally very naked install.Only 2,8 something Gb.Thunar,mplayer,openbox,gpic......Happened out of the blue when this was a minimal install.Worked just fine,nothing added or so,it just started.To make sure it wasn't due to that install,I did a clean install (full 9.10),same thing happened.
But like I said,have to get back to you later.Thanks in advance.

---

### Post by gwagchunks on 2010-02-16
Looks like someone else has posted a similiar issue:

[http://ubuntuforums.org/showthread.php?t=1407638](http://ubuntuforums.org/showthread.php?t=1407638)

---

### Post by dzon65 on 2010-02-16
Many similar problems with cpu have been reported,not too many solutions though.I'll do a thorough check once I get home.I hope there's a solution for this cause it's impossible to work with.

---

### Post by Flying Pikachu on 2010-02-16
> **dzon65 said:**
> The last couple off days,the cpu goes up 80/90% without an appearing cause.Even when nothing is running,just desktop,the cpu goes way up,fan turning like crazy.I checked the monitor and everything looks normal,everything taks it's normal part.This is a very leightweight install and cpu very rarely goes past 30% as does the ram.It's as if something's running on the background,using A LOT.Anyone an idea?Added a screenshot when it starts rising,no prog running,out of the blue.(conky's a bad color but....)

That used to happen to me in all Windows Versions (Eg. XP, Vista and 7) and it was 90% of the time at 100% and this is on my desktop PC but i then installed ubuntu 9.10 and now my CPU is about 5 - 10% with firefox open and on the sotware centre (currently)

Also P.S how did you get that thing on the right with all the system status?

Thanks.

---

### Post by dzon65 on 2010-02-16
> **Flying Pikachu said:**
> That used to happen to me in all Windows Versions (Eg. XP, Vista and 7) and it was 90% of the time at 100% and this is on my desktop PC but i then installed ubuntu 9.10 and now my CPU is about 5 - 10% with firefox open and on the sotware centre (currently)

Also P.S how did you get that thing on the right with all the system status?

Thanks.

I think you mean conky.It's in the synaptics,takes a while to configure though.

---

### Post by dzon65 on 2010-02-16
Okay guys,back home.Allright,like I said.System monitor takes some 10% cpu and that's it.Yet,even though cpu frequency is set to 800MHz , cpu runs well over 70% and the fan like halfspeed (so to speak).Not crazy but still,running.Don't think I ever heard the fan before.Took a lot to take the cpu up to 30% before.

---

### Post by dzon65 on 2010-02-16
Can't make sense of this.Here's the cpu.

---

### Post by dzon65 on 2010-02-16
And here the graphics:

---

### Post by cgroza on 2010-02-16
On my desktop ubuntu 9.10 runs very slow, and always my cpu does not drop below 80% .Try an earlyer version of ubuntu. Hardy and ibex run very fast on my desktop.

---

### Post by dzon65 on 2010-02-16
Yeah,heard it before but.9.10 has been running on this pc since octobre/november without a serious problem.This just started couple of days ago.

---

### Post by dzon65 on 2010-02-16
Doing a total minimal reinstall (could bake eggs on the pc).So far looking good.Keeping an eye ,a big one ,on it.

---

### Post by dzon65 on 2010-02-17
Okay.Reinstall seems to be working good.I'll consider the thread closed.

---

### Post by 3rdalbum on 2010-02-17
> **dzon65 said:**
> Can't make sense of this.Here's the cpu.

Sorry, but that was a useless screenshot from our point of view. You're scrolled down halfway in the process list, so all we can see is a bunch of processes using close to 0% CPU time. What we really would need to see is the top or bottom of the list, where the processes are using lots of CPU time.

---

### Post by dzon65 on 2010-02-17
3rd.Did a total reinstall and seems okay now.As for that screenshot.That was just the point,nothing there with a high cpu,bottom or top.
Must have been something with that install,but like I said,new install working fine.

---

