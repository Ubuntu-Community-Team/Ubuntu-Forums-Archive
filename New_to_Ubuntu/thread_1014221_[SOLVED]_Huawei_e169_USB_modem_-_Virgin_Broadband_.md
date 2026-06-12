---
title: "[SOLVED] Huawei e169 USB modem - Virgin Broadband - Australia [solved]"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by step_god on 2008-12-17
Been tearing my hair out for two weeks now with this one but I did get it to work. 

I have Ubuntu 8.10, Huawei e169 USB modem and Virgin Broadband. The modem was detected no problems although shows up as an E620, but that doesn't seam to matter, I created the connection in the nm-applet and it looked like it was trying to connect but would immediately disconnect or keep asking for the password which wouldn't work.  

It does seam the new network manager has alot of problems to sort out yet, the particular one causing me grief was that I couldn't change the settings on the PPP tab of the connection editor. I could change the check boxes but the changes are not retained. 

With Virgin,it seams, you must login with PAP authentication, but because I couldn't disable CHAP authentication in the connection editor I was unable to connect successfully

To fix 
sudo gedit /etc/ppp/options

find the line that says
#-chap   
and uncomment it (delete #)
-chap
 this (I think) disables CHAP authentication

I also had to change the APN to VirginBroadband instead of VirginInternet which was the default And now its happy. 

Other settings
Number *99#
Uname <your virgin username>
PW <your virgin password>

Hope this helps someone else.


One other warning on this type of connection. Your machine is visible on the net. Make sure you install a firewall (eg firestarter)to protect yourself.

---

### Post by Shhnap on 2008-12-17
That's very nice of you to help somebody else. And welcome to the forums. Also, if you want to mark a topic as solved just use the inbuilt, Thread Tools -> Mark as Solved option in the top right of this thread. :D

---

### Post by karlbowden on 2009-01-21
Wow! This really helped me too. And I can confirm that both steps were needed to be able to connect (-chap and APN VirginBroadband).

Also when it comes up with the password dialog I can enter anything in there and it connects.

---

### Post by HereInOz on 2009-02-10
Many thanks for this information.  Worked perfectly. You have saved me massive headaches.

---

### Post by brianco on 2009-02-12
:confused::confused::confused:
Thank you i followed your instructions but do not understand""
to fix
sudo gedit/etc/ppp/options
find the line etc. etc.

where do i type this or how do i find this sorry but am first time user ofubuntu and need more help

---

### Post by anaconda on 2009-02-12
you type that command in terminal. You should find terminal from 
Accessorie>terminal

(Or if you dont have terminal in there you can type Alt-F2 and type gnome-terminal in there..)

PS. gnome-ppp should work fine with e169 too.

---

### Post by brianco on 2009-02-12
> **anaconda said:**
> you type that command in terminal. You should find terminal from 
Accessorie>terminal

(Or if you dont have terminal in there you can type Alt-F2 and type gnome-terminal in there..)

PS. gnome-ppp should work fine with e169 too.

when i open terminal it shows brian@brian-dektop:~$ and i type       sudo gedit/etc/ppp/options
it then says type in password which i do i then press enter and it comes up command not found... i am not sure why it does not accept the command.!!

---

### Post by brianco on 2009-02-12
> **anaconda said:**
> you type that command in terminal. You should find terminal from 
Accessorie>terminal

(Or if you dont have terminal in there you can type Alt-F2 and type gnome-terminal in there..)

PS. gnome-ppp should work fine with e169 too.

when i open terminal it shows brian@brian-dektop:~$ and i type       sudo gedit/etc/ppp/options
it then says type in password which i do i then press enter and it comes up command not found... i am not sure why it does not accept the command.!!

---

### Post by brianco on 2009-02-13
i have also typed other commands in the terminal and have received the same answer   "command not found""  maybe i am missing some software??? loaded gnome-ppp and still cannot connect.have spent 5 hours searching the net for help and this site seems to be the only one where people have had success with loading the e 169 usb modem onto ubuntu....what must i be doing wrong????

---

### Post by anaconda on 2009-02-13
> **brianco said:**
> when i open terminal it shows brian@brian-dektop:~$ and i type       sudo gedit/etc/ppp/options
it then says type in password which i do i then press enter and it comes up command not found... i am not sure why it does not accept the command.!!

You typed it wrongly. It is:
sudo gedit /etc/ppp/options
NOT
sudo gedit/etc/ppp/options
There is supposed to be a space between qedit and /

And the gnome-ppp should also work, but you need to fill the information from your operator.. eg.
username, password, phone number, init Strings, and select the "Ignore terminal strings" from options tab. and from the modem tab press the "Detect" modem button...

---

### Post by brianco on 2009-02-13
well what a dodo i am i must have looked at that command line 50 times and did not see the space,sorry for that....thank you i typed it correctly and modem works perfectly....also i did not enter details in gnome ppp properly....many thanks for your patience!!

---

### Post by johanndeboer on 2009-02-20
Thank you so much! I called VirginBroadband to ask for help with this and they said "We do not support Linux" which I thought was very sad given that I had signed up for a 24 month contract. So I did a search on google to find your solution and it worked perfectly without a hitch! Thank you so much! I hope Virgin can use this to help other customers too.

---

### Post by surfsunadam on 2009-03-01
Thank you very much sir! Worked perfectly for me.

---

### Post by axelmasok on 2009-03-25
My first Post! First time K/Ubuntu user long time Linux user (circa 1998 ).
Confirming the ability to use Virgin Broadband in Australia. Here is my setup:

- Ubuntu Ultimate Intrepid with Kubuntu DE
- Linux laptop64 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64 GNU/Linux
- Qt: 3.3.8b, KDE: 3.5.10 (Yes but running 4.2), KNetworkManager: 0.7, Networkmanager 0.7
- Bus 006 Device 003: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
- Looks like it is using both usbserial and option kernal modules:
```
Mar 25 20:05:37 laptop64 kernel: [  167.568887] usbcore: registered new interface driver usbserial                       
Mar 25 20:05:37 laptop64 kernel: [  167.569314] usbserial: USB Serial support registered for generic                     
Mar 25 20:05:37 laptop64 kernel: [  167.569726] usbcore: registered new interface driver usbserial_generic               
Mar 25 20:05:37 laptop64 kernel: [  167.569729] usbserial: USB Serial Driver core                                        
Mar 25 20:05:37 laptop64 kernel: [  167.584601] usbserial: USB Serial support registered for GSM modem (1-port)          
Mar 25 20:05:37 laptop64 kernel: [  167.585106] option 6-2:1.0: GSM modem (1-port) converter detected                    
Mar 25 20:05:37 laptop64 kernel: [  167.585622] usb 6-2: GSM modem (1-port) converter now attached to ttyUSB0            
Mar 25 20:05:37 laptop64 kernel: [  167.586039] option 6-2:1.1: GSM modem (1-port) converter detected                    
Mar 25 20:05:37 laptop64 kernel: [  167.586466] usb 6-2: GSM modem (1-port) converter now attached to ttyUSB1            
Mar 25 20:05:37 laptop64 kernel: [  167.586879] option 6-2:1.2: GSM modem (1-port) converter detected                    
Mar 25 20:05:37 laptop64 kernel: [  167.587300] usb 6-2: GSM modem (1-port) converter now attached to ttyUSB2            
Mar 25 20:05:37 laptop64 kernel: [  167.587714] usbcore: registered new interface driver option                          
Mar 25 20:05:37 laptop64 kernel: [  167.587717] option: USB Driver for GSM modems: v0.7.2
```
- Clicked the Knetwork Manager icon in the tray, New Connection, ttyUSB0, entered a PIN, VirginBroadband for the APN, Network = Any, Band = 0, NUMBER = *99#.
- Edited the /etc/ppp/options file to uncomment #-chap as the previous posts suggested and VOILA!! Happy days! :)

---

### Post by ruggo on 2009-05-11
Just a security note about the original solution, the user name and password do NOT have to be your virgin user name and password. You can either leave these fields blank, or put any random text in that you wish.

---

### Post by no-clue on 2009-06-01
Thank you very much nice and short and painless

---

### Post by puttingau on 2009-06-10
Thanks from me, too!:p

---

### Post by jazzguyman on 2009-07-15
Thanks guys for all of this helpful info!!!  It worked for me as a result, but below I have outlined how a **newbie, like me, ****could do it**.  It worked for me on a few machines anyhow.  Much appreciated all of the info you supplied, though!  I needed it.

(Thanks to Grant Petch for helping to figure this out!!)

First off, this worked with Ubuntu Linux versions 8.10 and 9.04. This may or may not work in previous versions, but please let us know if this works under any other versions or distributions of Linux.
Secondly, the model number that this solution worked for is the "Huawei E169".

So, with your Ubuntu 8.10 or 9.04 system booted up and ready, plug in the USB device.
Wait.
Follow the prompts for a couple of screens and then when you come to the Name of the device, RENAME IT to "VirginBroadband" (all one word and note the capital letters).
Then apply that change by clicking OK. Then hit the close buttons of the open windows.

Now, go to your network icon at the top of the Ubuntu desktop, which is an icon of two computers. Left-click that once and then select 'VPN' and then select 'Configure VPN'.
Then click on the 'Mobile Broadband' tab. Highlight the Virgin Broadband option and then click 'Edit'. If you are asked about whether to accept a keyring, click 'Allow' or 'Accept All'.
Under the 'Mobile Broadband' tab, rename the APN to "VirginBroadband", which is exactly the same as the name we first gave the device.

Now, click on the 'PPP Settings' tab. Click 'Configure Methods' button and then _UNCHECK_ the 'CHAP' check-box. Click 'Apply' and then close all of the windows down.

Now, left-click on the networks icon again and now click on 'VirginBroadband'... wait a bit... and now, it should be working.

Open Mozilla Firefox or whatever internet browser you use, and test it out by going to 'Baysidechurch.org.au'... or any other web-page of choice. ;-)


