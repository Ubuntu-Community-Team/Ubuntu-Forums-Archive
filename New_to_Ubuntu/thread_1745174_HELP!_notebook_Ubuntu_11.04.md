---
title: "HELP! notebook Ubuntu 11.04?"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by Missi0n on 2011-04-30
Hi, im going to apologise in advanced for these probably very simple questions

I have just successfully installed Ubuntu 11.04 - the Natty Narwhal on a small netbook, when on the Ubuntu site a few days ago i noticed they had a netbook edition.. where did that go?

i read something saying that 11.04 had something to do with "unity"? i was guessing that meant that the desktop edition and notebook edition of Ubuntu had some how been combined seeing as there was no longer a netbook edition available to download?

**How do i optimise 11.04 to work on a low powered netbook?**

thank you in advance :confused:

---

### Post by Ken UK on 2011-04-30
Forget Netbook and Desktop edition. Netbook edition was Desktop edition with Unity instead of normal gnome, nothing much more than that.

For 11.04 they combined them because Unity is the new interface for all. Unity is suppose to be a better option for small screens because its space efficient, hence optimised.

As for optimisation Im not sure other than not enabling any effects, how does the default setup run?

---

### Post by Missi0n on 2011-04-30
Okay - how come there's no bar on the side? or have they removed that in this new version?

and it runs okay considering the spec of this machine, it's an old single core centrino processor with 500mb ram. When it first booted it suggested that the computer didn't have a high enough and i should change some options, but i couldn't find where to change anything - and now i cant remember what it said

---

### Post by Solstice Bahai on 2011-04-30
Probably like yourself,(I don't want to assume) I'm a bit of a newbie, But I am definetly moving to 11.04, from Netbook Edition of Meerkat, which is currently the ONLY OS on my Samsung N150.
If Unity does away with the need for a "netbook" edition ,... then that is all the better.
Trust the guys here, they rock when it comes to helping out
All the best, and good luck to you:D

---

### Post by Missi0n on 2011-05-01
thank you Solstice Bahai, i can any one else help me?

---

### Post by sffvba[e0rt on 2011-05-01
> **Missi0n said:**
> thank you Solstice Bahai, i can any one else help me?

Possible that Unity has gone to a fallback mode due to your netbook being unable to handle it.

There is a so called "2D" version that a bit less flashy and uses less resources...

I am on a Windows machine currently so can't verify the command in terminal but from Google you can try:
 [B][FONT=monospace]
[/FONT]sudo add-apt-repository ppa:unity-2d-team/unity-2d-daily[/B] [B][FONT=monospace]
[/FONT]sudo apt-get update
sudo apt-get install unity-2d
[/B]


404

PS - From the log-in screen you can select what session you would like at the bottom of the screen... You can try selecting "Ubuntu" and not "Ubuntu Classic" I can't remember the exact phrasing now and see if Unity works before installing 2D above

---

### Post by Missi0n on 2011-05-02
thankyou not found, i logged out and found out it was already running "Ubuntu" and not "Ubuntu Classic" so instead im installing the 2d version of Unity, your instructions were very helpfull and after googling them i found this which filled me in 

[http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1540-top-things-to-do-after-installing-ubuntu-1104-natty-narwhal](http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1540-top-things-to-do-after-installing-ubuntu-1104-natty-narwhal)

---

### Post by Missi0n on 2011-05-02
however i have decided to go with xubuntu, Ubuntu 11.04 ran but not as fast as i would preferable like it to

---

### Post by sffvba[e0rt on 2011-05-03
> **Missi0n said:**
> however i have decided to go with xubuntu, Ubuntu 11.04 ran but not as fast as i would preferable like it to

Oh cool!  Glad you got it sorted... as for Xubuntu, that is part of what makes GNU/Linux so awesome, choice ):P


404

---

### Post by Missi0n on 2011-05-04
hah, thanks

i've now installed Xubuntu 11.04 on my notebook... and having major problems :/

the live CD i made boots fine, and i've tried fresh installing 3 times but
every time i **boot the screen just stays black and doesnt boot** i've tried searching for the same problems, people have had them, no one has solved it though :/

---

### Post by sffvba[e0rt on 2011-05-05
Sounds like a troublesome netbook you have there... I hope you get the issue resolved!


404

---

