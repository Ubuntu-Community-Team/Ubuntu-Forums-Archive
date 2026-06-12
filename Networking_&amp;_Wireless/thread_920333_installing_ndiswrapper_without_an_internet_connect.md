---
title: "installing ndiswrapper without an internet connection"
date: 2008-09-15
forum: Networking &amp; Wireless
---

### Post by jammin2222 on 2008-09-15
ubuntu 8.40
My laptop cant connect to the internet at all until i get the Belkin F5D7010 ver300uk wireless notebook network card to function, and to do this i think i need to get ndiswrapper installed and then install the windows driver for my card.

As i cant connect to the internet on my laptop im using my desktop pc's internet connection to download stuff i need. I have downloaded ndiswrapper 1.53 and saved it to a memory stick and transfered it to the laptop that way.

I have followed just about every tutorial on how to install ndiswrapper but something always goes wrong. Either incomplete info/not enough info or assuming you know how to do something that you don't always get in the way of completing the install progress.

Is there a way to install ndiswrapper using synaptic packet manager without an internet connection. can i point synaptic to the zip file and tell it to install somehow? 

I have tried the terminal but something always goes wrong when following a tutorial. 

is there an installer for ndiswrapper?
 
Im starting to loose my mind with all this programming jargon 

Thanks

Ben

---

### Post by issih on 2008-09-15
Go find the cd you used to install ubuntu, throw that in the cd drive.

Now go to software sources under System->Administration, and eable the cd as a source (just tick the box)

You should now be able to install ndiswrapper quite happily from there, 

I think the command is:

```
sudo apt-get install ndiswrapper-common
```

But I wouldn't swear to the package name right now

---

### Post by jammin2222 on 2008-09-15
I didnt install ubuntu using a cd. I used wubi to download/install ubuntu 8.40 from windows xp.

---

### Post by tarps87 on 2008-09-15
Try downloading the latests version from:
[http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/](http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/)
(assuming you have the internet on the xp machine) Then use a usb stick to copy it, saying that I think ntfs read only support is default on Ubuntu now so you should be able to get it from the xp partition. Then is just click on it and it will install

---

### Post by jammin2222 on 2008-09-15
i have got a copy of the ndiswrapper file saved on my laptop, i just cant figure out how to install it.

 if i click the icon it asks me if a want to extract it. so i did. then when i click on it, it opens a folder with lots of icons, none of them will open when i click on them.

 There is one read me file that tells me how to install it, but it assumes i know how to use the terminal and what its saying to do dosent make sense to me. 

i have a zipped file called 

ndiswrapper-1.53.tar.gz

and after extracting it i have another folder called

ndiswrapper-1.53

how do i install it? in idiot proof language if posable

whan i click on start.exe  it says "There is no application installed for this file type."

What am i doing wrong?

Thanks 


Ben

---

### Post by tarps87 on 2008-09-15
Where did the start.exe come from?
The easiest option is to follow the link download the file:
ndiswrapper-utils-1.9_1.52-1ubuntu1_i386.deb, you may need the common .deb as well but we'll see.
The .deb is a Debian package , like .exe for windows.
Hope this helps

---

### Post by jammin2222 on 2008-09-15
ok i followed the link and downloaded ndiswrapper 1.52 and copied it over to my laptop, still dont know how to install it. it looks the same as the 1.53 version i downloaded. 

what do i do with the ndiswrapper 1.52 zip file?

---

### Post by tarps87 on 2008-09-15
Does it end with .deb not .tar or tar.gz? You should be able to double click on it and a window will appear with an install button in the top right

---

### Post by issih on 2008-09-15
First things first...tar.gz files are just archives...like .zip in windows (although we have .zip too) its simply a compressed file containing other files, nothing more nothing less.

When you click on one of those ubuntu will give you the equivalent of winzip or similar so you can see whats in there, and the option to extract the files.

The first download you got was almost certainly nothing more than source code inside the archive. This is relatively common practice, but you need to have various extra packages and a fair bit of knowledge to compile the code into a useable program.

Instead you need to be looking for .deb files (as suggested above) these are more akin to the .exe files of windows and install simply by clicking on them.

Be warned however that you are going about this whole thing the wrong way round. Ubuntu uses a package management system that relies on repositories of precompiled software. If you want to install something you ask the package manager (apt or synaptic) to install it. The package manager then installs the required program and any libraries/subprograms it is dependant on.

By sticking to a windows mindset and going out hunting for separate standalone debs and installing those, you are likely to eventually run into dependency issues (although there are ways around that)

It is much much simpler if you can simply jack into a hardwire internet connection for the time necessary to sort out your wireless connection, if that isn't feasible, then the .deb file from the website already suggested is your best bet

---

