---
title: "Wireless network password changes on restart"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by Im_Original on 2008-08-26
Hello everyone, 

I'm running 8.04, latest updates on an IBM Thinkpad T43. I've never had any problems on this computer that took more than 5 minutes to solve, all the hardware is well supported, etc. But I've been having one problem ever since I installed 8.04, which has me stumped. 

I'm on a wireless network protected by a WEP key, and whenever I turn on my computer, the network password has changed. What I mean is that whenever the computer is turned on or restarted, the password that was previously entered has changed. In the network manager menu where you enter the password, I can see that its length has changed from 10 characters, which is correct, to several dozen. I don't know what it has changed to since the password is only showed as a string of dots. 

In addition to this, sometimes after changing the password back to its correct value, the CPU usage goes to 100% and according to the system monitor, this use is from the system, not the user. This usually happens when firefox is open while changing the password, but it doesn't happen regularly so I can't see any other pattern. After this, the computer becomes slow (of course) but it doesn't freeze, things still work, just slowly. If, at this point, I try to restart, the computer freezes at the shutdown splash screen, after the progress bar is full. 

I did not have this problem on 7.10, on 8.04. 

So, that's it. Any help on this would be appreciated, I don't even know where to start on this one. I searched the forums and found no mention of this problem anywhere else, so I may just have to file a bug report and hope for the best. If nobody has a solution, could anyone tell me where the network password is stored, and how to access it? And how to tell which system process is using all the CPU? If I know where the password is stored, I could try writing a script to check it every time the computer starts up . . . a bandaid solution, but it might work. 

Thanks for reading my post.

---

### Post by Sam Lars on 2008-08-26
It could be that it's changing from your passphrase in regular text to the actual WEP key in hex.  Does it also make you re-enter your password to reconnect?

---

### Post by Im_Original on 2008-08-26
yes, I need to reenter the correct password before it lets me reconnect.

---

### Post by Sam Lars on 2008-08-26
After you try to set it and the system gets slow, is that just for a bit or is it until you shut it down?
You can try looking in Passwords and Encryption under Accessories, the last tab.

---

### Post by Im_Original on 2008-08-26
I'm not sure how long the system slows down for, but I've waited about 5-7 minutes for things to pick up again, and they didn't. After I restart it's fine, except for the password being changed. 

In Passwords and Encryption keys, I looked in the last tab and did see any entry. What am I supposed to be looking for? I thought that that tool was for encrypting data transfers and such.

---

### Post by Sam Lars on 2008-08-26
Well the passphrase for my network is stored in that Passwords tab.  Maybe that's not happening for you?
When the system slows down, is it still trying to connect?  What process does System Monitor say is using the processor?
Could you post the output of
```
lspci | grep Network
```

---

### Post by Im_Original on 2008-08-27
I should have mentioned this, but I only knew that it was a system process because of the color-coded system monitor tool that you can put on the panel in GNOME; it shows a little graph with the CPU use over a period of time with the user, system, nice etc in different colors. When the CPU goes to 100%, it's a system process according to that graph, but I looked in system monitor and didn't see anything. The system monitor only shows processes from the user space, doesn't it? Would it show a system process? I also tried sudo ps -a   and   sudo ps -l, but didn't see anything. 

And as requested: 

$ lspci | grep Network
04:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

---

### Post by Sam Lars on 2008-08-27
That makes more sense, I thought it was something like that.
If you go to the processes tab, in the View menu, you can tell it to show all processes, not just yours.
You can also run the command "top" which provides very similar information on the command line.

---

### Post by Im_Original on 2008-08-27
Ok, when the problem reoccurs, I'll try those suggestions to see which process is using all the cpu. In the meantime, any other ideas on why the password changes? You said it might be converted into hex and saved like that; any way to check that hypothesis? 

Thanks for your help!

---

### Post by Sam Lars on 2008-08-27
If you right click on the network manager icon, edit wireless networks, does yours show up?  If it does, does it have a password, and can you check the box to show it?

---

### Post by Im_Original on 2008-08-28
My network does not show up in "edit wireless networks," nor does any other network. The box is completely empty.

---

### Post by Sam Lars on 2008-08-28
When you put in the password and it works, does it then show up in the Passwords tab or Wireless Network list?

---

### Post by Im_Original on 2008-08-28
That's a 'no' on both counts. No password or network name in either of those places.

---

### Post by Sam Lars on 2008-08-29
Is there an option to tell it to remember the password when you enter it?
If you connect successfully, and then go back and click on your network again.  Does it ask you again?
You could also try using WICD instead of network manager.

---

### Post by Im_Original on 2008-09-01
Sorry for not posting the last few days, I've been busy. 

I found out which process is misbehaving, it's called ipw2200/0. It's owned by root. The strange thing is that sudo kill -9 does not work on this process. When I enter it on the command line, it appears to execute and doesn't show an error, but when I run the command top again I can still see ipw2200/0 running and using all the cpu.  

There is no option to save my password after I enter it in network manager. 

If I enter the correct password and then close and reopen the network manager, sometimes the password has already changed, but the network is still connected. 

Thanks for suggesting WICD, I'll give it a shot right now.

---

### Post by kokonobs on 2008-09-01
I used to have the same problem as you when i was trying to fic my wireless problem. The instructions are hard to follow and to be honest with you, i dont really remember which ones i did, as i did not follow them all. 

