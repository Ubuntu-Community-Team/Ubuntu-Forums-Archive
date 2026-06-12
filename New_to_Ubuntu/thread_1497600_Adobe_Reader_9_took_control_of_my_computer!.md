---
title: "Adobe Reader 9 took control of my computer!"
date: 2010-05-30
forum: New to Ubuntu
---

### Post by Kellemora on 2010-05-30
Hi Gang

Don't know why, but Adobe took over control of my computer for 6 hours.

It took a COLD BOOT to get rid of its hold!

Both System Monitor and HTop showed 4 instances of acroread!
2 were at 0% and sleeping, the other 2 were at 100% of CPU usage on a dual core.

I tried using END PROCESS in System Monitor, THAT FAILED.....
I tried using END PROCESS in HTOP, THAT FAILED........
I tried ctrl-alt-backspace to restart the GUI, that killed the GUI and I had to log in again, but there was acroread still hogging the CPU.

I finally did a COLD-REBOOT to clear it out......

The running file was /opt/adobe/reader9/intellinux/bin/(etc, etc, etc.)

I have to use Adobe Reader because Evince CHOKES to death on pdf files!

Is there a version that does NOT take over control of your computer?????

TTUL
Gary

---

### Post by mikewhatever on 2010-05-30
I think Acroread 9 is the latest version, also, the fact that both Evince and Acroread choke on your pdfs suggests the latter might be the issue.

---

### Post by Autodave on 2010-05-30
[QUOTE=Kellemora;9385736]Hi Gang



The running file was /opt/adobe/reader9/intellinux/bin/(etc, etc, etc.)

I have to use Adobe Reader because Evince CHOKES to death on pdf files!

Is there a version that does NOT take over control of your computer?????


You might try xpdf-reader in the repositories (Synaptic Package Manager).  I've used it w/o any problems and w/o excessive memory usage.

---

### Post by Kellemora on 2010-05-30
This is NOT an ongoing problem, it just started about the time Firefox was updated to the latest auto-update version (3.0.19), along with a few other problems I've noticed.

I use a lot of pdf files and actually, this has never happened before to the extent NOTHING would kill the running programs.

These are very old files too, read many times with no problems.
The only thing different I've done lately is used Evince to open them to see if there were features there not in Adobe.

I didn't say the pdf files choked on Adobe, ONLY on Evince!!!!!
Which is probably why I installed Adobe Reader 9 in the first place.

What concerns me is not the fact Adobe went haywire, my real concern is the fact that it could not be killed by either System Monitor OR HTop or restarting the GUI, that tells me both of these Kill programs are FAULTY in what they are supposed to do.
KILL a running program!  FAILED..........

That seems to make it an Ubuntu problem or bug!
Which is WHY I came here with it instead of to Adobe!
They wouldn't know a thing about the Ubuntu END PROCESS function that failed!

TTUL
Gary

---

### Post by formaldehyde_spoon on 2010-05-30
Do you really need Adobe's bloat?  If the default pdf reader doesn't suit, you could try ePDF from the repos. 

>  I have to use Adobe Reader because Evince CHOKES to death on pdf files!

Ahh.  Try epdf from the repos.
**sudo apt-get install epdfview**

---

### Post by llamabr on 2010-05-30
I like xpdf, too, though there's a bit of trouble with the keybindings with my last update.

If it's associated with firefox, you could turn off the firefox adobe plugin.  In firefox:

tools > add-ons > plugins > adobe > disable

---

### Post by 3rdalbum on 2010-05-31
> **Kellemora said:**
> 
What concerns me is not the fact Adobe went haywire, my real concern is the fact that it could not be killed by either System Monitor OR HTop or restarting the GUI, that tells me both of these Kill programs are FAULTY in what they are supposed to do.
KILL a running program!  FAILED..........

No, you have to understand something about Linux here.

There are two (well, actually more, but it's easier to just say two) internal methods for killing programs. There's the safe one, which sends a SIGNAL 15 to the program. This basically asks the program to close down gracefully. If the program is not responding to signals, this will fail. Then there's the unsafe one, which sends a SIGNAL 9 to the kernel; the kernel will then immediately stop executing the program, not giving it time to close network connections or flush out any pending disk writing operations.

System Monitor sends SIGNAL 15. Top (I don't know about htop) gives you the choice of which signal to send. By default, it sends SIGNAL 15, but you can specify SIGNAL 9 instead.

So, you can do:

```
kill -15 <process-id>
```

and if that fails to have an impact, do:

```
kill -9 <process-id>
```

Nothing can stop a SIGNAL 9, but you always want to try SIGNAL 15 first to give the program a chance to gracefully quit. If you constantly went around SIGNAL 9'ing everything you'd end off with data loss/corruption. Trust me, losing your program preferences is a pain :-)

Alternatively, use 'top' to kill programs.

---

### Post by Kellemora on 2010-05-31
> **llamabr said:**
> I like xpdf, too, though there's a bit of trouble with the keybindings with my last update.

If it's associated with firefox, you could turn off the firefox adobe plugin.  In firefox:

tools > add-ons > plugins > adobe > disable

BINGO, You nailed it llamabr!!!!!
Well, in a roundabout way that is!
I just checked my Add-On's and there were 4 copies of Adobe Reader 9 in there.  So I assume all 4 tried to work at once, or at least 2 of them tried to work at once.
That would explain the sudden SLOW DOWN I've been experiencing also.

I removed all but version 9.1 and ran through the on-line PDF's that were giving me problems.  They opened fast like they used to and I could scroll all 14 pages almost instantly.  
I opened and closed several files and the Reader would shut down when I closed out as it's supposed to do.

I wonder where those other ones came from?
They were not there a few weeks ago, when I was removing a music player I didn't like.

I will also check out the epdf and xpdf programs in synaptic, seems like I tried xpdf before though and it didn't render images to the printer properly or something like that.

Thanks for the help gang!

TTUL
Gary

---

