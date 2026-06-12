---
title: "[SOLVED] Wireless Belkin (rt73 inside) problems, not connecting."
date: 2007-10-16
forum: Networking &amp; Wireless
---

### Post by The_Marlboro_Man on 2007-10-16
Hello!.

Almost new to the forums and Ubuntu, I had no need to ask any question here until I switched Ubuntu from my laptop to a desktop computer. I had my problems getting the wireless network to work in the laptop but finally managed to connect, even with a WPA key... I would love to explain how I did it but I just mindlessly followed diverse how-tos and was never sure about what I was doing... Anyway, it seemed like something had to be done with the wpa_supplicant.

Now the story is quite different: I just bought an USB Belkin wireless adapter (product number F5D9050, wich seems to have the rt73 components since rt73.sys and bin files are included with the CD). Upon installing the adapter in Windows XP I come across no problems but with Ubuntu I am completely lost... I have followed many how tos, tutorials and read a lot of material, installed a lot of things and eventually reinstalled Ubuntu a couple of times because I didn't know what I was doing and if these things could interfere with each other. 

So here's the problem: when loading Ubuntu I use the Network Manager to find a wireless connection and I click on mine's (thus my wireless adapter *can see it* from the start). A moment after I get a message about an "Error in the requested network, the hardware doesn't provide with the security characteristics" (something like that, only in spanish... Not a lot of sense since it connects on Windows)... My router is under WPA protection so my first bet is that I have a problem with the wpa_supplicant but, does this error happen when trying to connect to an WPA wireless network on a fresh install????.

After installing and configuring the wpa supplicant I start to go crazy: absolutely no wireless networks appear in the Network Manager!!. I start to think about problems with the drivers and try using other software (like wicd) to no avail... Many times I have also installed ndiswrapper to use it with the windows drivers in the CD but had no luck... One of the things that caught my eye was that if I commented added lines on the "interfaces" file I could see my wireless network again (but could not connect with the same error!)... What else?. Oh, yes, I also tried fiddling with the console and I am sure I connected to some stranger wireless network (not sure of how!) but couldn't connect to mine's: most of the time a "scan" of the networks wouldn't return a single connection in the console (though I could see mine's on the network manager).

To sum up, I am confused, I am quite confused. Right now I am installing again as I write to start over again and try to get the thing working but I would like to be helped on this as I know little about Ubuntu. My first questions are: what's really going on?. Do I have problems with WPA and I have to work on that again?. Do I have problems with the device not being properly recognised or managed?. Both?.

Any help is welcome :).

---

### Post by The_Marlboro_Man on 2007-10-16
Not trying to bump the thread, but to bring new information to the table.

Say, I uninstalled the rt73 module that comes with Ubuntu in a fresh install and downloaded, "maked" and "make installed" the ones from SerialMonkey... All with a regular cable internet connection. After that, I logged into the router, disabled the security and left the wireless network open. Going into the Network Manager and manually configuring the wireless network resulted in a success!!!. I just unplugged the cable and surfed a bit on my open connection... So, well, next step should be trying some protected network, right?.

Wrong, hold it there... After protecting the network and plugging the cable again I get no internet connection!!!. That´s it, even with the cable right into the computer I get nothing. The Network Manager doesn´t display a "Cable connection" for choosing but only "manual configuration"... A Windows boot doesn´t work either (!!!) but connecting the cable to my laptop gives excellent results.

I know there should be no way in which Ubuntu could bust the thing but... What could be happening????

Edit: Okay.. All of a sudden the cable works BUT in System -> Administration -> Network there's no wlan interface. Also, "iwlist scan" returns that no interface supports scanning (!). I would have swore that I just connected to my own wireless network... "lsusb" returns the device existing and the wireless network is running (I can connect on my laptop). I am SO clueless!.

Edit: Oh, just another edit... Is it to be expected that the interfaces file appears as 

iface eth0 inet dhcp
auto eth0

instead of
iface eth0 inet dhcp
auto eth0???.

In the file there's also no mention to a wlan1 interface (shown in the iwlist command...), just a wlan0 (that doesn't show at the iwlist command). Could it have something to do that I switched the USB port the interface was in????.

3rd Edit: Kill me... I am wirelessly in!!!.

Okay, it seems that first I have to bring up the interface (that's why I said kill me) and then manually configuring it according to this info I found on the SerialMonkey forums:

iwconfig wlan0 mode managed
iwconfig wlan0 channel 6
iwconfig wlan0 ap 00:00:00:00:00:00
iwconfig wlan0 essid "MY_SSID"
iwpriv wlan0 set AuthMode=WPAPSK
iwpriv wlan0 set EncrypType=TKIP
iwpriv wlan0 set essid "MY_SSID"
iwpriv wlan0 set WPAPSK="MY_PASSKEY_HERE"
ifconfig wlan0 up
dhclient wlan0 

The info has to be extracted from the results given on a "iwlist scan" command :)... Next I need to know if this will work when I reboot and how can I automatically make it happen when I start Ubuntu!. I am adventuring into it right now. Wish me luck... In case it works, I would like to do another post for the users with the same problems :).

