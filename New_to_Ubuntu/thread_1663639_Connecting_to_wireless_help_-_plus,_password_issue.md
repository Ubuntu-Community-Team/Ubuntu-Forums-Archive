---
title: "Connecting to wireless help - plus, password issues bonus!"
date: 2011-01-09
forum: New to Ubuntu
---

### Post by ford-prefect on 2011-01-09
I've got two problems, one which I'm guessing I need for the other. (Although I may be wrong.)

The first problem is that I haven't found a way that explains well how to get ubuntu to recognize wireless. A while ago, I installed ubuntu and got wireless to work, but I've since had to uninstall it, and I definitely don't remember what I did to get it work - I just remember it had to do something ndiswrapper. The problem is that I don't have an ethernet cable or whatever they're called. What I'm looking for is instructions on, since I'm using wubi, how to get your computer to recognize wireless networks by downloading all the files I need on my Windows half of the computer, and then accessing them on ubuntu. If anybody could help me with that, that would be very much appreciated.

Second, I noticed some password issues with the terminal. Specifically, it says I have an "authentication failure" when I put in the password that I know works for everything else. (And no, the caps lock wasn't accidentally on.) I'm not sure if this is related, but earlier, I had a similar problem - earlier I had to reinstall ubuntu because it didn't recognize the password I was positive I put. I'm not sure if they're connected, but regardless, the terminal doesn't seem to recognize my password, which is strange. Does anybody know why this might be?

Thanks in advance for your help!

---

### Post by Bucky Ball on 2011-01-09
Firstly, welcome. ):P

Ubuntu release, please? 10.10, 10.04 LTS?

---

### Post by wep940 on 2011-01-09
Also, ndiswrapper and it's GUI'd front end can be installed directly from the LiveCD - no need to download something to 1 PC and transfer it to your Ubuntu box.
 
Before we can determine if you even need to use ndiswrapper now (some things have changed in the way of drivers), please also provide the following:
 
- open a terminal window (Applications/Accessories/Terminal)
- type in each of the following, pressing enter at the end of each line.  Where you see a single ">", it needs a space before and after.  Where you see 2 ">", there is no space between them:
 
lscpi > ~/testit.txt
lsusb >> ~/testit.txt
lshw -C network >> ~/testit.txt
ifconfig >> ~/testit.txt
iwconfig >> ~/testit.txt
 
- when you have finished, copy the file "testit.txt" from your home folder to some media so you can take it to a PC with internet access.  Post the file back here as an attachment to your reply.
 
FYI - ">" says to redirect the output - in this case from the screen to a file, starting the file as a new file.  The ">>" says do the same thing, but append it to the file.  So what you are doing is having all the outputs of the commands go to a file so you can post it back here.

---

### Post by Bucky Ball on 2011-01-09
> **wep940 said:**
> Also, ndiswrapper and it's GUI'd front end can be installed directly from the LiveCD - no need to download something to 1 PC and transfer it to your Ubuntu box.
 
Before we can determine if you even need to use ndiswrapper now (some things have changed in the way of drivers), please also provide the following:
 
- open a terminal window (Applications/Accessories/Terminal)
- type in each of the following, pressing enter at the end of each line.  Where you see a single ">", it needs a space before and after.  Where you see 2 ">", there is no space between them:
 
lscpi > ~/testit.txt
lsusb >> ~/testit.txt
lshw -C network >> ~/testit.txt
ifconfig >> ~/testit.txt
iwconfig >> ~/testit.txt
 
- when you have finished, copy the file "testit.txt" from your home folder to some media so you can take it to a PC with internet access.  Post the file back here as an attachment to your reply.
 
FYI - ">" says to redirect the output - in this case from the screen to a file, starting the file as a new file.  The ">>" says do the same thing, but append it to the file.  So what you are doing is having all the outputs of the commands go to a file so you can post it back here.

wep940, before getting too carried away we need to determine what release OP is using. There are some major issues with 10.10, kernel 2.6.35-24 regarding wireless (and other things) on many machines. ;)

If that is the kernel OP is using - and looks like a very recent install so it probably is - it is a good chance part, if not all, of the problem.

The solution in that case would simply be to revert to kernel 2.6.35-23 which is fine or re-install with 10.04 LTS (IMHO best option for a new user). :)

---

### Post by wep940 on 2011-01-09
No, it's not too much.  To just assume it's the kernel is an error.  In watching the forum since 10.10, I haven't seen anyone report a wireless problem that ended up being the kernel itself.  Modules TO the kernel, such as driver modules, yes, but not the kernel.
 
The information I requested will help us determine many things:  the adapter type and chipset, whether or not a default driver is getting loaded, etc..
 
Sit back, wait for ALL the information before just jumping to a conclusiion.

---

### Post by Bucky Ball on 2011-01-09
> **wep940 said:**
> To just assume it's the kernel is an error.


