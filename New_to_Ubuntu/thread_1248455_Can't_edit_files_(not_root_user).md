---
title: "Can't edit files (not root user)"
date: 2009-08-24
forum: New to Ubuntu
---

### Post by John kerr on 2009-08-24
Hi there, this question might be sooo simple but as a new user i need help :-?

I have installed Ubuntu v9 on my acer one laptop, as a few things don't work correctly, i.e webcam and wireless light to show traffic, i checked about for the code to solve these issues. I found the code to enable the light for my traffic on my wireless and it asks me to change a config file (which i have found and copied the code into) it then says i dont have the rights to edit this file (need to be root user).

I am the only user on my laptop so can anyone help me give myself the root user rights or how to create a root user?!?

thanks in advance,

John (the total Novice)

---

### Post by mcduck on 2009-08-24
Ubuntu's security model has root user locked down, and instead admin user's are able to gain temporary root permissions through the use of "sudo".

You should probably read this: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by halitech on 2009-08-24
to give yourself temp root priviledges, use sudo

in the terminal
```
sudo nano /name/of/file/to/edit
```
graphically
```
gksudo gedit /name/of/file/to/edit
```

---

### Post by ibizatunes on 2009-08-24
```
sudo
```

type sudo will raise your permission to root level and you will be able to edit the files, be careful though as root permission, you can really screw up your machine

---

### Post by muteXe on 2009-08-24
You can also type:
```

sudo -i

```

to keep your current terminal session at those privaleges

---

### Post by John kerr on 2009-08-24
Can i edit the .conf file using sudo? The file is /etc/sysctl.conf.

And it asks me to add the following code in that file

dev.wifi0.ledpin=3
dev.wifi0.softled=1

Can i do this using the terminal or can i give myself Root user rights on the GUI to
change it by opening the file and editing??
Thanks John

---

### Post by halitech on 2009-08-24
GUI
```
gksudo gedit /etc/sysctl.conf
```

terminal
```
sudo nano /etc/sysctl.conf
```

either will work

---

### Post by muteXe on 2009-08-24
I believe you can open your file browser from the command line with 'gksudo nautilus' and then open the file, OR do 'sudo vim <filename>' and edit it in a terminal using vim (if you know how to use vim).


Damn, i'm too slow again :)

---

### Post by fela on 2009-08-24
To make a root password, run ```
removed
```

Make sure to enter a good password, not easily guessed. Also: when you enter the password at this prompt and also at the sudo prompt, you won't be able to see what you're typing. This is a security feature to stop people looking (better than dots), and it will recognize what you type.

EDIT: apparently you have to look somewhere else to find out how to make a root password...

---

### Post by John kerr on 2009-08-24
I sort of see now, as i said total novice but i will use the terminal and edit the file the way you suggested.

Once edited will i be allowed to save it as normal or do i use code to do that also?

John

---

### Post by fela on 2009-08-24
> **John kerr said:**
> I sort of see now, as i said total novice but i will use the terminal and edit the file the way you suggested.

Once edited will i be allowed to save it as normal or do i use code to do that also?

John

If you open up the file as root (with sudo or logged in as root), you'll be able to do whatever you like to the file, modify it, etc.

NOT RECOMMENDED: to make the file editable by you, you can run:

```
sudo chown $USER /path/to/file
```

If you do that it will be a security risk but you'll be able to edit the file without sudo.

---

### Post by halitech on 2009-08-24
> **fela said:**
> To make a root password, run ```
removed
```

Make sure to enter a good password, not easily guessed. Also: when you enter the password at this prompt and also at the sudo prompt, you won't be able to see what you're typing. This is a security feature to stop people looking (better than dots), and it will recognize what you type.

Do not suggest how to enable the root account, it is against forum and Ubuntu's policy to use it and will not be supported if you mess  your system up. Better to use Sudo or gksudo for doing admin work

---

### Post by fela on 2009-08-24
> **halitech said:**
> Do not suggest how to enable the root account, it is against forum and Ubuntu's policy to use it and will not be supported if you mess  your system up. Better to use Sudo or gksudo for doing admin work

Right...whatever you say I guess :)

---

### Post by halitech on 2009-08-24
> **fela said:**
> If you open up the file as root (with sudo or logged in as root), you'll be able to do whatever you like to the file, modify it, etc.

NOT RECOMMENDED: to make the file editable by you, you can run:

