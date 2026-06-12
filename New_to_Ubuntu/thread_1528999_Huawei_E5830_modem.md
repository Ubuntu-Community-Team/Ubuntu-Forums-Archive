---
title: "Huawei E5830 modem"
date: 2010-07-11
forum: New to Ubuntu
---

### Post by nmlferreira on 2010-07-11
Hi,
I have a Huawei E5830 modem who works perfectly in a Windows environment. I've installed Ubunto several times and I never was able to make the modem work. Aldough it detects the equipment, it doesn't launch the auto-run to proceed with the installation.
I even tried to run the executable files individually, but it doesn't work.
Note that the modem is connected via USB, because I have no wireless in this desktop.
Is anyone aware of any incompatibility issues?
Thanks,
Nuno

---

### Post by spiky001 on 2010-07-11
have you set it up in network manager

---

### Post by mike555 on 2010-07-11
you might need to install Gnome-ppp dialer ..

---

### Post by lhb1142 on 2010-07-11
> **nmlferreira said:**
> Hi,
I have a Huawei E5830 modem who works perfectly in a Windows environment. I've installed Ubunto several times and I never was able to make the modem work. Aldough it detects the equipment, it doesn't launch the auto-run to proceed with the installation.
I even tried to run the executable files individually, but it doesn't work.
Note that the modem is connected via USB, because I have no wireless in this desktop.
Is anyone aware of any incompatibility issues?
Thanks,
Nuno

Dear Sir,

Assuming your modem is Linux-capable (make certain of this), here is how to set it up and use it in Ubuntu 10.04 'Lucid Lynx':

Install Gnome PPP (available in Synaptic Package Manager)

Access System > Administration > Users and Groups

Access Advanced Settings (enter password)

Open User Privileges Tab