NOT assuming. Asking what release is being used. :(

If it is a matter of fixing modules in the 2.6.35-24 kernel, why take a new user through endless tweaking, investigation, and problem solving? They probably just want to get into it. (I'm assuming THAT, of course.) 

Drop to the previous kernel or install 10.04 LTS (better for a new user IMHO in any case). ;)

---

### Post by wep940 on 2011-01-09
Yes, I KNOW you are.  However, you ARE assuming that's the problem according to your first post.  Even though my post count is low, I've actually been around here for several years.  Lost my old account so had to start over.  I've watched the forum and haven't seen the problem you mention.
 
Just relax - what you call "extra" information is not going to hurt a dang thing.  It's not much work, and it serves the user better to ask now and have them reply once, rather than turning back around and asking for the information.
 
Relax - it's not a big deal.  *IF* it turns out to be the kernel - so be it.  But asking for this information is just being proactive.

---

### Post by Bucky Ball on 2011-01-09
I am relaxed and also out of here. Leave it to ya and good luck ...

---

### Post by ford-prefect on 2011-01-10
Sorry, I should have mentioned that in the beginning, silly me. I'm using 10.04 LTS (that is what comes default on the latest Wubi download, right?) Attached is my "testit.txt" file. Thanks so much for your help!

---

### Post by Bucky Ball on 2011-01-10
10.04 LTS being used. Broadcom card. Should work out of the box without ndiswrapper (avoid).

Plug in an ethernet cable and you should be up in minutes. BUT if you are still on Wubi, that is mainly for trying Ubuntu. Don't know if you can install wireless drivers into it. Not experienced with Wubi at all. ;)

---

### Post by wep940 on 2011-01-13
As mentioned, the lspci output I asked for shows your wireless as Broadcom 43xx series. In the past, ndiswrapper was used for those cards, however there are now drivers available for those cards such that you don't need to use ndiswrapper. Ndiswrapper is normally only used in a few cases:
 
- there are no native or restricted drivers available
 
- you have no way to get on the net so you can't install the restricted drivers available for your adapter. In your case, you say you don't have an ethernet cable.
 
- there are no native or restricted drivers, and you can't get on the net.
 
For your card there are restricted drivers available now, so ndiswrapper shouldn't be needed. I would check under System/Administration/Additional Drivers and see if a driver shows there, and if so be sure it is enabled.
 
As also mentioned, WUBI is another animal entirely, but I can make the assumption that a driver is still needed based on the following:
 
- my understanding of WUBI is that it installs within Windows, but the system actually reboots to start WUBI. Never having used it, these are just my assumptions. Since we know WUBI isn't using virtualized hardware I would guess it still needs a driver. That being the case, there are 3 choices that I can see for you:
 
- check in System/Administration/Additional Drivers and see if a driver is alread there -> it would be something like STA or B43. If there, be sure to enable it. Then go to the "After Driver Is Installed" section below.
 
- get/borrow and ethernet cable and connect your PC directly to the router with it. Then do the following in the command line (Applications/Accessories/Terminal):
 
sudo apt-get update <press enter> This may run for a while
 
Now go back to System/Administration/Additional Drivers -> it may want to search so it may take a little while. If a driver eventually shows up be sure it is enabled. Physically disconnect the ethernet cable now. Then go to the "After Driver Is Installed" section below.
 
 

- if you do not see any drivers under System/Administration/Additional Drivers, and if you have no way to otherwise connect to the internet, then and only then install ndiswrapper and ndisgtk and use the Windows driver for your adapter. You can find the files for ndiswrapper and ndisgtk on the LiveCD, so you don't need to be connected to the net. After booting Ubuntu, insert the LiveCD and let it spin up. You may get a message about a software source being found - just cancel that. Now do the following:[LIST=1]
[*]Via "Places", navigate to /pool/main/n/ndiswrapper folder on the CD
[*]Double-click on the ndiswrapper common file to install it - wait for the install to complete.
[*]Double-click on the ndiswrapper utilities file to install it - wait for the install to complete.
[*]Navigate to the /pool/main/n/ndisgtk folder
[*]Double-click on the ndisgtk file to install it - wait for it to finish
[*]Copy your Windows XP driver files - the .inf and .sys files - to your desktop. Remember these must be Windows XP drivers only, and the type must match your Ubuntu type - 32 bit for 32 bit Ubuntu, 64 bit for 64 bit Ubuntu.
[*]Go to System/Administration/Windows Wireless Drivers - this will start up ndisgtk, and GUI'd front end to ndiswrapper.
[*]Click on "new....", then point it to the driver .inf file on your desktop and click "add" (I think - I'm on Windows right now so I don't remember for sure). It should come back and show a device/driver as loaded and active.
[*]"After Driver Is Installed" section below.
[/LIST]AFTER DRIVER IS INSTALLED
 
- right-click the network manager icon. Be sure "Enabled Wireless" shows and is checked 
 
- left-click ont the network manager icon. Do any networks show now?
 
- if connecting to a hidden network (the router is not broadcasting the network ID) be sure to use the "Connect To Hidden Network" option in network manager
 
- if encryption is enabled on the router, be sure to match the encryption and the password/passphrase
 
- if the router has MAC filtering enabled, be sure your adapter's MAC address is entered in the allowed list in the router
 
 
Post back with any problems you encounter or even more (hopefully) that it works.

---

