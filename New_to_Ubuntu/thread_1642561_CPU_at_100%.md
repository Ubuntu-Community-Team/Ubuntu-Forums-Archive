---
title: "CPU at 100%"
date: 2010-12-10
forum: New to Ubuntu
---

### Post by cmcanulty on 2010-12-10
Starting today my CPU is stuck at or near 100% with only a browser or a directory open. When I check system monitor I see nothing using that much CPU or RAM.Is there something I can post to pin this down? I can't even open a folder it is so stuck now.I am running Maverick and have 1 GB RAM worked fine until today even running a lot of stuff now I've stopped everything I can think of with no luck.I am attaching a screenshot showing how much CPU nautilus is taking I have a decent CPU: Mobile AMD Athlon(tm) 64 Processor 3700+

---

### Post by TeoBigusGeekus on 2010-12-10
```
top
```
or even better
```
htop
```
to see what's using the cpu. I've never trusted system monitor.

---

### Post by uRock on 2010-12-10
Do you have htop installed? It works a lot like the top command but has a few extra tools thrown in. htop will let you find, highlight, and kill whatever service is using up the CPU.

---

### Post by amjjawad on 2010-12-10
> **cmcanulty said:**
> Starting today my CPU is stuck at or near 100% with only a browser or a directory open. When I check system monitor I see nothing using that much CPU or RAM.Is there something I can post to pin this down? I can't even open a folder it is so stuck now.I am running Maverick and have 1 GB RAM worked fine until today even running a lot of stuff now I've stopped everything I can think of with no luck.I am attaching a screenshot showing how much CPU nautilus is taking I have a decent CPU: Mobile AMD Athlon(tm) 64 Processor 3700+

The screenshot you posted does not show the CPU is being used 100%.
You also mentioned it's stuck on 100% but it's not. I guess the figures are not accurate beside these figures/numbers keep changing.

---

### Post by cmcanulty on 2010-12-10
No but this chart shows it and it is stuck there or close to it[ATTACH]178061[/ATTACH]
I am installing htop then will repost, thanks all. OK I installed htop and got it running .I am attaching a screenshot of that also

---

### Post by smo0th on 2010-12-10
if you use 'top -S' and then 'shift+t' you'll see the top CPU-consuming processes, if you post that info it could help us to see what's going on wit your pc

---

### Post by cmcanulty on 2010-12-10
Here it is I typed top -S then when it ran I did the shift+t there are 2 screenshots evince thumbnails seems to be a big user don't even know what that is

---

### Post by Ahunt on 2010-12-10
This has been a really common problem with Ubuntu 10.10. I had the same problem on a test PC with 2 GB of RAM and a 2.66 Ghz Intel processor, a number of applications running on their own would max out the CPU, including playing videos in Totem (but not in VLC although that would run 70-95% CPU) and even just Ubuntu Software Centre just idling.

Launchpad has a number of bugs filed on this problem.

I tracked this problem from 10 October 2010 when Maverick came out until a week or two ago. Incidentally the box was dual booting Lubuntu and that hardly uses any CPU, even with many applications open, so that proved it was not a hardware problem, like a failing CPU.

I would suggest [downloading the Lubuntu ISO]("http://people.ubuntu.com/~gilir/lubuntu-10.10.iso"), burning a CD and trying that out in a live session. Lubuntu has a task manager similar to Ubuntu (but without the graph) and this will allow you to determine if it is a software or hardware problem. If the problem is not there with the live CD then the problem is Ubuntu and not your hardware. If so, you might want to try installing Lubuntu in a dual boot or sole installation and use that instead. We recently moved to Lubuntu on a desktop and netbook PC because the performance of Ubuntu 10.10 is just too slow for that hardware.

---

### Post by cmcanulty on 2010-12-10
I think 10.10 is a pretty bad distro is there a way to downgrade to 10.04? I hate to reinstall whole OS but will if needed.OK I just disabled all thumbnailers and still they are using a ton of CPU how can that be?

---

### Post by beew on 2010-12-10
Well while it doesn't consumes 100% cpu evince thumbnailer seems to be using lots of cpu nevertheless. Try to disable it and see what happens. I think this has to do with document preview. Open up any folder and choose edit and preference and then on the preview tab set the preview options to "no" and see what happens. Something like that. I can't be more precise because I have no access to Ubuntu right now.

Actually I find Maverick in general more efficient and uses less cpu than Lucid, especially with things like Videos. It is also faster. It is 10/10 perfect for me. Only Firefox still loads kind of slow but that is probably a firefox problem.

---

### Post by ajgreeny on 2010-12-10
> **cmcanulty said:**
> I think 10.10 is a pretty bad distro is there a way to downgrade to 10.04? I hate to reinstall whole OS but will if needed.
I'm afraid not.  If you want 10.04 again it will need to be a clean install.

I suggest you make a separate /home partition this time if you don't already have one as it is an enormous help when you come to install a new version of ubuntu, but can't, or don't want to do a distro update online.

[Separate /home]("http://www.psychocats.net/ubuntu/installseparatehome")

---

### Post by cmcanulty on 2010-12-10
I do have a separate home partition. Also I used gconf-editor to disable all thumbnails so how can the thumbnails still be hogging the CPU?

---

### Post by kainalu on 2010-12-10
If the computer hasn't been logged out yet, the "order" may have not gone through. Try killing the thumbnailer process manually.

in htop : 

press F6 and select CPU
Highlight the overburdening process
press F9, followed by 9, then press enter

---

### Post by cmcanulty on 2010-12-10
Oh great now CPU is at 30% I will try again tomorrow and see if it holds, thanks

---

### Post by amjjawad on 2010-12-11
I thought you already tried to **restart** or something before posting?! I mean that what I would do if I were you as the first step before doing anything else :)

---

### Post by zabsv on 2010-12-11
A good way to find out what something does is the man command. Typing "man evince-tumnailer" reveals that [I]evince-thumbnailer is a GNOME program to create thumbnails  from  Post&#8208;Script (PS), Portable Document Format (PDF), DjVu and DVI files. 
[/I]This process should only be running when new thumbnails are created, so I guess that you browsed a directory and something caused evince-thumbnailer to get stuck while creating these thumbnails.
Killing evince-thumbnailer and trying again could help. If it doesn't you may want to disable thumbnails only for the folder which is causing the problems.

---

### Post by cmcanulty on 2010-12-11
Yes I did restart but took a second restart and now seems solved, thanks all

---

### Post by amjjawad on 2010-12-11
> **cmcanulty said:**
> Yes I did restart but took a second restart and now seems solved, thanks all

Actually I meant to restart before posting here but never mind :)

Congratulation and I'm glad it worked for you ;)

---

