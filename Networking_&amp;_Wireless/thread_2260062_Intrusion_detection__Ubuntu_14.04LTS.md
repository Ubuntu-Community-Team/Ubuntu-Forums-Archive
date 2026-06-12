---
title: "Intrusion detection  Ubuntu 14.04LTS"
date: 2015-01-09
forum: Networking &amp; Wireless
---

### Post by MikeMecanic on 2015-01-09
UNDER HP-610-1130F Someone is on MY COMPUTER SINCE QUITE A WHILE. I try many things so far but the intruder still there and make me feel so.  Don't have a router, took out the WIFI board RT5392,disable IPV6,erase many things regarding desktop managements and secret code service, erase Ubuntu One and the passwords file, disable port 135,139,445,23;when to iptable and disable many ip addresses, _erase the Ethernet connection 60 time_s,study the log files in system log and so on.  There still on my back.  Install Angry Ip scanner not helpful at all.  When to Network Tool: Trace route my ISP IP address to block USA IP addresses (10.248.140.129...) but there back each time I reboot...  When in the terminal and try several things.  I am working since a week but need help!  I erase so many things that my computer runs on one leg. **Lets make it very clear: my desktop is double somewhere by someone. ****So, the question is: How can I block unnecessary ports and disable incoming IP addresses permanently and/or sniff the incoming intruder.  Thanks in advance!**

---

### Post by QIII on 2015-01-09
Hello!

Exactly *what* leads you to believe someone is accessing your computer?

---

### Post by MikeMecanic on 2015-01-09
The list is pretty long 
 **How can I block unnecessary ports and disable incoming IP addresses permanently and/or sniff the incoming intruder**

---

### Post by Elfy on 2015-01-09
Doesn't matter how long the list is.

Without it people are not going to be able to help you properly.

The first course of action being to help you ascertain whether your machine actually has been hacked.

Of course, if it has and you are completely sure then what you need to do is completely reinstall.

---

### Post by kpatz on 2015-01-09
First step, if you know you've been hacked is to reinstall, and setup the firewall (ufw or iptables).  Avoid installing services you don't need that listen on ports.

Next, get a router and connect it between your computer and your cable/DSL modem or whatever provides your Internet service.  This will add another layer of protection (NAT) between your computer and the outside world.

If you have an extra hard drive, and want to do some forensics to find out what they did, pull the drive out of the hacked machine, and put a new drive in before reinstalling.  Then put the old drive in a USB enclosure and connect it up (but don't run any executables on the old drive).  Mount it with nodev,nosuid,noexec options.  Then you can examine the logs and such to see what happened.

---

### Post by MikeMecanic on 2015-01-09
Chilly north east coast wind


The answer is not easy to explain shortly.  Keep in mind that on my side, I try to isolated an Ubuntu component that permits the intrusion of a person that knows very well the Linux infrastructure.  I didn't succeed!  The sequence is divided in 5 steps and implies network security issues. 


A second question remains:** I have on my computer a desktop remote manager, were is it? ** Was it installed via the WIFI path or the wire path?  Do they need to install one to access my desktop?  The remote is invisible and it can also be visible cause I saw them closing the HTTP connection and open the dash board.  The sequence is: see (above) INTRUSION DETECTION 2 : WAKE UP CALL

---

### Post by MikeMecanic on 2015-01-09
1) Have a HP all-in-one PC with a WIFI on board (RM5392) that I never used.  I deleted the WIFI account 3 weeks ago and took out the board last week. 2) I notice network problems in November.  The Ethernet connection eth1 was renamed auto Ethernet (by I don't know who) while Ethernet connection1 was still visible in the network connection wizard beside the clock.  To access Internet, I had to click on both: Ethernet connection1 and Auto Ethernet.  Here it seems like 2 connections are running at the same time?  I complain to my ISP that traffic was slower: speed test reveal nothing (10Mbdown/1.5up). Much more slower under Opera: Turbo had no effect.  


When we create an Ethernet connection (wired) it's auto Ethernet that appears instead of Ethernet connection1.  I deleted the auto Ethernet account and reboot the machine. By default, Ethernet connection1 should appear but it's auto Ethernet that reappear.  Here I fool around: Unplugged the PC, the cable modem, the phone modem (TekTalkBox), reset them to factory setting.  
3) I decide to create a second connection Ethernet connection1 (eth1) and delete auto Ethernet and it finally work on reboot.  Today, after 2 mounts I'm at Ethernet connection60, I have 3 in advance: a bus of new connections.  I delete one every time I access the web.  But the access remains very slow: the icon (beside the clock) to connect reacts very slowly.  It's even worst to disconnect:  I have time to shut down the computer and check what is still running.  Surprisingly, one day, VM ware not installed (12.04 to 14.04 deleted) is waiting to shut down, same for VM Player.  When I saw that I erase VM Player thinking they were accessing my desktop via the player.  Not at all!


