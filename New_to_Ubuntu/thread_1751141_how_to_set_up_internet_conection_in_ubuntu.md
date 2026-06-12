---
title: "how to set up internet conection in ubuntu"
date: 2011-05-06
forum: New to Ubuntu
---

### Post by naved ..... on 2011-05-06
i had just install ubuntu 10.10 but unable to connect to internet ...i called my isp but they said we dont know how to configure in linux u do it urself if u can ?
i m using dual boot so frm win 7 i m posting this msg plz help me plz

---

### Post by mtangoo on 2011-05-06
Have you checked the help?
If not see it [here]("https://help.ubuntu.com/10.10/internet/C/index.html")

---

### Post by HereInOz on 2011-05-06
How do you connect to the Internet with Windows 7?
Dial-up?
Through a router to an ADSL, ISDN or Cable service?
3G Wireless Broadband?

If you tell us this, we may be able to give you more information

---

### Post by naved ..... on 2011-05-06
> **mtangoo said:**
> Have you checked the help?
If not see it [here]("https://help.ubuntu.com/10.10/internet/C/index.html")

i m using dail-up connection ...and a wired cable internet cable connection and i have taken all the info of my connection throught ipconfig command...now help me asap

---

### Post by naved ..... on 2011-05-06
> **mtangoo said:**
> Have you checked the help?
If not see it [here]("https://help.ubuntu.com/10.10/internet/C/index.html")

i m using dail-up connection ...and a wired cable internet cable connection and i have taken all the info of my connection throught ipconfig command..plz .now help me asap

---

### Post by HereInOz on 2011-05-06
Ah, now if you are using an internal modem in your computer, which you probably are, please be aware that they are generally called WinModems, for good reason.  They usually only work with Windows, and the manufacturers have never produced drivers for Linux.

I know that some people far more persistent than I am have got some of these things working, but you really have to know what you are doing, and if you are new to Ubuntu, it may well be beyond you.

If you are using an external modem connected to a serial port, then it is a lot easier.  

Which modem type are you using?

---

### Post by kaldor on 2011-05-06
It's dialup? Ouch :(

That should be easy enough. Some years ago I needed to set up PPPoE manually. Maybe you should try that?

Does this help?: [https://help.ubuntu.com/community/ADSLPPPoE#pppoeconf](https://help.ubuntu.com/community/ADSLPPPoE#pppoeconf)

---

### Post by Bölvaður on 2011-05-06
*irrelevant*

---

### Post by HereInOz on 2011-05-06
Don't think that will help, Kaldor.  That is for ADSL PPPoE. whereas this one is an analog dial up modem.  

With an External dialup modem it is relatively easy by installing GnomePPP as a gui dialer.  It normally finds the modem and connects through it.

The internal Winmodems are often heartbreakers, though.

---

### Post by kaldor on 2011-05-06
Ah right, sorry :)

---

### Post by jmore9 on 2011-05-06
If you have a modem that is connected to your serial port you can try sudo pppconfig and follow the steps.  Couple of months ago i had to use dialup and i had to change the modem dev to 0 from ubuntu's 1.

To connect just use sudo pon , to disconnect sudo poff  

Hope that helps

---

### Post by naved ..... on 2011-05-06
its an internal modem , 
so in one word i cant use internet in ubuntu ????????

---

### Post by oldos2er on 2011-05-06
> **naved ..... said:**
> i m using dail-up connection ...and a wired cable internet cable connection

If you have wired broadband, why do you want to use dial-up?

---

