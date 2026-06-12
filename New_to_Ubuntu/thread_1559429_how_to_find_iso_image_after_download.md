---
title: "how to find iso image after download"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by salima on 2010-08-23
after creating the dvd i vaguely remember seeing the iso file listed twice...i deleted one. now i cant find the iso image anywhere and i want to make a usb stick from it. when i bring up brasero it still shows two items for that file with the same name but if i click on either of them i get the same error that the file is gone.

the file is not in the trash.

is it really gone?

---

### Post by LowSky on 2010-08-23
Is anything ever really gone?
try this command from a terminal

```
find / -name *.iso
```

---

### Post by salima on 2010-08-24
> **LowSky said:**
> Is anything ever really gone?
try this command from a terminal

```
find / -name *.iso
```

i am pretty sure of the original name of the file, so this is what i typed:
  	 	 	 	 	 	   Find / -10.04-desktop-i386*.iso
and got 'command not found'
then i retyped without the capital 'F' and got 'unknown predicate'


i typed this beginning from the $ prompt, is that correct?


sorry, i am very new at this. i need 'instructions for dummies'...

---

### Post by L Campbell on 2010-08-24
> **salima said:**
> after creating the dvd i vaguely remember seeing the iso file listed twice...i deleted one. now i cant find the iso image anywhere and i want to make a usb stick from it. when i bring up brasero it still shows two items for that file with the same name but if i click on either of them i get the same error that the file is gone.

the file is not in the trash.

is it really gone?

I'm not trying to be a wise guy here but did you look in 'Download'?

I wasted some time once, looking for something I had downloaded until I happened to look in Download.

---

### Post by silverglade00 on 2010-08-24
You need to type that command exactly without changing anything. Copy and paste it into the Terminal.

---

### Post by anaconda on 2010-08-24
> **salima said:**
> i am pretty sure of the original name of the file, so this is what i typed:
  	 	 	 	 	 	   Find / -10.04-desktop-i386*.iso
and got 'command not found'
then i retyped without the capital 'F' and got 'unknown predicate'


i typed this beginning from the $ prompt, is that correct?


sorry, i am very new at this. i need 'instructions for dummies'...

You entered a wrong command. it should have been something like:
find / -name 10.04-desktop-i386.iso

so no star if you know the filename

---

### Post by salima on 2010-08-25
thanks for the answers everyone-
actually i did look in download, the download helper file, and the brasero files but no luck.

if i enter either of those commands above now i am getting 'permission denied' and various gibberish.

should i be doing this from root?

---

### Post by ks07 on 2010-08-25
You can run the find command as root so that the command can search in folders where you don't normally have read access. However, I highly doubt you would have downloaded the .iso to one of these system folders. :p No harm in trying though!

```
sudo find / -name *.iso
```

---

### Post by fancypiper on 2010-08-25
There is also the locate command which can find a file anywhere on the computer:

locate *.iso

AFAIK, all bash commands are in lower case unless they are aliased to a command with capital letters.

---

### Post by salima on 2010-08-25
thanks anyway, but i think it is really gone. none of this works for me.

i will have to go about it another way.

---

### Post by fancypiper on 2010-08-25
You could try making an ISO with your DVD.  If you boot the live DVD, I think one of the programs is one to make a bootable usb stick.

Or, you can generate an ISO from a CD/DVD:
cd /path/to/isostorage
dd if=/dev/cdrom of=foo.iso
dd if=/dev/hdd of=foo.iso

---

### Post by LiquidMeson on 2010-08-25
or alt+f2 brasero

---

### Post by salima on 2010-08-26
that was the idea if i could find the iso image, to create a usb stick...

the actual problem is i cant mount the dvd-i was hoping for a faster fix. i started a new thread on that issue. 

also i cant do any upgrades through the internet because i have a superslow connection. i had to mmdownload the iso file by leaving the computer run all night (power cuts during the day in india) and pausing the download each night...took me four nights. that is why i am trying to find it. i wouldnt have intentionally deleted it until i knew the upgrade was in place and the cd was ok. i guess i did it unconsciously...


Quote LiquidMeson
"or alt+f2 brasero" 	

not sure ii understand. you mean open brasero and do alt+f2 to locate the image in brasero? because the image is listed there but when i click on it it says it doesnt exist.

i think it is really gone and probably i should close the thread if anyone can explain to me how to do that...? do i contact a mod? consider it solved?

---

### Post by Col.Krumpet on 2010-08-26
> **salima said:**
> thanks for the answers everyone-
actually i did look in download, the download helper file, and the brasero files but no luck.

if i enter either of those commands above now i am getting 'permission denied' and various gibberish.

should i be doing this from root?

Yes. This is just me but I tend to make it common practice to sign in as root every time I enter the Terminal. This may be a bad practice but it ensures that if something comes up that I need root access to take care of I'm already set :D

---

### Post by wojox on 2010-08-26
> **Col.Krumpet said:**
> Yes. This is just me but I tend to make it common practice to sign in as root every time I enter the Terminal. This may be a bad practice but it ensures that if I something comes up that I need root access to take care of I'm already set :D

If you need root access just use **sudo**.

---

### Post by salima on 2010-08-28
> **fancypiper said:**
> You could try making an ISO with your DVD.  If you boot the live DVD, I think one of the programs is one to make a bootable usb stick.

Or, you can generate an ISO from a CD/DVD:
cd /path/to/isostorage
dd if=/dev/cdrom of=foo.iso
dd if=/dev/hdd of=foo.iso

thanks-
i was able to make an iso image from the cd and create a pen usb boot stick but it also didnt work, so now i have to go back to trying to solve either of those two issues.

i am marking this thread solved, and the new thread for the cd is   called Live CD Won't Mount........if that isnt solved reasonably soon i will start a new thread on the usb issue...

---

### Post by johnlvs2run on 2012-07-27
> **LowSky said:**
> Is anything ever really gone?
try this command from a terminal

```
find / -name *.iso
```

Thanks very much.  You helped me to find the iso files in /tmp.

I'm having some trouble moving them though.  

```
mv /tmp/Fedora-17-i686-Live-LXDE.iso /home/john/Desktop
```

I got it!  Thanks very much.

---

### Post by coffeecat on 2012-07-27
Old thread closed.

---