4) The WIFI board is still in the machine didn't touch nothing yet.  In the system log, (OFFLINE) no physical activity of network (eth0 and eth1), someone under the name of Skynet (neighbours?)attempt to connect (never used the WIFI connection).  I reacted immediately by enabling the WIFI connection and deleting Mr.Skynet.  It came back on reboot.  Disable in the bios the network on bootup: no effect.  Try the RF switch in the terminal, it had no effect: Disable by RF switch, enable by state file. 


5)I deleted my WIFI account: no effect.  Mr. Skynet knows now that I'm aware of the manoeuvre because I kick I'm out a couple of times.  Finally, I took out the WIFI board and Ethernet connection40 became eth0. **That's how big brother works!**  **But what he knows now, is that I'm much more curios than he fought.** 


I don't feel to reinstall Ubuntu, I feel more like throw it away: HP don't support Linux and the bios upgrade is 4 years old.  Best regards, from Montreal, Canada.
P.S.:  My software Updater is disable since a week: I have too many components missing.  Still running quite well..

---

### Post by MikeMecanic on 2015-01-09
[COLOR=#000000]Chilly north east coast wind[/COLOR]


[COLOR=#000000]The answer is not easy to explain shortly. Keep in mind that on my side, I try to isolated an Ubuntu component that permits the intrusion of a person that knows very well the Linux infrastructure. I didn't succeed! The sequence is divided in 5 steps and implies network security issues. [/COLOR]


[COLOR=#000000]A second question remains:[/COLOR]** I have on my computer a desktop remote manager, were is it? Was it installed via the WIFI path or the wire path? Do they need to install one to access my desktop? The remote is invisible and it can also be visible cause I saw them closing the HTTP connection and open the dash board. The sequence is: see (above) INTRUSION DETECTION 2 : WAKE UP CALL**

---

### Post by slickymaster on 2015-01-09
Threads merged.

Please do not create duplicate threads, it dilutes the community&#8217;s efforts to provide support and causes confusion.

---

### Post by grahammechanical on 2015-01-09
So, you are in Canada and you are seeing Skynet as a Wifi access point. Perhaps one of your neighbours has a contract with this company

[http://skynetcanada.com/](http://skynetcanada.com/)

I live in London and my WiFi adapter is right now detecting 10 WiFi access points in range apart from my own WiFi router. Think about it. WiFi = Wireless Fidelity. We have on our computer a wireless/radio transmitter and receiver. So, we are going to detect wireless transmissions that are in range and are in the frequency range that wireless adapter transmits and receives on.

To gain access to my machine someone has to be in range of my router and they have to make a connection to the router. But there is a pass phrase that is required to authenticate the connection. And I can change the pass phrase from the default to make things more difficult.

I cannot access the WiFi routers of my neighbours because I do not have the correct pass phrase. Besides, I am a good neighbour.

It is also possible for someone to "listen in" on the radio transmissions between the router and my machine. But I am using encrypted transmissions. All things are possible but not always probable.

If we switch off the WiFi adapter or remove it as you have done and If we unplugged the ethernet cable from the router or switch off the router or disconnect the telephone line from the router then no one can gain access to the machine unless they are actually sitting at the keyboard.

I can go to Connection information and find out the Hardware Address  of both my Ethernet and WiFi adapters. I can then use a web browser to access the setup program in my router and find out the physical address of the devices that are connected to the router. In this way I can find out if my machine is not the only machine accessing the router.

I am connected by both ethernet and wireless to my router but right now the router setup utility is showing no devices connected to the router by WiFi and it shows the correct hardware address for my ethernet adapter and even the name that I gave to this machine when I installed Ubuntu.

So, I know that no one is accessing my machine by using a Wifi connection to the router. The sites that we can connect to on the internet and the software that we can download from the internet are a completely different source of possible malicious attacks.

Regards.

[https://wiki.ubuntu.com/UncomplicatedFirewall](https://wiki.ubuntu.com/UncomplicatedFirewall)

[https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)

---

### Post by Irihapeti on 2015-01-09
Did I see a mention of remote desktop? That is quite likely the problem. It's probably the most common reason I've seen for Ubuntu desktop machines getting hacked, in the years I've been on these forums. It's not enabled by default, but it seems that it's extremely easy to turn it on without meaning to. It's one of the first things I get rid of when I do a new installation.

Remove it using the command
```
sudo apt-get remove vino
```

If you're still having difficulties, then follow the suggestions of several other posters and reinstall. Then remove vino.

---

### Post by MikeMecanic on 2015-01-09
First, the RF kill process must be simplified and some actions must be redesign immediately:  Red Flags


In search of the failure and to know if they were using a component in Linux to duplicate my desktop, it appears that it's by Wine that they get in and/or by the terminal. To be confirmed? Please answer my question: where is the remote software in my PC or by which port they get in?  Used to be much more better at debugging Windows then Ubuntu, but since Ubuntu 10.04 I'm getting better every day:)


RK Kill, erase and disable many processes, discover many things that I wish to share with the community.  Hoping that Ubuntu would be a more efficient O/S.  I discuss here, above and below some of the actions that I took not only in search of a potential network failure, but above all on behalf of privacy and Internet security issue.  The main action was and is still to kick them out of my computer even on one leg (need your help).  I succeed in one path: The WIFI path is deadly dead and in the network manager (log file) there is only one path that I was not able to kill or disable: the Wimax path.  This port seems to open or alive all the time?


1) Bluetooth and Bluetooth D. Not install but log file indicates Radio Frequency Switch (RFSw) enable, enable by state file.  So I search for it:  In the dash board there is a dead window indicating that is was never installed in the pass.  RF kill it in the terminal: No effect, still enable.  Discover Bluetoothd in the system monitor on listen mode.  The only way to kill it, is clicking stop process (never seen it after). The 2 others options allow Bluethootd to be up on boot up (listen mode).  Bluetooth is a dangerous device for an intruder:  It allows to listen outside the room.  In my case, the mic is off bias since day one:  Wire badly connected, I left it the way it is when removing the WIFI board: thank's god that regarding my microphone, It's Friday every day. 2) IPV6;  Seen it disable only ounce.  Rf kill it a couple of times and apply ignore mode in Ethernet setting.


3) WINE:  My number one suspect with the terminal.  But it was too late: I try to erase it several time in the pass year.  I don't like that kids fool around with Wine: Telling them that nothing they know runs on Linux is not enough.  IN THE DASH BOARD, the uninstall process doesn't work.  What's up?  We must absolutely pass by Ubuntu One to erase it?  A set of corrections must be applied immediately:  The most dangerous software in the Linux environment.  Wine integrates windows architecture to run on Linux:  An intruder paradise.  Plus any one in front of the computer that install a Windows program without properly reading the installation pop-ups can destabilize the O/S.  This application should be password protected (8 Characters) with a bell (tone) set to medium-high (internal speaker and all others audio outputs). 


4) The same applies for the terminal: the heart of the computer.  Any one in the house should be able to ear the activation of the terminal; in all cases, even with a desktop remote manager, even on screen save mode (IT IS EXACTLY HERE THAT THEY GET IN: meditating on [www.Radio](www.Radio) Swiss classic with the screen saver on).  This is my number one suspect.  What is that pseudo-setup indicating a bell in the terminal?  There ain't no sound at all on my machine since Ubuntu 10.04LTS but there's a tone on boot up (Internal speaker works).  5)  Ubuntu One:  All the programs are installed there.  The equivalent of add/remove in Windows.  Suspect many components especially the desktop ones.  I erase many programs and at the end I erase Ubuntu One.  I also discover the existence of a secret service or a secret code that drive me forward to erase more components.


