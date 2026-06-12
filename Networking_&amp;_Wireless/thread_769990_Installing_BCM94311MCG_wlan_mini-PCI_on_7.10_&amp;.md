---
title: "Installing BCM94311MCG wlan mini-PCI on 7.10 &amp; 8.04 - Broadcom wifi on a HP dv9000"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by jlandaw on 2008-04-27
I'm making this Thread to Help others with the problem I had installing my BCM94311MCG wlan mini-PCI.  

I have a HP dv9000 (dv9428nr) Running Ubuntu 7.10(32 bit)
[COLOR="Red"]Update: Now running Ubuntu 8.04 LTS 64 bit -it is working but I had a little trouble setting up... I am including a bug-fix that any hardy (8.04) users should use before going forward*[/COLOR]

[INDENT][COLOR="SeaGreen"]Note: If the output for  &#8220;lspci | grep Broadcom&#8221; is :

&#8220;03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)&#8221;

Then this tutorial will work (baring some bug or alternate configuration you have tried to set up already).

Here is a list of computers that this tutorial has already worked on:
Hp dv2000:
HP dv2415nr 
HP dv2418nr

HP dv6000:
HP dv6258se
HP dv6408nr
HP dv6420
HP dv6423om
HP dv6607nr
HP dv6625us
HP dv6636nr
HP dv6660se

HP dv9000:
HP dv9205us
HP dv9428nr

HP tx1000:
HP tx1305 
HP tx1499

HP zv5000


Compaq Presario V3000
Compaq Presario V6000
Compaq Presario F500
Compaq Presario F562LA
Compaq Presario F700

Compaq 6515b
Compaq 6720s

Dell Inspiron 1501
Dell Inspiron 9400
Dell Inspiron E1705
Dell Latitude 131L

Acer Extensa 4420-5237
[/COLOR][/INDENT]

I do believe this will work with almost all hp dv**** and Compaq's (some forums show this to also work with dells...
[COLOR="Lime"]Edit: If you read the replies to this post they show that many different HP's, Compaq's and Dells all can work by using this method.[/COLOR]
Everything I put in here i have taken form other thread/forums, but none were set up in a way that a noob (Beginner) could follow easily.

First we need to do a few things.

You need to have a internet connection, wired since your wifi is not working yet :)

whenever you see the command "*sudo*" you will have to enter you password (the characters will not appear as you type.)
[COLOR="DarkRed"]
Step 1[/COLOR]
[INDENT]You will need to download the drivers we will use later.
Download it[ [COLOR="Blue"]Here[/COLOR]]("http://www.mediafire.com/?zyjnqmklzm1"). 
Edit: Thanks to rabalder and MrPickle for the non-rapidshare link
[/INDENT]

[COLOR="DarkRed"]Step 2[/COLOR]
[INDENT]You do not have to download the next file, we will do later on, in the instillation.
Go [[COLOR="Blue"]here[/COLOR]]("http://sourceforge.net/project/showfiles.php?group_id=93482") and write down the latest stable release number. On May 27, 2008 the release  number was 1.53[/INDENT]

[COLOR="DarkRed"]Step 3[/COLOR]
[INDENT]If you enabled the restricted drivers disable them

System --> Administration --> Restricted Drivers Manager


I guess if you never tried to use them you could try before going thru this...[/INDENT]

[COLOR="Green"]One more important thing... make sure that you know what way the wifi switch must go to be on... If its off you will never get online (I just went step by step with someone, and we faild to think of the fact that his wifi card was switch off... :mad: ) Its an easy thing to miss.
On my Hpdv9000, the switch is on if it is to the right. ===>[/COLOR]

[COLOR="DarkRed"]Step 4[/COLOR]
[INDENT]Next we need to uninstall ndiswrapper & bcm43xx-fwcutter

Open a Terminal (Applications --> Accessories --> Terminal)

[COLOR="Red"]**Copy each line into the terminal separately (do each line separately in every step)**[/COLOR]
(you can use ctrl+c to copy out of Firefox, but you have to use either ctrl+alt+v or shift+insert to paste into the terminal.)

```
sudo apt-get remove ndiswrapper-common ndiswrapper-utils-1.9

sudo apt-get remove bcm43xx-fwcutter
```

The step is complete even if it does not remove anything (you may not have had those packets installed)

[COLOR="Red"][INDENT]*If you are using Hardy you should run the following bug fix before proceading:

```
echo -e '\n#hardy ssb bug-fix\nrmmod b43\nrmmod b44\nrmmod ssb\nrmmod ndiswrapper\nmodprobe ndiswrapper\nmodprobe ssb\nmodprobe b44' | sudo tee -a /etc/init.d/rc.local
```

Edit: I updated the bug fix May 3, 2008 to add the line "modprobe b44", due to the fact that it was missing( this allows your wired lan to be configured.) Thank you to Ayuthia and the [Ubuntu documentation site]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-cbc75fcb762da2057fa8dbe904358e4b611353c0").
[/INDENT][/COLOR]
[/INDENT]

[COLOR="DarkRed"]Step 5[/COLOR]
[INDENT]Now you need to Blacklist the bcm43xx file

In the terminal you can put the following line and a text editor will pop up with the file we need to edit.

```
sudo gedit /etc/modprobe.d/blacklist
```

At the end add
```
blacklist bcm43xx
```
Do not put a # in front of it.

[COLOR="Red"]*In hardy bcm43xx is already blacklisted, but you need to add:
```
blacklist b43

```[/COLOR]

You can put it under the blacklist bcm43xxline

Save the file and close the editor

[/INDENT]

[COLOR="DarkRed"]Step 6[/COLOR]
[INDENT]If you are reading this from the web and you have not saved it or printed it, you may want to bookmark this page...(I always leave the page open and press shutdown. After you reboot, if you open Firefox it will ask you if you want to resort the session, click yes and you will be right back here....)

Reboot your computer,
[/INDENT]

[COLOR="DarkRed"]Step 7[/COLOR]
[INDENT]Lets get the drivers ready to use
Find the file you downloaded and move it to your home folder

your home folder is /home/[COLOR="Red"]yourusername
[/COLOR]
Just in case you missed it... [COLOR="Red"]yourusername[/COLOR] is your "user name"... whatever you use to log on...
You can right click it wherever it is, copy it and then go to the home folder from places and paste it

next open a terminal and type
```
tar -xzvf WLANBroadcom.tar.gz
```
Check and see, there should be a folder in you home folder called WLANBroadcom

you could also accomplish this by extracting the download to you home folder...[/INDENT]

[COLOR="DarkRed"]Step 8[/COLOR]
[INDENT]The next step is going to take some editing on your part, 

First type in the terminal the following```
uname -r
```and write down or copy to text editor (Application--> Accessories--> Text Editor)
the output
you should get something like;

2.6.22-14-generic
[/INDENT]

[COLOR="DarkRed"]Step 9[/COLOR]

Install ndiswrapper from source

[INDENT] Now you need to edit five things the following before you put it into the terminal

```
sudo apt-get update

sudo apt-get install build-essential

sudo apt-get install linux-headers-[COLOR="Red"]`uname -r`[/COLOR]

sudo ln -s /usr/src/linux-[COLOR="Red"]`uname -r`[/COLOR] /lib/modules/[COLOR="Red"]`uname -r`[/COLOR]/build

mkdir -p ~/bcm43xx/ndiswrapper

cd ~/bcm43xx/ndiswrapper

sudo wget http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-[COLOR="Red"]1.53[/COLOR].tar.gz

tar xvzf ndiswrapper-[COLOR="Red"]1.53[/COLOR].tar.gz

cd ndiswrapper*

make distclean

make

sudo make install
```

All three 'uname -r' need to be replaced with the output you got in step 8 (no " quotes should be in the code)

ie on the third line i put 

sudo apt-get install linux-headers-2.6.22-14-generic

The other two highlighted items need to be the release number you got in step 2
If it is still 1.53 just leave them like that. [/INDENT]

[COLOR="DarkRed"]Step 10[/COLOR]
[INDENT] Now we are going to install the drivers

In the terminal type

```
cd /home/[COLOR="Red"]yourusername[/COLOR]/WLANBroadcom/
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
```

Again [COLOR="Red"]yourusername[/COLOR] is your "username"
[/INDENT]

[COLOR="DarkRed"]Step 11[/COLOR]
[INDENT]Now we need to add ndiswrapper to the modules file
```
sudo gedit /etc/modules
```

just add the following at the end of the file and save and close it.
```
ndiswrapper
```
[/INDENT]

[COLOR="DarkRed"]Step 12[/COLOR]
[INDENT]
Enter in terminal
```
sudo modprobe ndiswrapper

sudo ndiswrapper -m
```



Now you can reboot again, and it should work.


Thanks to :
[[COLOR="Blue"]invaleed[/COLOR]]("http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/")
[[COLOR="Blue"]anomsuratno[/COLOR]]("http://linuxsalatiga.wordpress.com/2008/04/24/bcm43xx-ndiswrapper-in-hardy/")
[[COLOR="Blue"]doorknob60[/COLOR]]("http://ubuntuforums.org/showthread.php?t=768017")
Enjoy[/INDENT]

---

### Post by italomaia on 2008-04-27
Thank you very much dude! It worked like a charm in my Hardy Heron! ö/

---

### Post by jlandaw on 2008-04-27
No problem, glad to help

---

### Post by zspace on 2008-04-28
I just tried all of this on my HP dv6000 (same wireless model though) and it worked fine. I had to run step 9 line by line though, if I put it in all at once I got an error.
But it did work, I restated and just before login the little light turned blue.
I have no problems detecting signal strength, its kicking up my dorms wireless router at almost full strength and the one down the street shows up as a weaker signal.

Thanks a bunch!

-zspace

---

### Post by jlandaw on 2008-04-28
Great to hear its working!!

---

### Post by knaveman on 2008-04-28
gracias beyond words. I was ready to leave ubuntu over all this. confirm working on HP Pavillion DV6607nr broadcom BCM94311mcg (rev 2)

---

### Post by Alvarin on 2008-04-29
Thank you wery much for the solution . It worked for some , unfortunately , it did not work for me ... 
I have BCM94311MCG on my Presario F500 , running Hardy Heron ...

---

### Post by crobinson55331 on 2008-04-29
Thanks a bunch - I am replying wirelessly.  This was may last hurdle before committing to Ubuntu 8.04 as my business machine for my next trip to Asia.  Now i can go with confidence.

HP Pavillion dv6258se

---

### Post by zackymcharvest on 2008-04-29
BCM94311MCG wlan mini-PCI (rev 02)<---? will it work on this? I have a HP tx1000(tx1499)and its had many problems...will this work on (rev 02)? I am afraid to do this due to my bad experance with this(i have had to reinstall 4 times today) because every time i try a method it breaks all future attempts to get the wifi working. so (rev 02)??

---

### Post by Ayuthia on 2008-04-29
> **zackymcharvest said:**
> BCM94311MCG wlan mini-PCI (rev 02)<---? will it work on this? I have a HP tx1000(tx1499)and its had many problems...will this work on (rev 02)? I am afraid to do this due to my bad experance with this(i have had to reinstall 4 times today) because every time i try a method it breaks all future attempts to get the wifi working. so (rev 02)??There is a good chance that this one will work.  Most HP laptops seem to be able to use the same driver.  NDISwrapper is most likely the way to go right now for you because I have heard that the patch that allows the 4311 rev 02 chipset to work with this kernel and the b43 driver could not be applied because it breaks most of the other chipsets.

---

### Post by jlandaw on 2008-04-30
> **zackymcharvest said:**
> BCM94311MCG wlan mini-PCI (rev 02)<---? will it work on this? I have a HP tx1000(tx1499)and its had many problems...will this work on (rev 02)? I am afraid to do this due to my bad experance with this(i have had to reinstall 4 times today) because every time i try a method it breaks all future attempts to get the wifi working. so (rev 02)??
Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

My HPdv9000 has the same hardware so it will work: 

lspci | grep Broadcom

```
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
```

---

### Post by ECted on 2008-04-30
So I did this and my wireless connection in still not showing up when I go to System --> Administration --> Network. It still only shows my wired connection and point to point connection. Is there something Im missing?

--ted

---

### Post by jlandaw on 2008-04-30
First are you sure you did everything, next what is the output for;

```
lspci | grep Broadcom
```

---

### Post by VerballyCopulating on 2008-04-30
How would it be possible to do this WITHOUT an Internet connection?  Unfortunately for me, WiFi is the only possibility at the moment.  (I have a working connection in Vista and can import files to my Linux partition)

All these posts seem to me like "Here's how you get your Internet working, but one caveat, you need a working Internet connection first!"

---

### Post by Alvarin on 2008-04-30
I do have wired conneciton too , and if anyone can help me , my output for posed question is - 

03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

---

### Post by jlandaw on 2008-04-30
Ok Alvarin,

I'm trying to think of why this is not working for you.

Do you get any errors when you are doing any of the steps?

I'll try to help you, but from what i know, if you do everything in order, it will work...

---

### Post by BlueFeast on 2008-04-30
when i did this, it made my menu when clicking on the two black monitors to

"- Wired Network
_______________Wireless Networks___________
Connect to Other wireless Network...
Create New wireless Network...
-------------------------------------------
Connect to 802.1X Protected Wired Network....
Manual Configuration" 

and tells me i can use wireless but the light is still orange, maybe i dont know how to search for networks? 

the output is "03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)" when i put in ```
lspci | grep Broadcom\ Corporation
```

---

### Post by jlandaw on 2008-04-30
> **VerballyCopulating said:**
> How would it be possible to do this WITHOUT an Internet connection?  Unfortunately for me, WiFi is the only possibility at the moment.  (I have a working connection in Vista and can import files to my Linux partition)

All these posts seem to me like "Here's how you get your Internet working, but one caveat, you need a working Internet connection first!"

I am not sure, but I am working on finding out for you.

I will tell you either way soon.

---

### Post by Alvarin on 2008-05-01
[QUOTE=jlandaw]
These thing are so finicky it could be anything... I was jsut talking to someone and they forgot to put their wifi switch in the on position, so thats where i would start.

If you have a wired connection, then use it to do all the steps...[/QUOTE]

I have redone it twice , but now it WORKS !!! 
There was no difference between my last attempt and the two attempts before it , but whatever .

Thank you so much !!

---

### Post by daveerickson on 2008-05-01
jlandaw, you are the man! Thank you for compiling this information together in one easy to use place. I used this to get the wireless working on my sisters dv2000, specifically a dv2418nr, on hardy. I could not be more pleased. :)

---

### Post by das7002 on 2008-05-03
Hey this worked on my Acer Extensa 4420-5237(running hardy heron the wifi did not allow 7.04 and 7.10 to boot bcmw43xx_microcode.fw hardy heron no problem) just one edit to what is said for me it works best if you do not add
'blacklist b43' but follow the rest the light may come on and then shut off during boot up but who cares if it is on or off if it works:lolflag: anyway thanks, (openSUSE 10.3 is great but does not have Add/Remove programs that gets all the dependencies and ubuntu can use my internal wireless so go ubuntu:KS)

---

### Post by agentdave on 2008-05-03
Thank you so much for this post!  It worked in the first try when various other methods were dead ends.  

I'm currently using an HP dv2415nr notebook with the 64-bit (AMD64) version of Ubuntu 8.04 - Hardy Heron.  

My output in "lspci | grep Broadcom" gives:
...Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

As the post describes, this should work with most all HP Pavilion dv2000, dv6000, dv9000 or most Compaq Presario notebooks manufactured within the last year or two which use Broadcom wireless cards (I know, because I work at a major retailer as a technician and not much has changed on these computers internally since they started using the sleeker-looking chassis).

I searched far and wide for a solution to this problem after my own attempts failed, and I am ecstatic that this worked so easily!  And on the 64-bit platform! 

[ NOTE: I hope you don't mind my doing so, but the somewhat obvious or redundant information I included in this reply is so that others who experience this problem might be able to more easily find information when they perform searches on the forums. ]

Thank you again!

---

### Post by Ayuthia on 2008-05-03
jlandaw - Can you post your lspci -nn?  I just realized that you posted that you have a BCM94311MCG, but you did not mention which revision you are using.  I just want to confirm that it is a rev 01 instead of an 02.  From what I understand is that the rev 02 is having problems with the b43 driver (even with your fixes).

---

### Post by jlandaw on 2008-05-03
"lspci | grep Broadcom" output

03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

This works with rev 02

---

### Post by Ayuthia on 2008-05-03
> **jlandaw said:**
> "lspci | grep Broadcom" output

03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

This works with rev 02

Can you also post the "lspci -nn |grep Broadcom" output?  I want to see the chipset to see the 14e4:43xx number.  Thanks!

---

### Post by jlandaw on 2008-05-03
> **Ayuthia said:**
> Can you also post the "lspci -nn |grep Broadcom" output?  I want to see the chipset to see the 14e4:43xx number.  Thanks!

03:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 02)

---

### Post by MrPickle on 2008-05-04
Could you upload the files somewhere else please, I had to wait half an hour to download then it asked me for 4 letters with a cat (??)

Omg, screw rapidshare >:( It's telling me I'm already downloading something when I'm not and it's saying I've entered the code too many times when I haven't even entered it once.

---

### Post by viralbug on 2008-05-06
thanks a lot man! this works perfectly on my hp pavillion dv2000! :D

---

### Post by drunkmatador on 2008-05-06
Ha! Oh man I don't even believe it.. finally, wireless working on my notebook!

Thanks a million, just when I thought none of these tutorials would work. Now I just cross my fingers and hope I don't see any of the problems with random disconnects and low signal strength. :)

---

### Post by ArsHermetica on 2008-05-06
Thank you so much. Worked like a charm

Dell Inspiron 1501 Hardy Heron

---

### Post by dj_aj on 2008-05-06
Hello,

Thank you for this perfect guide! 
Got the wireless working on my HP DV6423OM in no time. I think it runs a Broadcom 4311.
Just following the steps in the guide was exactly what I needed to do...
thanks again..

---

### Post by nettobr on 2008-05-06
Very Good...

It works on my DELL 131L....   on Kubuntu 8.04 LTS 

Thanks,

NettoBR

---

### Post by vikramsharma on 2008-05-06
> **jlandaw said:**
> I'm making this Thread to Help others with the problem I had installing my BCM94311MCG wlan mini-PCI.  

I have a HP dv9000 (dv9428nr) Running Ubuntu 7.10(32 bit)[COLOR="Red"](Update: Now running Hardy 64 bit -is working but I had a little trouble setting up... I am including a bug-fix that any hardy users should use before going forward*)[/COLOR]

I do believe this will work with almost all hp dv**** and Compaq's (some forums show this to also work with dells...

Everything I put in here i have taken form other thread/forums, but none were set up in a way that a noob (Beginner) could follow easily.

First we need to do a few things.

You need to have a internet connection, wired since your wifi is not working yet :)

whenever you see the command "*sudo*" you will have to enter you password (the characters will not appear as you type.)
[COLOR="DarkRed"]
Step 1[/COLOR]
[INDENT]You will need to download the drivers we will use later.
Download it[ [COLOR="Blue"]here[/COLOR]]("http://rapidshare.com/files/70969505/WLANBroadcom.tar.gz"). It is free,just click the free button, and then click download via ******** (******** can be any one of the choices)[/INDENT]

[COLOR="DarkRed"]Step 2[/COLOR]
[INDENT]You do not have to download the next file, we will do later on, in the instillation.
Go [[COLOR="Blue"]here[/COLOR]]("http://sourceforge.net/project/showfiles.php?group_id=93482") and write down the latest stable release number. On April 21, 2008 the release  number was 1.52[/INDENT]

[COLOR="DarkRed"]Step 3[/COLOR]
[INDENT]If you enabled the restricted drivers disable them

System --> Administration --> Restricted Drivers Manager


I guess if you never tried to use them you could try before going thru this...[/INDENT]

[COLOR="Green"]One more important thing... make sure that you know what way the wifi switch must go to be on... If its off you will never get online (I just went step by step with someone, and we faild to think of the fact that his wifi card was switch off... :mad: ) Its an easy thing to miss.
On my Hpdv9000, the switch is on if it is to the right. ===>[/COLOR]

[COLOR="DarkRed"]Step 4[/COLOR]
[INDENT]Next we need to uninstall ndiswrapper & bcm43xx-fwcutter

Open a Terminal (Applications --> Accessories --> Terminal)

[COLOR="Red"]**Copy each line into the terminal separately (do each line separately in every step)**[/COLOR]
(you can use ctrl+c to copy out of Firefox, but you have to use either ctrl+alt+v or shift+insert to paste into the terminal.)

```
sudo apt-get remove ndiswrapper-common ndiswrapper-utils-1.9

sudo apt-get remove bcm43xx-fwcutter
```

The step is complete even if it does not remove anything (you may not have had those packets installed)

[COLOR="Red"][INDENT]*If you are using Hardy you should run the following bug fix before proceading:

```
echo -e '\n#hardy ssb bug-fix\nrmmod b43\nrmmod b44\nrmmod ssb\nrmmod ndiswrapper\nmodprobe ndiswrapper\nmodprobe ssb\nmodprobe b44' | sudo tee -a /etc/init.d/rc.local
```

Edit: I updated the bug fix May 3, 2008 to add the line "modprobe b44", due to the fact that it was missing( this allows your wired lan to be configured.) Thank you to Ayuthia and the [Ubuntu documentation site]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-cbc75fcb762da2057fa8dbe904358e4b611353c0").
[/INDENT][/COLOR]
[/INDENT]

[COLOR="DarkRed"]Step 5[/COLOR]
[INDENT]Now you need to Blacklist the bcm43xx file

In the terminal you can put the following line and a text editor will pop up with the file we need to edit.

```
sudo gedit /etc/modprobe.d/blacklist
```

At the end add
```
blacklist bcm43xx
```
Do not put a # in front of it.

[COLOR="Red"]*In hardy bcm43xx is already blacklisted, but you need to add:
```
blacklist b43

```[/COLOR]

You can put it under the blacklist bcm43xxline

Save the file and close the editor

[/INDENT]

[COLOR="DarkRed"]Step 6[/COLOR]
[INDENT]If you are reading this from the web and you have not saved it or printed it, you may want to bookmark this page...(I always leave the page open and press shutdown. After you reboot, if you open Firefox it will ask you if you want to resort the session, click yes and you will be right back here....)

Reboot your computer,
[/INDENT]

[COLOR="DarkRed"]Step 7[/COLOR]
[INDENT]Lets get the drivers ready to use
Find the file you downloaded and move it to your home folder

your home folder is /home/[COLOR="Red"]yourusername
[/COLOR]
Just in case you missed it... [COLOR="Red"]yourusername[/COLOR] is your "user name"... whatever you use to log on...
You can right click it wherever it is, copy it and then go to the home folder from places and paste it

next open a terminal and type
```
tar -xzvf WLANBroadcom.tar.gz
```
Check and see, there should be a folder in you home folder called WLANBroadcom

you could also accomplish this by extracting the download to you home folder...[/INDENT]

[COLOR="DarkRed"]Step 8[/COLOR]
[INDENT]The next step is going to take some editing on your part, 

First type in the terminal the following```
uname -r
```and write down or copy to text editor (Application--> Accessories--> Text Editor)
the output
you should get something like;

2.6.22-14-generic
[/INDENT]

[COLOR="DarkRed"]Step 9[/COLOR]

Install ndiswrapper from source

[INDENT] Now you need to edit five things the following before you put it into the terminal

```
sudo apt-get update

sudo apt-get install build-essential

sudo apt-get install linux-headers-[COLOR="Red"]`uname -r`[/COLOR]

sudo ln -s /usr/src/linux-[COLOR="Red"]`uname -r`[/COLOR] /lib/modules/[COLOR="Red"]`uname -r`[/COLOR]/build

mkdir -p ~/bcm43xx/ndiswrapper

cd ~/bcm43xx/ndiswrapper

sudo wget http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-[COLOR="Red"]1.52[/COLOR].tar.gz

tar xvzf ndiswrapper-[COLOR="Red"]1.52[/COLOR].tar.gz

cd ndiswrapper*

make distclean
make
sudo make install
```

