---
title: "Help needed please, this problem is so annoying."
date: 2011-08-27
forum: New to Ubuntu
---

### Post by johnb1976 on 2011-08-27
Hi i am hoping someone can help me, i was using windows 7 and decided to partition my hard-drive so i could use the wubi install of ubuntu 11.04. All was well at first i could dual boot with the windows loader then grub loader with no problems, i have not updated anything as far as i know anyway. The issue i have, that i can't find any help is now when i first boot my pc up i can 70% of the time choose the os i wish and it will load up fine, but the other 30% of time the selection will be unresponsive as in my keyboard does not work, so i just let it boot into windows 7(as this is my default boot) and miss out on choosing ubuntu as the keyboard will not move up and down to select the os. If i am lucky and get to choose what os i want, then it will boot just fine, But! on restart of the system everytime the selection process wont let me choose the os i wish, therefore just booting into windows 7. I don't have a usb legacy option in bios(ive read this can cause unresponsive keyboards) and the 4 usb options i have are enabled. My keyboard is a usb keyboard. i dont have an old keyboard to try. Also i have found a Temporary solution to this problem but it surely cant be good for the pc, if i cant select the os, i will shutdown the pc, unplug it, then hold the power button to discharge any left power in the pc. Then when i start the pc i am gauranteed to be able to choose what os i wish with out any problems at all, but on restart same thing, i can't choose os. It's really annoying and if anyone as any ideas what could be causing this, then i would like to hear what you think, Thank's.

---

### Post by Frogs Hair on 2011-08-27
Hi ,

Wubi does not require you to create a partition , it installs in a folder/partition inside Windows and will offer a 30 Gb maximum size . Do you have a traditional dual boot with Ubuntu on its own partition or an Wubi installation inside of Windows ?

---

### Post by johnb1976 on 2011-08-27
Hi tnx for the reply, I originally was going to apply ubuntu to a separate partition but had problems. So I formatted my harddrive and installed win 7, I then created a new partition in my c drive and called it z drive and gave it 40gb. I then downloaded the windows installer version of wubi 11.04. I ran the wubi installer through windows 7, which would only start the wubi app if I disabled my usb ports, strange I know. It then
which asked me at the top left of the installer
were I wanted to install it, so I choose the created partition drive z. And the installation went fine.On boot up I get the windows boot manager and then when I choose ubuntu I get the purple grub bootloader screen. And it boots fine, my problem starts when I need to restart the system my main concern is why the need for the power drain to be able to choose the os.

---

### Post by grahammechanical on 2011-08-27
Hi

1) You might have a faulty keyboard. Keep that in mind.

2) Try unplugging the keyboard and plugging it back in.

3) If it is a full size keyboard switch off number lock and use the 2 key to go down and the 8 key to go up on the number pad of the keyboard.

4) Carefully take the keyboard apart and clear out all the dust and stuff that has fallen into it.

5) When you are in Ubuntu, install Grub Customizer and use it to set Ubuntu as the default choice and then forget about Windows.

[http://ubuntuforums.org/showthread.php?p=10340183]("http://ubuntuforums.org/showthread.php?p=10340183")

Regards and I hope that something works for you.

P.S. Do the up and down arrow keys work when you are selecting from the Windows boot loader and when you are moving around the BIOS settings utility? Failure here could indicate faulty keys on the keyboard.

---

### Post by johnb1976 on 2011-08-27
Yeah my first thought was the keyboard so I went out and bought a new keyboard (and installed the drivers for it on both os) lol, but still the same problem, I can always get into bios and move up and down no problem but as soon as I leave bios I can't move up and down on the windows boot loader. I have tried all the keyboard tricks you mention with same problem. The only thing I haven't tried is the grub customizer you mention, maybe your right and the problem is the windows loader so if I can disable that then hopefully it will work again on reboot. Thanks for the information. I will try this as soon as I'm home.

---

### Post by blade4 on 2011-08-27
Hi , just going on a whim here : do you also have to press enter twice to reach ubuntu ? By that I mean does your boot first show a choice between win7 and ubuntu and then between the different ubuntu kernels ? ( Its like that for me on lucid ) . If so , and if your boot hangs on both screens then skip this next para , if not then read on :    


The problem might be solved if you just change the boot order and assign ubuntu as your primary OS ( easiest way to do this is to use msconfig in windows and change the order - that's the way I did it .) The advantage is that on the kernel selection screen , it also shows the option of booting into windows , so you still have a choice . 

The other reason , and I may be totally wrong here , could be the partition you made . I'm assuming your windows is also in C drive and that could be the cause . If you don't have too much data on your ubuntu , you could try reinstalling it on a different partition .

---

### Post by johnb1976 on 2011-08-27
> **grahammechanical said:**
> Hi

1) You might have a faulty keyboard. Keep that in mind.

2) Try unplugging the keyboard and plugging it back in.

