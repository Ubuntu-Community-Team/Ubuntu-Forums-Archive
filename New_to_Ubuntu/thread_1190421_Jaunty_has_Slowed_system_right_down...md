---
title: "Jaunty has Slowed system right down.."
date: 2009-06-17
forum: New to Ubuntu
---

### Post by FrancesL on 2009-06-17
Hi all,
I decided it was time to rid myself of a obese and getter larger everyday, WINXP on Hp pavilion 504a Desktop.(specs in signature)
Unfortunately after installing 8.04 off CD, using manual partition, using whole of the 30GB for Ubuntu, PC ran ok, then I used synaptic for the Upgrades through to Jaunty! now the PC is as slow as it was under WINXP.
Obviously I have missed something, although I carefully followed prompts, or need a driver/package or a something I cant ID. 
Can a younger/smarter brain than mine point me at a solution?
As a full-time at home Carer of disabled husband I fill my empty hours, browsing, I do internet banking, and I use Club Pogo and Face book as a way to pay games/interact with family and friends, Skype, and Pidgin. Email of course. Thats about my full list of expectations. 
Help please, allways appreciated.

---

### Post by 123456789123456789123456 on 2009-06-17
The only suggested way to upgrade 8.04 to 9.04 is to go to update manager, upgrade to 8.10, then from 8.10 to 9.04, as just updating the packages can cause problems.
Unfortiantly, there is no way I know of to actually get the problem fixed, if there were, it would probably take an extreamly long time to figure out.  I'm sure consists of uninstalling, and reinstalling packages, which could also cause system crashes, and messups.  I suggest that on the 30gb partiton you have set up, backup your personal data, use a 9.04 live cd, just tell the partitioner, to remove the current Ubuntu installation, and install in the same 30gb partition.  Its first option would be to resize the disk, creating another partition with 9.04, leaving 9.04, and the last partition, I believe the second option is the one you want, as the third will remove all partitions on disk, and use the entire 80gb for ubuntu.  This should fix the problem, and it should run very fast, expecially on 1.5gb of ram.

---

### Post by SOULRiDER on 2009-06-17
Your machine is a bit older but i believe it should be able to run Ubuntu with no problems at all. I have a few questions to ask and suggestions to make.

1- Did you upgrade from Hardy to Jaunty? If so, was it better in Hardy?
2- Is everything slow or some things like desktop effects? You could try disabeling them in the appearence section in preferences and see if performance improves.
3- Use a program like htop and try to monitor CPU and Swap use.
4- Are you using CPU frequency scaling? If so, try disableing it or setting it to Performance (im not in a linux machine now and cant remember how to do this from the top of my head but I believe the CPU monitor applet can be useful).

This is all i can think of for now.

---

### Post by QIII on 2009-06-17
What type of graphics card do you have?

---

### Post by Hobgoblin on 2009-06-17
Firstly upgrading can cause problems, you would be better doing a fresh install of 9.04

But I'm guessing you have an Intel video chipset, if so you may be better sticking with 8.10

---

### Post by QIII on 2009-06-17
Jaunty + Intel graphics = No Joy.

But there are work arounds and suggestions.

---

### Post by FrancesL on 2009-06-18
[QUOTE=123456789123456789123456;7475720]The only suggested way to upgrade 8.04 to 9.04 is to go to update manager, upgrade to 8.10, then from 8.10 to 9.04, as just updating the packages can cause problems.

Thank you for response..yes this is EXACTELY the process I used.

---

### Post by FrancesL on 2009-06-18
[QUOTE=SOULRiDER;7475733]Your machine is a bit older but i believe it should be able to run Ubuntu with no problems at all. I have a few questions to ask and suggestions to make.

1- Did you upgrade from Hardy to Jaunty? If so, was it better in Hardy?[COLOR="Red"]YES to Both[/COLOR]
2- Is everything slow or some things like desktop effects? You could try disabeling them in the appearence section in preferences and see if performance improves. [COLOR="Red"]Have no desktop effects enabled[/COLOR]
3- Use a program like htop and try to monitor CPU and Swap use.[COLOR="Red"]Will try that[/COLOR]
4- Are you using CPU frequency scaling? If so, try disableing it or setting it to Performance (im not in a linux machine now and cant remember how to do this from the top of my head but I believe the CPU monitor applet can be useful).[COLOR="Red"]No idea what this is..[/COLOR]

Thank your for your reply



OPPPS I dont think I have a SWAP PARTITION..there is likely to be the problem right there

---

### Post by FrancesL on 2009-06-18
> **QIII said:**
> What type of graphics card do you have?

Intel?..I can't truely remember...is there a way to check?

---

### Post by FrancesL on 2009-06-18
SWAP is working fine..checked that with system monitor ..so not that

---

### Post by FrancesL on 2009-06-18
> **QIII said:**
> Jaunty + Intel graphics = No Joy.

But there are work arounds and suggestions.

thats sad...so I may be best to do a clean install of Hardy! oh well..unless I can get a new graphics card..hmmm will have to price that idea..
Thanks for help

---

### Post by FrancesL on 2009-06-18
So would final suggestion be to do a clean install and stick with Hardy? 
Thanks all, you have been very kind.

---

### Post by SOULRiDER on 2009-06-18
Intel graphic cards can have issues (luckily i dont have any on my laptop which has intel graphics). There are some workarounds to these problems though, id suggest you try them before reinstalling.

Check this out, it may solve your problem. I wish you the bets of luck, and if all fails you can just go back to hardy. (and remember to make a separate /home partition!)
[http://www.ubuntu.com/getubuntu/releasenotes/904#Performance%20regressions%20on%20Intel%20graphics%20cards](http://www.ubuntu.com/getubuntu/releasenotes/904#Performance%20regressions%20on%20Intel%20graphics%20cards)

---

### Post by FrancesL on 2009-06-19
did a clean install of Hardy.and after it downloaded 633 packages..it is now giving me an error message that it cant install any updates until I remove broken packages. when I check in synaptic for these, there is none appearing. I am bemused. Have added a screen shot.

---