All three 'uname -r' need to be replaced with the output you got in step 8 (no " quotes should be in the code)

ie on the third line i put 

sudo apt-get install linux-headers-2.6.22-14-generic

The other two highlighted items need to be the release number you got in step 2
If it is still 1.52 just leave them like that. [/INDENT]

[COLOR="DarkRed"]Step 10[/COLOR]
[INDENT] Now we are going to install the drivers

In the terminal type

```
cd /home/[COLOR="Red"]yourusername[/COLOR]/WLANBroadcom/
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
```

Again [COLOR="Red"]yourusername[/COLOR] is your "username"
[/INDENT]

[COLOR="DarkRed"]Step 11[/COLOR]
[INDENT]Now we need to add ndiswrapper to the modules file
```
sudo gedit /etc/modules
```

just add the following at the end of the file and save and close it.
```
ndiswrapper
```
[/INDENT]

[COLOR="DarkRed"]Step 12[/COLOR]
[INDENT]
Enter in terminal
```
sudo modprobe ndiswrapper

sudo ndiswrapper -m
```



Now you can reboot again, and it should work.


Thanks to :
[[COLOR="Blue"]invaleed[/COLOR]]("http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/")
[[COLOR="Blue"]anomsuratno[/COLOR]]("http://linuxsalatiga.wordpress.com/2008/04/24/bcm43xx-ndiswrapper-in-hardy/")
[[COLOR="Blue"]doorknob60[/COLOR]]("http://ubuntuforums.org/showthread.php?t=768017")
Enjoy[/INDENT]

Thanks a lot buddy your advice really helped me out, now I have wireless working flawlessly on my laptop.

---

### Post by alaya.zied on 2008-05-07
I add a thanks from me jlandaw :o

it work for me
I have a dv6420 with Broadcom BCM94311MCG.

after the final reboot it detect the wireless network and I have an excellent signal

when I try a little ping, I have:
> ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
:confused:

I stopped ufw (new firewall on hardy) and I have now:
> 64 bytes from 172.16.1.1: icmp_seq=1 ttl=64 time=16.4 ms
64 bytes from 172.16.1.1: icmp_seq=2 ttl=64 time=11.7 ms
64 bytes from 172.16.1.1: icmp_seq=3 ttl=64 time=22.4 ms

now I can enjoy my Hardy
:popcorn:

---

### Post by Axis on 2008-05-08
Hello you responded to my topic about my wireless not working before. I am using a compaq presario f500 with 8.04. Well I followed your steps and my wireless is on now. I just can't connect to anything. I can see the networks that are broadcasting and I can't seem to connect to any of them. I have tried removing encryption but it didn't change my results at all. If it matters the wireless light is on now, and all of my programs (and ubuntu) recognize that I have wireless. Just can't connect

 Thanks,
Axis

EDIT:
It appears to work fine if you enable roaming mode and select your networks that way.Very glad to see this finally working it means so much to me, thanks a ton man!

---

### Post by tlxreed on 2008-05-10
This thread works great for me on a dv9000. I had to turn off WPA Personal on my router to get a connection, but I'm surfing wirelessly now. Thanks!

---

### Post by txcrackers on 2008-05-11
The Wife is now happy - got her 4311 working again. One change is that I actually used the ndiswrapper package from the repositories, instead of building it. (Laptop is a Compaq v6000.)

---

### Post by Lori Whitty on 2008-05-14
All I can say is THANK YOU...THANK YOU...THANK YOU!!!!!  I am BRAND NEW to linux and ubuntu and have spent the last day and a half researching how to make my wireless work.  I tried MANY other ways but yours FINALLY did it for me.  I'm EXTREMELY grateful for your post.  My wireless is working beautifully now.

I'm a much happier new user thanks to your post.  :)

---

### Post by Infini on 2008-05-16
Still not working... No matter what I try nothing ever works. I can see the network but it won't connect. I enter the passphrase and one of the little things go green while the other remains grey and then it prompts me for the passphrase again after trying for a while.

---

### Post by newbreed on 2008-05-16
dude...  DUDE!...sweet. worked great, just won tut of the year, thanks.

---

### Post by lola23 on 2008-05-16
Still no luck for me :(  I can see my WEP network but can't connect, it tries to apply the WEP key and fails.

Hardy on Dell Inspiron E1505 with Broadcom BCM94311MCG card.  Output of lspci -nn:

*0b:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)*

Tried nuking the network manager and installing wcid as suggested in one of the threads - better interface, still doesn't work.

Really lost at this point... re-installed Hardy, ndiswrapper and bcmwl5, doesn't seem to help.

Any suggestions? :confused:  Thanks!

---

### Post by Ayuthia on 2008-05-16
> **lola23 said:**
> Still no luck for me :(  I can see my WEP network but can't connect, it tries to apply the WEP key and fails.

Hardy on Dell Inspiron E1505 with Broadcom BCM94311MCG card.  Output of lspci -nn:

*0b:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)*

Tried nuking the network manager and installing wcid as suggested in one of the threads - better interface, still doesn't work.

Really lost at this point... re-installed Hardy, ndiswrapper and bcmwl5, doesn't seem to help.

Any suggestions? :confused:  Thanks!

What does lshw -C network, ndiswrapper -v, and ndiswrapper -l show?

---

### Post by Praxicoide on 2008-05-17
No luck on a Compaq Presario V3000 with a Broadcom 4311 (rev 02).

It istalled the driver, but still no wireless. iwconfig just shows lo and eth0 (no wlan0).

ndiswrapper -l states:
bcmwl5 : driver installed
         device (14E4:4311) present (alternate driver: bcm43xx)

EDIT:

lshw -C network

product: BCM94311MCG wlan mini-PCI
wendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:04:00.0
version: 02
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: driver_b43-pci-bridge latency=0 module=ssb

hmm....it seems I have the b43 driver? I blacklisted it as indicated, but maybe the bugfix wasn't successful. What can I do?

---

### Post by lola23 on 2008-05-17
> **Ayuthia said:**
> What does lshw -C network, ndiswrapper -v, and ndiswrapper -l show?

lshw -C network

```
 *-network DISABLED      
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wlan0
       version: 01
       serial: 00:16:ce:3a:af:b3
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:16:d1:5c
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.34 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s


```

ndiswrapper -v

```
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-16-generic SMP mod_unload 586 

```

ndiswrapper -l

```
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: ssb)

```

I guess it's showing that my wlan0 (wireless) is disabled??

---

### Post by Ayuthia on 2008-05-17
> **lola23 said:**
> lshw -C network

```
 *-network DISABLED      
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wlan0
       version: 01
       serial: 00:16:ce:3a:af:b3
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:16:d1:5c
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.34 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s


```

ndiswrapper -v

```
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-16-generic SMP mod_unload 586 

```

ndiswrapper -l

```
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: ssb)

```

I guess it's showing that my wlan0 (wireless) is disabled??

You are one of the people that needs to have ssb so that your wired ethernet card will work.  If you look at your other card, you will see the b44 driver.  That driver needs ssb.

Just for now, I would try to remove ssb just to see if you can just get your wireless back up:
```
sudo modprobe -r b43 b44 ssb ndiswrapper
sudo modprobe ndiswrapper
```
If it doesn't work, you can enable your wired connection again by:
```
sudo modprobe b44
```.  If it does, try connecting your wired again.

---

### Post by sixstorm on 2008-05-18
OMG!  Thank you so much for this guide, I've been going crazy having to wire my laptop connection up every time.  

MODS - STICKY THIS THREAD!!!!

---

### Post by lola23 on 2008-05-18
> **Ayuthia said:**
> You are one of the people that needs to have ssb so that your wired ethernet card will work.  If you look at your other card, you will see the b44 driver.  That driver needs ssb.

Just for now, I would try to remove ssb just to see if you can just get your wireless back up:
```
sudo modprobe -r b43 b44 ssb ndiswrapper
sudo modprobe ndiswrapper
```
If it doesn't work, you can enable your wired connection again by:
```
sudo modprobe b44
```.  If it does, try connecting your wired again.

That didn't seem to help :(  So you are saying that my problem is a conflict between ssb for wired ethernet card and wireless drivers??

---

### Post by Ayuthia on 2008-05-18
> **lola23 said:**
> That didn't seem to help :(  So you are saying that my problem is a conflict between ssb for wired ethernet card and wireless drivers??
No, the new Broadcom drivers are now using ssb which is causing a conflict with NDISwrapper.  The new Broadcom drivers are b43 (wireless) and b44 (wired).  

The reason why I asked you to do this was to make sure that there was not a conflict.  Since NDISwrapper still did not start up even though we removed the b44 and ssb drivers, we know that the wired card is not causing any problems.

Yours almost looks like your wireless is turned off.  Do you have a switch to turn it on?  If it is on, what happens when you go to the Terminal and type:
```
sudo ifconfig wlan0 up
sudo iwlist scan
```

---

### Post by jokobe on 2008-05-19
This was really helful, sticked to your howto and it was working...

---

### Post by Ayuthia on 2008-05-19
> **Praxicoide said:**
> No luck on a Compaq Presario V3000 with a Broadcom 4311 (rev 02).

It istalled the driver, but still no wireless. iwconfig just shows lo and eth0 (no wlan0).

ndiswrapper -l states:
bcmwl5 : driver installed
         device (14E4:4311) present (alternate driver: bcm43xx)

EDIT:

lshw -C network

product: BCM94311MCG wlan mini-PCI
wendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:04:00.0
version: 02
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: driver_b43-pci-bridge latency=0 module=ssb

hmm....it seems I have the b43 driver? I blacklisted it as indicated, but maybe the bugfix wasn't successful. What can I do?

Can you post your ndiswrapper -v and lspci -nn?  The fix is not always necessary.  The fix is needed if your wired card uses the b44 driver.  Once you post the information, we can then test NDISwrapper by removing the necessary modules and loading ndiswrapper.  When that is working, we can then configure the rest.

---

### Post by Praxicoide on 2008-05-20
I redid the guide and wireless works! Sorry for not updating sooner.

Thank you very much all involved. the configuration field on the lshw -C network now says ndiswrapper, not ssb like before.

---

### Post by imnotatfault on 2008-05-20
I followed the guide to a T. Rebooted and successfully found all network. Connected and was on my way, or so I thought. The internet, while functional, is crawling.

I'm currently downloading package files from between 1 and 3kb/s(not a typo). I am at my wit's end.

Edit: Here's some info that may help (maybe?)
 I'm running an Asus Barebones V2-M2V890 AMD with an Athlon Sempron Dual Core
 installed 8.04 Hardy Heron i386 and used the bug fix in the guide
 ASUS WL-138G V2 (Broadcom 4318 Air Force One 54G
 I used Step 2a and did not have to compile ndiswrapper from source.

After installation, networks were viewable and speeds actually seemed normal for a second. Then I rebooted and that brought me to the 3kb/s realm (4kb/s on network transfers between computers).

---

### Post by ygrof on 2008-05-20
What a detailed guide! Great for Linux noobs like me:)

Thank you so much for putting this up! I had been trying for days to get the wireless working on my HP tx1305...what a relief when the light finally turned blue!

---

### Post by Tavish on 2008-05-20
This is amazing, thanks so much!  It works like a charm now!

HP Compaq 6515b

---

### Post by sherwin on 2008-05-21
Thank you, thank you, thank you!  Perfect on Pavilion dv6625us with 8.04.  I wish I'd seen this thread first instead of wasting hours following other people's instructions!

---

### Post by Troca on 2008-05-22
Holy ******* **** it worked !!!! Thank you so much i want to make sweeeeet love to you almost. This was driving me nuts tryed several tutorials be4 i read yours and yours is the only easyone to follow for a beginner like me pluss it works THANK YOU SOOOOOOOOOOOO MUTCH dude

---

### Post by doctored on 2008-05-23
Thanks! I was getting very mixed up with advice from all over the place, but your idiot-proof (I'm proof of that) guide WORKED!! (on a Compaq Presario F500).

---

### Post by Troca on 2008-05-23
same laptop as me doctored and yes this tutorial rocks !!! :)

---

### Post by SonicSteve on 2008-05-23
Hi folks,
I really hope someone can help me with this. I'm having problems installing Ndiswrapper. I had this working under gutsy gibbon 7.10. However it had other issues which Hardy Heron 8.04 solved, sound card related.

I'm using a Compaq F700 based Laptop. It is definately using the broadcom 94311 r.2 wireless adapter. 

I've successfully done all the steps up to;
make distclean
make 
sudo make install

I believe that the make distclean command worked properly but the make and make install commands have errors. This is the output from all 3 commands, it's a bit lengthy.
You'll notice that I used sudo in front of distclean, this was an act of desperation and it seems to have had no consequence.

  	 	 	 	 	[PHP]steve@Compaq-buntu:~/bcm43xx/ndiswrapper/ndiswrapper-1.49$ sudo make distclean  
 make -C driver clean  
 make[1]: Entering directory `/home/steve/bcm43xx/ndiswrapper/ndiswrapper-1.49/driver'  
 rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapper.o usb.o divdi3.o usb.o win2lin_stubs.o \  
 	   divdi3.o workqueue.o .*.ko.cmd .*.o.cmd  compat.h \  
 	   ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers  
 make[1]: Leaving directory `/home/steve/bcm43xx/ndiswrapper/ndiswrapper-1.49/driver'  
 make -C utils clean  
 make[1]: Entering directory `/home/steve/bcm43xx/ndiswrapper/ndiswrapper-1.49/utils'  
 rm -f *~ *.o loadndisdriver  
 make[1]: Leaving directory `/home/steve/bcm43xx/ndiswrapper/ndiswrapper-1.49/utils'  
 rm -f *~  
 rm -fr ndiswrapper-1.49 ndiswrapper-1.49.tar.gz patch-stamp  
 make -C driver distclean  
 make[1]: Entering directory `/home/steve/bcm43xx/ndiswrapper/ndiswrapper-1.49/driver'  
 rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapper.o usb.o divdi3.o usb.o win2lin_stubs.o \  
 	   divdi3.o workqueue.o .*.ko.cmd .*.o.cmd  compat.h \  
 	   ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers  
 rm -f *_exports.h .\#* win2lin_stubs.h built-in.o  
 make[1]: Leaving directory `/home/steve/bcm43xx/ndiswrapper/ndiswrapper-1.49/driver'  
 make -C utils distclean  
 make[1]: Entering directory `/home/steve/bcm43xx/ndiswrapper/ndiswrapper-1.49/utils'  
 rm -f *~ *.o loadndisdriver  
 rm -f .\#*  
 make[1]: Leaving directory `/home/steve/bcm43xx/ndiswrapper/ndiswrapper-1.49/utils'  
 rm -f .\#*  
 steve@Compaq-buntu:~/bcm43xx/ndiswrapper/ndiswrapper-1.49$ sudo make  
 make -C driver  
 make[1]: Entering directory `/home/steve/bcm43xx/ndiswrapper/ndiswrapper-1.49/driver'  
 make -C /usr/src/linux-headers-2.6.24-17-generic SUBDIRS=/home/steve/bcm43xx/ndiswrapper/ndiswrapper-1.49/driver  
 make[2]: Entering directory `/usr/src/linux-headers-2.6.24-17-generic'  
 scripts/Makefile.build:46: *** CFLAGS was changed in "/home/steve/bcm43xx/ndiswrapper/ndiswrapper-1.49/driver/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.  
 make[2]: *** [_module_/home/steve/bcm43xx/ndiswrapper/ndiswrapper-1.49/driver] Error 2  
 make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-17-generic'  
 make[1]: *** [default] Error 2  
 make[1]: Leaving directory `/home/steve/bcm43xx/ndiswrapper/ndiswrapper-1.49/driver'  
 make: *** [all] Error 2  
 steve@Compaq-buntu:~/bcm43xx/ndiswrapper/ndiswrapper-1.49$ sudo make install  
 make -C driver install  
 make[1]: Entering directory `/home/steve/bcm43xx/ndiswrapper/ndiswrapper-1.49/driver'  
 make -C /usr/src/linux-headers-2.6.24-17-generic SUBDIRS=/home/steve/bcm43xx/ndiswrapper/ndiswrapper-1.49/driver  
 make[2]: Entering directory `/usr/src/linux-headers-2.6.24-17-generic'  
 scripts/Makefile.build:46: *** CFLAGS was changed in "/home/steve/bcm43xx/ndiswrapper/ndiswrapper-1.49/driver/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.  
 make[2]: *** [_module_/home/steve/bcm43xx/ndiswrapper/ndiswrapper-1.49/driver] Error 2  
 make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-17-generic'  
 make[1]: *** [default] Error 2  
 make[1]: Leaving directory `/home/steve/bcm43xx/ndiswrapper/ndiswrapper-1.49/driver'  
 make: *** [install] Error 2  
 steve@Compaq-buntu:~/bcm43xx/ndiswrapper/ndiswrapper-1.49$ 
 [/PHP]

Take note of all the "Error 2" remarks. Does anyone know what's going wrong with this? Please help me, I don't want to use Vista, and I know this can work if Ndiswrapper would just install.

---

### Post by Ayuthia on 2008-05-23
> **SonicSteve said:**
> 
Take note of all the "Error 2" remarks. Does anyone know what's going wrong with this? Please help me, I don't want to use Vista, and I know this can work if Ndiswrapper would just install.
The errors show up because you are using version 1.49 of NDISwrapper.  Versions 1.50 and higher support the 2.6.24 kernel (The one that is used in Hardy).  You might try using the 1.52 version from NDISwrapper or just use the ones from the repositories (or the Hardy liveCD).

---

### Post by SonicSteve on 2008-05-23
> **Ayuthia said:**
> The errors show up because you are using version 1.49 of NDISwrapper.  Versions 1.50 and higher support the 2.6.24 kernel (The one that is used in Hardy).  You might try using the 1.52 version from NDISwrapper or just use the ones from the repositories (or the Hardy liveCD).

It's times like this I love the Ubuntu community. These errors were happening because I'm using the same home folder that I had from Gutsy Gibbon. Remember I said that I had this working with that version? The generic directory calls used in the tutorial found the 1.49 folder because it was first. So all the make commands were happening in that folder instead of the 1.52 folder!

It works, thank you so much Ayuthia thank you thank you thank you.

In the words of Dr. Frankenstein, (which my wife just called because of my silly evil laugh that she over heard when things started working) 

ITS ALIVE!!!

---

### Post by fjcurcio on 2008-05-24
I have an HP Pavillion DV6000. Dumped Vista, installed Hardy; all good except wireless!

when i do an lspci - there is NO sign of a wireless card. 

nonethless i followed this post and all the install went fine.
when i do an ndisrapper -l i get a return saying the bcmwl5 driver is installed, but nothing about the devive being present.

any help greatly appreciated!!

TIA

---

### Post by idanool on 2008-05-24
Hi!

I'm using HP G7000 laptop. exact same wlan card (lspci). Ubuntu Hardy. 
I tried to follow the instructions on the guide, and didn't notice any errors. 
It seems that now the wireless networks around are discovered, and even it asks me for my authentication (WEP2) key, but it still doesn't connect to my network.
I tried to change to WEP or no authentication and still can't connect.
wired networks works. connect from another computer to my wireless network also works.

$sudo lspci | grep Broadcom
01:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

$sudo ndiswrapper -i bcmwl5.inf
driver bcmwl5 is already installed

$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: ssb)

$sudo ndiswrapper -m
module configuration already contains alias directive

any ideas ?

I used the link [http://www.stosha.net/WLANBroadcom.tar.gz](http://www.stosha.net/WLANBroadcom.tar.gz)
which I found on [http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/)
which is much faster then the rapidshare link (at least for me:)

---

### Post by -Morgoth- on 2008-05-25
nvm, i got it working. Thanks for the excellent guide :)

---

### Post by Karamiekos on 2008-05-25
This was awesome.  As soon as I saw my little blue WLAN light on my HP DV6408nr with a BCM94311MCG Rev 2, I jumped for Joy!!!!

OUTSTANDING!  Simply OUTSTANDING.  The only thing I also had to look at was here...
[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

Some of the settings in the network interfaces were off, but that page fixed my right up.  

TWO THUMBS UP!!

---

### Post by syga on 2008-05-25
These instructions worked for me!

I thought I had a problem, the first time I rebooted, the wifi light took more than 1 minute to turn on after logging on.

Now, the wifi light turns on during the boot process. 

Also, I'm dual booting with XP. Instead of downloading your files, I just copied bcmwl5 from Windows to my root folder, then made a few minor changes to your instructions. 

Thanks.

---

### Post by jocheem67 on 2008-05-25
I've got a success too...

Actually it's been a while since I used ndiswrapper, but was forced into it again cause I want to use wpa2.
The b43 doesn't seem to work on this, so I got directed to your howto. 
And a nice one it is!!:guitar:

Oh yeah...this is done on a dell 9400...

---

### Post by onetimeposter on 2008-05-26
I registered for this one post, because so many people were saying that they had fixed their problems without stating how. (Very frustrating.)

I followed the instructions perfectly, but I was having the problem listed here:

> **BlueFeast said:**
> when i did this, it made my menu when clicking on the two black monitors to

"- Wired Network
_______________Wireless Networks___________
Connect to Other wireless Network...
Create New wireless Network...
-------------------------------------------
Connect to 802.1X Protected Wired Network....
Manual Configuration" 



i.e., I was seeing my wired connection and not my wireless. So I tried this:

> **Ayuthia said:**
> You are one of the people that needs to have ssb so that your wired ethernet card will work.  If you look at your other card, you will see the b44 driver.  That driver needs ssb.

Just for now, I would try to remove ssb just to see if you can just get your wireless back up:
```
sudo modprobe -r b43 b44 ssb ndiswrapper
sudo modprobe ndiswrapper
```

That didn't work (or so I thought). So, I tried the above plus Ayuthia's next piece of advice (using the terminal to turn on the wireless card; a software on/off switch):

> **Ayuthia said:**
> 

Yours almost looks like your wireless is turned off.  Do you have a switch to turn it on?  If it is on, what happens when you go to the Terminal and type:
```
sudo ifconfig wlan0 up
sudo iwlist scan
```

Worked. Apparently, my hardware switch to turn my wireless card on and off isn't working properly. Then I re-enabled my wired:

> **Ayuthia said:**
> You can enable your wired connection again by:
```
sudo modprobe b44
```

And they both work now.

I am running a Dell Inspiron E1705.
Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)

If this helps anyone, please thank Ayuthia and jlandaw.
I am merely a onetimeposter.

---

### Post by WarningXdezzy on 2008-05-26
Thanks a million solved my problem completely

---

### Post by jocheem67 on 2008-05-27
Huh??

How can it be that after a kernel-upgrade, I actually don't have to compile ndiswrapper again??

Everything just keeps on working after going from the .16 to the .17 kernel..

---

### Post by doorknob60 on 2008-05-29
> **jocheem67 said:**
> Huh??

How can it be that after a kernel-upgrade, I actually don't have to compile ndiswrapper again??

Everything just keeps on working after going from the .16 to the .17 kernel..

Probably no incompatabilities that stop it from working or something? Idk. Anyways, thanks for making this guide, I just recommended it to soemone who's brand new to Ubuntu from another site, and I was glad to see my name in the Thanks To list :), let's hope it works OK for him (he has a presario f500).

---

### Post by aemdb on 2008-05-30
Many thanks for this tutorial! I was fighting with b43 drivers but without results. Following your guide I got my Compaq Presario F562LA wifi working! I'm using Ubuntu Hardy 8.04.

---

### Post by telescopic on 2008-05-31
I have hp dv6000 with amd64 and bcm9311. The steps works temporarily for me as i found out the connection is lost some minutes later, although it shows I am still connected. I have to disable and enable the wireless network for it works again.

---

### Post by nizox on 2008-06-01
This worked perfectly and was very easy to follow. 

Thank you very much!

---

### Post by Tuxor on 2008-06-02
Great! Helped me out on an upgraded (7.10->8.04) HP/Compaq 6720s, which lost the wlan in the upgrade. Worked the first time following your good guide. Perfect.

---

### Post by rabalder on 2008-06-03
Worked great on my pavilion zv5000 with Hardy
couldn't get the driver file through rapidshare though, I found these mirrrors:

