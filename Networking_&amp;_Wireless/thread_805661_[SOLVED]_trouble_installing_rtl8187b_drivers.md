---
title: "[SOLVED] trouble installing rtl8187b drivers"
date: 2008-05-24
forum: Networking &amp; Wireless
---

### Post by mbarvian on 2008-05-24
hi guys, im a complete newb when it comes to ubuntu, but know my way around windows pretty well.  i have a toshiba satellite laptop with a realtek wireless card (unfortunately).  i went to the hacked drivers and downloaded the jadams version, but i have absolutely no clue on how to install them.  i know that the first step is extracting the .tar.gz, so ive already done that.  can anyone help me out with where to go from there?

thanks

---

### Post by chili555 on 2008-05-24
Please open up System->Administration->Synaptic and install *build-essential, linux-headers-generic* and *linux-source*. These are all 'generic' packages that will pull in the exact requirements according, mostly to your running kernel. As well, as updates come along, they will be applied to your system.

Once that is done, open a (Applications->Accessories->) terminal and change directory to the folder that was created when you extracted the tar.gz. Now for a bit of magic: enter in the terminal, *cd Desktop/rtl8* and now press Tab. The rest of the file name will be filled in for you. This assumes you downloaded the file to your Desktop.

Next, some ape has written a pretty fair post #12 here: 
[http://ubuntuforums.org/showthread.php?t=782299&highlight=jadams&page=2](http://ubuntuforums.org/showthread.php?t=782299&highlight=jadams&page=2)

Please let me know if you get stuck. The included README is your friend.

---

### Post by mbarvian on 2008-06-19
also, would this technique work on the new opensuse? (v11)  just a question my friend wants to know

---

### Post by chili555 on 2008-06-19
The technique of compiling from source, also known as .tar.gz? Certainly. Will you find *build-essential* and *linux-headers* in Suse? I don't know, but I doubt it. I'm sure you could install gcc, make, g++ and a few other things and get it going.

---

### Post by mbarvian on 2008-06-19
OK, I guess I'll just convince her to upgrade to Ubuntu :)

---

### Post by mbarvian on 2008-06-21
also, I am having trouble installing after sudo chmod +x makedrv

can someone help?

---

### Post by chili555 on 2008-06-21
> **mbarvian said:**
> also, I am having trouble installing after sudo chmod +x makedrv

can someone help?What kind of trouble? What errors were thrown up? What is the stick point?

---

### Post by mbarvian on 2008-06-21
Well, after following your post (#12 on the thread you linked to), I proceeded with following the Readme.txt file, where it said to ./wlan0up.  After CD'ing to the right directory, I did:
```
./wlan0up
```
It would first say "Permission Denied" or something like that, so I tried:
```
sudo ./wlan0up
```
and it said:
```
Bash: command not found
```

Any suggestions?

---

### Post by treymul on 2008-06-21
Hey, I have used both, the drivers you are talking about and ndiswrapper.  The modified driver you are trying to use is difficult to get working with wpa encryption.  I could only get it to work with wep.  Ndiswrapper with the windows 98 driver is easy to get working with wpa.  Just something to think about.

---

### Post by mbarvian on 2008-06-21
ok, well, I'm pretty sure I have WEP, but my network is unprotected, so which one do you think I should use?

---

### Post by treymul on 2008-06-21
WEP is very easy to crack, if your router supports it I would try and use WPA or WPA2, which I think would be easier by using ndiswrapper.  Thats just my preference, a lot of people still use wep, so use your own judgement.

---

### Post by mbarvian on 2008-06-21
how could I change it to wpa?

---

### Post by treymul on 2008-06-21
change the wireless settings on the router, but again, i dont think the modified drivers can handle wpa.

---

### Post by mbarvian on 2008-06-21
> **treymul said:**
> change the wireless settings on the router, but again, i dont think the modified drivers can handle wpa.

ok, well I'll give ndiswrapper a shot after a switch to wpa, I just need to figure out how to do that... 

Not very good with wireless networks, does anyone have any good links for a newb like myself? :confused:

---

### Post by treymul on 2008-06-22
google the make and model of your router and you should be able to find an online manual for it.  type 192.168.1.1 into the address bar of your web browser and see if it brings up your router setup.

---

### Post by mbarvian on 2008-06-22
well, I have a wap54g v2 wireless access point, which apparently does not support wpa encryption.  Now what?:confused:

---

### Post by mbarvian on 2008-06-22
> **chili555 said:**
> Please open up System->Administration->Synaptic and install *build-essential, linux-headers-generic* and *linux-source*. These are all 'generic' packages that will pull in the exact requirements according, mostly to your running kernel. As well, as updates come along, they will be applied to your system.

Once that is done, open a (Applications->Accessories->) terminal and change directory to the folder that was created when you extracted the tar.gz. Now for a bit of magic: enter in the terminal, *cd Desktop/rtl8* and now press Tab. The rest of the file name will be filled in for you. This assumes you downloaded the file to your Desktop.

Next, some ape has written a pretty fair post #12 here: 
[http://ubuntuforums.org/showthread.php?t=782299&highlight=jadams&page=2](http://ubuntuforums.org/showthread.php?t=782299&highlight=jadams&page=2)

Please let me know if you get stuck. The included README is your friend.

I do not see build-essential or linux-source in synaptic, could that be because I have no working internet connection other than wireless?  I do see linux-headers-generic, but it appears that it is already installed.:confused:

---

### Post by mbarvian on 2008-06-23
OK, scratch that last post.  I was able to connect via wired connection, and installed the correct packages.  However, I am still having the same errors as before after cd'ing to the right directory and ./wlan0up?  At first it says permission denied, so I try sudo ./wlan0up and it says Bash: command not found.  :confused:  I know that it is possible to get this card working (somewhat) in linux, but just have no clue where to go from here...

Any help?

---

### Post by chili555 on 2008-06-23
While you are in the correct directory, verify that you can see *wlan0up* with *ls -l*, please do:```
sudo su
./wlan0up
```Let us know.

---

### Post by mbarvian on 2008-06-23
> **chili555 said:**
> While you are in the correct directory, verify that you can see *wlan0up* with *ls -l*, please do:```
sudo su
./wlan0up
```Let us know.

Well, Here is the outcome of all that:

```
maxwell@maxwell-laptop:~$ cd /home/maxwell/Desktop/rtl8187b-modified/
maxwell@maxwell-laptop:~/Desktop/rtl8187b-modified$ ls -l
total 56
drw-r--r-- 3 maxwell maxwell 4096 2008-06-23 08:16 ieee80211
-rw-r--r-- 1 maxwell maxwell   54 2007-08-22 03:21 ifcfg-wlan0
-rw-r--r-- 1 maxwell maxwell  196 2007-09-27 12:24 install
-rwxr-xr-x 1 maxwell maxwell  124 2007-08-22 03:21 makedrv
-rw-r--r-- 1 maxwell maxwell  681 2007-10-11 15:35 README.FIRST
-rw-r--r-- 1 maxwell maxwell 5117 2007-08-22 03:51 ReadMe.txt
-rw-r--r-- 1 maxwell maxwell  538 2007-08-22 03:46 release_note
drw-r--r-- 3 maxwell maxwell 4096 2008-06-23 08:16 rtl8187
-rw-r--r-- 1 maxwell maxwell  294 2007-08-22 03:21 wlan0dhcp
-rw-r--r-- 1 maxwell maxwell  471 2007-08-22 03:21 wlan0down
-rw-r--r-- 1 maxwell maxwell   75 2007-08-22 03:21 wlan0rmv
-rw-r--r-- 1 maxwell maxwell  611 2007-10-11 15:35 wlan0up
drw-r--r-- 6 maxwell maxwell 4096 2007-08-22 03:52 wpa_supplicant-0.5.3
maxwell@maxwell-laptop:~/Desktop/rtl8187b-modified$ sudo su
root@maxwell-laptop:/home/maxwell/Desktop/rtl8187b-modified# ./wlan0up
bash: ./wlan0up: Permission denied
root@maxwell-laptop:/home/maxwell/Desktop/rtl8187b-modified# 



```

---

### Post by chili555 on 2008-06-23
```
sudo chmod +x wlan0up
```

---

### Post by mbarvian on 2008-06-24
that did it, thanks again chili555 and everyone who has contributed!:)

---