```
sudo chown $USER /path/to/file
```

If you do that it will be a security risk but you'll be able to edit the file without sudo.

why suggest doing something that's a possible security risk (and totally not needed) to make an edit to 1 file once? Just use sudo in the terminal or gksudo to get him a gui app and be done with it instead of making recommendations that could break the guys system?

---

### Post by fela on 2009-08-24
> **halitech said:**
> why suggest doing something that's a possible security risk (and totally not needed) to make an edit to 1 file once? Just use sudo in the terminal or gksudo to get him a gui app and be done with it instead of making recommendations that could break the guys system?

Because learning by trial and error is learning. I said it wasn't recommended, but knowing how to do it contributes to your knowledge of Linux and the way it works. Is that bad?

---

### Post by halitech on 2009-08-24
you are free to run your system however you want but considering the fact that the OP was brand new and admitted that, why give him steps that could potentially break his system beyond repair and require a reinstall? This isn't windows and reinstalling to fix things shouldn't be an automatic first step when things get hosed. And if its not recommended, why suggest it in the first place?

---

### Post by fela on 2009-08-24
> **halitech said:**
> you are free to run your system however you want but considering the fact that the OP was brand new and admitted that, why give him steps that could potentially break his system beyond repair and require a reinstall? This isn't windows and reinstalling to fix things shouldn't be an automatic first step when things get hosed. And if its not recommended, why suggest it in the first place?

I didn't know I was a robot. Surely people on the forum can discuss ideas no matter how potentially-harmful to their systems? We're human beings after all, and Ubuntu is Linux for human beings. You seem to be acting like this is a microsoft forum where the support guys just tell them what to do, and don't tell them other things that would do the same thing (but not as well, or better at a slightly different thing).

---

### Post by John kerr on 2009-08-24
Thanks for all the help (seems to have gotten a touch heated in here)

I will edit the file using sudo nano / and hopefully that should work ok.

thanks for the posts and very quick responses!

John

---

### Post by fela on 2009-08-24
> **John kerr said:**
> Thanks for all the help (seems to have gotten a touch heated in here)

I will edit the file using sudo nano / and hopefully that should work ok.

thanks for the posts and very quick responses!

John

Yes, sudo nano is perfect for what you want to do. Also, if you want graphical you can use gksudo gedit, your choice as ever in Linux :)

---

### Post by halitech on 2009-08-24
> **fela said:**
> I didn't know I was a robot. Surely people on the forum can discuss ideas no matter how potentially-harmful to their systems? We're human beings after all, and Ubuntu is Linux for human beings. You seem to be acting like this is a microsoft forum where the support guys just tell them what to do, and don't tell them other things that would do the same thing (but not as well, or better at a slightly different thing).

discussing things is one thing, giving a suggestion on how to do something that is potentially harmful is another. I gave 2 helpful options that would not break his system, you gave multiple potentially harmful options. I just don't see the point in giving advice thats not recommended.

---

### Post by fela on 2009-08-24
> **halitech said:**
> discussing things is one thing, giving a suggestion on how to do something that is potentially harmful is another. I gave 2 helpful options that would not break his system, you gave multiple potentially harmful options. I just don't see the point in giving advice thats not recommended.

Maybe, if it's not 'advice', as such?

Users who just follow commands blindly are also dumb users aswell. If you did that then I couldn't blame the guy who told you to rm -rf /. Dumb users is the number 1 cause of computer failure.

---

### Post by halitech on 2009-08-24
> **fela said:**
> Maybe, if it's not 'advice', as such?

Users who just follow commands blindly are also dumb users aswell. If you did that then I couldn't blame the guy who told you to rm -rf /. Dumb users is the number 1 cause of computer failure.

I agree, however, new users come here for help and they don't know the commands and they assume that those who are posting advice here know what they are doing and follow the advice, good bad or indifferent which is why I try to make sure the commands/advice I am giving is both useful and safe. When I first started I copied/pasted commands because I didn't know any better. Now I know most of the common commands but it seems there are more and more new users that have only been using Linux for a month or 2 giving potentially bad advice to other new users who don't know any better.

This is where I see a danger of new users and a fast growing user base, not enough experienced users to guide them so new users get cocky and think they know it all and they give bad advice because they don't know any better.

now, before you get ticked off, I'm not aiming this at you, just stating what I see going on here on the forum.

---

