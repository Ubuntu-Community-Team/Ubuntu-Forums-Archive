---
title: "The use of Wine and Cursor jumping when mis-typing"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by Jim Hazou on 2009-10-22
1)  When is Wine going to be replaced/updated?  It is next to useless and without it I have to resort to MS OS (Vista) in order to run aviation planning software which is MS based.  How about a something like 'Parallel' which runs on Macs?

2) Whenever I mis-type the typing carriage blinking cursor jumps to wherever the mouse cursor happens to be.  This is extremely annoying; it doesn't happen with MS OS software such as Word or Outlook, but with Ubuntu it happens on every application; Open Org, Thunderbird, Firefox etc.  I have tried to change the keyboard typing seetings/preferences, but it doesn't seem to make much difference.

Thanks in advance,

Jim

---

### Post by revanb on 2009-10-22
You can try using VirtualBox to run your Aviation software in windows in Linux.

I don't understand your other question.

---

### Post by 3rdalbum on 2009-10-22
> **Jim Hazou said:**
> 1)  When is Wine going to be replaced/updated?  It is next to useless and without it I have to resort to MS OS (Vista) in order to run aviation planning software which is MS based.  How about a something like 'Parallel' which runs on Macs?

Wine is constantly updated, but it is incredibly difficult and slow work to reimplement Microsoft Windows, especially with all its "undocumented features". Wine is a last resort effort for people who need to run a particular Windows program.

As for your other question, Parallels Workstation is virtualisation software; that is, it runs an existing copy of Windows (or other operating system) within a window on your desktop. It is available from the Canonical Software Store (for 8.04) but it doesn't get used a lot on Linux because we already have the free Virtualbox. By all means, if you have an installable copy of Windows and you need to run your program, get Virtualbox from the repositories and install Windows and your program within it.

---

### Post by Hospadar on 2009-10-22
I also vote for virtualbox.  It runs a complete copy of windows on a virtual machine and has basically none of the strange compatability issues wine does.

The only reason you might use wine is for perfomance.  Because virtualbox (and parallels) emulate an entire machine, they have much higher requirements than wine.  Wine is actually a program loader and windows system library implementation that (at runtime) converts windows executables to linux executables as well as providing implementations of windows system calls and services.  This is super complex and the fact that it works at all is in my book a miracle.  There are of course lots of downsides to the wine approach, but the upshot is that since wine is running things natively (i.e. not in an emulator) there is almost no performance drop.  A lot of applications (for example 3-d games) would be totally unusable inside a virtual machine (where as something like microsoft office is perfectly happy in a virtual machine).

So it's a performance/compatability tradeoff.  Usually a virtual machine is better (and I think virtual box is the easiest to use) but in the cases where you really need the absolute most performance you can get, you have to live with wine.

---

### Post by mrboojive on 2009-10-22
> **Jim Hazou said:**
> 2) Whenever I mis-type the typing carriage blinking cursor jumps to wherever the mouse cursor happens to be.  This is extremely annoying; it doesn't happen with MS OS software such as Word or Outlook, but with Ubuntu it happens on every application; Open Org, Thunderbird, Firefox etc.  I have tried to change the keyboard typing seetings/preferences, but it doesn't seem to make much difference.

I'm not exactly sure what "mis-type" means, but are you on a laptop? It sounds like you are accidentally touching the touchpad while typing.

---

