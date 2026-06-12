---
title: "Guru Needed!"
date: 2011-09-08
forum: New to Ubuntu
---

### Post by Nickjpost on 2011-09-08
Is it possible to start a program in windows from a Linux terminal?

*Let's say this is 'program.exe' & I want to run it and it is in c:\Program Files\program.exe, could I run the .exe from a Linux terminal using that file path, say via samba?

Your insight is very valuable & appreciated!!

---

### Post by haqking on 2011-09-08
> **Nickjpost said:**
> Is it possible to start a program in windows from a Linux terminal?

*Let's say this is 'program.exe' & I want to run it and it is in c:\Program Files\program.exe, could I run the .exe from a Linux terminal using that file path, say via samba?

Your insight is very valuable & appreciated!!

kind of.

But you need wine to support .exe on Linux [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

but depends on what you are trying to run, not everything is supported in wine.

Far better to find a linux alternative, alot of which are better IMO than the Windows alternatives.

What exactly do you wish to run under Linux from the windows world ?

or there is virtualisation [www.virtualbox.org](www.virtualbox.org)

---

### Post by grahammechanical on 2011-09-08
I think that one condition to getting this to work is that the Linux terminal issuing the run command is on one machine and program.exe is on another machine and Windows is already running and the two machines are networked. Is this not a matter of remote access?

Regards.

---

### Post by haqking on 2011-09-08
> **grahammechanical said:**
> I think that one condition to getting this to work is that the Linux terminal issuing the run command is on one machine and program.exe is on another machine and Windows is already running and the two machines are networked. Is this not a matter of remote access?

Regards.


ahh i see.

He wants to connect to a remote machine and and execute an executable on that machine to run ?

is this the OP question ?

---

### Post by Nickjpost on 2011-09-08
> **haqking said:**
> ahh i see.

He wants to connect to a remote machine and and execute an executable on that machine to run ?

is this the OP question ?

Yes, that is what I want to do: Run a windows program remotely on a windows machine from a Linux terminal....kinda like using **net rpc**. I realize there are many workarounds, but this is to help make a task at work easier & I have no way to modify the Linux machine or windows machine. :)

Thank you both for replying and taking on this challenge; it is MUCH appreciated!

---

### Post by haqking on 2011-09-08
> **Nickjpost said:**
> Yes, that is what I want to do: Run a windows program remotely on a windows machine from a Linux terminal....kinda like using **net rpc**. I realize there are many workarounds, but this is to help make a task at work easier & I have no way to modify the Linux machine or windows machine. :)

Thank you both for replying and taking on this challenge; it is MUCH appreciated!


if you have no way to modidy either machine, then you are asking how to run a remote process on a remote machine without authorisation...this is cracking...LOL ;-)

if you cant make modifications then NO

---

### Post by Nickjpost on 2011-09-08
> **haqking said:**
> if you have no way to modidy either machine, then you are asking how to run a remote process on a remote machine without authorisation...this is cracking...LOL ;-)

if you cant make modifications then NO

The program I am running is to calibrate a POS register when to access that program through the hardware's gui is impossible, not to crack for my own purposes, thank you.

After thinking a bit, I understand how it seems I guess & respect the implications that you are concerned about, but dishonesty is not my intent; I simply want a quicker, more efficient way to assist my customers.

---

### Post by haqking on 2011-09-08
> **Nickjpost said:**
> The program I am running is to calibrate a POS register when to access that program through the hardware's gui is impossible, not to crack for my own purposes, thank you.

ok it wasnt meant offensively, you never know on here what is being asked.

But if you have no way to modify either machine i dont see how, remote access of some type needs to be set up.

You need to telnet, remote desktop, ssh etc into the machine to execute the process.

I am presuming you are not an admin for these machines ?

If you have access to the remote machine you could run a VM on your Ubuntu and issue the net commands from that if thats what you are used to ?

---

### Post by Nickjpost on 2011-09-08
> **haqking said:**
> ok it wasnt meant offensively, you never know on here what is being asked.

But if you have no way to modify either machine i dont see how, remote access of some type needs to be set up.

You need to telnet, remote desktop, ssh etc into the machine to execute the process.

I am presuming you are not an admin for these machines ?

If you have access to the remote machine you could run a VM on your Ubuntu and issue the net commands from that if thats what you are used to ?


No offense taken, I understand how it may have seemed to you. I do have limited Administrator privileges & am able to reboot & shutdown the machines, modify & change files, but I can not install new software, so I'm guessing I should, if it were possible with my admin passwd, be able to execute a program. I wouldn't be able to run a vm because when connected to my customer's network for trouble shooting, the linux terminal is all I have...a privelaged user with limited rights.

---

### Post by Gone fishing on 2011-09-08
Interesting question.

I suppose you could use VNC but their must be a much better way.

I'm wondering if Windows Services for UNIX Version 3.5 would allow you to SSH into a windows box and start applications?

[http://support.microsoft.com/kb/321712](http://support.microsoft.com/kb/321712)
[http://www.microsoft.com/download/en/details.aspx?id=274](http://www.microsoft.com/download/en/details.aspx?id=274)

---

### Post by haqking on 2011-09-08
> **Gone fishing said:**
> Interesting question.

I suppose you could use VNC but their must be a much better way.

I'm wondering if Windows Services for UNIX Version 3.5 would allow you to SSH into a windows box and start applications?

[http://support.microsoft.com/kb/321712](http://support.microsoft.com/kb/321712)
[http://www.microsoft.com/download/en/details.aspx?id=274](http://www.microsoft.com/download/en/details.aspx?id=274)


VNC and SSH require him to modify the remote machine to be able to, he cant do that thats the problem ;-)

---

### Post by s.fox on 2011-09-08
Closed for review.

Edit:- The thread will remain closed - suspected illegal activities.

---

