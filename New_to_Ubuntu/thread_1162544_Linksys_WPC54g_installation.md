---
title: "Linksys WPC54g installation"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by don_diego on 2009-05-17
Am trying to get Jaunty to recognize this pcmcia card on my laptop. I have read as many threads as I could find on this subject, have installed ndiswrapper, have located the card's driver (lsbcmnds.inf) and now - being the nooby that I am - need to know where I should put it so ndiswrapper can locate and install it.

TIA

---

### Post by Joeb454 on 2009-05-17
Perhaps this post will help :)

[http://ubuntuforums.org/showpost.php?p=113584&postcount=7](http://ubuntuforums.org/showpost.php?p=113584&postcount=7)

It seems to have worked for others using the same card

---

### Post by miwaypet on 2009-05-17
You need to locate the .inf file first. If it is in a seperate folder on the driver cd for your wireless then move it to the main folder. Copy that folder to desktop.

Open terminal: 

```
cd Desktop/<wireless folder>
```

```
sudo ndiswrapper -i ./<your wireless.inf>
```

```
sudo modprobe -r ndiswrapper
```

```
sudo modprobe ndiswrapper
```

```
sudo bash -c 'echo "ndiswrapper" >> /etc/modprobe'
```

Reboot

---

### Post by don_diego on 2009-05-17
> **miwaypet said:**
> You need to locate the .inf file first. If it is in a seperate folder on the driver cd for your wireless then move it to the main folder. Copy that folder to desktop.

Did that (foldername is 2KXP) and opened Terminal
```
cd Desktop/2KXP
```This resulted in an error:
```
bash: cd Desktop/2KXP: No such file or directory
```I figured there was no sense continuing with the rest of the commands you provided until this problem is resolved, my question is what can I do about it?

I would appreciate any further input/help because I do want this card to work so I can have webacccess from this laptop. 

Thank you.

---

### Post by don_diego on 2009-05-18
Well, leave it up to a complete dummy (me), of course "cd" works if I capitalize Desktop. 

Now I was able to perform the rest of the steps provided by miwaypet, they worked and the power LED on my wireless card is on - yet there is still no connection to the Internet. 

What else could/should I try?

---