You will definitely need to install new drivers and firmware for your wireless card and install them.(note that installing the drivers and installing the firmware are 2 separate events as noted by WitchCraft:
 [http://ubuntuforums.org/showthread.php?t=904256](http://ubuntuforums.org/showthread.php?t=904256)

This is what i did:

From : [http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/)

I downloaded the new firmware and as copied them into /lib/firmware. Ubuntu may have installed ipw2100 drivers as this is what was there before. I deleted those.

I then downloaded the drivers 1.2.0 it was and found the very confusing instructions within the download.
After that tried to follow what @Withcraft and @gmxgeek said.
Hope this helps.

NB: This method worked for me with both manual configuration and also just using roaming, selecting the network and then entering the password.

Can someone else confirm the above as i'm a newbie and i may be giving messy explanations ...

---

### Post by kokonobs on 2008-09-01
Also note:
When inputing the password in manual configuration, make sure only one network manager(window) is open and make sure the wireless card is actually switched on after you reboot.

---

### Post by 1308 on 2008-09-01
I´ve been having a very similar problem. I´m running a fresh install of 8.04.1 on a dell latitude C600, using a Netgear WG511v2 wireless card and ndiswrapper. Something seems to change my 13 digit key into a 26 digit hex number after I enter it in network manager, and it shows up the same way in nm-editor. The only way it will connect is if I restart, even though it still shows the ¨wrong¨ key. I´ve tried WICD and wifi radar but could not get either one to connect to a WPA network.

---

### Post by mrkyiwa on 2008-09-02
I have the same problem too. Although I've discovered it wasn't to do with rebooting, in fact every time I close the network settings the password has changed back to the long one it was before. I'm using WPA, interestingly I tried using WPA 2 which didn't work as far as internet going but it did keep the password for the next time I went in...

---

### Post by Im_Original on 2008-09-03
Hello everyone, 

This problem has been solved for me, it's no longer an issue. Installing WICD and following the directions on the [WICD website]("http://wicd.sourceforge.net/download.php")   worked perfectly. 

There is an interesting thing to note here. It says on the WICD site that I have to make changes to /etc/network/interfaces file before WICD works. I didn't, and when I ran WICD for the first time I had the same problem that I had with Network Manager, the process ipw2200/0 went out of control. 


Here is my original /etc/network/interfaces:



auto lo
iface lo inet loopback



iface eth1 inet dhcp
wpa-psk 7747d3ce0bdf5bc6aeb49cdcc34ad15f29a12b628d32f68c89955a73fd95c48c
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid my_network



auto eth1




Everything works dandy after changing the file to this:


auto lo
iface lo inet loopback



After making that change I haven't had any problems with WICD. 

Now, what's going on? There must be something in that configuration file that makes ipw2200/0 go out of control, but I don't know what. My guess is that this is a wireless network, and it's using the interfac eth1, which is reserved for ethernet, I think. Either that, or the hex key is being stored there when it shouldn't be. 

I would like making this change to /etc/network/interfaces and try it with the GNOME Network Manager, but after using WICD I've found that I like it more. Alot more. It replaced Network Manager on install, and I don't want to go back just to try this. So, could someone else give it a shot? Or maybe someone has another suggestion? If you do change the /etc/network/interfaces file don't forget to make a backup first.

---

### Post by Sam Lars on 2008-09-03
Great to hear that WICD worked for you.  You can mark this thread as solved with the thread tools at the top.
I think with the management apps like WICD or Network Manager, you want your interfaces file to be as empty as possible.  It could be that it was getting confused with the entries you had in it.
The eth1 has nothing to do with it, it's just an arbitrary name for the interface.  It depends on your driver what is used... eth0, wlan0, ath0, ra0...

---

### Post by Im_Original on 2008-09-04
Yes, WICD worked perfectly. Thak you for the suggestion!

So, if this is a problem with the configuration file, then it is a problem with auto configuration; I didn't touch that file until I installed WICD. If it's a problem with auto configuration, we should report it as a bug, correct? Or should we wait for the other posters on this thread to try what I did, and then report with more useful data?

---

### Post by Sam Lars on 2008-09-04
Did you try using the Gnome Network Settings to ever set you connection up?  That program uses the interfaces file for permanent settings.
I guess you could consider it a bug that Network Manager/ipw couldn't handle it, but then again I'm not sure you want it just wiping your interfaces file.  You might check around Launchpad or here to see if you find anything about Network Manager and you interfaces file.

---

### Post by 1308 on 2008-09-09
I don´t know if this will help but I just did a clean install of Kubuntu 8.04.1 and I´m not having the pass key problem anymore. I also have two desktop machines using the same D-Link wi-fi card, the one running Ubuntu has the pass key problem, the one running Kubuntu does not.

---

### Post by xarte on 2008-12-07
Hello,

I just installed Ubuntu Hardy Heron 8.4 

I'm having the same problem with the wireless settings defaulting back to WPA Personal with a long password when I reboot. 

I went as far as re-installing as I though the tinkering I'd done in the terminal must be over-riding the Ubuntu tools in some way. 

(clean install did help in terms of just applying the graphics and wireless cards - I just enabled them, and set the graphics effects to 'none' and everything seems to be going well.)

Some of the information above sounded a bit confusing, but I googled WICD and ended up at the UBUNTU page here:
[B]
[https://help.ubuntu.com/community/WICD](https://help.ubuntu.com/community/WICD)[/B]

I followed the instructions - very clear and step by step, you really can't get it wrong. Simply replacing the word "gutsy" with "hardy" for my version of Ubuntu in the line

deb [http://apt.wicd.net](http://apt.wicd.net) gutsy extras


and follow the bouncing ball. The warnings that the code is unverified and deleting the existing manager was a little alarming, but since it was from a Ubuntu page went ahead.

[B]On the first reboot I had to go into the wireless manager again and re-enter the passkey and connect.

On the second reboot I'm up and running, connected from the get-go.[/B]

YAY for WICD !!!!

And thank you for sharing your wisdom on the forum - I'd have given up on this ages ago if it wasn't for the great community. Now I have an uber-cool OS !!!

---

