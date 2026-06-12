---
title: "installing a secondary internal hard drive"
date: 2010-12-24
forum: New to Ubuntu
---

### Post by rburkartjo on 2010-12-24
i received a seagate(barracuda) internal 1tb hard drive for christmas. and my friend, a windows user, is going to install it for me on wed. is there anything i have to be careful about. i am going to keep my currently hd  for linux. are there any linux programs i can download first to give me the option to boot into either hd. usually i do a google search before posting on this form but i have not idea where to start./tks

---

### Post by Dark_Stang on 2010-12-24
Here is what I would do...

Unhook your current hard drive (with linux on it) and hook up the new one.
Install windows on the new hard drive.
Now hook up the old hard drive and set it as first boot device in your BIOS.
Reinstall GRUB.
When GRUB is installing it should see the drive with Windows on it and add it as an option to boot to.
When your computer boots up it will default to Linux, but if you hold Shift it will show you your boot options.

Edit: Also, you don't have to completely remove the old drive. Just disconnect it's SATA cable.

---

### Post by rburkartjo on 2010-12-24
tks for the info dark

---

### Post by rburkartjo on 2010-12-24
dark how would i reinstall grub

---

### Post by XeonBloomfield on 2010-12-24
```
sudo update-grub
```

---

### Post by amjjawad on 2010-12-24
> **rburkartjo said:**
> dark how would i reinstall grub

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

However, if your friend is going to install Windows for you, it means you just need to run:

```
sudo update-grub

```It's just like you disconnected the HDD that has Ubuntu, installed Windows in the new HDD then you re-plugged/re-connected the HDD that has Ubuntu.
Depends on your BIOS settings and what HDD will boot first, either Windows or Ubuntu will boot up.
So, you need to run update-grub so that Ubuntu can detect Windows.

Try to keep the new HDD as the 2nd HDD to boot from so that it will be sdb. So you don't need to re-install GRUB2.

---

### Post by amjjawad on 2010-12-24
> **Dark_Stang said:**
> Here is what I would do...

Unhook your current hard drive (with linux on it) and hook up the new one.
Install windows on the new hard drive.
Now hook up the old hard drive and set it as first boot device in your BIOS.
Reinstall GRUB.
When GRUB is installing it should see the drive with Windows on it and add it as an option to boot to.
When your computer boots up it will default to Linux, but if you hold Shift it will show you your boot options.

Edit: Also, you don't have to completely remove the old drive. Just disconnect it's SATA cable.

That's not entirely right. You don't need to "re-install GRUB2", you just need to do update-grub from terminal.

I've done that many times before and not a single time I had to re-install GRUB2.

---

### Post by amjjawad on 2010-12-24
[IMG]http://ubuntuforums.org/picture.php?albumid=2145&pictureid=7174[/IMG]

Example:
HDD1 is your old HDD
HDD2 is your new HDD

ALL what you need to do is:
1) Set HDD1 to be the first HDD to boot from
2) Set HDD2 to be the second HDD to boot from
3) Save and reboot
4) Login to Ubuntu
5) From Terminal run 
```
sudo update-grub

```6) Done.

---

### Post by rburkartjo on 2010-12-24
tks ya'll that is what i needed

---

### Post by Dark_Stang on 2010-12-24
> **amjjawad said:**
> That's not entirely right. You don't need to "re-install GRUB2", you just need to do update-grub from terminal.

I've done that many times before and not a single time I had to re-install GRUB2.
That's true, but saying reinstall is a little easier for other people to do. Running the following should also work.
```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

---

### Post by amjjawad on 2010-12-24
> **Dark_Stang said:**
> That's true, but saying reinstall is a little easier for other people to do. Running the following should also work.
```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

I'm sorry, I tend to disagree.
Re-installation is different than Updating.

Thank you :)

---

### Post by s1baker on 2010-12-24
I have 2 HD's mounted in my box, one with Ubuntu on it and another with XP on it. I switch from one to the other by rebooting and when the machine is rebooting, I hit the del key ( this might be diferent on different machines dependent on the Bios ) and then set the HD priority in the Bios to the HD I want to boot off of. I do this usually once or twice a day.

 As far as the installation of XP, I would only recommend first disconnecting the Ubuntu HD from the power cable and also from the data ribbon and then installing the XP on the new HD, after that, reconnecting the Ubuntu HD onto the ribbon. My luck is that if I didn't do this I probably would format my Ubunto HD by mistake and install XP on it instead of the new HD.

  That said, always unplug the power cord from the box before messing with plugging in the power and data connector into the HD's. I not only unplug the power from the box, I unplug the monitor as well ( just my cautionary self ).

---

### Post by s1baker on 2010-12-24
also, I wanted to mention, the power connector and data connector on the ribbon only go on one way, you don't want to try to put then on 180 degrees off. The power connection is shaped to where it is hard to get it on wrong, be more careful with the data connector ribbon. Look at your ribbon now on your Ubuntu HD and check which side of the ribbon the red stripe is on, this is probably the same side of the ribbon to mount the other connector in for the new HD.

---

### Post by |Eric| on 2010-12-24
i was wondering are you installing windows or installing a second hd ?

installing windows .... sacrilegious ... :P 

one good trick is this 
dd if=/dev/sdXX of=/bootfile.bin bs=512 count=1 
/dev/sdXX is referring to where grub is installed 
copy that boot file.bin  to  a usb key 
install win-blows 
put the file  in c: in your windows partition
just add the entry C:\bootfile.bin="linux rocks!!"  in boot.ini 

there you go booting linux from windows . tho for that to work your linux harddrive has to be same position ( ie primary master or somthing) 
or in another words geometry needs to stay the same for your Linux (Linux needs to perceive as it would not have moved)

---

### Post by rburkartjo on 2011-01-02
amj followed your advise worked like a charm/tks

---

### Post by amjjawad on 2011-01-03
> **rburkartjo said:**
> amj followed your advise worked like a charm/tks

You most welcome.
Don't forget to mark this thread as "Solved" ;)

---

