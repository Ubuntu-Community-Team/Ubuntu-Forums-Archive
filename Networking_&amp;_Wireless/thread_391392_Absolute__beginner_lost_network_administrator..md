---
title: "Absolute  beginner lost network administrator."
date: 2007-03-23
forum: Networking &amp; Wireless
---

### Post by rpaco on 2007-03-23
I have just (2 days ago) installed Ubuntu desktop edition 6.10 om my home pc. this is an AS Rock MB wiht VIA chipset and includes an onboard VIA Rhine II lan connecton. My Gome  virtual device manager adds the Prefix VT6102 to description but this does not aqppear in the windows devmangr.  

I made a cd from this site and installed on a separate hard disk to my windows system. All is fine except I cannot connect to the Inet. 

I have a separate Lynksys ADSLMU2 DSLmodem/1 port router, this is permanently on and connected to my pc via an ethernet cable. It works fine in windows and I cannot see how it can be affected by the pc (I am using it now via windows to send this). 

I have followed the help file instructions up to the point where it says "your network administrator will advise" I've looked in all my cupoards at home but he seems to have done a runner"

Now when I go to Admin>Network the Bug Buddy immediately tells me the network has crashed and it has made a report to send which it then cant because the network is not connecting me to my modem. 
HOWEVER If I go to Network Tools I can ping the bbc and F9 (MY ISP) and get proper responses. I can also traceroute ok, so 
"bits" are working,  If I select "configure" the bug buddy cuts in immediately again.

SO please advise a complete network moron how to A) stop the bug buddy interfering and allow access to the network setup. and B) set the network up.

I realise that is probably because I put the wrong address or DHCP in or something, my modem has a DHCP (or similar) and a DNS in cluded in it which again works vey well in windows.

I was brought up on DOS but never got to networks; as is obvious to those of you now laughing or sighing at my ignorance. I throw myself upon your mercy.:)

---

### Post by chili555 on 2007-03-23
I will be glad to help you kick off your new part-time, 10 minutes a week, career as Network Admin.

Sometimes the hardware detection and required module (called "driver" in the old world) insertion doesn't go perfectly, especially in a new system. Sometimes we have to shake the module to wake it up.

Your Via Rhine is supposed to work with a module called: via-rhine. Let's open up a terminal and do:```
sudo insmod via-rhine     <- successful if no output from terminal
ifconfig
sudo dhclient eth0
```Sometimes, I have seen modprobe work instead of insmod and vice-versa. Try both. All of this assumes that insertion of the module wakes up your card, an eth0 interface is created, and then you can ask eth0 to go get an IP address. If you get something like: ```
DHCPACK from 192.168.1.1
bound to 192.168.1.112 -- renewal in 38027 seconds
```Then you know you are good.

---

### Post by rpaco on 2007-03-23
Thanks Chili555 however I think 10 mins a week is insufficient, maybe if I have a years worth in one go.

I have tried to do what you said however all I got was file or directory does not exist. 

I did do an ifconfig which i take to be the same as a windows ipconfig and got a listing which you would need to read. However there is no way to print from the terminal. no way to save it to a windows directory so that left screenshot which I took. I then tried to print it but despite having my correct printer driver installed (HP 960c ) all it did was to print a whole page of black and run out my black cartridge. Byt this time I am getting a bit depressed and am in severe dispute with title page of Unbuntu which claims "It just works!" the insertion of only might be more appropraite. 
However I took a pic with my camera and having re-booted back into windows am now able to attach same. (IMG_1440.jpg 577KB)
If you have time and patience please advise further.
You are obviously an old hand at Linux and may care to comment on my impression that Ubuntu was not much quicker to load than windows, which surprised me a lot. I was hoping for DOS type speed. So overall so far I am rather disillusioned at the complexity and depth of knowledge required. A far cry from the impression given in the front pages. Maybe I have to learn unix and networks first. If that is the case then I will reluctantly go back to windows.

---

### Post by rpaco on 2007-03-23
A further thougt is that how can the ping and traceroute work ok if I have put the wrong addresses in the network configuration.

I note many other people on this thread with similar problems.

---

### Post by ffxr on 2007-03-23
i think youve just been unlucky with this issue you have found. chin up.. keep the faith..

i believe we just need to add some DNS servers to your network config.. but we have no netwrok manager as it would simply be a matter of adding them there; so as a workaround we can:


open your resolv.conf file..  by 

```
 gksu gedit /etc/resolv.conf 
```

and add these lines :

```