[http://www.stosha.net/WLANBroadcom.tar.gz]("http://www.stosha.net/WLANBroadcom.tar.gz")

[http://stosha.stylet-software.com/WLANBroadcom.tar.gz]("http://stosha.stylet-software.com/WLANBroadcom.tar.gz")

---

### Post by PerceptionX on 2008-06-03
Feels GREAT!!!

Finally Wireless!!!!!
I am a new Linux user, THANKS A LOT!!!!!!!!!!! REALLY. Linux had been sitting in my laptop useless for many month.

I just have a little final doubt, just as I reboot my computer and finally got wireless conection, the update arrow in the tray sistem appears and marks to new security updates which look very suspecious. One says linux-libc-dev, and the other linux-restricted-modules-common. I didnt install them fearing they could restore the previous configuration, thus killing wireless. Should I ever install them?

Then again, THANK YOU. You should post this in many other pages, there are probably thousands looking for a guide that actually works.

---

### Post by ljungkvist on 2008-06-03
Hi!

Thanks alot, this solved it nicely for me as well.

Perhaps you should try to compile a list over the computer models/network adapters that have worked so far. I'm using a Compaq Presario V6000 with the BCM94311MCG card and Ubuntu 8.04.

Thanks again!

---

### Post by MrPickle on 2008-06-03
Here's a download that's not rapidshare. [http://www.stosha.net/WLANBroadcom.tar.gz](http://www.stosha.net/WLANBroadcom.tar.gz)

---

### Post by saveferris7872 on 2008-06-03
this guide FTW!!

i have tried so many other guides online that i had just about given up. this was seriously going to be my last attempt at getting wifi working before just using wired permanently.

worked like a charm on my HP dv6636nr. thanks man!

---

### Post by geddyprogshred on 2008-06-03
aaaand you my friend are a SAINT!!!!

you don't even know how long i spent trying to make my wireless work. this little howto finally laid it all out perfectly for me. even taught a newb like me some new linux commands.

btw, my computer is an hp pavillion dv6660se notebook . a list of computers that this worked for would be a great help for anybody looking in the future

---

### Post by rafter109 on 2008-06-04
Thanks a bunch. Worked like a charm!

My system is as follows
Ubuntu 8.04 Desktop 2.6.24-18-generic
on HP Pavilion dv9205us
with Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

Tried fwcutter method before this to no avail.

---

### Post by rootie on 2008-06-05
[SOLVED!]

got a split-second message on shutdown. checked my error logs, which directed me to [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43). I don't know why I never tried this before, but it worked!

<old help request follows>

Hey there, I'm on a Lenovo 3000 and have the same Broadcom wifi card. I tried the tutorial above but it didn't work. I'll try to outline the problems I had.

I couldn't `make distclean' ndiswrapper
error: 
```
make[1]: Entering directory '~/bcm43xx/ndiswrapper/ndiswrapper-1.53/driver/'
make[1]: No rule to make target `distclean'. Stop.
make[1]: Leaving directory '~/bcm43xx/ndiswrapper/ndiswrapper-1.53/driver/'
make: *** [distclean] Error 2
```

In an act of desperation, I checked the liveCD to see if it contained an ndiswrapper package and installed that. Entering `ndiswrapper -l' I got the following as output:
```
bcmwl5: driver installed
	device (14E4:4311) present (alternate driver: bcm43xx)
```

So, I followed the rest of the tutorial.

The next roadblock I hit was on reboot. There was a problem unpacking the driver--unfortunately, I didn't catch the error. The driver is listed under 'Restricted Devices' as 'not in use.' When I click to activate it it tells me to reboot. This occurs ad nauseam.

ifconfig doesn't return the wlan entry. nmapplet doesn't have a Wireless option.

I hope someone can help with this. Thanks :)

Edit: By the way, I was in fact trying to use ndiswrapper 1.53. However, the version I actually installed (via liveCD) was 1.50.

---

### Post by Abhinav Gupta on 2008-06-05
Hi,
 I cannot thank you enough!!!! I am completely new to linux, and the posts on other forums for this fix were very confusing for me, especially the bit about adding a blacklist line. I used to add this line in the terminal!
Your instructions were, though, clear as crystal, and such instructions are required to convert newbees like me to linux! Thanks a lot again!
Abhinav.

---

### Post by *shiki on 2008-06-07
This solution worked like a charm. I was about to give up on Ubuntu for my HP. It would have been a shame since I currently use it on my dell and am very happy with it. :D

---

### Post by kj7lo on 2008-06-08
I did a clean install on 8.04 from 7.10 on my HP tx1000 and it blew away my wireless.  Your instructions worked perfectly.  I wish I understood what I did!  Thank you *VERY* much!

Jeff

---

### Post by SteelDragon on 2008-06-08
> **rootie said:**
> [SOLVED!]

got a split-second message on shutdown. checked my error logs, which directed me to [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43). I don't know why I never tried this before, but it worked!


I'm getting the same error as described in your pre-edit post, but I can't figure out what it is you found in that link that solved the problem. Do you mind being more specific about what was in your error log and what you did to fix it?

Thanks

SD

---

### Post by Ayuthia on 2008-06-08
> **SteelDragon said:**
> I'm getting the same error as described in your pre-edit post, but I can't figure out what it is you found in that link that solved the problem. Do you mind being more specific about what was in your error log and what you did to fix it?

Thanks

SDI am not the poster of the quote in your post, but the message that the poster is referring is the message for the b43 firmware in dmesg.  If you open the Terminal and type dmesg, you will find a message somewhere for the b43 drivers.  It will refer you to a site where you can get the firmware.  This is the same thing as using b43-fwcutter.  You can install it by using this [link]("http://ubuntuforums.org/showthread.php?t=779754").  You can also install the application in that link and it will configure the b43 driver if you have already installed NDISwrapper based on this guide.

---

### Post by Matt Damon on 2008-06-09
Compaq presario C500 running Hardy, just recently upgraded from Gutsy whereupon my wireless quit and sound is shattered.  Fortunately everything else (including wired) is OK.  I ran these instructions, everything seemed to run OK, but after the reboot at the end I seem to have 'lost' my wireless hardware...


miked@miked-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d4:e6:f8:ed  
          inet addr:192.168.2.33  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:fee6:f8ed/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3375 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3540 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2906580 (2.7 MB)  TX bytes:750630 (733.0 KB)
          Interrupt:20 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1122 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1122 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:56100 (54.7 KB)  TX bytes:56100 (54.7 KB)

miked@miked-laptop:~$ 
miked@miked-laptop:~$ aplay
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
aplay: main:546: audio open error: Device or resource busy
miked@miked-laptop:~$ aplay
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
aplay: main:546: audio open error: Device or resource busy
miked@miked-laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
	Subsystem: Hewlett-Packard Company Unknown device 30a5
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Unknown device 30a5
	Flags: bus master, fast devsel, latency 0, IRQ 20
	Memory at d0200000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 1800 [size=8]
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Memory at d0300000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Hewlett-Packard Company Unknown device 30a5
	Flags: bus master, fast devsel, latency 0
	Memory at d0280000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Hewlett-Packard Company Unknown device 30a5
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at d0340000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	Memory behind bridge: 30000000-300fffff
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30a5
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30a5
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30a5
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 1860 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30a5
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at d0544000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=32
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: d0100000-d01fffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
	Subsystem: Hewlett-Packard Company Unknown device 30a5
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
	Subsystem: Hewlett-Packard Company Unknown device 30a5
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1810 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01) (prog-if 01 [AHCI 1.0])
	Subsystem: Hewlett-Packard Company Unknown device 30a5
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 221
	I/O ports at 18b0 [size=8]
	I/O ports at 18a4 [size=4]
	I/O ports at 18a8 [size=8]
	I/O ports at 18a0 [size=4]
	I/O ports at 1890 [size=16]
	Memory at d0544400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
	Subsystem: Hewlett-Packard Company Unknown device 30a5
	Flags: medium devsel, IRQ 10
	I/O ports at 18c0 [size=32]

06:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
	Subsystem: Hewlett-Packard Company Unknown device 1364
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at 30000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

08:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Hewlett-Packard Company Unknown device 30a5
	Flags: bus master, medium devsel, latency 32, IRQ 20
	I/O ports at 2000 [size=256]
	Memory at d0100000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

miked@miked-laptop:~$

---

### Post by Ayuthia on 2008-06-09
> **Matt Damon said:**
> Compaq presario C500 running Hardy, just recently upgraded from Gutsy whereupon my wireless quit and sound is shattered.  Fortunately everything else (including wired) is OK.  I ran these instructions, everything seemed to run OK, but after the reboot at the end I seem to have 'lost' my wireless hardware...If you compiled NDISwrapper in Gutsy, you will need to get a new version of NDISwrapper (1.50 or higher) and will most likely need to reinstall the bcmwl5 driver.

---

### Post by ivarkvaal on 2008-06-09
SOLVED!

Hi,

thanks for the guide. I have tried, and re-tried it several times now, without any luck... Maybe someone here can help me figure out what I'm doing wrong.

- Computer: HP Pavilion dv6000.
- I have done all the steps in the guide, from a fresh Ubuntu 8.04 install.
- I have not enabled the restricted wireless driver.
- I get the blue light indicator on my wireless card.
- I can see some networks, but not my own. I cannot connect to any wireless networks.

I suspect the issue is related to ndiswrapper. I got this error when I tried the 'make distclean' command (even though it's from a fresh install).

```
make -C driver clean
make[1]: Entering directory `/home/magnhild/ndiswrapper-1.53/driver'
rm -f *.o *.ko .*.cmd *.mod.c *.symvers modules.order *~ .\#*
rm -f *_exports.h win2lin_stubs.h
rm -rf .tmp_versions
make[1]: Leaving directory `/home/magnhild/ndiswrapper-1.53/driver'
make -C utils clean
make[1]: Entering directory `/home/magnhild/ndiswrapper-1.53/utils'
rm -f *~ *.o loadndisdriver
make[1]: Leaving directory `/home/magnhild/ndiswrapper-1.53/utils'
rm -f *~
rm -fr ndiswrapper-1.53 ndiswrapper-1.53.tar.gz patch-stamp
make -C driver distclean
make[1]: Entering directory `/home/magnhild/ndiswrapper-1.53/driver'
make[1]: *** No rule to make target `distclean'.  Stop.
make[1]: Leaving directory `/home/magnhild/ndiswrapper-1.53/driver'
make: *** [distclean] Error 2

```

ndiswrapper -l output

```
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: ssb)

```

lshw -C network output
```
 *-network               
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:1a:73:2e:66:8f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
```

any ideas? Thanks!

EDIT:

I can actually connect to open networks... but I cant even see my own wep network. I have several other machines connected to it, so I know it the wireless router works...

EDIT2:

I restarted my router, and now everything works... Hehe.. Thanks for the guide, and sorry for not taking the time to restart my router before posting. Have a nice day! Cheers!

---

### Post by IuilAine on 2008-06-09
Hey there. I'm very new to linux and installed (dual boot with vista) Ubuntu by myself last night. Did all the updates and everything. Then got some linux-loving friends to try to help me get my wireless up and running. Gave up and tried again today with your guide and I still get nothing. 

I'm running a hp dv6647nr. The only real difference I noticed in the beginning is that I have 02:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02) instead of what you have. My wireless light is still orange and when I check my network connections, the only thing that shows up is my wired and the manual install thing.


Not really sure what to do since I'm entirely new to this, but I hope you might have some idea.

---

### Post by IuilAine on 2008-06-09
Nevermind. Worked for me after a fresh install. =)

---

### Post by phyz on 2008-06-09
> **vikramsharma said:**
> Thanks a lot buddy your advice really helped me out, now I have wireless working flawlessly on my laptop.

thanks dude...it works like charmed..

however,network-manager & network-manager-gnome still having wep & wpa encryption problem so i'd replaced them with "wicd".

because of we put some additional modprobe command in /etc/rc.local so i have to trigger 'sudo /etc/init.d/wicd start' to let my wireless connection via wicd works.

did anyone how is there any other way to remove ssb before ndiswrapper module loading on the system boot up?

thanks in advance....

---

### Post by Ayuthia on 2008-06-09
> **phyz said:**
> thanks dude...it works like charmed..

however,network-manager & network-manager-gnome still having wep & wpa encryption problem so i'd replaced them with "wicd".

because of we put some additional modprobe command in /etc/rc.local so i have to trigger 'sudo /etc/init.d/wicd start' to let my wireless connection via wicd works.

did anyone how is there any other way to remove ssb before ndiswrapper module loading on the system boot up?

thanks in advance....
You can try this:
```
echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper
```
This will put the loading and unloading at the modprobe command.  This is based on the no-fluff method at [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-6a90c0182f807f29d1a2f55e8654ac07689542bb](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-6a90c0182f807f29d1a2f55e8654ac07689542bb)

---

### Post by Matt Damon on 2008-06-10
> **Ayuthia said:**
> If you compiled NDISwrapper in Gutsy, you will need to get a new version of NDISwrapper (1.50 or higher) and will most likely need to reinstall the bcmwl5 driver.

Hi Ayuthia.  To clarify what I meant, I carried out Jlandaw's instructions at the start of this thread only after the upgrade from Gutsy to Hardy.  Wireless was working with Gutsy, it was only after the upgrade that Wireless stopped working.   The NDISwrapper version I installed as part of Jlandaws instructions was 1.53....

Update: I just noticed i'd kept the b43 driver disabled under admin>hardware drivers. Oops. I think I might have got confused with a message after the upgrade.  After enabling the B43 driver the hardware is back (surprise), I can view local wireless networks, but I can't connnect.  I do not have any security enabled.   Any ideas on some other checks I can do?:

---

### Post by Ayuthia on 2008-06-10
> **Matt Damon said:**
> Hi Ayuthia.  To clarify what I meant, I carried out Jlandaw's instructions at the start of this thread only after the upgrade from Gutsy to Hardy.  Wireless was working with Gutsy, it was only after the upgrade that Wireless stopped working.   The NDISwrapper version I installed as part of Jlandaws instructions was 1.53....

Update: I just noticed i'd kept the b43 driver disabled under admin>hardware drivers. Oops. I think I might have got confused with a message after the upgrade.  After enabling the B43 driver the hardware is back (surprise), I can view local wireless networks, but I can't connnect.  I do not have any security enabled.   Any ideas on some other checks I can do?:You might try the following:
```
sudo modprobe -r b43 ssb
sudo modprobe b43
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid <name>
sudo dhclient wlan0
```

---

### Post by Nike T on 2008-06-10
Help, I've been working on this for like 2 hours today, still can't get it.  I was messing around with this stuff, I did this tut before and I got the wireless to work, but my sister, it's her laptop, would always complain about her wireless cutting out.  So I looked into other tuts, tried what they told me, didn't work, and then tried this one again, and now I can't get anything.  Also when I log out, it shows some script and on that script it tells me that the modules b44 and b43 don't exist in like /proc/mod.  Or something like that.  Are there any codes that I could use so that you guys can know my problem better?

---

### Post by Ayuthia on 2008-06-10
> **Nike T said:**
> Help, I've been working on this for like 2 hours today, still can't get it.  I was messing around with this stuff, I did this tut before and I got the wireless to work, but my sister, it's her laptop, would always complain about her wireless cutting out.  So I looked into other tuts, tried what they told me, didn't work, and then tried this one again, and now I can't get anything.  Also when I log out, it shows some script and on that script it tells me that the modules b44 and b43 don't exist in like /proc/mod.  Or something like that.  Are there any codes that I could use so that you guys can know my problem better?
Just to see if NDISwrapper is installed correctly, check ndiswrapper -v from the terminal.  If it does not show any error messages and the version is greater than 1.50, then this is ok.

Next check ndiswrapper -l from the terminal.  If it shows that the driver is installed and the device is present then it is also fine.

You then can try and see if the wireless is going to work, you can unload all the modules that work for your Broadcom card and then install ndiswrapper:
```
sudo modprobe -r bcm43xx b43legacy b43 b44 ssb ndiswrapper wl
sudo modprobe ndiswrapper
ifconfig
```
If ifconfig does not show your wireless info, then you should check dmesg at the terminal.  The error message should show up at the end of the listing since sudo modprobe ndiswrapper is the most recent command entered.
If there are no errors, check:
```
lshw -C network
```
It will tell you if ndiswrapper is the driver being used.

If it does show your wireless, you can check
```
sudo iwlist scan
```If it shows you wireless information, then you must have missed something in the blacklisting (/etc/modprobe.d/blacklist), loading your modules (/etc/modules), or your wireless fix script.

---

### Post by Ayuthia on 2008-06-10
> **Nike T said:**
> Also when I log out, it shows some script and on that script it tells me that the modules b44 and b43 don't exist in like /proc/mod.Usually when it says that b44 and b43 don't exist in /proc/modules, that means that the modules were not loaded when it tried to remove them.  If you are using ndiswrapper, that is ok to see.  It does sound like the message might be coming from /etc/init.d/rc.local.  Can you post this?  It could be possible that there is something else in the script that it does not like or else it was the one of the last error messages that showed up while booting.

---

### Post by ljungkvist on 2008-06-11
Hi,

as I wrote in an earlier post I got everything to work after following this guide. It is still working, but two things have been annoying me:

- On shutoff the computer makes some shell output concerning "b43", and "wlan" before it shuts off. Can someone help me catch this output in some way?

- On startup the network manager starts up succesfully, finds the network that I connected to last time and tries to connect. The connection always fail after a short moment or so. The first "green blob" actually lights up almost instantly, but it never makes it to the second. However, if I uncheck the "enable wireless" option, wait a moment and the enable it again, it can connect perfectly well. What's up here?

Actually I would like to learn how to connect manually so to say, without having to use the manager. Can I put some instructions (which?) in a script and the make the system run it at startup?

Any help greatly appreciated!

---

### Post by Matt Damon on 2008-06-11
> **Ayuthia said:**
> You might try the following:
```
sudo modprobe -r b43 ssb
sudo modprobe b43
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid <name>
sudo dhclient wlan0
```

Hello again.  progress... maybe.  I'm connecting, but not associating.  Also my wlan0 dosn't show up anymore instead I have picked up an extra eth port - eth1 which 'iwconfig' shows is my wireless port which I don't ever recall seeing before... (what have I done I wonder??? Ooo-er).  I included some further output which I hope might show some clues. Maybe.  Thanks for showing the interest and continuing to help? Ayuthia.  People like you rock my Ubuntu!   

By the way, sorry for making this message so long..  I guess I should be attaching a file instead?

here's the output;

miked@miked-laptop:~$ lspci | grep Broadcom

06:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

miked@miked-laptop:~$ ndiswrapper -v

utils version: '1.9', utils version needed by module: '1.9'

module details:

filename:       /lib/modules/2.6.24-18-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko

version:        1.52

vermagic:       2.6.24-18-generic SMP mod_unload 586 


miked@miked-laptop:~$ ndiswrapper -l

bcmwl5 : driver installed

	device (14E4:4311) present (alternate driver: bcm43xx)


miked@miked-laptop:~$ lshw -C network

WARNING: you should run this program as super-user.

  *-network               

       description: Network controller

       product: BCM94311MCG wlan mini-PCI

       vendor: Broadcom Corporation

       physical id: 0

       bus info: pci@0000:06:00.0

       version: 01

       width: 32 bits

       clock: 33MHz

       capabilities: bus_master cap_list

       configuration: driver=b43-pci-bridge latency=0 module=ssb

  *-network

       description: Ethernet interface

       product: RTL-8139/8139C/8139C+

       vendor: Realtek Semiconductor Co., Ltd.

       physical id: 8

       bus info: pci@0000:08:08.0

       logical name: eth0

       version: 10

       serial: 00:16:d4:e6:f8:ed

       width: 32 bits

       clock: 33MHz

       capabilities: bus_master cap_list ethernet physical

       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes

  *-network

       description: Wireless interface

       physical id: 1

       logical name: eth1

       serial: 00:1a:73:43:fa:fd

       capabilities: ethernet physical wireless

       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


miked@miked-laptop:~$ sudo iwlist scan

lo        Interface doesn't support scanning.



eth0      Interface doesn't support scanning.



wmaster0  Interface doesn't support scanning.



eth1      No scan results



miked@miked-laptop:~$ sudo ifconfig

eth0      Link encap:Ethernet  HWaddr 00:16:d4:e6:f8:ed  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:46162 errors:0 dropped:0 overruns:0 frame:0

          TX packets:40992 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:47429325 (45.2 MB)  TX bytes:6988855 (6.6 MB)

          Interrupt:20 Base address:0x2000 



eth1      Link encap:Ethernet  HWaddr 00:1a:73:43:fa:fd  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:1150 errors:0 dropped:0 overruns:0 frame:0

          TX packets:1150 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:57500 (56.1 KB)  TX bytes:57500 (56.1 KB)



wmaster0  Link encap:UNSPEC  HWaddr 00-1A-73-43-FA-FD-00-00-00-00-00-00-00-00-00-00  

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


miked@miked-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by Ayuthia on 2008-06-11
> **ljungkvist said:**
> 
- On shutoff the computer makes some shell output concerning "b43", and "wlan" before it shuts off. Can someone help me catch this output in some way?There are two places that you might be able to find it.  You can view /var/log/messages or /var/log/dmesg.0.  /var/log/messages will contain information for the last few boots and /var/log/dmesg.0 will contain information only for the previous boot.

> - On startup the network manager starts up succesfully, finds the network that I connected to last time and tries to connect. The connection always fail after a short moment or so. The first "green blob" actually lights up almost instantly, but it never makes it to the second. However, if I uncheck the "enable wireless" option, wait a moment and the enable it again, it can connect perfectly well. What's up here?I have encountered this a few times too.  It seems to work fine if you do it manually, but when I do it through Wicd it connects for a few seconds then quits.  I have not tracked down what is causing this.

> Actually I would like to learn how to connect manually so to say, without having to use the manager. Can I put some instructions (which?) in a script and the make the system run it at startup?I would take a look at this sticky by kevdog:
[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)
He shows you how to do things manually and at the end, there is some information on how to add things to rc.local so that things will start up at boot.

---

### Post by Ayuthia on 2008-06-11
> **Matt Damon said:**
> Hello again.  progress... maybe.  I'm connecting, but not associating.  Also my wlan0 dosn't show up anymore instead I have picked up an extra eth port - eth1 which 'iwconfig' shows is my wireless port which I don't ever recall seeing before... (what have I done I wonder??? Ooo-er).This is ok.  For some reason it changed the name over but it will work fine.  If you don't like it, you can change it by editing /etc/udev/rules.d/70-persistent-net.rules.

> miked@miked-laptop:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-18-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-18-generic SMP mod_unload 586 

miked@miked-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: bcm43xx)

miked@miked-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@0000:08:08.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:e6:f8:ed
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:1a:73:43:fa:fd
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

You might check and be sure that ndiswrapper and bcm43xx are not loaded also:
```
cat /etc/modprobe.d/blacklist*|grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper
```
We might even see if you can connect without Network Manager running.  This command will only stop Network Manager from running for this session:
```
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo /etc/dbus-1/event.d/25NetworkManager stop
```
You can then try loading the modules again:
```
sudo modprobe -r b43 ssb bcm43xx ndiswrapper
sudo modprobe b43
sudo ifconfig eth1 up
sudo iwconfig eth1 <name>
sudo dhclient eth1
```

---

### Post by haitechan on 2008-06-12
Reporting a working Compaq v3000 with Hardy here! :p

I had some troubles because I didn't have another way to connect to internet and download the packages, neither do sudo apt-get update :(, so I went to another machine (I was configuring my mom's laptop :)) and downloaded the following packages on my home directory:

[LIST]
[*]build-essential_11.3ubuntu1_i386.deb
[*]dpkg-dev_1.14.16.6ubuntu3_all.deb
[*]g++-4.2_4.2.3-2ubuntu7_i386.deb
[*]g++_4.2.3-1ubuntu3_i386.deb
[*]libc6-dev_2.7-10ubuntu3_i386.deb
[*]libstdc++6-4.2-dev_4.2.3-2ubuntu7_i386.deb
[*]libtimedate-perl_1.1600-9_all.deb
[*]linux-headers-2.6.24-16-generic_2.6.24-16.30_i386.deb
[*]linux-libc-dev_2.6.24-18.32_i386.deb
[*]patch_2.5.9-4_i386.deb
[/LIST]

And then did sudo dpkg -i *.deb on a terminal :)

Just thought it might be useful for someone! :)
Thanks a lot for this great tutorial, btw! :D

---

### Post by ljungkvist on 2008-06-13
> **Ayuthia said:**
> There are two places that you might be able to find it.  You can view /var/log/messages or /var/log/dmesg.0.  /var/log/messages will contain information for the last few boots and /var/log/dmesg.0 will contain information only for the previous boot.
ok, checked both of them out. They both contained alot of information from the last boot ups but nothing from the shutoff. Is there a posibility to pause the process, so I can write it off manualy?

> 
I have encountered this a few times too.  It seems to work fine if you do it manually, but when I do it through Wicd it connects for a few seconds then quits.  I have not tracked down what is causing this.

what i've concluded is that it's not sufficient to just reconnect. I really have to shut the wireless on/off.

> I would take a look at this sticky by kevdog:
[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)
He shows you how to do things manually and at the end, there is some information on how to add things to rc.local so that things will start up at boot.

I tried this, but at this line:

```
sudo wpa_supplicant -w -D<****see footer below***> -i<interface> -c/etc/wpa_supplicant.conf -dd 

```

it just won't succeed. it just tries and tries... guess i have to post something there.

---

### Post by Ayuthia on 2008-06-13
> **ljungkvist said:**
> ok, checked both of them out. They both contained alot of information from the last boot ups but nothing from the shutoff. Is there a posibility to pause the process, so I can write it off manualy?I don't think that there is a way to pause it.  You might just dig through /var/log and see if there are any other logs that mihgt have what you are looking for:
```
cd /var/log
sudo grep -r b43 *
```
This will go into /var/log and look through all the files and folders to look for anything that contains b43.

---

### Post by ileftrunning on 2008-06-14
God bless you for your post.  I  was about to set fire to this %$#!@$ machine!  Again many thanks.

Sam aka ileftrunning

---

### Post by Chxta on 2008-06-14
This is a very useful thread. I'm cruising on my wifi now...

---

### Post by Momof9Blessings on 2008-06-15
the download file does not seem to be valid anymore....

---

### Post by Ayuthia on 2008-06-15
> **Momof9Blessings said:**
> the download file does not seem to be valid anymore....

I just tested the links and I they seem to be fine now.

---

### Post by SlingerXL on 2008-06-16
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

That's my lspci. I've done everything in this tutorial 2 or 3 times now and I have wicd and it still won't find any wireless networks. HP Pavilion tx 1000.

---

### Post by SlingerXL on 2008-06-16
2x post

---

### Post by Ayuthia on 2008-06-16
> **SlingerXL said:**
> 03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

That's my lspci. I've done everything in this tutorial 2 or 3 times now and I have wicd and it still won't find any wireless networks. HP Pavilion tx 1000.

Please post the results of the following:
```
lshw -C network
ndiswrapper -v
ndiswrapper -l
lsmod |grep -i -e b43 -e ssb -e ndiswrapper -e bcm43xx
```

---

### Post by j0sh818 on 2008-06-16
> **Ayuthia said:**
> You are one of the people that needs to have ssb so that your wired ethernet card will work.  If you look at your other card, you will see the b44 driver.  That driver needs ssb.

Just for now, I would try to remove ssb just to see if you can just get your wireless back up:
```
sudo modprobe -r b43 b44 ssb ndiswrapper
sudo modprobe ndiswrapper
```
If it doesn't work, you can enable your wired connection again by:
```
sudo modprobe b44
```.  If it does, try connecting your wired again.



thanks a lot for this guide! amazing! I'm currently using an HP dv2415nr notebook with the 64-bit (AMD64) version of Ubuntu 8.04 - Hardy Heron. at first it didnt work but after i followed the additional instruction above, my WLAN is now working flawlessly.

thanks again!
:KS

---

### Post by SlingerXL on 2008-06-16
> **Ayuthia said:**
> Please post the results of the following:
```
lshw -C network
ndiswrapper -v
ndiswrapper -l
lsmod |grep -i -e b43 -e ssb -e ndiswrapper -e bcm43xx
```

**lshw -C network**:

WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:1a:73:a6:9d:b4
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

**ndiswrapper -v**:

utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-18-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-18-generic SMP mod_unload 586 

**ndiswrapper -l**:

bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: bcm43xx)

**lsmod |grep -i -e b43 -e ssb -e ndiswrapper -e bcm43xx**:

bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: bcm43xx)
dan@dan-hp:~$ lsmod |grep -i -e b43 -e ssb -e ndiswrapper -e bcm43xx
ssb                    32260  1 b44
ndiswrapper           192920  0 
usbcore               146028  10 ndiswrapper,usbtouchscreen,usb_storage,usbhid,uvcvideo,libusual,hci_usb,ehci_hcd,ohci_hcd

---

### Post by Ayuthia on 2008-06-16
> **SlingerXL said:**
> **lshw -C network**:

WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:1a:73:a6:9d:b4
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
The disable portion leads me to believe that your wireless card is not flipped on.  Can you try the following:
```
sudo modprobe -r b43 ssb ndiswrapper bcm43xx
sudo depmod -ae
sudo modprobe ndiswrapper
sudo ifconfig wlan0 up
sudo iwlist scan
```
If you don't see any wireless access points, can you post the results of lshw -C network again along with the following:
```
dmesg|grep ndiswrapper
```

EDIT:
Please note that I changed iwconfig to ifconfig if you read this before my edit.  That was a mistake.

---

### Post by SlingerXL on 2008-06-16
After doing the first line of code I get this:

FATAL: Module ssb is in use.

What's that mean?

---

### Post by Ayuthia on 2008-06-16
> **SlingerXL said:**
> After doing the first line of code I get this:

FATAL: Module ssb is in use.

What's that mean?
It means that there is another module that is using ssb.  Most likely it is b44.  You can try the following:
```
sudo modprobe -r b43 b44 ssb ndiswrapper bcm43xx
sudo depmod -ae
sudo modprobe ndiswrapper
sudo modprobe b44
sudo ifconfig wlan0 up
sudo iwlist scan
```
Can you also post your entire results of lshw -C network?  I just want to verify that you really need the b44 module.

EDIT: Please note that the b44 module is removed in the first line and then reloaded after b44.  I forgot to remove the b44 module in the original version.

---

### Post by SlingerXL on 2008-06-16
Here's my full lshw:

dan@dan-hp:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:1a:73:a6:9d:b4
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

I put in all the code you said to and I'm about to reboot. After the last line heres what it said:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:17:3F:6A:DD:99
                    ESSID:"houseoflove"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:42/100  Signal level:-69 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:50:18:45:2A:72
                    ESSID:"BJ PALACE"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:18/100  Signal level:-84 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:1B:63:2D:20:A9
                    ESSID:"girlfess"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:73/100  Signal level:-49 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: 00:1C:10:14:AB:84
                    ESSID:"Citgo-3"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:12/100  Signal level:-88 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

---

### Post by Ayuthia on 2008-06-16
> **SlingerXL said:**
> Here's my full lshw:

dan@dan-hp:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:1a:73:a6:9d:b4
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

I put in all the code you said to and I'm about to reboot. After the last line heres what it said:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:17:3F:6A:DD:99
                    ESSID:"houseoflove"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:42/100  Signal level:-69 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:50:18:45:2A:72
                    ESSID:"BJ PALACE"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:18/100  Signal level:-84 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:1B:63:2D:20:A9
                    ESSID:"girlfess"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:73/100  Signal level:-49 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: 00:1C:10:14:AB:84
                    ESSID:"Citgo-3"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:12/100  Signal level:-88 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

It looks like you are able to see the wireless sites now.  Are you able to connect?

---

### Post by sebastianjanikowsky on 2008-06-16
Hi Ayuthia, I've been reading your instructions specially in SlingerXL's case, I have the same problem but in my case I'm having this results

vinny@vinny-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:1a:73:62:7e:a8
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

vinny@vinny-laptop:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-19-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-19-generic SMP mod_unload 586 

vinny@vinny-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: bcm43xx)

vinny@vinny-laptop:~$ lsmod |grep -i -e b43 -e ssb -e ndiswrapper -e bcm43xx
ssb                    34308  1 b44
ndiswrapper           192920  0 
usbcore               146028  6 ndiswrapper,uvcvideo,usbhid,ehci_hcd,ohci_hcd


And no red light, no wireless connection. HP dv6000 AMD Turion 64
Any suggestion?
thanks

---

### Post by Ayuthia on 2008-06-16
> **sebastianjanikowsky said:**
> Hi Ayuthia, I've been reading your instructions specially in SlingerXL's case, I have the same problem but in my case I'm having this result when I try to scan with sudo iwlist scan


lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

any help?

thanks

Let's take a step back and see if everything is configured correctly.  Please post the results of:
```
lshw -C network
ndiswrapper -v
ndiswrapper -l
lsmod |grep -i -e b43 -e ssb -e ndiswrapper -e bcm43xx
```

---

### Post by sebastianjanikowsky on 2008-06-17
Thanks for your answer, this is the result

vinny@vinny-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:1a:73:62:7e:a8
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
vinny@vinny-laptop:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-19-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-19-generic SMP mod_unload 586 
vinny@vinny-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: bcm43xx)
vinny@vinny-laptop:~$ lsmod |grep -i -e b43 -e ssb -e ndiswrapper -e bcm43xx
ndiswrapper           192920  0 
ssb                    34308  1 b44
usbcore               146028  6 usbhid,ndiswrapper,uvcvideo,ehci_hcd,ohci_hcd

---

### Post by SlingerXL on 2008-06-17
> **Ayuthia said:**
> It looks like you are able to see the wireless sites now.  Are you able to connect?

Sadly, no. No wireless networks show up still. Just so you can eliminate the possibility my wireless switch is on. By the way, I really appreciate all the help you've given me and other community members.

---

### Post by Ayuthia on 2008-06-17
> **SlingerXL said:**
> Sadly, no. No wireless networks show up still. Just so you can eliminate the possibility my wireless switch is on. By the way, I really appreciate all the help you've given me and other community members.Well, it looks like a configuration issue.  Can you post the results of:
```
cat /etc/modprobe.d/blacklist*|grep -i -e bcm43xx -e b43 -e b44 -e ssb -e ndiswrapper
cat /etc/modules|grep -i -e bcm43xx -e b43 -e b44 -e ssb -e ndiswrapper
```

If you can turn off your encryption, can you try the following:
```
sudo modprobe -r b43 b44 ssb ndiswrapper bcm43xx
sudo depmod -ae
sudo modprobe ndiswrapper
sudo modprobe b44
sudo ifconfig wlan0 up
sudo iwlist scan
sudo dhclient -r wlan0
sudo iwconfig wlan0 essid girlfess
sudo dhclient wlan0
```
I am just using "girlfess" mainly because it is the closest access point in your scan so I am assuming that it was yours.  Just replace girlfess with the name of your access point.

---

### Post by sebastianjanikowsky on 2008-06-17
Hi
This is my result

vinny@vinny-laptop:~$ cat /etc/modprobe.d/blacklist*|grep -i -e bcm43xx -e b43 -e b44 -e ssb -e ndiswrapper
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist b43
sudo apt-get install ndiswrapper-utils-1.9
mkdir ~/bcm43xx; cd ~/bcm43xx
blacklist bcm43xx
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist b43
sudo apt-get install ndiswrapper-utils-1.9
mkdir ~/bcm43xx; cd ~/bcm43xx
vinny@vinny-laptop:~$ cat /etc/modules|grep -i -e bcm43xx -e b43 -e b44 -e ssb -e ndiswrapper
ndiswrapper
ndiswrapper
vinny@vinny-laptop:~$

---

### Post by Ayuthia on 2008-06-17
> **sebastianjanikowsky said:**
> Thanks for your answer, this is the result

vinny@vinny-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:1a:73:62:7e:a8
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
vinny@vinny-laptop:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-19-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-19-generic SMP mod_unload 586 
vinny@vinny-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: bcm43xx)
vinny@vinny-laptop:~$ lsmod |grep -i -e b43 -e ssb -e ndiswrapper -e bcm43xx
ndiswrapper           192920  0 
ssb                    34308  1 b44
usbcore               146028  6 usbhid,ndiswrapper,uvcvideo,ehci_hcd,ohci_hcd
Your results look fine there.  Can you post the results of the following:
```
sudo modprobe -r b43 b44 ssb ndiswrapper bcm43xx
sudo depmod -ae
sudo modprobe ndiswrapper
sudo iwlist scan
ifconfig
iwconfig
```

---

### Post by Ayuthia on 2008-06-17
> **sebastianjanikowsky said:**
> Hi
This is my result

vinny@vinny-laptop:~$ cat /etc/modprobe.d/blacklist*|grep -i -e bcm43xx -e b43 -e b44 -e ssb -e ndiswrapper
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist b43
sudo apt-get install ndiswrapper-utils-1.9
mkdir ~/bcm43xx; cd ~/bcm43xx
blacklist bcm43xx
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist b43
sudo apt-get install ndiswrapper-utils-1.9
mkdir ~/bcm43xx; cd ~/bcm43xx
vinny@vinny-laptop:~$ cat /etc/modules|grep -i -e bcm43xx -e b43 -e b44 -e ssb -e ndiswrapper
ndiswrapper
ndiswrapper
vinny@vinny-laptop:~$
You are going to want to clean up these two files.  For the first file, you will need to edit it in admin mode:
```
gksu gedit /etc/modprobe.d/blacklist
```
You will need to remove the following lines:
```
sudo apt-get install ndiswrapper-utils-1.9
mkdir ~/bcm43xx; cd ~/bcm43xx
```and remove any duplicates.

You will also want to edit /etc/modules:
```
gksu gedit /etc/modules
```
and remove one of the ndiswrapper lines.

You will receive error messages when you load or unload modules (sudo modprobe/modprobe -r).  Other than that, it generally do not cause any harm.

---

### Post by sebastianjanikowsky on 2008-06-17
i didn't receive any error message, thats ok?

---

### Post by Ayuthia on 2008-06-17
> **sebastianjanikowsky said:**
> i didn't receive any error message, thats ok?
That is ok if you don't.

---

### Post by sebastianjanikowsky on 2008-06-17
sorry about this, noobie here!!! what's next?

---

### Post by SlingerXL on 2008-06-17
> **Ayuthia said:**
> Well, it looks like a configuration issue.  Can you post the results of:
```
cat /etc/modprobe.d/blacklist*|grep -i -e bcm43xx -e b43 -e b44 -e ssb -e ndiswrapper
cat /etc/modules|grep -i -e bcm43xx -e b43 -e b44 -e ssb -e ndiswrapper
```

If you can turn off your encryption, can you try the following:
```
sudo modprobe -r b43 b44 ssb ndiswrapper bcm43xx
sudo depmod -ae
sudo modprobe ndiswrapper
sudo modprobe b44
sudo ifconfig wlan0 up
sudo iwlist scan
sudo dhclient -r wlan0
sudo iwconfig wlan0 essid girlfess
sudo dhclient wlan0
```
I am just using "girlfess" mainly because it is the closest access point in your scan so I am assuming that it was yours.  Just replace girlfess with the name of your access point.
dan@dan-hp:~$ cat /etc/modprobe.d/blacklist*|grep -i -e bcm43xx -e b43 -e b44 -e ssb -e ndiswrapper
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist b43
blacklist bcm43xx
blacklist b43
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist b43
blacklist bcm43xx
dan@dan-hp:~$ 

The second line of code just brings up "ndiswrapper"

I don't know how to turn off the encryption since I didn't set up the wireless (I'm subleasing the place for the summer since I'm staying at Indiana University), but this is what the terminal said after I put in all the code:

dan@dan-hp:~$ sudo dhclient -r wlan0
There is already a pid file /var/run/dhclient.pid with pid 4349
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:1a:73:a6:9d:b4
Sending on   LPF/wlan0/00:1a:73:a6:9d:b4
Sending on   Socket/fallback
dan@dan-hp:~$ sudo iwconfig wlan0 essid girlfess
dan@dan-hp:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:1a:73:a6:9d:b4
Sending on   LPF/wlan0/00:1a:73:a6:9d:b4
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


EDIT: Yes, girlfess is the network name. I moved in to a house with 3 girls and we live on Fess Avenue haha.

---

### Post by rated_emman on 2008-06-17
IT WORKED LIKE MAGIC IN MY HARDY :D:D

thank YOU SO MUCH!!!! yOu GUys!! rocks sooo MUCH! thanks again!

---

### Post by Ayuthia on 2008-06-17
> **SlingerXL said:**
> 
EDIT: Yes, girlfess is the network name. I moved in to a house with 3 girls and we live on Fess Avenue haha.
If you are able to see wireless access points by:
```
sudo iwlist scan
```
after loading the modules:
```
sudo modprobe -r b43 b44 ssb ndiswrapper bcm43xx
sudo depmod -ae
sudo modprobe ndiswrapper
```
Then your wireless is working.  You will then need to try to connect.  Since this is WPA, I don't have much experience in it yet.  I would join you in this adventure, but my wireless card broke this morning.  What I can recommend is to try the following link for configuring manually:
[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)
There is a section for setting up WPA.  You should be able to use WPA supplicant.

Another good link to set up WPA is the following:
[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)
I have used this before to test out WPA a while back.  It works well also.

---

### Post by Ayuthia on 2008-06-17
> **sebastianjanikowsky said:**
> sorry about this, noobie here!!! what's next?That was my fault.  I was waiting for your results from my previous post (#128).  Can you show me the results to the following:
```
sudo modprobe -r b43 b44 ssb ndiswrapper bcm43xx
sudo depmod -ae
sudo modprobe ndiswrapper
sudo iwlist scan
ifconfig
iwconfig
```
The first three steps removes all the possible Broadcom modules, rebuilds the module dependencies, and then loads ndiswrapper.  The next step will look for wireless sites.  The fifth command will check your network configuration and the last one is your wireless configuration.

---

### Post by simohell on 2008-06-17
A bit of good news for Hardy, I think...

My WLAN was not working on install today. So I started looking for help. But now it is working with the drivers suggested by Hardy itself, after first installing all the latest updates. It might be, that things will work now for many others as well.

I'm using (since today) HP 6510b, Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

---

### Post by lcherryholmes on 2008-06-18
If there is a kernel update, does the ndiswrapper need to be recompiled to work with the new version?

I just got a new update the other day and started having issues again.  This is frustrating!

Thanks 4 ALL the help!!:KS

---

### Post by Ayuthia on 2008-06-19
> **lcherryholmes said:**
> If there is a kernel update, does the ndiswrapper need to be recompiled to work with the new version?

I just got a new update the other day and started having issues again.  This is frustrating!

Thanks 4 ALL the help!!:KS
If you are not using ndiswrapper from the repositories, yes.  The self-compiled versions are compiled with linux-headers-`uname-r` which means that it will only work with that kernel version.

---

### Post by lcherryholmes on 2008-06-19
> **Ayuthia said:**
> If you are not using ndiswrapper from the repositories, yes.  The self-compiled versions are compiled with linux-headers-`uname-r` which means that it will only work with that kernel version.

So let me get this straight whenever they update the Kernel they will update the ndiswrapper to work with it?  

If that's the case I wonder why mine quit working.

Any ideas?

---

### Post by Ayuthia on 2008-06-19
> **lcherryholmes said:**
> So let me get this straight whenever they update the Kernel they will update the ndiswrapper to work with it?  

If that's the case I wonder why mine quit working.

Any ideas?
No, if you compiled ndiswrapper on your own instead of using the ones from the repositories, you will have to compile ndiswrapper every time a kernel update is done or else it will quit working.

---

### Post by lcherryholmes on 2008-06-19
No what I was asking is if I did get ndiswrapper from the repositories when I update the Kernel the ndiwwrapper will update as well.

Same question - asked differently perhaps this will clear up what I am asking.  :)

---

### Post by Ayuthia on 2008-06-19
> **lcherryholmes said:**
> No what I was asking is if I did get ndiswrapper from the repositories when I update the Kernel the ndiwwrapper will update as well.

Same question - asked differently perhaps this will clear up what I am asking.  :)Sorry about that.  Yes, if you did get it from the repositories then it should update automatically.

---

### Post by lcherryholmes on 2008-06-19
> **Ayuthia said:**
> Sorry about that.  Yes, if you did get it from the repositories then it should update automatically.

So what should I do now after I did update of kernel the wifi is not working again?

At some point should I see if other drivers are created to work with this card or stick with ndiswrapper for a while longer.

I can be patient just hate having to redo after every kernel update.  

Thanks for ALL of the help!!

---

### Post by Ayuthia on 2008-06-19
> **lcherryholmes said:**
> So what should I do now after I did update of kernel the wifi is not working again?

At some point should I see if other drivers are created to work with this card or stick with ndiswrapper for a while longer.

I can be patient just hate having to redo after every kernel update.  

Thanks for ALL of the help!!

Can you post the results of:
```
lshw -C network
uname -r
```It will help see what driver is being used and the second will tell us what kernel version you are running.

---

### Post by lcherryholmes on 2008-06-19
I can't do it now as I am at work but I will tonight.  We don't have wireless at work yet.

Thanks

---

### Post by ljungkvist on 2008-06-20
Hi,

Some weeks ago I went through this guide and got it all up and running. As I wrote in an earlier post, my Network Manager was playing a bit with me and didn't want to connect unless I shut it on/off after system startup. Now It's stoped working completely. I see all the networks, but when I try to connect it just doesn't make it. Not even to the "first green blob". What are some good commands to try to determine what's wrong?

I don't really know what the reason for this sudden fuckup might be. Like someone else was discussing, I've had a couple of kernel upgrades since my installation of this wireless thing. Yesterday I thought I should just go through the guide from the beginning all over, but the fourth command doesn't uninstall anything. Can this be because I didn't install them (ndiswrapper/bcm43xx-fwcutter) through the apt in the first place? How can I get around this?

---

### Post by aviborse on 2008-06-20
Somehow it is not working out for me .........i tried thrice the same procedure. Doesnt seem to work. Here's what i get

_**Laptop**_
Compaq Presario 6608AU
AMD Turion
1GB ram
160 GB hard disk.

**_avi@avi-laptop:~$ lshw -C network_**
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:24:86:db:c0
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.5 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network DISABLED
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan1
       version: 02
       serial: 00:1a:73:92:4a:15
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g



**_avi@avi-laptop:~$ lshw -C network_**
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:24:86:db:c0
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.5 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network DISABLED
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan1
       version: 02
       serial: 00:1a:73:92:4a:15
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

**_avi@avi-laptop:~$ lspci | grep Broadcom_**
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

Please guide me!!!!!!!!
Thanks in advance.

---

### Post by durundal on 2008-06-20
Please, can someone tell me why my card worked "out of the box" on a xubuntu 8.04 install but suddenly on updating the kernal the wifi light turned red and it won't turn on again?

I even tried reinstalling ubuntu but still the light only turns blue on random occasions, and if it doesn't turn blue, ubuntu doesn't detect it as hardware.

---

### Post by Ayuthia on 2008-06-20
> **ljungkvist said:**
> Hi,

Some weeks ago I went through this guide and got it all up and running. As I wrote in an earlier post, my Network Manager was playing a bit with me and didn't want to connect unless I shut it on/off after system startup. Now It's stoped working completely. I see all the networks, but when I try to connect it just doesn't make it. Not even to the "first green blob". What are some good commands to try to determine what's wrong?

I don't really know what the reason for this sudden [explicit lyrics edited] might be. Like someone else was discussing, I've had a couple of kernel upgrades since my installation of this wireless thing. Yesterday I thought I should just go through the guide from the beginning all over, but the fourth command doesn't uninstall anything. Can this be because I didn't install them (ndiswrapper/bcm43xx-fwcutter) through the apt in the first place? How can I get around this?

Since there was a recent kernel upgrade and you did not install ndiswrapper from the repositories, you will have to recompile ndiswrapper.  Step 4 is not needed because you did that the first time around.  All you really need to do is theselines in step 9:
```
cd ~/bcm43xx/ndiswrapper
cd ndiswrapper*
make distclean
make
sudo make install
```Then verify that all is ok:
```
ndiswrapper -v
ndiswrapper -l
lshw -C network
```
the first command should show the current version without any error messages.  The second one will show that the driver is installed and device is present.  Both must be there or else it will not work.  An alternate driver showing is ok.  The third command will show that the ndiswrapper driver is installed.

If you still have issues, please come back and post the results of ndiswrapper -v, ndiswrapper -l, and lshw -C network.

---

### Post by Ayuthia on 2008-06-20
> **durundal said:**
> Please, can someone tell me why my card worked "out of the box" on a xubuntu 8.04 install but suddenly on updating the kernal the wifi light turned red and it won't turn on again?

I even tried reinstalling ubuntu but still the light only turns blue on random occasions, and if it doesn't turn blue, ubuntu doesn't detect it as hardware.

You will most likely want to post this in another thread because almost all Broadcom cards will not work out of the box.  The only one that might work now is the 4310 card (14e4:4315) because it was given a special driver.  However, that driver did not come out until the 2.6.24-18 Ubuntu kernel.

Please open a new thread and post your lspci -nn and which kernel you are using (uname -r).  Both of those commands are run in the Terminal.

---

### Post by Ayuthia on 2008-06-20
> **aviborse said:**
> 

**_avi@avi-laptop:~$ lshw -C network_**
multicast=yes
  *-network DISABLED
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan1
       version: 02
       serial: 00:1a:73:92:4a:15
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
The DISABLED label says that either the card is not on for some reason.  Can you post the results of:
```
lsmod|grep -i -e ndiswrapper -e b43 -e bcm43xx -e ssb -e b44
```

To see if it might work, please remove the cable from your wired connection, verify that the wireless card is on (if it has a switch), and try:
```
sudo modprobe -r b43 b44 ssb bcm43xx wl ndiswrapper
sudo depmod -ae
sudo modprobe ndiswrapper
lshw -C network
```See if the card is still listed as DISABLED.  If so, please do this:
```
dmesg|grep ndiswrapper > ~/Desktop/dmesgforum.txt
```Go to your desktop and attach dmesgforum.txt (along with any messages that came with the commands in this post) to your next post.

---

### Post by Vel-Tyno on 2008-06-20
Everything was going great until I hit Step 9.  It could not find build essential.

I am using an HP 530


Joe

---

### Post by Ayuthia on 2008-06-20
> **Vel-Tyno said:**
> Everything was going great until I hit Step 9.  It could not find build essential.

I am using an HP 530


Joe
If you have the Hardy liveCD, open the Terminal and do the following:
```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential
```
The first command will ask you for the CD.  Insert your Hardy liveCD.

Hope that helps.

---

### Post by lcherryholmes on 2008-06-20
Ayuthia -
Here are the output of the commands you asked for.

I also see something called wlan0:avahi not sure what this is but it seems to get an IP address from somewhere unless it is fake.

Thanks,
lcherryholmes

laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:24:da:79:21
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:1a:73:d0:8d:8a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g


laptop:~$ uname -r
2.6.24-19-generic

laptop:~$ lsmod |grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper
ssb                    34308  1 b44
ndiswrapper           192920  0 
usbcore               146028  8 ndiswrapper,uvcvideo,usb_storage,libusual,usbhid,ehci_hcd,ohci_hcd

---

### Post by durundal on 2008-06-20
> **Ayuthia said:**
> You will most likely want to post this in another thread because almost all Broadcom cards will not work out of the box.  The only one that might work now is the 4310 card (14e4:4315) because it was given a special driver.  However, that driver did not come out until the 2.6.24-18 Ubuntu kernel.

Please open a new thread and post your lspci -nn and which kernel you are using (uname -r).  Both of those commands are run in the Terminal.

Oh yes, you're right.  I had to go through the restricted driver manager to set it up.

---

### Post by jrodri14 on 2008-06-20
Hi, i tried your setup, but for some reason, dmesg indicates that windows was unable load the bcm9433. It gives some error C0000001.


I dont know what it could be.

---

### Post by Matt Damon on 2008-06-20
> **Ayuthia said:**
> This is ok.  For some reason it changed the name over but it will work fine.  If you don't like it, you can change it by editing /etc/udev/rules.d/70-persistent-net.rules.


You might check and be sure that ndiswrapper and bcm43xx are not loaded also:
```
cat /etc/modprobe.d/blacklist*|grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper
```
We might even see if you can connect without Network Manager running.  This command will only stop Network Manager from running for this session:
```
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo /etc/dbus-1/event.d/25NetworkManager stop
```
You can then try loading the modules again:
```
sudo modprobe -r b43 ssb bcm43xx ndiswrapper
sudo modprobe b43
sudo ifconfig eth1 up
sudo iwconfig eth1 <name>
sudo dhclient eth1
```

Hi There Ayuthia,

So I tried the above, and it failed to associate again.  I read through later posts and reloaded the drivers, a command I hadn't seen or done before (sudo depmod -ae) and IT WORKS!  Yee haaa.  

Could you check the output below anyway?  It looks to my newbie eyes that I am blacklisting drivers I use, but clearly can't be wrong if wireless is working...right?... all output is listed below...  Look ok?

miked@miked-laptop:~$ cat /etc/modprobe.d/blacklist*|grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist b43
# replaced by b43 and ssb.
blacklist bcm43xx
miked@miked-laptop:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-18-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-18-generic SMP mod_unload 586 
miked@miked-laptop:~$ sudo modprobe -r b43 ssb bcm43xx ndiswrapper
miked@miked-laptop:~$ sudo modprobe b43
miked@miked-laptop:~$ sudo ifconfig eth1 up
miked@miked-laptop:~$ sudo iwconfig eth1 
eth1      IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

miked@miked-laptop:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth1/00:1a:73:43:fa:fd
Sending on   LPF/eth1/00:1a:73:43:fa:fd
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
miked@miked-laptop:~$ sudo ifconfig eth1 up


Then I did this...

miked@miked-laptop:~$ sudo modprobe -r b43 b44 ssb ndiswrapper bcm43xx
miked@miked-laptop:~$ sudo depmod -ae
miked@miked-laptop:~$ sudo modprobe ndiswrapper
miked@miked-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:17:3F:81:63:1C
                    ESSID:"CUO"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.472 GHz (Channel 13)
                    Quality:65/100  Signal level:-54 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:13:10:3B:B2:82
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:4/100  Signal level:-93 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=50
                    Extra:atim=0

miked@miked-laptop:~$ 

And Bingo!.. Ayuthia You Are A RockStar!

---

### Post by Ayuthia on 2008-06-20
> **Matt Damon said:**
> 
Could you check the output below anyway?  It looks to my newbie eyes that I am blacklisting drivers I use, but clearly can't be wrong if wireless is working...right?... all output is listed below...  Look ok?

miked@miked-laptop:~$ cat /etc/modprobe.d/blacklist*|grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist b43
# replaced by b43 and ssb.
blacklist bcm43xxThe file has some duplicates, but it looks ok since you are using ndiswrapper.
> miked@miked-laptop:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-18-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-18-generic SMP mod_unload 586 You are using a version greater than or equal to 1.50 so that is fine for Hardy.
> miked@miked-laptop:~$ sudo modprobe -r b43 ssb bcm43xx ndiswrapper
miked@miked-laptop:~$ sudo modprobe b43
miked@miked-laptop:~$ sudo ifconfig eth1 up
miked@miked-laptop:~$ sudo iwconfig eth1 
eth1      IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

miked@miked-laptop:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth1/00:1a:73:43:fa:fd
Sending on   LPF/eth1/00:1a:73:43:fa:fd
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
miked@miked-laptop:~$ sudo ifconfig eth1 upThis is you testing the b43 drivers and it looks like it did not receive an IP address from dhclient.
> Then I did this...

miked@miked-laptop:~$ sudo modprobe -r b43 b44 ssb ndiswrapper bcm43xx
miked@miked-laptop:~$ sudo depmod -ae
miked@miked-laptop:~$ sudo modprobe ndiswrapper
miked@miked-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:17:3F:81:63:1C
                    ESSID:"CUO"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.472 GHz (Channel 13)
                    Quality:65/100  Signal level:-54 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:13:10:3B:B2:82
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:4/100  Signal level:-93 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=50
                    Extra:atim=0

miked@miked-laptop:~$ 

This portion shows that you are using the ndiswrapper and you are able to wireless signals.  So far, ndiswrapper seems to be the most successful driver for your card. It might be possible that ndiswrapper is not in /etc/modules.  If you are not sure, please post the results of:
```
cat /etc/modules|grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper
```and we can see what is being loaded.

Another option to try is to add the following:
```
echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper;' | sudo tee -a /etc/modprobe.d/ndiswrapper
```This is a modified version of a script from [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-6a90c0182f807f29d1a2f55e8654ac07689542bb](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-6a90c0182f807f29d1a2f55e8654ac07689542bb).  I just took out the b44 addition mainly because you don't seem to need it.

Hope that helps.

> And Bingo!.. Ayuthia You Are A RockStar!Wait until I go on tour!!!  Thanks!  I glad that things are working and hopefully this post will help finalize it for you.

---

### Post by Matt Damon on 2008-06-20
Here you go...

miked@miked-laptop:~$ cat /etc/modules|grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper
ndiswrapper


But also, I am not quite there yet.   I think the drivers are not reloading automatically after reload.  So when I rebooted even though my wireless indicator was shining brightly there was no wireless option under network connections.  So I ran the following...   

miked@miked-laptop:~$ sudo modprobe -r b43 b44 ssb ndiswrapper bcm43xx
miked@miked-laptop:~$ sudo depmod -ae
miked@miked-laptop:~$ sudo modprobe ndiswrapper

And I am wireless again. 

Do you know the commands to automatically reload the drivers?

---

### Post by Ayuthia on 2008-06-20
> **Matt Damon said:**
> Here you go...

miked@miked-laptop:~$ cat /etc/modules|grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper
ndiswrapper


But also, I am not quite there yet.   I think the drivers are not reloading automatically after reload.  So when I rebooted even though my wireless indicator was shining brightly there was no wireless option under network connections.  So I ran the following...   

miked@miked-laptop:~$ sudo modprobe -r b43 b44 ssb ndiswrapper bcm43xx
miked@miked-laptop:~$ sudo depmod -ae
miked@miked-laptop:~$ sudo modprobe ndiswrapper

And I am wireless again. 

Do you know the commands to automatically reload the drivers?

I did not proofread my comments in an earlier post.  Please try the following and let me know if it works:
```
echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper;' | sudo tee -a /etc/modprobe.d/ndiswrapper
```This command will add the removal and reload commands.  The only part it is missing is the depmod -ae, but that might be ok.

---

### Post by aviborse on 2008-06-21
avi@avi-laptop:~$ sudo modprobe -r b43 b44 ssb bcm43xx wl ndiswrapper
avi@avi-laptop:~$ sudo depmod -ae
avi@avi-laptop:~$ sudo modprobe ndiswrapper
avi@avi-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:24:86:db:c0
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan1
       version: 02
       serial: 00:1a:73:92:4a:15
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
avi@avi-laptop:~$ dmesg|grep ndiswrapper > ~/Desktop/dmesgforum.txt

---------Here's is wat i get . still no wireless.....i have attached tht file

---

### Post by aviborse on 2008-06-21
wow !!!!!!!! its working now, i m replying wireless ly..thx a millon Ayuthia

---

### Post by swoody on 2008-06-21
Thank you very much for this write up! I don't know why, but I had my wireless card working out of the box, and then I had to reinstall Ubuntu on my comp (same install disc as first time) and my wireless wouldn't work?? But thanks to you, I know can have a cigg and surf the web at the same time, haha.

---

### Post by lazyfirecloud on 2008-06-22
Thanks!  I finally got it working on my TX1499.  It did take a few hours though =(

For those who are still struggling, here are the commands I took from this thread which helped me debug:


Check that you are using the correct driver
```
$lshw -C network
```
and look for:
```
driver=ndiswrapper+bcmwl5
``` 



If you have b43-pci-bridge instead (or just to make sure everything is running properly):
```
$sudo modprobe -r b43 b44 ssb ndiswrapper
$sudo modprobe ndiswrapper
```



If this fixes the driver, check that you did the bug fix in step 
```
$sudo gedit /etc/init.d/rc.local
```
Make sure you have the following lines:
```
rmmod b43
rmmod b44
rmmod ssb
rmmod ndiswrapper
modprobe ndiswrapper
modprobe ssb
modprobe b44
```
Also, double-check step 5.



Make sure you have the correct network in /etc/modprobe.d/ndiswrapper
```
$sudo ifconfig -a
```
to get the name of the wireless network (mine was wlan1)
```
$sudo gedit /etc/modprobe.d/ndiswrapper
```
to edit the file.



To turn the card on/check for networks:
```
$sudo ifconfig wlan0 up
$sudo iwlist scan
```
If you don't get any networks, press/slide the switch on the laptop for your wireless card and run those commands again.  The card may not turn on until you do the scan.



If the above returns access points but you don't see any wireless in the network manager in the taskbar, right-click on the network manager icon and make sure that the 'Enable wireless' option is checked =)

---

### Post by Matt Damon on 2008-06-22
> **Ayuthia said:**
> I did not proofread my comments in an earlier post.  Please try the following and let me know if it works:
```
echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper;' | sudo tee -a /etc/modprobe.d/ndiswrapper
```This command will add the removal and reload commands.  The only part it is missing is the depmod -ae, but that might be ok.

Hi there.  I did the commands, and like, it works.  I will queue all night when you do your world tour.

T H A N K S for your time.

---

### Post by Matt Damon on 2008-06-22
Hey lazyfirecloud

Nice work.  I was going to do the same.  You did better than I would have anyway:-)

---

### Post by mags73 on 2008-06-22
This thread is still serving the community quite well.  After many threads, this one was the last one that actually worked.

My BCM94311MCG wlan mini-PCI (rev 01) on Hardy 8.04 is working flawlessly. \\:D/

Maybe you could add Dell Latitiude D630 to your list of supported laptops?

Thank you for your time, it is greatly appreciated.

---

### Post by lola23 on 2008-06-22
I am back to trying to fix this issue after using another machine for a while...

> **Ayuthia said:**
> No, the new Broadcom drivers are now using ssb which is causing a conflict with NDISwrapper.  The new Broadcom drivers are b43 (wireless) and b44 (wired).  

The reason why I asked you to do this was to make sure that there was not a conflict.  Since NDISwrapper still did not start up even though we removed the b44 and ssb drivers, we know that the wired card is not causing any problems.

Yours almost looks like your wireless is turned off.  Do you have a switch to turn it on?  If it is on, what happens when you go to the Terminal and type:
```
sudo ifconfig wlan0 up
sudo iwlist scan
```

My wireless card does not have an on/off switch; the light is on (was off before I installed the driver) and I see the available networks.  However, when I try to set the ESSID or other parameters (password) it doesn't seem to work - it doesn't give me an error message but simply does not connect.

---

### Post by Vel-Tyno on 2008-06-23
> **Ayuthia said:**
> If you have the Hardy liveCD, open the Terminal and do the following:
```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential
```
The first command will ask you for the CD.  Insert your Hardy liveCD.

Hope that helps.

OK, we're still moving forward.

I submitted this command and was told "Permission Denied"

sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build

Joe

---

### Post by Dusk Eagle on 2008-06-24
Thanks for this tutorial my wireless network finally works!

---

### Post by parabolee on 2008-06-24
THANK YOU!

I had the strangest problem with mine. One day it was working fine, right out of the box by enabling the hardware in the restricted manager (Inspiron 6400). Then it stopped working, the WiFi light was still on and it found networks but when I tried to connect it would fail and then stop finding available networks.

So I do fresh install after many failed attempts to fix it (figuring I messed it up after trying to get networking with a windows workgroup working).

On a new install it NEVER worked (wifi light is on), never found a network at all!

So I go through your guide twice. Didn't work.

Boot into Vista figuring I'll try a fresh install with your guide only to find it no longer works in Vista! Try to enable from Vista, Wifi will not enable, light never comes on!

Try to enable from Function key shortcut (my computer does not have a switch), and BOOM light comes on and is working again! Great so boot back into Linux and works like a charm.:guitar:

I love Ubuntu Linux but crap like this keeps regular users away, took over 6 hours fixing this!

Hopefully 9 or 10 will bring us close to the usability and ease of use needed for regular people.

THANKS!!!!

---

### Post by cutcrank on 2008-06-26
Hi guys, I have followed jlandaw's instructions to the T and i have the wireless card working in my laptop and i can search and see the networks. But there is a weird problem that i am experiencing.

 [B]
 Hardware:[/B] Compaq Presario V3611AU, AMD64x2, BCM94311MCG (rev o2)

 **OS:** Kubuntu 8.04
 
The problem is that i can see the networks in my office but i cannot connect to it. When i try to connect to a network nothing happens. One SSID has WEP protection and another SSID has 802.1x protection and the third one has no protection, security is disabled. Even to the security disabled network i'm not able to connect to.
 
I use Kwifi manager to search for networks. I have tried configuring the wlan interface manually by providing the SSID and the keys but still it won't connect. What could be the  problem. This has got me perplexed. Can anyone help me with a solution.

Here are the outputs of:

lspci | grep Broadcom
04:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)


ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: bcm43xx)


lshw -C network
  *-network
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:16:d3:af:f6:5f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.3.26 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan1
       version: 02
       serial: 00:1a:73:95:e2:1e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g


wlan1     Scan completed :
          Cell 01 - Address: 00:1A:70:B1:E0:D0
                    ESSID:"iBus-OnBoard WiFi"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:54/100  Signal level:-61 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:0F:66:BF:CD:F0
                    ESSID:"Linuxense_ap01"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:76/100  Signal level:-47 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


Here is a screenshot of the kwifimanager and the scan results.
[ATTACH]75366[/ATTACH]

Hoping somebody would have the solution for this problem. Thanks in advance.

---

### Post by Maputo on 2008-07-05
It worked on mine laptop too!!!  I own a Dell Inspiron 1520.  I think it too can be added to the list of those laptops :).
Thanks!

However, there seems to be a minor issue. Whenever I (re)boot my computer, before being able to use the wireless, I have to:

sudo modprobe -r bcm43xx b43 b44 ssb ndiswrapper
sudo modprobe ndiswrapper
sudo ifconfig eth1 up

if I don't do this it looks like there is no wireless card on my computer at all.  And the wifi led simply seems to be ignorant to switching the wifi on/off (if it's turned off, then it's always turned off, no matter if I switch the wifi on).

Anyone knows what the reason for this might be?  It would be cool if I wouldn't have to do all the "modprobing" every time I boot up my laptop.  

Thanks a lot!

---

### Post by matthewbpt on 2008-07-10
If you update the kernel, would the previous setup still work do you have to repeat this to make the wireless work again? i ask this because one of the steps involves finding your kernel version

---

### Post by aparrales on 2008-07-10
Just to report that it worked on DELL Inspiron 6400, fresh installation form CD.
Thanks you all.

---

### Post by PharCyDeD on 2008-07-10
Another great, easy, and simple install on a HP dv6000. Many many thanks man! I really appreciate it! This topic should be sticky since it covers so many different computers and is a great tutorial for beginners such as myself. 5 Stars!

:KS:KS:KS:KS:KS

---

### Post by jlandaw on 2008-07-10
I'm not sure how it works, but the kernel updates do not affect the wifi once it is done. I believe the updated kernel takes all the settings from the last kernel and applies them to itself, therefore there should be no need to do anything else once you get your wifi up.

I have updated my kernel consistently since 8.04 was released and have not had to re-do anything. None of my tweaks for any part of my system that did not run "out of box" have been overwritten by updates.

Upgrade with confidence

---

### Post by cyberclops on 2008-07-13
thank you, very, very much.  this worked perfectly.

i'm running on a hp6500 on 8.04.

and now my internet works everywhere!!!!

---

### Post by stevejesus on 2008-07-13
I did this a couple of months ago from info that I scratch up from around the web.  It worked fine, but upgrading your kernel kills your wireless.  I assumed that is what would happen.  

How do I get it working again?  I really have to get my wife off of my lappy.  She has a C700 with 32-bit hardy.

---

### Post by pt6071 on 2008-07-13
Wireless works flawlessly on my lappy now w/ Hardy (HP Pavillion dv9000).  Thank you!

---

### Post by Vartan on 2008-07-17
Many many many thanks, i had spent the last 2 day doing this and scrubbing that on my D630 laptop with no luck.

but now my wireless works like a charm

thank you.
-Vartan

---

### Post by drgnrave on 2008-07-17
I am a linux n00b, and I am running Hardy Heron on my Compaq Presario C714NR (dual-boot with Vista Home Premium) . Before coming to this forum, I have tried to set up my wireless with ndiswrapper, but without the bug fixes for Hardy. When I start up my Kubuntu install, and go to Kwifimanager, I am connected to wifi, but when I try to switch to a network, I end up in Ad-Hoc mode. I have my WEP Password and everything, a direct network connection through a cable works fine, and my wifi is active, yet I always end up in Ad-Hoc mode when I try to connect. I will try to redo the fix the way said here, but could there be anything else wrong with what I am doing?

--drgnrave

---

### Post by drgnrave on 2008-07-17
Here is a screen shot of my situation,
Please help me with this.
--drgnrave

---

### Post by drgnrave on 2008-07-17
Ok sorry for the triple post but got it to work. If it doesn't work for you, this might help:


> If the above returns access points but you don't see any wireless in the network manager in the taskbar, right-click on the network manager icon and make sure that the 'Enable wireless' option is checked =)

Thank you so much. Now I can finally sleep

---

### Post by M8M on 2008-07-23
I've gone through these steps four times and again we get that the Broadcom B43 wireless driver is enabled but not in use. It also does not show wireless as an option to connect. Since we live 10 mins away from a wired connection, I'm getting tired of going over there everyday to try to figure this out. I have another laptop that still has Windows on it and the wireless works on it. So can someone help me walk through trying to figure out what's wrong? I'll have no internet connection on the Ubuntu laptop (that's what I'm trying to fix), but I do have it on the Windows one. So I can communicate, but can't download to Ubuntu until tomorrow late afternoon. Can someone help me please?

---

### Post by daafisch on 2008-07-23
Worked for me Xubuntu 8.04 on my Dell 600m excellent!

---

### Post by Ayuthia on 2008-07-23
> **M8M said:**
> I've gone through these steps four times and again we get that the Broadcom B43 wireless driver is enabled but not in use. It also does not show wireless as an option to connect. Since we live 10 mins away from a wired connection, I'm getting tired of going over there everyday to try to figure this out. I have another laptop that still has Windows on it and the wireless works on it. So can someone help me walk through trying to figure out what's wrong? I'll have no internet connection on the Ubuntu laptop (that's what I'm trying to fix), but I do have it on the Windows one. So I can communicate, but can't download to Ubuntu until tomorrow late afternoon. Can someone help me please?
If you are using ndiswrapper, you will not be able to see the b43 wireless driver in use through Hardware Drivers.  This is because there is a native Linux driver that does exist for Broadcom cards.

You should check and see these two things first:
```
ndiswrapper -l
lshw -C network
```
The first command will help you see if the driver is working and that the hardware is present.  The second command checks to see what driver it is using and that the card is ok.  The second command should say that it is using ndiswrapper instead of b43-bridge-pci (or something like that).

You can also check and see if the correct drivers are loaded:
```
lsmod|grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper -e wl
```
This command should only return ndiswrapper and possibly ssb (with b44 attached to it).  If you see anything else (b43 or bcm43xx) then that means that the drivers are not getting blacklisted.  You can also try the following:
```
sudo modprobe -r b43 b44 ssb bcm43xx ndiswrapper wl
sudo depmod -ae
sudo modprobe ndiswrapper
```
If you are able to see wireless connections, then that means that you have some drivers in there that need to be blacklisted.  If you are not able to get connected, do the lsmod command again and see if ndiswrapper shows up in the list.  If it does not, check:
```
dmesg|grep ndiswrapper
```
There is most likely an error message out there for ndiswrapper explaining what is wrong.

Feel free to post back what you have found and we can try to see if we can get things up and running.

---

### Post by M8M on 2008-07-24
You should check and see these two things first:
Code:

ndiswrapper -l
lshw -C network

The first command will help you see if the driver is working and that the hardware is present. The second command checks to see what driver it is using and that the card is ok. The second command should say that it is using ndiswrapper instead of b43-bridge-pci (or something like that).

Thank you, Auythia!

After the first command, this is what came up:
bcmwl5 : driver installed
         device (14E4:4311) present (alternate driver: bcm43xx)
I went back to hardware drivers and disabled the broadcom B43 wireless driver, which we manually enabled after following all the steps, b/c my husband insisted that it needed to be enabled.
After the second command it shows that the driver is b43-bridge-pci and not ndiswrapper. So I think that would be the first(hopefully only) problem, but I don't know how to fix it. Do I just follow the rest of the steps you posted?

---

### Post by M8M on 2008-07-24
ok, so I thought it wouldn't hurt to just keep going and I found out that after this command:
lsmod|grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper -e wl

it says:
grep: ndiswrapper: no such file or directory

so I guess I need to go re-download and install the ndiswrapper file again. But I'm not sure what is not right, since we've downloaded it three times already and we DO HAVE a folder named ndiswrapper-1.53 in the home folder. Any suggestions?

---

### Post by Ayuthia on 2008-07-24
> **M8M said:**
> ok, so I thought it wouldn't hurt to just keep going and I found out that after this command:
lsmod|grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper -e wl

it says:
grep: ndiswrapper: no such file or directory

so I guess I need to go re-download and install the ndiswrapper file again. But I'm not sure what is not right, since we've downloaded it three times already and we DO HAVE a folder named ndiswrapper-1.53 in the home folder. Any suggestions?

Actually, you should not have to reinstall.  What that is telling you is that you missed a -e before ndiswrapper.  The command thinks that you want to search for b43, bcm43xx, and ssb in the ndiswrapper file.

If you received a response from ndiswrapper -l, the application is there.  To verify the version:
```
ndiswrapper -v
```

---

### Post by M8M on 2008-07-24
If you received a response from ndiswrapper -l, the application is there.  To verify the version:
```
ndiswrapper -v
```

when I typed that in this is what I got: (hopefully I'll copy it correctly and not miss any characters)
utils version: '1.9' , utils version needed by module: '1.9"
module details:
filename:                 /lib/modules/2.6.24-19-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:           1.52
vermagic:          2.6.24-19-generic SMP mod_unload

Excited to see you might be online at the same time as I am!

---

### Post by Ayuthia on 2008-07-24
> **M8M said:**
> You should check and see these two things first:
Code:

ndiswrapper -l
lshw -C network

The first command will help you see if the driver is working and that the hardware is present. The second command checks to see what driver it is using and that the card is ok. The second command should say that it is using ndiswrapper instead of b43-bridge-pci (or something like that).

Thank you, Auythia!

After the first command, this is what came up:
bcmwl5 : driver installed
         device (14E4:4311) present (alternate driver: bcm43xx)
I went back to hardware drivers and disabled the broadcom B43 wireless driver, which we manually enabled after following all the steps, b/c my husband insisted that it needed to be enabled.
After the second command it shows that the driver is b43-bridge-pci and not ndiswrapper. So I think that would be the first(hopefully only) problem, but I don't know how to fix it. Do I just follow the rest of the steps you posted?
I would go ahead with this:
```
sudo modprobe -r b43 b44 ssb bcm43xx ndiswrapper wl
sudo depmod -ae
sudo modprobe ndiswrapper
```
The b43-bridge-pci most likely means that there is another driver that is conflicting with ndiswrapper.  The modprobe commands will remove any conflicting drivers and load ndiswrapper.

> I went back to hardware drivers and disabled the broadcom B43 wireless driver, which we manually enabled after following all the steps, b/c my husband insisted that it needed to be enabled.What???  You listened to him?  My wife has always told me that the woman is always right.  :)

---

### Post by M8M on 2008-07-24
Going to do that right now.

---

### Post by M8M on 2008-07-24
[QUOTE=Ayuthia;5450320]I would go ahead with this:
[code]sudo modprobe -r b43 b44 ssb bcm43xx ndiswrapper wl

This command returned:
FATAL: Module bmc43xx not found

---

### Post by tunafishman on 2008-07-24
What an absolute nightmare.

Thankyou for your wonderful guide and your 20 pages of explanations and special case studies. Page 19 had my answer.

HP tx1120us with Broadcom BCM94311MCG wlan mini-PCI posting on the Ubuntu forums via a wireless connection.

My specific complications:
-64 bit drivers
-previously installed b43 firmware in Hardware Drivers that needed to be disabled.

Thanks again.

Edit:
Spoke too soon. On reboot I am having to do the
```
sudo modprobe -r b43 b44 ndiswrapper wl
sudo depmod -ae
sudo modprobe ndiswrapper
```
How do I make it work more betterer?

---

### Post by M8M on 2008-07-24
> **M8M said:**
> [QUOTE=Ayuthia;5450320]I would go ahead with this:
[code]sudo modprobe -r b43 b44 ssb bcm43xx ndiswrapper wl

This command returned:
FATAL: Module bmc43xx not found


I reentered the command without the "bcm43xx" part and then followed through and its much better, but still not enough.

I have a connection, but cannot get on to a webpage or on amsn. Both laptops (Windows and Ubuntu) are side by side and the signal strength is not the best but it's still working pretty good on the Windows one. Both laptops are identical, except for the operating systems, as I just installed Edubuntu on the one I'm trying to get internet on.

---

### Post by Ayuthia on 2008-07-24
> **M8M said:**
> [QUOTE=M8M;5450367]


I reentered the command without the "bcm43xx" part and then followed through and its much better, but still not enough.

I have a connection, but cannot get on to a webpage or on amsn. Both laptops (Windows and Ubuntu) are side by side and the signal strength is not the best but it's still working pretty good on the Windows one. Both laptops are identical, except for the operating systems, as I just installed Edubuntu on the one I'm trying to get internet on.

You might check:
```
ifconfig
```and see if your wireless (should be wlan0 or eth1) is attached to an ip address (something like 219.152.3.6 but the numbers will most likely be different).  If there is one attached, see if you can ping to a website:
```
ping -c1 www.google.com
```If this returns something without a packet loss, then you are connected.  Since you said that you can't get to a website or even use amsn, then most likely you won't get a successful reply.

How strong is your signal?  Can you check:
```
sudo iwlist scan
```If your signal is pretty weak, then it might not be connecting too well.  Unfortunately, I have not really seen the wireless cards work as well in Linux in comparison to Windows.  You might try getting closer to the router (if it is located in your place).

---

### Post by Ayuthia on 2008-07-24
> **tunafishman said:**
> 
Edit:
Spoke too soon. On reboot I am having to do the
```
sudo modprobe -r b43 b44 ndiswrapper wl
sudo depmod -ae
sudo modprobe ndiswrapper
```
How do I make it work more betterer?

Have you tried the red portion in step 4 of the first post?  The command pretty much does those steps when the system starts up unless you have a 4310 card.  You can check this by:
```
lspci -nn|grep 14e4
```If you see 14e4:4310, then you will need to blacklist the wl driver:
```
echo blacklist wl|sudo tee -a /etc/modprobe.d/blacklist
```

---

### Post by M8M on 2008-07-24
> **Ayuthia said:**
> [QUOTE=M8M;5450539]

You might check:
```
ifconfig
```and see if your wireless (should be wlan0 or eth1) is attached to an ip address (something like 219.152.3.6 but the numbers will most likely be different).  If there is one attached, see if you can ping to a website:
```
ping -c1 www.google.com
```If this returns something without a packet loss, then you are connected.  Since you said that you can't get to a website or even use amsn, then most likely you won't get a successful reply.

How strong is your signal?  Can you check:
```
sudo iwlist scan
```If your signal is pretty weak, then it might not be connecting too well.  Unfortunately, I have not really seen the wireless cards work as well in Linux in comparison to Windows.  You might try getting closer to the router (if it is located in your place).

I rebooted and seemed to have lost everything, no blue light on the wireless switch, no wireless option on the network manager, etc.

After the "ifconfig" command I got:
eth0  Link encap:Ethernet  HWaddr 00:16:36:e0:01:be
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:20 Base address:0xe000

---

### Post by tunafishman on 2008-07-24
I followed all of the steps in the first post thoroughly (and repeatedly).

```
tunafish@tunafish-ubuntu:~$ lspci -nn|grep 14e4
03:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)

