---
title: "Ubuntu won't start up"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by greenleaves123 on 2009-02-17
I have no idea what is wrong.

I tried to turn on my Dell Mini 9 and the Ubuntu words come up, then it's a black screen with tons of errors scrolling down, then a blue box that says the graphical interface won't start. There is a Yes or No option, I try hitting enter, but it won't work. None of the keys work. 

Then I press the power button and the computer shuts down.

I've tried shutting down several times and starting back up, same thing happens.

Please help.

---

### Post by JustANewb on 2009-02-17
What are some of the errors showing up?

---

### Post by sandyd on 2009-02-17
when you get to the blue error screen, press "ctrl + c"
or go into recovery console

when you get a terminal running, type this in

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

you probably fried your xorg.conf. its probably fixable another way, but this is the fastest

---

### Post by greenleaves123 on 2009-02-17
I tried control+c on the blue screen but nothing happens. None of the keys do anything. 

How do I get the terminal running?

---

### Post by 0br0k3n0 on 2009-02-17
> **greenleaves123 said:**
> I tried control+c on the blue screen but nothing happens. None of the keys do anything. 

How do I get the terminal running?

when you boot, does it give you any options at the beginning?

---

### Post by greenleaves123 on 2009-02-17
OK, the blue screen went away, I'm not sure why. Now it's the black screen and it says:

Ubuntu 8.04.1 jenny tty1

jenny login:

What do I do?

---

### Post by 0br0k3n0 on 2009-02-17
do crt-alt f7 if not then ctrl- alt- f11

---

### Post by greenleaves123 on 2009-02-17
I did ctrl+alt+F7 on the login, but nothing happened. Also I do not have an F11 key on my Dell mini 9.

---

### Post by 0br0k3n0 on 2009-02-17
do ctrl-alt-f1

---

### Post by 0br0k3n0 on 2009-02-17
well when you boot up, at one point, does it say press esc for....

---

### Post by greenleaves123 on 2009-02-17
I'm not sure if I'm using the F keys correctly, my netbook neets the Fn keys to activate the F keys.

I am on Dell technical support and I've been transfered 6 times and no one can help me.

---

### Post by 0br0k3n0 on 2009-02-17
because if you do press esc at boot up it will take you to optoin to run normal, recovery mode, and settings
you can terminal on recovery

---

### Post by greenleaves123 on 2009-02-17
It goes really fast, I mananged to read 0 for boot options.

---

### Post by 0br0k3n0 on 2009-02-17
umm this is what i did, when you press esc when your booting up and it gives you that option, tell it to run normal (first one) i did that and it worked and figure the rest while your running ubuntu

---

### Post by greenleaves123 on 2009-02-17
OK, I hit zero repeatedly when I turned it on and now it's the Boot Menu

The options are:

Hard Drive
Network Book
CD/DVD/CD-RW
Removable Devices
Diagnostics

---

### Post by 0br0k3n0 on 2009-02-17
im no expert at this and i am just a kid but i figure things out.. i just mess around with the booting options and i made it work =)

---

### Post by 0br0k3n0 on 2009-02-17
oh oops sorry i meant when it is bearly loading ubuntu and it says loading 1.5 kernal

---

### Post by 0br0k3n0 on 2009-02-17
well i got to go to bed so if you acess  the terminal so -sudo apt-get install ii-

---

### Post by greenleaves123 on 2009-02-18
I have a black screen that asks for my login

How do I login?

I don't know what to do.

---

### Post by Kain000 on 2009-02-18
> **greenleaves123 said:**
> I have a black screen that asks for my login

How do I login?

I don't know what to do.

ok so you've pressed f1 or under the esc boot menu you've tried recovery mode right?

You are at a terminal window.

it wants you to log on normaly, so do so with the info you used to install your system.

username and password

---

### Post by greenleaves123 on 2009-02-18
I've tried all combinations of my name and nothing works. What is the login info??

I only use one password and it worked before when I had other problems and had to do the sudo stuff. 

I don't know how to log in.

---

### Post by Kain000 on 2009-02-18
once you log on type this:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and press enter.