NOW, I found a difference when using Ubuntu 8.10, whereby it actually asked for a password to access the internet. I went and found a solution to this problem too! Here it is:

Double-click the 'VIRGIN BROADBAND' icon on desktop to open it.
You will then see a file called 'SysConfig.dat'. Double-click this to open it.
You will be asked the question, "Do you want to run 'SysConfig.dat', or display its contents?" to which you should click on 'Display'.

There will be a list of paragraphs with headings in square brackets. Find the paragraph with "[customize]" as the heading and then notice the first line following that reads "operator=VirginMobile_C261", or something like that.
THIS is your password! Well, not with the operator bit, the password is actually "VirginMobile_C261", at least it was for me. Yours might be different.
So, either write that down, or copy it by clicking Ctrl+C on your keyboard and then PASTE (or type) that password into the space provided when prompted for the password again.
A smart thing to do would be to create a quick text document using Text Editor and then paste this password into there. Save this text file to your desktop as something like "Virgin Broadband password".

There you have it! You should be able to open your internet browser now and surf the three w's.

Hoping for the best,

jazzguyman.

---

### Post by DaveQB on 2009-09-14
Thanks for this thread all.

I am looking at getting Virigin Broadband for my girlfriends PC and she is running Kubuntu 8.04 I believe.

So I will update it to 9.04 to get this working.

