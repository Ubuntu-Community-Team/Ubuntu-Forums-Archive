---
title: "where do i write the code ??"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by kokokiki on 2009-12-03
i'm sorry for this question if it's that stupid but i don't know i looked everywhere , in the post below it's from another topic where it's written code: .... where am i supposed to write that i opened something called terminal but it wont except any of these commands it only accepts file locations so ???? 

**complete tutorial on how to set up Netgear WPN111** 			 			 			 		   		 		 		This is a complete how to on installing and setting up the Netgear WPN111 wireless device in Ubuntu Gutsy Gibbon.

1. Download the two attachments (WIndows drivers and ndiswrapper)

2. Install build-essential (Needed for compiling ndiswrapper) 	Code:
 	sudo apt-get install build-essential 
3. Extract ndiswrapper 	Code:
 	tar -zxvf ndiswrapper-1.51.tar.tar 
4. Go to the ndiswrapper directory 	Code:
 	cd ndiswrapper-1.51 
5. Run 	Code:
 	make distclean
make
sudo make install 
6. Check that ndiswrapper is installed properly  	Code:
 	ndiswrapper -v 
If it outputs something like this:
 	Code:
 	utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.45
vermagic:       2.6.22-14-generic SMP mod_unload 586 
It has installed correctly. 
If it show something different (Please upgrade ndiswrapper to the latest version by going to the ndiswrapper website [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)), run  	Code:
 	sudo make uninstall 
 Three times and repeat steps 5-8 again and check ndiswrapper -v again. 

If it does display the correct output, then you can move to the next step 

7. Go back to your home directory 	Code:
 	cd .. 
 and then extract the windows drivers 	Code:
 	tar -zxvf win-drivers.tar.gz 
8. Change directory to the windows drivers 	Code:
 	cd win-drivers 
9. Run 	Code:
 	sudo ndiswrapper -i netwpn11.inf 
10. Check if the windows driver is installed 	Code:
 	ndiswrapper -l 
If it shows: then you can move onto the next step.
 	Code:
 	netwpn11 : driver installed
        device (1385:5F01) present 
If not, remove driver 	Code:
 	sudo ndiswrapper -r netwpn11 
 And reinstall the driver 	Code:
 	sudo ndiswrapper -i netwpn11.inf 
11. Run 	Code:
 	sudo depmod -a
sudo ndiswrapper -m
sudo modprobe ndiswrapper 
If it all goes to plan, Ubuntu should still be running OK and the Netgear device should be winking at you:KS

12. Finally make sure that the device initializes at boot, run 	Code:
 	nano /etc/modules 

 and one more question i just installed linux yesterday but i can't find any of my partitions does that mean my data is gone ?? thanx for reading all that and i hope someone helps me i'm really lost here

---

### Post by Diametric on 2009-12-03
Go to: Applications -> Accessories -> Terminal

This opens a console where commands are executed.  I recommend reading a bit about the command console before attempting to run any commands.  I'm new at this too, and have found it to be the center for all that is Linux so far....good luck, mate.

---

### Post by Cheezespread on 2009-12-03
> where am i supposed to write that i opened something called terminal but it wont except any of these commands it only accepts file locations so ???? 
You got it right . You have to enter the commands/codes in the terminal(**Applications -> Accessories -> Terminal**) . But the code from second part "tar -zxvf ndiswrapper-1.51.tar.tar " works only if you have the downloaded file in the directory you are in now.

By default your terminal ( or command prompt if you have used Windows) are pointing to the home directory which is shown by this symbol - " ~" .  So if you have downloaded the files into your Desktop , you will have to change the working directory (directory shown in the terminal ).

```
cd Desktop
``` should do .  Try the codes after that .

---

### Post by kokokiki on 2009-12-03
thanx diametric for that it really sucks that it's the center of everything must we write codes for every program we want :confused:
and cheezespread thank u for that u r a life saver but the first command did not work it said e: couldn't find package build essential ! i looked it up and i think i should have internet connection on the linux computer but i'm really tired and with the whole where did all my data go thing i think i'm going back to windows for now but thanx for all your help guys):P

---

### Post by lisati on 2009-12-03
> **kokokiki said:**
> thanx diametric for that it really sucks that it's the center of everything must we write codes for every program we want :confused:
and cheezespread thank u for that u r a life saver but the first command did not work it said e: couldn't find package build essential ! i looked it up and i think i should have internet connection on the linux computer but i'm really tired and with the whole where did all my data go thing i think i'm going back to windows for now but thanx for all your help guys):P
The terminal is just a tool for telling the computer what you want to do. Yes, it can be a bit baffling when you're used to using your mouse to do your work, but taking the time to familiarise yourself with some of the basics can be very rewarding. Thankfully, many people have put in the work to let you use your mouse for most things instead of having to remember commnads that don't immediately seem to make sense.

And yes, when someone gives you instructions on using the terminal, it is quite common for them to assume that you have a working internet connection.

---

### Post by kokokiki on 2009-12-03
i feel bad because linux  sounds like a great system and especially after you helped me but i feel bad about the data that got lost , sorry to disappoint you guys

---

