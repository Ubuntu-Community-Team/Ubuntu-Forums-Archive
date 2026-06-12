---
title: "HOWTO: Installing Madwifi drivers for Atheros AR5418  on Ubuntu Hardy Heron (8.04)"
date: 2008-10-08
forum: Networking &amp; Wireless
---

### Post by Nxion on 2008-10-08
[LEFT][CENTER]***[SIZE=3][COLOR=Red]***For the most up-to-date guide please visit my blog. This version located here at the forums is out o date and will be updated soon****[/COLOR][/SIZE]***
[/CENTER]
[I][B][SIZE=3][COLOR=Red] [URL="http://nmbechdol.com/2008/09/18/installing-madwifi-drivers-ubuntu/"]
http://nmbechdol.com/2008/09/18/installing-madwifi-drivers-ubuntu/[/URL]
[/COLOR][/SIZE] 
EDIT: OK, Good news for everyone :). After some testing. This way of installing the drivers work on both Hardy and Intrepid. Just follow the guide below as you would. In this guide I will add a few extra steps to get it to work on Intrepid. I will highlight them in red. Watch for them, the ones in [COLOR=#ff0000]RED are ONLY FOR INTREPID[/COLOR]. So follow the guide and ignore the [COLOR=#ff0000]RED[/COLOR] entries if you are on hardy. if you are on Intrepid make sure to run the [COLOR=#ff0000]RED[/COLOR] as well as the rest of the guide. If you have any questions or need traditional help. please leave a comment on this thread.[/B][/I]
 [/LEFT]
***REMEMBER TO FOLLOW THIS TO THE TEETH AND DOUBLE CHECK THE COMMANDS BEFORE YOU HIT THE ENTER KEY.******My disclaimer is that this worked fine on my machine. This is the way I got it to work on my machine. There might be many different ways to do it but this one worked fine for me. I take no responsibility if this breaks in any way. I really don't believe that it will. but I just wanted to let everyone know***

 1. First things first,make sure all the repos are enabled:


 ```
sudo nano /etc/apt/sources.list
```From there make sure you uncomment anything that starts with "deb" in there. So changer it from "#deb" to "deb" Something along thoes lines. To exit and save hit "CTRL+X" the answer "YES" to do you want to save, then finally hit "ENTER".
 

2. Make sure you have all the latest updates:
 

```
sudo apt-get update && sudo apt-get upgrade
```And answer yes to any thing it wants to install. Wait till it is complete and reboot.
 

3. Now the fun part. Install the build tools to compile and install the Madwifi drivers:
 

```
sudo apt-get install build-essential libssl-dev
```4. Now install the kernel headers for your architecture. I have only tested this on X86 and I know it works,but for 64-Bit systems I just have not had the time to test it. This below command will install the headers based on what ever your current type of kernel is installed. By default the generic kernel is installed.
 

FOR HARDY OR INTREPID **Thanks kevdog!**:
 
```
sudo apt-get install linux-headers-`uname -r`
``` 5.  Next we install subversion. Learn more about subversion [here]("http://en.wikipedia.org/wiki/Subversion_%28software%29").
 

```
sudo apt-get install subversion
```6. No we get the subversion driver package.
 

```
sudo svn checkout http://svn.madwifi-project.org/madwifi/trunk/ madwifi-ng
```[COLOR=#ff0000]
[/COLOR]
[COLOR=Red][COLOR=Black]_****NOTE* Now for the rest of the commands, we need to run them as root. Open a terminal and type this:***_
[/COLOR] 
```
sudo -i
```[/COLOR] 

7. Move yourself to the newley created "madwifi-ng" directory.```
cd madwifi-ng
```[COLOR=#ff0000] 
8.Blacklist ATH Drivers
[/COLOR]
 ```
echo "" >> /etc/modprobe.d/blacklist
``` [COLOR=#ff0000]
[/COLOR]
```
echo "#Remove To Install MadWIFI Drivers" >> /etc/modprobe.d/blacklist
```[COLOR=#ff0000]
[/COLOR]
```
echo "blacklist ath9k" >> /etc/modprobe.d/blacklist
``` [COLOR=#ff0000]
[/COLOR]
```
echo "blacklist ath5k" >> /etc/modprobe.d/blacklist
```8. Build the installer and install it :)
 

```
make && make install
```9. After that is complete we have one final step and that is to add the module "ath_pci" to the /etc/modules file.
 

```
echo ath_pci >> /etc/modules
```Save and close.
 

That is it. You should have nice new drivers now installed to power your wireless card. 

AGAIN IF YOU HAVE ANY QUESTIONS PLEASE CONTACT ME OR PM ME OR USE THE COMMENTS BELOW

Reboot and check NetworkManager to see if you can see any wireless networks.
 Hope this help you as it helped me. :)

---

### Post by nixforme on 2008-10-27
YAY!!!!! Thanks to you my wireless is working again! Thanks!!!!

---

### Post by sh@dowl1ght on 2008-12-14
i followed this guide, but madwifi still not working. when i do iwconfig, instead of getting ath0, i get wlan1, so i can't use wlanconfig. Is there another way to put the card in master/ap mode?

my specs are:

Dell xps m1530 Laptop, 2G ram, core2duo, built-in IPW4965, and a D-Link DWA643 MiniPCI-Ex Atheros based wifi card, Running Ubuntu 8.10 64bit

Thanks.

---

### Post by Nxion on 2008-12-16
What do you mean my ap/master mode?. Also check my blog in my sig. I have updated the guide for Intrepid. I will up dat it here as well. I am doing that now. For now check the blog. 

[BLOG]("http://bbechdol.wordpress.com")

---

### Post by Nxion on 2008-12-16
> **sh@dowl1ght said:**
> i followed this guide, but madwifi still not working. when i do iwconfig, instead of getting ath0, i get wlan1, so i can't use wlanconfig. Is there another way to put the card in master/ap mode?

my specs are:

Dell xps m1530 Laptop, 2G ram, core2duo, built-in IPW4965, and a D-Link DWA643 MiniPCI-Ex Atheros based wifi card, Running Ubuntu 8.10 64bit

Thanks.

Do you have both the Intel card and the D-Link car active at the same time?

---

### Post by sh@dowl1ght on 2008-12-18
> What do you mean my ap/master mode?.

It basically allows other computers to connect directly to it as if it where an access point.

> Also check my blog in my sig. I have updated the guide for Intrepid. I >will up dat it here as well. I am doing that now. For now check the blog.


Thanks, the guide worked, and i now have ath0. however, when i set up the interface in master mode, i can see it from a second pc, also running intrepid, but when i try to connect, it says "Athuentication key required by wireless network", and the only interactable element on the requester is a cancel button. I then scanned it with airodump-ng, which said the network was unencrypted. [http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

### Post by BlackAce on 2009-01-07
Do you know if this will also work with the Atheros A5416?

---

### Post by BlackAce on 2009-01-07
I went ahead and tried this. I think they may be the same. But I am having a problem everytime I sudo echo I get "permission denied"! 

```
 sudo echo "" >> /etc/modprobe.d/blacklist 
```



```


sudo echo "#Remove To Install MadWIFI Drivers" >> /etc/modprobe.d
/blacklist

```


```


sudo echo "blacklist ath9k" >> /etc/modprobe.d/blacklist


```

```


sudo echo "blacklist ath5k" >> /etc/modprobe.d/blacklist


```

```


sudo echo ath_pci >> /etc/modules

```

All permission denied

???:(:(:(

---

### Post by Nxion on 2009-01-07
> **BlackAce said:**
> I went ahead and tried this. I think they may be the same. But I am having a problem everytime I sudo echo I get "permission denied"! 

```
 sudo echo "" >> /etc/modprobe.d/blacklist 
``````


sudo echo "#Remove To Install MadWIFI Drivers" >> /etc/modprobe.d
/blacklist

``````


sudo echo "blacklist ath9k" >> /etc/modprobe.d/blacklist


``````


sudo echo "blacklist ath5k" >> /etc/modprobe.d/blacklist


``````


sudo echo ath_pci >> /etc/modules

```All permission denied

???:(:(:(


Don't worry, it can easily be fixed. I have to fix this guide. The reason what the above commands don't work is that you cannot run the echo commands as a normal user. I found this out the hard way, not ever sudo will suffice either. Instead do this. Open a new terminal and enter this:

```
sudo -i
```

This will bring you to a root prompt. from there finish running the commands. I took off the "sudo" part because it is not needed since your root I will fix my guide today to reflect this:

```
echo "" >> /etc/modprobe.d/blacklist 
``````
echo "#Remove To Install MadWIFI Drivers" >> /etc/modprobe.d/blacklist
``````
echo "blacklist ath9k" >> /etc/modprobe.d/blacklist
``````
echo "blacklist ath5k" >> /etc/modprobe.d/blacklist
``````
echo ath_pci >> /etc/modules
```Here is some more documentation on root in Ubuntu: [click here]("http://ubuntuforums.org/showthread.php?p=5457263")

---

### Post by kevdog on 2009-01-07
For the linux headers why make the distinction based on kernel version?

Just use the command:

sudo apt-get install linux-headers-`uname -r`

Thats all you need.

---

### Post by BlackAce on 2009-01-07
Well it works but unfortunately for some reason I have to be right on top of my wireless router for it to get a signal. I am not really what do to now? Seems like a lot of people have having issues with their wireless on 8.10.

---

### Post by BlackAce on 2009-01-07
I appreciate the help!:D

---

### Post by Nxion on 2009-01-09
> **kevdog said:**
> For the linux headers why make the distinction based on kernel version?

Just use the command:

sudo apt-get install linux-headers-`uname -r`

Thats all you need.

Thanks for this. I will update the guide to reflect the change. When I wrote the guide I was looking for this command but could never find it. Thanks again!

---

### Post by Nxion on 2009-01-09
> **BlackAce said:**
> I appreciate the help!:D

No problem :) All is well in wireless land I assume?

---

### Post by Ketara on 2009-01-28
When I run this part: "make && make install" I get "no makefile specified"

Not sure what I did wrong.

---

### Post by lazlov on 2009-02-05
Hi!

I've a problem.

> sudo svn checkout [http://svn.madwifi-project.org/madwifi/trunk/](http://svn.madwifi-project.org/madwifi/trunk/) madwifi-ng

The specified address doesn't exist in the *../trunk* folder.

What can I do in this case?

Br,
Lazlo

---

### Post by Nxion on 2009-02-09
> **Ketara said:**
> When I run this part: "make && make install" I get "no makefile specified"

Not sure what I did wrong.

Did you get this error AFTER you ran "sudo -i"? If so then iyt is becasue you are not in the folder with the madwifi drivers. I will modify the guide to reflect this.

After you run "sudo -i" do this:

```
cd /home/user/madwifi-ng
```

user  =  your username.

Then run step 8 again. YOu should be fine.

---

### Post by Nxion on 2009-02-09
> **lazlov said:**
> Hi!

I've a problem.



The specified address doesn't exist in the *../trunk* folder.

What can I do in this case?

Br,
Lazlo


Make sure you have a space between ***trunk/ and madwifi-ng*** If you don't then the command will fail. It could also be that the server was down when you tried it. Give it another try. I just did it last night and it was fine.

---

### Post by kzeouki on 2009-02-17
Thanks for the instructions, installation went flawless!

However, connectivity periodically disconnected.

I tried on 8.04 and 8.10 (both 64bit), problem still exists.

Comments will be greatly appreciated.

---

### Post by HammerOfDoubt on 2009-02-25
I ran this guide and it seems the drivers won't load after a reboot. Also, it completely hung up and lost connection before the reboot.

How do I remove this? I have no connection now and I'm posting through my netbook. Once I get this removed, I'm going to try setting up ndiswrapper.

---

### Post by Nxion on 2009-02-25
> **HammerOfDoubt said:**
> I ran this guide and it seems the drivers won't load after a reboot. Also, it completely hung up and lost connection before the reboot.

How do I remove this? I have no connection now and I'm posting through my netbook. Once I get this removed, I'm going to try setting up ndiswrapper.

Are you running a 64Bit version of Intrepid?

---

### Post by Nxion on 2009-02-25
> **kzeouki said:**
> Thanks for the instructions, installation went flawless!

However, connectivity periodically disconnected.

I tried on 8.04 and 8.10 (both 64bit), problem still exists.

Comments will be greatly appreciated.And your sure you added "ath_pci" to "/etc/modules". This symtom sounds to me like it is still using the built in Ath9k drivers.

---

### Post by HammerOfDoubt on 2009-02-26
> **Nxion said:**
> Are you running a 64Bit version of Intrepid?

I found the drivers in a link on this forum to the Linux Mint forum. I transferred the file to my desktop, compiled and installed them. Everything is working fine now.

This thread was of some help too. [http://ubuntuforums.org/showthread.php?t=816780](http://ubuntuforums.org/showthread.php?t=816780)

---

### Post by beetlejelly on 2009-02-27
Thanks! This works like a charm, although I also notice frequent drops. What's the easiest method to go back and forth from the madwifi-ng driver to the ath9k driver? 
I tried uncommenting out the driver in the blacklist but it still used the madwifi-ng driver after reboot.

---

### Post by kzeouki on 2009-03-08
> **Nxion said:**
> And your sure you added "ath_pci" to "/etc/modules". This symtom sounds to me like it is still using the built in Ath9k drivers.

To be honest, I am not sure. I followed your steps, and systems finally detects AR5418,  but disconnect periodally. Without madwifi It would not even detect the card, so I thought i was using the madwifi driver.

I would probably get a fresh reinstall, how can I check if I am using madwifi or Ath9k driver?

Following is what i have for part of /etc/modprobe.d/blacklist:
[I]#Remove To Install MadWIFI Drivers
blacklist ath9k
blacklist ath5k[/I]

---

### Post by drpjkurian on 2009-04-22
Hi nxion
I am new to Linux.I purchased a new Dell vostro A860.
I Followed all your steps, but unfortunately after typing the command 'sudo svn checkout [http://svn.madwifi-project.org/madwifi/trunk/](http://svn.madwifi-project.org/madwifi/trunk/) madwifi-ng' in terminal,  some files got downloaded and my cursor was simply blinking on  screen without any prompt. Well i closed the terminal and continued with the other commands. It was found out that after typing the command 'make && install it showed that there is no tyarget to build.

I am sorry if i am not understandable because i am not a linux geek so far...
I would like to be like ypu... solving other's problems

Dr Kurian:p

---

### Post by drpjkurian on 2009-05-17
Hi Everybody
I tried this method to install the madwifi in my new dell vostro A860 which was pre installed with atheros card
[COLOR="Red"]**Thanks to NXION who helped me a lot to do this**[/COLOR]
Well open the terminal and follow these steps.

```
sudo nano /etc/apt/sources.list
```
 
```
sudo apt-get update && sudo apt-get upgrade

```

```
sudo apt-get install build-essential libssl-dev
```

```
sudo apt-get install linux-headers-`uname -r`

```

 ```
sudo apt-get install subversion
```

```
sudo -i
```

 ```
sudo svn checkout http://svn.madwifi-project.org/madwifi/trunk/ madwifi-ng
```

```
cd madwifi-ng
```

```
make && make install
```

```
echo ath_pci >> /etc/modules
```

Well after this reboot your machine and enjoy your wifi

---

### Post by Nxion on 2009-05-17
Technically this is the same speps that I have already in my guide. The only difference is that the "sudo -i" step and the svn step is switched. Which I have tried and they work either way. it makes no difference if you do the SVN command before or after the sudo -i command. I believe in your situation it was a fluke in your setup. Thanks you for your suggestions but I have chosen to keep my guide the way it is.

---

### Post by Nxion on 2009-05-17
I have not had the time to update this guide on the forums. The latest up to date guide is on my blog. Once I have some time, maybe today, I will update it.

---

### Post by drpjkurian on 2009-05-20
> **Nxion said:**
> Technically this is the same speps that I have already in my guide. The only difference is that the "sudo -i" step and the svn step is switched. Which I have tried and they work either way. it makes no difference if you do the SVN command before or after the sudo -i command. I believe in your situation it was a fluke in your setup. Thanks you for your suggestions but I have chosen to keep my guide the way it is.

Dear Nxion
Thank you for your suggestion

:KS

---

### Post by nicklausmichael on 2009-11-04
So say I want to undo all of this .. what would be the steps I would take to restore the original drivers I had before madwifi installation...?

---

### Post by drpjkurian on 2009-11-04
> **nicklausmichael said:**
> So say I want to undo all of this .. what would be the steps I would take to restore the original drivers I had before madwifi installation...?


Hi

To remove madwifi
Please navigate to the systems--->Administration---> Synaptic package manager.
In this packet manager type madwifi in the search bar. You will be getting the madwifi packages.
Click it and uninstall. The OS may ask for a password prompt.

This will remove the madwifi driver, But it does not mean that you will be getting back your old driver. You may have to install the old driver.

With regards
Dr Kurian

---

### Post by nicklausmichael on 2009-11-04
> **drpjkurian said:**
> Hi

To remove madwifi
Please navigate to the systems--->Administration---> Synaptic package manager.
In this packet manager type madwifi in the search bar. You will be getting the madwifi packages.
Click it and uninstall. The OS may ask for a password prompt.

This will remove the madwifi driver, But it does not mean that you will be getting back your old driver. You may have to install the old driver.

With regards
Dr Kurian
All Im getting from that is:hostapd package when I enter madwifi into the search.. and thats the only thing...and Im pretty sure madwifi is running seeing I had entered modprobe madwifi-ng and its listed in the modules..

---

### Post by drpjkurian on 2009-11-06
> **nicklausmichael said:**
> All Im getting from that is:hostapd package when I enter madwifi into the search.. and thats the only thing...and Im pretty sure madwifi is running seeing I had entered modprobe madwifi-ng and its listed in the modules..

Hi
Try to boot into a recovery console (one should be available from grub). Navigate to your madwifi folder (where you make installed from in the first place) and type

 
```
make uninstall
```

Try this
With best of luck
Dr Kurian

---