it will then ask you for your sudo password  (all sudo does is just give the user :you in this case: "sudo" god-like permissions) (sudo meaning just for a little bit)

it's a preventive measure against crackers and people who have access to your computer, so they have to have your password to make any real changes to the system.

so once you've run that command what happens?

---

### Post by Kain000 on 2009-02-18
> **greenleaves123 said:**
> I've tried all combinations of my name and nothing works. What is the login info??

I only use one password and it worked before when I had other problems and had to do the sudo stuff. 

I don't know how to log in.

ok so you got this thing from dell right?


when you first booted it up you had to set up an account didnt you?

I ask because Ive never gotten a ubuntu laptop from dell before, just install form CDs'

---

### Post by greenleaves123 on 2009-02-18
I don't remember having to set up a username for my netbook, just my password. There is no username. 

It says:

Ubuntu 8.04.1 jenny ttyl

jenny login:

What do I type??

---

### Post by greenleaves123 on 2009-02-18
Yes, I got it from Dell, it's an Inspiron mini 9.

I called Dell and they transfered me like 6 times and no one knows anything about Ubuntu.

---

### Post by Kain000 on 2009-02-18
> **greenleaves123 said:**
> I don't remember having to set up a username for my netbook, just my password. There is no username. 

It says:

Ubuntu 8.04.1 jenny ttyl

jenny login:

What do I type??


If you didnt have to set up a username and the password you gave it is incorrect or not accepted I dont kno.   Try using the name 

root
and then your password

---

### Post by greenleaves123 on 2009-02-18
Nothing works, root doesn't work.

:(

---

### Post by Kain000 on 2009-02-18
to be quite honest, I'm not sure what Dell puts on their ubuntu systems if anything, but if it's anything like their windows laptops (how mine came) their chocked full of "dell extras" that bog down and screw up.   

If you are having this much trouble with a fresh system and cant log in, at this point I would just download a live cd (if dell hasnt already included one) burn it and do a re-install.   It takes perhaps 20-30 mins to do and I think will save you a lot of headache.  Plus you will be able to set your user name and password.    You could even enable auto login if you wish, (not recomended but if you like...)

---

### Post by greenleaves123 on 2009-02-18
I have a CD with Ubuntu on it, but my netbook doesn't have a CD drive.

At the screen with the blue, everything is all messed up, there are random pixels.

---

### Post by Kain000 on 2009-02-18
> **greenleaves123 said:**
> I have a CD with Ubuntu on it, but my netbook doesn't have a CD drive.

At the screen with the blue, everything is all messed up, there are random pixels.

wow......](*,):-s  you certainly dont like the easy route do you... lol

Hummmm ok if you want to do a fresh install (I recommend you do )  You must have a usb drive right???


do you have a usb stick?

---

### Post by greenleaves123 on 2009-02-18
No, I don't have a USB stick, I'll have to buy one. I don't know much about them, should I buy a specific type?

---

### Post by Kain000 on 2009-02-18
Well I hate to tell you that you have to go "buy" somthing to make your Linux system work... but sadly I dont know how to fix your system as is and think that a fresh install would be your best bet.

If anyone else knows please chime in...

  The good news is that USB memory sticks are pretty cheep these days and can be found just about anywhere.  every stick is just about the same, im sure you can find someone to tell you otherwise but dont pay ALOT for a USB drive.  I would recomend at least a 1 GB stick, i'm not sure what the min is, but I know my older 256MB one was too small.

I bought a 4 GB one for $12 at bestbuy made by a brand name PNY, just for this reason and now in addition to being able to eaisly tote my files from school and home, I have the stick set up to be an entire ubuntu system.

now keep in mind it's only a 4GB stick so I cant have many apps installed but I can keep quite a few files and pics.

If you want once your up and running I can help you make it into a boot disk so you can go up to any computer, put your usb stick in and tell the computer to boot from it, and vollaaaa! you have your own system with your saved files on what ever computer you choose!!!  it always gets a few looks from classmates.

---

### Post by sandyd on 2009-02-18
the username is "jenny"