### Post by jammin2222 on 2008-09-15
unfortunately i cant hardwire my laptop into my router as it dosent have a LAN socket, it only has 2 usb slots a parallel port and two pcmcia slots. 
Life would be simple if i could just plug in a cable...

I found the .deb file, clicked on it and its now it says ndiswrapper is installed. I guess i need to install the windows driver now but am stumped once again.
I have saved the windows driver onto the laptop but need to know what to do with it. 

Also i have no idea how to configure ndiswrapper as there dosent seem to be an entry in any of the menus relating to ndiswrapper.

 I don't know what i was expecting really, I guess i was hoping it would be a case of opening ndiswrapper and point it to where i saved the windows driver and bish bash bosh jobs a good un. but no thats too easy says the programmers lol
What do i do now ndiswrapper is installed?

Many thanks for be patient with me

Ben

---

### Post by tarps87 on 2008-09-16
This link will explain how to set it up:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
If you want to use the command line follow step 3.4.2
```

sudo ndiswrapper -i ~/drivers/drivername.inf

```
In this code ~ is your home drive, its short for /home/<username>
(Pressing tab will auto complete command/ filenames)

If not you can use this to install this gui package
[http://packages.ubuntu.com/hardy/net/ndisgtk](http://packages.ubuntu.com/hardy/net/ndisgtk)
Once this is installed you should be able to navigate to the .inf file and select it.

I hope this helps, if you get stuck on any part post back and I'll see what I can do

---

### Post by jammin2222 on 2008-09-16
sorry guys im truly stumped.

Im almost at the point of giving up. I have installed ndiswrapper, tested the installation like it said and all looks to be installed.I have black listed what it told me to. I have installed the gui package and pointed it to the windows driver .inf file but it still wont work. 

I have read everything related to my F5D7010 wireless network card, i have followed this tutorial to the letter [https://help.ubuntu.com/community/Wi...er/Ndiswrapper](https://help.ubuntu.com/community/Wi...er/Ndiswrapper) and still cant connect to my network.

I can see my networks name in the top right hand corner of the screen, the lights are on on my card. when prompted for my network key i enter it then click connect, wait for a few mins and the network key box pops up again asking for my network key again! Im locked in a circle of uselessness.

I don't know what else to try. my card should work as it is mentioned in several places.

should i uninstall Ubuntu to get rid of the mess that i have created by typing stuff i have no clue about into the terminal? Im sure i messed something up somewhere, its not exactly straight forward now is it?

why is it so hard to install a driver?

the problem is probably between the computer and chair, but really should it be this complex?

or is it just a fact that my laptop is a heap of junk?



Many thanks

Ben

---

### Post by tarps87 on 2008-09-16
If you can see the network and talk to it, it should be working. It could be a problem with the wireless key. Check it is using the same type of key (wep/wpa)
One thing to try is if you have access to the hub remove all encryption/keys try to connect. If it connects it the key if not it is probably something else, don't forget to turn all the security back on as soon as you've tried (If you do try it)

Most drivers are built in to the kernel, the problem is some manufactures aren't keen to let people see in their drivers. The Ndiswrapper is an attempt to solve this problem and is a very good one but the ideal would be to have the support build into the kernel. The more open source OS's are used hopefuly there will be more support from hardware manufactures. I have been lucky in which out of three laptops two worked "out of the box" and the third had a pci-expansion wireless card and worked with Ndiswrapper.

Its just twigged that the pci-expansion wireless card I was talking about is a belkin and it possibly the same card. I will have to check but I know its the one the shortest range. I will post back when I get a chance to check it.

Try checking your access point for mac-filtering as well. I think I have had problems using wep before but it is working fine with wap2.

---

### Post by tarps87 on 2008-09-16
Just to confirm the card is a F5D7010, using the xp driver from the CD. Green light on, yellow flashing when in normal operation.

---

### Post by jammin2222 on 2008-09-16
Thanks for sticking this out, im completely retarded, or at least thats how i feel.

I have already tried disabling the encryption but it still dose not connect.
 
yes it is the F5D7010 but its only got two green lights, one is on all the time the other flashes like crazy when using windows but is lit 98% when in Ubuntu. 

also now after all my tinkering and following the instructions to blacklist certain files the wireless card dose not load up when i boot anymore. 

what a mess

I really cant be bothered to try and re enable the wireless card to be honest, but part of me is saying don't give up.

i think i will give up for now though, i have been doing nothing else but try and sort this out for at least eight hours a day since Saturday and its Tuesday night now.I have been reading this forum for so long it has burnt the tabs from my web browser onto my flat screen. :-k

Unless there is a phone line i can call and somebody can talk me through it from scratch i don't think i will ever manage it.

Your help has been really appreciated though as i would never of even got this far without it.

I haven't ever tried uninstalling Ubuntu yet. I used wubi to install it, I hope its as easy as several youtube videos made it out to be. 

At least my main desktop machine using Ubuntu works 98% great and who knows, the next distribution might come with the right driver. 

Many thanks once again

Ben

---

### Post by jammin2222 on 2008-09-17
Im glad to say i made some more progress today. :guitar: I Only just remembered when i woke up this morning that when i setup my router 2 years ago i had to change the wireless channel to a different number because it was interfering with the cordless phone and my wireless cctv camera.  
 
I uninstalled Ubuntu and reinstalled it, and the card lit up like it use to.

I changed the wireless channel on my router back to the default number 11 and entered my network key and im online now.

why didnt i think of that earlier...Im still kicking myself in the face right now. I have already punched the living daylights out of my nuts, and after i finish writing this ill go and head but a brick wall for the rest of the day for being so stupid.  :redface:

the only thing is now im back on channel 11 the cordless phone and wireless camera are playing up. 

All i need to figure out now is how to change the wireless card in my laptop to a different channel?  Any Ideas? i cant find any options for it anywhere.

Im such a Fool

Many thanks

Ben

---

### Post by tarps87 on 2008-09-17
Lucky you remembered, I would have never thought of that

I think this should do it:
```

sudo iwconfig wlan0 channel <number>
```
where:
wlan0 is your wireless interface
<number> is the channel number

I can't remeber how to find out interface name, it may be listed in ```

ifconfig
```

There is also some info here:
[http://ubuntuforums.org/showthread.php?t=172810&page=2](http://ubuntuforums.org/showthread.php?t=172810&page=2)

---

### Post by jammin2222 on 2008-09-17
Thank you very much for all your help, i will have to try your last suggestion later on tonight when i get home from work.

ill leave it on downloading updates at an incredibly slow speed while im out, and hopefully ill be running internet at normal speed when i change the channel later to avoid the interference. 

thanks once again

Ben

---

### Post by jammin2222 on 2008-09-18
Me again, i have tried to change the wireless channel as you mentioned but no joy, now i am connected though All be it a 1 Mbps its easy for me paste what the terminal is saying.


ben@ben-laptop:~$ sudo iwconfig wlan0 channel 13
Error for wireless request "Set Frequency" (8B04) :
    SET failed on device wlan0 ; Invalid argument.
ben@ben-laptop:~$ sudo iwconfig wlan0 channel <13>
bash: syntax error near unexpected token `13'

I didnt post the results of ifconfig as im not sure if showing my ip settings is a good idea? but there was a part relating to dropped packets and errors that all reported 0

What can i try next to change the frequency?


many thanks 


Ben

---

### Post by tarps87 on 2008-09-18
I have just tried it, try:
```
sudo iwlist wlan0 c
```
I only have channels 1 to 14.
If you know the frequency you can use
```
sudo iwconfig wlan0 freq <x.xxxG>
```
x.xxx = your frequency
If this does not work can you try another channel?
the iwlist command will show you other frequency's, also
```
sudo iwlist wlan0 scan
```
will give you a detailed list of all the routers it can see. including channel numbers and frequency's

---

### Post by jammin2222 on 2008-09-18
Thanks once again for your help :) This is kind of weird but there isn't a channel 13 listed lol. thats probably why couldn't change to that channel. There is a channel 13 in windows though :confused: I will have to try using the other end of the frequency range i guess.

 Also I only have a 1Mb/s connection speed reported in the connection information and in the following results it has a list of bit rates. can i choose 54Mb/s some how, or is it on 1Mb/s because there is a problem?

the results are as follows: 


ben@ben-laptop:~$ sudo iwlist wlan0 scan
[sudo] password for ben: 
wlan0     Scan completed :
          Cell 01 - Address: 00:11:50:80:49:44
                    ESSID:"Belkin54g"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=54/100  Signal level=-33 dBm  
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=0000001dbf5ef3b3

ben@ben-laptop:~$ sudo iwlist wlan0 c
wlan0     11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency=2.462 GHz (Channel 11)

ben@ben-laptop:~$ 



Much thankings once again



Ben

---

### Post by wise-tangerine on 2009-01-03
I read somewhere that there are 3 slightly different standards for wireless devices, which affects the range of available frequences and therefore the nubmer of available channels. It's like the American standard defines only 11 available channels (1-11), the European smth like 12, and the Japanese standard defines 14 of them. By default your system is probably configured to work within the range of the American standard, which means only 11 channels.
I suggest trying another channel, between 1 and 11. Later on, if you manage to get things up and running, you may want to google in order to find out how to change your system's wireless preferences in order to allow it to connect to the whole Japanese range. I'm pretty sure this can be  done, but not with the regular gui config tools.
Hope this helps.

---