```

My blacklist currently includes
```
blacklist bcm43xx
blacklist b43
blacklist wl
blacklist b44
```

When I restart I still have to
```
sudo modprobe -r b43 b44 ndiswrapper wl
sudo depmod -ae
sudo modprobe ndiswrapper
```

The first line seems to need all 4 arguments for the process to work. I tried unloading them one at a time in an attempt to narrow down the possible offender, but it only works if I modprobe -r all the keys at once.

Apologies if I'm thick, I'm not trying to be.

Edit: Found out that
```
sudo modprobe -r b44 ndiswrapper
sudo modprobe ndiswrapper
```
seems to do the job. Why would b44 be bothering me if it's in my blacklist file?

---

### Post by Ayuthia on 2008-07-24
> **M8M said:**
> [QUOTE=Ayuthia;5450622]

I rebooted and seemed to have lost everything, no blue light on the wireless switch, no wireless option on the network manager, etc.

After the "ifconfig" command I got:
eth0  Link encap:Ethernet  HWaddr 00:16:36:e0:01:be
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:20 Base address:0xe000
Sorry about that.  I forgot to mention to you that this is going to happen.  There is something missing in /etc/modprobe.d/blacklist or /etc/modules that is not being loaded/unloaded.  You can get it started again by doing the modprobe commands listed earlier.  You will need to check the files:
Blacklist
```
grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper -e wl /etc/modprobe.d/blacklist
```
You will need to make sure that the following are listed:
blacklist b43
blacklist ssb
blacklist bcm43xx
blacklist wl
If they are not, you will need to add them:
```
echo blacklist <module>|sudo tee -a /etc/modprobe.d/blacklist
```
Just replace <module> with the module that is missing.

You will also need to make sure that ndiswrapper is loaded.  Check:
```
grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper -e wl /etc/modules
```Make sure that only ndiswrapper shows up.  If it is missing:
```
echo ndiswrapper|sudo tee -a /etc/modules
```
If b43, ssb, bcm43xx, or wl is listed in there, you will have to edit the file and remove it.  To edit he file:
```
gksu gedit /etc/modules
```

---

### Post by Ayuthia on 2008-07-24
> **tunafishman said:**
> I followed all of the steps in the first post thoroughly (and repeatedly).

```
tunafish@tunafish-ubuntu:~$ lspci -nn|grep 14e4
03:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)