type in your password

then type in 
```

sudo dpkg-reconfigure -phigh xserver-xorg

```no quotes in the username please :)

/word vomit
and this is why i sometimes hate preloaded OSes sooo much.
they come with all the manufacturers programs and stuff, which you may never run, and they do these weird customizations to the OS that causes problems like this one.

Although this is for newbies, put something out there that will allow a person to fix his/her own problems. Don't customize the OS so much. Everyone has to learn how to use this stuff

/end word vomit

---

### Post by Kain000 on 2009-02-18
> **carlee said:**
> the username is "jenny"

type in your password

then type in 
```

sudo dpkg-reconfigure -phigh xserver-xorg

```no quotes in the username please :)

/word vomit
and this is why i sometimes hate preloaded OSes sooo much.
they come with all the manufacturers programs and stuff, which you may never run, and they do these weird customizations to the OS that causes problems like this one.

Although this is for newbies, put something out there that will allow a person to fix his/her own problems. Don't customize the OS so much. Everyone has to learn how to use this stuff

/end word vomit

haha yeah I agree about the preloaded stuff.   Does the dell ubuntu come with extra stuff?    never had to deal with one.

I thought she already tried jenny and even root and it wouldn't let her in, hence my suggestion for a fresh install.

and what do you mean is for newbies?

---

### Post by greenleaves123 on 2009-02-18
Hello, thanks for helping me out.

I called Dell again tonight and got transfered like 5 times back and forth and back and forth and finally I got angry and threw a fit and finally someone helped me. He said there was a Canadian division that is supposed to help me, but the Canadian division doesn't know anything about Ubuntu. The American guy helped me out.

He determined that there is something wrong with the operating system and it needs a fresh reinstall. You guys were right. 

He says I need an an external optical drive. 

I'm supposed to call the Canadian support and they hopefully help me out, cross my fingers.

Do I have to get an external drive? Or is the USB thingie ok? I am technicially challenged so someone would have to give me the steps.

---

### Post by Kain000 on 2009-02-18
Haha now that is funny, not for you of course but that Dell has no idea!  


You dont need a Cd drive if you dont think you will have a use for it after you re-install.

Personally if my laptop had no drive, and I had to choose usb or cd drive with the same money to spend, I would def. go with the USB because I think I would get alot more use out of it.


get yourself a 4GB USB flash drive from best buy  (or newegg.com if you are not in a hurry, as you could probably get a better deal) but either way it will cost about 12-15 bucks.

By the way what machine are you using to get on the forums?  ubuntu or windows?

I ask because once you have the drive you will need to create a boot disk and I can tell you what program but need to know what operating system.

---

### Post by greenleaves123 on 2009-02-20
Thanks for helping me out, it seems you guys are my only hope now. I called technical support again, this time the Canadian division and even after telling them I need a reinstall of Ubuntu, they can't help me. The gave me a number for Ubuntu and I think it is for businesses only because I had already called that number before and they said they couldn't help me. Seriously no one can help me but you guys. 

I guess I could take my netbook into a computer shop if worse comes to worse, but I'd rather not spend the money. 

I am using Windows, not Vista but the one before it, I forget what it's called. 

Thanks so much for helping me, Dell is sooo frustrating. They have no Ubuntu support.

---

### Post by Kain000 on 2009-02-20
> **greenleaves123 said:**
> 

Thanks so much for helping me, Dell is sooo frustrating. They have no Ubuntu support.

Hey no problem this is what this form is for, and dont feel bad I was just as lost when I started out.


OK so you are using windows XP to get on here witch means that you will need to gather the following for this all to work out correctly.


