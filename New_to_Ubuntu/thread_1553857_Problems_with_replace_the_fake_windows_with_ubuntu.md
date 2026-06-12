---
title: "Problems with replace the fake windows with ubuntu"
date: 2010-08-15
forum: New to Ubuntu
---

### Post by danielm316 on 2010-08-15
Helo ladies and gentlemen of Ubuntu forum

I have a customized computer without cd player or dvd player.

I have an 32 inch LCD screen and I wanted a cheap CPU, this one has 1 ghz procesor AMD, 1 giga ram, 40 gigas hard disk.
6 usb ports. 

The windows (ugh) is an ilegal copy. Aparently there is a CD of the mother board, I dont know if that is what I need, it would be a shame because there is no cd viewer.

Oh, and the motherboard is a foxconn M61PMV. The method that I am using is the usb drive, but there is something wrong here. I cant even install the windows version of linux.
I am adding an image of the error mesage on the screen.

Well, I cant install ubuntu linux in my computer. That is frustrating.

Please help me. I want to have Ubuntu, but there seems to be no way.

Thank you in advance

---

### Post by danielm316 on 2010-08-15
umm the image is not very clear, but it says:

Ocurrió un error

Permision denied

para más información vea el archivo del registro
c:\windows\temp\wubi-10.04-rev189.log.

---

### Post by admiralspark on 2010-08-15
Well, the quick and easy answer is this: your permissions are set up so that you need to be in the Administrator account to install Ubuntu. This happens alot. 

As for your situation, I do not recommend continuing with the Wubi install (Ubuntu inside windows). Since you've come on a public forum and admitted to having a less-than-legit copy of windows, I'd install Ubuntu over Windows completely. There are about 4 million threads and websites telling how to do this, but it's all pretty straightforward. 

First: How are you installing it? From a USB stick? If not, I recommend you install it to a USB (use the free program "unetbootin"), then plug it into your computer and boot from the USB. This will boot into a live, working copy of Ubuntu where you can try it out and most importantly _make sure everything works_. If it's all good to go (probably will be), you can then click the "install Ubuntu" icon on the desktop and install it from there, and make sure to select the "install Ubuntu on complete harddrive" option when it shows up. Otherwise you'll still have windows, and you can't do that ;)

If you need a step-by-step, post here and I or someone will find you one.

---

### Post by danielm316 on 2010-08-15
Thank you admiralspark for your answer.

Now let me tell you two things.

1) I am the administrator, and still I cant install the wubi
2) The Bios is somehow defective. When I turn on the computer I press Esc to select the boot device, I choose the USB drive but there is no instalation process.

I believe that there is a proble with the Bios in my computer, that is why I try to install it on windows (wubi)

Perhaps the Bios is not updated.

This is something very strange.

Something is wrong here. Right?

---

### Post by linux18 on 2010-08-15
forget  i said anything

---

### Post by linux18 on 2010-08-15
then you pirated the wrong copy of windows...

did you format the drive before using unetbootin ?

---

### Post by russnae on 2010-08-15
I had problems with it also. dont know about the Bios prob. But i used universl usb installer to install the actual ubuntu live onto the usb and it installed for me that way. hope it helps.

---

### Post by danielm316 on 2010-08-16
> **russnae said:**
> I had problems with it also. dont know about the Bios prob. But i used universl usb installer to install the actual ubuntu live onto the usb and it installed for me that way. hope it helps.

I dont have a cd player. It is a cheap cpu.

The bios thing is this. When I go to Bios advanced options then it recognizes as the first boot option the removable disk.

When I go to the boot menu, the (pendrive) usb drive appears, its a hewllet packard, and the bios recognizes it. But when I chose to boot from the pendrive, fake windows starts again. It is very uncomfortable, to be reminded time and time again that this "may be an ilegal copy" and I know it is.

Formating the disk seems to be a little extreme, because the problem is the Bios that does not boot from the pendrive (usb drive) so maybe there must be an executable file that updates the bios, how to do it? That is the question I think.

Thank you for your replies. You are very kind.

---

### Post by 3rdalbum on 2010-08-16
Did you use Unetbootin to make the USB drive bootable?

Installing Ubuntu using the Wubi installer is not what you want, because this sets up a kind of "dual-boot" where you can choose between Windows or Ubuntu whenever you boot up.