3) If it is a full size keyboard switch off number lock and use the 2 key to go down and the 8 key to go up on the number pad of the keyboard.

4) Carefully take the keyboard apart and clear out all the dust and stuff that has fallen into it.

5) When you are in Ubuntu, install Grub Customizer and use it to set Ubuntu as the default choice and then forget about Windows.

[http://ubuntuforums.org/showthread.php?p=10340183]("http://ubuntuforums.org/showthread.php?p=10340183")

Regards and I hope that something works for you.

P.S. Do the up and down arrow keys work when you are selecting from the Windows boot loader and when you are moving around the BIOS settings utility? Failure here could indicate faulty keys on the keyboard.

Hi grahammechanical

Just a quick question, as I'm using the windows boot loader as I installed using wubi, if I use grub customizer? will it stop me booting into windows 7? Sorry to be a pain.

---

### Post by gnometorule on 2011-08-27
When I first used ubuntu, I had it Wubi installed. It worked fine out of the box.. As several others have guessed above, I have a strong hunch that the problem is you first creating a different drive and saving it there. The main appeal of Wubi is to not have to worry about Grub(2), partitioning and such - why else even use it? It's meant to broaden Linux' appeal to people who loath meddling with their partitioning. You are meant to download it wherever you run Windows. It's just another program from W7's view. Booting is adjusted by Wubi to give you the option of what seems like 2 OS, but in a way, you're really staying in Windows world. Before anything else, I suggest you uninstall what you have currently installed (should be easy from W7), then reinstall it in the drive you have your W7 OS, and see what happens.

Keep in mind too that you lose some of the appeal of Ubuntu running it as Wubi. As it's integrated into W7, you are as security protected as you are under W7, even if you seem to be in safe Ubuntu world.

---

### Post by johnb1976 on 2011-08-27
> **blade4 said:**
> Hi , just going on a whim here : do you also have to press enter twice to reach ubuntu ? By that I mean does your boot first show a choice between win7 and ubuntu and then between the different ubuntu kernels ? ( Its like that for me on lucid ) . If so , and if your boot hangs on both screens then skip this next para , if not then read on :    


The problem might be solved if you just change the boot order and assign ubuntu as your primary OS ( easiest way to do this is to use msconfig in windows and change the order - that's the way I did it .) The advantage is that on the kernel selection screen , it also shows the option of booting into windows , so you still have a choice . 

The other reason , and I may be totally wrong here , could be the partition you made . I'm assuming your windows is also in C drive and that could be the cause . If you don't have too much data on your ubuntu , you could try reinstalling it on a different partition .

Hi blade, you from sheffield by any chance? But serious back to this, I don't have to press enter twice, sometimes I'm lucky on my first boot and I'm able to choose which os I wish and then when I choose ubuntu I get the ubuntu (grub loader screen -purple) and selecting any of them boots fine. My problem is if I have to restart for an update or to change the os, it just don't let me select, but still boots into my default os, I have tried to change boot order in windows and then when I reset it is locked as in I can't select, then the countdown boots ubuntu and when I get to the grub boot selecter tht also doesent let me choose any of the selections, so countdown carrys on and loads ubuntu. The concerning thing is If I turn on my pc and it won't let me select I boot up win 7 and then shutdown and unplug the pc then hold power button and then when I resume I can select either just fine (but why) I have the latest bios update and part of me thinks it could be the battery, but I have no symptons of battery failure. I didn't place ubuntu in the same place as windows I created a seperate partition and made it z drive as told to do on several wubi install guides. Thanks for your reply.

---

### Post by johnb1976 on 2011-08-27
> **gnometorule said:**
> When I first used ubuntu, I had it Wubi installed. It worked fine out of the box.. As several others have guessed above, I have a strong hunch that the problem is you first creating a different drive and saving it there. The main appeal of Wubi is to not have to worry about Grub(2), partitioning and such - why else even use it? It's meant to broaden Linux' appeal to people who loath meddling with their partitioning. You are meant to download it wherever you run Windows. It's just another program from W7's view. Booting is adjusted by Wubi to give you the option of what seems like 2 OS, but in a way, you're really staying in Windows world. Before anything else, I suggest you uninstall what you have currently installed (should be easy from W7), then reinstall it in the drive you have your W7 OS, and see what happens.

Keep in mind too that you lose some of the appeal of Ubuntu running it as Wubi. As it's integrated into W7, you are as security protected as you are under W7, even if you seem to be in safe Ubuntu world.

A lot of posts are very contriversal on installation of wubi and as a newbie then, I just thought creating a new partition was the best thing to do, Also with wubi asking were I wanted to install it, I thought it was too good to be true lol. I guess I will try the grub customizer later and then if no joy, I will just install it along side windows and I will let you know tnx.

---

### Post by blade4 on 2011-08-27
There is one other option : try changing the boot waiting time from either grub or msconfig . I think the default is 10 seconds - try changing that to any other value . I don't know if this can set things right for you but it definitely won't hurt to try .

---

### Post by johnb1976 on 2011-08-27
> **blade4 said:**
> There is one other option : try changing the boot waiting time from either grub or msconfig . I think the default is 10 seconds - try changing that to any other value . I don't know if this can set things right for you but it definitely won't hurt to try .

Changed it previously to 15 seconds, still same but tnx anyway.

---

### Post by bcbc on 2011-08-27
The menu you are having an issue with is the windows boot manager, not grub. So using the grub customizer won't help. If you want to boot Ubuntu all the time, install it direct, not Wubi.

Most likely this is an issue between you keyboard and bios.

---

### Post by johnb1976 on 2011-08-27
hi guys just an update, ive removed ubuntu and the partition and restored my win boot up to remove the windows loader, but i feel i have removed ubuntu un-necessary as it seems all along that some of you may have been right, i cant access the bios as in the del on my keyboard is unresponsive "sometimes" but not all the time. Doing the cmos reset or unpluging and holding the power button lets me enter bios. Any ideas guys as i really need to sort this so i can reinstall ubuntu once more. 

ps: im 100% positive my keyboard was working fine before i replaced it with a new one, i do remember plugging the new one in on startup before actually installing the drivers for it, dont know if this as done anything out of the ordinary. Thanks

---

### Post by johnb1976 on 2011-08-27
Guy thanks for all the tips, I think I've sorted it, I have successfully been able to choose my os from the boot screen, I didn't know in my bios if I pressed alt and f1 it unlocked more settings, so I disabled the num lock and it seems to have done the trick, I did some research on the microsoft keyboard curve 2000 and it seems it alters your bios, so will see how it goes.

---

### Post by johnb1976 on 2011-08-28
> **johnb1976 said:**
> Guy thanks for all the tips, I think I've sorted it, I have successfully been able to choose my os from the boot screen, I didn't know in my bios if I pressed alt and f1 it unlocked more settings, so I disabled the num lock and it seems to have done the trick, I did some research on the microsoft keyboard curve 2000 and it seems it alters your bios, so will see how it goes.

Ah geez same problem as come back with a 3rd keyboard tried and still not able to select unless I drain the power?

---

