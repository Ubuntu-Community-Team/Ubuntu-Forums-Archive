---
title: "How do I create a file in the kernel folder?"
date: 2010-10-29
forum: New to Ubuntu
---

### Post by amateur_mav on 2010-10-29
I got this message in my kernel log to "echo 2 > /proc/sys/kernel/perf_counter_paranoid" and no matter what sudo command I use in the root terminal or in nano, I get "Permission Denied" or "No such file or directory" and "Could not find" from gksudo gedit - can Anyone HELP me get this file created?  I am very new with these commands and environment and all out of patience. Thanks for viewing this...

By the way, my prompt is a # not a $. Would that make the difference? How do I change it?

---

### Post by BugBuster on 2010-10-30
Try this ..
```
sudo -i
```
This will mimic a proper root prompt.
Then at the root prompt,run your command;
```
 echo 2 > /proc/sys/kernel/perf_counter_paranoid 
```

I have found by personal experience that somehow sudo does not always work when used along with the echo command, while the above trick always does.

---

### Post by amateur_mav on 2010-10-30
Thanks so much for the hint BugBuster. I got the root prompt but the echo command responded with "No such file or directory" so I switched to nano and got the same error. 
I really don't know beans about Linux but I have 25 years experience with DOS/Windows.  I fell in love with this new version of Ubuntu and have an XP VirtualBox guest working wonderfully.  This message just started appearing at boot time and I can't get the file created. I have a bad feeling it has something to do with directory permissions, which I have been unsuccessful at changing too.

By the way, my prompt is a # not a $. Would that make the difference? How do I change it?

---

### Post by oldos2er on 2010-10-30
What is your goal in creating that file? /proc is a virtual filesystem and I don't think it's meant to be written to by any users.

---

### Post by amateur_mav on 2010-10-30
> **oldos2er said:**
> What is your goal in creating that file? /proc is a virtual filesystem and I don't think it's meant to be written to by any users.

You are very right Ann. I just installed Oracle's VM VirtualBox and now I get this message everytime I boot up:

kernel: [   13.933461] vboxdrv: Trying to deactivate the NMI watchdog permanently...
kernel: [   13.933468] vboxdrv: Warning: 2.6.31+ kernel detected. Most likely the hardware performance
kernel: [   13.933470] vboxdrv: counter framework which can generate NMIs is active. You have to prevent
kernel: [   13.933472] vboxdrv: the usage of hardware performance counters by
kernel: [   13.933474] vboxdrv:   echo 2 > /proc/sys/kernel/perf_counter_paranoid

I've tried using the chown and chmod commands with no success. I'm just too new at this to know how to do it right. Thanks for the reply.

---

### Post by amateur_mav on 2010-10-30
Recent Posts on the virtualbox.org forum

by Perryg » 30. Oct 2010, 18:34
Tell us why you are interested in doing this. Is it only due to the log file, or are you having problems?
_______________________________
by amateur_mav » 30. Oct 2010, 18:39
Thanks Perryg,
I haven't experienced any visual problems as of yet but I just installed VirtualBox 2 days ago. If the message isn't meaningful, then why is it displayed at every boot?
_______________________________
by Perryg » 30. Oct 2010, 18:45
Maybe it is the process of things. There are a lot of things that goes on in the background especially with kernels and their parameters.
I see that on a lot of my VMs and if you look further down you will see that it has either been taken care of or it has been ignored. If it was a true problem I suspect that you would be having serious problems. It is good you are reading and learning, but keep in mind that VirtualBox is actually emulating a processor and you will see errors (some false positives) on occasion. Report problems but I would not try to edit or change the files you are suggesting or the VM will become useless.
_______________________________
by amateur_mav » 30. Oct 2010, 19:01
Thanks again Perryg,
The only message I get about VirtualBox after that one in the kernel log at boot time is:

**kernel: [ 2732.625550] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)**

and maybe this one:
kernel: [ 16.490878] Disabling lock debugging due to kernel taint

but they don't appear on the screen.

It seems to me that preventing the usage of the hardware performance counter to the OS would be counter productive
but is that what that instruction is for?
_______________________________
by Perryg » 30. Oct 2010, 19:09
Nothing to worry about.
Different OSes and kernels report things like this, but in all actuality is still works.
_______________________________
by amateur_mav » 30. Oct 2010, 19:21
Your replies are very much appreciated Perryg but my original question still hasn't been answered.
I'm a DOS man actually, and I can't stand it when I don't have total control over my system. I am only now beginning to learn Linux and I do have a small learning curve to navigate but it's nowhere as complicated as MS VBasic. Know what I mean?
_______________________________
by Perryg » 30. Oct 2010, 19:34
OK to answer you original question

echo 2 > /proc.sys/kernel/perf_counter_paranoid is not a file. The /proc (processor) folder is not there to edit and it will kill your host if you keep messing around with it.

Actually Visual Basic is easy compared to a lot of programming languages. But that is just my opinion.

(oh and you did not have total control over DOS either unless you knew assembler and could write your own, but I do know what you mean.)
_______________________________
by amateur_mav » 30. Oct 2010, 19:54
Bless you Perryg, bless you. I can finally move on. Thanks very very much.

(and I do write machine code)
________________________________
by amateur_mav » 1. Nov 2010, 21:12 

Hey Perrryg - 

How come you didn't tell me about the fix that was already posted on August 3??
Now I feel like an idiot cause my original search to find something on this topic didn't appear.

For everyone else reading this post, the fix is explained like this:

_____________________________________________
Re: Annoying "2.6.31+ kernel detected" errors

Postby Frank Mehnert » 3. Aug 2010, 00:50
These messages are not real errors (although printed with the KERN_ERR tag) but warnings.
The real fix which makes this message obsolete is quite complicated and even VBox 3.2.8 will not contain it.
**For now it is important to not use hardware-aided performance counters on the host while running VMs with VirtualBox**, therefore the warning.
_____________________________________________
Re: Annoying "2.6.31+ kernel detected" errors

Postby Prikrutil » 3. Aug 2010, 12:08
Frank Mehnert, thanks for your answer.

According to your letter in mailing list [http://vbox.innotek.de/pipermail/vbox-d](http://vbox.innotek.de/pipermail/vbox-d) ... 02860.html /proc/sys/kernel/perf_event_paranoid has to be used instead of /proc/sys/kernel/perf_counter_paranoid

So there are two quite easy to implement in 3.2.8 things which will make this message go away until the real fix is ready

1. Change /proc/sys/kernel/perf_counter_paranoid to /proc/sys/kernel/perf_event_paranoid in the warning message
2. If /proc/sys/kernel/perf_event_paranoid already contains 2, there shouldn't be any warnings in errors.log

Having errors.log full of warning messages I can't really fix is really annoying :(

Thanks!

_________________________________

Oh, now I know, it doesn't work.
:(

---

### Post by amateur_mav on 2010-10-31
I will just have to wait for the version of Oracle's VirtualBox that has this fixed but I think this should be an Ubuntu task installing a proper switch for this.
 :(

---