```

My blacklist currently includes
```
blacklist bcm43xx
blacklist b43
blacklist wl
blacklist b44
```

When I restart I still have to
```
sudo modprobe -r b43 b44 ndiswrapper wl
sudo depmod -ae
sudo modprobe ndiswrapper
```

The first line seems to need all 4 arguments for the process to work. I tried unloading them one at a time in an attempt to narrow down the possible offender, but it only works if I modprobe -r all the keys at once.

Apologies if I'm thick, I'm not trying to be.

Edit: Found out that
```
sudo modprobe -r b44 ndiswrapper
sudo modprobe ndiswrapper
```
seems to do the job. Why would b44 be bothering me if it's in my blacklist file?

No need for apologies.  The new modules are harder to configure.  I am thinking that you have created a script that is loading b44.  You might check /etc/rc.local.  In step 4, there is a script that loads b44.  You only need it if you have the b44 driver for your wired connection.  You can check this by doing lshw -C network and check your eth0 card.  It will have b44 as the driver.  If it does not, then you don't need to load it.  If /etc/rc.local has any commands on modprobe (or modprobe -r)b44, b43, ssb, ndiswrapper, you can comment them out by adding # at the beginning of each line.  You can edit the file by:
```
gksu gedit /etc/rc.local
```
Hope that is what is causing it.

---

### Post by tunafishman on 2008-07-24
/etc/rc.local is clean. There is no mention anywhere that I can find of b44.

I fixed the problem by including a file named b44 in /etc/modprobe.d/ that blacklists b44.```
sudo depmod -ae
sudo update-initramfs -u
```
fixes the initrd script, apparently.

Rebooted, all is well. This make any sense to you?

---

### Post by Ayuthia on 2008-07-24
> **tunafishman said:**
> /etc/rc.local is clean. There is no mention anywhere that I can find of b44.

I fixed the problem by including a file named b44 in /etc/modprobe.d/ that blacklists b44.```
sudo depmod -ae
sudo update-initramfs -u
```
fixes the initrd script, apparently.

Rebooted, all is well. This make any sense to you?
It makes sense, but why that works instead of the other way surprises me.  You can create special blacklist files for each module which is what you did.  The initramfs is usually dealt with during booting (if I recall correctly).  So when you updated the initrd, it added the b44 blacklisting.  Apparently, something else must be calling b44 and since you created the special blacklist, it will never load.  Glad to see you have it working!

EDIT:
Upon further thinking, the b44 file that you created is most likely being checked every time something calls for that module where /etc/modprobe.d/blacklist most likely is being called only upon booting.   I am still thinking that something is calling b44 but I am not for sure what.

---

### Post by M8M on 2008-07-24
[QUOTE=Ayuthia;5451027]
If they are not, you will need to add them:
```
echo blacklist <module>|sudo tee -a /etc/modprobe.d/blacklist
```
Just replace <module> with the module that is missing.

After trying to add the ssb module I got the following:
bash: ssb: No such file or directory

I'm a real n00b, so I need step by step help. Thank you for holding my hand...

---

### Post by Ayuthia on 2008-07-24
> **M8M said:**
> [QUOTE=Ayuthia;5451027]
If they are not, you will need to add them:
```
echo blacklist <module>|sudo tee -a /etc/modprobe.d/blacklist
```
Just replace <module> with the module that is missing.

After trying to add the ssb module I got the following:
bash: ssb: No such file or directory

I'm a real n00b, so I need step by step help. Thank you for holding my hand...

Try the following:
```
echo blacklist ssb|sudo tee -a /etc/modprobe.d/blacklist
```

If that does not work, just go and edit the file:
```
gksu gedit /etc/modprobe.d/blacklist
```You can then add whatever you need.  Just let us know if you run into problems.

---

### Post by M8M on 2008-07-27
> **Ayuthia said:**
> [QUOTE=M8M;5451852]

Try the following:
```
echo blacklist ssb|sudo tee -a /etc/modprobe.d/blacklist
```

If that does not work, just go and edit the file:
```
gksu gedit /etc/modprobe.d/blacklist
```You can then add whatever you need.  Just let us know if you run into problems.

Thanks, now I see what I did wrong (I included the "<>"). I went through all these steps and it was all working fine, but I couldn't establish a connection. I concluded that that was b/c we were having general internet problems since Windows kept loosing internet too. After that we had no internet at all for a full day. Now its back and strong again, but when I turned my unbuntu on again to try it, I lost everything again (no blue light, no wireless option, etc) How do I make it so the settings stay and I don't have to start the steps all over again every time I shut down?

---

### Post by Ayuthia on 2008-07-27
> **M8M said:**
> [QUOTE=Ayuthia;5452311]

Thanks, now I see what I did wrong (I included the "<>"). I went through all these steps and it was all working fine, but I couldn't establish a connection. I concluded that that was b/c we were having general internet problems since Windows kept loosing internet too. After that we had no internet at all for a full day. Now its back and strong again, but when I turned my unbuntu on again to try it, I lost everything again (no blue light, no wireless option, etc) How do I make it so the settings stay and I don't have to start the steps all over again every time I shut down?

It might be easier to have you post the results of the following and then we can see what we need to get it to work on reboot:
```
grep -i -e b43 -e b44 -e bcm43xx -e ssb -e ndiswrapper /etc/modprobe.d/blacklist
grep -i -e b43 -e b44 -e bcm43xx -e ssb -e ndiswrapper /etc/modules
lshw -C network
```
In some cases, we just need to make sure that the blacklist and module files are all that is needed to make things work on reboot, but sometimes we need to add another command that will load and unload the modules.

---

### Post by ceolfrith on 2008-07-27
Just wanted to say thanks. I'm new to Linux and the forums arfe a major help.
I'm using an HP dv9000 and I followed the instructions and they worked. Now I can unplug and go get comfortable.

After I rebooted my download automatically installed after asking permission, so I stopped there. It works and I thank you for the help.

---

### Post by ceolfrith on 2008-07-27
Now if I could only spell.

---

### Post by M8M on 2008-07-29
It might be easier to have you post the results of the following and then we can see what we need to get it to work on reboot:
```
grep -i -e b43 -e b44 -e bcm43xx -e ssb -e ndiswrapper /etc/modprobe.d/blacklist
```
[/QUOTE]

I didn't fix anything since the last reboot and here are the results:

# replaced by b43 and ssb.
blacklist bcm43xx
blacklist bcm43xx
blacklist b43
blacklist ssb

After the modules one it showed only "ndiswrapper"

After the network one:
*-network
     description: Network controller
     product: BCM94311MCG wlan mini-PCI
     vendor: Broadcom Corporation
     physical id: 0
     bus info: pci@0000:03:00.0
     version: 01
     width: 32 bits
     clock: 33MHz
     capabilities: pm msi pciexpress bus_master cap_list
     configuration: driver=b43-pci-bridge latency=0 module=ssb

Thank you for your help.

---

### Post by M8M on 2008-07-29
I don't know if this is relevant or not, and if not just ignore. Under system>administration>windows wireless drivers there is currently installed a bcmwl5 driver with hardware present. I don't see bcmwl5 listed on the blacklist. But then I'm a total n00b so, my thinking may not be correct. Should it also be blacklisted? should I remove it? or is this totally irrelevant?

Thanks again.

---

### Post by Ayuthia on 2008-07-29
> **M8M said:**
> I don't know if this is relevant or not, and if not just ignore. Under system>administration>windows wireless drivers there is currently installed a bcmwl5 driver with hardware present. I don't see bcmwl5 listed on the blacklist. But then I'm a total n00b so, my thinking may not be correct. Should it also be blacklisted? should I remove it? or is this totally irrelevant?

Thanks again.
The windows wireless drivers is the driver that is used for NDISwrapper.  So this driver does not get noticed by the kernel and is not used.  The driver here is "wrapped" into ndiswrapper.  If it says that the hardware is present, it means that ndiswrapper is happy with that driver.

---

### Post by Ayuthia on 2008-07-29
> **M8M said:**
> It might be easier to have you post the results of the following and then we can see what we need to get it to work on reboot:
```
grep -i -e b43 -e b44 -e bcm43xx -e ssb -e ndiswrapper /etc/modprobe.d/blacklist
```


I didn't fix anything since the last reboot and here are the results:

# replaced by b43 and ssb.
blacklist bcm43xx
blacklist bcm43xx
blacklist b43
blacklist ssb

After the modules one it showed only "ndiswrapper"

After the network one:
*-network
     description: Network controller
     product: BCM94311MCG wlan mini-PCI
     vendor: Broadcom Corporation
     physical id: 0
     bus info: pci@0000:03:00.0
     version: 01
     width: 32 bits
     clock: 33MHz
     capabilities: pm msi pciexpress bus_master cap_list
     configuration: driver=b43-pci-bridge latency=0 module=ssb

Thank you for your help.[/QUOTE]

The only driver that I am not for sure about is b44.  This is a Broadcom driver for wired ethernet cards.  If you have a b44 card, when you type:
```
lspci -nn|grep 14e4
```, it will come up with two items.  If it only shows your 4311 card, then you most likely don't have the b44 driver.

To try out something different, we are going to create a new file to just blacklist the b43 module:
```
echo blacklist b43|sudo tee -a /etc/modprobe.d/b43
echo blacklist ssb|sudo tee -a /etc/modprobe.d/b43
```
In theory, this file will be checked every time the b43 module is being requested for loading.  If this file exists, it will read the file and do what it says.  Since it says to blacklist it, it should prevent the b43 module from loading.

---

### Post by M8M on 2008-07-29
Everything seems to be working ok (blue light), except that I can't log on. The signal strength is reasonably strong, (about 1/3 of the bar) but I can't log on.  I've tried different settings for the wireless, but still can't log on. I'm not sure what's wrong.

---

### Post by iHaVEnOmMrS on 2008-07-31
> **M8M said:**
> Everything seems to be working ok (blue light), except that I can't log on. The signal strength is reasonably strong, (about 1/3 of the bar) but I can't log on.  I've tried different settings for the wireless, but still can't log on. I'm not sure what's wrong.

I'm getting the same exact thing. Any help?

---

### Post by alexa.pintea on 2008-08-01
Hi!It's working for my HP NX7300!Thanks alot!

---

### Post by ThaRabbit on 2008-08-01
> **iHaVEnOmMrS said:**
> I'm getting the same exact thing. Any help?

I had the same issue, are you using 128 bit wep by any chance?

It seems the network manager fails to correctly configure in case of a 128 bit wep key on some systems:
[https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/67876](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/67876)

try this:
```
sudo iwconfig wlan0 mode managed
sudo iwconfig wlan0 essid yourwirelessnetworkname
sudo iwconfig wlan0 channel yourwirelessnetworkchannel
sudo iwconfig wlan0 key yourwepkey
```

then:
```
sudo dhclient wlan0
```

if you get something like this:
> Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan1/00:21:00:1e:d6:aa
Sending on   LPF/wlan1/00:21:00:1e:d6:aa
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.11 on wlan1 to 255.255.255.255 port 67
DHCPACK of 192.168.1.11 from 192.168.1.1
bound to 192.168.1.11 -- renewal in 35778 seconds.
stefan@lapsteef:~$ 


you're connected :)

----

**Working on HP 6720s**

Though I did have to unload ssb.

---

### Post by M8M on 2008-08-01
**Working on HP 6720s**

Though I did have to unload ssb.[/QUOTE]

I followed these steps (more than once) and got:
There is already a pid file /var/run/dhclient.pid with pid 12348 killed old client process, removed PID file
Internet systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:1a:73:1d:bf:0a
Sending on LPF/wlan0/00:1a:73:1d:bf:0a
Sending on Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping

We did manage to connect to a neighbor's unsecure network, but cannot connect to my own network with the Ubuntu 8.04, but can with the windows laptop.

I don't know understand the whole loading and unloading of modules, so I don't know how to unload the ssb.

---

### Post by M8M on 2008-08-01
> **ThaRabbit said:**
> I had the same issue, are you using 128 bit wep by any chance?

Yes, I am.

---

### Post by M8M on 2008-08-01
> **M8M said:**
> Everything seems to be working ok (blue light), except that I can't log on. The signal strength is reasonably strong, (about 1/3 of the bar) but I can't log on.  I've tried different settings for the wireless, but still can't log on. I'm not sure what's wrong.

I also lose the settings every time I reboot. So I have a little note pad scribble with the commands I need to punch in to get it working again, but I have to do that every time again.

---

### Post by ThaRabbit on 2008-08-02
> **M8M said:**
> [quote=ThaRabbit]**Working on HP 6720s**

Though I did have to unload ssb.

I followed these steps (more than once) and got:
There is already a pid file /var/run/dhclient.pid with pid 12348 killed old client process, removed PID file
Internet systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:1a:73:1d:bf:0a
Sending on LPF/wlan0/00:1a:73:1d:bf:0a
Sending on Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping

We did manage to connect to a neighbor's unsecure network, but cannot connect to my own network with the Ubuntu 8.04, but can with the windows laptop.

I don't know understand the whole loading and unloading of modules, so I don't know how to unload the ssb.[/QUOTE]

Ok, first, please post the output of:
```
sudo ndiswrapper -l
``` (that's an L non capital)
and
```
sudo iwconfig
```
and
```
sudo ifconfig
```

---

### Post by M8M on 2008-08-02
Ok, first, please post the output of:
```
sudo ndiswrapper -l
``` 
(that's an L non capital)

bcmwl5: driver installed
device (14E4:4311) present (alternate driver: bcm43xx)


and
```
sudo iwconfig
```
lo no wireless extensions.
eth0 no wireless extensions.

and
```
sudo ifconfig
```[/QUOTE]
eth0  Link encap:Ethernet HWaddr 00:16:36:e0:01:be
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:20 Base address:0xe000

Thanks

---

### Post by ThaRabbit on 2008-08-03
You didn't blacklist b43xx / b43 drivers?

Please post your /etc/modprobe.d/blacklist file's contents :)

---

### Post by M8M on 2008-08-03
I'm not sure how to do this, but looking back at the previous posts I followed this command:
grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper -e wl /etc/modprobe.d/blacklist

The result was the following (my comment in parentheses):
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist bcm43xx (yes, twice)
blacklist b43
blacklist ssb
blacklist wl

---

### Post by ThaRabbit on 2008-08-04
> **M8M said:**
> I'm not sure how to do this, but looking back at the previous posts I followed this command:
grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper -e wl /etc/modprobe.d/blacklist

The result was the following (my comment in parentheses):
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist bcm43xx (yes, twice)
blacklist b43
blacklist ssb
blacklist wl

Utterly confusing.

please do:
```
sudo modprobe -r b43
sudo modprobe -r ndiswrapper
duso modprobe ndiswrapper
```

then please post the output of:
```
ndiswrapper -l
```

and
```
dmesg
```

and
```
ifconfig
```

Please use pastebin for the longer outputs :)
[http://pastebin.ubuntu.com/](http://pastebin.ubuntu.com/)

---

### Post by M8M on 2008-08-04
Ok, I've never done this before, but I think I did it right...
Here's the link to the pastebin: [http://pastebin.ubuntu.com/34164/](http://pastebin.ubuntu.com/34164/)

Thank you for your help!

---

### Post by hackerlife on 2008-08-04
hey I've got an HPdv2000, and I'm trying to install my drivers without an internet connection. I just downloaded the two files onto a memstick and am going to put it on the ubuntu laptop. Is this gonna work? all help is much appreciated. I also have my own thread here:[http://ubuntuforums.org/showthread.php?t=878558](http://ubuntuforums.org/showthread.php?t=878558)
thanks all!

---

### Post by ThaRabbit on 2008-08-04
> **M8M said:**
> Ok, I've never done this before, but I think I did it right...
Here's the link to the pastebin: [http://pastebin.ubuntu.com/34164/](http://pastebin.ubuntu.com/34164/)

Thank you for your help!

That seems to work, try 

```
iwlist wlan0 scanning
```

You may have to redo the commands we did before.

if it detects your network using iwlist, then try:

```
sudo iwconfig wlan0 mode managed
sudo iwconfig wlan0 essid youressid
sudo iwconfig wlan0 channel yourchannel
sudo iwconfig wlan0 key yourwlanwepkey
```

Now do:
```
iwconfig
```

to check if the settings you set have been set correctly (post them again please :) ), if that is the case:
```
sudo dhclient wlan0
```

---

### Post by rkolb86 on 2008-08-08
worked on my HP CTO dv92000 (dv9000 customized) I had to use the Windows XP (32 bit) drivers from the HP site though. I have a BCM4328.

---

### Post by bookofjoshua on 2008-08-08
thank you very much! I'm a noob mostly because I can't get interested in programing and every time I have installed a version of Linux there was so much to do to make it work right I would just give up.

Thanks to you (and of course everyone who programs on Ubuntu) I now have all the functions I need to get more familiar with Ubuntu (linux in general) and I think it will be more fun this time.

Thanks!!!!!!:KS

---

### Post by ramsuhas on 2008-08-09
Thanks a lot... :D
You Rock! :guitar:

---

### Post by TerryP on 2008-08-12
Outstanding!  Wireless is working great! :) 

System is a Compaq C714NR with BCM4311MCG Rev 02 on Hardy 8.04.01.  Kernel is "2.6.24-19-generic" X86_64.  I'm a Linux newbie and spent countless hours over several days to get the wireless card working. I think I tried every other how-to I could find at least once (often multiple times) with no success -- until I found this one!  

Since I didn't have an Internet connection, I used another PC to download the files and the Ubuntu CD in the optical drive for the commands in Step 9.  I didn't realize it at the time, but later found that I didn't add "generic" to the end of `uname -r` for the following commands in Step 9:

sudo apt-get install linux-headers-`uname -r`

sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build

In spite of the mistakes, it's working flawlessly, but I'm unsure whether I should repeat all the steps again to be sure (if it ain't broke, don't fix it?).


Thank you for this awesome work!

---

### Post by japelj on 2008-08-15
Hello! I followed the instructions and the result is that my computer can actually detect the network but it can't connect. (actually I managed to get a connection once, but I was unable to access the internet via google...). So, here are some results and I ask you, if you can look at them:

lshw -C network

[HTML]WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82562GT 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1f:29:86:42:ae
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=1.1-2 latency=0 module=e1000 multicast=yes
  *-network
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: wlan1
       version: 02
       serial: 00:21:00:0f:af:67
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g[/HTML]

ndiswrapper -v

[HTML]utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-19-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-19-generic SMP mod_unload 586 [/HTML]


ndiswrapper -l

[HTML]bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: bcm43xx)[/HTML]


lsmod | grep -i -e b43 -e ssb -e ndiswrapper -e bcm43xx

[HTML]ssb                    34308  1 b44
ndiswrapper           192920  0 
usbcore               146028  5 ndiswrapper,hci_usb,ehci_hcd,uhci_hcd[/HTML]

---

### Post by claudiney on 2008-08-15
thanks for the tutorial, it works perfectly on my hp dv6409 laptop. 
I have tried for weeks to have it work, using different tutorial,but none work. your explanation was simple to follow and works.
I really appreciate your time and help posting the tutorial.
God Bless you!
C.Esteves

---

### Post by MisanthropicAnthropoid on 2008-08-18
I started a new thread today trying to figure out how to do this (didn't know what wireless card I had at the time), and it took three hours to enable what I apparently need to disable (generally because I have no idea what I'm doing). Anyways, I don't have an internet connection at all in Ubuntu right now, so I can't go through this until tomorrow or Tuesday, but it appears that the first link is down. Is there another not-rapidshare source from which to download the file?

---

### Post by Ayuthia on 2008-08-18
> **MisanthropicAnthropoid said:**
> I started a new thread today trying to figure out how to do this (didn't know what wireless card I had at the time), and it took three hours to enable what I apparently need to disable (generally because I have no idea what I'm doing). Anyways, I don't have an internet connection at all in Ubuntu right now, so I can't go through this until tomorrow or Tuesday, but it appears that the first link is down. Is there another not-rapidshare source from which to download the file?

You might try the following steps:
```
sudo apt-get install cabextract
wget ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe
cabextract sp34152.exe
```

This information comes from [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by MisanthropicAnthropoid on 2008-08-18
> **Ayuthia said:**
> You might try the following steps:
```
sudo apt-get install cabextract
wget ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe
cabextract sp34152.exe
```

This information comes from [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Thanks for the attempt, but those instructions fail. And I can't do anything with the instructions given in the original post because the first link is broken. Any other ideas?

---

### Post by Ayuthia on 2008-08-18
> **MisanthropicAnthropoid said:**
> Thanks for the attempt, but those instructions fail. And I can't do anything with the instructions given in the original post because the first link is broken. Any other ideas?

Can you go into the Terminal and tell me the numbers in the brackets for the Vendor, Device, SVendor, Sdevice, and Rev:
```
lspci -nnmvd 14e4:*
```
The information should look something like:
```
Device: 03:00.0
Class:  Network controller [0280]
Vendor: Broadcom Corporation [14e4]
Device: BCM4311 802.11b/g WLAN [4311]
SVendor:        Hewlett-Packard Company [103c]
SDevice:        BCM4311 802.11b/g Wireless LAN Controller [1363]
Rev:    01