---

### Post by the8thstar on 2010-08-16
It could be that you pendrive doesn't contain any bootable media that can be recognized by the bios.

There are a lot of inexpensive USB plugged CD-drives on the market nowadays. Why not try that?

---

### Post by danielm316 on 2010-08-16
> **3rdalbum said:**
> Did you use Unetbootin to make the USB drive bootable?

Installing Ubuntu using the Wubi installer is not what you want, because this sets up a kind of "dual-boot" where you can choose between Windows or Ubuntu whenever you boot up.

I used that program and no results, also the .iso I downloaded first by using my browser and second by using torrent, no sucess in both cases.

> **the8thstar said:**
> It could be that you pendrive doesn't contain any bootable media that can be recognized by the bios.

There are a lot of inexpensive USB plugged CD-drives on the market nowadays. Why not try that?

It could be a solution or maybe not, what you suggest is expensive. The thing is that the issue here is that the bios recognizes it. That is the issue.

---

### Post by linux18 on 2010-08-16
your using a pirated copy of windows, you / your friend must have had access to a cd burner

---

### Post by Legendary_Bibo on 2010-08-16
It sounds like you need to go into your BIOS and change the boot order. You'll need to put USB first of course and leave the drive in there when you reboot.

When you install the .iso on the pendrive did you check it to see if there was a bunch of system files. You can't just copy the .iso. Also it'll wipe your drive when you turn it into a Live USB.

---

### Post by danielm316 on 2010-08-18
> **Legendary_Bibo said:**
> It sounds like you need to go into your BIOS and change the boot order. You'll need to put USB first of course and leave the drive in there when you reboot.

When you install the .iso on the pendrive did you check it to see if there was a bunch of system files. You can't just copy the .iso. Also it'll wipe your drive when you turn it into a Live USB.

Thank you for your answer Legendary_Bibo. I did changed the order, first and second is removable disk, and the removable disc is recognized as usb drive.
When i go to the boot menu, the usb drive appears, and when I do enter on it, Windows starts again.

---

### Post by danielm316 on 2010-09-19
Bad news my friends.

I bougth a DVD writer.
Put the ubuntu instal cd. Reboot the computer.

The instalation process starts, asks the language, ask what I want to do.
The word "ubuntu" appears, and an horizontal bar.
The bar is getting filled and then the computer turns off.

Please help!!!!!!

---

### Post by Rasa1111 on 2010-09-19
which version of Ubuntu are you trying to install? 10.04? 
If so, Im not really surprised by your last post. 
10.04 gave/gives many people problems upon first trying to install. 

Maybe just for kicks, try an Ubuntu 9.10, or 10.10 beta CD, and see if it doesnt boot up properly.

---

### Post by danielm316 on 2010-09-19
> **Rasa1111 said:**
> which version of Ubuntu are you trying to install? 10.04? 
If so, Im not really surprised by your last post. 
10.04 gave/gives many people problems upon first trying to install. 

Maybe just for kicks, try an Ubuntu 9.10, or 10.10 beta CD, and see if it doesnt boot up properly.

actually is the 9.04 version. And now my DVD writer does is disconected, aparently the wires are loose, tomorrow I am going to call a technitian and demand to be installed properly.

Thank you for your concern Rasa1111

---

### Post by sandyd on 2010-09-19
> **danielm316 said:**
> Bad news my friends.

I bougth a DVD writer.
Put the ubuntu instal cd. Reboot the computer.

The instalation process starts, asks the language, ask what I want to do.
The word "ubuntu" appears, and an horizontal bar.
The bar is getting filled and then the computer turns off.

Please help!!!!!!
how long have you had this computer for?

If its longer than 1.5-2 years, take it outside, and get all the dust out with a non-animal fur brush. Or just take a deep breath and blow. Dust can easily interfere with computer operation.

Secondly, since your computer seems to be having all these issues, and you mentioned BIOS issues, -> [http://www.award-bios.com/](http://www.award-bios.com/)

Thirdly, after you get your cd/dvd drive up and running, boot from the ubuntu cd. As soon as you see the purple screen, press ESC, and choose "check memory" (or whatever is similar to check memory)

---

### Post by danielm316 on 2010-09-22
the computer is new, sandyd, maybe the problem is the HD tv.
Ia am going to creat a new post on this subject.

---