Make sure EVERYTHING (especially &#8220;Connect to internet with a modem&#8221; plus &#8220;Use modems&#8221;) is checked

Plug in your external (USB) modem, open Gnome PPP, click on Setup, click on Detect (Gnome PPP will then detect this modem if it Linux-compatible), close the setup box, and then enter your connection (login, password, local telephone number of ISP) information

Connect

When connection is established, open browser

To exit, close browser and Disconnect

I hope this helps you.

Lawrence

P.S. I am assuming you are trying to connect to the internet via a dial-up connection. If I am incorrect, I hope that someone else here, who possibly has experience with this particular modem, will be of more help.

---

### Post by nmlferreira on 2010-07-12
I did... or at least tried.

Maybe I'm just not using the correct definitions.
This is how I did it:
Under "Network Connections" I select "Mobile Broadband".
I fill in the country = Britain (UK)
the provider = 3
and the plan = internet
I then chose "Connect automatically"
I'm given a number = *99#
I'm not given a "User Name", a "Password".
The APN is defined autumatically = 3Internet
And I'm not given a "Network" or a "Pin".
Where do I fill in the SSID given by the provider? and the WIFI Key?

---

### Post by gandaran on 2010-07-12
> **nmlferreira said:**
> I did... or at least tried.

Maybe I'm just not using the correct definitions.
This is how I did it:
Under "Network Connections" I select "Mobile Broadband".
I fill in the country = Britain (UK)
the provider = 3
and the plan = internet
I then chose "Connect automatically"
I'm given a number = *99#
I'm not given a "User Name", a "Password".
The APN is defined autumatically = 3Internet
And I'm not given a "Network" or a "Pin".
Where do I fill in the SSID given by the provider? and the WIFI Key?
the APN (3internet) could be wrong and is the most important factor along with the authentication method, probably you only need to know these details, the rest don't fill in anything, do you really have to fill in the SSID?
if you have windows with the mobile setup you can check the properties windows for the details (or call your internet provider), if it uses dynamic APN then just leave APN field blank in Ubuntu, if it requires static APN then fill in the exact APN which I doubt is 3internet but then I could be wrong, and check which authentication method you have to enable.

edit:
you may need to reboot for the setup to start working.

---

### Post by spiky001 on 2010-07-12
hi I have just found something they say to eject the usb device then it shows up in network man dont remove just right click eject

[http://ubuntuforums.org/showthread.php?t=1417992](http://ubuntuforums.org/showthread.php?t=1417992) #2

worth a try, I didn't fill any ssid or wifi in. i,m with 3 as well just filled the same as you

---

### Post by mike555 on 2010-07-12
I don't think you need to use network manager , just use Gnome-ppp ......... at least that's what I did to get Verison wireless broadband . this is what I did -- of course your username and password will be different ;

To use the modem, do the following:

Step 1. Plug the modem in.
Step 2. Launch gnome-ppp as administrator (e.g., press Alt-F2 and type "gksu gnome-ppp"), and configure the following settings:

    * Modem Tab
          o Device: /dev/ttyACM0 (in my case, the auto-detect button correctly identified the device)
          o Type: USB Modem (do not leave as analog modem!)
          o Speed: 460800
          o Phone Line: Tone
          o Volume: Off

    * Options Tab
          o Minimize: checked
          o Dock in Notification Area: checked

Click Close. Fill in the fields in the main Gnome PPP window:

    * Username: [email]1234567890@vzw3g.com[/email] (use your number)
    * Password: vzw
    * Phone Number: #777

Step 3. Click Connect. That should be it.


To disconnect, click on the gnome-ppp dock notification icon.

These settings will be saved for the next time you need to connect.

 -- be sure you have rights to the groups "connect to internet using a modem", " connect to wireless and ethernet networks" & "use modems" --- in users and groups > advanced settings > user privileges tab.--

---

### Post by nmlferreira on 2010-07-14
Mike,
This looks like dial-up parameters. I'm using mobile broadband.
The configuration process looks very simple (too simple for my taste). But the problem is defenetly the modem.
To answer Grandaran, I was looking in other forums and it looks like the APN = 3internet is correct. Maybe I should just call the guys and confirm! Unfortunately the technical guys from 3 are always putting me into trouble. And I'm almost sure they will send me back to their internet FAQs page, where it says this modem is for Windows and Mac only and that they are working on availability to other OS.
I'm also discussing this issue with pdc: [http://ubuntuforums.org/showthread.php?t=1436954](http://ubuntuforums.org/showthread.php?t=1436954)
Please join if you want to exchange some more ideas.
Thanks,
Nuno

---

### Post by philinux on 2010-07-14
See the General Help forum sticky thread.

Problem with Huawei and possibly other usb mobile broadband dongles. 

```
sudo apt-get install usb-modeswitch
```

---

### Post by mike555 on 2010-07-14
if by mobile broadband you mean 3g , try my suggestions , (it still needs to dial out to connect to cell tower ).

---

### Post by gandaran on 2010-07-14
Nuno
the reason I have doubts about the network managers's automatic APN fill in is because I struggled a full whole day to get my mobile pen working (Portuguese Kanguru mobile broadband), it wouldn't work with the default APN (internet), I did contact Kanguru and they sent me a deferent one which doesn't work too! 
I solved it checking the windows XP mobile pen setup, the APN was dynamic APN and authentication CHAP, well I had the correct details now but it wasn't the end of my problems, I was about to give up completely but for some reason I rebooted the computer was surprised internet was connected then, so you see this is not easy!  I think it's a shame there isn't one internet webpage with linux mobile broadband instructions and practically nobody shares their experience.
bye.

---

### Post by nmlferreira on 2010-07-15
Gandaran,
I've phoned the guys from 3 and they gave me two options for the APN: the first one being **three.co.uk **and if this doesn't work **3internet**.
I've been using the second one, because as I wrote before, I've seen in other forums that that is the one to use.
I'll try to play with this later.

I agree with you that someone should post general information to solve problems like this, however I understand that so many things can vary, that wouldn't be possible to cover everything.
If any experienced user is reading this, please consider Gandaran's comment above.
If we new what to look for and how to make some configurations, it would be great.
For example I learned that by using lsusb, I could find out if the system recognized the equipment and what its state was. This could be the first step.
As for the dmesg command, I'm still strugling to understand what it does.
If I can solve my issue, I'll try to put something together. But before that I need your assistance.
Cheers everyone.
Nuno

---

### Post by nmlferreira on 2010-07-15
> **mike555 said:**
> I don't think you need to use network manager , just use Gnome-ppp ......... at least that's what I did to get Verison wireless broadband . this is what I did -- of course your username and password will be different ;

To use the modem, do the following:

Step 1. Plug the modem in.
Step 2. Launch gnome-ppp as administrator (e.g., press Alt-F2 and type "gksu gnome-ppp"), and configure the following settings:

    * Modem Tab
          o Device: /dev/ttyACM0 (in my case, the auto-detect button correctly identified the device)
          o Type: USB Modem (do not leave as analog modem!)
          o Speed: 460800
          o Phone Line: Tone
          o Volume: Off

    * Options Tab
          o Minimize: checked
          o Dock in Notification Area: checked

Click Close. Fill in the fields in the main Gnome PPP window:

    * Username: [email]1234567890@vzw3g.com[/email] (use your number)
    * Password: vzw
    * Phone Number: #777

Step 3. Click Connect. That should be it.


To disconnect, click on the gnome-ppp dock notification icon.

These settings will be saved for the next time you need to connect.

 -- be sure you have rights to the groups "connect to internet using a modem", " connect to wireless and ethernet networks" & "use modems" --- in users and groups > advanced settings > user privileges tab.--

Hi Mike,

I was trying to follow your steps above, but had no success.
If I go to the software center and try to install Gnome PPP, it only gives me the possibility of "More Info". Then "Use This Source" and nothing happens.
If I use the gksu command, it asks me for the password, but nothing happens.
I also tried to install the Gnome-PPP package, but I ger an error: "Dependency is not satisfiable: wvdial"
Am I doing something wrong?

---

### Post by mike555 on 2010-07-15
If you can connect to some kind of internet ,then just go to Synaptic Package Manager and type in Gnome-ppp check the box next to it and install ..........  I'm not sure if the live cd has it on it or not , but you might try it if you don't have any way to get on Internet ..... just start Ubuntu , put in live cd then try installing gnome-ppp from it .

---

### Post by nmlferreira on 2010-07-20
I'm going to try a usb stick with wireless, to see if I can overcome this issue.
I'll be back if it doesn't work.
Thanks a lot for your support.

---

### Post by nmlferreira on 2010-07-26
Mike,

Got the Gnome-PPP to work and followed your steps. Unfortunately it didn't detect the modem.
Can you please follow this discussion on 

[http://ubuntuforums.org/showthread.php?t=1436954](http://ubuntuforums.org/showthread.php?t=1436954)

I've been discussing my difficulty to connect there as well.
Thanks

PS: How do I close this thread, since it's not solved?

---

### Post by jarviser on 2010-07-26
The guy from Portugal has it. The difference bewteen you and the other contributors is you are in UK and the automatic APN is set up for US providers.

As the earlier posters said, IF the modem is compatible with the kernel you need none of the extras advised earlier, you simply need to do what you did earlier using the correct UK APN for your supplier
This is how I did my UK Orange connection on Lucid out of the box...
1. Insert the SIM card in the device (With PIN number de-activated first)
2. Plug the device into the laptop. IGNORE the software on the dongle!
3. Right-click on the network icon in the System Tray
4. Select Edit Connections.
5. Click on the Mobile Broadband tab.
6. Click on Add.
7. Select the device from the drop-down and click Forward - it will appear there if the device has been recognised.
8. Select country (Britain UK in my case)
9. In the Select your provider, I selected** "I can't find my provider...." **and typed in "Orange USB" and hit Forward.
10. I typed "consumerbroadband" for domestic UK Orange service (yours may be different and if not Orange WILL be different. Google for it)
11. Confirmed next 2 pages. The dial number was correct so I made no changes.
12.To connect Left click on the Network icon and select the connection you just added. 

[http://www.jarviser.co.uk/jarviser/3gdell5510lucidlynx.html](http://www.jarviser.co.uk/jarviser/3gdell5510lucidlynx.html)

If that does not work maybe the dongle is not suitable.

---

### Post by jarviser on 2010-07-26
By the way a bit of googling got..

APN: 3internet
dial number is *99#
password: leave blank
username leave blank

the other APN you were given is for mobile phones.

---

### Post by nmlferreira on 2010-07-26
You're right in both your postings. I've tried that already (with the provider, and with an unlisted one). The problem is when I left click the Network Manager, it doesn't show the added broadband connection. It only shows the wired and, when I tried wirelessly, it also showed them. Never got it by adding broadband connections .

---

### Post by jarviser on 2010-07-26
It does that if there is no dongle recognised. Same as if you switch off wifi card the wireless option is not there.

Is there an Enable Mobile Broadband tickbox if you right-click the icon?  If not it sounds like the dongle is not supported out of the box,

---

### Post by nmlferreira on 2010-07-27
I think you are right again, however the good news are I managed to connect via wifi.
I read through a thread about how to use Windows drivers so that Ubuntu could recognize the hardware and it worked. I'm now surfing the web again!! Let's hope it lasts.
Thanks everyone for your help and support.

---

