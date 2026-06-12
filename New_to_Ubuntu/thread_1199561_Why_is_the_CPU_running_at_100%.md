---
title: "Why is the CPU running at 100%?"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by dunbrokin on 2009-06-29
...but when I check in htop etc....i can only find about 25% of cpu?

---

### Post by mcduck on 2009-06-29
What makes you think you have CPU usage of 100% if top reports only 25%?

Could you post output of top here so we can have a look, otherwise this is just going to be a random guessing competition.. ;)

---

### Post by dunbrokin on 2009-06-29
[QUOTE=mcduck;7533550

Could you post output of top here so we can have a look, otherwise this is just going to be a random guessing competition.. ;)[/QUOTE]

How do I capture the output of TOP in text format to print here?

---

### Post by dunbrokin on 2009-06-29
Ah...I think this is what you are looking for..

---

### Post by mcduck on 2009-06-29
Just highlight the text in terminal, and then middle-click to paste it. Or sue Shift-Ctrl-C to copy from terminal.

And you'll definitely want to use the code-tags (the "#"-button when typing a message to these forums) around the output.

edit: screenshot works quite fine as well, but then you'll have to make it big enough to actually show the process names etc. Also, make sure you haven't hidden kernel threads or other user's processes, and that you have scrolled to very top of the output (so that the programs with highest CPU usage are actually visible)

---

### Post by dunbrokin on 2009-06-29
Oooops...sorry ...on all counts....

---

### Post by SunnyRabbiera on 2009-06-29
Sometimes readouts like this are not that accurate with linux, the way Linux interacts with hardware is much different then how windows does.
Sometimes the readouts take a guess with things like RAM, hard drive space, CPU scaling and the like.
But this depends on the hardware, some hardware interacts well with Linux while others sometimes there is a workaround used.
I have seen this happen with my hardware, but its mostly nothing to worry about.
But I have seen windows do it too.

---

### Post by dunbrokin on 2009-06-29
OK, thanks....not seen it happen before....I think it changed during the last update.

---

### Post by lovinglinux on 2009-06-29
I've seen cases where the system monitor app in the gnome panel reports 100% CPU usage and you feel that the machine is busy, but top gives a report with much less CPU usage.

I bet the problem is the Remote Desktop, which is loaded by default. To solve this open "System >> Preferences >> Startup Applications (aka Session)", disable the "Remote Desktop" option and reboot.

---

### Post by dunbrokin on 2009-06-29
Yeah, Hmmmm.

The problem is that this PC does need the remote desktop as it is the one that runs my weather station and I need to interrogate it from my normal PC.

---

### Post by lovinglinux on 2009-06-29
> **dunbrokin said:**
> Yeah, Hmmmm.

The problem is that this PC does need the remote desktop as it is the one that runs my weather station and I need to interrogate it from my normal PC.

I wouldn't use remote desktop. It's not secure.

If you need remote access, use ssh. You can do anything from ssh command-line. If you need or prefer graphical interface, then enable ssh X forwarding, so you can launch applications from the remote machine, but display them on the local machine. The only difference is that you don't see the desktop. Additionally, you can setup ssh to use encryption keys.

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)
[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)
[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)
[https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

---

### Post by dunbrokin on 2009-06-29
Thanks...maybe it is time for me to move to ssh.

---

### Post by dunbrokin on 2009-06-29
> **lovinglinux said:**
> I wouldn't use remote desktop. It's not secure.
. The only difference is that you don't see the desktop. [/url]

Hmmm...I need to see the Weather Station graphs etc from my own PC...so does that rule out SSH?

---

### Post by dunbrokin on 2009-06-29
> **lovinglinux said:**
> 

I bet the problem is the Remote Desktop, which is loaded by default. To solve this open "System >> Preferences >> Startup Applications (aka Session)", disable the "Remote Desktop" option and reboot.

You win your bet...that did indeed solve the problem....but now I cannot see my Weather PC...so I guess SSH is the way to go to solve that.

---

### Post by Pinball Wizard on 2009-06-29
You would be amazed what you can do through SSH. How is the weather info displayed though?

---

### Post by lovinglinux on 2009-06-29
> **dunbrokin said:**
> You win your bet...that did indeed solve the problem....

;)

> **dunbrokin said:**
> but now I cannot see my Weather PC...so I guess SSH is the way to go to solve that.

What is a Weather PC?

> **dunbrokin said:**
> Hmmm...I need to see the Weather Station graphs etc from my own PC...so does that rule out SSH?

Can you explain what are those graphs? I think ssh with X forwarding should do the trick, because it allows you for example to run Firefox on the remote machine, using the profile of the remote user, but display it on your screen.

---

### Post by QIII on 2009-06-29
Try turning Vino off.

Despite what top is telling you, Vino can be a CPU hog.

EDIT:  Doh!  Should have read the rest of the thread.  Never mind.  That seems to have fixed the immediate problem.

---

### Post by dunbrokin on 2009-06-30
> **lovinglinux said:**
> ;)

What is a Weather PC?

Can you explain what are those graphs? I think ssh with X forwarding should do the trick, because it allows you for example to run Firefox on the remote machine, using the profile of the remote user, but display it on your screen.

My Weather PC is an old lap top connected to my weather station...it sends the data every couple of minutes to Weather Underground. As the Weather PC is remote from my normal PC I like to check it occasionally. It runs a program called Weather Display which gives a dashboard display of the various instrument. Using VNC, I can easily log in can see what is going on.

---

### Post by dunbrokin on 2009-06-30
> **lovinglinux said:**
> I wouldn't use remote desktop. It's not secure.

l]

But it is only being used within the confines of the LAN. Surely that is as secure as any PC on the LAN.

---

### Post by Pinball Wizard on 2009-07-01
Yeah, plus can't you have a secure remote desktop connection?

---

### Post by lovinglinux on 2009-07-01
> **Pinball Wizard said:**
> Yeah, plus can't you have a secure remote desktop connection?

Yes, you can tunnel the Remote Desktop connection through ssh ;)

[https://help.ubuntu.com/community/SSH/OpenSSH/Advanced?action=show&redirect=AdvancedOpenSSH](https://help.ubuntu.com/community/SSH/OpenSSH/Advanced?action=show&redirect=AdvancedOpenSSH)

---

