---
title: "Has anyone managed to use speedtouch 330 usb in ubuntu?"
date: 2005-04-21
forum: Networking &amp; Wireless
---

### Post by rdfi on 2005-04-21
I'm trying for several days to configure my ADSL modem in ubuntu.
I've tried 4 diferent how-to with no success.
I know my VCI an VPI values.

If someone knows how to configure the speedtouch  330 (silver) please help
My modem uses pppoe.

Thanks
Rui

---

### Post by Karlos on 2005-04-21
i indeed know very well how to do this.......

you need the version of speedtouchconf from 10-Nov-2004 and some firmware ( rev4fw.zip)

do google search for them .. let me know if you dont find em

put the firmware in the speedtouchconf directory and then put the whole lot into /tmp and run the script from there

once connectedyou have to add 'pppoatm' to your /etc/modules

then adjust /etc/speedtouch.conf

change..

LOAD_USBCORE=1           to   LOAD_USBCORE=0
LOAD_USBINTERFACE=1   to   LOAD_USBINTERFACE=0  (IF APPLICABLE)

you should now connect on boot


if this just confuses you more let me know an ill write a more in depth kinda howto for ya..Karlos

---

### Post by Karlos on 2005-04-21
actually this seemed to work for someone..

 i can explain roughly how I did it 
 
 This is from the point of view of a fresh install..ok
 
 first you need to apt-get gcc and g++ from the ubuntu cd
 
 (not sure if you really need g++ but it seems to work if I do it like this)
 (I have done this on 3 diferent machines now...with success)
 
 then..
 make a directory called usr/local/lib/speedtouch
 
 $ sudo mkdir /usr/local/lib/speedtouch
 
 then..
 
 $ sudo gedit /etc/modules
 
 ..in here add the line
 
 pppoatm
 
 <hit save>
 
 I HAVE FOUND THAT THE WHOLE THING SEEMS TO WORK BETTER IF I RE-BOOT THE MACHINE AT THIS POINT...DUNNO WHY...JUST WORKS
 
 once rebooted run the speedtouchconf script again ( I do this bit in /tmp)
 
 (if your using the silver 330 you need the "rev4fw.zip" fimware)
 
 If you manage to connect successfully then good for you hooraaa
 
 ..say yes when it asks you about the connecting on reboot sorta blurb at the end
 
 next..do this..
 
 $ sudo gedit /etc/speedtouch.conf
 
 ..in here you have to change 2 settings
 
 change LOAD_USBCORE=1  to  LOAD_USBCORE=0
 
 and
 
 change LOAD_USBINTERFACE=1  to  LOAD_USBINTERFACE=0
 
 <hit save>
 
 That should make it fire up on boot
 
 That's basically what I do and it seems to work quite well....
 
 ...hope this helps..Karlos

---

### Post by Karlos on 2005-04-21
check the END of this thread .. the KARLOS bit (of course)

[http://www.ubuntuforums.org/showthread.php?t=11303&page=2&pp=10](http://www.ubuntuforums.org/showthread.php?t=11303&page=2&pp=10)

---

### Post by rdfi on 2005-04-21
Unfortunatly this didn't work...
When I was running the speedtouchconf script there was an error saying that "module usb_ohci not found"

I don't know how to solve this, so I could use some more help.

Thanks

---

### Post by rdfi on 2005-04-22
Here is what the output of the script:
> 
Are these correct? (Y/N)
y
No further user interaction is required.
Configuring SpeedTouch Driver...
Software Configuration - SUCCESS
Building SpeedTouch Driver...
Software Build - SUCCESS
Installing SpeedTouch Driver...
Software Installation - SUCCESS
Creating ppp files in //etc/ppp
FATAL: Module usb_ohci not found.

   *** Configuration finished. Starting the connection ***

The modem lights should start flashing for approx. 20 seconds...
The modem_run command failed (code 250)
modem_run results:
Failed to load microcode - this is not a problem if you
have already loaded the microcode.
The microcode can only be loaded once per system boot;
We'll assume that the microcode is already loaded, and
not call this an error.
You may encounter problems, though.
If you get a message to check your password, and your
password is definitely correct, switch off the PC, disconnect the
modem for a few seconds, re-connect, switch on, remove the speedtch
module if it is loaded, and try again.
Running : pppd call adsl
*********************************
* Don't seem to have connected. *
*********************************
Please check the username and password in /etc/ppp/*-secrets.
Also check the VPI/VCI in /etc/ppp/peers/adsl
Then run /etc/init.d/speedtouch start


---

### Post by Karlos on 2005-04-24
are you sure you got your username and password right

ie yoursurname.wanadoo.co.uk@fs

or something like that

also try adding pppoatm to your /etc/modules and reboot before you run the script

ive found that the script from 10-Nov-2004 seems to be the only one that works for me make sure your using that one

..stick with it you will get there it took me ages as well to get the thing going but its worth it when you get there

if you get really stuck you could try emailing steve parker the bloke who wrote the script..he will probably direct you to someone who can help..his email address is somewhere in amongst all the blurb in the script files..thats what i did in the end..

---

### Post by Karlos on 2005-04-24
dont worry about that module error bit (ohci) mine does that too and it still works

---

### Post by rdfi on 2005-04-25
[QUOTE=Karlos]are you sure you got your username and password right

ie yoursurname.wanadoo.co.uk@fs

or something like that

also try adding pppoatm to your /etc/modules and reboot before you run the script

ive found that the script from 10-Nov-2004 seems to be the only one that works for me make sure your using that one

..stick with it you will get there it took me ages as well to get the thing going but its worth it when you get there

if you get really stuck you could try emailing steve parker the bloke who wrote the script..he will probably direct you to someone who can help..his email address is somewhere in amongst all the blurb in the script files..thats what i did in the end..[/QUOTE]
 I've checked the username and password, they're good, I've tried to add pppoatm to /etc/modules, still didn't work.

Can it be because my ISP uses PPPoE ?

---

### Post by saul on 2005-04-29
Hi, I have the same modem. It wasn't easy, I tried different ways to configure it  ](*,), but finally I found a page with the instructions for ubuntu and suse among others. I have tried both (ubuntu and suse) and the modem works properly with all of them   :razz: . Here's the page: [http://linux-usb.sourceforge.net/SpeedTouch/index.html](http://linux-usb.sourceforge.net/SpeedTouch/index.html)  =D>

---

### Post by Karlos on 2005-04-30
thats excellent .. well done

I've kinda found me own haphazard way of getting it to work using the speedtouchconf script

but that method looks much better

I'm gonna reboot my system soon ... I'll try out that method, it looks good..!

---