---

### Post by The_Marlboro_Man on 2007-10-16
Triple posting... Again, sorry but I got no replies but I though that I had useful information for other users with the same problems.

Anyway, my problem is solved right here. I am writing from my desktop (finally in a desk instead of lying on the floor next to the ethernet cable) connected to the internet with my Belkin USB adapter :) to a WPA protected network

I'd like to sum up everything that I have done to get it working in case anyone else is experiencing the same problem and my experience can serve any purpose. Before explaining it I would like to comment on the results: though I am still running the Network Manager I do not connect "with" it but from the console. The Network Manager DOES NOT see my wireless network in any way and I find no use for it: I just like the "!" sign on the tray, as if something was wrong :P. So, again, everything I have to do to connect I have to do from the console... I copied and pasted the contents to a file and now I only have to copy and paste them to the console itself to connect. I am sure there's an "automagical" way of doing it, I just don't know a lot about Ubuntu.

That said, here's what I did:

-First: I started from a clean installation of Fiesty: no "diswrapper" installed but with wpa_supplicant on it. On this clean installation it seems that the rt73 module (the one in charge of controlling this and some other wireless adapters) has some problems with the adapter so you just get rid of it (I also got rid of some of its friends):

>>sudo rmmod rt73usb

Then, at the end of the /etc/modprobe.d/blacklist file (open it with gedit as "sudo") you add

blacklist rt73usb
blacklist rt2570
blacklist rt2×00lib

I guess that instructs Ubuntu to ignore these modules... Not sure. At this point we should be done with the default interface. Next we get free a free rt73 module from SerialMonkey (gotta love these people :D) at this adress [http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz) and unpack it. You can just unpack it in the desktop with Right Click->Unpack here. Next step is to move inside the folder we just unpacked, we do it from the console. Once inside we move another step into the "Module" folder. Here we have the new modules we have to "compile". It should be easy provided we have the appropriate packages in our system (I read they are "build-essential" and "linux-headers". You can get both with synaptic from the Ubuntu install CD... Just don't give up if you don't get the thing to compile and ask). From the console we do:

>> make

And we get a lot of stuff. I think we should get some warning about a directory not existing and a file being too big.Then, again, from the console:

>>strip -S rt73.ko

When we did "make" we created this rt73.ko file. It is bigger than it should so this strip command makes it smaller. When done we do some console again:

>>sudo make install

And that should install the new module to manage the rt73. Now try running the module from the console with "sudo modprobe rt73". Nothing should happen, try doing "lsmod" in the console and look for a line with "rt73" on it. If it's there the module is loaded. Maybe you'll have to restart when you get to this point... Also, with "iwconfig" on the console you should be able to see the status of the thing...  

Anyway, at this moment the thing should be working. Yeah, sure... Here I was able to unlock my wireless network and access it. Also, at this point the Network Manager stopped seeing my network so I had to left click on it, going into manual configuration, wireless connection and filling up the blanks with the name of my network and such... But my network has to be protected so I won't accept this solution :P.

Oh, I almost forgot, I didn't discover any of these things. I just got them from [http://www.ambientix.org/2007/09/compilar-rt73-en-linux.html](http://www.ambientix.org/2007/09/compilar-rt73-en-linux.html) and some other sources. Thanks guys :).

So, can we connect to an unprotected network (try yours)?. Let's move one more step... If your interface can see the network there should be chances that we could connect to it. First, try on the console:

>>iwconfig

That should bring a list of interfaces and one of them should have "RT73 WLAN"  on it. Write down wich one is it. Mine's wlan1 so anytime I write "wlan1" here just write whatever you have on yours. Next, try this on the console:

>>sudo ifconfig wlan1 up
>>iwlist scan

If everything's okay you should get the interface up (if it wasn't already) and you should also get a list of the wireless networks in your area. Locate yours and then copy and paste all the data from it. For some weird reason my adapter takes a lot until it "sees" a network (until I retrieve a list, in other words) but I can connect right from the start. Just don't ask :S...  Anyway, the list data you got should look like:

          Cell XX - Address: XX:XX:XX:XX:XX:XX
                    ESSID:"thenameofyournetwork"
                    Mode: whatever
                    Channel:XX
                    Encryption key: whatever
                    ....

