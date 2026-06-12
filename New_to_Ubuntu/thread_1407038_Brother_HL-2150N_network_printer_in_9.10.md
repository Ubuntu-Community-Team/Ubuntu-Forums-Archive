---
title: "Brother HL-2150N network printer in 9.10"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by london_bug on 2010-02-14
HELP

Am 2 days into Ubuntu and loving it - has been a painless install and while it found the wireless network and my 2150N printer on the network with no problems i cant get the thing to work

No driver for it within Ubuntu and have tried one of the other brother drivers that was suggested on a website i found but still nothing

has anyone managed to get this printer working over a network ??

---

### Post by gordintoronto on 2010-02-14
I use a Brother 2170 network printer.  I went to the Brother web site to get the drivers.

---

### Post by london_bug on 2010-02-15
Any chance of a few pointers mate ?

I went to the brother website and ended up going round and round in circles

thought i had cracked it but it still didnt work 

as i say this is my first go at dipping my toe in the linux waters so all new to me

---

### Post by plucky on 2010-02-15
> **london_bug said:**
> Any chance of a few pointers mate ?

I went to the brother website and ended up going round and round in circles

thought i had cracked it but it still didnt work 

as i say this is my first go at dipping my toe in the linux waters so all new to me

Go [Here](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2150N) download the cupswrapper and LPR driver .deb files and install as shown on the website install instructions.

Good Luck

---

### Post by gordintoronto on 2010-02-15
> **london_bug said:**
> Any chance of a few pointers mate ?

I went to the brother website and ended up going round and round in circles


I did a couple of laps around the circle myself, but eventually it sank in.

One of the things I ran into was Linux' desire to find the printer at a consistent IP address.  I admit that I installed Brother's Windows-based printer manager program, in order to tell the printer to use a static IP address.

---

### Post by london_bug on 2010-02-18
ARGHHHHHHH

right went to the brother site - downloaded and installed the lpr and cupswrapper

checked cupswrapper and lpr and all as per the guide

when i goto localhost:631/printers it not only has no printer there to configure its completely different image to the guides screen grabs:confused:

going round and round and getting no where fast - i really am loving my Ubuntu experience other than this :(:(

Really dont want to go back wo Windoze but unless i can get the printer working i have no choice 

Also going to Email brother and tell them to update the guide ;)

---

### Post by gordintoronto on 2010-02-18
You might not have this program installed on your system.  Try opening Accessories/terminal, and enter the command:
system-config-printer

If that works, click the "server" tab, selecting new/printer.

---

### Post by cariboo on 2010-02-18
gordintoronto, beat me to it, but you shouldn't have to go to brother to get drivers for your print. I have an HL-5250DN, it worked using the printer wizard at System->Administration->Printing.

---

### Post by london_bug on 2010-02-19
Now dont this sum up computers perfectly ....

Just ran thru the process again doing exactly the same as before and it worked !!!!

i now have a fully working brother printer :o) so bye bye windoze for good 

thanks for everyones help :)

---

### Post by walt.smith1960 on 2010-02-19
I installed a Brother MFC-6490CW which isn't in the FooMatic database. I downloaded the .deb files and printed out the instructions.  The Brother instructions include Fedora(?) and also label printers. There were extra nonapplicable steps. I scratched out those steps. I boiled down to about 3 lines from a terminal and right clicking the .deb files. The scanner drivers were as easy.  Even better were the MFC-7820N & HP Photosmart 7460D. For those two, System>administration>printing>Server>New>Printer and let it search.  Oh...if the computer doesn't find the networked printer....make sure the printer is powered on :oops:.

---

### Post by Daan on 2010-10-07
In stead of installing anything from the Brother website I just added the printer with "system-config-printer" (as root). My printer is on a network, and Ubuntu gave two search results for it, I went with the second one which also mentioned the ip. I went with the default options, and installed the driver for the 2140, cause there was no option the 2150. The Ubuntu test page came out just fine. :)

I'm using Ubuntu 10.04.

---

