---
title: "Cannot read other files in the same network"
date: 2008-06-17
forum: Networking &amp; Wireless
---

### Post by hosammy on 2008-06-17
I am using 8.04 Hardy, with gnome environment and samba installed.

Yesterday, I can still use the nautilus to check other PC Windows system network. The method is to click the network, then the address path "network:/// " shows, Desktop network and Windows network, then I click Windows Network, it shows my Windows network, namely, Klnchambers. Then I can select to choose which system's file by choosing its respective name and click into it.

Now, today, I can still enter the network, I find that the Desktop Network disappear and only exists the Windows Network and the address path is "network:///". I click this Windows Network and the address path only shows smb:/// and nothing is found in its content.

I have used the command "nmblookup -A 192.168.1.3" where the ip address 192.168.1.3 is one the PC ip address in the "Klnchambers network" which shows normal and can be accessed by my Ubuntu system. Other Windows System can also access each other in the same Klnchambers Network and only my Ubuntu fail to view others.

Please advise ...
:confused:

---

### Post by superprash2003 on 2008-06-17
try smb://x.x.x.x where x.x.x.x is the ip of the windows share pc.. try this in nautilus(PLaces->Computer)

---

### Post by linux6994 on 2008-06-17
I have windoze networking working well, this is what I have installed:
see attched

---

### Post by hosammy on 2008-06-18
> **superprash2003 said:**
> try smb://x.x.x.x where x.x.x.x is the ip of the windows share pc.. try this in nautilus(PLaces->Computer)

Thank you, after typing the respective ip address, I can access the required PC in the network now.

However, since the network use a router to connect the internet and the ip address is dynamic, it means that the particular PC's ip address may change from time to time. Does any method to search my designated PC in the network so that I need not search it manually in the future?

Also, I find another problem today is I cannot send to print my document to the printer attached to this PC, Please advise ...

:confused:

---

### Post by SolitudeX on 2008-06-18
Hello. I've experienced similar issues with samba over wireless networks on Hardy. If I use my laptop over my wireless network (Gigabyte GN-BR01G Wireless Router - in access point mode, doesn't do DHCP) it is unable to find my workgroup PCs or shares. Yet if I try smb://x.x.x.x (IP address) then it works fine. However, if I plug in an ethernet cable, it will work perfectly each time I goto Places > Network.

hosammy - Are you using wireless or ethernet cable? Interesting to see if it's just me or other users experiencing issues with wireless only too!

So the question remains, why does samba not see the workgroup via wireless, but it does via ethernet cable?

Perhaps some Ubuntu Guru can spread a lil joy our way and enlighten us with knowledge :-)

---

### Post by hosammy on 2008-06-19
> **SolitudeX said:**
> Hello. I've experienced similar issues with samba over wireless networks on Hardy. If I use my laptop over my wireless network (Gigabyte GN-BR01G Wireless Router - in access point mode, doesn't do DHCP) it is unable to find my workgroup PCs or shares. Yet if I try smb://x.x.x.x (IP address) then it works fine. However, if I plug in an ethernet cable, it will work perfectly each time I goto Places > Network.

hosammy - Are you using wireless or ethernet cable? Interesting to see if it's just me or other users experiencing issues with wireless only too!

So the question remains, why does samba not see the workgroup via wireless, but it does via ethernet cable?

Perhaps some Ubuntu Guru can spread a lil joy our way and enlighten us with knowledge :-)

In my case, I am using an ethernet cable to connect.
I am still waiting the solution to make use the Windows PC Printer !!!
:confused:

---

### Post by celem on 2008-06-19
This issue has been around for quite a while. I experienced it with Dapper but finally got it working there. It has been broken for me ever since Dapper. I can see Windows shares through a WiFi router using smb://192.168.0.104 (DHCP assigned) inserted into Nautilus, but this is bad for the reasons stated herein by others. I realize that many people don't seem to have a problem seeing Windows shares but many, like myself, do continue to have problems. Seeing shares in your own network shouldn't be difficult but it is!

Why, I wonder does putting smb://192.168.0.104 into nautilus works, yet clicking on the Icons in the Places->Network fails?

---

### Post by SolitudeX on 2008-06-21
After some research i've figured out that this issue seems to be gnome specific. I installed kubuntu-desktop and ran konq. from GNOME and was able to browse shares perfectly, while going Places > Network still showed nothing. After some reading, people are claiming this is a gvfs/nautalis issue introduced in Hardy. But if some users have had this problem since dapper might be something else!

---

### Post by celem on 2008-06-21
There may be more than one problem with similar symptoms. Using a machine running KDE on PCLinuxOS I get the same results, namely using Nautilus with smb://192.168.104 works but clicking through the graphical route fails just like it does in Ububtu.

---

### Post by hosammy on 2008-06-23
I run the synaptic update this morning to upgrade Hardy 8.04 to 8.04.1 & some other smb type packages. The bug had slightly changed.

Now I click the Places > Network, then click the Windows Newtwork, it did not show nothing but open a new information window box say that "Failed to retrieve share list from server".

This bug did not come with the Hardy. When I upgrade to Hardy, I cannot still view the other PCs' file through the Network.

Please advise ...

:confused:

---

### Post by bristolbadger23 on 2009-04-27
Did anyone get this working in Intrepid?

I was going to sit this one out until Jaunty came along, then found that Jaunty hasn't got nVidia 184 drivers working so was unable to find if it worked on that or not...

I am getting the same thing, graphically unable to reach shares, but if i put smb://ip.ad.re.ss into nautilus it gets there...

---

### Post by celem on 2009-04-27
See my original reply at #7 above. I think that this isn't wholly a Linux issue but rather some issue with how it handles DNS forwarding. I recently changed my router but nothing else and suddenly the problem is gone. In my case, DNS is forwarded by the router.

---

