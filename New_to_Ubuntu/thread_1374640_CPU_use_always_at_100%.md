---
title: "CPU use always at 100%"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by Cod on 2010-01-07
Hi
I recently installed Karmic on my wife's laptop. It has never worked properly.  One of the main problems is the computer is very slow and stuttery.  This does not happen when I boot into Windows.  Looking at System Monitor it appears that CPU use is at 100%.  However, looking under processes (either in System Monitor or using ps aux in a terminal) there appear to be only a few processes actually using processor.  Total processor according to the list of processes is about 20%.

I really don't know what is going on.  Judging by the performance of the computer it seems like something is chugging away in the background but I don't know what.

Can someone help a relative newbie?

Thanks

---

### Post by melrokz on 2010-01-07
System monitor > view menu > All processes.

Do this and u can see all processes. U can find which one is problematic.
Do use 'kill process' with caution, though, as u would do on Windows.
Or issue this command in a Terminal:

top

---

### Post by Cod on 2010-01-07
Hi,
Thanks for the assistance.

If I view all processes in System Monitor I can the processes that are running.  Only a few processes are listed as using the CPU and the largest one is Nautilus at about 10%.  Adding the CPU usage up from these processes comes to about 25%.

However, on the Resources tab the CPU use is at 100% (the little System Monitor icon in the top bar is full of blue too).

So apparently the combined total CPU use of my processes is not 100%.  But my CPU is using 100%.  The computer performance is really being hit.

Weird.  Any further ideas.

---

### Post by melrokz on 2010-01-07
how bout clicking on the '% CPU' on the processes tab so that u have the processes with max cpu usage on the top? And did u try 

top

in a terminal?

---

### Post by melrokz on 2010-01-07
Applications > Accessories > Terminal.

just type:
top
and press enter.

---

### Post by iponeverything on 2010-01-07
Try turning off compiz, if it is on. Also is the tracker applet running. Try killing it.

---

### Post by Temposs on 2010-01-07
sometimes you can see processes in the "top" program that you can't see in System Monitor, so you should run the "top" command in terminal.

---

### Post by Cod on 2010-01-07
Thanks for the suggestions so far.

> Try turning off compiz, if it is on. Also is the tracker applet running. Try killing it. 

Under Appearance Preferences, I have Visual Effects set to None.  Is that the same as turning Compiz off?  If not, how do I turn off Compiz?

I have removed the System Monitor tracker applet from the bar.

>just type: top and press enter. 

If I understand the output correctly, running top in a terminal shows me that CPU use is around 90% (i.e 'Cpu(s): 90%us').  But again, looking at the list of processes, I estimate the total use of the processes is about 25%.  The two largest being nautilus and firefox.

Any other suggestions?

---

### Post by melrokz on 2010-01-07
take a screenshot and post it here???

---

### Post by Cod on 2010-01-07
Thanks again for your suggestions so far.
Here is a screen grab of the terminal with top running.

---

### Post by Soul-Sing on 2010-01-07
strange i don't see any stressed processes...

---

### Post by melrokz on 2010-01-07
Try:

```
sudo pkill evince-thumbnailer
```

Could be that evince is causing the problem.

otherwise:

```
sudo pkill nautilus
```

or try removing any connected removable drives.

---

### Post by Cod on 2010-01-07
Fantastic.  That did it.  You can see from the screengrab that the CPU use has dropped to something normal.

Unfortunately, I killed both processes before checking so I don't know which one was causing me problems.

I guess the next question is why they were a problem in the first place (and will that problem return when I reboot?).

Thanks for the help

---

### Post by Cod on 2010-01-07
Rebooted and the problem came back.  Almost 100% CPU use.

By killing Nautilus the CPU drops down to less than 10% so it looks to be cause of the problem.

Anyone got an idea why Nautilus is eating all my CPU (but not showing it in the process lists?)

---

### Post by Soul-Sing on 2010-01-07
There are known bugs and some comments on this: [http://www.mail-archive.com/ubuntu-us-ca@lists.ubuntu.com/msg00524.html](http://www.mail-archive.com/ubuntu-us-ca@lists.ubuntu.com/msg00524.html)
: [https://bugs.edge.launchpad.net/ubuntu/+source/brasero/+bug/413660](https://bugs.edge.launchpad.net/ubuntu/+source/brasero/+bug/413660)
but it is filed in august......

---

### Post by melrokz on 2010-01-07
My pleasure. I'm also still discovering linux, and i'm going to learn RHCE!
So, 4 the timebeing, try,

```

sudo pkill nautilus
gdb nautilus
(gdb) run

```

and post the output...

---

### Post by melrokz on 2010-01-07
looks like a hardware problem...

---

### Post by Cod on 2010-01-07
You might be onto somwthing with gdb.

Looks like there is some kind of usershare problem.  I don't know what that actually means or if it is important.  Here is the output:

```

(gdb) run
Starting program: /usr/bin/nautilus 
[Thread debugging using libthread_db enabled]

(nautilus:2603): Eel-CRITICAL **: eel_preferences_get_boolean:
     assertion `preferences_is_initialized ()' failed
[New Thread 0xb7ea1b70 (LWP 2606)]
Initializing nautilus-gdu extension
[New Thread 0xb6be3b70 (LWP 2607)]
[Thread 0xb6be3b70 (LWP 2607) exited]

** (nautilus:2603): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:2603): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:2603): WARNING **: No marshaller for signature of signal 'ShareCreateError'
[New Thread 0xb6be3b70 (LWP 2609)]
[New Thread 0xb62fab70 (LWP 2610)]
(...snip)
[New Thread 0xb21a5b70 (LWP 2622)]
Nautilus-Share-Message: Called "net usershare info" but it failed:
    'net usershare' returned error 255: net usershare: cannot open 
     usershare directory /var/lib/samba/usershares. Error No such
     file or directory
Please ask your system administrator to enable user sharing.

[Thread 0xb62fab70 (LWP 2613) exited]
[Thread 0xb31b0b70 (LWP 2620) exited]

snip...
etc...

```

---

### Post by melrokz on 2010-01-07
1. what all software did u install in Ubuntu?
   If you are using file sharing, u have to install smbclient.

2. You can enable a share (and install smbclient) like this: In a terminal:

```
shares-admin
```

this program will help you add shares too, but I dont know how this will solve your cpu load problem :-(

---