The adress, channel and ESSID are key elements here. Remember the name of your interface?. We're going to link the interface to that wireless network: run each of these lines on the console. Just replace UPPERCASE stuff with the elements you got from the list.

sudo iwconfig wlan1 mode managed
sudo iwconfig wlan1 channel CHANNELYOUGOT
sudo iwconfig wlan1 ap ADRESSYOUGOT
sudo iwconfig wlan1 essid "ESSIDYOUGOT"
sudo iwpriv wlan1 set AuthMode=WPAPSK
sudo iwpriv wlan1 set EncrypType=TKIP
sudo iwpriv wlan1 set essid "ESSIDYOUGOT"
sudo iwpriv wlan1 set WPAPSK="THEKEYWORDFORYOURNETWORK"
sudo ifconfig wlan1 up
sudo dhclient wlan1

If everything is Ok you should see that the last command brought some lines, one of them talking about the IP you got from the router... Though there's no visual clue we're connected to the internet now :D!!!. Again, none of that stuff is mine, I just got it from the SerialMonkey forums. Thanks a lot!!!.

There's still an issue to adress... When rebooting we lose our changes from the moment we did "sudo modprobe rt73" and we have to type it all over again. Okay, you can add a line like "rt73" to the /etc/modules file and you will have it loaded. Next you should do Iwconfig, iwconfig wlan1 up, iwlist scan... My personal solution (for now) is to copy each line from the console from a succesful connection and paste it to other file, separate each line with a semicolon (;) and just copy+paste it on the console each time. My file looks like this:

sudo ifconfig wlan1 down;
sudo ifconfig wlan1 up;
iwlist scan;
sudo iwconfig wlan1 mode managed;
sudo iwconfig wlan1 channel XX;
sudo iwconfig wlan1 ap XX:XX:XX:XX:XX:XX;
sudo iwconfig wlan1 essid "XXXXXXX";
sudo iwpriv wlan1 set AuthMode=WPAPSK;
sudo iwpriv wlan1 set EncrypType=TKIP;
sudo iwpriv wlan1 set essid "XXXXXXX";
sudo iwpriv wlan1 set WPAPSK="XXXXXXXX";
sudo ifconfig wlan1 up;
sudo dhclient wlan1;

and though when I do "iwlist scan" I get no networks (until some minutes pass) I can just connect from the go.

And well, that's all, more or less... I hope this help other users that could have the same problems that I did. I just got running in less than a day so I guess it shouldn't be hard :). Good luck!!!:

PS: I guess I could uninstall Network Manager now and nothing bad would happen. What I wonder is If I will be able to recreate this from a clean install again. Maybe I'm trying tomorrow!.

Edit: I can confirm that the method works from a clean install... I think that the build-essential packages are needed to compile the module. Also, when certain updates are installed (kernel updates?) the whole process has to be repeated. I guess the original module that we removed is recompiled and the tr73 we compiled is removed.

---

### Post by paxmark1 on 2007-10-19
Hey.  Yeah last July with 7.04 Kubuntu I had no luck whatsoever and the forums were confusing until I went with the serial monkey site.  The blacklisting was important for me also besides bringing wlan0 down and then back up.  Worked very well and now I utilize wep also.

I have a script I run when I reboot to sudo iwconfig the ap, frequency and channel.  I see no need to install Knetwork manager, since it appears others are not getting the RT73 to work out of the box on 7.10.  

I upgraded via command line. Went very well.  After upgrade to 7.10 iwconfig changed one options name  and I had to change frequency to freq in script.  I kept my old /etc/modprobe.d/blacklist - I need to check on that.  Still working like a charm.  

Kernel updates have not caused me any problems since July.  The rt73 is in a seperate module.  

Clean installs?  My mileage has been that if I always install and update with aptitude (I have a script for update and upgrade I run each day) - then I see no dependency problems and then every six months I can just change /etc/sources.list  and then do aptitude dist-upgrade via command line then there are less intermediate things to go wrong during the update.  

Sounds like you are good to go.  Have fun

---

### Post by The_Marlboro_Man on 2007-10-19
PaxMark, thanks, I was indeed ready to have fun but I could not resist switching to 7.10 and then trying it again. The method works exactly as well as it does on the previous release with no problems on my part...

Still, I had to reinstall 7.10 (I don't know how Amarok screwed my playing of media files so much!!) and found that right out of the box I have support not only for my Belkin but also for WPA keys :D!. My smile was enormous but lasted little since something seemed to go wrong  with the downloading of packs like Anjuta, the SDL library or the GStreamer plugins. I reused my old method and then found out that there were problems because I just forgot to instruct Synaptic on which repositories to look at.... I guess tomorrow I'll undo my blacklisting and will try with the Network Manager again.

As for running the thing, I just put all the commands in a file and run it each time :P.

---

