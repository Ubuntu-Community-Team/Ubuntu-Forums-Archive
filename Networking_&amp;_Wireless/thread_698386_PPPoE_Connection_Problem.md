---
title: "PPPoE Connection Problem"
date: 2008-02-16
forum: Networking &amp; Wireless
---

### Post by SebK on 2008-02-16
**Hi everyone,**
I'm a Ubuntu newbie and I just installed it, but I have a problem:
**How can I configure a PPPoE connection on Ubuntu?**

I opened a terminal and typed "*sudo pppoeconf*" and and followed the instructions. I did everything, and at the end, when I typed "sudo *pon dsl-provider*" to connect, internet still didn't work. I checked with "*plog*" and still nothing. Halp! I need a step-by-step guide (*with screenshots if possible*?) to use ppoeconf correctly + I need to know what info it will need (*and what is the meaning of that info it asks*...)

Thanks in advance,
**SebK**

---

### Post by lnx4me on 2008-02-16
Quick question,
 Why do you think you need pppoe? I ask because my dsl connection is handled by my modem.

---

### Post by SebK on 2008-02-16
> **lnx4me said:**
> Quick question,
 Why do you think you need pppoe? I ask because my dsl connection is handled by my modem.

Well I live in Iran, so I don't really have much choice. It's this (PPPoE 384k) or 56K modem. I use a Symphony ADSL Router SY800C.

---

### Post by lnx4me on 2008-02-16
Are you connecting the ubuntu box to the router and then the internet?

---

### Post by SebK on 2008-02-16
> **lnx4me said:**
> Are you connecting the ubuntu box to the router and then the internet?

What do you mean? I'm sorry I'm really new to al lthis stuff so.. :S 
Right now I'm using Vista. (Dual Boot).

---

### Post by lnx4me on 2008-02-16
A router is a piece of hardware that connects multiple PC's to the net. typically the router connects to the ISP (pppoe) and the PC's would get there information from the router. 
They other option is you have a dsl modem and a username and password, the PC that connects to the inet has software that allows the connection. from what you have stated you have a router but it appears that its really a modem.

---

### Post by SebK on 2008-02-16
> **lnx4me said:**
> A router is a piece of hardware that connects multiple PC's to the net. typically the router connects to the ISP (pppoe) and the PC's would get there information from the router. 
They other option is you have a dsl modem and a username and password, the PC that connects to the inet has software that allows the connection. from what you have stated you have a router but it appears that its really a modem.

Can't it be both? Some months ago I used this same router to connects multiple PC's to the net. Then my ISP called and said that now I have to use PPPoE. They sent me a tutorial, and I created a connection with windows. Password, username...etc and that's how I connect.

---

### Post by lnx4me on 2008-02-16
Is this a usb device?

---

### Post by SebK on 2008-02-16
> **lnx4me said:**
> Is this a usb device?

No, it's not. The router/modem is connected to a phone thingy, and there's another thicker ethernet wire that ocnnects to my PC.

---

### Post by lnx4me on 2008-02-16
yes I forgot to ask. Is the Ubuntu box a desktop version?

---

### Post by SebK on 2008-02-16
Yes it is =)

---

### Post by xc3RnbFO8P on 2008-02-16
Have you seen this:

> [http://forum.persiantools.com/t80504-page14.html](http://forum.persiantools.com/t80504-page14.html)

---

### Post by SebK on 2008-02-16
> **Ringi said:**
> Have you seen this:

Lol yeah but I cannot read farsi. I can just speak it a little bit. I'm french. I'm leaving next year lol...

---

### Post by lnx4me on 2008-02-16
Give me a few minutes. I dont use the desktop version at all. I build servers. Since your ISP sent you some instruction for windows it stands to reason that you should be able click on network manger and setup a new DSL connection to the internet. I'll do some more checking.

---

### Post by xc3RnbFO8P on 2008-02-16
Do have a manual for SY800C, if not you can download it from here:

> [http://www.refatek.com/InternetServices/ADSL/adsl-ModemDrivers.htm](http://www.refatek.com/InternetServices/ADSL/adsl-ModemDrivers.htm)

---

### Post by xc3RnbFO8P on 2008-02-16
On page 25 is about **pppoe**

---

### Post by SebK on 2008-02-16
> **Ringi said:**
> On page 25 is about **pppoe**

Thank you =) Read some stuff, but doesn't really say anything about Ubuntu or Linux... :S

---

### Post by xc3RnbFO8P on 2008-02-16
> **SebK said:**
> Thank you =) Read some stuff, but doesn't really say anything about Ubuntu or Linux... :S
No, but it is not about linux, you add your username and password in the router and it will automatically connect.