```
And I would like to see something like:
14e4 4311 103c 1363 01

---

### Post by MisanthropicAnthropoid on 2008-08-18
```
jay@jay-laptop:~$ lspci -nnmvd 14e4:*
Device: 03:00.0
Class:  Network controller [0280]
Vendor: Broadcom Corporation [14e4]
Device: BCM94311MCG wlan mini-PCI [4311]
SVendor:        Hewlett-Packard Company [103c]
SDevice:        Unknown device [1374]
Rev:    02

jay@jay-laptop:~$ 

```

Also, the thread I mentioned previously trying to get help in is here: [http://ubuntuforums.org/showthread.php?t=892808](http://ubuntuforums.org/showthread.php?t=892808)

I'm generally making a mess of things, so I don't know if there's any useful information there, but that's what I've got.

---

### Post by Ayuthia on 2008-08-18
> **MisanthropicAnthropoid said:**
> ```
jay@jay-laptop:~$ lspci -nnmvd 14e4:*
Device: 03:00.0
Class:  Network controller [0280]
Vendor: Broadcom Corporation [14e4]
Device: BCM94311MCG wlan mini-PCI [4311]
SVendor:        Hewlett-Packard Company [103c]
SDevice:        Unknown device [1374]
Rev:    02

jay@jay-laptop:~$ 

```

Also, the thread I mentioned previously trying to get help in is here: [http://ubuntuforums.org/showthread.php?t=892808](http://ubuntuforums.org/showthread.php?t=892808)

I'm generally making a mess of things, so I don't know if there's any useful information there, but that's what I've got.

Ok!  That did have some useful information.  It might be better to see if we can get the bcm43xx driver to work first.  By any chance did you get the bcm43xx-fwcutter installed?  If so, can you check and see if the following exists:
```
ls -l /usr/share/bcm43xx-fwcutter/install*
```
It has been a while since I have tried Gutsy and I can't remember how well the bcm43xx driver worked for your card.

If you want to try the NDISwrapper route, can you let us know if you are still using Windows?  If so, is it something else besides Vista?  We need to have a Windows driver that is not from Vista to get ndiswrapper to work.

You also mentioned that you could not get the sp34152.exe to work.  What did you mean by that?  Were you not able to download the file, not able to get cabextract installed, or did the driver not work with NDISwrapper?

There is also a Linux driver that has been created by Broadcom.  However, I don't think that it has been tested in any kernels less than 2.6.24 so I am not for sure if it is going to work in Gutsy.  Here is the link to it:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Can you also let us know if you are using 32-bit or 64-bit?

---

### Post by MisanthropicAnthropoid on 2008-08-18
> **Ayuthia said:**
> Ok!  That did have some useful information.  It might be better to see if we can get the bcm43xx driver to work first.  By any chance did you get the bcm43xx-fwcutter installed?  If so, can you check and see if the following exists:
```
ls -l /usr/share/bcm43xx-fwcutter/install*
```
It has been a while since I have tried Gutsy and I can't remember how well the bcm43xx driver worked for your card.

If you want to try the NDISwrapper route, can you let us know if you are still using Windows?  If so, is it something else besides Vista?  We need to have a Windows driver that is not from Vista to get ndiswrapper to work.

You also mentioned that you could not get the sp34152.exe to work.  What did you mean by that?  Were you not able to download the file, not able to get cabextract installed, or did the driver not work with NDISwrapper?

There is also a Linux driver that has been created by Broadcom.  However, I don't think that it has been tested in any kernels less than 2.6.24 so I am not for sure if it is going to work in Gutsy.  Here is the link to it:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Can you also let us know if you are using 32-bit or 64-bit?

Well, I no longer have Internet access with Ubuntu (I can try to find a connection again tomorrow). I do still have windows, but it is Vista (with which I'm getting a wireless connection). With the instructions you linked, I followed them all, but when step 3 started, and I tried to call the NDISwrapper file, it claimed that the file wasn't found.

---

### Post by Ayuthia on 2008-08-19
> **MisanthropicAnthropoid said:**
> Well, I no longer have Internet access with Ubuntu (I can try to find a connection again tomorrow). I do still have windows, but it is Vista (with which I'm getting a wireless connection). With the instructions you linked, I followed them all, but when step 3 started, and I tried to call the NDISwrapper file, it claimed that the file wasn't found.

Ok.  We can confirm that bcm43xx works for you.  Since you lost your wireless connection, it is because the b43legacy firmware portion is not working for your card.  You should be able to get your wireless back by doing the following (it will only work for the current session):
```
sudo modprobe -r b43 b44 b43legacy ndiswrapper wl ssb bcm43xx
sudo depmod -ae
sudo modprobe bcm43xx
sudo ifconfig wlan0 up
```

When you have a chance, I would like to see if there is any information in dmesg when you load ndiswrapper.  Can you do the following:
```
sudo modprobe -r b43 b44 b43legacy ndiswrapper wl ssb bcm43xx
sudo depmod -ae
sudo modprobe ndiswrapper
dmesg|grep ndis
```

---

### Post by MisanthropicAnthropoid on 2008-08-19
> **Ayuthia said:**
> Ok.  We can confirm that bcm43xx works for you.  Since you lost your wireless connection, it is because the b43legacy firmware portion is not working for your card.  You should be able to get your wireless back by doing the following (it will only work for the current session)

Not quite accurate. I never had any wireless connection in Ubuntu. I was stealing an ethernet connection from my parents' computer, but their AC is broken and they have no available plugs, so I lasted as long as my battery and then decided to break until tomorrow. Getting the wireless in Ubuntu is the task at hand, and it's still seeming a bit intimidating.

---

### Post by Ayuthia on 2008-08-19
> **MisanthropicAnthropoid said:**
> Not quite accurate. I never had any wireless connection in Ubuntu. I was stealing an ethernet connection from my parents' computer, but their AC is broken and they have no available plugs, so I lasted as long as my battery and then decided to break until tomorrow. Getting the wireless in Ubuntu is the task at hand, and it's still seeming a bit intimidating.

Sorry, I meant that we know that bcm43xx does something but the b43 modules do not.  I did not mean to say that it works.

If you are willing, you could try out this:
[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

It is for 8.04.  The only downside to it is that it is a pre-release kernel.  It does seem to work for your card.

---

### Post by MisanthropicAnthropoid on 2008-08-19
> **Ayuthia said:**
> Sorry, I meant that we know that bcm43xx does something but the b43 modules do not.  I did not mean to say that it works.

If you are willing, you could try out this:
[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

It is for 8.04.  The only downside to it is that it is a pre-release kernel.  It does seem to work for your card.

I'm only in 7.10 though. And I don't seem to be able to update. Every time I click on "update," it tells me that certain packages can't be authenticated, and then lists pretty much every package.

---

### Post by MisanthropicAnthropoid on 2008-08-19
> **Ayuthia said:**
> 
```
sudo modprobe -r b43 b44 b43legacy ndiswrapper wl ssb bcm43xx

```

```

FATAL: Module b43 not found

```

---

### Post by Ayuthia on 2008-08-19
> **MisanthropicAnthropoid said:**
> ```

FATAL: Module b43 not found