### Post by naved ..... on 2011-05-06
its an internal modem , 
so in one word i cant use internet in ubuntu ?
help me ....:((((((

---

### Post by naved ..... on 2011-05-06
i dont ,  [someone here]he asked me how u connect to internet in win 7 ?....i just want to use internet no matter how ! help me

or i have to tell my isp to give me a external modem ! will this resolve my problem ????

---

### Post by roger_1960 on 2011-05-06
Hi

I gave up with an internal winmodem after many many hours of terminal bashing - learned a lot but got nowhere!  I bought a USR5637 USB modem - see

[http://www.usr.com/support/product-template.asp?prod=5637](http://www.usr.com/support/product-template.asp?prod=5637)

and then used the following instructions (from a kind soul on these forums) to make it work:

Dial-up Internet Access With A USB Modem
One easy way to connect to the internet using a dial-up
account is to buy a USB modem which the manufacturer
describes as "Linux-compatible".
&#8226; Install Gnome PPP (available in Synaptic Package Manager)
&#8226; Access System > Administration > Users and Groups
&#8226; Access Advanced Settings (enter password)
&#8226; Open User Privileges Tab
Make sure everything (especially &#8220;Connect to internet with a
modem&#8221; plus &#8220;Use modems&#8221;) is checked then plug in your
external (USB) Linux-compatible modem [in this example I'm
using a USRobotics USR Model 5637.]
A &#8226; Open Gnome PPP, click on Setup, click on Detect (Gnome
   PPP will then detect the modem), after detection close the
  setup box, and enter your connection information such as
 login, password, local telephone number of ISP and so on.
When connection is established, open your browser and surf!

To end the session and exit, close the browser and click
Disconnect

Good luck

---

### Post by naved ..... on 2011-05-06
i configure the network settings and insert the correct ip and all info like gateway and all it shows me the connection established and active but i couldnt connect to internet ??:(

instead of usb if i use external modem like cisco external modem so will i able to access internet ????

---

### Post by roger_1960 on 2011-05-06
Hi again

The USR modem I referred to is an external modem which plugs into a USB port.  I think you are confused about what you are using.  What does your Cisco external "modem" plug into?  USB port or LAN port or telephone socket (all on your PC)?

What is the model no of the Cisco modem?

---

### Post by larrypg on 2011-05-06
I am getting stuck on the wording of the OP.  It almost seems that they are either using dial-up or a cable company internet connection.  I am not sure if it is just the way the sentence is worded.  

"i m using dail-up connection ...and a wired cable internet cable  connection and i have taken all the info of my connection throught  ipconfig command..plz .now help me asap"

In Windows do you use a cable company internet connection or is the only way to access the internet is by dial-up?  Just thought this should get straightened out.

---

### Post by naved ..... on 2011-05-07
hii...i dont have any external usb modem my frnd has it and its company is cisco , and i dont know where he connects it ..?
my problem is how i could connect to internet , is external modem is the only way , coz i need to buy 1..it ll cost my pocket ...:(

---

### Post by naved ..... on 2011-05-07
> **larrypg said:**
> I am getting stuck on the wording of the OP.  It almost seems that they are either using dial-up or a cable company internet connection.  I am not sure if it is just the way the sentence is worded.  

"i m using dail-up connection ...and a wired cable internet cable  connection and i have taken all the info of my connection throught  ipconfig command..plz .now help me asap"

In Windows do you use a cable company internet connection or is the only way to access the internet is by dial-up?  Just thought this should get straightened out.

dude so what are the other way to connect to internet except dail-up , i asked my isp but he says he dont have any knowledge abt linux , so i m help less at this point but as u r saying i can connect to internet only by external modem , but to do this i need to buy 1..:(

---

### Post by dineshs on 2011-05-07
Please post the result of ```
ipconfig /all
``` in [COLOR="Red"]windows[/COLOR] when connection is working
What does ```
lspci 
```say in ubuntu ?

---

### Post by roger_1960 on 2011-05-07
Hi

I suggest you plug your friends USB modem into your USB socket, the other cable into the phone socket and try the instructions in my earlier post #16.  The make of modem should not matter.

---

### Post by Thewhistlingwind on 2011-05-07
> **dineshs said:**
> please post the result of ```
ipconfig /all
``` in [color=red]windows[/color] when connection is working
what does ```
lspci 
```say in ubuntu ?

+1

---

### Post by naved ..... on 2011-05-07
> **roger_1960 said:**
> Hi

I suggest you plug your friends USB modem into your USB socket, the other cable into the phone socket and try the instructions in my earlier post #16.  The make of modem should not matter.
i m not using telephone modem to connect to internet !!

---

### Post by naved ..... on 2011-05-07
> **dineshs said:**
> Please post the result of ```
ipconfig /all
``` in [COLOR=Red]windows[/COLOR] when connection is working
What does ```
lspci 
```say in ubuntu ?
answer to ur question is [check out the files]

---

### Post by alphacrucis2 on 2011-05-07
> **naved ..... said:**
> dude so what are the other way to connect to internet except dail-up , i asked my isp but he says he dont have any knowledge abt linux , so i m help less at this point but as u r saying i can connect to internet only by external modem , but to do this i need to buy 1..:(

Hardly anyone uses dialup these days AFAIK. Most people use some sort of broadband connection.

---

### Post by roger_1960 on 2011-05-07
Hi again

Sorry - but when you said

> i m using dail-up connection 

you implied a telephone connection!  

I've had a quick look at your posted outputs and there appears to be a problem with your MCP61 Ethernet card which identifies itself as a bridge?!  Its a bit technical but might explain why you can't configure it.  Perhaps someone knows more - I couldn't find anything but confirmations that there is a problem with that bit of hardware.  Probably you will need an external modem.

---

### Post by naved ..... on 2011-05-08
> **roger_1960 said:**
> Hi again

Sorry - but when you said



you implied a telephone connection!  

I've had a quick look at your posted outputs and there appears to be a problem with your MCP61 Ethernet card which identifies itself as a bridge?!  Its a bit technical but might explain why you can't configure it.  Perhaps someone knows more - I couldn't find anything but confirmations that there is a problem with that bit of hardware.  Probably you will need an external modem.

so you mean buying an external modem is the only way to connect to internet with ubuntu 10.10 in my case ?
my isp is about to send some technical person to solve this lets see what happens next !
hope i did not need to purchase an external modem i do not want to cost my pocket just to use internet in ubuntu .....:(

---

### Post by vatsagaurav007 on 2011-05-08
hi
this is the simple way to connect to internet in ubuntu.

goto terminal
type <sudo pppoeconf>
then the system will automatically detect connection, and will ask you for username and password of the connection, mention it.

then type, (to connect)<sudo pon dsl-provider>
to disconnect <sudo poff>


revert back for any help.
thanks

---

### Post by naved ..... on 2011-05-09
> **vatsagaurav007 said:**
> hi
this is the simple way to connect to internet in ubuntu.

goto terminal
type <sudo pppoeconf>
then the system will automatically detect connection, and will ask you for username and password of the connection, mention it.

then type, (to connect)<sudo pon dsl-provider>
to disconnect <sudo poff>


revert back for any help.
thanks
just this much ..and mu internet will work ? are you sure ?
or you r kidding me i dont need to configure ip or dns or gateway ?
but i ll try what you said hope it works for me ?

---

### Post by dineshs on 2011-05-09
> goto terminal
type <sudo pppoeconf>pppoeconf is for DSL whereas ```
sudo pppconfig
``` is for dialup
If you are using an internal dialup modem, lspci should show something like```
05:0b.0 Modem: Smart Link Ltd. SmartPCI2800 V.92 PCI Soft DFT (rev 02)
```I dont see anything like that from what you have posted.Was the modem plugged in PCI slot while running that command ?
Can you tell which telephone number are you dialling? or can you attach the image of dialler you are using in windows?

---

### Post by naved ..... on 2011-05-10
> **dineshs said:**
> pppoeconf is for DSL whereas ```
sudo pppconfig
``` is for dialup
If you are using an internal dialup modem, lspci should show something like```
05:0b.0 Modem: Smart Link Ltd. SmartPCI2800 V.92 PCI Soft DFT (rev 02)
```I dont see anything like that from what you have posted.Was the modem plugged in PCI slot while running that command ?
Can you tell which telephone number are you dialling? or can you attach the image of dialler you are using in windows?
i m not using phone modem . i m using dial-up to my isp i dont have modem connected any where its just the internal modem i have and the ubuntu guys are saying that (internal modem aka winmodem) dont have linux driver so you probably need an external modem this is the only way available for me i guess i tried what the above guy said but nothing happens....

---

### Post by dineshs on 2011-05-10
naved .....
Are you using a dialler on windows?If yes how did you create it?
Pl see this link
[http://www.bayan.com.ph/forum/yaf_postst3417_DIY-Tutorial-Setup-a-PPoE-Dialer-in-Windows-7-With-Images.aspx](http://www.bayan.com.ph/forum/yaf_postst3417_DIY-Tutorial-Setup-a-PPoE-Dialer-in-Windows-7-With-Images.aspx)
and tell us what option you selected in step 7 while creating dialler ? PPPoE or dialup?
I am asking this because I think you are using ethernet card not dialup modem.An ethernet card has RJ45 port which look similar to RJ11 port in dialup modem.Pl confirm.
> Was the modem plugged in PCI slot while running that command ?
Can you tell which telephone number are you dialling? or can you attach the image of dialler you are using in windows?
Pl reply

---

### Post by naved ..... on 2011-05-11
> **dineshs said:**
> naved .....
Are you using a dialler on windows?If yes how did you create it?
Pl see this link
[http://www.bayan.com.ph/forum/yaf_postst3417_DIY-Tutorial-Setup-a-PPoE-Dialer-in-Windows-7-With-Images.aspx](http://www.bayan.com.ph/forum/yaf_postst3417_DIY-Tutorial-Setup-a-PPoE-Dialer-in-Windows-7-With-Images.aspx)
and tell us what option you selected in step 7 while creating dialler ? PPPoE or dialup?
I am asking this because I think you are using ethernet card not dialup modem.An ethernet card has RJ45 port which look similar to RJ11 port in dialup modem.Pl confirm.

Pl reply
ya same thing i did its pppoe ...we r using ethernet to connect to internet with username and password ...now what i have  to do to connect to internet in ubuntu ..my isp too didnt have any knowledge abt linux he says do on ur own ...bloody freak !

---

### Post by dineshs on 2011-05-11
Pl try this
[http://ubuntuforums.org/showpost.php?p=9611450&postcount=2](http://ubuntuforums.org/showpost.php?p=9611450&postcount=2)

---