1) A USB drive of reasonable size (1GB or more i'd recomend)

2) a disk image of the ubuntu system you want .iso file  (basicly the virtural equavlant of a real life cd, it's what we will put on the USB drive to boot from)

3) a copy of unetbootin for windows (the program that will put the image file onto the usb and make it into the computer equavlant of the live cd that dell gave you.


go here for the image file 
[http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download")
leave the selections already checked (ubuntu 8.10  and 32 bit)  and select a physical geographic location (the closer to your location usually the faster the download) and just save the file to your desktop or documents, just somewhere you will know to find it later.


you can get unetbootin here:
[http://sourceforge.net/project/downloading.php?groupname=unetbootin&filename=unetbootin-windows-312.exe&use_mirror=superb-east]("http://sourceforge.net/project/downloading.php?groupname=unetbootin&filename=unetbootin-windows-312.exe&use_mirror=superb-east")

save the file again somewhere you can find it.

once you have the usb and the 2 files ready post me back and we will get your system up and running.

---

### Post by sandyd on 2009-02-20
> **Kain000 said:**
> haha yeah I agree about the preloaded stuff.   Does the dell ubuntu come with extra stuff?    never had to deal with one.

I thought she already tried jenny and even root and it wouldn't let her in, hence my suggestion for a fresh install.

and what do you mean is for newbies?
meaning: netbooks that contain ubuntu are good for newbies to get a start on ubuntu b/c i'm guessing they have the ubuntu-restricted-extras, codecs, media players, and stuff already isntalled. probably because Dell is a company. Its not considred illegal for them to distribute it like that.

your right. the username should.... be the name of her computer... because i ripped it from a few other forums to comfirm it.... reinstall time i guess. not so much bloatware and weird customizations, this time at least

---

### Post by sailthesea on 2009-02-20
Wouldn't an mp3 player with decent capacity double as a flash drive?
You would at least have something that does more than just fix the problem and you can do the same again if need be I used my Zen Stone to transfer stuff loads of times If you can't get something for nothing at least get the most from it!
 Hope you succeed!

---

### Post by Kain000 on 2009-02-21
> **sailthesea said:**
> Wouldn't an mp3 player with decent capacity double as a flash drive?
You would at least have something that does more than just fix the problem and you can do the same again if need be I used my Zen Stone to transfer stuff loads of times If you can't get something for nothing at least get the most from it!
 Hope you succeed!

true you can use a mp3 as a portable storage unit like the zen or the ipod, problem is we are creating a new partition table on the usb drive to make it into a bootable "live cd", after this is on there you can use it like a normal usb drive but if she was to use her ipod like that It would format it first.

also you can use the USB drive for anything, the least of witch is a live cd for live boots and system repairs.   You can even give yourself a bit of drive space on the usb stick so that when you take it to school for instance, you can plug it into the computer you will be working on and boot up your own system with your saved files.... mind you It cant be a very large system (lots of apps) but you can keep quite a few open office documents and pictures.

---

### Post by greenleaves123 on 2009-02-21
I bought an 8GB USB flash drive. It was $17. There were some others that were a lot more expensive.

I downloaded the two files to my desktop.

---

### Post by Kain000 on 2009-02-21
> **greenleaves123 said:**
> I bought an 8GB USB flash drive. It was $17. There were some others that were a lot more expensive.

I downloaded the two files to my desktop.

alright now that you've got everything double click the .exe file you downloaded to install the unetbootin on your system.

---

### Post by Kain000 on 2009-02-21
once that is installed, you need to run it and it should open a window.

the first thing you need to select is the distro, you want ubuntu towards the bottom. 

the second one is 8.10 live

the next thing to select is the disk image , ISO and then click the box on the right with the 3 dots ...    find your .iso file you downloaded to your desktop and select it.

lastly make sure USB is selected and then ok.

---

### Post by greenleaves123 on 2009-02-21
I didn't have to install unetbootin, I clicked on it and there was a run option.

I got a Windows No Disk error. I put in the USB drive, but maybe I did it too late?

Right now it's extracting and copying files. I don't know if the error affects things. The error box won't go away.

---

### Post by greenleaves123 on 2009-02-21
OK, I closed it all and did it again, this time I selected the other drive. I think it worked, it extracted and copied all the files. The it told me to reboot and to select Boot or something.

I just rebooted, but there is nothing to select.

---

### Post by Kain000 on 2009-02-21
> **greenleaves123 said:**
> OK, I closed it all and did it again, this time I selected the other drive. I think it worked, it extracted and copied all the files. The it told me to reboot and to select Boot or something.

I just rebooted, but there is nothing to select.

alright great, so now you need to take your usb drive and plug it into your netboot.   when you press the power button you will have to be quick about this as you only have a few seconds each time you boot but when you start it there should be some words that say press F1 or delete or esc to enter setup or somthing like that, once you hit the right key you will be in a screen that looks like blue or green depending on your computer.    

you will need to use the arrow keys to make you way to the boot opntions section and select the first boot device.

Right now it's mostlikely your harddrive, change this to removiable and press esc or sometimes its F10 and a diolouge that says somthing like press somthing to save changes and exit    

save the changes and it will reboot this time off the usb drive and you will get a selection of languages

choose english and then from the ubuntu menu select install, 

next answer it's questions and give yourself a password.

Once to the part where it asks about how to install the system (shows a bar and your hardrive)  choose "guided, use entire disk"

this will erase your old install and do a fresh one.

---

### Post by greenleaves123 on 2009-02-21
Hmmm...it's not working. When it boots off the USB drive, it goes to this screen that says UNetbootin. The options are Default, Help or OEM install for manufacturers.

I try pressing enter for each of them and nothing happens. 

At the bottom it says Automatic Boot in _ seconds. (It's a countdown from 10, but nothing happens when it reaches 1)

---

### Post by greenleaves123 on 2009-02-22
Does anyone have any ideas on how why this is not working?

---

### Post by Kain000 on 2009-02-22
> **greenleaves123 said:**
> Does anyone have any ideas on how why this is not working?
sorry I have been burried with work and I have an electronic final tuesday.

alright look at the screen shot in the picture, does your unetbootin in windows look like that?    

Make sure that the iso image path (that long string of words next to the word iso)  is pointing to your desktop where you downloaded the ubuntu 8.10 file.

also go to start > mycomputer and look what drive the usb stick is.   it may be D:\ or somthing like that, make sure when you select USB in the unetbootin window that it's pointing to the right drive.

then click ok and let it wright to the USB drive

---

### Post by greenleaves123 on 2009-02-22
Oh, no problem, I am busy at work a lot too.

I got it to work!

I think the problem was that the Ubuntu image iso file I downloaded was messed up or something. On unetbootin, I selected the first radial dial instead of the second one that lets you load a file. It downloaded the iso file again and this time the file worked.

I got the live version of Ubuntu up and running and I selected install. I installed it and now I'm just waiting for updates to be downloaded.

Are there other things I need to do to make Ubuntu fully functional? I'm going to go back to my previous threads and do some of the stuff that made Ubuntu more functional, like restricted extras and stuff.

Yay! And now I have the latest version of Ubuntu too! I called Future Shop the other day and this would have cost me $100 so I owe you a big thanks.

---

### Post by Kain000 on 2009-02-23
> **greenleaves123 said:**
> Oh, no problem, I am busy at work a lot too.

I got it to work!

I think the problem was that the Ubuntu image iso file I downloaded was messed up or something. On unetbootin, I selected the first radial dial instead of the second one that lets you load a file. It downloaded the iso file again and this time the file worked.

I got the live version of Ubuntu up and running and I selected install. I installed it and now I'm just waiting for updates to be downloaded.

Are there other things I need to do to make Ubuntu fully functional? I'm going to go back to my previous threads and do some of the stuff that made Ubuntu more functional, like restricted extras and stuff.

Yay! And now I have the latest version of Ubuntu too! I called Future Shop the other day and this would have cost me $100 so I owe you a big thanks.


hey no problem, just happy to help.

As far as extras for playing media, i suggest opening up the add/remove package mananger 
(appliaction > add/remove)   and under the "all supported software" selection, search for gstreamer, 

this will pull up a handful of "codecs" witch are sorta the keys to playing different kinds of media (.mp3 .m4a .aac ect) 

As far as media management I dont think you can beat amarok espacially if you have an ipod.  just about the only thing you cannot do is transfer video, (you need another app for that)

---

