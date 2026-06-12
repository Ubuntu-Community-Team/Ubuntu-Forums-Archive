---
title: "Unable to install"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by Spiffjiggins on 2009-11-27
I've tried literally all day today to install Ubuntu on two separate computers. One computer is crashed but I was told you can start the computer with a downloaded version of ubuntu and it will still work. If it won't that explains that, however on my HP Compaq 6110 laptop it tells me that I lack the memory to install saying I only have 247mb of memory. Do I actually have to increase my memory to install Ubuntu?

---

### Post by sandyd on 2009-11-27
> **Spiffjiggins said:**
> I've tried literally all day today to install Ubuntu on two separate computers. One computer is crashed but I was told you can start the computer with a downloaded version of ubuntu and it will still work. If it won't that explains that, however on my HP Compaq 6110 laptop it tells me that I lack the memory to install saying I only have 247mb of memory. Do I actually have to increase my memory to install Ubuntu?
you need at least 375mb to install to install ubuntu
if your using a 247mb laptop, use xubuntu, puppy, dsl, or some other less-ram sucking OS.

---

### Post by Spiffjiggins on 2009-11-28
That was it! Thanks. But now I have another problem. I cannot log on to the internet on that computer. The wireless icon will not light up on the system.

---

### Post by bwang on 2009-11-28
What wireless hardware do you have?
In terminal run:
```
lspci
```
to list PCI devices
or 
```
lsusb
```
to list USB devices.

---

### Post by Spiffjiggins on 2009-11-28
I am about as ignorant as humanly possible when it comes to this stuff. I don't know what terminal means.
I figured I'd just run a cord to the computer get on that way untill I get it figured out. Figured out that I would need to download adobe flash to view certain websites. I can't even do THAT. The instructions to download flash say that when I want to download I will be prompted to select download location. It does not prompt for that. It goes directly to a little download square the almost imediately disapears. I don't know which file to download (Deb.,`.rpm, apt) and they are just sitting there in the download section. I don't know how to access them so that they are on the system. People knock Windows XP, but when I download Flash, I just hit accept to download wait for it to complete and go back to the website that said I needed the update. Is there a setting to make this that easy? Do I have to go through rediculous steps just of watch a video?

---

### Post by Spiffjiggins on 2009-11-28
[[SIZE=5][COLOR=#000000]carlee[/COLOR][/SIZE]]("http://ubuntuforums.org/member.php?u=717412"), I really would like to thank you for your help on that issue. I have dreds down to the middle of my back, and I about pulled them all out.

---

### Post by Spiffjiggins on 2009-11-28
Well went and google what a terminal is and some other website said that I need to type in some comands "Sudo update flash plugin" when I do it then prompts me to put in my password. When I attempt to do this the cursor does not move. And I hit enter and it gives me an error message. Soo...

---

### Post by Spiffjiggins on 2009-11-28
I want to smash my head thru a plateglass window!

---

### Post by Some Penguin on 2009-11-28
A terminal is simply a window or screen in which you type commands.

Nobody's going to be able to help you much until you actually identify what hardware is involved, and until you clarify what you have tried to what result.   One of the more obvious things to check is the documentation that came with the computer -- but 'lspci' and 'dmesg' are both quite useful for identifying what hardware is visible to the kernel.

---

### Post by Spiffjiggins on 2009-11-28
I've actually moved on from that by going old school and plugging it straight into the modem. I now want to install adobe flash player. I don't know how.

---

### Post by Some Penguin on 2009-11-28
Then see [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash) ...

---

### Post by DougieFresh4U on 2009-11-28
Relax
When typing password in terminal, you will not see it or any thing to indicate it was typed. Just type p-word and press enter.
for the 2 commands that were posted for you to run in terminal, no p-word is required

---

### Post by Elfy on 2009-11-28
When you use sudo it wants your password - type it in - the password will be invisible this is normal.

Just like dougie said ;)

---

### Post by Spiffjiggins on 2009-11-28
That's NOT available on my Xubuntu. THAT sucks cause that's exactly what I'm looking for.

---

### Post by Spiffjiggins on 2009-11-28
> **DougieFresh4U said:**
> Relax
When typing password in terminal, you will not see it or any thing to indicate it was typed. Just type p-word and press enter.
for the 2 commands that were posted for you to run in terminal, no p-word is required
 
I typed the password in when prompted three times and now its changed my computer name.

---

### Post by Spiffjiggins on 2009-11-28
It used to say just XXXX-laptop:-$
I typed "sudo update-flashplugin"
it then states "password for xxxx"
I typed it in and it says "sorry, try again.
I type it in again and now it says command not found.
 
 
Is there a way that I can go to website and just click to download?

---

