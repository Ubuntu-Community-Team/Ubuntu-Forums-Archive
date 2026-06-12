---
title: "[SOLVED] Thunderbird, gets a life!"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by jay li on 2008-12-11
Every time I plug my eee pc to the power, Thunderbird opened by himself.
Any ideas what causing it?

Ubuntu 8.10
Asus Eee PC 701 4G Surf

P.S. No problem with Ubuntu 8.04

---

### Post by Ong on 2008-12-11
It might be a startup program.To disable it, go to system> preferences>sessions.On the startup programs tab look for Thunderbird and uncheck it:confused:

---

### Post by jay li on 2008-12-12
Thunderbird is not there.

---

### Post by lisati on 2008-12-12
My copy of Xubuntu sometimes seems to remember what was running when I shut it down, and start them up again when I next boot Xubuntu - I usually get round this by manually closing any programs that I don't want automatically loaded before shutting it down (if I remember).

---

### Post by jay li on 2008-12-12
Let me refresh my problem.

When my battery laptop is empty then I need to charge it, right?
Now if I plug the AC Adaptor to electricity then Thunderbird pop up. 
I had this problem with evolution too, and it's drive me nuts. 
So I removed it and install Thunderbird, thinking maybe I'll solve this nasty habit. 
I think it's a bug on Ubuntu 8.10, cause on Ubuntu 8.04 it didn't happen.

---

### Post by misfitpierce on 2008-12-12
It could be a bug... Did you try uninstalling thunderbird plug in eeepc then unplug then reinstall with it plugged in then try unplugging and replugging in?

---

### Post by jay li on 2008-12-12
No, I did not. 
But first let me see if I understand you. 
Are you suggesting me to install thunderbird while my laptop is connected to the wall, and see what will happen?

---

### Post by Rhubarb on 2008-12-12
This happens to me too on my eee PC S101 with Ubuntu 8.10
I haven't had much time recently to try and figure out what's going on.
Suffice to say I haven't even done a simple web search on it yet either.

If I discover anything before the solution is worked out here, I'll post a message here in this thread.

It's quite bizzare, when my eee PC is running off battery power, then connect the AC power cord up to it, it then opens up the default email application (which for me in this case is evolution).

---

### Post by jay li on 2008-12-12
Thanks Rhubarb.

---

### Post by cariboo on 2008-12-12
Have either of you tried System-->Preferneces-->Sessions-->Options
and chcecked to see if Automatically remember running apllcations when logging out is checked?

If it isn't, close all running applications then put a check mark in the above command, then shutdown and restart to see if Thunderbird or other applications opens at startup.

Jim

---

### Post by Aearenda on 2008-12-12
It looks to me as though something triggered by the change in power status is starting the mail application. It's nothing to do with saved sessions or logging off and on. When you plug the power in the ACPI subsystem reports this and it can trigger changes, such as running a program. Unfortunately, I'm not familiar with Xubuntu so I can't suggest how to change this on your system.

---

### Post by mobilediesel on 2008-12-12
> **cariboo907 said:**
> Have either of you tried System-->Preferneces-->Sessions-->Options
and chcecked to see if Automatically remember running apllcations when logging out is checked?

If it isn't, close all running applications then put a check mark in the above command, then shutdown and restart to see if Thunderbird or other applications opens at startup.

Jim

It doesn't sound like a startup issue. I think he's saying that, if the computer is already powered up, the email application launches when he plugs it into AC power. The computer is already on and in use.

---

### Post by jay li on 2008-12-12
Hi, cariboo907 I tried your suggestion but unfortunately nothing changed.

---

### Post by Rhubarb on 2008-12-12
Looks like this is a known bug, see here:
[https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/268422](https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/268422)

I'm just about to try the solution that's mentioned there on mine.
I'll report my findings.

---

### Post by lisati on 2008-12-12
> **Aearenda said:**
> It looks to me as though something triggered by the change in power status is starting the mail application. It's nothing to do with saved sessions or logging off and on. When you plug the power in the ACPI subsystem reports this and it can trigger changes, such as running a program. Unfortunately, I'm not familiar with Xubuntu so I can't suggest how to change this on your system.

I mentioned Xubuntu - I think the OP uses Ubuntu. Personally, I'm not overly bothered by the relatively minor inconvenience of having Thunderbird or whatever else was running sometimes being "remembered" when I restart my machine for whatever reason.... my own solution is to remember to shut down what I don't want active on restart, and to exerecise patience when I've forgotten.

---

### Post by Rhubarb on 2008-12-12
To fix this:

Open up a terminal (Applications --> Accessories --> Terminal), and enter this in:
```
gksu gedit /etc/acpi/events/asus-mail
```
- You will need to enter in your password

Comment out the last two lines with a **#** in front, so it looks like this:
> # /etc/acpi/events/asus-mail
# This is called when the user presses the mail button and calls
# /etc/acpi/hotkey.sh for further processing.

# event=hotkey (ATKD|HOTK) 00000050
# action=/etc/acpi/mailbtn.sh
Then save and quit gedit.

Now, restart the acpi service for changes to make effect (so you don't need to restart your netbook):
```
sudo service acpid restart
```

Then plug in your AC adapter, and the email application should not start up :D

- Rhubarb

---

### Post by jay li on 2008-12-12
> **Rhubarb said:**
> Looks like this is a known bug, see here:
[https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/268422](https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/268422)

I'm just about to try the solution that's mentioned there on mine.
I'll report my findings.

Thanks Rhubarb.

You know I tried google it several times, and I didn't find any mention about it.

---

### Post by jay li on 2008-12-12
:D Finely this problem has been solved.

Thank you! Rhubarb.

---

### Post by jay li on 2008-12-12
OK, since this has been solved do I have to make somthing, get this thread mark as "[SOLVED]"?

---

### Post by Rhubarb on 2008-12-12
There should be a way to mark this thread as solved.
I'm not sure how as I mainly answer threads not create them :P

I did a google search for something like "intrepid power email evolution".

---

### Post by jay li on 2008-12-12
Can't find it yet, but hi thanks man for everything. :D

---

### Post by capnthommo on 2008-12-12
hi, dunno if you found it yet but to mark the thread solved look at the top and on the right there's atab for "thread tools" click there and there is an opdtion for mark thread as solved.  hope that helps
cheers

---

### Post by jay li on 2008-12-12
Thanks to you too, I just did.
BTW my name is jay li, remember that... ;-)

---

### Post by capnthommo on 2008-12-12
oops, sorry to sound so off hand, jay li.  best of luck
nigel

---

### Post by jay li on 2008-12-12
Best of luck for you too, and thanks again capnthommo.

---

### Post by brokenLockpick on 2009-01-16
Wow that was just the ticket Rhubarb. I was having the same problem on my 900a, thanks for the informative post.

---