Still, after all you've been reading here, above and below, Ubuntu 14.04LTS is running very good (more stable that it was under 10.04 version): any, any fatal error at all.  It appears that none of the Ubuntu components were involved to duplicate my desktop.  Only the boot up sequence change, I now have the text file in.  Ubuntu acts like a first class O/S and slowly but surely on is way to push Windows8 at the level of a third class O/S.
I hope that my work will help Linux to perform in a more secure manner and efficient way.  Sincerely,

---

### Post by cariboo on 2015-01-09
Merged another newly started thread.

---

### Post by MikeMecanic on 2015-01-09
Ouf!  Your telling me  that there in my computer since more time than I expected.  Thanks for the advice.  The way to prevent that is to take out the radio frequency board: Wifi

---

### Post by MikeMecanic on 2015-01-09
Ouf! Your telling me that there in my computer since more time than I expected. Thanks for the advice. The way to prevent that is to take out the radio frequency board: Wifi

---

### Post by MikeMecanic on 2015-01-09
Thanks Appreciate and I already remove Vino.  I'm not gonna re install yet.  The only difficulty was to kick them out and I succeed many times

---

### Post by kpatz on 2015-01-09
Make sure x11vnc isn't installed either.  That's another popular remote desktop tool for Ubuntu.

I'd get a router or at least set up ufw.

---