nameserver 208.67.220.220
nameserver 208.67.222.222 
```


this will add opendns name servers : [http://www.opendns.com/](http://www.opendns.com/)

try that and see if that helps..


btw the you can copy the data in terminal by highlighting it and selecting edit -> copy ... your digital camera workaround was ingenious tho : )

---

### Post by rpaco on 2007-03-23
Ok thanks I will try your suggestion. Will report further later.

Re copying:   Nice, but I will just add that re booting into another operating system in order to access this site rather tends to delete the copy buffer/clip board or whatever its called.

Is there no way I can access windows files in Ubuntu? Even just text would help. No dont bother its probably far too complicated.

Re the printer which did a complete page of black in when it was suppposed to print my screenshot (after checking print preview was ok although unwantedly rotated 90º)  It then printed a Ubuntu test page perfectly.!! Ah well another thread another time maybe.

---

### Post by ffxr on 2007-03-23
lol.. oh right .. yes.. forgive my shortsightedness

aye you can access files in windows from unbuntu & vice versa.. 

theres a guide to reading & writing windows files here:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows)

thats good starters' guide to ubuntu generally, if you wanna have a wee look over it..

---

### Post by rpaco on 2007-03-26
Thanks, adding the other DNS did stop the bug buddy thing appearing and I can now get at the network setup again. However to no avail. I have tried all teh addresses I can think of but none makes any difference. 
Did you note on my earlier screenshot that the Rhine-via thingy said bad name or file. does this mean its not installed? I have tried the motherboard manufacturer (AS ROCK) but they dont seem to have any linux drivers. And even if they di I couldnt load them because despite followit the instructions to the letter to enable me to see windows directories thet came back wiht an error as well. Though I did do a fdisk -l and noted the that hda1 is the correct windows disk/partition. 

Well Im hoping my son who is a progremmer at IBM can sort it when he comes over for easter. He is writing test thingies for cross platfom apps so he has to know about most o/s s 

But thanks for all the help so far.
cheers
Dick

---

### Post by chili555 on 2007-03-26
According to the screenshot you attached, you have an IP address: 192.168.1.3. Is this because you set up a static configuration in Network Administration, or because you are indeed connected? When you open a terminal and do:```
ping -c3 192.168.1.1
```what do you see? You don't have to take a picture of your screen, just tell us whether you see packets returned, like this:```
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
```If you see packets returned, you are connected. Then try:```
ping -c3 www.google.com
```

I doubt we need an IBM programmer, we just need a tweak or two.> You are obviously an old hand at Linux and may care to comment on my impression that Ubuntu was not much quicker to load than windows, which surprised me a lot. I was hoping for DOS type speed. So overall so far I am rather disillusioned at the complexity and depth of knowledge required. A far cry from the impression given in the front pages. Maybe I have to learn unix and networks first. If that is the case then I will reluctantly go back to windows.I have no frame of reference to compare. Among the six or seven computers (I lose track, and UPS is expected soon with a new Thinkpad), none run Windows.

I think a lot of people run a default install quite nicely with no trouble. Compare the number of registered users on this forum with the number of downloads of all flavors of Ubuntu. I am sure the ratio is quite low. Once you get a bug or two ironed out, you will be bored with how trouble-free and BSOD-free this is. 

You should have been in linux six or seven years ago, in the days of kernel 2.2.x. Everything; display, sound, USB, printer, CDROM AND network had to be tweaked to get running. If you could find a forum, there were about 15 guys in there and 13 of them knew less than you did. You guys have it lucky: install, tweak one, maybe two items with the help of thousands of posts on a forum and you are good to go.

---

### Post by rpaco on 2007-03-27
Ok I will reboot and do that do that, unfortunately the method of accesing windows files from ubuntu didn't work.

I told you initially that i can ping the bbc and my ip (force9) and get results ok.  So I expect the same to work in a terminal.

I should repeat that I am usung a separate Lynksys ADSL2MU dsl modem/single port router which includes DCHP. This is connected to my pc by an ethernet cable, this stays switched on and connected between reboots, I know it is working fine. 

However I also repeat my earlier question if the "Sudo insmod via-rhine" brings forth "no such file" does this not mean that the linux driver for the lan card is not loaded?

Will be back in 10. but I gues its middle of the night over there. 
cheers

---

### Post by chili555 on 2007-03-27
> the method of accesing windows files from ubuntu didn't work.The poster was giving a guide to accessing Windows files on a living system; that is, Computer W is running Windows and is booted up and running and you are on Computer U which is booting up and running Ubuntu. The system he refers to, Samba, allows you to access files from either one to the other. That is not your situation, you wish to access files on the not-booted side of a dual-boot system. You may be able to do it, but it's far more trouble than the old-school grey-bearded Linux/Unix way: use an *actual* notepad, made of paper, and a pencil. The lead end I call "Enter" and the eraser end I call "Delete." Transfers bits of information well.

The failure of the module via-rhine to load is a mystery to me; however, you can ping:> i can ping the bbc and my ip (force9) and get results ok.so some module must be loaded well enough.

You got rid of the bug buddy with better DNS nameservers. So, what is left that you want to configure? Is it time to open up Firefox and get the updates to your system, viral videos, torrents and download MP3s?

---

### Post by rpaco on 2007-03-27
Hi again
Yes I get packets returned both from the internal address and from google. Google is taking about 125ms which is ok the bbc is much closer and the round trip is about 35-40ms.

I have looked at the VIA rhine driver from the VIA website and used modprobe and added a line in /etc/modules.conf  "alias eth0 via-rhine" without the quotes, assumed you are not suposed to put eh quote marks in too.

However it has made no difference I still cant connect via Firefox.

I may try the FTP to see if I can reach my website.
cheers

---

### Post by chili555 on 2007-03-27
I think if your machine will ping OK, the right module is loaded. It may not be via-rhine, but it works. I would *sudo gedit /etc/modprobe.d/blacklist* to add the following on its own line.```
blacklist ipv6
```When you reboot, see if eth0 is working, that is, if you can still successfully ping. Then try Firefox and see if it's faster. Post back and let us know.

---

### Post by Zoandar on 2007-03-27
Re:
"You guys have it lucky: install, tweak one, maybe two items with the help of thousands of posts on a forum and you are good to go."

I must say that it is not going that way for me. I have spent all day on several forums trying all sorts of things and still cannot get my HP DV1000 notebook running Ubuntu 6.10 to produce sound from the recognized Intel ICH6 chipset. 

Now I have hit yet another snag, and cannot edit a file as suggested, because it says I don't have permission to edit the alsa-base file as suggested.

I am the only user on this system. How do I become the administrator?

I would strongly disagree with anyone who says Linux is now "easy to install and get working".

Larry

---

### Post by chili555 on 2007-03-27
```
sudo gedit <your_file>
```

For security, ordinary users are not allowed to edit configuration files or install software. So, if you, the only user, need to do so, you need to temporarily get Super User privileges. 

Sort of stops viruses, spyware and malware dead in its tracks, doesn't it? They don't know your password and you aren't about to give it up. In my opinion, that, among a few other reasons, is why viruses are all but unknown in linux; they are very difficult to implement because of those darned passwords.

Windows would be 90% more secure if users logged in as users, not administrators, and used secure passwords.

---

### Post by rpaco on 2007-03-28
Chilli
Your reply of 2 or 3 ago seems to have been out of sequence, telling me to open up Firefox and dowload updates is a little out of place when my original and still current problem is that I cannot connect to the internet. The fact that I can ping and get results does NOT connect Firefox to the internet. This was the whole of my problem, I told you #I( could ping right at the start, had youread the beginning of my thread. 

The other fact that I cannot get at the files I have in my windows system which would have helped me here ( ie the updates and the via driver and a linux version of Skype) is another thorn in the side.  I have to reboot into windows to contact the internet pinging is not helping Firefox connect.  And who ever it was who suggested that I copy files out longhand I forget your name ( luckily) I have a suitable comment for you but I think it would violate the forum rules.

---

### Post by chili555 on 2007-03-28
When you open Firefox, type [http://www.google.com](http://www.google.com) in the address bar and press enter, what happens?

---

### Post by dannyboy79 on 2007-03-28
in order to help you I will need you to please post some information! Also, please make sure you answer all my questions before posting back as know one likes asking something twice. +Are you going to be using DHCP or a static ip for your ubuntu installation?

+the files that you would like to access on your dual boot computer that are within windows, are they on a fat32 partition or a ntfs partition? 

+Are you going to want to write to a NTFS partition from Ubuntu?

+What is the routers ip address?

+What is the ip address of Windows when you boot to windows on this dual-boot computer?

+Are you using 1 hard drive with both os's on it or do you have Windows on 1 and Ubuntu on another?

+ You stated that you could ping your router as well as [www.gogle.com](www.gogle.com), can you still???


Now please post the output from the following commands entered into a terminal exactly as you see them and no matter how much it returns, please post back everything!

lspci -v | grep Ethernet

sudo cat /etc/resolv.conf

sudo cat /etc/network/interfaces

sudo cat /etc/dhcp3/dhclient.conf
(NOTE: you only need to give me this output if you are using DHCP for your ubuntu box)

sudo iptables -L

sudo fdisk -l
(NOTE: when you give me the results of this, please inform me where each of the OS's are. For example, say /dev/hda1 is where you have windows and /dev/hda3 is where you have Linux)


Now, as long as you answer all my questions and provide what I have asked for we can get you working soon! Talk to you soon.

---

### Post by rpaco on 2007-03-28
Chilli 
Many thanks the blacklist must have done it because for the first time ever I am sending this from Firefox running in Ubunbtu. I did as you said and added the line then rebooted and hey presto. 

Thanks for your patience and although previous responses have not been logical I am just happy that the damn thing works now.

---

### Post by chili555 on 2007-03-28
Super! I am happy we got it going! Good luck and have fun!

---

### Post by rpaco on 2007-03-28
Dannyboy
Thanks I will get back to you later, but now that I have Firefox working I have to install Java to be able to use several of my normal websites. So that will probably take a couple of days at the previous rate. 

Re your instructions, I have no idea what the ip address of windows is. I am using Ubuntu on my old hard disk which is set as slave and HD1 while windows is on a separate HD which is set as master, HD0. As listed in Ubuntu the Windows HD is /dev/hda1 through 8 and Ubuntu is on /dev/hdb1 through 3 (I want to read/copy/write if possible files on windows partition 5 and 6. which are ntfs formatted. I will send all details you asked for later when I retry this. 
many thanks.

---

