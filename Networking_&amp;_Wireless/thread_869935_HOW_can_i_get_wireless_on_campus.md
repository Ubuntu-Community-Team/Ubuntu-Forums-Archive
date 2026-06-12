---
title: "HOW can i get wireless on campus??"
date: 2008-07-25
forum: Networking &amp; Wireless
---

### Post by ali112 on 2008-07-25
I'm a student and the on campus network at my university uses SecureW2 for the 802.1X authentication. I'm totally new to Ubuntu and still in the process of transfering over and leaving Windows XP for good. So the obvious question is how do i get campus WiFi on Ubuntu. 

I'm not sure if this helps in answering my question or specifying what the problem is but these are the instructions my University provides in connecting to the campus WiFi on windows xp.  

   1. Use the Windows XP wireless network connection feature to connect to "laurierdownload".
   2. Point your favorite browser at wireless.wlu.ca.
   3. Download and install SecureW2 from here. A reboot is required. Continue at step 4 when your system returns. By default the SecureW2 installer is downloaded to the Desktop. During SecureW2 installation accept all the default choices.
   4. Reconnect to "laurierdownload", and reload wireless.wlu.ca. From “Start” point to “Connect to” then choose “Wireless Network Connection”. (see screenshot)
   5. Click on Properties. (see screenshot)
   6. Click “Wireless Networks” tab, verify “Use Windows to configure my wireless network settings” is checked and click “Add”. (see screenshot)
   7. Under the Association tab, Enter “laurierwireless” to “Network name (SSID)”, choose “WPA” for Network Authentication and “TKIP” for Data Encryption. (see screenshot)
   8. Click the Authentication tab, ensure that the "Enable IEEE802.1x authentication for this network" box is check, choose “SecureW2 TTLS” as the EAP type, and ensure the "Authenticate as computer when computer information is available" box is checked, then click “Properties”. (see screenshot)
   9. In the SecureW2 window leave DEFAULT in the Profile box and click on Configure. (see screenshot)
  10. Under “Connection” tab ensure that the "Use alternate outer identity” box is NOT checked and that the "Use anonymous outer identity" circle is checked. Also the "Enable session resumption (quick connect)" box should not be checked. (see screenshot)
  11. Under the Certificate tab ensure that both boxes are not checked. (see screenshot)
  12. Under the Authentication tab ensure PAP is chosen in the "Select Authentication Method" box. (see screenshot)
  13. Under the User Account tab ensure that the Domain box is blank , the "Prompt user for credentials" box is unchecked and the "Use this account to logon computer" box is not checked. Enter your Novell Username in the "Username" box and your Novell Password in the "Password" box. (see screenshot)
  14. Click on OK three times to close the various windows we have used except the "Wireless Network Connection Properties" window. In the "Wireless Networks" tab, choose "laurierwireless" in the "Preferred networks" window, then keep clicking the "Move up" button until it is on the top of the preferred networks list. Remove "laurierdownload" from the list of preferred networks. Click "OK" to close this window.  (see screenshot)
  15. Your wireless system should now be ready to access the Internet. 

Any help would be greatly appreciated!!!! 

Thanks.

---

### Post by Sub101 on 2008-07-29
Ive never used securew2 myself but [http://vuksan.com/linux/dot1x/wpa-client-config.html]("http://vuksan.com/linux/dot1x/wpa-client-config.html") looks promising.

Also the bottom script on this page may work [http://www.securew2.org/forum/viewtopic.php?f=4&t=483]("http://www.securew2.org/forum/viewtopic.php?f=4&t=483")

Good Luck, and post back, i'm sure someone more experienced than me will see this soon

---

### Post by jimv on 2008-07-30
They may or may not be helpful, but did you attempt to get in touch with your campus's ITS helpdesk?

Here's a list of contacts.  Probably any of the network guys could help...but I would try the HelpDesk first (it's in the middle of the list).

---

### Post by gaurang on 2008-08-22
hey , 

me too have same trouble, this secure w2 works only with windows :( ... and being linux fan its really irritating for me ... 

i tried to talk with IT dept. of our campus .. but they said they don't provide any kind of technical support for Linux .. (damn !! ) ... 

i use vista and ubuntu ... so i can work on that junk windows .. but it could be really helpful if someone can guide ... i found couple of threads about same but for European system ( they call its SecureRome or something like that .. ) which was not much helpful though ...

so .. from now on .. me too with you on this quest :) .. 

just hope that we find our way ...

---

### Post by chalewa on 2008-08-22
there are ways, my campus used securew2 as well, but i was able to get on through some terminal commands. 

its been a few years and a couple distros back, but i think i have posted my config files on here before, but ill see if i can find them again. i used xsupplicant to connect.

---

### Post by XxLeekxX on 2008-08-26
I'm also hoping to solve this, since I'm going back to Laurier very soon.  As soon as I find an answer, I will not hesitate to post on this thread.

---

### Post by XxLeekxX on 2008-09-06
Dude I just found out how to do it.  Firstly, on your internet taskbar and choose laurierwireless,  Then choose the following

Wireless Security: WPA Enterprise
EAP Method: TTLS
Key type: Automatic (default)
Phase2 type: PAP
Identity: Your novell username
Password: Your novell password
Anonymous Identity: (Leave blank)
Client certification file: (none)
CA certificate file: (None)
Private key file (None)
Private Key password: (None)

And voila! You are done.  Here is a screenshot of what it should look like:
[http://smg.photobucket.com/albums/v168/XxLeekxX/?action=view&current=laurierwireless.png](http://smg.photobucket.com/albums/v168/XxLeekxX/?action=view&current=laurierwireless.png)

---

### Post by gaurang on 2008-09-09
> **XxLeekxX said:**
> Dude I just found out how to do it.  Firstly, on your internet taskbar and choose laurierwireless,  Then choose the following

Wireless Security: WPA Enterprise
EAP Method: TTLS
Key type: Automatic (default)

ah .. i don't know y .. but i don't have WPA-Enterprise option :(.. i just have WPA-Personal ... and so all i can feed is PSK :confused:

what else can be done ??

and still i have one confusion, is that why security type of that wifi connection shows WEP ?? because when i try for WEP , it says WEP- passphrase , WEP - HEX and WEP- ASCII ... bt i am sure that none of it can be applied .. then what is the way ?? 

damn, its really irritating ...:mad:

---