I will test with other distro's too while I have the device for people's interest. Mandriva 2009.1 will be tested. The Network Manager there has USB, Bluetooth options all there, so I am confident, as long as the kernel works out the hardware.

Thanks

---

### Post by DaveQB on 2009-09-20
I ran up a DVD of Kubuntu 8.10 I had here, rc1, i386.

In that, using Knetworkmanager. I only had to use the GUI. There was a page that had a bunch of check boxes, one was "Refuse CHAP", so I ticked that from my readings here and all worked second go. I didn't do anything different second go, just tried again when it first failed.

---

### Post by shiggydiggy on 2009-10-06
OMG this works!! (OP)

---

### Post by blue_shoe12 on 2010-05-03
> **jazzguyman said:**
> Thanks guys for all of this helpful info!!!  It worked for me as a result, but below I have outlined how a **newbie, like me, ****could do it**.  It worked for me on a few machines anyhow.  Much appreciated all of the info you supplied, though!  I needed it.

(Thanks to Grant Petch for helping to figure this out!!)

First off, this worked with Ubuntu Linux versions 8.10 and 9.04. This may or may not work in previous versions, but please let us know if this works under any other versions or distributions of Linux.
Secondly, the model number that this solution worked for is the "Huawei E169".

So, with your Ubuntu 8.10 or 9.04 system booted up and ready, plug in the USB device.
Wait.
Follow the prompts for a couple of screens and then when you come to the Name of the device, RENAME IT to "VirginBroadband" (all one word and note the capital letters).
Then apply that change by clicking OK. Then hit the close buttons of the open windows.