```

I am not for sure why it says that it is FATAL.  It just means that the module is not loaded.  Nothing to worry about.  We are trying to remove it.

---

### Post by jackechanprime on 2008-08-19
i donno how else to say this so... erm... help?

I have a Compaq Presario C700 with an Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter. aaaand... it dosnt work. I'm running hardy heron, and have tried a whole bunch of stuff, and nothing has really worked. ndiswrapper makes my computer crash/freeze every 3 minutes, but gets me wireless. where as none of the other drivers even phazed the problem. when i looked at your instructions, and clicked the download link for the driver, i got a 404 error, and i have been finding those allover the net every time i think i finally found the god given 'this one actually works' page. i think theyre all pointing to the same page, and if so, it's been down for at least 3 weeks now. soooo... does anyone have the file i need/ know what's going on/ have the slightest clue how to help me? i've had sooooo little luck elsewhere that i'm getting desperate.

plz, anyone, help.
*begs on hands and knees... trying to not look to totally pathetic...*
jack

---

### Post by rehaby on 2008-08-20
> **jackechanprime said:**
> i donno how else to say this so... erm... help?

I have a Compaq Presario C700 with an Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter. aaaand... it dosnt work. I'm running hardy heron, and have tried a whole bunch of stuff, and nothing has really worked. ndiswrapper makes my computer crash/freeze every 3 minutes, but gets me wireless. where as none of the other drivers even phazed the problem. when i looked at your instructions, and clicked the download link for the driver, i got a 404 error, and i have been finding those allover the net every time i think i finally found the god given 'this one actually works' page. i think theyre all pointing to the same page, and if so, it's been down for at least 3 weeks now. soooo... does anyone have the file i need/ know what's going on/ have the slightest clue how to help me? i've had sooooo little luck elsewhere that i'm getting desperate.

plz, anyone, help.
*begs on hands and knees... trying to not look to totally pathetic...*
jack

Heres the a link to the same file. Good luck [http://rs8.rapidshare.com/files/70969505/WLANBroadcom.tar.gz](http://rs8.rapidshare.com/files/70969505/WLANBroadcom.tar.gz)

---

### Post by jackechanprime on 2008-08-21
erm... arn't these windows files? can u show me how to work them with ubuntu?

oh, and btw, i just reinstalled ubuntu, so the system should be clean of the prior mentioned 'drama' getting other drivers and stuff (and yes, the wireless card still dosent work, at least as far as my somewhat unskilled eye can see.)

---

### Post by chamus on 2008-08-22
hi to all. I have here really a problem, i had been trying alot to set up my broadcom, and i had already done it ones, but now i can not.
The strange thing is that when i go to restricted hardware nothing apears, an when i type "lspci | grep Broadcom" nothing apears, i had also install hardinfo to search manually for my card but nothing apeard there.
So at the first steps of this tutorial i dont know the broadcom i have.
My system is ubuntu 8.04 and my notebook is a Compaq f500, and i think that my card is a broadcom bcm94311 mini pci, but i am not sure of this last. What can i do? i really think that my card is broken, could it be? Can somebody help with this!!

Thanks.
:(

---

### Post by Ayuthia on 2008-08-22
> **chamus said:**
> hi to all. I have here really a problem, i had been trying alot to set up my broadcom, and i had already done it ones, but now i can not.
The strange thing is that when i go to restricted hardware nothing apears, an when i type "lspci | grep Broadcom" nothing apears, i had also install hardinfo to search manually for my card but nothing apeard there.
So at the first steps of this tutorial i dont know the broadcom i have.
My system is ubuntu 8.04 and my notebook is a Compaq f500, and i think that my card is a broadcom bcm94311 mini pci, but i am not sure of this last. What can i do? i really think that my card is broken, could it be? Can somebody help with this!!

Thanks.
:(

From what I have seen with lspci is that if your card does not show up in there, it usually means that the hardware is not working for some reason.  If you have Windows installed on your laptop still, you might see if you can connect from there.  If you can't, then it is definitely a hardware issue.

---

### Post by minder on 2008-08-22
Funny thing - Ubuntu 8.04 right after install shows "Broadcom .... BCM[b]9[b]4311..." but after update it changed to "BCM4311":confused: The rest of the line looks pretty the same.

The laptop is **HP Compaq 6720s**

Before the update I switched on the Broadcom driver (I'm not sure now if I even downloaded the firmware!) in the System -> Administration -> Drivers and I was able to detect my home network and even connect to it. Unfortunatelly packets were unable to travel - only during the first second after establishing the connection (!)

I don't consider myself a total n00b and I got really confused after the WiFi stopped to work at all after the upgrade (new kernel - was 2.6.24-17, now is 2.6.24-19). dmesg first showed that the driver some eror ("b43-phy0: Radio hardware status changed to DISABLED"). after reloading the module there was one funny thing: "b43-phy0: Radio turned on by software
b43-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on." :D
But the laptop has no buttons tu turn WiFi on/off. I mean - sure, it has a button with the antenna symbol which normally lits orange and turns to blue after I tap it (that's when the Bletooth applet kicks in). Tapping it again turns the light to orange again. And no networks detected.

Then I followed this HOWTO. Now dmesg says that ndiswrapper has control over the wifi card. And still nothing! Tapping the wifibutton once turns the bluetooth on, tapping it the second time... wait.. some networks showed up! Weeee! Erm... looks like it won't connect to my home network. But it sees it!

Quick check of lsmod:

hmmmm... what's this: b44 ? I had b43 as the driver before blacklisting it during this howto. should I blacklist b44 too? Anyone has any idea why this laptop behaves so funny?

P.S.
Since the link to the driver in the first post is cold dead, I downloaded driver for WindowsXP from HP website (.exe file which I unpacked using Wine).

P.S.2
```

# ndiswrapper -l

bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: ssb)
```

---

### Post by summuner848 on 2008-08-23
Thank u soo much!

---

### Post by jackechanprime on 2008-08-23
> **jackechanprime said:**
> erm... arn't these windows files? can u show me how to work them with ubuntu?

oh, and btw, i just reinstalled ubuntu, so the system should be clean of the prior mentioned 'drama' getting other drivers and stuff (and yes, the wireless card still dosent work, at least as far as my somewhat unskilled eye can see.)

erm... do i need ndiswraper? I know i'm really green at ubuntu, but i really need help. I got the files, and went to my friend to ask him how to work them, and he told me that theyre windows files. he kinda... didn't say anything else, we were IMing, and he never responded again. soo, yeah, i really don't have anywhere else to turn (that i know of). please, if anyone knows what i need to do, please help me.

jack

---

### Post by LaGzo on 2008-09-01
I tried this twice and it's not working. Ndiswrapper worked for me before and now for some reason it isn't. 

When I try make distclean I get - ERROR 2, something like that. Everything else goes in fine.

---

### Post by spocksbeard on 2008-09-01
> **rehaby said:**
> Heres the a link to the same file. Good luck [http://rs8.rapidshare.com/files/70969505/WLANBroadcom.tar.gz](http://rs8.rapidshare.com/files/70969505/WLANBroadcom.tar.gz)

Hey, rapidshare seems to think I'm downloading something already when I'm not and won't let me download the file, any chance you know of anywhere else it's posted?

TIA

---

### Post by spocksbeard on 2008-09-01
Not to worry, I managed to make it work without this guide through random clicking and finger crossing. Whether it works after a reboot only time will tell. I **THINK** what I did was go to System>Administration>Hardware Drivers and tick the box in there, which lead to a box telling me that it would need firmware, which the next step then allowed me to download after ticking another box. Sorry if thats not very clear, I'm having to remember what I clicked at random.

If it makes any difference I am using Wubi and Windows XP Pro (on a Dell Inspiron 6400) as I wanted be sure about Ubuntu before doing a proper dualboot system.

---

### Post by josiahtreibs on 2008-09-03
HELP! Can't download first file (WLANBroadcom.tar.gz?) I can't find it anywhere on the web! Is there another place to download it?

---

### Post by josiahtreibs on 2008-09-03
oh! second to last post. there it was. like the doofus I am.

---

### Post by josiahtreibs on 2008-09-03
I still don't know why I couldn't find it on the web.#-o

---

### Post by mandi_ich on 2008-09-08
I am new to ubuntu, I had Windows before so I have no idea on how to use ubuntu but I am trying.
Sorry if this sounds completely stupid but, when I type lspci |grep Broadcom on my terminal nothing comes up, and when I use just lpsci my wireless adapter is not listed..
I have an HP dv2415nr. When I first installed Ubuntu, about a week ago, the wireless adapter was working fine, but now the led is always red, meaning that my wireless adapter is off, and it wont turn blue now. I had the same exact problem with Windows, and many more, even with my HD. So I bought a new hard drive and installed ubuntu and now I cant get my wireless to work!
please help...

---

### Post by Ayuthia on 2008-09-08
> **mandi_ich said:**
> I am new to ubuntu, I had Windows before so I have no idea on how to use ubuntu but I am trying.
Sorry if this sounds completely stupid but, when I type lspci |grep Broadcom on my terminal nothing comes up, and when I use just lpsci my wireless adapter is not listed..
I have an HP dv2415nr. When I first installed Ubuntu, about a week ago, the wireless adapter was working fine, but now the led is always red, meaning that my wireless adapter is off, and it wont turn blue now. I had the same exact problem with Windows, and many more, even with my HD. So I bought a new hard drive and installed ubuntu and now I cant get my wireless to work!
please help...

Did you install Windows back on to see if the wireless card still works there?  You might check and see if there is a BIOS setting for it too.  You might even check HP to see if there is a "recall" of any sort for your laptop.  I know that there was one for the dv6000/9000 series, and mine encountered the same issue but was fixed by HP at no cost.  However yours is a dv2000 series so I am not for sure if the issue goes out to that or not.

You could try another liveCD and see if it notices your card.

---

### Post by mandi_ich on 2008-09-08
Yeah I've checked with HP and there's no recall, nothing... My hard drive broke, so they replaced it, but that was all. I have no idea of how can I check if there is a BIOS setting for it or what you mean by trying another liveCD... Sorry, I am really a begginer with computers...

---

### Post by Ayuthia on 2008-09-08
> **mandi_ich said:**
> Yeah I've checked with HP and there's no recall, nothing... My hard drive broke, so they replaced it, but that was all. I have no idea of how can I check if there is a BIOS setting for it or what you mean by trying another liveCD... Sorry, I am really a begginer with computers...

For the BIOS, there should be a screen that comes up when you boot and it will give you an option to go into setup.  I want to say it is either F3 or F10, but I cannot remember.

As for the liveCD, you might try and see if you can see your card by using the Ubuntu install CD.  Just put in the CD and reboot.  Just select the option that does not do the install (I think it is the first option on the Ubuntu splash screen) and then when it has finished starting up, go into the Terminal and type lspci and see if your card shows up.

---

### Post by avinash_destiny on 2008-09-09
Thanx for this simple and great explaination
When executed last command it worked and after a restart the wireless n/w is getting detected but not getting connected ...its not any n/w problem

---

### Post by rakan21 on 2008-09-11
Well after staying up 6 hours strait trying to get the BCM94311MCG wlan mini-PC to work on 8.04 I have figured out the simplest and shortest way ever.

wget [http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2](http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2)
tar xjf b43-fwcutter-011.tar.bz2
cd b43-fwcutter-011
make
cd ..


just copy and paste these codes make sure your connected to a Ethernet cable to download the stuff. I you don't have a Ethernet then you can get another laptop or PC near you and download the tarball. Then extract it into your home directory, navigate to b43-fwcutter-011, then type in make, then type in cd ..
System restart is not required but I recommend you do so. Just in case.

-Siliconic Hell
Enjoy.

P.S. for newbies this is all done in terminal just copy and past one line @ a time.  :)

---

### Post by willie8605 on 2008-09-13
you can add the hp pavilion zv5000 to the working list too.

thanks!

---

### Post by pwnprog on 2008-09-15
hi there. what would be the proper way to "re-install" these drivers. i installed these about 6 months ago and now they are beginning to act up. occasionally wireless will stop working and i'll have to reboot the computer to get it up and running again

---

### Post by Zorinea on 2008-09-18
Link for the driver is broken and the site it is hosted on says "Under COnstruction"

Anyone got an alternate link?

---

### Post by Ayuthia on 2008-09-18
> **Zorinea said:**
> Link for the driver is broken and the site it is hosted on says "Under COnstruction"

Anyone got an alternate link?

Try this one:
[http://ubuntuforums.org/showpost.php?p=5627620&postcount=251](http://ubuntuforums.org/showpost.php?p=5627620&postcount=251)

---

### Post by KashvW on 2008-09-23
Thank you so much. I now have my wireless working.

---

### Post by matic13 on 2008-09-23
it works fine for me :D thanks

---

### Post by tictac1608 on 2008-10-13
[COLOR="DarkRed"]Step 9[/COLOR]

Install ndiswrapper from source

[INDENT] Now you need to edit five things the following before you put it into the terminal

```
sudo apt-get update

sudo apt-get install build-essential

sudo apt-get install linux-headers-[COLOR="Red"]`uname -r`[/COLOR]

sudo ln -s /usr/src/linux-[COLOR="Red"]`uname -r`[/COLOR] /lib/modules/[COLOR="Red"]`uname -r`[/COLOR]/build

mkdir -p ~/bcm43xx/ndiswrapper

cd ~/bcm43xx/ndiswrapper

sudo wget http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-[COLOR="Red"]1.53[/COLOR].tar.gz

tar xvzf ndiswrapper-[COLOR="Red"]1.53[/COLOR].tar.gz

cd ndiswrapper*

make distclean

make

sudo make install
```

All three 'uname -r' need to be replaced with the output you got in step 8 (no " quotes should be in the code)

ie on the third line i put 

sudo apt-get install linux-headers-2.6.22-14-generic

The other two highlighted items need to be the release number you got in step 2
If it is still 1.53 just leave them like that. [/INDENT]

I got stucked in this step because I don't have a wired connection.I downloaded ndiswrapper-[COLOR="Red"]1.53[/COLOR].tar.gz.How to install it and go through this step (codes)? Thanks

---

### Post by Ayuthia on 2008-10-13
> **tictac1608 said:**
> [COLOR="DarkRed"]Step 9[/COLOR]

Install ndiswrapper from source

[INDENT] Now you need to edit five things the following before you put it into the terminal

```
sudo apt-get update

sudo apt-get install build-essential

sudo apt-get install linux-headers-[COLOR="Red"]`uname -r`[/COLOR]

sudo ln -s /usr/src/linux-[COLOR="Red"]`uname -r`[/COLOR] /lib/modules/[COLOR="Red"]`uname -r`[/COLOR]/build

mkdir -p ~/bcm43xx/ndiswrapper

cd ~/bcm43xx/ndiswrapper

sudo wget http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-[COLOR="Red"]1.53[/COLOR].tar.gz

tar xvzf ndiswrapper-[COLOR="Red"]1.53[/COLOR].tar.gz

cd ndiswrapper*

make distclean

make

