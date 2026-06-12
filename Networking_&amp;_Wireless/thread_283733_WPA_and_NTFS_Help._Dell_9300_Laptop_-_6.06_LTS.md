---
title: "WPA and NTFS Help. Dell 9300 Laptop - 6.06 LTS"
date: 2006-10-24
forum: Networking &amp; Wireless
---

### Post by apel444 on 2006-10-24
I’ve encountered a number of issues when using Ubuntu LTS 6.06 on my Dell Inspiron 9300 laptop. I'm proberly a bit of a newbee yet i usualy grasp things like this well, i don't understand why im getting the problems and the help would be Great!

The first problem I encountered was that of my wireless connection, being a WPA connection it is not supported by the ubuntu simple UI, yet I managed to configure the ect/network/interfaces box to connect to my wpa. I thought this was a great opportunity to update my version of ubuntu, so I go to the updates manager and update, the dialog box comes up telling me I should restart, so I do. After the updates it seems on the gimp boot loader ubuntu is now listed twice (not to worried about it but not sure if it’s a bug?) yet the main problem was that when ubuntu had booted up the method I used of adding WPA-SSID, WPA-MGMT and WPA-Passphrase to the interfaces config file no longer seemed to have a effect (I use Intel pro wireless, the standard on insperon’s – yet I don’t think it’s a driver issue because it worked before updates). I’ve tried the wpa_Suppliment method yet had no joy! If anyone has had the same problem, or knows how to fix it…. It would be a great help!

Before I installed the updates I also took the opportunity to mount my windows NTFS partition (while my net was still working) using the method on ubuntgiude.org for reed a write permissions, yet this didn’t seem to work. I’m stuck and out of idea’s! I really want to move over to Linux, yet the transition seems to be a difficult one (from windows), I know my way around windows well yet virus’s and the stability of windows are too much of a consent problem. Maybe I should give up and go to Mac – shame Mac osx 86 doesn’t support Intel pro wireless either.

If anyone can help it would be a great help. Many thanks.
Apel444

---

### Post by catlett on 2006-10-24
It is not a bug that ubuntu is listed twice. You got an updated version of the kernel when you did the update.You can choose between the 2 kernels when you start up. You will continue to get kernel updates over time. It is good to have 2 kernels. One you know works and the latest one. This way you can try out the new one and if it has problems, you can boot with the old one. Kernels can be added and removed with synaptic package manager.
Your other issues may be kernel related. Some configurations need to be updated when the kernel updates. Try booting the the second entry in the grub menu. The second entry will be your old kernel. Hopefully everything will work correctly with that kernel.
Before you drop a couple of hundred on Mac OSX, you may want to try Xandros linux. It is not free but for $80 you can get the premium edition or for $35 you can get the base system. It is the most user friendly of all linux distros and it has excellent hard ware support. Plus the $80 version comes with the best documentation of any linux distro. [http://www.xandros.com/products/home.html](http://www.xandros.com/products/home.html)

---

### Post by randomnumber on 2006-10-25
I have a inspiron 9300 with a wireless centrino abg card and have had no problems with drivers. My laptop seems to work completely except for the media buttons which probibly can be fixed.

I use "network manager" with "wpa supplicant" for the wpa networks. If you are interested in try it you can search the forums/web for how-to's. I have not had a chance to see if the type a network works

As far as the ntfs partition, I suggest that you use a fat partition to move data from one os to the other. I have a concern over corupting the partition.  I named my fat partition "shared". 

As far as moving to only linux I suggest dual booting and only booting windows when you need to. When you get to the point that you dont boot windows you maybe ready to format the windows partition.

I think that a good reason to move to linux now is the release of vista which you will have to buy eventually if you continue to be a windows user. It will not be your choice, using xp will be like using windows 95 today. 

It take a little practice but most all the information you need about linux is availble in the internet and you have taken a big step forward by just joining a forum and asking questions. 

Good luck

---