### Post by fela on 2009-08-24
> **halitech said:**
> I agree, however, new users come here for help and they don't know the commands and they assume that those who are posting advice here know what they are doing and follow the advice, good bad or indifferent which is why I try to make sure the commands/advice I am giving is both useful and safe. When I first started I copied/pasted commands because I didn't know any better. Now I know most of the common commands but it seems there are more and more new users that have only been using Linux for a month or 2 giving potentially bad advice to other new users who don't know any better.

This is where I see a danger of new users and a fast growing user base, not enough experienced users to guide them so new users get cocky and think they know it all and they give bad advice because they don't know any better.

I hope the dystopia that you're talking about is not true.

> now, before you get ticked off, I'm not aiming this at you, just stating what I see going on here on the forum.

Good job aswell, as I've been using Linux/UNIX since before I even knew about windows and know /etc like the back of my hand...

---

### Post by halitech on 2009-08-24
> **fela said:**
> I hope the dystopia that you're talking about is not true.

I wish it wasn't but just look around at some of the advice coming from users that have only been using Ubuntu for a few months...

> Good job aswell, as I've been using Linux/UNIX since before I even knew about windows and know /etc like the back of my hand...

Wish I had started out with *nix before I knew about windows but I didnt know about it till I heard about Redhat 6 but only really started using it around 3 years ago when I switched cold turkey to Ubuntu and then Debian a year ago

---

### Post by fela on 2009-08-24
> **halitech said:**
> I wish it wasn't but just look around at some of the advice coming from users that have only been using Ubuntu for a few months...

People obviously don't understand the significance and power of the *nix command line.

> Wish I had started out with *nix before I knew about windows but I didnt know about it till I heard about Redhat 6 but only really started using it around 3 years ago when I switched cold turkey to Ubuntu and then Debian a year ago

I included MacOSX in *nix, as it's UNIX. I've been using Linux (like you) for 3 years now (almost to the day O:)), and used OSX before that. I only started using windows on and off 1 year ago.

---

### Post by halitech on 2009-08-24
> **fela said:**
> People obviously don't understand the significance and power of the *nix command line.

no they don't and it's scary the way they toss commands around

> I included MacOSX in *nix, as it's UNIX. I've been using Linux (like you) for 3 years now (almost to the day O:)), and used OSX before that. I only started using windows on and off 1 year ago.

I've played a little with OSX at work but they had it locked down so there was alot I couldn't try. Mac has always had my respect for being a solid, stable system but I couldn't justify the price tag that came along with it. I had an old G3 (running OS9) for a few months but it was huge and no room to set it up so just gave it away.

---

### Post by fela on 2009-08-24
> **halitech said:**
> I've played a little with OSX at work but they had it locked down so there was alot I couldn't try. Mac has always had my respect for being a solid, stable system but I couldn't justify the price tag that came along with it. I had an old G3 (running OS9) for a few months but it was huge and no room to set it up so just gave it away.

OS9 and earlier, in my experience of it, was very unstable, especially considering it must have been customized for the hardware it was designed to run on. OSX is very stable, but not as stable as Linux, probably mostly due to more 3rd party drivers. I think the actual systems are about on par with each other stability wise.

---

### Post by halitech on 2009-08-24
> **fela said:**
> OS9 and earlier, in my experience of it, was very unstable, especially considering it must have been customized for the hardware it was designed to run on. OSX is very stable, but not as stable as Linux, probably mostly due to more 3rd party drivers. I think the actual systems are about on par with each other stability wise.

didn't do much with os9, it was being phased out when I started doing support for an internet company but I was under the understanding that the hardware and software were designed for each other in 9 and they carried that up to OSX. Now with the newer machines running on Intel platform and able to run windows, not sure what they are like (still to expensive for my blood)

---

### Post by fela on 2009-08-24
> **halitech said:**
> didn't do much with os9, it was being phased out when I started doing support for an internet company but I was under the understanding that the hardware and software were designed for each other in 9 and they carried that up to OSX. Now with the newer machines running on Intel platform and able to run windows, not sure what they are like (still to expensive for my blood)

With apple, yes the hardware is chosen with the software in mind, as it's all chosen by one company. The hardware may be standard x86 components (with EFI of course instead of BIOS), but OSX is optimized (I believe) for the hardware that they sell. For example they don't sell AMD macs do they, and getting hackintosh to work on an AMD is harder (and was impossible I think) than intel.

---

