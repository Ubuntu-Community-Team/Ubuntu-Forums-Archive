---
title: "No desktop from Lubuntu live cd"
date: 2011-07-23
forum: New to Ubuntu
---

### Post by garagestmarien on 2011-07-23
Hi all,

I have downloaded Lubuntu and burnt to disk. The disk was checked and okay.
When I run the live cd to try Lubuntu, all I end up with is the terminal command line.
I have tried ctrl-alt-f7 and all I get is a blank screen. ctrl-alt-f2 gets me back to terminal.
How do I get the desktop up, as I would love to try this distro and I want to see it working before I do any install.

John

---

### Post by westie457 on 2011-07-23
> **garagestmarien said:**
> Hi all,

I have downloaded Lubuntu and burnt to disk. The disk was checked and okay.
When I run the live cd to try Lubuntu, all I end up with is the terminal command line.
I have tried ctrl-alt-f7 and all I get is a blank screen. ctrl-alt-f2 gets me back to terminal.
How do I get the desktop up, as I would love to try this distro and I want to see it working before I do any install.

John

Did you download lubuntu from [http://lubuntu.net/](http://lubuntu.net/) or from somewhere else?

---

### Post by whatthefunk on 2011-07-23
What are the specs of the machine youre running it on?

---

### Post by Rex Bouwense on 2011-07-23
I know that you said that you checked the CD and it was OK, but did you check the md5sum and burn the ISO at the lowest possible speed.  I just downloaded a Lubuntu ISO and made a bootable flash drive and it works without error.
See this site for info:
[https://help.ubuntu.com/community/Lubuntu/Documentation](https://help.ubuntu.com/community/Lubuntu/Documentation)

---

### Post by garagestmarien on 2011-07-23
Rex Bouwense
es the md5 check was okay

whatthefunk
All the specs are in my signature

westie457
Yes I downloaded from Lubuntu.net

I am going to re-download from [http://lubuntu.lafibre.info/11.04/](http://lubuntu.lafibre.info/11.04/) via torrent to see if this is any better.
I'll post once this has been done.
It's strange, because I have never had this problem before on any live distros.

---

### Post by Rex Bouwense on 2011-07-23
I know that things happens, but I have downloaded dozens of ISOs and have never had that happen.

---

### Post by kansasnoob on 2011-07-23
I've had some trouble with the Lubuntu 11.04 live CD. When you get to the terminal prompt try:

```
sudo service lxdm start
```

Or:

```
sudo /etc/init.d/lxdm restart
```

Oh, forgot to mention, you'll then need to login as ubuntu (as I recall, but it could be lubuntu) and just leave the password blank and press enter.

---

### Post by garagestmarien on 2011-07-23
Solved, but I don't know how :confused:
Downloaded the new iso which checked out exactly the same as the previous one.
Run live cd. Terminal again. As I forgot the sudo instructions from kansasnoob I shut down and booted into my other distro to get them.
Then I run the live cd again ready to try the instruction and it booted into the desktop. 
I have no idea what made that happen but enough to say that I am really pleased with it and will be doing an install later.

Even so I would like to know how this happened.
Thanks to everyone for the replies.

John

---

### Post by garagestmarien on 2011-07-23
Update.

Have installed and everything has gone well.
I am impressed at the speed of this thing.
Much cheaper than buying a more powerful computer!!
:popcorn:

---

### Post by amjjawad on 2011-07-23
> **garagestmarien said:**
> Hi all,

I have downloaded Lubuntu and burnt to disk. The disk was checked and okay.
When I run the live cd to try Lubuntu, all I end up with is the terminal command line.
I have tried ctrl-alt-f7 and all I get is a blank screen. ctrl-alt-f2 gets me back to terminal.
How do I get the desktop up, as I would love to try this distro and I want to see it working before I do any install.

John

Without reading the other posts here(sorry about that, I'm in hurry), I have faced the same issue.

Long story short. Instead of choosing "TRY", choose "Install". On the first step, click "Close" or "Exit" - can't remember which one exactly?

After that, you'll see the desktop.

For some reason, the TRY Option doesn't work in Lubuntu 11.04.

Good luck!

P.S.
The above process will make you able to TRY Ubuntu without installation. If you managed to install it, then ignore my post ;)

---

### Post by ChrisOfBristol on 2011-08-19
@kansansnoob Thanks for the tip!

Lubuntu 11.04 - trying without installing.
[LIST]
[*]It got stuck at the terminal screen on my PC. Adding 'nomodeset' to the startup options fixed that.
[*]It also got stuck at the terminal screen on my laptop. Typing 'sudo service lxdm start' at the terminal screen fixed that.
[*]I didn't want to install it on my PC so I haven't tried that, but it installs on my laptop without any problems.
[/LIST]

---