### Post by dBuster on 2009-12-03
As far as your data being gone, it all depends on how you had partitioned your hard drive with the installation of Ubuntu.  

I have done several partitioning hard drive jobs and never have I lost data.  It may be on a different drive letter but it is still there for me.  Now if it was on a NT file format drive Ubuntu, depending on version, may need help to read that drive.  

To give up on something that might not be fully understood is not really a loss but rather a goal not obtained.  You can do it, takes patience and time to learn just as it did with windows when you first started out with windows.  I still remember learning windows 2.0 and then 3.0, 3.1, 3.11 and so on.  Talk about a nightmare.

---

### Post by kokokiki on 2009-12-03
> **dBuster said:**
> As far as your data being gone, it all depends on how you had partitioned your hard drive with the installation of Ubuntu.  

I have done several partitioning hard drive jobs and never have I lost data.  It may be on a different drive letter but it is still there for me.  Now if it was on a NT file format drive Ubuntu, depending on version, may need help to read that drive.  

To give up on something that might not be fully understood is not really a loss but rather a goal not obtained.  You can do it, takes patience and time to learn just as it did with windows when you first started out with windows.  I still remember learning windows 2.0 and then 3.0, 3.1, 3.11 and so on.  Talk about a nightmare.

a nightmare indeed thanx dbuster for ur support i would like if i stayed and learned about it but i'm afraid about all my the drives they were initially ntfs i dont know what i really did i wanted to delete widonws i must have deleted the other partitions with it  plus c was 7gb before and now it's 60 or 7o gb or smth so i kinda lost my will to learn if it turned out the data is still there i definetly will set it up again that is if i can return winodws now !

---

### Post by themusicalduck on 2009-12-03
Going back to your original problem, you might be able to get your wireless working a lot easier than by using ndiswrapper.

Can you connect to the internet using an ethernet cable? Perhaps if you have a router or something that you can just plug into?

Then you could go to System > Administration > Hardware Drivers. You might be able to install wireless drivers from there as long as you can connect with ethernet first.

Also just to check if your partitions are really gone, type this command into a terminal ```
sudo fdisk -l
``` (small L at the end) and post the result here.

Lastly, which version of Ubuntu did you install?

---

### Post by kokokiki on 2009-12-04
hey themusicalduck
it's a ubuntu, linux 2.6.31-14-generic

i did what u said and i'm actually very surprised that i wrote a command that actually worked  

disk /dev/sda: 80.0 gb,  80026361856 bytes 
255 heads, 63  sectors/track, 9729 cylinders
units = cylinders of 16065 * 512 = 8225280 bytes
disk identifier: 0xc79ec79e

    device boot          start           end       blocks             id      system

/dev/sda1     *            1             9355      75144006       83       linux
/dev/sda2                 9356          9729       3004155         5     extended 
/dev/sda5                 9356          9729       3004123+     82     linux swap /solaris

---

### Post by themusicalduck on 2009-12-04
Well it looks like you only have your Ubuntu partition and not any of your old partitions.

Did you managed to connect to the internet through ethernet cable so you could download your wireless drivers?

---

### Post by kokokiki on 2009-12-05
> **themusicalduck said:**
> Well it looks like you only have your Ubuntu partition and not any of your old partitions.

Did you managed to connect to the internet through ethernet cable so you could download your wireless drivers?


i did and it updated twice but when i restart everything goes back to being the same and this message comes when i enter the second command cd ndiswrapper-1.51
cd ndiswrapper-1.51 : no such file or directory 

anyway thanx for your help i really appreciate it

i just want to do one last thing before i set up windows which is recovering my data and i heard there is this program called test desk and photo rec but again i cant get them to work whatever it is i downloaded ar all text files so would u please help me one last time to set this up then i could go back to windows thanx again

---

### Post by themusicalduck on 2009-12-06
What updated twice? You need to go to System > Administration > Hardware Drivers and to activate any drivers listed there. If you did manage to install a driver from there and it still didn't work, then I don't know what else to suggest. The theory is if you download them from there then you won't have to bother with ndiswrapper. Bearing in mind that that tutorial is for Gutsy Gibbon which is a very old version of Ubuntu, it's very likely not the best way to fix it now, and ndiswrapper is pretty unreliable.

I can't really help with data recovery. If you really want to try and recover stuff then it might be better to make a new thread about it.

---

### Post by kokokiki on 2009-12-06
> **themusicalduck said:**
> What updated twice? You need to go to System > Administration > Hardware Drivers and to activate any drivers listed there. If you did manage to install a driver from there and it still didn't work, then I don't know what else to suggest. The theory is if you download them from there then you won't have to bother with ndiswrapper. Bearing in mind that that tutorial is for Gutsy Gibbon which is a very old version of Ubuntu, it's very likely not the best way to fix it now, and ndiswrapper is pretty unreliable.

I can't really help with data recovery. If you really want to try and recover stuff then it might be better to make a new thread about it.

thanx for all ur help really i opened it and it turned out linux crashed it had crashed before but this time i used the live cd to format and install windows if it was going to be formatted anyway this is the second time it keeps crashing every 2 days idk why but anyway thanx for ur help u have been very helpfull i'll try windows recovery data softwares thanx again;)

---