Now, go to your network icon at the top of the Ubuntu desktop, which is an icon of two computers. Left-click that once and then select 'VPN' and then select 'Configure VPN'.
Then click on the 'Mobile Broadband' tab. Highlight the Virgin Broadband option and then click 'Edit'. If you are asked about whether to accept a keyring, click 'Allow' or 'Accept All'.
Under the 'Mobile Broadband' tab, rename the APN to "VirginBroadband", which is exactly the same as the name we first gave the device.

Now, click on the 'PPP Settings' tab. Click 'Configure Methods' button and then _UNCHECK_ the 'CHAP' check-box. Click 'Apply' and then close all of the windows down.

Now, left-click on the networks icon again and now click on 'VirginBroadband'... wait a bit... and now, it should be working.

Open Mozilla Firefox or whatever internet browser you use, and test it out by going to 'Baysidechurch.org.au'... or any other web-page of choice. ;-)


NOW, I found a difference when using Ubuntu 8.10, whereby it actually asked for a password to access the internet. I went and found a solution to this problem too! Here it is:

Double-click the 'VIRGIN BROADBAND' icon on desktop to open it.
You will then see a file called 'SysConfig.dat'. Double-click this to open it.
You will be asked the question, "Do you want to run 'SysConfig.dat', or display its contents?" to which you should click on 'Display'.

There will be a list of paragraphs with headings in square brackets. Find the paragraph with "[customize]" as the heading and then notice the first line following that reads "operator=VirginMobile_C261", or something like that.
THIS is your password! Well, not with the operator bit, the password is actually "VirginMobile_C261", at least it was for me. Yours might be different.
So, either write that down, or copy it by clicking Ctrl+C on your keyboard and then PASTE (or type) that password into the space provided when prompted for the password again.
A smart thing to do would be to create a quick text document using Text Editor and then paste this password into there. Save this text file to your desktop as something like "Virgin Broadband password".

There you have it! You should be able to open your internet browser now and surf the three w's.

Hoping for the best,

jazzguyman.


This solution does not work for me..

1. Virgin Broadband does not display on my desktop

2. I tried everything in this solution, all I get is GSM not available

3. I even installed Ubuntu 9.04 but that seemed like a waste of my time.

4. I'm a newbie of 4 years trying to connect to the internet with Virgin Mobile.

I need my internet to do anything at all with Linux. frustration is persistant

---

### Post by annefernee on 2010-05-26
Hi,

Has anyone tried to install the e169 or e1762 Huawei USB modem with Ubuntu 10.04 LTS version?

I tried the previously listed methods... and as a windows convert.. 10.04 does not look the same as previous postings..

I'm really keen to cut over and use Ubuntu as my full time OS, just need a little help to get everything set up n working in order to do so..

any help will be much appreciated.

Cheers,
Anthony.

---

### Post by philinux on 2010-05-26
This is an old thread. Try the advice in the General Help sticky for 10.04 lucid.

---

### Post by DaveQB on 2010-05-26
> **annefernee said:**
> Hi,

Has anyone tried to install the e169 or e1762 Huawei USB modem with Ubuntu 10.04 LTS version?

I tried the previously listed methods... and as a windows convert.. 10.04 does not look the same as previous postings..

I'm really keen to cut over and use Ubuntu as my full time OS, just need a little help to get everything set up n working in order to do so..

any help will be much appreciated.

Cheers,
Anthony.

I will be soon. Maybe this weekend. I'll find the new thread & post my findings. I suspect being more modern, it will be easier.

---

### Post by patmanpato on 2011-03-25
The suggestions made by the OP worked perfectly for me for Ubuntu 9.10.

With Ubuntu 10.04 and 10.10 however, it's not working, and I've tried fiddling with a few more things, to no avail. It looks like it's trying (green light on the dongle keeps flashing on and off), but never connects.


Any suggestions? Or is there another thread I should be posting this to? (I searched but couldn't find any more appropriate ones).

---

