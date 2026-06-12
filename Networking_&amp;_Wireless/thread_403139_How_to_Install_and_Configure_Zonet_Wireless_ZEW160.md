---
title: "How to Install and Configure Zonet Wireless ZEW1602"
date: 2007-04-06
forum: Networking &amp; Wireless
---

### Post by mdesenfants on 2007-04-06
Since I couldn't find a very specific or detailed post relating to my wireless card, I decided to write my own.  Hopefully, you'll get yours done working faster than I did!  Granted, I didn't have any Internet connection to my Linux box, so I'll assume you don't either.

I bought this Zonet wireless card while I was building my own computer with the understanding that it wasn't Linux friendly - it was cheap, I was planning on running Windows primarily anyway, and I love a challenge.

So this is what I had to do:

Assuming you're using the Edgy DVD (the utilities required will probably be on the cd as well), you first need to install ndiswrapper.  Insert the DVD into your computer and go to System -> Administration -> Synaptic Package Manager.

After you enter your password (the one you used to log in), the package manager will open.  Scroll down and find the "ndiswrapper-utils-1.8" and "ndiswrapper-common" packages, check the boxes next to them, and click "Apply" at the top of the window.

NDISWrapper is now installed.

Use your card's driver CD and look for the folder containing the netmw125.inf file.  Copy the entire folder to your home directory (or to the directory of your choosing, as long as you know where it is and how to get there).  

Open terminal and go to the directory you just copied from the CD.

Enter the following command:
```
sudo ndiswrapper -i netmw125.inf
```

Now check to see if your driver was installed:
```
sudo ndiswrapper -l
```

Finish up this part (not exactly sure what this command does, but it works):
```
sudo modprobe ndiswrapper
```

And to make the driver load at startup:
```
sudo ndiswrapper -m
gksudo gedit /etc/modules
```

Once the window is open with the /etc/modules file, add ndiswrapper to the file in its own line.  Save the file and exit.

Enter this command to do the initial configuration of your card, changing wlan0 to whatever the id of your wireless card:

```
sudo iwconfig wlan0 essid "AP" mode Managed
```
You might have to add an option for a wireless key if your network is secured with WEP or whatnot.  Mine uses mac filters, so I didn't need a key.


Here's the part that took me the longest... basically because I forgot what an ESSID was... sort of a noob mistake on my part... but you can learn from my mistakes!

Now that your card's driver is installed, go to System -> Administration -> Networking.  The Network Settings window should contain an item for "Wireless connection".  Double click on your connection and make sure to configure it according to your network.  The ESSID is the name of your wireless router / access point.  If your network is configured for DHCP, make sure you put DHCP in "Configuration".  Otherwise set your IP address, net mask, and default gateway.

Short Glossary:
ESSID - name of router
DHCP - automatically gets your wireless card set up for use with the network.
IP Address - the numbers used to identify your card / computer on a network.
Net Mask - in short, how a router looks at an IP address.
Default Gateway - the IP address of the computer or router that leads to the internet (in most cases, it's the router itself)


Hope this helps the cheap folks like me - the brave folks who know their devices aren't linux friendly but want to make them work anyway!

And it's very possible I missed an instruction or two.  I wasn't exactly writing things down as I went along.  If anyone has any corrections, post them please!

---

### Post by demonzrulaz on 2007-05-13
Hi. I would like to say that great tutorial. I have some problems understanding this tutorial though because I am completely new to Ubuntu. I have Zonet ZEW1602 and followed every step. I don't understand some of it though and I have a few questions. 
1 - How do I get the ID of my that adapter?
2 - When you say: "Once the window is open with the /etc/modules file, add ndiswrapper to the file in its own line. Save the file and exit.". what do you write in the text file exactly?
3 - during this step: "sudo ndiswrapper -l". I typed that in and it gave me this:
"Installed drivers:
netmw125           invalid driver!"
 what do i do? do i ignore it?
4 - "sudo iwconfig wlan0 essid "AP" mode Managed" what do type in exactly? Is AP the name of your access point? (i need to clarify). what is mode and what is Managed. Also,  the the access point is WEP secured. where do i type in the wep keys (and which one do i use, i have 4)

thanks for any help.

---

### Post by mdesenfants on 2007-05-24
I sort of screwed up my installation of Ubuntu, and I haven't really gotten around to fixing it, so answering your questions could be a little tough, but I'll answer what I can.

1 - Assuming that the zew1602 is the only wireless card installed on your computer, its id is most likely "wlan0".

2 - You will type exactly "ndiswrapper" in the text file.  I expected it to be more complex when I first read it too.  The file should look something like:

```

#Random bits of configuration code and whatnot
ndiswrapper

```

Notice that it's simply "ndiswrapper" on its own line.

Aside:  Man, I wish my Ubuntu was working so I could actually just copy/paste the file for you to look at!

3 - There are some other discussion topics out there for this card and similar cards that say if you find a driver when you type in "sudo ndiswrapper -l" you should remove it and replace it with the new driver in the later steps.  Sounds like a great plan, but  I can't remember exactly how to do this.  When I installed my card the list was blank, so I never had this problem.

4 - I took a class on exactly how to configure this stuff... but blast if I can recall a word of that chapter...
So let me start by saying, "It would be best to find a separate tutorial on wireless network configuration."

That being said, here's what I have to offer:

Enter "man iwconfig" to get a good description on how the iwconfig command works.  It will have some details on how to configure WEP wireless.  If, for some reason, your WEP configuration is no longer applicable (as it was with my router), you can enter

```
sudo iwconfig wlan0 essid "AP" mode Managed
```

directly into the terminal as it is written.  When you get to the last steps of this howto (the part where it asks you to go to System -> Administration -> Networking), you will tell your card the name of your network.  I think there's also a way to configure WEP at that point as well, but I never wrote about it because I don't use it.

Hope that helped a little!  And if anyone else has more details or whatever, they would be appreciated.

---

### Post by lefthand on 2007-07-29
I was able to get this working with the driver on the cd. It didn't like the driver at first and threw an error. After removing it and re-installing it a couple times it worked. BUT, since it can't do WPA in fiesty, I think I'll have to return it.

---

### Post by mcginnis_john on 2007-08-03
First of all KUDOS! This is an excellent How-To. Like you I bought these cards (3) because they were dirt
cheap ~ $3 each. Throw aways at that price. But enough, here is what I want to add.

-------------------

I have a AMD dual core 64bit X2 system running kubuntu. It rocks, so don't knock it. Yeah I know the pain but its worth it. If you want to get the ZEW1602 card running on it here's what you do.

1) There is a subdirectory on the Zonet provided CD marked "WinX64" Copy that over to the directory of your choice on the Linux box.

