---
title: "wireless problem using linksys wpc54g"
date: 2007-11-12
forum: Networking &amp; Wireless
---

### Post by EnterTheDarkSide on 2007-11-12
Hi,

I just installed ubunt 7.04 and I was wondering how would I setup the wireless connection. I downloaded and installed the ndiswrapper and the ndisgtk package. I used system>>administration>>windows wireless drivers and selected my linksys wpc54g adapter's driver (the ***.inf file). Ubuntu confirmed that the driver was installed, so I turn off my pc and turned it back on. However, ubuntu isn't detecting any wireless connection. 

I total newbie to linux and would appreciate it if anyone can offer any help on this topic.

---

### Post by shoryuken on 2007-11-12
> **EnterTheDarkSide said:**
> Hi,

I just installed ubunt 7.04 and I was wondering how would I setup the wireless connection. I downloaded and installed the ndiswrapper and the ndisgtk package. I used system>>administration>>windows wireless drivers and selected my linksys wpc54g adapter's driver (the ***.inf file). Ubuntu confirmed that the driver was installed, so I turn off my pc and turned it back on. However, ubuntu isn't detecting any wireless connection. 

I total newbie to linux and would appreciate it if anyone can offer any help on this topic.

Here is how I got mine (v.4) working.
I followed the following some of the instructions in this post:
[http://ubuntuforums.org/showpost.php?p=113584&postcount=7]("http://ubuntuforums.org/showpost.php?p=113584&postcount=7")


Here are some of the things I had to install through synaptic before going any further:
wpasupplicant
ndiswrapper-common
ndiswrapper-utils-1.9
wifi-Radar
network-manager
network-manager-gnome
network-manager-kde

Now I have to admit that I am not an expert at ubuntu but I've got things working thanks to this forum and although I am not sure if all the different network managers are necessary or not but since my setup works you might want to give them a try.

Once you've installed all the above go to linksys website and download the driver for your version of the card. Make sure to extract the *.sys and *.inf files in the linksys download. As the following instructions indicate, a good place to put the extracted files is in a folder on your desktop. The following is a modification from the link above:

1. Use Synaptic to get the above listed linux files and to install them
2. Get the windows drivers, and copy the .sys and .inf to somewhere (say /home/<yourusername>/Linksys/)
3. Open terminal, and enter the following commands:
3a. cd Linksys
3b. sudo ndiswrapper -i <name>.inf (mine was WLIPNDS.INF (The above link indicates that The screen should show something about Forcing parameter RadioState|0 to RadioState|1...) I don't remember having seen this.


The following two steps were not necessary for me so you might want to just jump to step 4.
3c. cd /etc/ndiswrapper/
3d. Edit all the .conf files, look for the line RadioState|1 and change it to RadioState|0 (to do this, I had to type sudo gedit and open the files from the GUI... gedit didn't quite like opening files with \: from the command line, not sure why) I'm not sure if just changing one or two files will work, but I just changed all 4.

4. sudo modprobe ndiswrapper
5. sudo echo ndiswrapper >> /etc/modules

6. Start Wifi-Radar and setup a New Wifi Profile (This would be a dummy profile for some reason I've had to do this and after each re-boot I have to try to connect to it so that I can actually detect all the available networks).

7. Start Network-Manager oras I have done add nm-applet to your panel
8. You should now be able to detect your network.
9. When you try to connect to, Wifi -Radar will ask to set-it up a profile. If you are going to use WAP then set the driver to "wext"

you should now be good to go. The only issues I have is that sometimes I need to use the nm-applet to get the connection working. For some reason it is sometimes the only way to get the connection working.

Anyway, I hope that this will be of help.

Cheers

---

### Post by SpiritIsReality on 2007-11-13
howdy
I'm speechless. WOW!!!
3or4links
Unified documentation site - I need your input [http://ubuntuforums.org/showthread.php?t=579726](http://ubuntuforums.org/showthread.php?t=579726)
Documentation of Ubuntu [http://ubuntuforums.org/showthread.php?t=602668](http://ubuntuforums.org/showthread.php?t=602668)
Networking And Wireless Documentation Links [http://ubuntuforums.org/showthread.php?t=608751&highlight=documentation](http://ubuntuforums.org/showthread.php?t=608751&highlight=documentation)
LTSP Documentation Links [http://ubuntuforums.org/showthread.php?t=608744&highlight=documentation](http://ubuntuforums.org/showthread.php?t=608744&highlight=documentation)
trails

---

### Post by shoryuken on 2007-11-16
This is an update to my previous post. Instead of the lynksis driver you should download the ipn2220 driver v3.07.02.2005 - as used by TOSHiBA, PACKARD BELL, BENQ, ACER and that can be found at [http://www.laptopvideo2go.com/forum/index.php?showtopic=7172&hl=ipn2220]("http://www.laptopvideo2go.com/forum/index.php?showtopic=7172&hl=ipn2220")

After installing this driver instead of the Lynksis one (so in the instructions below replace WLIPNDS.INF with neti2220.inf), I now have a stable connection that hasn't dropped, connects easily after reboots and using WAP. The card picks-up all the near by networks right off the bat and no more need for having both nm-applet and Wifi-Radar. I'm now using mn-applet and I pick up all the networks as soon as I log in. \\:D/ :guitar::guitar: \\:D/

The installation of some of the components listed below should now become optional. The optional components should be at least these two:
wifi-Radar
network-manager-kde



> **shoryuken said:**
> Here is how I got mine (v.4) working.
I followed the following some of the instructions in this post:
[http://ubuntuforums.org/showpost.php?p=113584&postcount=7]("http://ubuntuforums.org/showpost.php?p=113584&postcount=7")


Here are some of the things I had to install through synaptic before going any further:
wpasupplicant
ndiswrapper-common
ndiswrapper-utils-1.9
wifi-Radar
network-manager
network-manager-gnome
network-manager-kde

Now I have to admit that I am not an expert at ubuntu but I've got things working thanks to this forum and although I am not sure if all the different network managers are necessary or not but since my setup works you might want to give them a try.

Once you've installed all the above go to linksys website and download the driver for your version of the card. Make sure to extract the *.sys and *.inf files in the linksys download. As the following instructions indicate, a good place to put the extracted files is in a folder on your desktop. The following is a modification from the link above:

1. Use Synaptic to get the above listed linux files and to install them
2. Get the windows drivers, and copy the .sys and .inf to somewhere (say /home/<yourusername>/Linksys/)
3. Open terminal, and enter the following commands:
3a. cd Linksys
3b. sudo ndiswrapper -i <name>.inf (mine was WLIPNDS.INF (The above link indicates that The screen should show something about Forcing parameter RadioState|0 to RadioState|1...) I don't remember having seen this.


The following two steps were not necessary for me so you might want to just jump to step 4.
3c. cd /etc/ndiswrapper/
3d. Edit all the .conf files, look for the line RadioState|1 and change it to RadioState|0 (to do this, I had to type sudo gedit and open the files from the GUI... gedit didn't quite like opening files with \: from the command line, not sure why) I'm not sure if just changing one or two files will work, but I just changed all 4.

4. sudo modprobe ndiswrapper
5. sudo echo ndiswrapper >> /etc/modules

6. Start Wifi-Radar and setup a New Wifi Profile (This would be a dummy profile for some reason I've had to do this and after each re-boot I have to try to connect to it so that I can actually detect all the available networks).

7. Start Network-Manager or as I have done add nm-applet to your panel
8. You should now be able to detect your network.
9. When you try to connect to, Wifi -Radar will ask to set-it up a profile. If you are going to use WAP then set the driver to "wext"

you should now be good to go. The only issues I have is that sometimes I need to use the nm-applet to get the connection working. For some reason it is sometimes the only way to get the connection working.

Anyway, I hope that this will be of help.

Cheers

---