sudo make install
```

All three 'uname -r' need to be replaced with the output you got in step 8 (no " quotes should be in the code)

ie on the third line i put 

sudo apt-get install linux-headers-2.6.22-14-generic

The other two highlighted items need to be the release number you got in step 2
If it is still 1.53 just leave them like that. [/INDENT]

I got stucked in this step because I don't have a wired connection.I downloaded ndiswrapper-[COLOR="Red"]1.53[/COLOR].tar.gz.How to install it and go through this step (codes)? Thanks

Have you installed build-essential?  If so you need to do the last five commands in Step 9.

As for `uname -r`, they are back-quotes (`) not single quotes (').  If you do the following in the Terminal:
```
echo `uname -r`
```It should return 2.6.22-14-generic.  If it shows 'uname -r' then you are using the single quotes.

---

### Post by billgujie on 2008-10-14
hi, everything is fine until i get to type:
```
ndiswrapper -l
```

and get this back:
```
WARNING: /etc/modprobe.d/ndiswrapper line 5: ignoring bad line starting with 'ndiswrapper'
WARNING: /etc/modprobe.d/ndiswrapper line 8: ignoring bad line starting with 'ndiswrapper'
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: ssb)
```

and after i added "ndiswrapper" in the opening txt file and save it then i type:
```
sudo modprobe ndiswrapper
```

and get errors:
```
WARNING: /etc/modprobe.d/ndiswrapper line 5: ignoring bad line starting with 'ndiswrapper'
WARNING: /etc/modprobe.d/ndiswrapper line 8: ignoring bad line starting with 'ndiswrapper'
WARNING: /etc/modprobe.d/ndiswrapper line 5: ignoring bad line starting with 'ndiswrapper'
WARNING: /etc/modprobe.d/ndiswrapper line 8: ignoring bad line starting with 'ndiswrapper'
WARNING: /etc/modprobe.d/ndiswrapper line 5: ignoring bad line starting with 'ndiswrapper'
WARNING: /etc/modprobe.d/ndiswrapper line 8: ignoring bad line starting with 'ndiswrapper'
WARNING: /etc/modprobe.d/ndiswrapper line 5: ignoring bad line starting with 'ndiswrapper'
WARNING: /etc/modprobe.d/ndiswrapper line 8: ignoring bad line starting with 'ndiswrapper'
WARNING: /etc/modprobe.d/ndiswrapper line 5: ignoring bad line starting with 'ndiswrapper'
WARNING: /etc/modprobe.d/ndiswrapper line 8: ignoring bad line starting with 'ndiswrapper'
Usage: modprobe [-v] [-V] [-C config-file] [-n] [-i] [-q] [-Q] [-b] [-o <modname>] [ --dump-modversions ] <modname> [parameters...]
modprobe -r [-n] [-i] [-v] <modulename> ...
modprobe -l -t <dirname> [ -a <modulename> ...]
FATAL: Error running install command for ndiswrapper
```

and the last command (sudo ndiswrapper -m) also get error feedback:
```
WARNING: /etc/modprobe.d/ndiswrapper line 5: ignoring bad line starting with 'ndiswrapper'
WARNING: /etc/modprobe.d/ndiswrapper line 8: ignoring bad line starting with 'ndiswrapper'
module configuration already contains alias directive

module configuration contains directive install ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install
;you should delete that at /usr/sbin/ndiswrapper line 868, <MODPROBE> line 285.
module configuration contains directive install ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install
;you should delete that at /usr/sbin/ndiswrapper line 868, <MODPROBE> line 289.
```

someone can help me?

---

### Post by tictac1608 on 2008-10-14
> **Ayuthia said:**
> Have you installed build-essential?  If so you need to do the last five commands in Step 9.

As for `uname -r`, they are back-quotes (`) not single quotes (').  If you do the following in the Terminal:
```
echo `uname -r`
```It should return 2.6.22-14-generic.  If it shows 'uname -r' then you are using the single quotes.
Thanks Ayuthia!You solved my problem.
Cheers

---

### Post by Ayuthia on 2008-10-14
> **billgujie said:**
> hi, everything is fine until i get to type:
```
ndiswrapper -l
```

and get this back:
```
WARNING: /etc/modprobe.d/ndiswrapper line 5: ignoring bad line starting with 'ndiswrapper'
WARNING: /etc/modprobe.d/ndiswrapper line 8: ignoring bad line starting with 'ndiswrapper'
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: ssb)
```

and after i added "ndiswrapper" in the opening txt file and save it then i type:
```
sudo modprobe ndiswrapper
```

and get errors:
```
WARNING: /etc/modprobe.d/ndiswrapper line 5: ignoring bad line starting with 'ndiswrapper'
WARNING: /etc/modprobe.d/ndiswrapper line 8: ignoring bad line starting with 'ndiswrapper'
WARNING: /etc/modprobe.d/ndiswrapper line 5: ignoring bad line starting with 'ndiswrapper'
WARNING: /etc/modprobe.d/ndiswrapper line 8: ignoring bad line starting with 'ndiswrapper'
WARNING: /etc/modprobe.d/ndiswrapper line 5: ignoring bad line starting with 'ndiswrapper'
WARNING: /etc/modprobe.d/ndiswrapper line 8: ignoring bad line starting with 'ndiswrapper'
WARNING: /etc/modprobe.d/ndiswrapper line 5: ignoring bad line starting with 'ndiswrapper'
WARNING: /etc/modprobe.d/ndiswrapper line 8: ignoring bad line starting with 'ndiswrapper'
WARNING: /etc/modprobe.d/ndiswrapper line 5: ignoring bad line starting with 'ndiswrapper'
WARNING: /etc/modprobe.d/ndiswrapper line 8: ignoring bad line starting with 'ndiswrapper'
Usage: modprobe [-v] [-V] [-C config-file] [-n] [-i] [-q] [-Q] [-b] [-o <modname>] [ --dump-modversions ] <modname> [parameters...]
modprobe -r [-n] [-i] [-v] <modulename> ...
modprobe -l -t <dirname> [ -a <modulename> ...]
FATAL: Error running install command for ndiswrapper
```

and the last command (sudo ndiswrapper -m) also get error feedback:
```
WARNING: /etc/modprobe.d/ndiswrapper line 5: ignoring bad line starting with 'ndiswrapper'
WARNING: /etc/modprobe.d/ndiswrapper line 8: ignoring bad line starting with 'ndiswrapper'
module configuration already contains alias directive

module configuration contains directive install ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install
;you should delete that at /usr/sbin/ndiswrapper line 868, <MODPROBE> line 285.
module configuration contains directive install ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install
;you should delete that at /usr/sbin/ndiswrapper line 868, <MODPROBE> line 289.
```

someone can help me?

Can you post the results of:
```
cat /etc/modprobe.d/ndiswrapper
```

---

### Post by djb6 on 2008-10-15
Does this work for Ubuntu 8.10 release?  I just downloaded and installed it and everything else works great, except the wireless.  I wanted to ask before I went ahead and tried to make sure I don't mess anything else up.

---

### Post by Ayuthia on 2008-10-15
> **djb6 said:**
> Does this work for Ubuntu 8.10 release?  I just downloaded and installed it and everything else works great, except the wireless.  I wanted to ask before I went ahead and tried to make sure I don't mess anything else up.

Yes, this should work on 8.10. However, if you have a 4311 card, you should try the wl driver on it first.  It comes with 8.10 and seems to work pretty well with the 4311 cards.

EDIT: I have not verified this, but it looks like if you compile ndiswrapper from source, it will not compile in 2.6.27 (Intrepid's kernel).  It does look like the ndiswrapper devs are working on a fix for it.  I do believe that the ndiswrapper package from the Ubuntu repositories will work though.

---

### Post by sungbros on 2008-10-17
WOW. Worked like a charm for me. Dual booting on a Dell Inspiron 640M w/ Vista. Added a fresh install of Hardy Heron w/ kernel 2.6.24-19-generic. Tried several other threads over 2 days and was just getting frustrated, as I have no wired network access (getting internet thru free neighborhood wifi only). Used this tutorial with the below advice and it worked right away. This was literally my last attempt before I gave up on trying to learn Linux... thanks!:)



> **haitechan said:**
> Reporting a working Compaq v3000 with Hardy here! :p

I had some troubles because I didn't have another way to connect to internet and download the packages, neither do sudo apt-get update :(, so I went to another machine (I was configuring my mom's laptop :)) and downloaded the following packages on my home directory:

[LIST]
[*]build-essential_11.3ubuntu1_i386.deb
[*]dpkg-dev_1.14.16.6ubuntu3_all.deb
[*]g++-4.2_4.2.3-2ubuntu7_i386.deb
[*]g++_4.2.3-1ubuntu3_i386.deb
[*]libc6-dev_2.7-10ubuntu3_i386.deb
[*]libstdc++6-4.2-dev_4.2.3-2ubuntu7_i386.deb
[*]libtimedate-perl_1.1600-9_all.deb
[*]linux-headers-2.6.24-16-generic_2.6.24-16.30_i386.deb
[*]linux-libc-dev_2.6.24-18.32_i386.deb
[*]patch_2.5.9-4_i386.deb
[/LIST]

And then did sudo dpkg -i *.deb on a terminal :)

Just thought it might be useful for someone! :)
Thanks a lot for this great tutorial, btw! :D

---

### Post by buccaneere on 2008-10-19
> **jlandaw said:**
> I'm making this Thread to Help others with the problem I had installing my BCM94311MCG wlan mini-PCI.  

I have a HP dv9000 (dv9428nr) Running Ubuntu 7.10(32 bit)

Note: If the output for &#8220;lspci | grep Broadcom&#8221; is :

&#8220;03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)&#8221;


How 'bout that!

I have a HPDV9429nr also. BUT, the return is:

chuckbhp@chuckbhp-laptop:~$ lspci | grep Broadcom
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)

The reference to **mini-PCI** is missing. Does this matter?

---

### Post by buccaneere on 2008-10-19
Step #1:

Link does not work.

Is there another source?

ED.:
Got it...

---

### Post by ThaRabbit on 2008-10-21
Quick note:
2.6.24-21-generic is now available for update via the 8.04 update manager. It includes the "wl"  driver which is working flawlessly for me.

As this topic mentions:
[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

The new WL driver by broadcom is included with the new update. It worked for me and I've hence uninstalled ndiswrapper and retraced all steps done in this topic.

[u][b]This uninstall procedure will undo what this first post in this topic does. Follow at your own risk.

Please review the steps I make and notify me if you find a problem[/b][/u]

I removed ndiswrapper by doing the following:

1. Unload the module:
```
sudo modprobe -r ndiswrapper
```

2. Remove the driver:
```
sudo ndiswrapper -r bcmwl5
```

3. Remove the loading of ndiswrapper in /etc/modules
```
sudo gedit /etc/modules
```

Simply remove the "ndiswrapper" line in this file

4. Remove the fix (do not take this step if you have a Broadcom wired interface, please check the post below this one)
```
sudo gedit /etc/init.d/rc.local
```

Simply remove the block at the bottom of this file looking like this:
```
#hardy ssb bug-fix 
rmmod b43 
rmmod b44 
rmmod ssb 
rmmod ndiswrapper 
modprobe ndiswrapper 
modprobe ssb 
modprobe b44
```

***optional extra steps* - this completely removes the ndiswrapper source and windows driver**

5. Uninstall Ndiswrapper
```

sudo cd ~/bcm43xx/ndiswrapper/ndiswrapper-1.53/
sudo make uninstall
```

6. Remove the folder holding the wireless driver and the ndiswrapper source
```
sudo rm ~\bcm43xx\ -R
```

---

### Post by Ayuthia on 2008-10-21
> **ThaRabbit said:**
> 
Simply remove the block at the bottom of this file looking like this:
```
#hardy ssb bug-fix 
nrmmod b43 
nrmmod b44 
nrmmod ssb 
nrmmod ndiswrapper 
nmodprobe ndiswrapper 
nmodprobe ssb 
nmodprobe b44
```

Instead of doing this, you might just want to comment out the lines instead:
```
#hardy ssb bug-fix 
#rmmod b43 
#rmmod b44 
#rmmod ssb 
#rmmod ndiswrapper 
#modprobe ndiswrapper 
#modprobe ssb 
#modprobe b44
```

This will prevent the commands from executing instead of the script trying to run invalid code (not for sure if it will show up as an error anywhere--not harmful though).  HOWEVER, if you do have a Broadcom ethernet (wired) card with a model number 44XX, you will still need some kind of ssb fix.  You will need to replace ndiswrapper with wl.  To see if you have this card, just type lshw -C network in the Terminal and see if the b44 driver is listed for your ethernet card.

---

### Post by ThaRabbit on 2008-10-21
> **Ayuthia said:**
> Instead of doing this, you might just want to comment out the lines instead:
```
#hardy ssb bug-fix 
#rmmod b43 
#rmmod b44 
#rmmod ssb 
#rmmod ndiswrapper 
#modprobe ndiswrapper 
#modprobe ssb 
#modprobe b44
```

This will prevent the commands from executing instead of the script trying to run invalid code (not for sure if it will show up as an error anywhere--not harmful though).  HOWEVER, if you do have a Broadcom ethernet (wired) card with a model number 44XX, you will still need some kind of ssb fix.  You will need to replace ndiswrapper with wl.  To see if you have this card, just type lshw -C network in the Terminal and see if the b44 driver is listed for your ethernet card.

Good call, thanks :)

---

### Post by chicopixel on 2008-11-02
First, Thank you very much, it works perfect for me (I tried for 5 days with other methods)


But I have a problem... I installed ubuntu from my XP OS and now, from windows I detect all the nets but trying to connect my card won't obtain an IP... Since  I used this in linux!!!!

And I need Windows to work  :(


This tip make changes to the bios??  I've got a compaq presario R3000 with Xp and Hardy Heron... and I a newbie with Linux


I think that changes made a conflict with windows drivers?

Please help and sorry for my bad english!!!

---

### Post by Ayuthia on 2008-11-02
> **chicopixel said:**
> First, Thank you very much, it works perfect for me (I tried for 5 days with other methods)


But I have a problem... I installed ubuntu from my XP OS and now, from windows I detect all the nets but trying to connect my card won't obtain an IP... Since  I used this in linux!!!!

And I need Windows to work  :(


This tip make changes to the bios??  I've got a compaq presario R3000 with Xp and Hardy Heron... and I a newbie with Linux


I think that changes made a conflict with windows drivers?

Please help and sorry for my bad english!!!

To my understanding, Linux should not change how your wireless works in Windows.  You might try and see if there is a troubleshooting button for your wireless in XP.  It might fix the problem for you.

---

### Post by chicopixel on 2008-11-02
> **Ayuthia said:**
> To my understanding, Linux should not change how your wireless works in Windows.  You might try and see if there is a troubleshooting button for your wireless in XP.  It might fix the problem for you.


Thank you Ayuthia, I tried and tried and finally I follow your advice and called to the internet provider... and fix the problem

This problem happened Simultaneously I fixed ubuntu connection...what a coincidence!;:lolflag:

Total 5 days spended, but,  with this tutorial resolve the problem in 5 minutes... and I've got a life to enjoy Linux

Thank You very Much!!!!

Óscar

---

### Post by alaya.zied on 2008-11-04
I have the same Broadcom card in HP Pavilion dv6420em, it works for me with Ubuntu 8.04

Note that with Ubuntu 8.10 I tried Broadcom STA wireless driver and know it works fine and much better then before.

---

### Post by alaya.zied on 2008-11-04
I have the same Broadcom card in HP Pavilion dv6420em, it works for me with Ubuntu 8.04

Note that with Ubuntu 8.10 I tried Broadcom STA wireless driver and know it works fine and much better then before.

---

### Post by fabrile on 2008-11-07
I have a Compaq C705LA (C700) with a broadcom Wireless Card.
I started with ubunto 8.04 Hardy, and i was great, but i havn't wireless capabilities.  I tried everithing in the Foros, but nothing.
I was just about to return to windows and...
updated to Ubuntu 8.10 and voila!  [COLOR="Red"]problem solved[/COLOR]

Best regards...

---

### Post by E-Cecilia on 2008-12-01
Ugh, everything goes well till step 7. This is what happens in my terminal
[I]estela@estela-laptop:~/bcm43xx/ndiswrapper/ndiswrapper-1.53$ make distclean
make -C driver clean
make[1]: Entering directory `/home/estela/bcm43xx/ndiswrapper/ndiswrapper-1.53/driver'
Makefile:34: *** Cannot find kernel version in /usr/src/linux-2.6.22-16-generic, is it configured?.  Stop.
make[1]: Leaving directory `/home/estela/bcm43xx/ndiswrapper/ndiswrapper-1.53/driver'
make: *** [clean] Error 2
estela@estela-laptop:~/bcm43xx/ndiswrapper/ndiswrapper-1.53$ 
[/I]

---

### Post by Ayuthia on 2008-12-01
> **E-Cecilia said:**
> Ugh, everything goes well till step 7. This is what happens in my terminal
[I]estela@estela-laptop:~/bcm43xx/ndiswrapper/ndiswrapper-1.53$ make distclean
make -C driver clean
make[1]: Entering directory `/home/estela/bcm43xx/ndiswrapper/ndiswrapper-1.53/driver'
Makefile:34: *** Cannot find kernel version in /usr/src/linux-2.6.22-16-generic, is it configured?.  Stop.
make[1]: Leaving directory `/home/estela/bcm43xx/ndiswrapper/ndiswrapper-1.53/driver'
make: *** [clean] Error 2
estela@estela-laptop:~/bcm43xx/ndiswrapper/ndiswrapper-1.53$ 
[/I]

It looks like linux-headers is not installed.  Please check in Synaptic to see if it is installed or post the results of:
```
aptitude search linux-headers
```

---

### Post by hacker0wnz on 2008-12-06
I neeed Help


I got more option after i did this step

when i right click on the wireless icon thingy, i get one more option which says "Enable Wireless"

but it wont detect any wifi/router :(


help please 

i have hp pavillion dv5z1000
Atheros Driver

---

### Post by hacker0wnz on 2008-12-06
Omfg your da best!!!!!!!!!!!!!!


Thanks a bunch !!!!!!!


It works on hp pavillion dv5z-1000 

just to let everyone know :)

thank you so much :)

---

### Post by cybo1470 on 2009-01-21
I'm having trouble deciphering these messages. I'm running 8.10, and have a Presario C751 NR. Can somebody explain this to me really simply?


[http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif](http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif) /Jack

---

### Post by cybo1470 on 2009-01-21
When I put this in the terminal:
00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f0] (rev a2)
	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Capabilities: <access denied>

00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0

00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Capabilities: <access denied>

00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: b4000000-b5ffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000d01fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: b6000000-b7ffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:05.0 VGA compatible controller [0300]: nVidia Corporation C51 [Geforce 6150 Go] [10de:0244] (rev a2) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 19
	Region 0: Memory at b2000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Region 3: Memory at b1000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at 50000000 [disabled] [size=128K]
	Capabilities: <access denied>

00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Capabilities: <access denied>

00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Region 0: I/O ports at 1d00 [size=128]

00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin A routed to IRQ 10
	Region 4: I/O ports at 3040 [size=64]
	Region 5: I/O ports at 3000 [size=64]
	Capabilities: <access denied>

00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)
	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin B routed to IRQ 10
	Region 0: Memory at b0040000 (32-bit, non-prefetchable) [size=256K]

00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3) (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at b0004000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin B routed to IRQ 16
	Region 0: Memory at b0005000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1) (prog-if 8a [Master SecP PriP])
	Subsystem: Unknown device [f03c:30b7]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	Region 4: I/O ports at 3080 [size=16]
	Capabilities: <access denied>

00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1) (prog-if 85 [Master SecO PriO])
	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin A routed to IRQ 17
	Region 0: I/O ports at 30c0 [size=8]
	Region 1: I/O ports at 30b4 [size=4]
	Region 2: I/O ports at 30b8 [size=8]
	Region 3: I/O ports at 30b0 [size=4]
	Region 4: I/O ports at 3090 [size=16]
	Region 5: Memory at b0006000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2) (prog-if 01 [Subtractive decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=64
	Memory behind bridge: b8000000-b80fffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (500ns min, 1250ns max)
	Interrupt: pin B routed to IRQ 20
	Region 0: Memory at b0000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (250ns min, 5000ns max)
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at b0008000 (32-bit, non-prefetchable) [size=4K]
	Region 1: I/O ports at 30e0 [size=8]
	Capabilities: <access denied>

00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Capabilities: <access denied>

00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Capabilities: <access denied>

03:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)
	Subsystem: Hewlett-Packard Company Unknown device [103c:1363]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 21
	Region 0: Memory at b6000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

07:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64 (500ns min, 1000ns max)
	Interrupt: pin A routed to IRQ 5
	Region 0: Memory at b8000000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

07:05.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64
	Interrupt: pin B routed to IRQ 7
	Region 0: Memory at b8000800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

07:05.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 0a)
	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin B routed to IRQ 11
	Region 0: Memory at b8000c00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

07:05.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 05)
	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin B routed to IRQ 11
	Region 0: Memory at b8001000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

07:05.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff) (prog-if ff)
	!!! Unknown header type 7f

I got this: 
	Latency: 0 (750ns min, 250ns max)
	Injack@jack-laptop:~$ Subsystem: Hewlett-Packard Company Presario V6133Cb7]103c:30 
terrupt: pin A routed to IRQ 17
	Region 0: I/O ports at 30c0 [sizbash: Subsystem:: command not found
jack@jack-laptop:~$ Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- e=8]
	Region 1: I/O ports at 30b4 [size=4]
	Region 2: I/O portbash: Control:: command not found
jack@jack-laptop:~$ Status: Cap+ 66MHz+ UDF- Fast
s at 30b8 [size=8]
	Region 3: Ibash: Status:: command not found
jack@jack-laptop:~$ 
jack@jack-laptop:~$ Interrupt: pin A routed to IRQ 19
/O ports at 30b0 [size=4]
	Region 4:bash: Interrupt:: command not found
jack@jack-laptop:~$ Region 0: Memory at b2000000 (32-bit, non-prefetchable) [size=16M]
bash: syntax error near unexpected token `('
 I/O ports at 3090 [size=16]
	Region 5: Memory at b0006000 (32-bit, jack@jack-laptop:~$ Region 1: Memo6M]at c0000000 (64-bit, prefetchable) [size=25 
bash: syntax error near unexpected token `('
non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:10jack@jack-laptop:~$ Region 3: Memory at b1000000 (64-bit, non-prefetchable)e=16M]
bash: syntax error near unexpected token `('
.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f
jack@jack-laptop:~$ [virtual] Expansion ROM at 50000000 [disabled] [size=128K]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop
bash: [virtual]: command not found
jack@jack-laptop:~$ Capabilities: <access denied>
bash: syntax error near unexpected token `newline'
	Status: Cap+ 66MHz+ UDF- Fast
jack@jack-laptop:~$ 
jack@jack-laptop:~$ 00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
bash: syntax error near unexpected token `('
	Latency: 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=64
	Memory bejack@jack-laptop:~$ Subsystem: Hewlett-Packard Company Presariob7]133CL [103c:30 
hind bridge: b8000000-b80fffff
	Secondary status: 66MHz- FastB2B+bash: Subsystem:: command not found
jack@jack-laptop:~$ Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
 ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISbash: Control:: command not found
jack@jack-laptop:~$ Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
bash: MAbort-: No such file or directory
A+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:10.1 Audio device [0403]: nVjack@jack-laptop:~$ Latency: 0
idia Corpora
bash: Latency:: command not found
jack@jack-laptop:~$ Capabilities
	Subsystem: H
bash: Capabilities: command not found
jack@jack-laptop:~$ 
jack@jack-laptop:~$ 00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR-
bash: syntax error near unexpected token `('
jack@jack-laptop:~$ Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- 
bash: Subsystem:: command not found
jack@jack-laptop:~$ Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Latency: 0 (500ns min, 1250ns max)
	Interrupt: pin B routed to IRQ 20
	Region 0: Memory at bbash: Control:: command not found
jack@jack-laptop:~$ Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
0000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:14.0 Bridge [06bash: MAbort-: No such file or directory
jack@jack-laptop:~$ Laten
80]: nV
bash: Laten: command not found
jack@jack-laptop:~$ Region 0: I/O ports at 1d00 [size=128]
	Subsystem: Hewlett-Packard Company Pre
bash: Region: command not found
jack@jack-laptop:~$ 
jack@jack-laptop:~$ 00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepp
bash: syntax error near unexpected token `('
jack@jack-laptop:~$ Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- 
bash: Subsystem:: command not found
jack@jack-laptop:~$ Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Latency: 0 (250ns min, 5000ns max)
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at bbash: Control:: command not found
jack@jack-laptop:~$ Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >
0008000 (32-bit, non-prefetchable) [size=4K]
	Region 1: I/O ports at 30e0 [size=8]
	bash: syntax error near unexpected token `newline'
jack@jack-laptop:~$ Interrupt: pin A routed to IRQ 10
Capabilities: <access denied>

00:1bash: Interrupt:: command not found
jack@jack-laptop:~$ Region 4: I/O ports at 3040 [size=64]
8.0 Host bridge [0600]: Advanced Micro 
bash: Region: command not found
jack@jack-laptop:~$ Region 5: I/O ports at 3000 [size=64]
	Control: I/O- Mem- BusMaster- SpecCyc
bash: Region: command not found
jack@jack-laptop:~$ Capabilities: <access denied>
bash: syntax error near unexpected token `newline'
	Status: Cap+ 66MHz- UDF- Fast
jack@jack-laptop:~$ 
jack@jack-laptop:~$ 00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)
bash: syntax error near unexpected token `('
	Capabilities: <access denied>

00:18.1 Host bridge [0600]: Advanced Micro Devijack@jack-laptop:~$ Subsystem: Heb7]tt-Packard Company Presario V6133CL [103c:30 
ces [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
	Control:bash: Subsystem:: command not found
jack@jack-laptop:~$ Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop-  I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- St
bash: Control:: command not found
jack@jack-laptop:~$ Status: Cap- 66MHz+ UDF- Fast
	Status: Cap- 66MHz- UDF- Fast
bash: Status:: command not found
jack@jack-laptop:~$ Latency: 0 (750ns min, 250ns max)

00:18.2 Host bridge [060bash: syntax error near unexpected token `('0
]: Advanjack@jack-laptop:~$ Interrupt: pin B routed to IRQ 10
ced Micro Devices [AMD] K8 [Athlon6
bash: Interrupt:: command not found
jack@jack-laptop:~$ Region 0: Memory at b0040000 (32-bit, non-prefetchable) [size=256K]
bash: syntax error near unexpected token `('
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr-
jack@jack-laptop:~$ 

jack@jack-laptop:~$ 00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3) (prog-if 10 [OHCI]

00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:11bash: syntax error near unexpected token `('
jack@jack-laptop:~$ Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
03]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- bash: Subsystem:: command not found
jack@jack-laptop:~$ Control: I/O+ Mem+ BusMaster+ 
ParErr- Stepping- SERR- FastB2B-
bash: Control:: command not found
jack@jack-laptop:~$ Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <
bash: syntax error near unexpected token `newline'
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <
jack@jack-laptop:~$ Latency: 0 (750ns min, 250ns max)
	Capabilities: <access denied>

03bash: syntax error near unexpected token `('
jack@jack-laptop:~$ Interrupt: pin A routed to IRQ 16
:00.0 Network controller [0280]: Br
bash: Interrupt:: command not found
jack@jack-laptop:~$ Region 0: Memory at b0004000 (32-bit, non-prefetchable) [size=4K]
bash: syntax error near unexpected token `('
	Subsystem: Hewlett-Packard Company Unknown device [103c:1363]
	Cojack@jack-laptop:~$ Capabilities: <access denied>
bash: syntax error near unexpected token `newline'
ntrol: I/O+ Mem+ BusMaster+ Spe
jack@jack-laptop:~$ 
jack@jack-laptop:~$ 00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3) (prog-if 20 [EHCI])
bash: syntax error near unexpected token `('
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cacjack@jack-laptop:~$ Subsystem: Hewlett-Packard Company Prb7]rio V6133CL [103c:30 
he Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 21
	Regionbash: Subsystem:: command not found
jack@jack-laptop:~$ Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
 0: Memory at b6000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

0bash: Control:: command not found
jack@jack-laptop:~$ Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
7:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (prog-i
bash: MAbort-: No such file or directory
jack@jack-laptop:~$ Latency: 0 (750ns min, 250ns max)
	Subsystem: Hewlett-Packard Companbash: syntax error near unexpected token `('

jack@jack-laptop:~$ Interrupt: pin B routed to IRQ 16
	Control: I/O- Mem+ BusMaster+ Spe
bash: Interrupt:: command not found
jack@jack-laptop:~$ Region 0: Memory at b0005000 (32-bit, non-prefetchable) [size=256]
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <
bash: syntax error near unexpected token `('
jack@jack-laptop:~$ Capabilities: <access denied>
	Latency: 64 (500ns min, 1000n
bash: syntax error near unexpected token `newline'
jack@jack-laptop:~$ 
jack@jack-laptop:~$ 00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1) (prog-if 8a [Master SecP PriP])
bash: syntax error near unexpected token `('
	Interrupt: pin A routed to IRQ 5
	Region 0: Memory at b8000000 (32-bit, non-prefetchable) [size=2K]
	Capabilitijack@jack-laptop:~$ Subsystem: Unknown device [f03c:30b7]
es: <access denied>

07:05.1 SD Host cobash: Subsystem:: command not found
jack@jack-laptop:~$ Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SER
ntroller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] 
bash: Control:: command not found
jack@jack-laptop:~$ 

jack@jack-laptop:~$ Latency: 0 (750ns min, 250ns max)
	Control: I/O- Mem+ BusMaster+ Spe
bash: syntax error near unexpected token `('
jack@jack-laptop:~$ Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >S
bash: syntax error near unexpected token `('
jack@jack-laptop:~$ Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	Latency: 64
	Interrupt: pin B routed to IRQ 7
	Region 0: Memory at b8000800 (32-bit, bash: syntax error near unexpected token `('
jack@jack-laptop:~$ Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
bash: syntax error near unexpected token `('
non-prefetchable) [size=256]
	Capabilities: <access denied>

07:05.2 System peripheral jack@jack-laptop:~$ Region 3: [virtual] Memory at 00000370 (type 3, no
[0880]: Ricoh Co Ltd R5C843 MMC Host Controller [118
bash: syntax error near unexpected token `('
jack@jack-laptop:~$ Region 4: I/O ports at 3080 [size=16]
	Subsystem: Hewlett-Packard Company Pr
bash: Region: command not found
jack@jack-laptop:~$ Capabilities: <access denied>
bash: syntax error near unexpected token `newline'
	Control: I/O- Mem+ BusMaster-
jack@jack-laptop:~$ 

jack@jack-laptop:~$ 00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1) (prog-if 85 [Master SecO PriO
	Interrupt: pin B routed to IRQ 11
	Region 0: Memory at b8000c00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access dbash: syntax error near unexpected token `('
jack@jack-laptop:~$ Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b
enied>

07:05.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Mbash: Subsystem:: command not found
jack@jack-laptop:~$ Control: I/O+ Mem+ BusMaster+
emory Stick Bus Host Adapter [1
bash: Control:: command not found
jack@jack-laptop:~$ Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
bash: MAbort-: No such file or directory
	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Control: I/O- Mem+ BusMaster-jack@jack-laptop:~$ Latency: 0 (750ns min, 250ns max)
 SpecCycle- MemWINV- VGASnoop- ParEbash: syntax error near unexpected token `('

jack@jack-laptop:~$ Interrupt: pin A routed to IRQ 17
	Status: Cap+ 66MHz- UDF- FastB2B-
bash: Interrupt:: command not found
jack@jack-laptop:~$ Region 0: I/O ports at 30c0 [size=8]
	Interrupt: pin B routed to IRQ 11
	Rbash: Region: command not found
jack@jack-laptop:~$ Region 1: I/O ports at 30b4 [size=4]
egion 0: Memory at b8001000 (32-bit, n
bash: Region: command not found
jack@jack-laptop:~$ Region 2: I/O ports at 30b8 [size=8]
	Capabilities: <access denied>

07:05bash: Region: command not found
jack@jack-laptop:~$ Region 3: I/O ports at 30b0 [size=4]
.4 System peripheral [0880]: Ricoh Co 
bash: Region: command not found
jack@jack-laptop:~$ Region 4: I/O ports at 3090 [size=16]
	!!! Unknown header type 7fbash: Region: command not found
jack@jack-laptop:~$ Region 5: Memory at b0006000 (32-bit, non-prefetchable) [size=4K]
bash: syntax error near unexpected token `('
jack@jack-laptop:~$ Capabilities: <access denied>
bash: syntax error near unexpected token `newline'
jack@jack-laptop:~$ 
jack@jack-laptop:~$ 00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f
bash: 00:10.0: command not found
jack@jack-laptop:~$ Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop
bash: Control:: command not found
jack@jack-laptop:~$ Status: Cap+ 66MHz+ UDF- Fast
bash: Status:: command not found
jack@jack-laptop:~$ Latency: 0
bash: Latency:: command not found
jack@jack-laptop:~$ Bus: primary=00, secondary=07, subordinate=07, sec-latency=64
bash: Bus:: command not found
jack@jack-laptop:~$ Memory behind bridge: b8000000-b80fffff
bash: Memory: command not found
jack@jack-laptop:~$ Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- <SERR- <PERR-
bash: MAbort-: No such file or directory
jack@jack-laptop:~$ BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
bash: BridgeCtl:: command not found
jack@jack-laptop:~$ Capabilities: <access denied>
bash: syntax error near unexpected token `newline'
jack@jack-laptop:~$ 
jack@jack-laptop:~$ 00:10.1 Audio device [0403]: nVidia Corpora
bash: 00:10.1: command not found
jack@jack-laptop:~$ Subsystem: H
bash: Subsystem:: command not found
jack@jack-laptop:~$ Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR-
bash: Control:: command not found
jack@jack-laptop:~$ Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- 
bash: Status:: command not found
jack@jack-laptop:~$ Latency: 0 (500ns min, 1250ns max)
bash: syntax error near unexpected token `('
jack@jack-laptop:~$ Interrupt: pin B routed to IRQ 20
bash: Interrupt:: command not found
jack@jack-laptop:~$ Region 0: Memory at b0000000 (32-bit, non-prefetchable) [size=16K]
bash: syntax error near unexpected token `('
jack@jack-laptop:~$ Capabilities: <access denied>
bash: syntax error near unexpected token `newline'
jack@jack-laptop:~$ 
jack@jack-laptop:~$ 00:14.0 Bridge [0680]: nV
bash: 00:14.0: command not found
jack@jack-laptop:~$ Subsystem: Hewlett-Packard Company Pre
bash: Subsystem:: command not found
jack@jack-laptop:~$ Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepp
bash: Control:: command not found
jack@jack-laptop:~$ Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- 
bash: Status:: command not found

It keeps saying "command not found" and "syntax error near unexpected token". Help!!!

---

### Post by Ayuthia on 2009-01-22
> **cybo1470 said:**
> When I put this in the terminal:
00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f0] (rev a2)
	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Capabilities: <access denied>

<snip>

It keeps saying "command not found" and "syntax error near unexpected token". Help!!!

It looks like you were copying the lspci -vv results into the Terminal.  They are not a set of commands, but information about your pci cards.

What are you attempting to do?

---

### Post by mercurous on 2009-03-15
Hello, i followed the steps posted. I am using DV2415nr. It could detect the wireless router..but it wont connect to it. I says no IPv6 routers present. Should it be ipv4? I am new to ubuntu and I need help to fix my wireless adapter.

5742.764855] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 5748.006274] wlan1: no IPv6 routers present 

thanks,
Mark

---

### Post by superjew94 on 2009-03-22
Hey thanks it works great on my hp dv4225nr now i don't have to use a useless pcmcia card thanks again

---

### Post by rebel9690 on 2009-06-20
I am a noob because i dont know what this terminal thing is im trying to fix my wireless but im not understanding these steps maybe its because im american lol i dont know.Please help me with this man.

---

### Post by Ayuthia on 2009-06-20
> **rebel9690 said:**
> I am a noob because i dont know what this terminal thing is im trying to fix my wireless but im not understanding these steps maybe its because im american lol i dont know.Please help me with this man.

You might want to first try out System->Administration->Hardware Drivers and activating either the b43 version or the Broadcom STA version.  Both of them seem to work pretty well with the 4311 card now.

If it doesn't work, let us know and we can help you through whichever option you want.

---

### Post by hfranco75 on 2009-07-08
Yeah, it's working for Jaunty in a Presario F700 toaster. Good job, thanks. Let me translate this to Spanish in my BLOG, please.

---

### Post by Sloppyunderfoot on 2009-11-06
Thank you so much for this "how to information".  I never could have gotten the wireless going in my daughter's Lenovo 3000 c200 running Hardy Heron had it not been for it.

---

### Post by derekshaw on 2010-09-23
see this ubuntu community wiki page:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by thokchom on 2010-11-04
:confused:Hi, I am new on Linux. I have installed ubuntu 10.10 (32 bits compaq presario c700tu) and wireless connection is disabled on linux but on window xp, it is working (dual boot), and I faced the same problem as discussed on this topic. 

By doing step 9 & 10, i got errors, and details are given here:

james@james-Presario:~/bcm43xx/ndiswrapper/ndiswrapper-1.53$ make distclean
make -C driver clean
make[1]: Entering directory `/home/james/bcm43xx/ndiswrapper/ndiswrapper-1.53/driver'
Makefile:51: *** No .config found in /lib/modules/build, please set KBUILD to configured kernel.  Stop.
make[1]: Leaving directory `/home/james/bcm43xx/ndiswrapper/ndiswrapper-1.53/driver'
make: *** [clean] Error 2
james@james-Presario:~/bcm43xx/ndiswrapper/ndiswrapper-1.53$ make
make -C driver
make[1]: Entering directory `/home/james/bcm43xx/ndiswrapper/ndiswrapper-1.53/driver'
Makefile:51: *** No .config found in /lib/modules/build, please set KBUILD to configured kernel.  Stop.
make[1]: Leaving directory `/home/james/bcm43xx/ndiswrapper/ndiswrapper-1.53/driver'
make: *** [all] Error 2
james@james-Presario:~/bcm43xx/ndiswrapper/ndiswrapper-1.53$ sudo make install
make -C driver install
make[1]: Entering directory `/home/james/bcm43xx/ndiswrapper/ndiswrapper-1.53/driver'
Makefile:51: *** No .config found in /lib/modules/build, please set KBUILD to configured kernel.  Stop.
make[1]: Leaving directory `/home/james/bcm43xx/ndiswrapper/ndiswrapper-1.53/driver'
make: *** [install] Error 2
james@james-Presario:~/bcm43xx/ndiswrapper/ndiswrapper-1.53$ 
james@james-Presario:~/bcm43xx/ndiswrapper/ndiswrapper-1.53$ cd /home/james/WLANBroadcom/
james@james-Presario:~/WLANBroadcom$ sudo ndiswrapper -i bcmwl5.inf
sudo: ndiswrapper: command not found
james@james-Presario:~/WLANBroadcom$ ndiswrapper -l
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
james@james-Presario:~/WLANBroadcom$ 

I also tried to install 'ndiswrapper-common' but same error is there. Please help me. FYI, details for lspci, ifconfig, iwconfig[FONT=monospace] are given.

[/FONT]lspci

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:38:39:bf:9a  
          inet addr:123.238.27.231  Bcast:123.238.27.255  Mask:255.255.254.0
          inet6 addr: fe80::21b:38ff:fe39:bf9a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1400  Metric:1
          RX packets:16132 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5425 errors:0 dropped:0 overruns:3 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4722645 (4.7 MB)  TX bytes:933633 (933.6 KB)
          Interrupt:16 Base address:0x1000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

AnyOne...PLZ help me out ???

---

### Post by thokchom on 2010-11-11
I got the solution from other forums and wanna to share it 

My problem was

Not working Wifi in Compaq presario: 

Wireless driver (Sata) is installed while using Ubuntu 9.10 or 10.10 (32 bit) but Wifi button is not on (wireless network is disabled). But while using window xp, wifi button is able to on or off. It seems Compaq has problem with linux.
Laptop Model: Compaq presario c702tu.
[B]
Try the following procedure:

Check the wifi driver (sata) is activated - [/B]Go to system>Administration>aditional drivers. If activated, proceed the below. If not, click on activate button. Once done follow the below steps
 0) Install wicd using the following Terminal command:
 sudo apt-get install wicd
 1) Put the wireless hardware switch in the OFF/DISABLED position
2) Shut down the pc so that it is completely turned off.
3) Cold boot the PC and WAIT until you get to the Ubuntu desktop and can see the wicd icon (wicd is a replacement for NetworkManager)
4) Put the wireless hardware switch in the ON/ENABLED position once you can see the wicd icon
5) run the following Terminal commands:


 **sudo rfkill unblock all**
 **rfkill unblock hp-wifi**

 6) Then try connecting to the wireless access point using wicd


In my laptop, it works well. I forgot the name of forum where I collect the information & feel sorry for that.

---

### Post by sovelliss06 on 2011-08-08
Okay, so I can't get the first driver package that I need. When I open the link it says "invalid or deleted file". Anyone know of a mirror or even which file I need so I can look for it? Many thanks.

---

### Post by fovoc on 2013-01-09
> **sovelliss06 said:**
> Okay, so I can't get the first driver package that I need. When I open the link it says "invalid or deleted file". Anyone know of a mirror or even which file I need so I can look for it? Many thanks.

Another one added! Please some feedback... :-?

---