---

### Post by lnx4me on 2008-02-16
Did you try this link:
[https://help.ubuntu.com/7.10/internet/C/modems-adsl-pppoe.html](https://help.ubuntu.com/7.10/internet/C/modems-adsl-pppoe.html)

Does the windows system show the modem as a piece of hardware?

---

### Post by SebK on 2008-02-16
> **Ringi said:**
> No, but it is not about linux, you add your username and password in the router and it will automatically connect.

I know, I'm currently using it on Windows. On Vista I have no problems with PPPoE. It's only on Linux. 
Rgiht now I'm connected to the internet with PPPoE on vista. But when if put the username, passowrd...etc on Ubuntu, it doesn't work... :(

---

### Post by SebK on 2008-02-16
I have, and did everything, but at the end, it just doesn't want to connect. :S 

"*The PPPoE package to be installed in order for the following command to work. This package is installed by default.*"

Maybe it's not installed?

---

### Post by lnx4me on 2008-02-16
Take another look at what Ringi stated. If the modem can be configured with the username and password to connect then you dont need pppoe. You can just set the modem up and it will work.

---

### Post by xc3RnbFO8P on 2008-02-16
Remember to restart the modem or router.

---

### Post by lnx4me on 2008-02-16
Hey Ringi,
 we use siemes 4100, 4200 ect that you configure from pointing to the modem address 192.168.0. I still have a few systems that have the old modems that just do the DSL and rely on a client program to do the pppoe. I used RH way back when and there was a connection wizard that you could use from the GUI to setup the connection. Does ubuntu have a similar desktop tool?

---

### Post by xc3RnbFO8P on 2008-02-16
I have not seen it, I dont know.

---

### Post by SebK on 2008-02-16
Okay I don't think it'll help but well => [http://i28.tinypic.com/hsv0cx.jpg](http://i28.tinypic.com/hsv0cx.jpg)
Here's a screenshot of how I connect to the internet on my PC. It's pppoe right? Well, now what can i do to connect on ubuntu? :S

---

### Post by lnx4me on 2008-02-16
Did you go back to what Ringi stated?

---

### Post by SebK on 2008-02-16
> **lnx4me said:**
> Did you go back to what Ringi stated?

"*No, but it is not about linux, you add your username and password in the router and it will automatically connect.*" 

How can I do that?

---

### Post by xc3RnbFO8P on 2008-02-16
In Ubuntu open Firefox type 192.168.1.1 return

username admin passw. admin

---

### Post by SebK on 2008-02-16
> **Ringi said:**
> In Ubuntu open Firefox type 192.168.1.1 return

username admin passw. admin

I type it in the adress bar? So I first type * 192.168.1.1 return* and then *username admin passw. admin*? 

I'm sorry if I'm being annoying, but I never used Ubuntu before..

---

### Post by xc3RnbFO8P on 2008-02-16
> **SebK said:**
> I type it in the adress bar? So I first type * 192.168.1.1 return* and then *username admin passw. admin*? 
.

yes

---

### Post by lnx4me on 2008-02-16
> **SebK said:**
> I type it in the adress bar? So I first type * 192.168.1.1 return* and then *username admin passw. admin*? 

I'm sorry if I'm being annoying, but I never used Ubuntu before..

Your not annoying. This forum is about getting help. Sometimes it takes a little longer but thats okay.

---

### Post by SebK on 2008-02-16
Okay, so I typed the IP+return in the adress bar (Firefox) and it just  became a google search. the page didnt display because well internet didnt connect -_-

---

### Post by xc3RnbFO8P on 2008-02-16
We don't say this on Ubuntu forum, but:

> [COLOR="White"]You can do it in windows.[/COLOR]

---

### Post by lnx4me on 2008-02-16
Your currently working from vista: try this
192.168.1.1    press enter

---

### Post by xc3RnbFO8P on 2008-02-16
> **SebK said:**
> Okay, so I typed the IP+return in the adress bar (Firefox) and it just  became a google search. the page didnt display because well internet didnt connect -_-

How do you connect to the router?

---

### Post by SebK on 2008-02-16
Lol well I typed the IP you gave me and I got this: [http://www.google.com/search?q=192.168.1.1&rls=com.microsoft:*&ie=UTF-8&oe=UTF-8&startIndex=&startPage=1](http://www.google.com/search?q=192.168.1.1&rls=com.microsoft:*&ie=UTF-8&oe=UTF-8&startIndex=&startPage=1)

As for my router: There's a wire connected to a telephone line, and another thicker wire connected to my PC. It's not USB.

---

### Post by xc3RnbFO8P on 2008-02-16
You are in IE, you have to remove this search function.

---

### Post by lnx4me on 2008-02-16
In windows goto the command prompt and check this:
ipconfig

then

ping 192.168.1.1

and see if there is a response.

---

### Post by SebK on 2008-02-16
> **Ringi said:**
> You are in IE, you have to remove this search function.

Disabled automatic search. Now, when I only type the IP, I get: *Internet Explorer cannot display the webpage*

I did the cmd promt thing and here's a screenshot of what I got: [http://i28.tinypic.com/9ru1he.jpg](http://i28.tinypic.com/9ru1he.jpg)

---

### Post by xc3RnbFO8P on 2008-02-16
Try 192.168.1.1 again in the browser.

---

### Post by SebK on 2008-02-16
> **Ringi said:**
> Try 192.168.1.1 again in the browser.

On Vista? I did, and it gives me a "*Internet Explorer cannot display the webpage*" error.

---

### Post by lnx4me on 2008-02-16
Try restarting Internet Explorer. Also you may need to delete cache history.

---

### Post by SebK on 2008-02-16
Done. And still doesn't work => [http://i30.tinypic.com/3467sq9.jpg](http://i30.tinypic.com/3467sq9.jpg)

---

### Post by tavati on 2008-02-16
just follow the steps and tell me

step 1: == type this in address bar == 192.168.1.1
step 2: == press "ENTER" button on keyboard

// now u should get a screen asking username and password

step 3:  == type the words "admin" in both username and password box
step 4: == press "ENTER" on keyboard  OR "OK" button on the screen

// now u should get a screen with your ISP name in some good color and somewhere slightly down the screen you should see a table with lot of details about your misterious device which is actually a router/gatway for ur computer.

step 5: == now locate the row which says this  Primary DNS : xxx.xxx.xxx.xxx
step 6: == now locate the row just below which says : Secondary DNS : yyy.yyy.yyy.yyy

step 7: == please write down these numbers xxx.xxx.xxx.xxx and yyy.yyy.yyy.yyy on paper

step 8: == use ur mouse in ubuntu to open NETWORK like this : System -> Administration -> network

step 9: == enter your ubuntu login password when asked by ubuntu
step 10: == now select "Wired connection" checkbox and press "properties" button
step 11: == select "General" tab
step 12: == select "static IP addressing in first row"
step 13: == write this in IP address in next row :== 192.168.1.2
step 14: == write this in IP adress in last row ( GATEWAY ADDRESS) :== 192.168.1.1

// now the most important step

step 15: == select the DNS tab

// here u can add as many address as u want in the big box below

step 16: == now put the number xxx.xxx.xxx.xxx which u copied earlier
step 17: == add one more adress in the same box this time put yyy.yyy.yyy.yyy

now save and quit

// now please browse in ubuntu and give me ur reply using ubuntu

---

### Post by SebK on 2008-02-16
Thanks Tavati, but after stp 2, I didn't get  a screen asking username and password, I got the error :S

---

### Post by tavati on 2008-02-16
i just forgot

before step 15: just do the following

additional step after step 14: in "subnet mask" write this: == 255.255.255.0
// if u don;t do this u will face problem

---

### Post by xc3RnbFO8P on 2008-02-16
In the manual says that ip sould be 192.168.1.1 but some has 192.168.0.1, try that.

---

### Post by tavati on 2008-02-16
OK in that case just read the guide/tutorial which u got for windows. instead of 192.168,1.1 there must be some other number like zzz.zzz.zzz.zzz. do the same with this number. also use the same logic. i mean write ur static address as zzz.zzz.zzz. (zzz+1). i hope u get it -- add 1 to the last three digits and put that for example if the number given zzz.zzz.zzz.zzz is 192,168,2,5 then ur static address should be 192.168.2.6 . put the GATEWAY address same as zzz.zzz.zzz.zzz

---

### Post by SebK on 2008-02-16
> **tavati said:**
> OK in that case just read the guide/tutorial which u got for windows. instead of 192.168,1.1 there must be some other number like zzz.zzz.zzz.zzz. do the same with this number. also use the same logic. i mean write ur static address as zzz.zzz.zzz. (zzz+1). i hope u get it -- add 1 to the last three digits and put that for example if the number given zzz.zzz.zzz.zzz is 192,168,2,5 then ur static address should be 192.168.2.6 . put the GATEWAY address same as zzz.zzz.zzz.zzz

Which tutorial? The one my ISP gave me? It was on the phone, and the only thing they told me was how to create a PPPoE connection with my new username and pw. How can I get this IP adress? :S

---

### Post by lnx4me on 2008-02-16
Sometimes on the modems they get a little flaky about delivering the web page to admin it. Try restarting the modem and give it a minute then try to open the address 192.168.1.1 without connecting to the internet. It should open a page to setup the modem.

---

### Post by SebK on 2008-02-16
> **lnx4me said:**
> Sometimes on the modems they get a little flaky about delivering the web page to admin it. Try restarting the modem and give it a minute then try to open the address 192.168.1.1 without connecting to the internet. It should open a page to setup the modem.

Okay I resteared my PC, cleared the cache, turned off the modem/router and tried again, still nothing,

---

### Post by lnx4me on 2008-02-16
Did you try:
192.168.0.1

---

### Post by SebK on 2008-02-16
> **lnx4me said:**
> Did you try:
192.168.0.1

Yep, still nothing.

---

### Post by xc3RnbFO8P on 2008-02-16
I dont know how it work in Vista, what about: firewall, allowded sites

---

### Post by xc3RnbFO8P on 2008-02-16
Do you hava a Ubuntu live cd?

---

### Post by SebK on 2008-02-16
I disabled my AVG 8.0firewall, and the only CD I have is the Ubuntu installation CD. (I downloaded the .iso file and burned it) Still nothing.

---

### Post by xc3RnbFO8P on 2008-02-16
Popup blocker?

---

### Post by SebK on 2008-02-16
> **Ringi said:**
> Popup blocker?

I don't have any and the IE one is off. :S

---

### Post by lnx4me on 2008-02-16
Does this modem have both the USB and LAN connection? I finally got the manual downloaded and unzipped.

---

### Post by lnx4me on 2008-02-16
OKAY stop the insanity. basic principles of networking need to take place here. Based on what I am reading in the manual we need to configure the network card for static address's. Then we can configure the darn thing. It appears that this thing doesn't use DHCP on the LAN. Look on Page 14 of the manual.

---

### Post by xc3RnbFO8P on 2008-02-16
I found on the internet, that this modem is not supported by Linux.

---

### Post by lnx4me on 2008-02-16
> **Ringi said:**
> I fount on the internet, that this modem is not supported by Linux.

This may be from the USB side. Based on the manual. It should be able to be configured from the web space. the trick is you have to manually set the IP address on the Windows PC and then log in to set auto connect as well as the dhcp up.

---

### Post by SebK on 2008-02-16
Hi everyone,

Well I don't have the USB cable anyways. And as for the IP thing, I'll try to see what I can do. I'll repost tomorrow. Thnks for everything!

Seb

---

### Post by tavati on 2008-02-16
few things u should know which will help u

1.  IF u r able to connect in windows then it means that ur router/gateway device given by vendor is working. so don't change any setting in that 

2. now when u open ubuntu, i expect ur( ours !!) ubuntu to detect ur network card and give it a name which should be == "eth0". don't expect ubuntu to detect ur router/gateway now.

3.ur router/gateway is connected to this "eth0". so now u have to set the network card to work with this gateway your ISP has given.

4. VERY IMPORTANT : disable DHCP in ur ubuntu. 

5. GIve static address to ur network card  "eth0" as was told by me in step by step guide

6. for giving this static address u should know what is the static address of ur router/gateway which should be 192.168.1.1 OR 192.168.0.1 Or may be something else also. U have to know this OR else u cannot proceed further

7. VERY IMPROTANT : unless u put those DNS IP addresses which i referred to in my step by step guide ubuntu will not connect. 

8. U r left with the following jobs now

first: == find out the IP of ur gateway/router
second: == follow steps as told in the step by step guide
third: == disable DHCP while setting up the network card in the steps above

REM: u can find out the router IP . primary DNS and Secondary DNS IP addresses from ur ISP also by phone. but this may not be very practical -- at least in my country. 

i hope it helps u.

---