2) You use a different driver. Instead of netmw125.inf substitute netmw126.inf for the ndiswrapper install command.

3) follow the rest of mdesenfants instructions to the letter. It worked first time out for me. 

One other item that mdesenfants didn't mention that I might consider a very first step is to verify that the MB recognizes the card. It it doesn't then mdesenfants excellent instructions are for naught. So, type the following to validate the presence of the card:


     lspci | grep "Ethernet"


If the card is found it should look something like:

0X:0X.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless

X of course could be any number differing from what I got based on your MB and other cards in the box.

Very smooth....

And again, thanks, mdesenfants.

---

### Post by rdutcher on 2007-08-08
I just purchased a zonet ZEW1602 wireless pci network card and I am running Feisty on an
AMD SEMPRON 3000+ tower with a VIA K8M800-M2 MB.  The card is recognized and ndiswrapper works.  It fails on the very last step --  iwconfig with an error message of:  
"Error for wireless request "Set ESSID" (8B1A) "

I've tried several of the different .inf files on the cards' CD (121.inf/sys, 123.inf/sys,125.inf/sys), all with the same results.  Between each attempt, I've gone to /etc/ndiswrapper/<inf folder> and removed the previous files and directory, so I know that I'm bringing in the latest version.  

 My laptop, running XP Pro, connects to the Zonet wireless  (802.11g MIMO) router with no problems, and that is what I'm using to post this message.  So I know the wireless router/Cable Modem are functioning.  

 On the card, the green light is flickering, like it is sending/receiving but the terminal window hasn't updated and can't get to the internet in the web browser.  When I tried the netmw123.inf, the iwconfig just hangs forever.

  Any suggestions on how to resolve this would be greatly appreciated !  Thanks

---

### Post by hotdog003 on 2007-08-16
I've gotten WPA working in Feisty successfully. Here's how.

0. Make sure your card currently works with WEP by following the instructions above.
1. DIsable this card in Network Manager- It uses a broken method of authentication. I'm going to post to their mailing list about it.
2. Do a ```
sudo bash -c 'wpa_passphrase PUT_YOUR_ESSID_HERE PUT_YOUR_PASSPHRASE_HERE > /etc/wpa_supplicant/wpa_supplicant.conf'
```
3. AT THIS POINT: If you do ```
 sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant/wpa_supplicant.conf
``` then the card should function perfectly. If it does not, then something is wrong- Stop here and ask for help.

Now let's make it do that for you automatically.
4. Do a ```
sudo gedit /etc/network/interfaces
```
5. If you have any lines in that file that contain 'wlan0', remove them. Most likely, that will be 'auto wlan0' and 'iface wlan0 inet dhcp'.
6. Paste this in at the bottom.
```
auto wlan0
iface wlan0 inet dhcp
pre-up wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant//wpa_supplicant.conf -B
pre-down killall wpa_supplicant
```.
7. Save and close.
8. Do a ```
sudo ifdown wlan0; sudo ifup wlan0
``` to activate your card. You're done!
:guitar:

---

### Post by Nachowarrior on 2007-11-16
hmm... i'm stupid with this so far... but i've gotten up to the last line in the original line and i get....

"Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device."

I was going to try the next one for wap because I think i need that instruction but what is "passphrase". I'm working on this for a customer... this is why I always buy popular parts... much easier... pnp :-p, but i'm enjoying the challenge, lets just hope my customer is enjoying the wait! 

thanks for any help or re-defining, cuz i'm pretty much ignorant to Linux and network stuff thus far.

also, i ran the command to verify the card is recognized, and it came back positive, and crap, i just spilled beer on my desk. whoops!   anyway. for some reason nothing is recognizing it to set up as an actual card. I do however have an onboard wired and a pci wired. I don't know if that'll affect it. 

once again, appreciate the help.

---

### Post by skulldriveshaft on 2008-03-22
THANKS A TON!

Got my wireless internet working immediately!

Thanks +1 :]

:guitar:

---

### Post by ejvinit on 2008-06-20
hey guys any of ull know how to install this card on win 2k sp4.i am getting an error "code 10 device did not start" after installing the card & drivers.plz help

---

